# OGC API - Records - Term Aggregations

This folder contains the content for the standard extension OGC API - Records - Term Aggregations.

# Overview

This extensions enables the capability to include Term Aggregations in the items (records) response. These aggregations can be used by clients to enable [faceted search](https://en.wikipedia.org/wiki/Faceted_search).

Various backends support faceted search. Examples are [Elastic](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-terms-aggregation.html), [SOLR](https://solr.apache.org/guide/8_8/json-facet-api.html) and limited support in [PostGres](https://akorotkov.github.io/blog/2016/06/17/faceted-search/), [Oracle](https://blogs.oracle.com/apex/apex-192-faceted-search).

Facet statistics are also interesting to give an overview of the spatio temporal distribution of items in a (part of a) collection.

## Extending a json search result with Term Aggregations

The server includes the Term Aggregations for any search result within a collection. For example, for a collection `cat` the response to

```
GET /collections/cat/items
```

may include the following property `aggregations`. The content represents an array of aggregated terms.
A aggregation is identified by a collection property name and contains the top number of buckets with
their count. A bucket is a number of results in the resultset matching the key. A parameter `next` 
indicates if there are potentially more buckets to be retrieved. 

```
{
  "type": "FeatureCollection",
  "aggregations": [
    {
      "property": "keyword", 
      "buckets": [
        {
          "key": "forestry",
          "count": "202"
        },
        {
          "key": "marine",
          "count": "150"
        }
      ],
      "next": "0"    
    }
  ],
  features": [],
  "numberMatched": 375,
  "numberReturned": 0,
  "links": []
}
```

## Numerical, spatial and temporal buckets

For dynamic values a range of buckets can be returned defined by a min, max or bbox value. 

```
{
  "aggregations": [
    "key": "scale", 
    "buckets": [
      {
        "key": "0.1 - 0.001",
        "count": "175"
      },
      {
        "key": "0.001 - 0.00001",
        "count": "120"
      }
    ],
    "next": "2"
    },
    {
      "key": "date",
      "buckets": [
        {
          "key": "1990/01/01 - 1995/01/01",
          "count": "12"
        },
        {
          "key": "1995/01/01 - 2000/01/01",
          "count": "340"
        },
        {
          "key": "2000/01/01 - 2005/01/01",
          "count": "1200"
        }
      ],
      "next": "5"
    }  
  ]
}
```

In the case of geometries this is a boundingbox in WGS84 defined by two points. 

```
{
  "aggregations": [
    {
      "key": "bbox",
      "buckets": [
        {
          "key": "0,0 5,5",
          "count": 175
        },
        {
          "key": "0,5 5,10",
          "count": 120
        },
        {
          "key": "10,5 15,10",
          "count": 77
        }
      ],
      "next": 7
    }
  ]
}
```

## Interacting with aggregations

In some situations clients are interested only in the aggregations. In other situations the aggregations are not required. These aspects can be controlled via additional query parameters.

| Parameter | Explanation |
| -- | -- | 
| aggregationsOnly | default `false`, Returns the aggregations without search results. Similar to `&limit=0`. |
| includeAggregations | default `true` (if available), can be set to `false` |

# Folder structure

This folder is organized as follows:

* openapi - normative OpenAPI components specified by the standard

