> :warning: The OGC API - Records specification is **still a work in progress.**  Please be aware that the specification document that is in this repository is not yet in a state that could be useful to anyone who has not been attending the bi-weekly standards working group (SWG) meetings and/or who is not actively working on the document.  The SWG is working diligently to update the specification so please refer back to this readme periodically for any status updates.
> What we think we have consensus on so far are the following:
> 1. The API will be similar to the [OGC API - Features](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html) API with some extended query capabilities.
> 2. The recommended encoding of a catalogue record will be GeoJSON to take advantage of the available tooling and make STAC alignment easier.
> 3. There will be an endpoint to retrieve the set of queryables (i.e. the properties that may be used to construct a filter).
> 4. The content model of a record will be made up of a set of "core" queryables (i.e. a set of mandatory properties that every record must have; stuff like id, type, title, modified, rights, license, etc.) and then any other properties that a domain of practice (e.g. EO, STAC, etc.) might want to add.
> 
> There have been discussions on a number of other topics too (see the [issues](https://github.com/opengeospatial/ogcapi-records/issues) on github) but nothing concrete yet.

# OGC API - Records - Part 1: Core

This folder contains the content for the OGC API - Records - Part 1: Core standard.

The repo is organized as follows:

* standard - the main standard document content
  - organized in multiple sections and directories
* openapi - normative OpenAPI components specified by the standard
* examples - JSON and XML examples
