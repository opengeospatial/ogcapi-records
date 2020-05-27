> :warning: The OGC API - Records specification is **still a work in progress.**  Please be aware that the specification document that is in this repository is not yet in a state that could be useful to anyone who has not been attending the bi-weekly standards working group (SWG) meetings and/or who is not actively working on the document.  The SWG is working diligently to update the specification so please refer back to this readme periodically for any status updates.
> What we think we have consensus on so far are the following:
> 1. The API will be similar to the [OGC API - Features](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html) API with some extended query capabilities.
> 2. The recommended encoding of a catalogue record will be GeoJSON to take advantage of the available tooling and make STAC alignment easier.
> 3. There will be an endpoint to retrieve the set of queryables (i.e. the properties that may be used to construct a filter).
> 4. The content model of a record will be made up of a set of "core" queryables (i.e. a set of mandatory properties that every record must have; stuff like id, type, title, modified, rights, license, etc.) and then any other properties that a domain of practice (e.g. EO, STAC, etc.) might want to add.
> 
> There have been discussions on a number of other topics too (see the [issues](https://github.com/opengeospatial/ogcapi-records/issues) on github) but nothing concrete yet.

# OGC API - Records

## Overview

OGC API - Records provides discovery and access to metadata about geospatial data and services.

```
GET /collections/myCatalogue/items
```

Lists all the metadata records in the catalogue.

```
GET /collections/myCatalogue/items?bbox=160.6,-55.95,-170,-25.89
```

Lists all the metadata records that describe objects in the New Zealand economic zone.

The response format is determined using standard [HTTP content negotiation](https://restfulapi.net/content-negotiation/).

Data is returned in pageable chunks, with each response containing a `next` link pointing to the next set of response records.  The core specification supports a basic set of filters roughly analogous to the [OpenSearch](https://opensearch.org) and OGC OpenSearch Geo (https://portal.opengeospatial.org/files/?artifact_id=56866) query parameters.

```
GET /collections/myCatalogue/items/{recordId}
```

Returns a specific metadata record.

## Using the standard

A draft of the OGC API - Records standard is available:

* T.B.D.

Those who want to just see the endpoints and responses can explore the generic
OpenAPI definition on SwaggerHub:

* T.B.D.

There have been several implementations of the draft standard, though they are
still getting up to compliance with the first draft release:

* [Implementations of the draft specification / demo services](https://github.com/opengeospatial/ogcapi-records/blob/master/implementations.md)

## Communication

Join the [mailing list](https://lists.opengeospatial.org/mailman/listinfo/ogcapi-records.swg) or [![chat at https://gitter.im/opengeospatial/ogcapi-records](https://badges.gitter.im/opengeospatial/ogcapi-records.svg)](https://gitter.im/opengeospatial/ogcapi-records)

Most all work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/ogcapi-records/issues), so browse there to get a good idea of what is happening, as well as past decisions.

## Additional Information

* [Checklist for implementers](guide/conformance_checklist.md)

Also a non-normative document, the "OGC API - Records User's Guide", is planned.

The current expectation is to have a stable version of the Core specification in 2020. We want to wait for sufficient implementation feedback, mature implementations including a test suite, results from OGC testbeds and experience with draft extensions first.

* [Charter for this SWG](OGC_API_Catalogues_SWG_Charter.adoc)
* [OGC API Records - Part 1: Core, Editor's Draft](https://github.com/opengeospatial/ogcapi-records/blob/master/core/outline.adoc)

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership and ISO/TC 211, shall be incorporated into OGC and ISO/TC 211 standards documents and that all copyright and intellectual property shall be vested to the OGC.

The OGC API Records Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/ogcapi-records/issues)
* [Proposing changes](https://github.com/opengeospatial/ogcapi-records/wiki/Propose-a-change-to-a-draft-of-a-CAT40-specification-document)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/ogcapi-records/master/LICENSE)
