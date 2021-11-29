# OpenEDI-Specification

### Version 1.1.0   
This document is licensed under [The Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).

## Introduction   
The OpenEDI Specification defines a standard, language-agnostic, and format-agnostic interface to all EDI and HL7 messaging standards, allowing them to be used with HTTP APIs by both humans and computers.     

### EDI and HL7
The format of EDI documents is governed by their implementation guidelines, which in most cases (depending on the standard and the issuing party), describe it only figuratively. Hence, it is human-readable, and it is NOT in a common, machine-readable form.   
More information about EDI can be found in our [What is EDI?](https://support.edifabric.com/hc/en-us/articles/360000291391-What-is-EDI) article.

### OpenAPI
The OpenAPI Specification (OAS) defines a standard, language-agnostic interface to HTTP APIs, which allows both humans and computers to discover and understand the capabilities of the service without access to source code, documentation, or through network traffic inspection. 
For more details, go to [The OpenAPI Specification](https://github.com/OAI/OpenAPI-Specification).

### EDI and OpenAPI, together
OpenAPI input and output types are defined by the [Schema Object](http://spec.openapis.org/oas/v3.0.3#schema-object), which is ready to be machine-processed, widespread across all internal/external APIs worldwide, and supported by almost every programming language.

We combined the two, and now every EDI implementation guideline, regardless of its origin or format, can easily be transposed into an OpenAPI Schema Object. 

[Interactive example for X12 5010 837P](https://app.swaggerhub.com/apis/EdiNation/edi-nation-837P-example/2)

### OpenEDI contributors
The OpenEDI Specification was created by [EdiFabric](https://www.edifabric.com/) to support their API and Web products for modern EDI development, collectively known as [EdiNation](https://www.edination.com/). All examples in this document refer to concrete applications of the OpenEDI format in EdiNation. 

## OpenEDI is an extension of OpenAPI
To model an EDI format using OpenAPI is to provide an OpenAPI definition file, with the addition of a few extension attributes.

### Supported OpenAPI version
OpenEDI supports OpenAPI 3+.

### Integration with OpenAPI
The only required OpenAPI objects are Component and Schema. All other top-level objects, Info, Security, Tags, Paths, Servers are ignored.

### Resolved or unresolved
OpenEDI supports resolved OpenAPI schemas. All objects that contain one or more other objects must be defined using references to those objects using the Reference object.

![OpenEDI example 837P](https://support.edifabric.com/hc/article_attachments/360019345057/openapi-edi-format.png)

### Case sensitivity
All values in the custom extensions are case sensitive and must be in upper-case.

## Supported EDI and HL7 standards
The following EDI messaging standards have already been implemented using OpenEDI:
- [EANCOM GS1](https://www.edination.com/edi-file-formats.html?edi=EdiNation.Edifact.EAN)
- [EDIFACT UN](https://www.edination.com/edi-file-formats.html?edi=EdiNation.Edifact.UN)
- [X12 ASC](https://www.edination.com/edi-file-formats.html?edi=EdiNation.X12.ASC)
- [X12 HIPAA](https://www.edination.com/edi-file-formats.html?edi=EdiNation.X12.HIPAA)
- [HL7](https://www.edination.com/edi-file-formats.html?edi=EdiNation.HL7)
- [NCPDP Telecommunications](https://www.edination.com/edi-file-formats.html?edi=EdiNation.NCPDP)
- [NCPDP SCRIPT](https://www.edination.com/edi-file-formats.html?edi=EdiNation.NCPDP)
- [VDA](https://www.edination.com/edi-file-formats.html?edi=EdiNation.Vda)
- [IATA PADIS](https://www.edination.com/edi-file-formats.html?edi=EdiNation.Edifact.IA)
- [X12 IAIABC](https://www.edination.com/edi-file-formats.html?edi=EdiNation.X12.IAIABC)
- EDIGAS
- [EDIFACT ACE](https://www.edination.com/edi-file-formats.html?edi=EdiNation.Edifact.ACE)
- [EDIFACT SMDG](https://www.edination.com/edi-file-formats.html?edi=EdiNation.Edifact.SMDG)

## EDI standards represented with OpenEDI
EDI implementation guidelines can be seamlessly converted to OpenEDI without losing information and avoiding any ambiguity.
All EDI items such as message, loop, segment, or composite/data element are represented as OpenAPI Schema objects and must include their corresponding OpenEDI attribute, which is defined as a regular OpenAPI extension property.

### EDI Message
EDI messages are defined by their EDI format, EDI version (optional) and EDI transaction ID.

- `x-edination-message-standard` The EDI standard, either X12 or EDIFACT. Required.
- `x-edination-message-id` The message ID. Required.
- `x-edination-message-version` The EDI edition and release. Required only if multiple messages with the same message ID are included in the same definition to avoid duplicates.

*Example of EDI message definition for message 837P standard X12 and version 005010X222A1*
![Example of EDI message definition for message 837P standard X12 and version 005010X222A1](https://support.edifabric.com/hc/article_attachments/360019345437/openapi-edi-message-id.png)

