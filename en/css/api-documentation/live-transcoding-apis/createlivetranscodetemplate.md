# CreateLiveTranscodeTemplate

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to create a transcoding template. Up to 50 transcoding templates can be created in total. To use a template, you need to call [CreateLiveTranscodeRule](https://intl.cloud.tencent.com/document/product/267/32647?from_cn_redirect=1) to bind the template ID returned by this API to a stream.

For more information about transcoding, see [Live Remuxing and Transcoding](https://intl.cloud.tencent.com/document/product/267/32736?from_cn_redirect=1).

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: CreateLiveTranscodeTemplate. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| TemplateName | Yes | String | Template name, such as “900p”. This can be only a combination of letters and digits. |
| VideoBitrate | Yes | Integer | Video bitrate in Kbps. Value range: 100-8000. Note: the transcoding template requires that the bitrate be unique. Therefore, the final saved bitrate may be different from the input bitrate. |
| Acodec | No | String | Audio codec. Default value: aac. Note: this parameter is unsupported now. |
| AudioBitrate | No | Integer | Audio bitrate. Default value: 0. Value range: 0-500. |
| Vcodec | No | String | Video codec. Valid values: h264, h265, origin (default)  origin: original codec as the output codec |
| Description | No | String | Template description. |
| NeedVideo | No | Integer | Whether to keep the video. 0: no; 1: yes. Default value: 1. |
| Width | No | Integer | Width. Default value: 0. Value range: 0-3000 It must be a multiple of 2. The original width is 0. |
| NeedAudio | No | Integer | Whether to keep the audio. 0: no; 1: yes. Default value: 1. |
| Height | No | Integer | Height. Default value: 0 Value range: 0-3000 The value must be a multiple of 2. The original height is `0`. This parameter is required for a top speed codec template (when `AiTransCode` is `1`). |
| Fps | No | Integer | Frame rate. Default value: 0. Value range: 0-60 |
| Gop | No | Integer | Keyframe interval in seconds. Default value: original interval Value range: 2-6 |
| Rotate | No | Integer | Rotation angle. Default value: 0. Valid values: 0, 90, 180, 270 |
| Profile | No | String | Encoding quality: baseline/main/high. Default value: baseline. |
| BitrateToOrig | No | Integer | Whether to use the original bitrate when the set bitrate is larger than the original bitrate. 0: no, 1: yes Default value: 0. |
| HeightToOrig | No | Integer | Whether to use the original height when the set height is higher than the original height. 0: no, 1: yes Default value: 0. |
| FpsToOrig | No | Integer | Whether to use the original frame rate when the set frame rate is larger than the original frame rate. 0: no, 1: yes Default value: 0. |
| AiTransCode | No | Integer | Whether it is a top speed codec template. 0: no, 1: yes. Default value: 0. |
| AdaptBitratePercent | No | Float | Bitrate compression ratio of top speed codec video. Target bitrate of top speed code = VideoBitrate * (1-AdaptBitratePercent)  Value range: 0.0-0.5. |
| ShortEdgeAsHeight | No | Integer | Whether to use the short side as the video height. 0: no, 1: yes. Default value: 0. |
| DRMType | No | String | The DRM encryption type. Valid values: fairplay, normalaes, widevine. If you do not pass this parameter or pass in an empty string, the existing configuration will be reset. |
| DRMTracks | No | String | The tracks to encrypt. Valid values: AUDIO, SD, HD, UHD1, UHD2. You can choose only one video track (SD, HD, UHD1, or UHD2). If you do not pass this parameter or pass in an empty string, the existing configuration will be reset. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TemplateId | Integer | Template ID. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Creating a transcoding template

This example shows you how to create a transcoding template.

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateLiveTranscodeTemplate
<Common request parameters>

{
    "Profile": "main",
    "AudioBitrate": "500",
    "Rotate": "0",
    "Description": "test",
    "TemplateName": "900m",
    "VideoBitrate": "900",
    "Vcodec": "h264",
    "Height": "250",
    "Width": "250",
    "NeedAudio": "1",
    "FpsToOrig": "0",
    "Fps": "30",
    "BitrateToOrig": "0",
    "HeightToOrig": "0",
    "NeedVideo": "1",
    "Gop": "3",
    "Acodec": "aac"
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
| FailedOperation.AiTranscodeOptionFail | Failed to manipulate the AI API. |
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| InternalError | Internal error. |
| InternalError.ArgsNotMatch | For the transcoding template adding API. |
| InternalError.ConfInUsed | The template is in use. |
| InternalError.ConfNotFound | The template does not exist. |
| InternalError.ConfOutLimit | The number of templates exceeded the limit. |
| InternalError.InvalidInput | Parameter check failed. |
| InternalError.NotFound | The record does not exist. |
| InternalError.ProcessorAlreadyExist | The transcoding template name already exists. |
| InternalError.RuleAlreadyExist | The rule has already been configured. |
| InternalError.RuleInUsing | The rule is in use. |
| InternalError.RuleNotFound | The rule does not exist. |
| InvalidParameter | Invalid parameter. |
| InvalidParameter.ArgsNotMatch | Incorrect template name. |
| InvalidParameter.GopMustEqualAndExists | The GOP of an adaptive bitrate template is required and must be the same for each stream. |
| InvalidParameter.ProcessorAlreadyExist | Transcoding template already exists. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| UnsupportedOperation.NotLVBCodeMode | Not a LVB code/new console mode |


---
*Source: [https://www.tencentcloud.com/document/product/267/30790](https://www.tencentcloud.com/document/product/267/30790)*
