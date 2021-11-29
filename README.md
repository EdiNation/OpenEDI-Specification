# OpenEDI-Specification

### Version 1.1.0   
This document is licensed under [The Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).

## Introduction   
The OpenEDI Specification defines a standard, language-agnostic and format-agnostic interface to all EDI and HL7 messaging standards which allows them to be used with HTTP APIs by both humans and computers.   

### EDI and HL7
The format of EDI documents is governed by their implementation guidelines, which in most cases (depending on the standard and the issuing party), describe it only figuratively. Hence, it is human-readable, and it is NOT in a common, machine-readable form.   
More information about EDI can be found in our [What is EDI?](https://support.edifabric.com/hc/en-us/articles/360000291391-What-is-EDI) article.

### OpenAPI
The OpenAPI Specification (OAS) defines a standard, language-agnostic interface to HTTP APIs which allows both humans and computers to discover and understand the capabilities of the service without access to source code, documentation, or through network traffic inspection. When properly defined, a consumer can understand and interact with the remote service with a minimal amount of implementation logic.
For more details go to [The OpenAPI Specification](https://github.com/OAI/OpenAPI-Specification).

### EDI and OpenAPI, together
OpenAPI input and output types are defined by the [Schema Object](http://spec.openapis.org/oas/v3.0.3#schema-object), which is ready to be machine-processed, widespread across all internal/external APIs worldwide, and supported by almost every programming language.

We combined the two, and now every EDI implementation guideline, regardless of its origin or format, can easily be transposed into an OpenAPI Schema Object. This tutorial will guide you through the steps to achieve that.

[Interactive example for X12 5010 837P](https://app.swaggerhub.com/apis/EdiNation/edi-nation-837P-example/2)
