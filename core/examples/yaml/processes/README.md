# Making the "/processes" endpoing behave like a mini-catalog

This directory is an example of how to extend the OGC API "/processes" endpoint so that it can be accessed by an "OGC API - Records" client as if it was a catalog of the processes available at this OGC API deployment.

The schema of the process list is extended to include the common catalog properties.  The "itemType" property of the catalog is set to "record" since this catalog does not reference other catalogs (i.e. hierarchical process lists are not supported in OGC APIs).  The "recordsArrayName" property is set to "processes" which is the name of the array property in the process list object that contains the records (i.e. the summary description of each process offered by this OGC API deployment).

The schema of each process summary (i.e. each record of this catalog) is extended with the common record properties.
