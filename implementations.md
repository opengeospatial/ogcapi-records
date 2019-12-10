# Implementations

## Overview

This page points to servers implementing drafts of the OGC API Records series.

## Implementations:

Servers:

* [CubeWerx Inc.](#cubeWerx)

Clients:

## CubeWerx Inc.

The following server implements a good portion of the current draft OpenAPI
document for OGC API - Records.  This is a very rough implementation and still
needs quite a bit of work but feel free to play with it.

I have currently harvested a bunch of RADARSAT metadata and will shortly have 
harvested all the SENTINEL-1 metadata that is available on AWS.

Langing page:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0?f=json

API document:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/api

Conformance Page:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/conformance?f=json

List of catalogues:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections?f=json

Describe cwcat catalogue:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/cwcat?f=json

Records:

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/cwtepcat/items?limit=10

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/cwtepcat/items?limit=500&f=json&bbox=-68.301,40.136,-64.214,45.189

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/cwtepcat/items?limit=500&f=json&bbox=-68.301,40.136,-64.214,45.189&time=20171101/20171231

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/cwtepcat/items?limit=500&f=json&bbox=-68.301,40.136,-64.214,45.189&time=20171101/20171231&filter-lang=CQL&filter=passDirection%3D%27Ascending%27
