# Api Documentation
Api Documentation

## Version: 1.0

### Terms of service
urn:tos


**License:** [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0)

### /api/v2/canonical_id

#### GET
##### Summary:

Generate a canonical values for different type of user ids

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| encryptionKey | query | Encryption key. If omitted, encryption versions will not be generated | No | string |
| id | query | ID of a user | No | string |
| type | query | Type of user id. See https://docs.ksense.ai/javascript-pixel/user-identification-calls#parameters-and-encryption for further information | No | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Canonical ids successfully generated | [JSON response](#json-response) |
| 400 | Error occurred (details will be provided in response body as json) |  |

### /api/v2/user_info

#### GET
##### Summary:

userInfo

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | OK |

### Models


#### JSON response

Please see examples for JSON structure

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| JSON response | object | Please see examples for JSON structure |  |
