# DescribeLiveTranscodeTemplates

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to get the transcoding template list.

A maximum of 500 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeLiveTranscodeTemplates. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| Templates | Array of [TemplateInfo](https://www.tencentcloud.com/document/api/267/30767#TemplateInfo) | List of transcoding templates. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeLiveTranscodeTemplates
<Common request parameters>

{}
```

#### Output Example

```json
{
    "Response": {
        "Templates": [
            {
                "Width": 250,
                "Fps": 30,
                "TemplateId": 1000,
                "Gop": 3,
                "Acodec": "xx",
                "Profile": "xx",
                "Description": "xx",
                "VideoBitrate": 30,
                "BitrateToOrig": 0,
                "AiTransCode": 0,
                "HeightToOrig": 0,
                "AudioBitrate": 15,
                "Rotate": 0,
                "TemplateName": "xx",
                "AdaptBitratePercent": 0.0,
                "Vcodec": "xx",
                "NeedAudio": 1,
                "DRMTracks": "xx",
                "NeedVideo": 1,
                "DRMType": "xx",
                "ShortEdgeAsHeight": 0,
                "Height": 250,
                "FpsToOrig": 0
            }
        ],
        "RequestId": "xx"
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
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| UnsupportedOperation.NotLVBCodeMode | Not a LVB code/new console mode |


---
*Source: [https://www.tencentcloud.com/document/product/267/30785](https://www.tencentcloud.com/document/product/267/30785)*
