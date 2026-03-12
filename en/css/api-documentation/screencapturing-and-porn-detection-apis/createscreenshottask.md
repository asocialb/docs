# CreateScreenshotTask

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to create a screencapturing task that has a specific start and end time and takes screenshots according to the template configured.

Note
If the stream is interrupted, screencapturing will stop. However, the task will still be valid before the specified end time, and screencapturing will be performed as required after the stream is resumed.
Avoid creating screencapturing tasks with overlapping time periods. The system will execute at most three screencapturing tasks on the same stream at a time.
Task records are only kept for three months.
The new screencapturing APIs (CreateScreenshotTask/StopScreenshotTask/DeleteScreenshotTask) are not compatible with the legacy ones (CreateLiveInstantSnapshot/StopLiveInstantSnapshot). Do not mix them when you call APIs to manage screencapturing tasks.
If you create a screencapturing task and publish the stream at the same time, the task may fail to be executed at the specified time. After creating a screencapturing task, we recommend you wait at least three seconds before publishing the stream.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: CreateScreenshotTask. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| StreamName | Yes | String | The stream name. |
| DomainName | Yes | String | The push domain. |
| AppName | Yes | String | The push path. |
| EndTime | Yes | Integer | The task end time, which must be a Unix timestamp and later than `StartTime` and the current time. The end time and start time cannot be more than 24 hours apart. |
| TemplateId | Yes | Integer | The ID of the screencapturing template, which is returned by `CreateLiveSnapshotTemplate`. If an incorrect template ID is passed in, the screencapturing task will fail. |
| StartTime | No | Integer | The task start time, which must be a Unix timestamp and cannot be later than six days from the current time. If you do not specify this parameter, the task will start immediately. |
| StreamType | No | Integer | The publishing type. Valid values: `0` (default): Live stream `1`: Mixed stream |
| Extension | No | String | An extension field, which is not defined currently and is empty by default. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | A unique task ID. If this parameter is returned, the screencapturing task is created successfully. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Creating a screencapturing task

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=CreateScreenshotTask
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
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://www.tencentcloud.com/document/product/267/54799](https://www.tencentcloud.com/document/product/267/54799)*
