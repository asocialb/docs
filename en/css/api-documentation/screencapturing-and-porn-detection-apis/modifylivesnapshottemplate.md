# ModifyLiveSnapshotTemplate

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to modify the screencapturing template configuration.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: ModifyLiveSnapshotTemplate. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| TemplateId | Yes | Integer | Template ID. |
| CosAppId | Yes | Integer | The COS application ID. **Please note that this parameter is required now**. |
| CosBucket | Yes | String | The COS bucket name. Note: Do not include the `-[appid]` part in the value of `CosBucket`. **Please note that this parameter is required now**. |
| CosRegion | Yes | String | The COS region. **Please note that this parameter is required now**. |
| TemplateName | No | String | Template name. Maximum length: 255 bytes. |
| Description | No | String | Description. Maximum length: 1,024 bytes. |
| SnapshotInterval | No | Integer | Screencapturing interval in seconds. Default value: 10s. Value range: 5-300s. |
| Width | No | Integer | Screenshot width. Default value: 0 (original width). |
| Height | No | Integer | Screenshot height. Default value: 0 (original height). |
| PornFlag | No | Integer | Whether to enable porn detection. Default value: 0. 0: do not enable. 1: enable. |
| CosPrefix | No | String | COS bucket folder prefix. |
| CosFileName | No | String | COS filename. |

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
X-TC-Action: ModifyLiveSnapshotTemplate
<Common request parameters>

{
    "CosRegion": "beijing",
    "Description": "testDesc",
    "SnapshotInterval": "10",
    "PornFlag": "0",
    "CosBucket": "bucket",
    "TemplateName": "testName",
    "Height": "250",
    "CosAppId": "123",
    "Width": "250",
    "TemplateId": "1000"
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
| FailedOperation.CosBucketNotExist | The COS bucket does not exist. |
| FailedOperation.CosBucketNotPermission | You don’t have permission to access the COS bucket. |
| FailedOperation.CosRoleNotExists | The COS role does not exist. Please go to the “Feature Configuration > Live Screencapture & Porn Detection” page of the CSS console to grant the permission. |
| FailedOperation.NotFound | No records found. |
| InternalError | Internal error. |
| InternalError.ArgsNotMatch | For the transcoding template adding API. |
| InternalError.ConfInUsed | The template is in use. |
| InternalError.ConfNotFound | The template does not exist. |
| InternalError.InvalidInput | Parameter check failed. |
| InternalError.NotFound | The record does not exist. |
| InternalError.RuleAlreadyExist | The rule has already been configured. |
| InternalError.RuleInUsing | The rule is in use. |
| InternalError.RuleNotFound | The rule does not exist. |
| InvalidParameter | Invalid parameter. |
| InvalidParameter.COSCustomFileNameError | Incorrect custom COS filename. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| UnsupportedOperation.NotLVBCodeMode | Not a LVB code/new console mode |


---
*Source: [https://www.tencentcloud.com/document/product/267/30828](https://www.tencentcloud.com/document/product/267/30828)*
