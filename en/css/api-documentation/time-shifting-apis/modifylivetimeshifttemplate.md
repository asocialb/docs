# ModifyLiveTimeShiftTemplate

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to modify a time shifting template.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: ModifyLiveTimeShiftTemplate. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| TemplateId | Yes | Integer | The time shifting template ID. |
| TemplateName | No | String | The template name. Only letters, numbers, underscores, and hyphens are supported. |
| Description | No | String | The template description. Maximum length: 1,024 bytes. Only letters, numbers, underscores, and hyphens are supported. |
| Duration | No | Integer | The time shifting duration. Unit: Second. |
| ItemDuration | No | Integer | The segment size. Value range: 3-10. Unit: Second. Default value: 5 |
| RemoveWatermark | No | Boolean | Whether to remove watermarks. If you pass in `true`, the original stream will be recorded. Default value: `false`. |
| TranscodeTemplateIds.N | No | Array of Integer | The transcoding template IDs. This API works only if `RemoveWatermark` is `false`. |
| Area | No | String | The region. `Mainland`: The Chinese mainland. `Overseas`: Outside the Chinese mainland. Default value: `Mainland`. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ModifyLiveTimeShiftTemplate
<Common Request Parameters>

{
    "Description": "xx",
    "TranscodeTemplateIds": [
        0
    ],
    "RemoveWatermark": true,
    "TemplateName": "xx",
    "ItemDuration": 1,
    "TemplateId": 1,
    "Duration": 1,
    "Area": "xx"
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "3c140219-cfe9-470e-b241-907877d6fb03"
    }
}
```

## 5. Developer Resources

### SDK

TencentCloud API 3.0 integrates SDKs that support various programming languages to make it easier for you to call APIs.

Tencent Cloud SDK 3.0 for Python
Tencent Cloud SDK 3.0 for Java
Tencent Cloud SDK 3.0 for PHP
Tencent Cloud SDK 3.0 for Go
Tencent Cloud SDK 3.0 for Node.js
Tencent Cloud SDK 3.0 for .NET
Tencent Cloud SDK 3.0 for C++

### Command Line Interface

Tencent Cloud CLI 3.0

## 6. Error Code

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/267/30851#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| InternalError | Internal error. |
| InternalError.ArgsNotMatch | For the transcoding template adding API. |
| InternalError.ConfInUsed | The template is in use. |
| InternalError.ConfNotFound | The template does not exist. |
| InternalError.ConfOutLimit | The number of templates exceeded the limit. |
| InternalError.InvalidInput | Parameter check failed. |
| InternalError.NotFound | The record does not exist. |
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| UnsupportedOperation.NotLVBCodeMode | Not a LVB code/new console mode |


---
*Source: [https://www.tencentcloud.com/document/product/267/53718](https://www.tencentcloud.com/document/product/267/53718)*
