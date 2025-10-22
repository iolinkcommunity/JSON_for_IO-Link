# Changelog: JSON for IO-Link REST API Specification

## Symbols and abbreviated terms

- M/O/C - Mandatory/Optional/Conditional

## Version 2.0.0

### Introduced features

- Wireless extension according to *IO-Link Wireless System Extensions V1.1.3 - Order No: 10.112*
- IO-Link Device FW Update extension, Host-side protocol. Based on *IO-Link Profile BLOBs & FW-Update Version 1.2 - Order No: 10.082*
- Power supply monitoring.
- Security scheme suggestions. While the selected scheme and the way of restricting requests are the responsibility of the vendor. It is recommended to limit access to writable endpoints.

### Additions

#### OpenAPI 3 document

New endpoints have been added to the existing ones.
Endpoints marked as M must be implemented.
Mandatory endpoint with a note must be implemented if the indicated optional feature is available on the gateway (GET /gateway/capabilities) or applies for that Master/Port.

| Endpoint | Description | M/O/C |
|---|---|---|
| *[GET] /openapi* | Retrieves the OpenAPI interface description. | M |
| *[GET] /apiversion* | Retrieves the REST interface version. | M |
| *[GET] /gateway/diagnosis* | Retrieves the pending events. | M |
| *[GET] /gateway/monitor* | Retrieves current and voltage values of the gateway. | O |
| *[POST] /mqtt/topics/{topicId}* | Changes or deactivates a specific MQTT topic. | M - MQTT support |
| *[GET] /masters/{masterNumber}/capabilities* | Separate response schema for IO-Link Wireless Master. | M - For Wireless Masters |
| *[GET] /masters/{masterNumber}/configuration* | Reads IO-Link Wireless Master related configuration. | M - For Wireless Masters |
| *[POST] /masters/{masterNumber}/configuration* | Writes IO-Link Wireless Master related configuration. | M - For Wireless Masters |
| *[GET] /masters/{masterNumber}/trackstatus* | Reads the actual Track status of the specified Wireless-Master. | M - For Wireless Masters |
| *[GET] /masters/{masterNumber}/scan* | Handles Wireless Master track scanning procedure. | M - For Wireless Masters |
| *[POST] /masters/{masterNumber}/scan* | Handles Wireless Master track scanning procedure. | M - For Wireless Masters |
| *[POST] /masters/{masterNumber}/rawsmi* | Sends an arbitrary SMI message. | O |
| *[POST] /masters/{masterNumber}/ports/{portNumber}/pairing* | Pairs a Wireless-Device with the specified Wireless-Port. | M - For Wireless Ports |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/monitor* | Reads current and voltage or wireless info (depends on the Port type). | O - For Wired Ports / M - For Wireless Ports |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/power* | Reads the current power mode of the specified port. | C - For Class A with PortPowerOffOn or Class B Ports |
| *[POST] /masters/{masterNumber}/ports/{portNumber}/power* | Sets the power mode of the specified port. | C - For Class A with PortPowerOffOn or Class B Ports|
| *[GET] /devices/{deviceAlias}/fwupdate* | Performs Device FW Update procedure. | M - Device FW Update support |
| *[POST] /devices/{deviceAlias}/fwupdate* | Performs Device FW Update procedure. | M - Device FW Update support |

##### Additions affecting each endpoint

- Added HTTP 401 status code as a possible response.
- Updated error schemas for 4xx/5xx codes; error codes now part of schema.
- Extended schemas with value range/length limitations.

#### Async API document

New specification available.
The Async API document, called `MQTT_for_IO-Link.yaml`, which describes the MQTT interface.

### Modifications

Modifications are introduced in the parameter, request or response schemas for almost every endpoint. Please revise your implementation.

#### OperationId and Tag

Operation IDs and tags have been standardized.

#### Path Structure

- URL parameters *{index}*, *{parameterName}* → *{parameterIdent}*
- URL parameters *{subIndex}*, *{subParameterName}* → *{subParameterIdent}*
- Major versioning has been increased, all endpoints moved to basepath `/iolink/v2` from `/iolink/v1`.

### Clarifications

#### Optional features

Optional features are defined in the OpenAPI document under GET /gateway/capabilities. If an optional feature is indicated as supported all optional feature related endpoints are mandatory, unless stated otherwise.

#### Discrepancies in version 1.0.0

Property names differed between the PDF and the OpenAPI document in v1.0.0.

| PDF location | PDF | OpenAPI v1.0.0 | OpenAPI v2.0.0 |
|-|-|-|-|
| Table 38 | iolinkRevision | ioLinkRevision | iolinkRevision |
| Table 54 | iolinkRevision | ioLinkRevision | iolinkRevision |
| Table 60 | iolink | ioLink | iolink |
