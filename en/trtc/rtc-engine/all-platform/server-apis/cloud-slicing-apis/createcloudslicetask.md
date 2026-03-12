# CreateCloudSliceTask

## 1. API Description

Domain name for API request: trtc.intl.tencentcloudapi.com.

API description:
This API is used to enable the cloud slicing feature, completing audio and video slicing tasks in the room, and uploading them to the specified cloud storage.
This API is used to achieve the following goals:

This API is used to specify the slicing parameter (SliceParams) to define the blocklist or allowlist of the anchors that require slicing.
This API is used to specify the storage parameter (SliceStorageParams) to specify the cloud storage you want to upload to. Currently, Tencent Cloud Object Storage (COS) and third-party AWS are supported.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/647/34263).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: CreateCloudSliceTask. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: 2019-07-22. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/647/34263#region-list) supported by the product. This API only supports: ap-singapore, eu-frankfurt. |
| SdkAppId | Yes | Integer | [SdkAppId](https://www.tencentcloud.com/document/product/647/46351?from_cn_redirect=1#sdkappid) of TRTC, which is the same as the SdkAppId corresponding to the TRTC room. |
| RoomId | Yes | String | [RoomId](https://www.tencentcloud.com/document/product/647/46351?from_cn_redirect=1#roomid) of TRTC, which is the RoomId corresponding to the TRTC room. |
| UserId | Yes | String | Chatbot's UserId, which is used to enter the room and initiate a slicing task. [*note] This UserId should not be duplicated with the UserIds of the current anchors or audience members in the room. If multiple slicing tasks are initiated in one room, the chatbot's UserId should also be unique; otherwise, the previous slicing task is interrupted. It is recommended to include the room ID as part of the UserId, ensuring that the chatbot's UserId is unique in the room. |
| UserSig | Yes | String | Signature verification corresponding to the chatbot's UserId, namely, the UserId and UserSig serve as the login password for the chatbot to enter the room. For specific calculation methods, see TRTC solution for calculating UserSig. |
| SliceParams | Yes | [SliceParams](https://www.tencentcloud.com/document/api/647/36760#SliceParams) | Control parameters for cloud slicing. |
| SliceStorageParams | Yes | [SliceStorageParams](https://www.tencentcloud.com/document/api/647/36760#SliceStorageParams) | Parameters for uploading cloud slicing files to the cloud storage. |
| RoomIdType | No | Integer | Type of the TRTC room number. [*Note] It should be the same as the type of the RoomId corresponding to the recording room. 0: string type; 1: 32-bit integer type (default value). Example value: 1. |
| ResourceExpiredHour | No | Integer | Validity period for calling the API, which starts upon successful initiation of recording and obtaining the task ID. After the timeout, APIs such as querying, updating, or stopping cannot be called, but the recording task is not stopped. The unit of the parameter is hours, with a default value of 72 hours (3 days). The maximum value is 720 hours (30 days), while the minimum value is 6 hours. For example, if this parameter is not specified, the validity period for calling the querying, updating, and stopping recording APIs is 72 hours upon the successful start of recording. Example value: 24. |
| PrivateMapKey | No | String | TRTC room permission encryption string, which is required only when advanced permission control is enabled in the TRTC console. After enabling, the TRTC backend service system verifies a "permission ticket" called [PrivateMapKey], which contains an encrypted RoomId and an encrypted "permission bit list". Since the PrivateMapKey includes the RoomId, the specified room cannot be entered if only UserSig is provided and PrivateMapKey is not provided. Example value: eJw1jcEKgkAURX9FZlvY****fL9rfNX4_. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Task ID assigned by the cloud slicing service. It is a unique identifier for the lifecycle of a slicing task, which loses its significance after the task is completed. The task ID needs to be retained by the business system as a parameter for future operations related to this task. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Creating a Slicing Task

This example shows you how to start a cloud slicing task for the specified room (room number: 150) with SdkAppId 200806.
This example shows you how to set the idle time for the room to 30 seconds.
This example shows you how to set the slicing mode to audio slicing + video frame extraction.
This example shows you how to slice the audio every 15 seconds.
This example shows you how to extract a video frame every 5 seconds.

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateCloudSliceTask
<Common request parameters>

{
    "SdkAppId": 200806,
    "RoomId": "150",
    "UserId": "inspect",
    "UserSig": "eJxxxv3xY6jx2KgRU1NPHMy3CnQIZEJBDxf1SulLZcs*pAAuveqIuFaeqrW2kMVyAFYogrTGbnBiScDmm2zf0*HdqoLAhxQ85dn4vMn4*N8zFT7f-aXIf3Zj0fWn78*ktBUUyJoEmHMS0ChM83AAD---1NMfA_",
    "SliceParams": {
        "SliceType": 3,
        "MaxIdleTime": 30,
        "SliceAudio": 15,
        "SliceVideo": 5
    },
    "SliceStorageParams": {
        "CloudSliceStorage": {
            "Vendor": 0,
            "Region": "ap-guangzhou",
            "Bucket": "av-recover-prod-1258344699",
            "AccessKey": "AKIDiGYZYrugBPM3TbS2MO9dqxxx",
            "SecretKey": "91w4wXswiDSQ7XfX8So31xxx",
            "FileNamePrefix": [
                "prefix1"
            ]
        }
    },
    "RoomIdType": 1,
    "ResourceExpiredHour": 72
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "6c8eac0c-a46e-4002-893a-935160b43b34",
        "TaskId": "-npVqpdU7qidKD61us+k9KlbamMCLrDbczWnLoK-2OqyoZWQndib8Ma8fbGq2JxnW26LgE."
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
| FailedOperation.CSUnsupportMethod | The cloud slicing method is not supported. |
| FailedOperation.RestrictedConcurrency | Maximum number of concurrent on-cloud recording tasks reached. Contact us to raise the limit. |
| InternalError.CSInternalError | Internal service error of cloud slicing occurs. |
| InvalidParameter.OutOfRange | Parameter value is out of range. |
| InvalidParameter.SdkAppId | `SdkAppId` is incorrect. |
| MissingParameter.AccessKey | `AccessKey` parameter missing. |
| MissingParameter.Bucket | `Bucket` parameter missing. |
| MissingParameter.Region | `Region` parameter missing. |
| MissingParameter.RoomId | `RoomId` is missing. |
| MissingParameter.SdkAppId | `SdkAppId` is missing. |
| MissingParameter.SecretKey | `SecretKey` parameter missing. |
| MissingParameter.SliceParams | The SliceParams parameter is required. |
| MissingParameter.SliceStorageParams | The SliceStorageParams parameter is required. |
| MissingParameter.SliceType | The SliceType parameter is required. |
| MissingParameter.TaskId | `TaskId` parameter missing. |
| MissingParameter.UserId | Missing `UserId` parameter. |
| MissingParameter.UserSig | `UserSig` parameter missing. |
| MissingParameter.Vendor | `Vendor` parameter missing. |
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://trtc.io/document/72331](https://trtc.io/document/72331)*
