# OGC API - Records - Facets

This folder contains the content for the standard extension OGC API - Records - Facets.

# Overview

This extension aggregates the items (records) in buckets and provides a number associated to each bucket. Each of the related buckets are grouped into a facet enabling [faceted search](https://en.wikipedia.org/wiki/Faceted_search).

Various backends support faceted search. Examples are [Elastic](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-terms-aggregation.html), [SOLR](https://solr.apache.org/guide/8_8/json-facet-api.html) and limited support in [PostGres](https://akorotkov.github.io/blog/2016/06/17/faceted-search/), [Oracle](https://blogs.oracle.com/apex/apex-192-faceted-search).

## Definition of a Facet

The word _Facet_ refers here to a high-level piece of information that is computed over a set of records in a
collection.

A facet can be of several types:

### Terms facet

A `terms` facet can be applied to any text property and produces a list of values appearing for a specific
property across all matching records, as well as the count of records containing each value.

#### Example

A terms facet based on `keyword` countries might return a list of buckets like so:

* `Greece` (24 records)
* `Germany` (12 records)
* `England` (5 records)
* etc.

### Histogram facet

A `histogram` facet can be applied to any temporal or numeric property to distribute item values over ranges or intervals.

#### Example

The facet `createDate` will return a list of buckets like so:

* `2020-01-01` to `2020-02-01`: 18 records
* `2020-02-01` to `2020-03-01`: 22 records
* `2020-03-01` to `2020-04-01`: 43 records

or
* `2020`: 18 records
* `2021`: 22 records
* `2022`: 43 records
* etc.

### Filters facets

A `filters` facets produces a count of matching records for one or several predefined queries. This essentially
lets the user run "sub-queries" cheaply to have a better understanding of the composition of the search results.

#### Example

The facet `hasDownloads` will return the amount of records which have at least 1 distribution of a download type (CSV, Excel...):

`hasDownloads`
* 'CSV, Excel, ...' : 2051 records
* 'None' : 351 records


## Requirements

### 1. Advertising available facets

An additional `/facets` entrypoint (similar to `/queryables`)has to be supported at the collection level. This endpoint only supports `GET` requests.

For example, for a collection called `myOrg`, a request on

Note
```http request
GET /collections/myOrg/facets
```

will return a JSON object describing the various available facets for that collection. For each facet the
following information are included:

* The identifier of the facet
* The type of facet: a facet can be of type `terms`, `histogram` or `filters`
* The maximum count of buckets returned in the _facets overview_
* For terms facets:
  * Name of the property targeted by this facet
  * Sort criteria: count or value (alphabetical)
  * Minimum occurrence count
  * Support for including/excluding terms
* For histogram facet:
  * Name of the property targeted by this facet
  * Type of buckets used: fixed intervals, fixed buckets count, equalized amount of records in each bucket
* For filters facets:
  * CQL expression used for each filter; this then lets the user apply the same filter in subsequent queries

> **Note** that all the `facettables` attributes must be `queryables`

Example:

```json
{
  "type": "object",
  "title": "Observations",
  "defaultCount": 10,
  "properties": {
    "date": {
      "type": "histogram"
    },
    "organization": {
      "type": "terms"
    },
    "created": {
      "type": "histogram"
    },
    "format": {
      "type": "terms"
    },
    "usage": {
      "type": "filter",
      "view": "link.type = 'wms'",
      "download": "link.type = 'wfs'"
    }
  },
  "$schema": "http://json-schema.org/draft/2019-09/schema"
}
```
### 2. Extending queryables response

The queryable response will advertize that an attribute is facettable or not, to eventually skip the `/facets` request.

eg.
```json
{
  "properties": {
    "organization": {
      "title": "organization",
      "type": "string",
      "facets": true
    }
  }
}
```
### 3. Extending a JSON search result with a Facet Overview

The server might include a facet Overview for any search result within a collection. For example, for a collection `myOrg` the response to

```http request
GET /collections/myOrg/items
```

should include the following property `facets`. The content represents a dictionary of all facets available
for that collection, each containing
various buckets describing different facets of the search results.
A facet is identified by an identifier and contains the top number of buckets with
their count. A bucket is a number of results in the result set matching the key. A parameter `more`
indicates how many buckets were left out to keep the response size low (0 if all buckets were included in the overview).

Note: `more` can also simply have the value `true` in case the precise amount of additional buckets could not be
computed.

```json
{
  "type": "FeatureCollection",
  "facets": {
    "keywords": {
      "type": "terms",
      "property": "keyword",
      "buckets": [
        {
          "value": "Greece",
          "count": "202"
        },
        {
          "value": "Germany",
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

In some situations clients are interested only in the facets. In that case, they can use the `facets` parameter with `&limit=0`.

### Examples
```
GET /collections/myOrg/items?q=&facets=keywords:20:value_asc,date:quantile:4,update:year.month,usage
```

# Folder structure

This folder is organized as follows:

* openapi - normative OpenAPI components specified by the standard

