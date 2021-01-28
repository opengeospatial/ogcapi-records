# OGC API - Records

[OGC API standards](https://ogcapi.ogc.org/) define modular API building blocks to spatially enable Web APIs
in a consistent way. [OpenAPI](http://openapis.org) is used to define the reusable
API building blocks with responses in JSON and HTML.

The OGC API family of standards is organized by resource type. The draft OGC API - Records standard defines an API with two goals:

* Provide modern API patterns and encodings to facilitate further lowering the barrier to finding the existence of spatial resources on the Web.

* Provide metadata discovery and retrieval functionality that is comparable to that of the OGC Catalogue Service (CSW) standard.

## Overview of OGC API - Records - Part 1: Core

```
GET {root}/
```

Retrieves the landing page. The purpose of the landing page is to provide clients with a starting point for using the API. Any resource exposed through an API can be accessed by following paths or links starting from the landing page.

The landing page includes three metadata elements; title, description, and attribution. Only the title is required. These three elements describe the API as a whole. Clients can expect to encounter metadata which is more resource-specific as they follow links and paths from the landing page.

```
GET {root}/api
```

Retrieves the API definition which describes the capabilities provided by that API. This resource can be used by developers to improve their understanding of the API, by software clients to connect to the server, and by development tools to support the implementation of servers and clients.

```
GET {root}/conformance
```

Provides a list declaring the modules that are implemented by the API. These modules are referred to as Conformance Classes. The list of Conformance Classes is key to understanding and using an OGC Web API.

```
GET {root}/collections
```

Metadata describing the spatial collections available from this API.

```
GET /collections/{collectionId}
```

Metadata describing the collection which has the unique identifier {collectionid}


```
GET {root}/collections/{collectionid}/items
```

Search results based on querying the service for records satisfying 0..n query parameters.


```
GET {root}/collections/{collectionid}/items/{recordid}
```

Record of metadata which has the unique identifier {recordid}.
