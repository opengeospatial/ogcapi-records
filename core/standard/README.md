
# OGC API - Records Specification

This directory contains the OGC API - Records Specification. This specification, working with the parallel OGC API Common specification, defines the API analog to the CSW standard.

This specification addresses only those parts of an API which are specific to Records resources. Those capabilities which may have applicability beyond Records should be considered for inclusion in OGC API - Common.

## Generating HTML and PDF

The latest drafts of each standard in this repository are built daily (based on the configuration contained in the [asciidoctor.json](https://github.com/opengeospatial/ogcapi-records/blob/master/asciidoctor.json) file):

* [Part 1: Core](https://docs.ogc.org/DRAFTS/20-004.html)

To generate HTML and PDF representations of the standard yourself, asciidoctor is required.  To install:

```bash
gem install asciidoctor --pre
gem install asciidoctor-pdf --pre
```

From here, run `HTML_gen.bat` and `PDF_gen.bat` accordingly.  Outputs are written to the parent directory.
