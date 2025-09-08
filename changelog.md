# Changelog: JSON for IO-Link REST API Specification

## V1 --> V2

### Introduced features

| Feature | Description |
|---|---|
| IO-Link Wireless | Support for Wireless IO-Link Masters and Devices added according to IO-Link Wireless System Extensions V1.1 |
| Monitor | Powersupply monitoring optional endpoints has been added. |
| IO-Link Device FW Update Profile | Performs the Device FW update procedure based on a .iolfw file according to ??? |
| Security schemes suggestions | The selected scheme and the way of restricting requests are the responsibility of the vendor. It is recommended to limit access to writable endpoint. |

### Additions

| Endpoint | Description |
|---|---|
| *[GET] /openapi* | Retrieves the OpenAPI interface description. |
| *[GET] /apiversion* | Retrieves the REST interface version. |
| *[GET] /gateway/diagnosis* | Retrieves the pending events. |
| *[GET] /gateway/monitor* | Retrieves current and voltage values of the gateway. Optional. |
| *[POST] /mqtt/topics/{topicId}* | Changes or deactivates a specific MQTT topic. |
| *[GET, POST] /masters/{masterNumber}/configuration* | Reads and writes IO-Link Wireless Master related configuration. |
| *[GET] /masters/{masterNumber}/trackstatus* | Reads the actual Track status of the specified Wireless-Master. |
| *[GET, POST] /masters/{masterNumber}/scan* | Handles Wireless Master track scanning procedure. |
| *[POST] /masters/{masterNumber}/ports/{portNumber}/pairing* | Pairs a Wireless-Device with the specified Wireless-Port. |
| *[GET] /masters/{masterNumber}/ports/{portNumber}/monitor* | Reads current and voltage or wireless info (depends on the Port type). |
| *[GET, POST] /devices/{deviceAlias}/fwupdate* | Performs Device FW Update procedure. |

#### Security

- Security schemes (`basicAuth`, `bearerAuth`, `oauth2`) defined in `components.securitySchemes`.

#### HTTP status codes and JSON for IO-Link error codes

- Response 401 introduced for each? endpoint.
- The JSON for IO-Link specific error schemas for 4xx and 5xx HTTP status codes has been updated. Allowed values are no longer provided as an example, they are part of the schema.

#### Schemas

##### *[GET] /gateway/identification*

- Response 200: New properties.

##### *[GET] /gateway/capabilities*

- Response 200: New MANDATORY property.

##### *[GET] /gateway/configuration*

- Response 200: New property, string patterns added.

##### *[POST] /gateway/configuration*

- Request body: New property, string patterns added.

---

### Breaking changes

#### Path Structure

- Major versioning has been increased, all endpoints are moved to basepath `/iolink/v2` instead of `/iolink/v1`.

#### Parameters

- Introduction of `parameterIdent` and `subParameterIdent` for more flexible addressing, replaced `{index}`, `{parameterName}`, `{subIndex}` and `{subParameterName}

#### OperationId and Tag

- Operation IDs and tags have been standardized and changed for many endpoints.
