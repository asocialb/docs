# ModifyLivePullStreamTask

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to modify a stream pulling task.

You cannot modify the destination URL. To publish to a new destination, please create a new task.
You cannot modify the source type. To use a different source type, please create a new task.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: ModifyLivePullStreamTask. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/267/30763#region-list) supported by the product. This API only supports: ap-bangkok, ap-beijing, ap-guangzhou, ap-hongkong, ap-mumbai, ap-seoul, ap-shanghai, ap-singapore, ap-tokyo, eu-frankfurt, na-ashburn, na-siliconvalley. |
| TaskId | Yes | String | The task ID. |
| Operator | Yes | String | The operator. |
| SourceUrls.N | No | Array of String | The source URL(s). If `SourceType` is `PullLivePushLive`, you can specify only one source URL. If `SourceType` is `PullVodPushLive`, you can specify at most 30 source URLs. |
| StartTime | No | String | The start time. It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| EndTime | No | String | The end time. Notes: 1. The end time must be later than the start time. 2. The end time and start time must be later than the current time. 3. The end time and start time must be less than seven days apart. It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| VodLoopTimes | No | Integer | The number of times to loop video files. -1: Loop indefinitely 0: Do not loop > 0: The number of loop times. A task will end either when the videos are looped for the specified number of times or at the specified task end time, whichever is earlier. This parameter is valid only if the source is video files. |
| VodRefreshType | No | String | The behavior after the source video files (`SourceUrls`) are changed. ImmediateNewSource: Play the new videos immediately ContinueBreakPoint: Finish the current video first and then pull from the new source. This parameter is valid only if the source is video files. |
| Status | No | String | Whether to enable or pause the task. Valid values: enable pause |
| CallbackEvents.N | No | Array of String | The events to listen for. If you do not pass this parameter, all events will be listened for. TaskStart: Callback for starting a task TaskExit: Callback for ending a task VodSourceFileStart: Callback for starting to pull from video files VodSourceFileFinish: Callback for stopping pulling from video files ResetTaskConfig: Callback for modifying a task |
| CallbackUrl | No | String | A custom callback URL. Callbacks will be sent to this URL. |
| FileIndex | No | Integer | The index of the video to start from. The value of this parameter cannot be smaller than 1 or larger than the number of elements in `SourceUrls`. |
| OffsetTime | No | Integer | The playback offset (seconds). Notes: 1. This parameter should be used together with `FileIndex`. |
| Comment | No | String | The remarks for the task. |
| BackupSourceType | No | String | The backup source type. PullLivePushLive: Live streaming PullVodPushLive: Video files Notes: 1. Backup sources are supported only if the primary source type is live streaming. 2. Leaving this parameter empty will reset the backup source. 3. When pull from the primary source is interrupted, the system will pull from the backup source. 4. If the backup source is a video file, each time the video is finished, the system will check if the primary source is recovered and will switch back if it is. |
| BackupSourceUrl | No | String | The URL of the backup source. You can specify only one backup source URL. |
| WatermarkList.N | No | Array of [PullPushWatermarkInfo](https://www.tencentcloud.com/document/api/267/30767#PullPushWatermarkInfo) | The information of watermarks to add. Notes: 1. You can add up to four watermarks to different locations of the video. 2. Make sure you use publicly accessible URLs for the watermark images. 3. Supported image formats include PNG and JPG. 4. If you change the watermark configuration of a task whose source is a list of video files, the new configuration will take effect for the next file in the list. 5. If you change the watermark configuration of a task whose source is a live stream, the new configuration will take effect immediately. 6. If you want to stop using watermarks, pass in an empty array. 7. Currently, animated watermarks are not supported. |
| VodLocalMode | No | Integer | Whether to use local mode when the source type is video files. The default is `0`. 0: Do not use local mode 1: Use local mode Note: If you enable local mode, MP4 files will be downloaded to local storage, and the local files will be used for push. This ensures more reliable push. Pushing a local file will incur additional fees. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ModifyLivePullStreamTask
<Common request parameters>

{
    "Operator": "yourname",
    "EndTime": "2020-04-17T12:02:00Z",
    "StartTime": "2020-04-16T11:02:00Z",
    "TaskId": "123",
    "SourceUrls": [
        "rtmp://your.domainname.com/live/stream1"
    ]
}
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
| FailedOperation | Operation failed. |
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| InvalidParameter | Invalid parameter. |
| InvalidParameter.InvalidBackupToUrl | invalid BackupToUrl. |
| InvalidParameter.InvalidCallbackUrl | Invalid callback URL. |
| InvalidParameter.InvalidSourceUrl | Invalid source URL. |
| InvalidParameter.InvalidTaskTime | The time period of the task exceeded the limit. |
| InvalidParameter.InvalidToUrl | Invalid destination URL. |
| InvalidParameter.InvalidWatermark | Invalid watermark parameter. |
| InvalidParameter.TaskNotExist | The task does not exist. |
| InvalidParameter.ToUrlNoPermission | No permission to access the external URL. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.UserNotExist | The CSS service has not been activated. |


---
*Source: [https://www.tencentcloud.com/document/product/267/48354](https://www.tencentcloud.com/document/product/267/48354)*
