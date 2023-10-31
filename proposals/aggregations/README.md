# OGC API - Records - Aggregations

This folder contains the content for the standard extension OGC API - Records - Term Aggregations.

# Overview

This extension enables the capability to include different types of Aggregations in the items (records) response. These
aggregations can be used by clients to enable [faceted search](https://en.wikipedia.org/wiki/Faceted_search).

Various backends support faceted search. Examples
are [Elastic](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-terms-aggregation.html), [SOLR](https://solr.apache.org/guide/8_8/json-facet-api.html)
and limited support
in [PostGres](https://akorotkov.github.io/blog/2016/06/17/faceted-search/), [Oracle](https://blogs.oracle.com/apex/apex-192-faceted-search).

Facet statistics are also interesting to give an overview of the spatio-temporal distribution of items in a (part of a)
collection.

This extension has three major requirements:

1. A new endpoint advertising the available aggregations for a collection, similar to `sortables` and `filterables`
2. An _aggregation overview_ should be included in the responses of the `/items` collection endpoint which let the user
   specify which aggregations they are
   interested in
3. A new endpoint which lets the user "drill down" into a single aggregation, querying more results and applying filters

## Definition of an Aggregation

The word _Aggregation_ refers here to a high-level piece of information that is computed over a set of records in a
collection.

An aggregation can be of several types:

### Terms aggregation

A "terms" aggregation can be applied to any text property and produces a list of values appearing for a specific
property across all matching records, as well as the count of records containing each value.

#### Example

The aggregation `keyword` will return a list of buckets like so:

* `forestry` (24 records)
* `marine` (12 records)
* `pollution` (5 records)
* etc.

### Histogram aggregation

A "histogram" aggregation can be applied to any temporal or numeric property and produces a list of buckets describing
the repartition of values across matching documents.

#### Example

The aggregation `createDate` will return a list of buckets like so:

* `2020-01-01` to `2020-02-01`: 18 records
* `2020-02-01` to `2020-03-01`: 22 records
* `2020-03-01` to `2020-04-01`: 43 records
* etc.

### Filters aggregation

A "filters" aggregation produces a count of matching records for one or several predefined queries. This essentially
lets the user run "sub-queries" cheaply to have a better understanding of the composition of the search results.

> Note: an improvement here could be to let the user specify their own sub-queries to run, using CQL

#### Example

The aggregations `hasDownloads` and `hasMaps` are defined like so:

* `hasDownloads` returns the amount of records which have at least 1 distribution of a download type (CSV, Excel...)
* `hasMaps` returns the amount of records which have at least 1 distribution which is a map service (WMS, OGC API Map,
  ESRI Rest)...

### Spatial aggregation

> WIP

## Requirements

### 1. Advertising available aggregations

An additional `/aggregations` has to be supported at the collection level. This endpoint only supports `GET` requests.

For example, for a collection called `myOrg`, a request on

```http request
GET /collections/myOrg/aggregations
```

will return a JSON object describing the various available aggregations for that collection. For each aggregation the
following information are included:

* The identifier of the aggregation
* The type of aggregation: an aggregation can be of type `terms`, `histogram`, `spatial` or `filters`
* The maximum count of buckets returned in the _aggregations overview_
* For terms aggregations:
  * Name of the property targeted by this aggregation
  * Sort criteria: count or value (alphabetical)
  * Minimum occurrence count
  * Support for including/excluding terms
* For histogram aggregations:
  * Name of the property targeted by this aggregation
  * Type of buckets used: fixed intervals, fixed buckets count, equalized amount of records in each bucket
* For filters aggregations:
  * CQL expression used for each filter; this then lets the user apply the same filter in subsequent queries

### 2. Extending a JSON search result with an Aggregations Overview

The server might include an Aggregations Overview for any search result within a collection. For example, for a
collection `myOrg` the response to

```http request
GET /collections/myOrg/items
```

should include the following property `aggregations`. The content represents a dictionary of all aggregations available
for that collection, each containing
various buckets describing different facets of the search results.
An aggregation is identified by an identifier and contains the top number of buckets with
their count. A bucket is a number of results in the result set matching the key. A parameter `more`
indicates how many buckets were left out to keep the response size low (0 if all buckets were included in the overview).

Note: `more` can also simply have the value `true` in case the precise amount of additional buckets could not be
computed.

```json
{
  "type": "FeatureCollection",
  "aggregations": {
    "keywords": {
      "type": "terms",
      "property": "keywords",
      "buckets": [
        {
          "value": "forestry",
          "count": "202"
        },
        {
          "value": "marine",
          "count": "150"
        }
      ],
      "more": 0
    },
    "createDate": {
      "type": "histogram",
      "property": "createDate",
      "buckets": [
        {
          "min": "2010-01-01",
          "max": "2011-01-01",
          "count": 100
        },
        {
          "min": "2011-01-01",
          "max": "2012-01-01",
          "count": 220
        }
      ],
      "more": 12
    }
  },
  "features": [],
  "numberMatched": 375,
  "numberReturned": 0,
  "links": []
}
```

In some situations clients are interested only in the aggregations. In other situations the aggregations are not
required. These aspects can be controlled via additional query parameters.

| Parameter        | Explanation                                                                              |
|------------------|------------------------------------------------------------------------------------------| 
| aggregations     | default `true`; will include the aggregations overview in the response                   |
| aggregationsOnly | default `false`; returns the aggregations without search results. Similar to `&limit=0`. |

> Note: give the possibility for the user to only ask for a subset of the aggregations?

### 3. Offering the possibility to "drill-down" on a single aggregation

An additional `/aggregation/{aggregationId}` has to be supported at the collection level. This endpoint only
supports `GET` requests.

This endpoint takes in the _aggregation identifier_ as advertised in the `/aggregations` endpoint or in the overview in
the `/items` endpoint, as well as the following query parameters:

* the `limit` and `offset` parameters can be used similarly to the `/items` endpoint, but for paginating through the
  list of returned buckets
* the `q`, `bbox`, `datetime` and `filter` parameters behave the same way as for the `/items` endpoint, and let the user
  get an exhaustive list of buckets for an existing search results set
* for terms aggregations:
  * the `include` and `exclude` params accept text values including wildcards; both of these values will be used to
    either include or exclude buckets based on their associated values (note that this has to be advertised as supported
    in the `/aggregations` endpoint)

For example, for a collection called `myOrg`, a request on

```http request
GET /collections/myOrg/aggregation/keyword?exclude=*climate*&offset=100&limit=10
```

might return:

```json
{
  "property": "keyword",
  "type": "terms",
  "buckets": [
    {
      "value": "forestry",
      "count": "202"
    },
    {
      "value": "marine",
      "count": "150"
    },
    ...
    {
      "value": "landcover",
      "count": "12"
    }
  ],
  "bucketsCount": 150,
  "links": [
    {
      "rel": "next",
      "title": "The next page of buckets for this aggregation",
      "href": "https://example.org/collections/myOrg/aggregation/keyword?exclude=*climate*&offset=110&limit=10"
    },
    {
      "rel": "previous",
      "title": "The previous page of buckets for this aggregation",
      "href": "https://example.org/collections/myOrg/aggregation/keyword?exclude=*climate*&offset=90&limit=10"
    }
  ]
}
```

# Folder structure

This folder is organized as follows:

* openapi - normative OpenAPI components specified by the standard

