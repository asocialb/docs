# CreateCloudRecording

## 1. API Description

Domain name for API request: trtc.intl.tencentcloudapi.com.

API description:.
Start on-cloud recording to complete audio and video recording in the room and upload to designated cloud storage. This API is used to record each audio and video stream in the TRTC room separately or merge multiple video images into one stream.
Before official online operation, pay attention to the recording best practices (https://www.tencentcloud.comom/document/product/647/76497?from_cn_redirect=1#e7e2f04c-6cde-43c9-9cd0-0f8d22dee68c). In conjunction with best practices, it can greatly improve API recording availability.

This API is used to achieve the following goals:.
Specify the subscription stream parameter (RecordParams) to specify the blocklist or allowlist of anchors that need to be recorded.

This API is used to specify the storage parameter (StorageParams) to specify the cloud storage you want to upload to. Currently, Tencent Cloud Video on Demand (VOD), Cloud Object Storage (COS), and third-party AWS are supported.
Specify detailed parameters for audio and video transcoding in mixed-stream mode (MixTranscodeParams), including video resolution, video bitrate, video frame rate, and sound quality.
Specify the position and layout of each stream in mixed-stream mode, or configure via an automatic Template.

Key nouns:.

Single stream recording: Record the audio and video of subscribed UserIds in the room separately. The recording service uploads the files to your designated cloud storage in real time.
Mixed-stream recording: Mix the audio and video of subscribed UserId in the room into a video file and upload the recorded files to your designated cloud storage. (After recording ends, go to the VOD console https://console.cloud.tencent.com/vod/media or the object storage COS console https://console.cloud.tencent.com/cos/bucket to view files).

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/647/34263).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: CreateCloudRecording. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: 2019-07-22. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/647/34263#region-list) supported by the product. This API only supports: ap-beijing, ap-guangzhou, ap-shanghai, ap-singapore. |
| SdkAppId | Yes | Integer | The [SDKAppID](https://intl.cloud.tencent.com/document/product/647/37714) of the TRTC room whose streams are recorded. |
| RoomId | Yes | String | [RoomId](https://www.tencentcloud.comom/document/product/647/46351?from_cn_redirect=1#RoomId) of TRTC, which is the RoomId corresponding to the TRTC room in the recording. |
| UserId | Yes | String | The [user ID](https://www.tencentcloud.com/document/product/647/37714#userid) of the recording robot in the TRTC room, which cannot be identical to the user IDs of anchors in the room or other recording robots. To distinguish this user ID from others, we recommend you include the room ID in the user ID. |
| UserSig | Yes | String | The signature (similar to a login password) required for the recording robot to enter the room. Each user ID corresponds to a signature. For information on how to calculate the signature, see [What is UserSig?](https://intl.cloud.tencent.com/document/product/647/38104). |
| RecordParams | Yes | [RecordParams](https://www.tencentcloud.com/document/api/647/36760#RecordParams) | The on-cloud recording parameters. |
| StorageParams | Yes | [StorageParams](https://www.tencentcloud.com/document/api/647/36760#StorageParams) | The storage information of the recording file. Currently, you can save recording files to Tencent Cloud VOD or COS. |
| RoomIdType | No | Integer | The type of the TRTC room ID, which must be the same as the ID type of the room whose streams are recorded. |
| MixTranscodeParams | No | [MixTranscodeParams](https://www.tencentcloud.com/document/api/647/36760#MixTranscodeParams) | The stream mixing parameters, which are valid if the mixed-stream recording mode is used. |
| MixLayoutParams | No | [MixLayoutParams](https://www.tencentcloud.com/document/api/647/36760#MixLayoutParams) | The layout parameters, which are valid if the mixed-stream recording mode is used. |
| ResourceExpiredHour | No | Integer | The amount of time (in hours) during which API requests can be made after recording starts. Calculation starts when a recording task is started (when the recording task ID is returned). Once the period elapses, the query, modification, and stop recording APIs can no longer be called, but the recording task will continue. The default value is `72` (three days), and the maximum and minimum values allowed are `720` (30 days) and `6` respectively. If you do not set this parameter, the query, modification, and stop recording APIs can be called within 72 hours after recording starts. |
| PrivateMapKey | No | String | The permission ticket for a TRTC room. This parameter is required if advanced permission control is enabled in the console, in which case the TRTC backend will verify users' [PrivateMapKey](https://intl.cloud.tencent.com/document/product/647/32240?from_cn_redirect=1), which include an encrypted room ID and permission bit list. A user providing only `UserSig` and not `PrivateMapKey` will be unable to enter the room. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | The task ID assigned by the recording service, which uniquely identifies a recording process and becomes invalid after a recording task ends. After a recording task starts, if you want to perform other actions on the task, you need to specify the task ID when making API requests. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Starting Cloud Recording

Start cloud recording for the specific room (room number 3560) with SdkAppId 1400188366.

This example shows you how to set the idle wait time for the room to 1 minute.
The recording mode is mixed-stream recording.
The stream type for recording is audio and video.
Subscribe all users to the default stream.
The video recording width is 360, height is 640, frame rate is 15, bitrate is 500,000bps, with default background.
The layout mode for video recording is nine-grid layout.
Store to Tencent Cloud Video on Demand (VOD)

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateCloudRecording
<Common request parameters>

{
    "StorageParams": {
        "CloudVod": {
            "TencentVod": {
                "ExpireTime": 0
            }
        }
    },
    "UserSig": "eJw1jcEKgkAURX9FZlvYc3SaC***PiwmafL9rfNX4_",
    "UserId": "10001",
    "RecordParams": {
        "MaxIdleTime": 60,
        "StreamType": 0,
        "RecordMode": 2
    },
    "RoomIdType": 1,
    "MixTranscodeParams": {
        "VideoParams": {
            "Width": 360,
            "BitRate": 500000,
            "Fps": 15,
            "Height": 640,
            "Gop": 10
        }
    },
    "MixLayoutParams": {
        "MixLayoutMode": 3
    },
    "SdkAppId": 1400188366,
    "RoomId": "3560"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskId": "-gCTFWtU7t7DUlo7A8Isw***sdOEycyX4CnzhIm4RAQ..",
        "RequestId": "71993312-6ab8-4768-9124-118e0a20c45f"
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/647/34270#common-error-codes).

| Error Code | Description |
| --- | --- |
| AuthFailure | CAM signature/authentication error. |
| AuthFailure.UnRealNameAuthenticated | Identity verification has not been completed, so this operation is not allowed. |
| AuthFailure.UnauthorizedOperation | CAM authentication failed. |
| AuthFailure.UnsupportedOperation | Unsupported operation. |
| FailedOperation | Operation failed. |
| FailedOperation.CRUnsupportMethod | Unsupported on-cloud recording method. |
| FailedOperation.RestrictedConcurrency | Maximum number of concurrent on-cloud recording tasks reached. Contact us to raise the limit. |
| InternalError.CRInternalError | On-cloud recording internal error. |
| InvalidParameter.OutOfRange | Parameter value is out of range. |
| InvalidParameter.SdkAppId | `SdkAppId` is incorrect. |
| MissingParameter.AccessKey | `AccessKey` parameter missing. |
| MissingParameter.Bucket | `Bucket` parameter missing. |
| MissingParameter.CloudStorage | `CloudStorage` parameter missing. |
| MissingParameter.RecordMode | `RecordMode` parameter missing. |
| MissingParameter.RecordParams | `RecordParams` parameter missing. |
| MissingParameter.Region | `Region` parameter missing. |
| MissingParameter.RoomId | `RoomId` is missing. |
| MissingParameter.SdkAppId | `SdkAppId` is missing. |
| MissingParameter.SecretKey | `SecretKey` parameter missing. |
| MissingParameter.StorageParams | `StorageParams` parameter missing. |
| MissingParameter.StreamType | `StreamType` parameter missing. |
| MissingParameter.TaskId | `TaskId` parameter missing. |
| MissingParameter.UserId | Missing `UserId` parameter. |
| MissingParameter.UserSig | `UserSig` parameter missing. |
| MissingParameter.Vendor | `Vendor` parameter missing. |
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://trtc.io/document/46960](https://trtc.io/document/46960)*
