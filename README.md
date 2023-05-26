# OGC API - Records

## Overview

[OGC API standards](https://ogcapi.ogc.org) define modular API building blocks to spatially enable Web APIs in a consistent way. [OpenAPI](https://openapis.org) is used to define the reusable API building blocks.

OGC API - Records provides discovery and access to metadata about geospatial resources (e.g. data, services, ML models, etc.).  Having found a record describing a resource, binding information contained therein allows the discovered resources to be accessed.

The OGC API - Records specification being developed in this repository defines three main **building blocks**:

* Record
* Collections
* Records API

## The Record building block

The _**Record**_ is the atomic unit of information in a catalogue.

A record provides a description (i.e. metadata) about a resource that the provider of the resource wishes to make discoverable.

The record building block defines the core schema of a catalogue record.  It includes a small number of properties that are common across all resource types.  The following table lists the core set of record properties (called queryables):

|Queryables |Requirement |Description 
|-----------|------------|-----------------------------------
|recordId |**M** |A unique record identifier assigned by the server.
|conformsTo |O |A list of identifiers indicating that the record conforms to one or more extensionsl  Ideally, the requirements of each listed extension is formally published.
|created |O |The date this record was created in the server.
|updated |O |The most recent date on which this record was changed.
|language |O |The natural language used for textual values (i.e. titles, descriptions, etc) of this record.
|languages |O |The list of languages in which this record can be requested.
|time |**M** |A characteristic temporal instance or interval associated with the resource; can be _null_ if not known or applicable.
|geometry |**M** |A characteristic spatial extent associated with the resource; can be _null_ if not known or applicable.
|type |**M** |The nature or genre of the resource described by this record.
|title |**M** |A human-readable name given to the resource described by this record.
|description |O |A free-text description of the resource.
|keywords |O |A list of free-form keywords or tags associated with the resource.
|resourceLanguages |O |A list of languages in which the resource can be requested.
|externalIds |O |A list of identifiers for the resource assigned by one or more external entities.
|themes |O |A knowledge organization system used to classify the resource.
|formats |O |A list of available distributions for the resource.
|contacts |O |A list of entities to contact about the resource.
|license |O |A legal document under which the resource is made available.
|rights |O |A statement that concerns all rights not addressed by the license such as a copyright statement.
|links |O |A list of links including links for accessing the resource (e.g. download link, access link, etc.) in one of the supported distribution formats, links to other resources associated with this resource and links for navigating the API (e.g. prev, next, alternate, etc.). See [link schema.](https://raw.githubusercontent.com/opengeospatial/ogcapi-records/master/core/openapi/schemas/common/link.yaml).

It is anticipated that the schema of a record will be extended to describe specific resource types (e.g. data sets, earth observation products, services, machine models, etc.) and also extended by information communities wishing to enrich the information content of the record to suit their needs.  The specification does not mandate a specific encoding for a record but conformance classes are defined for encoding records as GeoJSON feature and HTML.

The following is an example of a catalogue record encoded as GeoJSON:

```
    {
      "id": "urn:uuid:dc9b6d52-932a-11ea-ad6f-823cf448c401",
      "type": "Feature",
      "time": null,
      "geometry": {
        "type": "Polygon",
        "coordinates": [ [ [ -117.35, 32.58 ], [ -117.35, 33.45 ],
                           [ -116.21, 33.45 ], [ -116.21, 32.58 ],
                           [ -117.35, 32.58 ] ] ]
      },
      "properties": {
        "updated": "2020-05-10T21:58:08Z",
        "type": "vector digital data",
        "title": "AG_PRESERVE",
        "description": "Agriculture Preserve Lands\nThe California Land Conservation Act, better known as the Williamson Act, has been the state's premier agricultural land protection program since its enactment in 1965. More than 16 million of the state's 30 million acres of farm and ranch land are currently protected under the Williamson Act. \n\nThe California Legislature passed the Williamson Act in 1965 to preserve agricultural and open space lands by discouraging premature and unnecessary conversion to urban uses. The Act creates an arrangement whereby private landowners contract with counties and cities to voluntarily restrict their land to agricultural and compatible open-space uses. The vehicle for these agreements is a rolling term 10-year contract (i.e., unless either party files a \"notice of nonrenewal,\" the contract is automatically renewed for an additional year.). In return, restricted parcels are assessed for property tax purposes at a rate consistent with their actual use, rather then potential market value.\nAn agricultural preserve defines the boundary of an area within which a city or county will enter into contracts with landowners. The boundary is designated by resolution of the board of supervisors (board) or city council (council) having jurisdiction. Only land located within an agricultural preserve is eligible for a Williamson Act contract. Preserves are regulated by rules and restrictions designated in the resolution to ensure that the land within the preserve is maintained for agricultural or open space use.",
        "keywords": [
          "Agriculture Presever",
          "Preserve Lands",
          "Ag Preserve"
        ],
        "language": "en-US",
        "externalIds": [ "urn:uuid:dc9b6d52-932a-11ea-ad6f-823cf448c401" ],
        "formats": [
          "vector digital data"
        ]
      },
      "links": [
        {
          "href": "\\\\lueg-gis\\data\\dplu-projects\\20050909_williamson_ag\\shapefiles\\Williamson_agpreserve.shp",
          "rel": "enclosure"
          "type": "x-gis/x-shape"
        }.
        {
          "href": "https://demo.pycsw.org/gisdata/collections/metadata:main/items/urn:uuid:dc9b6d52-932a-11ea-ad6f-823cf448c401?f=json",
          "rel": "self",
          "type": "application/geo+json"
        },
        {
          "href": "https://demo.pycsw.org/gisdata/collections/metadata:main/items/urn:uuid:dc9b6d52-932a-11ea-ad6f-823cf448c401?f=html",
          "rel": "alternate",
          "type": "text/html"
        }
      ]
    }
```

## The Collection building block

The Collection building block is used to describe a collection of resources.  This can be a collection of related records (also called a catalogue) but it can also be a collection of any other type of resource (e.g. feature, coverage, etc.).

The `Collection` building block [extends](https://raw.githubusercontent.com/opengeospatial/ogcapi-records/master/core/openapi/schemas/extendedCollectionInfo.yaml) the information defined for a collection by [OGC API - Common - Part 2: Geospatial Data](http://docs.opengeospatial.org/DRAFTS/20-024.html#collection-description) and [OGC API - Features - Part 1: Core](http://schemas.opengis.net/ogcapi/features/part1/1.0/openapi/schemas/collection.yaml) to:

* include additional metadata to enhanced the description of a collection 
* and, to provide links for accessing the items of the collection.

The following is an example of a searchable record collection encoded as JSON:

```
{
  "id": "metadata:main",
  "title": "pycsw Geospatial Catalogue gisdata demo",
  "description": "pycsw is an OARec and OGC CSW server implementation written in Python",
  "links": [
    {
      "rel": "self",
      "type": "application/json",
      "title": "This document as JSON",
      "href": "https://demo.pycsw.org/gisdata/collections/metadata:main?f=json",
      "hreflang": "en-US"
    },
    {
      "rel": "alternate",
      "type": "text/html",
      "title": "This document as HTML",
      "href": "https://demo.pycsw.org/gisdata/collections/metadata:main?f=html",
      "hreflang": "en-US"
    },
    {
       "rel": "search",
       "href": "https://demo.pycsw.org/gisdata/collections/metadata:main/items"
    }
  ],
  "itemType": "record",
  "crs": "http://www.opengis.net/def/crs/OGC/1.3/CRS84",
  "type": "Collection",
  "keywords": [
     "Catalogue","word2","word3","Ag Preserve"
  ],
  "language": "en-US",
  "updated": "2019-10-10T15:45:19Z",
  "publisher": {
     "individualName": "Joe Smith",
     "organizationName": "pygeoapi",
     "positionName": "developer",
     "contactInfo": {
       "phone": "+1555555555",
       "email": {
         "work": "joesmith@pygeoapi.io"
       }
     }
  },
  "license": "https://creativecommons.org/licenses/by/4.0/legalcode"
}

<<This is example is still being revised.>>
```

NOTE: In OGC API - Features and OGC API - Common, the link relation `items` is used to point to a searchable endpoint for accessing the resources of a collections.  This endpoint should, more correctly, use the IANA link relation `search` since the `/items` endpoint is really a search endpoint returnings subsets of resource depending to query parameters specified at the endpoint.

The following is an example of a crawlable record collection encoded as JSON.  In this case, it is a catalogue of other catalogues of RADARSAT Earth observation products.

```
{
  "id": "radarsat-1",
  "title": "RADARSAT-1 Open Data",
  "description": "Launched in November 1995, RADARSAT-1 provided Canada and the world with an operational radar satellite system capable of timely delivery of large amounts of data. RADARSAT-1 used a synthetic aperture radar (SAR) sensor to image the Earth at a single microwave frequency of 5.3 GHz, in the C band (wavelength of 5.6 cm). This was a Canadian-led project involving the Canadian federal government, the Canadian provinces, the United States, and the private sector. RADARSAT-1 reached end of service on March 29, 2013. In order to download RADARSAT-1 datasets, credentials for the Earth Observation Data Management System are required.",
  "extent": {
    "spatial": [ -180, -90, 180, 90 ],
    "temporal": [ "1995-11-04T14:22:00Z", "2013-03-29T00:00:00Z" ]
  },
  "itemType": "collection",
  "keywords": [ "sar", "eo", "radar", "radarsat", "canada" ],
  "language": "en-CA",
  "publisher": {
    "organizationName": "Canadian Space Agency (CSA)",
    "contactInfo": {
      "onlineResource": {
        "href": "http://www.asc-csa.gc.ca/eng/satellites/radarsat1/Default.asp"
      }
    },
    "role": {
      "name": "producer"
    }
  },
  "license": "proprietary",
  "properties": {
    "sar:platform": "RADARSAT-1",
    "sar:constellation": "RADARSAT",
    "sar:instrument": "C-SAR",
    "sar:frequency_band": "C",
    "sar:center_wavelength": 5.6,
    "sar:center_frequency": 5.3,
    "sar:polarization": [ "HH" ],
    "sar:observation_direction": "right"
  },
  "links": [
    {
      "href": "https://open.canada.ca/en/open-government-licence-canada",
      "rel": "license",
      "type": "text/html",
      "title": "license"
    },
    {
      "rel": "item",
      "href": "slc/collection.json"
    },
    {
      "rel": "item",
      "href": "raw/collection.json"
    },
    {
      "rel": "item",
      "href": "sgf/collection.json"
    },
    {
      "rel": "item",
      "href": "sgx/collection.json"
    },
    {
      "rel": "item",
      "href": "scn/collection.json"
    },
    {
      "rel": "item",
      "href": "scw/collection.json"
    }
  ]
}
```

## The Records API

The OGC API - Records specification defines a core catalogue access and search API by extending OGC API - Common - Part 2: Geospatial Data and the OGC API - Features - Part 1: Core APIs.

OGC API - Common specifies a well-defined access path to information about collections (i.e. `/collections`).  OGC API - Features specifies a well-defined access path to the records (i.e. `/collections/{collectionId}/items`) of a catalogue (i.e. a record collection).  OGC API - Records extended each of these endpoints with additional query parameters to enable catalogue search capabilities.

In the first case this allows deployments with a large number of collections to be searched as a sort of mini-catalogues of the deployment's resource collections (i.e. features, coverages, etc.). 

In the latter case, this allows collections of records (i.e. catalogues) to be searched.

The search capabilities of the Records API are organized into various levels of complexity starting from simple spatial, temporal, keyword and type search predicates (i.e. `bbox=`, `datetime=`, `q=`, `type=`) that can be combined using a logical `AND` all the way up to a full blown predicate language (based on OGC API - Features - Part 3: Filtering and the Common Query Language (CQL)), that supports complex filter expressions of logically connected query predicates.

## Deployment patterns

There are a number of ways that records can be deployed as a "collection of records" or a catalogue.  The OGC API - Records specification envisions three deployment patterns using the building blocks described above:

* a catalogue deployed as a crawlable collection of records
* a catalogue deployed as a searchable endpoint(s)
* a local resources catalogue

:warning: In STAC the terms _static_ and _dynamic_ are used to describe these deployment patterns.  However, a _static_ catalogue is not really static since additional records can be added at any time.  As a result, it was decided to try some different, more descriptive, terminology.  The terms _crawlable_ and _searchable_ have been proposed and are used in this README and in the OGC API - Records specification.  Other proposed terms include _basic_ and _searchable_.  The SWG decided to try out _crawlable_ and _searchable_ for now but these terms are subject to change based on feedback.

### Crawlable Catalogue

The crawlable catalogue deployment pattern involves creating a file that contains a record that describes each discoverable resource.  Each file (i.e. record) is then deployed to some web accessible location (e.g. S3 bucket, web accessible directory, etc.), usually co-located with the resource the record is describing.  Sets of related records are identified by creating a _Record collection_ object, another file also deployed to some web accessible location.  The record collection object provides metadata about this collection of records (i.e. about this catalogue) and also includes hypermedia controls (i.e. links, one per record) that allow navigation to the records of the collection.

This deployment pattern imposes a very low implementation burden because it relies on HTTP to do most of the work of accessing the records of a catalogue.  This makes it easy to deploy and to navigate to the records using a browser or by search engine crawlers.  However, complex searches using logically connect spatio-temporal and/or scalar predicates are not easily supported by this deployment pattern.

![crawlable catalogue](images/crawlable_catalogue_example.png)

### Searchable catalogue

As is the case for a crawlable catalogue, in a searchable catalogue deployment, records are created to describe discoverable resources.  Collections of these records, rather than being deployed into web-space, are typically (but not necessarily) stored in some back end data management system such as a NO-SQL database or an RDBMS and access to the records is provided through the Records API.  The API also makes use of hypermedia controls (i.e. links) that allow navigation to records in a manner similar to that in the crawlable deployment case.  Information about the catalogue (i.e. the record collection) itself is also accessible through the API.  

Unlike the crawlable deployment case, the API also provides search capability that allows subsets of records to be identified and accessed based on client-supplied criteria such as a bounding box, a data range or a free text search.  

The following examples illustrate accessing the catalogue through the Records API:

```
GET /collections/DataCatalogue
```

Get the description or metadata about a catalogue with the identifier `DataCatalogue` (i.e. the `DataCatalogue` collection or records).

```
GET /collections/DataCatalogue/items
```

Gets the first page of records from the `DataCatalogue` catalogue.

```
GET /collections/DataCatalogue/items/rid001
```

Fetches a specific catalogue record (with identifier `rid001`).

```
GET /collections/DataCatalogue/items?bbox=160.6,-55.95,-170,-25.89
```

Searches the catalogue for records that describe resources in the New Zealand economic zone.

```
GET /collections/DataCatalogue/items?34.5322,18.9328,41.6715,27.0956&dattime=2021-07-15/2021-08-08
```

Searches the catalogue for records that describe resources from Greece between July 15th, 2021 and August 8th, 2021.

```
GET /collections/DataCatalogue/items?34.5322,18.9328,41.6715,27.0956&dattime=2021-07-15/2021-08-08&q=burn,fire
```

Searches the catalogue for records that describe resources from Greece between July 15th, 2021 and August 8th, 2021 and that contain the keywords `burn` and `fire`.

In all search cases, the response format is determined using standard [HTTP content negotiation](https://restfulapi.net/content-negotiation/).

Records are returned in pageable chunks, with each response containing a `next` link pointing to the next set of response records.  The core API specification supports a basic set of filters roughly analogous to the [OpenSearch](https://github.com/dewitt/opensearch) and OGC OpenSearch Geo (https://portal.opengeospatial.org/files/?artifact_id=56866) query parameters.


### Local resources catalogue

The OGC API resource tree has a number of resource endpoints that represent lists of resources.  Some example endpoints include:

* `/collections` - list of collections offered by an OGC API
* `/processes` - list of processes offered by an OGC API
* `/collections/{collectionId}/scenes` - list of source scenes for a coverage or map

The OGC API - Records building blocks can be used to enable catalogue-like queries at these endpoints.  This is especially useful if the endpoint can potentially have a very large number of sub-resources as might be the case at the `/collections` endpoint.  For example, the following request searches for collections whose spatial extent intersects a specified bounding box and whose temporal extent intersects a specified time period:

```
GET /collections?bbox=-69.64,37.76,-56.12,46.63&datetime=2020-01-11T00:00:00/2020-01-12T00:00:00
```

Only collections that satisfy that specified predicates are included in the response.

### OpenSearch

The OpenSearch protocol defines an XML description document describing how to request search results from a service. If these search results are encoded in ATOM or RSS, this allows results from multiple services to be combined.  It is still used extensively by some communities within OGC and was originally part of Part 1.  It has, recently, been moved into own part, Part 2.  This was primarily done because of the current status of OpenSearch.

The OpenSearch protocol used by OGC API - Records is based on a protocol that was launched in 2005 by A9.com, an Amazon subsidiary.  In 2021, Amazon.com launched the open source OpenSearch search engine project, unrelated to the OpenSearch launched by A9.com aside from repurposing the name.  The two projects will continue to independently co-exist, though the search protocol (now hosted [here](https://github.com/dewitt/opensearch)) has largely remained stable and unchanged for over ten years, with no significant updates expected on the horizon.  Neither of these two efforts is related to the Open Search Foundation project found [here](https://opensearchfoundation.org/).

Because of this shift in status of OpenSearch issolating it in its part of the OGC API - Records suite of standards would allow the related conformance class(es) to be easilt deprecated or renamed in the future.  The work for this part, Part 2, is being carried out [here](https://github.com/opengeospatial/ogcapi-records/tree/master/extensions/OpenSearch).

## Using the standard

A draft of the **OGC API - Records - Part 1: Core** standard is available:

* [HTML version](https://docs.ogc.org/DRAFTS/20-004.html)
* [PDF version](https://docs.ogc.org/DRAFTS/20-004.pdf)

Draft(s) are built daily based on the configuration contained in the [asciidoctor.json](https://github.com/opengeospatial/ogcapi-records/blob/master/asciidoctor.json) file.

Those who want to just see the endpoints and responses can explore the generic
OpenAPI definition on SwaggerHub:

* T.B.D.

There have been several implementations of the draft standard, though they are
against different versions of the evolving draft:

* [Implementations of the draft specification / demo services](https://github.com/opengeospatial/ogcapi-records/blob/master/implementations.md)

## Communication

Join the [mailing list](https://lists.ogc.org/mailman/listinfo/ogcapi-records.swg) or [![chat at https://gitter.im/opengeospatial/ogcapi-records](https://badges.gitter.im/opengeospatial/ogcapi-records.svg)](https://gitter.im/opengeospatial/ogcapi-records)

Most all work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/ogcapi-records/issues), so browse there to get a good idea of what is happening, as well as past decisions.

## Additional Information

A non-normative document, the "OGC API - Records User's Guide", is planned.

The current expectation is to have a stable version of the Core specification in 2021. We want to wait for sufficient implementation feedback, mature implementations including a test suite, results from OGC testbeds and experience with draft extensions first.

* [Charter for this SWG](OGC_API_Catalogues_SWG_Charter.adoc)

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership and ISO/TC 211, shall be incorporated into OGC and ISO/TC 211 standards documents and that all copyright and intellectual property shall be vested to the OGC.

The OGC API - Records Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/ogcapi-records/issues)
* [Proposing changes](https://github.com/opengeospatial/ogcapi-records/wiki/Propose-a-change-to-a-draft-of-a-CAT40-specification-document)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/ogcapi-records/master/LICENSE)

Pull Requests from contributors are welcomed. However, please note that by sending a Pull Request or Commit to this GitHub repository, you are agreeing to the terms in the Observer Agreement https://portal.ogc.org/files/?artifact_id=92169

