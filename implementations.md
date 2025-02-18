# Implementations

## Overview

This page points to servers implementing drafts of the OGC API - Records series.

## Implementations:

Servers:

* [CubeWerx Inc.](#cubewerx-inc)
* [pygeoapi](#pygeoapi)
* [Esri Inc.](#esri-inc)
* [GeoNetwork opensource](#geonetwork-opensource)
* [pycsw](#pycsw)

Clients:
* [QGIS](#qgis)
* [OWSLib](#owslib)
* [stac-browser](#stac-browser)
* [mdme](#mdme)

Parsers/Encoders:
* [pygeometa](#pygeometa)

## CubeWerx Inc.

The following server implements a good portion of the current draft OpenAPI
document for OGC API - Records.  This is a very rough implementation and still
needs quite a bit of work but feel free to play with it.

I have currently harvested a bunch of RADARSAT metadata and will shortly have 
harvested all the SENTINEL-1 metadata that is available on AWS.

Landing page:
* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/cwtepcat2?f=json

API document:
* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues/api

Conformance Page:
* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues/conformance?f=json

List of catalogs:
* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues?f=json

Description of the catalog:
* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/cwtepcat2?f=json

Records:
* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/cwtepcat2/items?f=json

* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/cwtepcat2/items?f=json&&bbox=-69.64,37.76,-56.12,46.63

* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/cwtepcat2/items?f=json&&bbox=-69.64,37.76,-56.12,46.63&datetime=2017-04-01T00:00:00/2017-04-30T00:00:00

* https://test.cubewerx.com/cubewerx/cubeserv/default/ogcapi/catalogues/collections/cwtepcat2/items?f=json&&bbox=-69.64,37.76,-56.12,46.63&datetime=2017-04-01T00:00:00/2017-04-30T00:00:00&q=Ascending

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
Esri Geoportal Server 2.7.1 [public sandbox](https://gpt.geocloud.com/geoportal2) implementation of the OGC Records API.

Landing page:

* https://gpt.geocloud.com/geoportal2/ogcrecords

API document:

* https://gpt.geocloud.com/geoportal2/ogcrecords/api

Conformance page:

* https://gpt.geocloud.com/geoportal2/ogcrecords/conformance

List of catalogues:

* https://gpt.geocloud.com/geoportal2/ogcrecords/collections

Describe geoportal2 catalogue:

* https://gpt.geocloud.com/geoportal2/ogcrecords/collections/metadata

Queryables:

* https://gpt.geocloud.com/geoportal2/ogcrecords/collections/metadata/queryables

Records:

* https://gpt.geocloud.com/geoportal2/ogcrecords/collections/metadata/items
* https://gpt.geocloud.com/geoportal2/ogcrecords/collections/metadata/items?bbox=-111.791110603%2C18.91619%2C-66.96466%2C71.3577635769 - Items within bbox
* https://gpt.geocloud.com/geoportal2/ogcrecords/collections/metadata/items/0052b84c4a25478ea5c1c4154fc9c6bc - get individual item based on item identifier

OpenAPI page:
* https://gpt.geocloud.com/geoportal2/#apiPanel

### ArcGIS Hub Search API

The [ArcGIS Hub](https://hub.arcgis.com/) Search API conforms to the new OGC API - Records specification.

OpenAPI definition:
* https://hub.arcgis.com/api/search/definition/

User documentation: 
* https://doc.arcgis.com/en/hub/content/federate-data-with-external-catalogs.htm#GUID-EAF833F8-FADA-4EC7-A1CA-F704DC987362

## GeoNetwork opensource

[GeoNetwork](https://geonetwork-opensource.org) is a java/xml oriented catalogue application. As part of an ongoing effort, the GeoNetwork API component is extended to support OGC API - Records. The work in progress is available at https://github.com/geonetwork/geonetwork-microservices/pull/23.

GeoNetwork has a concept of [sub-portals](https://geonetwork-opensource.org/manuals/trunk/en/administrator-guide/configuring-the-catalog/portal-configuration.html). In the OGC API - Records implementation these subportals are available as collections of records. GeoNetwork uses an [Elastic Search](https://elastic.co) backend, supporting a configurable set of queryables. Records are available in various encodings, such as text/html, application/geo+json, application/dcat.ld+json, application/iso19139+xml, application/iso19115-3+xml, application/dublin-core+xml, application/datacite+xml, through the accept-header mechanism. The html encoding of records contains an embedded schema-org json-ld snippet to facilitate search engines. A [Sitemap](https://sitemaps.org) endpoint is available to notify the search engine of available records.

GeoNetwork supports basic authentication, but can also be set up with alternative authentication mechanisms to facilitate autorisation on subsets of records.

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

## mdme

Model Driven Metadata Editor ([MDME](https://osgeo.github.io/mdme)) is a 
metadata editor driven by arbitrary json schema models based on [vjsf](https://koumoul-dev.github.io/vuetify-jsonschema-form). You can configure it with the OGC API - Records schema to use it to author metadata in the OGC API - Records model. MDME also offers capabilities to transform between models using metadata transformation services provided by [pygeoapi.io](https://demo.pygeoapi.io/master/processes/)
