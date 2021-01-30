# Implementations

## Overview

This page points to servers implementing drafts of the OGC API Records series.

## Implementations:

Servers:

* [CubeWerx Inc.](#cubewerx-inc)
* [pygeoapi](#pygeoapi)
* [Esri Inc.](#esri-inc)
* [GeoNetwork opensource](#geonetwork-opensource)

Clients:
* [OWSLib](#owslib)

Parsers/Encoders:
* [pygeometa](#pygeometa)

## CubeWerx Inc.

The following server implements a good portion of the current draft OpenAPI
document for OGC API - Records.  This is a very rough implementation and still
needs quite a bit of work but feel free to play with it.

I have currently harvested a bunch of RADARSAT metadata and will shortly have 
harvested all the SENTINEL-1 metadata that is available on AWS.

Landing page:
* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues?f=json

API document:
* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/api

Conformance Page:
* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/conformance?f=json

List of catalogues:
* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections?f=json

Describe sentinel1cat catalogue:
* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/sentinel1cat?f=json

Queryables:
* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/sentinel1cat/queryables?f=json

Records:
* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/sentinel1cat/items?f=json&limit=100

* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63

* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63&datetime=2020-01-11T00:00:00/2020-01-12T00:00:00

* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63&datetime=2020-01-11T00:00:00/2020-01-12T00:00:00&filter-lang=CQL&filter=passDirection%3D%27Ascending%27

## pygeoapi

The [pygeoapi](https://pygeoapi.io) project implements most of the current
OGC API - Records draft (note: work in progress can be found on [GitHub](https://github.com/tomkralidis/pygeoapi/tree/oarec)).

A sample instance is deployed using discovery metadata from the
Meteorological Service of Canada as part of the WMO Information System.

Landing page:

* http://147.102.109.27/pygeoapi-oarec
* http://147.102.109.27/pygeoapi-oarec/?f=json

API document:

* http://147.102.109.27/pygeoapi-oarec/openapi
* http://147.102.109.27/pygeoapi-oarec/openapi?f=json

Conformance page:

* http://147.102.109.27/pygeoapi-oarec/conformance
* http://147.102.109.27/pygeoapi-oarec/conformance?f=json

List of catalogues:

* http://147.102.109.27/pygeoapi-oarec/collections
* http://147.102.109.27/pygeoapi-oarec/collections?f=json

Describe MSC discovery metadata catalogue

* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc?f=json

Queryables:

* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/queryables

Records:

* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items?title=metar
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items?title=metar&f=json
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items?bbox=-100,40,-80,50&title=pilot
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items?bbox=-100,40,-80,50&title=pilot&f=json
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items?bbox=-100,40,-80,50&datetime=2000-11-11/..
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items?bbox=-100,40,-80,50&datetime=2000-11-11/..&f=json
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items?q=forecast
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items?q=forecast&f=json

Single record:

* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items/urn:x-wmo:md:int.wmo.wis::ca.gc.ec.msc-1.1.10.2
* http://147.102.109.27/pygeoapi-oarec/collections/msc-wis-dcpc/items/urn:x-wmo:md:int.wmo.wis::ca.gc.ec.msc-1.1.10.2&f=json

## Esri Inc

This Esri Geoportal Server 2.6.4 [public sandbox](http://geoss.esri.com/geoportal_264) has now been extended with a work-in-progress implementation of the OGC Records API.

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

## GeoNetwork opensource

[GeoNetwork](https//geonetwork-opensource.org) is a java/xml oriented catalogue application. As part of an ongoing effort, the GeoNetwork API component is extended to support OGC API Records. The work in progress is available at https://github.com/geonetwork/geonetwork-microservices/pull/23.

GeoNetwork has a concept of [sub-portals](https://geonetwork-opensource.org/manuals/trunk/en/administrator-guide/configuring-the-catalog/portal-configuration.html). In the OGC API Records implementation these subportals are available as collections of records. GeoNetwork uses an [Elastic Search](https://elastic.co) backend, supporting a configurable set of queryables. Records are available in various encodings, such as text/html, application/geo+json, application/dcat.ld+json, application/iso19139+xml, application/iso19115-3+xml, application/dublin-core+xml, application/datacite+xml, through the accept-header mechanism. The html encoding of records contains an embedded schema-org json-ld snippet to facilitate search engines. A [Sitemap](https://sitemaps.org) endpoint is available to notify the search engine of available records.

GeoNetwork supports basic authentication, but can also be set up with alternative authentication mechanisms to facilitate autorisation on subsets of records.

## OWSLib

[OWSLib](https://geopython.github.io/OWSLib/) is an OGC Web Services client
written in Python which also implements the evolving OGC API standards.  See the
[documentation](https://geopython.github.io/OWSLib/#ogc-api-records-1-0) for example workflow.

## pygeometa

[pygeometa](https://geopython.github.io/pygeometa) is a Python package to generate
metadata for geospatial datasets.  Supports OGC API - Records record metadata generation.
