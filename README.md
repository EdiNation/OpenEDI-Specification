# OpenEDI-Specification

### Version 1.1.0   
This document is licensed under [The Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).

## Introduction   
The OpenEDI Specification defines a standard, language-agnostic, and format-agnostic interface to all EDI and HL7 messaging standards, allowing them to be used with HTTP APIs by both humans and computers.   

## Table of Contents   
- [Definitions](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#definitions)
  - [EDI and HL7](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-and-hl7)
  - [OpenAPI](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#openapi)
  - [EDI and OpenAPI, together](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-and-openapi-together)
  - [OpenEDI and SEF](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#openedi-and-sef)
  - [OpenEDI contributors](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#openedi-contributors)
- [OpenEDI is an extension of OpenAPI](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#openedi-is-an-extension-of-openapi)
  - [Supported OpenAPI version](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#supported-openapi-version)
  - [Integration with OpenAPI](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#integration-with-openapi)
  - [Resolved or unresolved](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#resolved-or-unresolved)
  - [Case sensitivity](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#case-sensitivity)
- [Supported EDI and HL7 standards](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#case-sensitivity)
- [OpenEDI extensions for EDI items](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#openedi-extensions-for-edi-items)
  - [EDI Message](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-message)
  - [EDI Loop](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-loop-edi-group)
  - [EDI Segment](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-segment)
  - [EDI Composite Data Element](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-composite-data-element)
  - [EDI Data Element](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-data-element)
  - [EDI Syntax Rules](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-syntax-rules)
  - [EDI Situational Rules](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-situational-rules)
  - [Additional grouping of EDI Loops or EDI Segments](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#additional-grouping-of-edi-loops-or-edi-segments)
  - [EDI Sequences](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#edi-sequences)

## Definitions

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

### OpenEDI and SEF
The Standard Exchange Format is an open standard text format developed by the Foresight Corporation (now part of Tibco). Its purpose is to provide a machine-readable specification for EDI documents. 

[SEF Guideline](https://www.edination.com/files/sef161.pdf)

OpenEDI aims to support all parts of the SEF format and provide a web and API-friendly alternative for a global EDI meta format. EdiNation offers a detailed guide on which parts of [SEF are supported by OpenEDI](https://support.edifabric.com/hc/en-us/articles/360002918137-How-to-migrate-from-SEF-to-OpenAPI), and a free online tool to [convert SEF files into OpenEDI](https://www.edination.com/edi-models-custom.html) definitions.

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

## OpenEDI extensions for EDI items
EDI implementation guidelines can be seamlessly converted to OpenEDI without losing information and avoiding any ambiguity.
All EDI items such as message, loop, segment, or composite/data element are represented as OpenAPI Schema objects and must include their corresponding OpenEDI attribute, which is defined as a regular OpenAPI extension property.

### EDI Message
EDI messages represent the different types of B2B, Healthcare, or other business documents, such as purchase orders, medical claims, or price lists. They are composed of EDI Segments (units of data) and EDI Loops (blocks of EDI Segments) that are ordered and can be repeatable. Messages are defined as Schema objects with the following extension properties:

- `x-edination-message-standard` The EDI standard, either X12 or EDIFACT. Required.
- `x-edination-message-id` The message ID. Required.
- `x-edination-message-version` The EDI edition and release. Only required if multiple messages with the same message ID are included in the same definition to avoid duplicates.

![Example of EDI message definition for message 837P standard X12 and version 005010X222A1](https://support.edifabric.com/hc/article_attachments/360019345437/openapi-edi-message-id.png)  
*Example of EDI message definition for message 837P standard X12 and version 005010X222A1*

### EDI Loop (EDI Group)
EDI Loops represent a block of EDI Segments which allows the whole block to repeat as a unit. All segments within a loop are ordered and must have distinct positions. Loops are defined as Schema objects with the following extension property:

- `x-edination-loop-id` The loop ID. Required.

![Example of EDI loop](https://support.edifabric.com/hc/article_attachments/360019345477/openapi-edi-loop-id.png)  
*Example of EDI loop 2100B*

### EDI Segment
EDI Segments represent units of data known as data elements. Segments are defined as Schema objects with the following extension property:

- `x-edination-segment-id` The segment ID. Required.

![Example of EDI segment](https://support.edifabric.com/hc/article_attachments/360019345497/openapi-edi-segment-id.png)  
*Example of EDI segment PRV*

### EDI Composite Data Element
EDI Composite Data Elements are blocks of data elements that allow the whole block to repeat as a unit. Composite Data Elements are defined as Schema objects with the following extension property:

- `x-edination-composite-id` The composite data element ID. Required.

![Example of EDI composite data element](https://support.edifabric.com/hc/article_attachments/360019345517/openapi-edi-composite-id.png)  
*Example of EDI composite data element C040*

### EDI Data Element
EDI Data Elements are the actual units of data and can appear in a specific position in either a segment or a composite data element. Data elements can also be repeatable, with (X12) or without (EDIFACT) a repetition character. Data Elements are defined as primitive properties of a Schema object, with type `string` and the following extension property:

- `x-edination-element-id` The data element ID. Required.

![Example of EDI data element](https://support.edifabric.com/hc/article_attachments/360019345637/openapi-edi-element-id.png)  
*Example of EDI data element ReferenceIdentificationQualifier_01*

### EDI Syntax Rules
EDI Syntax Rules define all intra-segment (intra-composite data element) dependencies, such as when the data element for the first line of address exists, then the data element for postcode must also exist. Syntax rules are defined on segment/composite data element level with the following extension property:

- `x-edination-syntax` An array of items that represent all syntax rules in the segment/composite data element. Optional.

The format of each array item must be `{condition designator}{start position}[other positions]{end position}` where:
1. `{start position}, {end position}` and all other positions in-between must be two-digit numeric values, 0 to 9 must be padded with a leading zero.
2. `{condition designator}` must be one of the following values:
   - `P` Paired. If any of the elements in the specified positions is not null, then all the elements in the specified positions must not be null.
   - `R` Required. At least one of the elements in the specified positions must not be null.
   - `E` Exclusion. Only one of the EDI data elements in the specified positions must not be null.
   - `C` Conditional. If the EDI data element in the first position is not null, then all elements at the specified positions must also be not null.
   - `L` List Conditional. If any of the elements in the specified positions is not null, then at least one more of the EDI data elements in the specified positions must also be not null. 

![Example of EDI syntax rules](https://support.edifabric.com/hc/article_attachments/360019345797/openapi-edi-syntax-notes.png)  
*Example of EDI syntax rules*

### EDI Situational Rules
EDI Situational Rules define intra-segment (composite data element) conditions, very much like the syntax rules; however, instead of checking for existence/non-existence, the situational rules check if a data element in a certain position exists or is of a certain value, then another data element needs to conform to be of another value(s). Situational rules are defined on segment/composite data element level with the following extension property:

- `x-edination-situational` An array of items that represent all situational rules in the segment/composite data element. Optional.

The format of each array item must be:
- To mark "Not Used" data elements `{condition designator}{start position}[other positions]` 
- To mark conditional required or conditional exclusion `{condition designator}{start position}{end position}_{value1}[_{other values}]`  
where:
1. `{start position}, {end position}` and all other positions in-between must be two-digit numeric values, 0 to 9 must be padded with a leading zero.
2. `{value1}`, and all other values must be separated by _ (underscore).
3. `{condition designator}` must be one of the following values:
   - `R` Conditional Required. When the element in the second position is equal to one of the specified codes, then the first element must not be null.
   - `E` Conditional Exclusion. When the element in the second position is equal to one of the specified codes, then the first element must be null.
   - `N` Not used. When a "Not Used" data element's value is not null, it is marked as a validation error.

![Example of EDI situational rules](https://support.edifabric.com/hc/article_attachments/4404421186577/edination-situational.png)  
*Example of EDI situational rules*

### Additional grouping of EDI Loops or EDI Segments
Usually, segments are grouped in loops, where each segment must have a distinct position within the loop, and the first segment in a loop, known as "trigger segment", is mandatory and can only repeat once. A repetition of the trigger segment means that the whole loop is being repeated.

OpenEDI fits multiple B2B and Healthcare formats and thus needs to cater for the following extra adjustments:
- Segments or loops that can appear in the same position (X12 HIPAA).
- Multiple segments or loops are allowed in the same position, but only one of them can be present (HL7).
- Multiple segments can be grouped together in a sequence, very much like in EDI Loops; however, the first segment is not mandatory (HL7).

These additional types of grouping are defined as Schema objects with the following extension property:

- `x-edination-group-type` which can take the following values:
  - `anyOf` for segments or loops that can appear in the same position, in any order
  - `oneOf` for segments or loops that can appear in the same position; however, only one of them must be present
  - `seqOf` for segments that can appear in order, however, can't be represented as EDI Loops because the first segment is optional

![Example of EDI segments in the same position](https://support.edifabric.com/hc/article_attachments/4404421585169/edination-all.png)  
*Example of EDI segments in the same position*

### EDI Sequences
In X12, service line numbers must be sequential, e.g., the values in the first data element in all LX segments in a repeating loop must be sequential. This is defined on loop level with the following extension property:

- `x-edination-loop-seq` To denote the segment within a repeating loop, that needs to be checked for sequential numbers, such as LX. The value is the position of the data element within the segment. Optional.

![Example of EDI sequence](https://support.edifabric.com/hc/article_attachments/4404421761169/edination-loop-seq.png)  
*Example of EDI sequence in loop 2400*

## Interoperability of EDI Guidelines
The format of EDI messages is laid out in their implementation guides, either the official ones (from UN EDIFACT or ASC X12) or the respective trading partners' specific ones. The guides are meant for humans and are usually in text or PDF formats, and can't be transferred automatically from machine to machine.

OpenEDI allows B2B and Healthcare partners to exchange EDI implementation guidelines in a machine-readable form so that EDI translators and applications can automatically import/verify them and thus save users considerable time in developing new translations or maps.

### Convert EDI Message to OpenEDI
Each EDI message, or transaction set, is identified by the following three values:
- **EDI Standard** - This could be X12, EDIFACT, or other, denoting the particular EDI dialect. 
- **EDI Version** - This is the edition and release of the transaction set, for example, 004010 or D96A. 
- **EDI Transaction Set ID** - This is the transaction set ID as specified by the standard, for example, 850 is the ID for a purchase order in the X12 standard and ORDERS is the ID for a purchase order in the EDIFACT standard.  

To convert EDI Message to OpenEDI do:
1. Represent it as a Schema object.
2. Use the following extension properties:
   - `x-edination-message-standard` (Required)
   - `x-edination-message-version` (Optional when no other transaction sets with the same ID are used in the same definition, otherwise it is mandatory)
   - `x-edination-message-id` (Required)

The structure of each EDI Message is usually depicted in their implementation guidelines with schemas more or less similar to the one below:  
![Example of EDI guideline](https://support.edifabric.com/hc/article_attachments/360019346697/edi-guide.png)  
*Example of EDI guideline. The image is copyrighted by X12.org*

The guideline defines the positions (the order) of all segments and loops, their IDs (the EDI codes to identify each segment and loop), the usage (mandatory or not), and the repetitions in the same position. A description is also available for some or all segments/loops but it is not essential.

The following concepts must be used to convert the depicted structure above into an OpenAPI Schema object:
- **Position**  

The position of the segments, loops, and data elements is inferred from the order in the schema definition. The top item (ST) is in position 0, the next item (BHT) is in position 1, etc.  

![Example of EDI position](https://support.edifabric.com/hc/article_attachments/360019346737/edi-position.png)  
*Example of EDI position*

- **Multiple segments/loops in the same position** 

When the guideline shows two or more loops/segments to be in the same position like the two NM1 Loops above in position 0200, then a new Schema object must be created to contain all the items in the same position.

![Example of EDI items in the same position](https://support.edifabric.com/hc/article_attachments/360019419778/edi-all.png)  
*Example of EDI items in the same position*

This new Schema object must be marked with the `x-edination-group-type` extension property.

![Example of EDI grouping for items in the same position](https://support.edifabric.com/hc/article_attachments/4412316766737/edi-same-position.png)  
*Example of EDI grouping for items in the same position*

[List of available values for x-edination-group-type](https://github.com/EdiNation/OpenEDI-Specification/blob/main/README.md#additional-grouping-of-edi-loops-or-edi-segments)

Both the "same position container" and any of the items contained in it can be repeatable.

![Example of repeatable EDI items in the same position](https://support.edifabric.com/hc/article_attachments/360019419958/edi-repeat.png)  
*Example of repeatable EDI items in the same position*
