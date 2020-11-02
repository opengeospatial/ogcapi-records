# Implementations

## Overview

This page points to servers implementing drafts of the OGC API Records series.

## Implementations:

Servers:

* [CubeWerx Inc.](#cubewerx-inc)
* [pygeoapi](#pygeoapi)
* [Esri Inc.](#esri-inc)

Clients:
* [OWSLib](#owslib)

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

The [pygeoapi](https://pygeoapi.io) project implements most of the current
OGC API - Records draft (note: work in progress can be found on [GitHub](https://github.com/tomkralidis/pygeoapi/tree/oarec)).

A sample instance is deployed using discovery metadata from the
Meteorological Service of Canada as part of the WMO Information System.

Landing page:

* https://dev.api.weather.gc.ca/msc-wis-dcpc
* https://dev.api.weather.gc.ca/msc-wis-dcpc/?f=json

API document:

* https://dev.api.weather.gc.ca/msc-wis-dcpc/openapi
* https://dev.api.weather.gc.ca/msc-wis-dcpc/openapi?f=json

Conformance page:

* https://dev.api.weather.gc.ca/msc-wis-dcpc/conformance
* https://dev.api.weather.gc.ca/msc-wis-dcpc/conformance?f=json

List of catalogues:

* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections?f=json

Describe MSC discovery metadata catalogue

* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata?f=json

Queryables:

* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/queryables

Records:

* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items?title=metar
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items?title=metar&f=json
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items?bbox=-100,40,-80,50&title=pilot
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items?bbox=-100,40,-80,50&title=pilot&f=json
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items?bbox=-100,40,-80,50&datetime=2000-11-11/..
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items?bbox=-100,40,-80,50&datetime=2000-11-11/..&f=json
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items?q=forecast
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items?q=forecast&f=json

Single record:

* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items/urn:x-wmo:md:int.wmo.wis::ca.gc.ec.msc-1.1.10.2
* https://dev.api.weather.gc.ca/msc-wis-dcpc/collections/discovery-metadata/items/urn:x-wmo:md:int.wmo.wis::ca.gc.ec.msc-1.1.10.2&f=json

## Esri Inc

This Esri Geoportal Server 2.6.4 [public sanbox](http://geoss.esri.com/geoportal_264) has now been extended with a work-in-progress implementation of the OGC Records API.

Landing page:

* https://geoss.esri.com/ogcrecords

API document:

* https://geoss.esri.com/ogcrecords/api

Conformance page:

* https://geoss.esri.com/ogcrecords/conformance

List of catalogues:

* https://geoss.esri.com/ogcrecords/collections

Describe geoportal_264 catalogue:

* TODO - geoss.esri.com/ogcrecords/master 

Queryables:

* TODO - geoss.esri.com/ogcrecords/collections/master/queryables

Records:

* https://geoss.esri.com/ogcrecords/collections/master/items
* https://geoss.esri.com/ogcrecords/collections/master/items/89ed638c5eed41df9fe25473677d9df4 - get individual item based on item identifier

## OWSLib

[OWSLib](https://geopython.github.io/OWSLib/) is an OGC Web Services client
written in Python which also implements the evolving OGC API standards.  See the
[documentation](https://geopython.github.io/OWSLib/#ogc-api-records-1-0) for example workflow.
