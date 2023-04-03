# Implementations

## Overview

This page points to servers implementing drafts of the OGC API - Records series.

## Implementations:

Servers:

* [CubeWerx Inc.](#cubewerx-inc)
* [pygeoapi](#pygeoapi)
* [Esri Inc.](#esri-inc)
* [GeoNetwork opensource](#geonetwork-opensource)
* [ldproxy](#ldproxy)
* [pycsw](#pycsw)

Clients:
* [QGIS](#qgis)
* [OWSLib](#owslib)
* [stac-browser](#stac-browser)

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

* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63&datetime=2022-05-01T00:00:00/2022-05-15T00:00:00

* https://eratosthenes.pvretano.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/sentinel1cat/items?f=json&limit=10000&bbox=-69.64,37.76,-56.12,46.63&datetime=2022-05-20T00:00:00/2022-05-15T00:00:00&filter-lang=CQL&filter=passDirection%3D%27Ascending%27

## pygeoapi

The [pygeoapi](https://pygeoapi.io) project implements most of the current OGC API - Records draft.

A sample instance is deployed using sample metadata records from
the [Dutch Nationaal georegister](https://www.nationaalgeoregister.nl).

Landing page:

* https://demo.pygeoapi.io/master
* https://demo.pygeoapi.io/master/?f=json

API document:

* https://demo.pygeoapi.io/master/openapi
* https://demo.pygeoapi.io/master/openapi?f=json

Conformance page:

* https://demo.pygeoapi.io/master/conformance
* https://demo.pygeoapi.io/master/conformance?f=json

List of catalogues:

* https://demo.pygeoapi.io/master/collections
* https://demo.pygeoapi.io/master/collections?f=json

Describe sample metadata records from Dutch Nationaal georegister

* https://demo.pygeoapi.io/master/collections/dutch-metadata
* https://demo.pygeoapi.io/master/collections/dutch-metadata?f=json

Queryables:

* https://demo.pygeoapi.io/master/collections/dutch-metadata/queryables

Records:

* https://demo.pygeoapi.io/master/collections/dutch-metadata/items
* https://demo.pygeoapi.io/master/collections/dutch-metadata/items?f=json&title=Geesten%20van%20Holland
* https://demo.pygeoapi.io/master/collections/dutch-metadata/items?f=json&title=Geesten%20van%20Holland&f=json
* https://demo.pygeoapi.io/master/collections/dutch-metadata/items?bbox=4,51,7,53
* https://demo.pygeoapi.io/master/collections/dutch-metadata/items?bbox=4,51,7,53&f=json
* https://demo.pygeoapi.io/master/collections/dutch-metadata/items?q=Kaartboeck
* https://demo.pygeoapi.io/master/collections/dutch-metadata/items?q=Kaartboeck&f=json

Single record:

* https://demo.pygeoapi.io/master/collections/dutch-metadata/items/b7d2fd24-8cd8-4965-a997-69eb1a987b5a
* https://demo.pygeoapi.io/master/collections/dutch-metadata/items/b7d2fd24-8cd8-4965-a997-69eb1a987b5a?f=json

## Esri Inc

### ArcGIS Pro CSW Client as OGC API - Records consumer
The ArcGIS Pro CSW Client has been updated to include initial support for OGC API - Records. Details may be found on the [Geoportal Server wiki](https://github.com/Esri/geoportal-server-catalog/wiki/OGC_API_Records), the Visual Studio project to build the Pro addin is available in the [Components](https://github.com/Esri/geoportal-server-catalog/tree/master/components/CswClient/Pro/CswClient) section of the Geoportal Server github repo.

### Geoportal Server OGC API - Records provider
Esri Geoportal Server 2.6.4 [public sandbox](https://gpt.geocloud.com/geoportal2) has now been extended with a work-in-progress implementation of the OGC Records API.

Landing page:

* https://gpt.geocloud.com/ogcrecords

API document:

* https://gpt.geocloud.com/ogcrecords/api

Conformance page:

* https://gpt.geocloud.com/ogcrecords/conformance

List of catalogues:

* https://gpt.geocloud.com/ogcrecords/collections

Describe geoportal2 catalogue:

* TODO - gpt.geocloud.com/ogcrecords/master 

Queryables:

* TODO - gpt.geocloud.com/ogcrecords/collections/master/queryables

Records:

* https://gpt.geocloud.com/ogcrecords/collections/master/items
* https://gpt.geocloud.com/ogcrecords/collections/master/items/456688037ef0400fa46c87a3bec3a893 - get individual item based on item identifier

## GeoNetwork opensource

[GeoNetwork](https://geonetwork-opensource.org) is a java/xml oriented catalogue application. As part of an ongoing effort, the GeoNetwork API component is extended to support OGC API - Records. The work in progress is available at https://github.com/geonetwork/geonetwork-microservices/pull/23.

GeoNetwork has a concept of [sub-portals](https://geonetwork-opensource.org/manuals/trunk/en/administrator-guide/configuring-the-catalog/portal-configuration.html). In the OGC API - Records implementation these subportals are available as collections of records. GeoNetwork uses an [Elastic Search](https://elastic.co) backend, supporting a configurable set of queryables. Records are available in various encodings, such as text/html, application/geo+json, application/dcat.ld+json, application/iso19139+xml, application/iso19115-3+xml, application/dublin-core+xml, application/datacite+xml, through the accept-header mechanism. The html encoding of records contains an embedded schema-org json-ld snippet to facilitate search engines. A [Sitemap](https://sitemaps.org) endpoint is available to notify the search engine of available records.

GeoNetwork supports basic authentication, but can also be set up with alternative authentication mechanisms to facilitate autorisation on subsets of records.

## ldproxy

[ldproxy](https://github.com/interactive-instruments/ldproxy) supports (most of) the core/cql/json/html conformance classes of the current draft of OGC API - Records.

A sample instance with enumerations and codelists from the data specification of the German mapping and cadastral authorities for topographic, cadastral, geodetic, land use and land cover data ("GeoInfoDok NEU") is available at https://demo.ldproxy.net/geoinfodok. Sample URLs are shown below, to override content negotiation use `f=html` for HTML and `f=json` for JSON.

Landing page:

* https://demo.ldproxy.net/geoinfodok

API definition / documentation:

* https://demo.ldproxy.net/geoinfodok/api

Conformance declaration:

* https://demo.ldproxy.net/geoinfodok/conformance

List of collections (each enumeration or codelists is a collection):

* https://demo.ldproxy.net/geoinfodok/collections

Landing page of the AX_Gebaeudefunktion enumeration (building functions):

* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion

Queryables:

* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/queryables

Response schema (not part of OGC API - Records, JSON Schema only):

* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/schema

Records (enums in the AX_Gebaeudefunktion enumeration):

* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/items
* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/items?title=Brauerei
* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/items?theme.concept=DLM250
* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/items?theme.concept=DLKM%20(Grunddatenbestand)
* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/items?q=Tier
* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/items?q=DLM250,Tier
* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/items?filter=theme.concept='DLKM%20(Grunddatenbestand)'%20AND%20title%20LIKE%20'Wohn%'

Single record (enum):

* https://demo.ldproxy.net/geoinfodok/collections/ax_gebaeudefunktion/items/2113

## pycsw

[pycsw](https://pycsw.org/) is an OGC CSW server implementation written in Python.
Implementation of OGC API - Records is a work in progress for pycsw.

Landing page:

* https://demo.pycsw.org/gisdata

Conformance page:

* https://demo.pycsw.org/gisdata/conformance

List of catalogues:

* https://demo.pycsw.org/gisdata/collections

Describe sample metadata records from CSW CITE tests

* https://demo.pycsw.org/gisdata/collections/metadata:main

Queryables:

* https://demo.pycsw.org/gisdata/collections/metadata:main/queryables

Records:

* https://demo.pycsw.org/gisdata/collections/metadata:main/items
* https://demo.pycsw.org/gisdata/collections/metadata:main/items?filter=type%20=%20%22vector%20digital%20data%22

Single record:

* https://demo.pycsw.org/gisdata/collections/metadata:main/items/urn:uuid:dc9e3c58-932a-11ea-ad6f-823cf448c401

## QGIS
[QGIS](https://qgis.org) is a free and open-source cross-platform desktop geographic information system application that supports viewing, editing, and analysis of geospatial data.  The QGIS MetaSearch core plugin supports OGC API - Records as a search client.

## OWSLib

[OWSLib](https://geopython.github.io/OWSLib/) is an OGC Web Services client
written in Python which also implements the evolving OGC API standards.  See the
[documentation](https://geopython.github.io/OWSLib/#ogc-api-records-1-0) for example workflow.

## pygeometa

[pygeometa](https://geopython.github.io/pygeometa) is a Python package to generate
metadata for geospatial datasets.  Supports OGC API - Records record metadata generation.

## stac-browser

[stac-browser](https://github.com/radiantearth/stac-browser) is a web client developed for [Spatio-Temporal Asset Catalog (STAC)](https://github.com/radiantearth/stac-spec) static catalogs. It is compatible with OGC API - Records crawlable catalogs. A live version is available [here](https://radiantearth.github.io/stac-browser/#/)
