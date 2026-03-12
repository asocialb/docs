# CreateLiveSnapshotTemplate

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to create a screencapture template. After a template ID is returned, you need to call the [CreateLiveSnapshotRule](https://intl.cloud.tencent.com/document/product/267/32625?from_cn_redirect=1) API to bind the template ID to a stream. You can create up to 50 screencapture templates.

To learn more about the live screencapture feature, see [Live Screencapture](https://intl.cloud.tencent.com/document/product/267/32737?from_cn_redirect=1).

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: CreateLiveSnapshotTemplate. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| TemplateName | Yes | String | Template name. |
| CosAppId | Yes | Integer | COS application ID. |
| CosBucket | Yes | String | COS bucket name. Note: the value of `CosBucket` cannot contain `-[appid]`. |
| CosRegion | Yes | String | COS region. |
| Description | No | String | Description. Maximum length: 1,024 bytes. Only letters, digits, underscores, and hyphens can be contained. |
| SnapshotInterval | No | Integer | Screencapturing interval (s). Default value: 10 Value range: 2-300 |
| Width | No | Integer | Screenshot width. Default value: `0` (original width) Value range: 0-3000 |
| Height | No | Integer | Screenshot height. Default value: `0` (original height) Value range: 0-2000 |
| PornFlag | No | Integer | Whether to enable porn detection. 0: no, 1: yes. Default value: 0 |
| CosPrefix | No | String | COS Bucket folder prefix. If no value is entered, the default value `/{Year}-{Month}-{Day}` will be used. |
| CosFileName | No | String | COS filename. If no value is entered, the default value  `{StreamID}-screenshot-{Hour}-{Minute}-{Second}-{Width}x{Height}{Ext}` will be used. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TemplateId | Integer | Template ID. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateLiveSnapshotTemplate
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
    "Width": "250"
}
```

#### Output Example

```json
{
    "Response": {
        "TemplateId": 1000,
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
| InternalError | Internal error. |
| InternalError.ArgsNotMatch | For the transcoding template adding API. |
| InternalError.ConfInUsed | The template is in use. |
| InternalError.ConfNotFound | The template does not exist. |
| InternalError.ConfOutLimit | The number of templates exceeded the limit. |
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
*Source: [https://www.tencentcloud.com/document/product/267/30834](https://www.tencentcloud.com/document/product/267/30834)*
