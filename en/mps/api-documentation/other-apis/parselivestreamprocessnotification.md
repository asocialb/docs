# ParseLiveStreamProcessNotification

## 1. API Description

Domain name for API request: mps.intl.tencentcloudapi.com.

This API is used to parse the content of an MPS live stream processing event notification from the `msgBody` field in the message received from CMQ.
Instead of initiating a video processing task, this API is used to help generate SDKs for various programming languages. You can parse the event notification based on the analytic function of the SDKs.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/1041/33628).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: ParseLiveStreamProcessNotification. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: 2019-06-12. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). This parameter is not required for this API. |
| Content | Yes | String | Live stream event notification obtained from CMQ. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| NotificationType | String | Live stream processing result type, including:. |
| TaskId | String | Video processing task ID. |
| ProcessEofInfo | [LiveStreamProcessErrorInfo](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamProcessErrorInfo) | Information of a live stream processing error, which is valid when `NotificationType` is `ProcessEof`. Note: when this field return null, means no valid values can be obtained. |
| AiReviewResultInfo | [LiveStreamAiReviewResultInfo](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamAiReviewResultInfo) | Content audit result, which is valid when `NotificationType` is `AiReviewResult`. Note: when this field return null, means no valid values can be obtained. |
| AiRecognitionResultInfo | [LiveStreamAiRecognitionResultInfo](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamAiRecognitionResultInfo) | Content recognition result, which is valid if `NotificationType` is `AiRecognitionResult`. |
| AiAnalysisResultInfo | [LiveStreamAiAnalysisResultInfo](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamAiAnalysisResultInfo) | Content analysis result, which is valid if `NotificationType` is `AiAnalysisResult`. |
| AiQualityControlResultInfo | [LiveStreamAiQualityControlResultInfo](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamAiQualityControlResultInfo) | Media quality inspection result, which is valid if `NotificationType` is `AiQualityControlResult`. |
| LiveRecordResultInfo | [LiveStreamRecordResultInfo](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamRecordResultInfo) | Live recording result is valid when NotificationType is LiveRecordResult. Note: when this field return null, means no valid values can be obtained. |
| AiSmartSubtitleResultInfo | [LiveStreamAiSmartSubtitleResultInfo](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamAiSmartSubtitleResultInfo) | Smart subtitle result. valid when NotificationType is AiSmartSubtitleResult. |
| SessionId | String | The ID used for deduplication. If there was a request with the same ID in the last seven days, the current request will return an error. The ID can contain up to 50 characters. If this parameter is left empty or an empty string is entered, no deduplication will be performed. |
| SessionContext | String | The source context which is used to pass through the user request information. The task flow status change callback will return the value of this field. It can contain up to 1,000 characters. |
| Timestamp | Integer | - expiration time, event notification signature expiration in UNIX Timestamp format. - notifications from media processing default to an expiration time of 10 minutes. if the time specified by the Timestamp value in a message notification has expired, the notification can be deemed invalid, furthermore preventing network replay attacks. - the Timestamp format is decimal UNIX Timestamp, seconds elapsed since midnight (UTC/GMT) on january 1, 1970. |
| Sign | String | Event notification security signature. Sign = MD5 (Timestamp + NotifyKey). Note: Media Processing Service concatenates Timestamp and NotifyKey from TaskNotifyConfig as a string and calculates the Sign value through MD5. This value is included in the notification message. Your backend server can verify whether the Sign is correct using the same algorithm, to confirm whether the message is indeed from the Media Processing Service backend. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Parse Live Stream Event Notification Content

Callback body description

#### Input Example

```
https://mps.intl.tencentcloudapi.com/?Action=ParseLiveStreamProcessNotification
&Content={"NotificationType":"AiReviewResult",XXX
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "NotificationType": "AiReviewResult",
        "TaskId": "2459149217-procedure-live-xxx51da009t0",
        "ProcessEofInfo": null,
        "AiReviewResultInfo": {
            "ResultSet": [
                {
                    "Type": "VoicePorn",
                    "ImagePornResultSet": [],
                    "ImageTerrorismResultSet": [],
                    "ImagePoliticalResultSet": [],
                    "VoicePornResultSet": [
                        {
                            "StartPtsTime": 0.266,
                            "EndPtsTime": 4.146,
                            "Confidence": 98,
                            "Suggestion": "block",
                            "Label": "sexual_moan"
                        }
                    ]
                }
            ]
        },
        "AiRecognitionResultInfo": null,
        "AiAnalysisResultInfo": null,
        "AiQualityControlResultInfo": null,
        "SessionId": "",
        "SessionContext": "",
        "RequestId": "335bdaa3-db0e-46ce-9946-51941d9cb0f5"
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
| FailedOperation.InvalidMpsUser | Operation failed: unauthorized MPS user. |
| InvalidParameterValue.InvalidContent | The value of the parsed `Content` is invalid. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33680](https://www.tencentcloud.com/document/product/1041/33680)*
