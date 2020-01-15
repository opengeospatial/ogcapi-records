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
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat?f=json

Records:

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/items?limit=100&f=json

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63&time=2020-01-11T00:00:00/2020-01-12T00:00:00

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63&time=2020-01-11T00:00:00/2020-01-12T00:00:00&filter-lang=CQL&filter=passDirection%3D%27Ascending%27
