## Overview

This document describes the fields needed for an OGC Record to describe a 'dataset'. A dataset is a
"collection of data, published or curated by a single agent, and available for access or download in 
one or more serializations or formats" (from [dcat](https://www.w3.org/TR/vocab-dcat-2/#dcat-scope)). In the
geospatial domain datasets typically are defined with the same properties and share higher level metadata. In GIS a 
dataset typically corresponds to a 'layer', and in the satellite world a dataset would be all the scene captures that
 come from the same sensor or constellation. It corresponds directly to what others call a "dataset series" (ESA, ISO 19115),
"collection" (CNES, NASA), and "dataset" (JAXA, DCAT). 

The Dataset Record is the metadata needed for users to actually find the data they need. The data itself may be available as
an OGC API Service, an older OGC W\*S Service, or an actual data file.

A dataset record is an [OGC Record](ogc-record-geojson-spec.md), and uses all the exact same fields, but makes
more of the fields required, in order to more fully describe the metadata users need to understand the dataset. 

A Record is the GeoJSON equivalent of an [OGC Dataset Collection](https://github.com/cholmes/ogc-collection/blob/main/ogc-collection-spec.md) 
(todo: port this to be a proposal in Features API) that includes 'Dataset Fields', and shares most all the same fields.

Dataset Records are represented in JSON format and are very flexible. Any JSON object that contains all the
required fields is a valid Record.

- Examples:
  - See this [example](./examples/record-meetlocaties-example.json) that contains more fields and links.
- JSON Schema: TODO


## Dataset Record Fields

The core Record fields for a 'Dataset Record' remain the same as in the core [OGC Record](ogc-record-geojson-spec.md), with the
exact same Item fields as [specified there](ogc-record-geojson-spec.md#item-fields). (TODO: Link to main spec when Peter's refactor lands)

### Datset Record Property Fields

The property fields are where the Dataset Record has more requirements. It uses all the same core Record definitions, but adds in 
more requirements and a couple defaults. 

| Field Name        | Required in Core Record | Required in Dataset Record | Description                                                                                                                                                 |
|-------------------|-------------------------|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| type              | M                       | M                          | Denotes the resource type of the record. For the dataset record this is **required** to be `dataset`.                                                         |
| title             | M                       | M                          | A short descriptive human-readable one-line title for the Collection.                                                                                       |
| description       | O                       | M                          | Detailed multi-line description to fully explain the Collection. |
| keywords          | O                       | M                          | List of keywords describing the Collection.                                                                                                                 |
| keywordsCodespace | O                       | O (defaults to XXX)        | A reference to a controlled vocabulary used for the keywords property.                                                                                      |
| language          | O                       | O (defaults to english)    | The natural language used for textual values (i.e. titles, descriptions, etc) that the collection information is given in.                                  |
| externalId        | O                       | O                          | Identifier for the Collection that is unique across the provider.                                                                                           |
| publisher         | O                       | M                          | The entity making the resource available.                                                                                                                   |
| created           | O                       | M                          | The date-time the collection represented by this record was created, formatted to [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6).              |
| updated           | O                       | O                          | The date-time this collection represented by this record was updated, formatted to [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6).             |
| themes            | O                       | O                          | A knowledge organization system used to classify the resource.                                                                                              |
| formats           | O                       | O                          | A list of available distributions for the resource.                                                                                                         |
| contactPoint      | O                       | M                          | An entity to contact about the resource.                                                                                                                   |
| license           | O                       | M                          | A legal document under which the resource is made available.                                                                                                |
| rights            | O                       | O                          | A statement that concerns all rights not addressed by the license such as a copyright statement.                                                            |
| extent            | O                       | M                          | Spatial and temporal extents.                                                                                                                               |
| associations      | O                       | M                          | A list of links for accessing the resource, links to other resources associated with this resource, etc.                                                    |
| crs               | O                       | O (default to latlong)     | Coordinate reference system of the data represented by this collection.                                                                                     |

### Associations

At least one association is required. This should link to the actual dataset. It could be to OGC API (or OGC W\*S interfaces to the data, it 
could link directly to the source format file for the dataset, or it ideally is a combination: several OGC services and a link to the source data.

TODO: Flesh out common rel types for ogc api links, source data file links, etc.

### Dataset definition ideas (Work in Progress)

From STAC: a set of assets that are defined with the same properties and share higher level metadata. In the satellite world these would typically all come from the same sensor or constellation. It corresponds directly to what others call a "dataset series" (ESA, ISO 19115), "collection" (CNES, NASA), and "dataset" (JAXA, DCAT). So if all your Items have the same properties, they probably belong in the same Collection.

We should also reference vector dataset ideas, how it maps to a 'layer', can be a coverage, etc.