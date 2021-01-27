> :warning: The OGC API - Records specification is **still a work in progress.**  Please be aware that the specification document that is in this repository is not yet in a state that could be useful to anyone who has not been attending the bi-weekly standards working group (SWG) meetings and/or who is not actively working on the document.  The SWG is working diligently to update the specification so please refer back to this readme periodically for any status updates.
> What we think we have consensus on so far are the following:
> 1. The API will be similar to the [OGC API - Features](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html) API with some extended query capabilities.
> 2. The recommended encoding of a catalogue record will be GeoJSON to take advantage of the available tooling and make STAC alignment easier.
> 3. There will be an endpoint to retrieve the set of queryables (i.e. the properties that may be used to construct a filter).
> 4. The content model of a record will be made up of a set of "core" queryables (i.e. a set of mandatory properties that every record must have; stuff like id, type, title, updated, rights, license, etc.) and then any other properties that a domain of practice (e.g. EO, STAC, etc.) might want to add.
> 
> There have been discussions on a number of other topics too (see the [issues](https://github.com/opengeospatial/ogcapi-records/issues) on github) but nothing concrete yet.

# OGC API - Records Specification

This directory contains the OGC API - Records Specification. This specification, working with the parallel OGC API Common specification, defines the API analog to the CSW standard.

This specification addresses only those parts of an API which are specific to Records resources. Those capabilities which may have applicability beyond Records should be considered for inclusion in OGC API - Common.

## Generating HTML and PDF

The latest drafts of each standard in this repository are built daily (based on the configuration contained in the [asciidoctor.json](https://github.com/opengeospatial/ogcapi-records/blob/master/asciidoctor.json) file):

* [Part 1: Core](http://docs.ogc.org/DRAFTS/20-004.html)

To generate HTML and PDF representations of the standard yourself, asciidoctor is required.  To install:

```bash
gem install asciidoctor --pre
gem install asciidoctor-pdf --pre
```

From here, run `HTML_gen.bat` and `PDF_gen.bat` accordingly.  Outputs are written to the parent directory.
