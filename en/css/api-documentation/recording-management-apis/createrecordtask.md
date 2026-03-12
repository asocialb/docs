# CreateRecordTask

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to create a recording task that starts and ends at specific times and records videos according to a specific recording template.

Prerequisites
Because recording files are saved in VOD, you must first activate VOD.
Storage and playback traffic fees are charged for storing and playing the videos recorded. For details, see
Purchase Guide
.
Notes
If streaming is interrupted, the current recording will stop and a recording file will be generated. When streaming resumes, as long as it’s before the end time of the task, recording will start again.
Avoid creating recording tasks with overlapping time periods. If there are multiple tasks with overlapping time periods for the same stream, the system will start three recording tasks at most to avoid repeated recording.
Task records are kept for three months by the platform.
Do not use the new
CreateRecordTask
,
StopRecordTask
, and [DeleteRecordTask] APIs together with the old
CreateLiveRecord
,
StopLiveRecord
, and
DeleteLiveRecord
APIs.
Do not create recording tasks and push streams at the same time. After creating a recording task, we recommend you wait at least three seconds before pushing streams.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: CreateRecordTask. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/267/30763#region-list) supported by the product. This API only supports: ap-bangkok, ap-guangzhou, ap-hongkong, ap-jakarta, ap-mumbai, ap-seoul, ap-singapore, ap-tokyo, eu-frankfurt, na-ashburn, na-siliconvalley, na-toronto, sa-saopaulo. |
| StreamName | Yes | String | Stream name. |
| DomainName | Yes | String | Push domain name. |
| AppName | Yes | String | Push path. |
| EndTime | Yes | Integer | Recording end time in UNIX timestamp format. `EndTime` should be later than `StartTime` and the current time, and the duration between `EndTime` and `StartTime` is up to 24 hours. |
| StartTime | No | Integer | Recording start time in UNIX timestamp format. Leaving this parameter empty means starting recording now. `StartTime` cannot be later than the current time plus 6 days. |
| StreamType | No | Integer | Push type. Default value: 0. Valid values: 0: LVB push. 1: mixed stream, i.e., A + B = C mixed stream. |
| TemplateId | No | Integer | Recording template ID, which is the returned value of `CreateLiveRecordTemplate`. If this parameter is left empty or incorrect, the stream will be recorded in HLS format and retained permanently by default. |
| Extension | No | String | Extension field which is not defined now. It is empty by default. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | A globally unique task ID. If `TaskId` is returned, the recording task has been successfully created. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=CreateRecordTask
&AppName=live
&DomainName=5000.live.push.com
&StreamName=livetest
&StartTime=1589889600
&EndTime=1589904000
&TemplateId=0
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "eac6b301-a322-493a-8e36-83b295459397",
        "TaskId": "UpTbk5RSVhRQFkAAfHwQCCjcRD0lRFcZ0xTSlNTQltlRVRLU1JAWW9EUb"
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
| InternalError.GetConfigError | Error getting the configuration. |
| InternalError.NetworkError | Internal network error. |
| InvalidParameter | Invalid parameter. |
| LimitExceeded.MaximumRunningTask | The current number of concurrent tasks exceeds the limit. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceUnavailable.InvalidVodStatus | The VOD service has not been activated. |
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37309](https://www.tencentcloud.com/document/product/267/37309)*
