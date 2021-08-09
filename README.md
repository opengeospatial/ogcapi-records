# OGC API - Records

## Overview

[OGC API standards](https://ogcapi.ogc.org) define modular API building blocks to spatially enable Web APIs in a consistent way. [OpenAPI](http://openapis.org) is used to define the reusable API building blocks.

OGC API - Records provides discovery and access to metadata about geospatial resources (e.g. data, services, ML models, etc.).  Having found a record describing a resource, binding information contained therein allows the discovered resources to be accessed.

The OGC API - Records specification defines three main building blocks:

* Record
* Record collection
* Records API

## The Record building block

The _**Record**_ is the atomic unit of information in a catalogue.  The record building block defines the core schema of a catalogue record.  It includes a small number of properties that are common across all resource types.  It is anticipated that the schema of a record will be extended to describe specific resource types (e.g. data sets, earth observation products, services, machine models, etc.) and also extended by information communities wishing to enrich the information content of the record to suit their needs.  The specification does not mandate a specific encoding for a record but conformance classes are defined for encoding records as GeoJSON feature and HTML.

The following is an example of a catalogue record encoded as GeoJSON:

[source,JSON]
```
    {
      "id": "urn:uuid:dc9b6d52-932a-11ea-ad6f-823cf448c401",
      "type": "Feature",
      "geometry": {
        "type": "Polygon",
        "coordinates": [ [ [ -117.35, 32.58 ], [ -117.35, 33.45 ],
                           [ -116.21, 33.45 ], [ -116.21, 32.58 ],
                           [ -117.35, 32.58 ] ] ]
      },
      "properties": {
        "recordUpdated": "2020-05-10T21:58:08Z",
        "type": "vector digital data",
        "title": "AG_PRESERVE",
        "description": "Agriculture Preserve Lands\nThe California Land Conservation Act, better known as the Williamson Act, has been the state's premier agricultural land protection program since its enactment in 1965. More than 16 million of the state's 30 million acres of farm and ranch land are currently protected under the Williamson Act. \n\nThe California Legislature passed the Williamson Act in 1965 to preserve agricultural and open space lands by discouraging premature and unnecessary conversion to urban uses. The Act creates an arrangement whereby private landowners contract with counties and cities to voluntarily restrict their land to agricultural and compatible open-space uses. The vehicle for these agreements is a rolling term 10-year contract (i.e., unless either party files a \"notice of nonrenewal,\" the contract is automatically renewed for an additional year.). In return, restricted parcels are assessed for property tax purposes at a rate consistent with their actual use, rather then potential market value.\nAn agricultural preserve defines the boundary of an area within which a city or county will enter into contracts with landowners. The boundary is designated by resolution of the board of supervisors (board) or city council (council) having jurisdiction. Only land located within an agricultural preserve is eligible for a Williamson Act contract. Preserves are regulated by rules and restrictions designated in the resolution to ensure that the land within the preserve is maintained for agricultural or open space use.",
        "keywords": [
          "Agriculture Presever",
          "Preserve Lands",
          "Ag Preserve"
        ],
        "language": "en-US",
        "externalId": "urn:uuid:dc9b6d52-932a-11ea-ad6f-823cf448c401",
        "formats": [
          "vector digital data"
        ],
        "extent": {
          "spatial": {
            "bbox": [ [ -117.35, 32.58, -116.21, 33.45 ] ],
            "crs": "http://www.opengis.net/def/crs/OGC/1.3/CRS84"
          }
        },
        "associations": [
          {
            "href": "\\\\lueg-gis\\data\\dplu-projects\\20050909_williamson_ag\\shapefiles\\Williamson_agpreserve.shp",
            "rel": "enclosure"
            "type": "x-gis/x-shape"
          }
        ]
      },
      "links": [
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
## The Record collection building block

A catalogue is a collection of records.  The `Record collection` building block extends the information defined for a collection by http://docs.opengeospatial.org/DRAFTS/20-024.html#collection-description(OGC API - Common - Part 2: Geospatial Data) and http://schemas.opengis.net/ogcapi/features/part1/1.0/openapi/schemas/collection.yaml(OGC API - Features - Part 1: Core) to:

* include additional metadata for describing a catalogue (i.e. collection of records)
* and to provide links for accessing the records of the collection

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
     "individual-name": "Joe Smith",
     "organizationName": "pyGeoAPI",
     "positionName": "developer",
     "contactInfo": {
       "phone": "+1555555555",
       "email": {
         "work": "joesmith@pygeoapi.org"
       }
     }
  },
  "license": "https://creativecommons.org/licenses/by/4.0/legalcode"
}
```

```
Add an example of a collection object accessed through an API.
```

## The Records API

The OGC API - Records specification defines a core access and search API by extending the OGC API - Features - Part 1: Core specification.

OGC API - Features specifies well-defined access paths to information about the collection (i.e. the catalogue) and to the records of the collection.  The Features API also defines a basic search capability that is extended by the Records API to allow subsets of records to be identified and accesses based on client-supplied search criteria such as a bounding box, a data range or a free text search.

The search capability of the Records API is organized into various levels of complexity starting from simple spatial, temporal, keyword and type search predicates (i.e. `bbox=`, `datetime=`, `q=`, `type=`) that can be combined using a logical `AND` all the way up to a full blown predicate language (based on OGC API - Features - Part 3: Filtering and the Common Query Language (CQL)), that supports complex filter expressions of logically connected query predicates.

## Deployment patterns

There are a number of ways that records can be deployed as a "collection of records" or a catalogue.  The OGC API Records specification envisions two deployment patterns using the building blocks described above:

* a catalogue deployed as a static collection of records
* a catalogue deployed as a searchable endpoint(s)

### Static Catalogue

The static deployment pattern involves creating a record as a file to describe each discoverable resource.  Each record is then deployed to some web accessible location (e.g. S3 bucket, web accessible directory, etc.), probably co-located with the resource the record is describing.  Sets of related records are identified by creating a _Record collection_ object, another file deployed to some web accessible location.  The record collection object provides metadata about this collection of records (i.e. about this catalogue) and also includes hypermedia controls (i.e. links, one per record) that allow navigation to the records of the collection.

This deployment pattern imposes a very low implementation burden because it relies on HTTP to do most of the work of accessing the records of a catalogue.  This makes it easy to deploy and to navigate to the records using a browser or by search engine crawlers.  However, complex searches using logically connect spatio-temporal and/or scalar predicates are not easily supported by this deployment pattern.

```
add an image illustrating a static catalogue
```

### Searchable catalogue

As is the case for a static catalogue, in a searchable catalogue deployment, records are created to describe discoverable resources.  Collections of these records, rather than being deployed into web-space, are typically (but not necessarily) stored in some back end data management system such as a NO-SQL database or an RDBMS and access to the records is provided through the Records API.  The API also makes use of hypermedia controls (i.e. links) that allow navigation to records in a manner similar to that in the static deployment case.  Information about the catalogue (i.e. the record collection) itself is also accessible through the API.  

Unlike the static deployment case, the API also provides search capability that allows subsets of records to be identified and accessed based on client-supplied criteria such as a bounding box, a data range or a free text search.  

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

Records are returned in pageable chunks, with each response containing a `next` link pointing to the next set of response records.  The core API specification supports a basic set of filters roughly analogous to the [OpenSearch](https://opensearch.org) and OGC OpenSearch Geo (https://portal.opengeospatial.org/files/?artifact_id=56866) query parameters.

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

The OGC API Records Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/ogcapi-records/issues)
* [Proposing changes](https://github.com/opengeospatial/ogcapi-records/wiki/Propose-a-change-to-a-draft-of-a-CAT40-specification-document)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/ogcapi-records/master/LICENSE)

Pull Requests from contributors are welcomed. However, please note that by sending a Pull Request or Commit to this GitHub repository, you are agreeing to the terms in the Observer Agreement https://portal.ogc.org/files/?artifact_id=92169
