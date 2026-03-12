# CreateLiveCallbackTemplate

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to create a callback template. Up to 50 templates can be created. After the template ID is returned, you need to call the [CreateLiveCallbackRule](https://intl.cloud.tencent.com/document/product/267/32638?from_cn_redirect=1) API to bind the template ID to a domain name/path.

For information about callback protocols, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/32744?from_cn_redirect=1).
Note: You need to specify at least one callback URL.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: CreateLiveCallbackTemplate. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| TemplateName | Yes | String | Template name. |
| Description | No | String | Description. |
| StreamBeginNotifyUrl | No | String | Stream starting callback URL, Protocol document: [Event Message Notification](https://intl.cloud.tencent.com/document/product/267/32744?from_cn_redirect=1). |
| StreamEndNotifyUrl | No | String | Interruption callback URL, Protocol document: [Event Message Notification](https://intl.cloud.tencent.com/document/product/267/32744?from_cn_redirect=1). |
| RecordNotifyUrl | No | String | Recording callback URL, Protocol document: [Event Message Notification](https://intl.cloud.tencent.com/document/product/267/32744?from_cn_redirect=1). |
| SnapshotNotifyUrl | No | String | Screencapturing callback URL, Protocol document: [Event Message Notification](https://intl.cloud.tencent.com/document/product/267/32744?from_cn_redirect=1). |
| PornCensorshipNotifyUrl | No | String | Porn detection callback URL, Protocol document: [Event Message Notification](https://intl.cloud.tencent.com/document/product/267/32741?from_cn_redirect=1). |
| CallbackKey | No | String | Callback key. The callback URL is public. For the callback signature, please see the event message notification document. [Event Message Notification](https://intl.cloud.tencent.com/document/product/267/32744?from_cn_redirect=1). |
| StreamMixNotifyUrl | No | String | Disused |
| PushExceptionNotifyUrl | No | String | The push error callback URL. |

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
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateLiveCallbackTemplate
<Common request parameters>

{
    "StreamBeginNotifyUrl": "http://www.yourdomain.com/api/notify?action=streamBegin",
    "StreamEndNotifyUrl": "http://www.yourdomain.com/api/notify?action=streamEnd",
    "TemplateName": "testName",
    "RecordNotifyUrl": "http://www.yourdomain.com/api/notify?action=record",
    "SnapshotNotifyUrl": "http://www.yourdomain.com/api/notify?action=snapshot",
    "PornCensorshipNotifyUrl": "http://www.yourdomain.com/api/notify?action=porn",
    "CallbackKey": "adasda131312",
    "Description": "test"
}
```

#### Output Example

```
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://intl.cloud.tencent.com/document/api/267/30851#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation.ConfInUsed | The template is in use. |
| FailedOperation.NotFound | No records found. |
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
| InvalidParameter.ArgsNotMatch | Incorrect template name. |
| InvalidParameter.COSCustomFileNameError | Incorrect custom COS filename. |
| InvalidParameter.InvalidVodFileName | Incorrect `VodFileName`. |
| InvalidParameter.UrlNotSafe | Failed to resolve the domain name. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| UnsupportedOperation.NotLVBCodeMode | Not a LVB code/new console mode |


---
*Source: [https://www.tencentcloud.com/document/product/267/30815](https://www.tencentcloud.com/document/product/267/30815)*
