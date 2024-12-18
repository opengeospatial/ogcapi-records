# Making the "/collections" endpoint behave like a mini-catalog

This directory is an example of how to extend the OGC API "/collections" endpoint so that it can be accessed by an "OGC API - Records" client as if it was a catalog of the collections available at this OGC API deployment.

The schema of the collections is extended to include the common catalog properties.  The "itemType" property of the catalog is set to "record" since this catalog does not reference other catalogs (i.e. hierarchical collections are not supported in OGC APIs).  The "recordsArrayName" property is set to "collections" which is the name of the array in the collections object that contains the records (i.e. the description of each collection offered by this OGC API deployment).

The schema of each collection (i.e. each record of this catalog) is extended
with the common record properties.
