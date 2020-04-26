# Implementations

## Overview

This page points to servers implementing drafts of the OGC API Records series.

## Implementations:

Servers:

* [CubeWerx Inc.](#cubewerx-inc)
* [pygeoapi](#pygeoapi)

Clients:

## CubeWerx Inc.

The following server implements a good portion of the current draft OpenAPI
document for OGC API - Records.  This is a very rough implementation and still
needs quite a bit of work but feel free to play with it.

I have currently harvested a bunch of RADARSAT metadata and will shortly have 
harvested all the SENTINEL-1 metadata that is available on AWS.

Landing page:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0?f=json

API document:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/api

Conformance Page:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/conformance?f=json

List of catalogues:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections?f=json

Describe cwcat catalogue:
* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat?f=json

Queryables:

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/queryables?f=json

Records:

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/items?limit=100&f=json

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63&time=2020-01-11T00:00:00/2020-01-12T00:00:00

* http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63&time=2020-01-11T00:00:00/2020-01-12T00:00:00&filter-lang=CQL&filter=passDirection%3D%27Ascending%27


## pygeoapi

The [pygeoapi](https://pygeoapi.io) project implements most of the current OGC API - Records
draft (note: work in progress can be found on [GitHub](https://github.com/tomkralidis/pygeoapi/tree/oarec)).

A sample instance is deployed using discovery metadata from the Meteorological Service of Canada as part
of the WMO Information System.

Landing page:

* http://52.170.144.218:8000
* http://52.170.144.218:8000/?f=json

API document:

* http://52.170.144.218:8000/openapi
* http://52.170.144.218:8000/openapi?f=json

Conformance page:

* http://52.170.144.218:8000/conformance
* http://52.170.144.218:8000/conformance?f=json

List of catalogues:

* http://52.170.144.218:8000/collections
* http://52.170.144.218:8000/collections?f=json

Describe MSC discovery metadata catalogue

* http://52.170.144.218:8000/collections/msc-wis-dcpc
* http://52.170.144.218:8000/collections/msc-wis-dcpc?f=json

Queryables:

* http://52.170.144.218:8000/collections/msc-wis-dcpc/queryables

Records:

* http://52.170.144.218:8000/collections/msc-wis-dcpc/items
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items?title=metar
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items?title=metar&f=json
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items?bbox=-100,40,-80,50&title=pilot
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items?bbox=-100,40,-80,50&title=pilot&f=json
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items?bbox=-100,40,-80,50&datetime=2000-11-11/..
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items?bbox=-100,40,-80,50&datetime=2000-11-11/..&f=json
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items?q=forecast
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items?q=forecast&f=json

Single record:

* http://52.170.144.218:8000/collections/msc-wis-dcpc/items/urn:x-wmo:md:int.wmo.wis::ca.gc.ec.msc-1.1.10.2
* http://52.170.144.218:8000/collections/msc-wis-dcpc/items/urn:x-wmo:md:int.wmo.wis::ca.gc.ec.msc-1.1.10.2&f=json
