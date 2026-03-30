# DCAT-AP JSON Schema for API Records

The way DCAT metadata is structured in API Records is currently open for interpretation. For certain use cases it is desirable to have a more clearly defined profile how DCAT metadata is structured in a API Records Item.

There are a number of implementations I am currently aware of:
- WMO profile: https://wmo-im.github.io/wcmp2/standard/wcmp2-STABLE.html
- draft DCAT-AP-NL profile: https://geonovum.github.io/bblock-dcat-ap-nl/bblock/geonovum.bbr.dcat.dcat-ap-nl-records
- OGC GeoDCAT: https://ogcincubator.github.io/geodcat-ogcapi-records/bblock/ogc.geo.geodcat.geodcat-records
- others?

For interoperability in the Dutch Digital Twin ecosystem (DTaaS program) we would like to have a profile that has clear guidelines for the following challenges:

- language tags
 
	TTL is naturally multi-language compatible. The DCAT-AP Profile explicitly supports this (e.g. https://semiceu.github.io/DCAT-AP/releases/3.0.1/#Dataset.title) and in the European data portal (data.europa.eu) you see this reflected.
	-> What's the best way to model this in a JSON schema for API Records?

- Distributions
  
	A DCAT Dataset is typically described with 1 or more Distributions. From a linked data perspective the Dataset and Distribution are different classes (with their own identifiers). The relation between a Dataset and Distribution is currently implemented in different ways. 
	
	Coming from a ISO19115 metadata record where distributions are encoded 'inline' (format tag) you see distributions show up as blank nodes in the Dataset class (see for example the Semic GeoDCAT iso to dcat xslt: https://github.com/SEMICeu/iso-19139-to-dcat-ap)
	The Ecplipse Dataspace protocol also seems to adopt this pattern: https://eclipse-dataspace-protocol-base.github.io/DataspaceProtocol/2025-1-err1/#example-catalog-response

	Another pattern that shows up in implementations is to describe the distribution in the links section of the item. This is how WCMP2 has implemented this: https://wmo-im.github.io/wcmp2/standard/wcmp2-STABLE.html#_1_19_3_distribution_information
	From a DCAT-AP(-NL) point of view it is at least important to also honor the required properties for a Distribution (like a license).

- Dataservices
  
	Similar to Distributions, Dataservices are also separate classes in DCAT. Unlike Distributions (which are always related to a Dataset) a Dataservice can also be it's own entry in a catalog. One reason for this is that a Dataservice can be composed of multiple (logical) Datasets. 
	
	The Dataspace protocol seems to treat Dataservices the same as Distributions, in the sense that they are subproperties (accessService) of a Distribution.
	In WCMP2 Dataservice seem to be separate items in a catalog: https://wmo-im.github.io/wcmp2/standard/wcmp2-STABLE.html#_1_6_properties_type  

- mismatch properties API Records and DCAT-AP?
  
	This list is probably not complete yet. There are some subtle differences between the properties defined in the API Records schema and the structure of those properties in DCAT-AP.
	- contact: I think the schema specified for contact does not match the contact point in DCAT-AP (which is a [vCard](https://www.rfc-editor.org/rfc/rfc6350.html) (Individual, Organization, Location, Group))
	- Language: I think the property in API Records is about the language of the metadata (item) record, while the property in DCAT is about the dataset/distribution language.
	- ??

