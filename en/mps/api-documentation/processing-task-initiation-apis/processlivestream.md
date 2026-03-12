# ProcessLiveStream

## 1. API Description

Domain name for API request: mps.intl.tencentcloudapi.com.

This API is used to initiate a processing task for live streaming. Features include:.

Intelligent content moderation (porn detection in images, sensitive information detection, audio pornography detection);.

Smart content recognition (human faces, full texts, text keywords, full speech, speech keywords, real-time speech translation, object recognition, game tagging).
Intelligent content analysis (clipping, highlights).
Quality inspection (live stream format diagnosis, audio and video content detection (jitter, blur, low light, overexposure, black and white edges, black and white screens, screen glitch, noise, mosaic, QR code, and more), and no-reference scoring).
recording.

Live stream processing event notification supports HTTP callback and also supports real-time writing to user-specified TDMQ CMQ. Users obtain event notification results from TDMQ CMQ. Meanwhile, if output files exist during the process, they will be written to the target storage specified by the user.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/1041/33628).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: ProcessLiveStream. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: 2019-06-12. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). This parameter is not required for this API. |
| Url | Yes | String | Live streaming URL (must be a live stream address, supports rtmp, hls, flv, trtc, webrtc, and srt). |
| TaskNotifyConfig | Yes | [LiveStreamTaskNotifyConfig](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamTaskNotifyConfig) | Event notification information of a task, which is used to specify the live stream processing result. |
| OutputStorage | No | [TaskOutputStorage](https://www.tencentcloud.com/document/api/1041/33690#TaskOutputStorage) | Target bucket of a live stream processing output file. This parameter is required if a file will be output. |
| OutputDir | No | String | Target directory of a live stream processing output file, such as `/movie/201909/`. If this parameter is left empty, the `/` directory will be used. |
| AiContentReviewTask | No | [AiContentReviewTaskInput](https://www.tencentcloud.com/document/api/1041/33690#AiContentReviewTaskInput) | Type parameter of a video content audit task. |
| AiRecognitionTask | No | [AiRecognitionTaskInput](https://www.tencentcloud.com/document/api/1041/33690#AiRecognitionTaskInput) | Type parameter of video content recognition task. |
| AiAnalysisTask | No | [AiAnalysisTaskInput](https://www.tencentcloud.com/document/api/1041/33690#AiAnalysisTaskInput) |  |
| AiQualityControlTask | No | [AiQualityControlTaskInput](https://www.tencentcloud.com/document/api/1041/33690#AiQualityControlTaskInput) | Media quality inspection type task parameters. |
| SmartSubtitlesTask | No | [LiveSmartSubtitlesTaskInput](https://www.tencentcloud.com/document/api/1041/33690#LiveSmartSubtitlesTaskInput) | Smart subtitling task parameter. |
| SessionId | No | String | The ID used for deduplication. If there was a request with the same ID in the last seven days, the current request will return an error. The ID can contain up to 50 characters. If this parameter is left empty or an empty string is entered, no deduplication will be performed. |
| SessionContext | No | String | The source context which is used to pass through the user request information. The task flow status change callback will return the value of this field. It can contain up to 1,000 characters. |
| ScheduleId | No | Integer | The live scheme ID. Note 1: If an output storage (`OutputStorage`) and directory (`OutputDir`) are specified for a subtask of the scheme, those output settings will be applied.  u200cIf an output storage (`OutputStorage`) and directory (`OutputDir`) are not specified for a subtask of the scheme, the output parameters specified for `ProcessLiveStream` (if any) will be applied.  Note 2: If `TaskNotifyConfig` is specified when `ProcessLiveStream` is called, the specified settings will be applied instead of the default callback settings of the scheme. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Task ID |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Initiating a Live Stream Identification Task

Trigger a content recognition task for the live stream with the URL http://www.abc.com/abc.m3u8.

#### Input Example

```
POST / HTTP/1.1
Host: mps.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ProcessLiveStream
<Common request parameters>

{
    "Url": "http://www.abc.com/abc.m3u8",
    "AiRecognitionTask": {
        "Definition": 10
    },
    "TaskNotifyConfig": {
        "CmqRegion": "gz",
        "CmqModel": "Queue",
        "QueueName": "queue-125717729292"
    }
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "5ca61e3a-6b8e-4b4e-9256-fdc701190064ef0",
        "TaskId": "125xxxxxx07-live-procedure-813dc41e6fdc22dcf24aa6e9c61cp92"
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/1041/33691#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation.GenerateResource | Resource generation failed. |
| FailedOperation.InvalidMpsUser | Operation failed: unauthorized MPS user. |
| InternalError | Internal error. |
| InvalidParameter | Parameter error. |
| InvalidParameterValue.Definition | Parameter error: Definition. |
| InvalidParameterValue.Definitions | Parameter error: Definitions. |
| InvalidParameterValue.SessionId | The deduplication ID already exists. The request is removed due to duplication. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33641](https://www.tencentcloud.com/document/product/1041/33641)*
