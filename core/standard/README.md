:warning: **The OGC API - Records specification is still a work in progress.  Please be aware that the specification document in this directory is not yet in a state that could be useful to anyone who has not been attending the bi-weekly standards working group (SWG) meetings and/or who is not actively working on the document.  The SWG is working diligently to update the specification so please refer back to this readme periodically for any status updates.**

# OGC API - Records Specification

This directory contains the OGC API - Records Specification. This specification, working with the parallel OGC API Common specification, defines the API analog to the CSW standard.

This specification addresses only those parts of an API which are specific to Records resources. Those capabilities which may have applicability beyond Records should be considered for inclusion in OGC API - Common.

## Generating HTML and PDF

To generate HTML and PDF representations of the standard, asciidoctor is required.  To install:

```bash
gem install asciidoctor --pre
gem install asciidoctor-pdf --pre
```

From here, run `HTML_gen.bat` and `PDF_gen.bat` accordingly.  Outputs are written to the parent directory.
