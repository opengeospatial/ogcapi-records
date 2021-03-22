# OGC API - Records Support of OGC Web API Guidelines

# Overview

This document outlines OGC API - Records support of the design principles put forth as part of the [OGC Web API Guidelines](https://github.com/opengeospatial/OGC-Web-API-Guidelines).

- [x]  Principle #1 – Don’t Reinvent
  - adopts concepts from
    - OGC API - Common (landing page, conformance, exceptions, collections, conformance bbox, datetime query parameters)
    - OGC API - Features (`/collections/{collectionId}/items/{recordId}`), queryables, `itemType` concept, GeoJSON
- [x]  Principle #2 – Keep the API Simple and Intuitive
  - allows for minimal compliant implementation close to OGC API - Features
  - provides interaction with minimal domain knowledge
  - provides simple full-text search capability via `q=`
- [x]  Principle #3 - Use Well-Known Resource Types
  - supports `itemType`
- [x]  Principle #4 – Construct consistent URIs
  - adopts collection of resources principle
    - `/collections/{collectionId}/items`
- [x]  Principle #5 – Use HTTP Methods consistent with RFC 7231
  - implements resource-based HTTP `GET` methods
- [x]  Principle #6 – Put Selection Criteria behind the ‘?’
  - provides query parameter support in order to further subset a given resource/query type
- [x]  Principle #7 – Error Handling and use of HTTP Status Codes
  - provides exception schema (code and description) as well as the appropriate HTTP status codes (section 7.7.2)
- [x]  Principle #8 – Use explicit list of HTTP Status Codes
  - support of numerous codes at the 2xx, 3xx, 4xx, 500 levels (see Table 8)
- [x]  Principle #9 – Use of HTTP Header
  - allows for Link headers
  - allows for ETag and associated headers
- [ ]  Principle #10 - Allow flexible Content Negotiation
- [x]  Principle #11 - Pagination
  - provides navigation via link relations (next, prev) and `limit` parameter
- [ ]  Principle #12 – Processing Resources
  - Not applicable
- [x]  Principle #13 – Support Metadata
  - provides `service-desc` and `service-doc` link relations
  - provides metadata via extended collections model
  - resource model itself is metadata with associations
- [x]  Principle #14 – Consider your Security needs
  - supports HTTPS (See 7.7.1) and RFC2818
- [x]  Principle #15 – API Description
  - supports OpenAPI for API documentation
- [x]  Principle #16 - Use well-known identifiers
  - provides media types and link relations that are based on IANA
  - (in development) provides extended link relations and via the OGC Definitions Server
- [x]  Principle #17 - Use explicit relations
  - provides link relations as well as associations in the metadata model
- [x]  Principle #18 - Support W3C Cross-Origin Resource Sharing
  - CORS is supported (See 7.7.5)
- [x]  Principle #19 - Resource encodings
  - supports JSON, GeoJSON and HTML
- [x]  Principle #20 - Good APIs are testable from the beginning
  - enables standard programming libraries in implementing standard HTTP request/response, headers and well-known media types and design patterns
  - (planned) demonstrates via the OGC API - Records ETS
- [x]  Principle #21 - Specify whether operations are safe and/or idempotent
  - provides both safe and idempotent operations via HTTP `GET`
- [x]  Principle #22 – Make resources discoverable
  - implements common OGC API link relations
  - supports links with URI templates (via `link.templated` property)
- [x]  Principle #23 - Make default behavior explicit
  - default request/response patterns always return content/response

