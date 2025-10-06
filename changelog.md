# Changelog: JSON for IO-Link REST API Specification

## Symbols and abbreviated terms

- M/O/C - Mandatory/Optional/Conditional

## Version 2.0.0

### Introduced features

- Wireless extension according to *IO-Link Wireless System Extensions V1.1.3 - Order No: 10.112*
- IO-Link Device FW Update extension based on *IO-Link Profile BLOBs & FW-Update Version 1.2 - Order No: 10.082*
- Power supply monitoring.
- Security scheme suggestions. While the selected scheme and the way of restricting requests are the responsibility of the vendor. It is recommended to limit access to writable endpoint.

### Additions

| Endpoint | Description | M/O/C |
|---|---|---|
| *[GET] /openapi* | Retrieves the OpenAPI interface description. | M |
| *[GET] /apiversion* | Retrieves the REST interface version. | M |
| *[GET] /gateway/diagnosis* | Retrieves the pending events. | M |
| *[GET] /gateway/monitor* | Retrieves current and voltage values of the gateway. | O |
| *[POST] /mqtt/topics/{topicId}* | Changes or deactivates a specific MQTT topic. | C - MQTT support |
| *[GET] /masters/{masterNumber}/capabilities* | Separate response schema for IO-Link Wireless Master. | C - Wireless support |
| *[GET] /masters/{masterNumber}/configuration* | Reads IO-Link Wireless Master related configuration. | C - Wireless support |
| *[POST] /masters/{masterNumber}/configuration* | Writes IO-Link Wireless Master related configuration. | C - Wireless support |
| *[GET] /masters/{masterNumber}/trackstatus* | Reads the actual Track status of the specified Wireless-Master. | C - Wireless support |
| *[GET] /masters/{masterNumber}/scan* | Handles Wireless Master track scanning procedure. | C - Wireless support |
| *[POST] /masters/{masterNumber}/scan* | Handles Wireless Master track scanning procedure. | C - Wireless support |
| *[POST] /masters/{masterNumber}/rawsmi* | Sends an arbitrary SMI message. | O |
| *[POST] /masters/{masterNumber}/ports/{portNumber}/pairing* | Pairs a Wireless-Device with the specified Wireless-Port. | C - Wireless support |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/monitor* | Reads current and voltage or wireless info (depends on the Port type). | O / C - Wireless support |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/power* | Reads the current power mode of the specified port. | C - Class A with PortPowerOffOn |
| *[POST] /masters/{masterNumber}/ports/{portNumber}/power* | Sets the power mode of the specified port. | C - Class A with PortPowerOffOn |
| *[GET] /devices/{deviceAlias}/fwupdate* | Performs Device FW Update procedure. | C - Device FW Update support |
| *[POST] /devices/{deviceAlias}/fwupdate* | Performs Device FW Update procedure. | C - Device FW Update support |

#### Additions affecting each endpoint

- Added HTTP 401 status code as a possible response.
- Updated error schemas for 4xx/5xx codes; error codes now part of schema.
- Extended schemas with value range/length limitations.

### Modifications

Modifications are introduced in the parameter, request or response schemas.

| Endpoint | M/O/C |
|---|---|
| *[GET] /gateway/identification* | M |
| *[GET] /gateway/capabilties* |  M |
| *[GET] /gateway/configuration* | M |
| *[POST] /gateway/configuration* | M |
| *[GET] /gateway/events* | M |
| *[GET] /mqtt/configuration* | C - MQTT support |
| *[POST] /mqtt/configuration* | C - MQTT support |
| *[GET] /mqtt/topics* | C - MQTT support |
| *[POST] /mqtt/topics* | C - MQTT support |
| *[GET] /mqtt/topics/{topicID}* | C - MQTT support |
| *[GET] /iodds* | C - IODD support |
| *[DELETE] /iodds* | C - IODD support |
| *[GET] /iodds/file* | C - IODD support |
| *[GET] /masters/{masterNumber}/capabilities* | C - Wireless support |
| *[GET] /masters/{masterNumber}/identification* | M |
| *[GET] /masters/{masterNumber}/ports* | M / C - Wireless support |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/capabilities* | M / C - Wireless support |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/status* | M / C - Wireless support |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/configuration* | C - Wireless support |
| *[POST] /masters/{masterNumber}/ports/{portNumber}/configuration* | M / C - Wireless support |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/datastorage* | M |
| *[POST] /masters/{masterNumber}/ports/{portNumber}/datastorage* | M |
| *[GET] /devices* | C - IODD support |
| *[GET] /devices/{deviceAlias}/capabilities* | M |
| *[GET] /devices/{deviceAlias}/identification* | M / C - IODD support |
| *[GET] /devices/{deviceAlias}/processdata/value* | M / C - IODD support |
| *[POST] /devices/{deviceAlias}/processdata/value* | M / C - IODD support |
| *[GET] /devices/{deviceAlias}/processdata/getdata/value* | M / C - IODD support |
| *[POST] /devices/{deviceAlias}/processdata/getdata/value* | M / C - IODD support |
| *[GET] /devices/{deviceAlias}/parameters* | C - IODD support |
| *[GET] /devices/{deviceAlias}/parameters/{parameterIdent}/value* | C - IODD support |
| *[POST] /devices/{deviceAlias}/parameters/{parameterIdent}/value* | C - IODD support |
| *[GET] /devices/{deviceAlias}/parameters/{parameterIdent}/subindices/{subParameterIdent}/value* | C - IODD support |
| *[POST] /devices/{deviceAlias}/parameters/{parameterIdent}/subindices/{subParameterIdent}/value* | C - IODD support |
| *[POST] /devices/{deviceAlias}/blockparameterization* | C - IODD support |
| *[POST] /devices/{deviceAlias}/events* | M |

#### OperationId and Tag

- Operation IDs and tags have been standardized and changed.

#### Path Structure

- URL parameters *{index}*, *{parameterName}* → *{parameterIdent}*
- URL parameters *{subIndex}*, *{subParameterName}* → *{subParameterIdent}*
- Major versioning has been increased, all endpoints moved to basepath `/iolink/v2` from `/iolink/v1`.

#### Discrepancies in version 1.0.0

Property names differed between PDF and YAML in v1.0.0.

| PDF location | PDF | YAML v1.0.0 | YAML v2.0.0 |
|-|-|-|-|
| Table 38 | iolinkRevision | ioLinkRevision | iolinkRevision |
| Table 54 | iolinkRevision | ioLinkRevision | iolinkRevision |
| Table 60 | iolink | ioLink | iolink |
