
# OGC API - Records

## Overview

OGC API - Records provides discovery and access to metadata about geospatial data and services.

[OGC API standards](https://ogcapi.ogc.org) define modular API building blocks to spatially enable Web APIs in a consistent way. [OpenAPI](https://openapis.org) is used to define the reusable API building blocks.

```
GET /collections/myCatalogue/items
```

Lists all the metadata records in the catalogue.

```
GET /collections/myCatalogue/items?bbox=160.6,-55.95,-170,-25.89
```

Lists all the metadata records that describe objects in the New Zealand economic zone.

The response format is determined using standard [HTTP content negotiation](https://restfulapi.net/content-negotiation/).

Data is returned in pageable chunks, with each response containing a `next` link pointing to the next set of response records.  The core specification supports a basic set of filters roughly analogous to the [OpenSearch](https://opensearch.org) and OGC OpenSearch Geo (https://portal.ogc.org/files/?artifact_id=56866) query parameters.

```
GET /collections/myCatalogue/items/{recordId}
```

Returns a specific metadata record.

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

