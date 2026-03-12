# ModifyLiveRecordTemplate

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to modify the recording template configuration.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: ModifyLiveRecordTemplate. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| TemplateId | Yes | Integer | Template ID obtained through the `DescribeRecordTemplates` API. |
| TemplateName | No | String | Template name. |
| Description | No | String | Message description |
| FlvParam | No | [RecordParam](https://www.tencentcloud.com/document/api/267/30767#RecordParam) | FLV recording parameter, which is set when FLV recording is enabled. |
| HlsParam | No | [RecordParam](https://www.tencentcloud.com/document/api/267/30767#RecordParam) | HLS recording parameter, which is set when HLS recording is enabled. |
| Mp4Param | No | [RecordParam](https://www.tencentcloud.com/document/api/267/30767#RecordParam) | MP4 recording parameter, which is set when MP4 recording is enabled. |
| AacParam | No | [RecordParam](https://www.tencentcloud.com/document/api/267/30767#RecordParam) | AAC recording parameter, which is set when AAC recording is enabled. |
| HlsSpecialParam | No | [HlsSpecialParam](https://www.tencentcloud.com/document/api/267/30767#HlsSpecialParam) | Custom HLS recording parameter. |
| Mp3Param | No | [RecordParam](https://www.tencentcloud.com/document/api/267/30767#RecordParam) | MP3 recording parameter, which is set when MP3 recording is enabled. |
| RemoveWatermark | No | Boolean | Whether to remove the watermark. This parameter is invalid if `IsDelayLive` is `1`. |
| FlvSpecialParam | No | [FlvSpecialParam](https://www.tencentcloud.com/document/api/267/30767#FlvSpecialParam) | A special parameter for FLV recording. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=ModifyLiveRecordTemplate
&TemplateName=templat
&Description=test
&FlvParam.Enable=1
&FlvParam.RecordInterval=1800
&FlvParam.StorageTime=700
&TemplateId=1000
&<Common request parameters>
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
| InvalidParameter.InvalidVodFileName | Incorrect `VodFileName`. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30838](https://www.tencentcloud.com/document/product/267/30838)*
