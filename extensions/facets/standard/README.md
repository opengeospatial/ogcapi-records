
# OGC API - Records - Part 2: Facets Specification

This directory contains the OGC API - Records - Part 2: Facets Specification. This specification, working with OGC API - Records - Part 1: Core, defines the mechanisms with which to apply faceting to an OGC API - Records endpoint.

## Generating HTML and PDF

The latest drafts of each standard in this repository are built daily (based on the configuration contained in the [asciidoctor.json](https://github.com/opengeospatial/ogcapi-records/blob/master/asciidoctor.json) file):

* [Part 1: Core](https://docs.ogc.org/DRAFTS/25-013.html)

To generate HTML and PDF representations of the standard yourself, asciidoctor is required.  To install:

```bash
gem install asciidoctor --pre
gem install asciidoctor-pdf --pre
```

From here, run `HTML_gen.bat` and `PDF_gen.bat` accordingly.  Outputs are written to the parent directory.
