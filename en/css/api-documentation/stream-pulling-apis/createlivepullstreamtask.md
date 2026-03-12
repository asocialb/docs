# CreateLivePullStreamTask

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to create a task to pull streams from video files or an external live streaming source and publish them to a specified destination URL.
Notes:

By default, you can have at most 20 stream pulling tasks at a time. You can submit a ticket to raise the limit.
Only H.264 and H.265 are supported for video. If the source video is in a different format, please transcode it first.
Only AAC is supported for audio. If the source audio is in a different format, please transcode it first.
You can enable auto deletion in the console to delete expired tasks automatically.
The pull and relay feature is a paid feature. For its billing details, see
Relay
.
CSS is only responsible for pulling and relaying content. Please make sure that your content is authorized and complies with relevant laws and regulations. In case of copyright infringement or violation of laws or regulations, CSS will suspend its service for you and reserves the right to seek legal remedies.

A maximum of 50 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: CreateLivePullStreamTask. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/267/30763#region-list) supported by the product. This API only supports: ap-bangkok, ap-beijing, ap-guangzhou, ap-hongkong, ap-mumbai, ap-seoul, ap-shanghai, ap-singapore, ap-tokyo, eu-frankfurt, na-ashburn, na-siliconvalley. |
| SourceType | Yes | String | The source type. Valid values: |
| SourceUrls.N | Yes | Array of String | The source URL(s). If `SourceType` is `PullLivePushLive`, you can specify only one source URL. If `SourceType` is `PullVodPushLive`, you can specify at most 30 source URLs. Supported file formats: FLV, MP4, HLS. Supported protocols: HTTP, HTTPS, RTMP, RTMPS, RTSP, SRT. Notes: 1. We recommend you use FLV files as the source. Poorly interleaved MP4 files may result in playback stuttering. You can also re-interleave your MP4 files before adding them as the source. 2. Do not use private network domains or malicious URLs. CSS will block accounts that do. 3. To avoid push and playback issues, make sure the source files are properly interleaved. 4. Supported video coding formats: H.264, H.265. 5. Supported audio coding format: AAC. 6. Use small video files, preferably not longer than one hour. Large files may take a long time to load or resume after pause. Relay may fail if the time consumed exceeds 15 seconds. |
| DomainName | Yes | String | The push domain name. The pulled stream is pushed to this domain. Note: If the destination is not a CSS address and its format is different from that of CSS addresses, pass the full address to `ToUrl`. For details, see the description of the `ToUrl` parameter. |
| AppName | Yes | String | The application to push to. The pulled stream is pushed to this application. |
| StreamName | Yes | String | The stream name. The pulled stream is pushed under this name. |
| StartTime | Yes | String | The start time. It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| EndTime | Yes | String | The end time. Notes: 1. The end time must be later than the start time. 2. The end time and start time must be later than the current time. 3. The end time and start time must be less than seven days apart. It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| Operator | Yes | String | The operator. |
| PushArgs | No | String | The push parameter. This is a custom parameter carried during push. Example: bak=1&test=2 |
| CallbackEvents.N | No | Array of String | The events to listen for. If you do not pass this parameter, all events will be listened for. TaskStart: Callback for starting a task TaskExit: Callback for ending a task VodSourceFileStart: Callback for starting to pull from video files VodSourceFileFinish: Callback for stopping pulling from video files ResetTaskConfig: Callback for modifying a task  `TaskAlarm` indicates a warning event. `AlarmType` examples: PullFileUnstable: Pull from video files is unstable. PushStreamUnstable: Push is unstable. PullFileFailed: Error pulling from video files. PushStreamFailed: Push error. FileEndEarly: The video file ended prematurely. |
| VodLoopTimes | No | String | The number of times to loop video files. Default value: -1. -1: Loop indefinitely 0: Do not loop > 0: The number of loop times. A task will end either when the videos are looped for the specified number of times or at the specified task end time, whichever is earlier. This parameter is valid only when the source is video files. |
| VodRefreshType | No | String | The behavior after the source video files (`SourceUrls`) are changed. ImmediateNewSource: Play the new videos immediately ContinueBreakPoint: Play the new videos after the current video is finished playing (the remaining videos in the old playlist will not be played).  This parameter is valid only if the source before the change is video files. |
| CallbackUrl | No | String | A custom callback URL. Callbacks about pull and relay events will be sent to this URL. |
| ExtraCmd | No | String | Other parameters. For example, you can use `ignore_region` to ignore the region passed in and assign a region based on load distribution. |
| Comment | No | String | The remarks for a task, not longer than 512 bytes. |
| ToUrl | No | String | The complete destination URL. If you specify this parameter, make sure you pass in an empty string for `DomainName`, `AppName`, and `StreamName`.  Note: Make sure that the expiration time of the signature is later than the task end time. |
| BackupSourceType | No | String | The backup source type. PullLivePushLive: Live streaming PullVodPushLive: Video files Notes: 1. Backup sources are supported only if the primary source type is live streaming. 2. When pull from the primary source is interrupted, the system will pull from the backup source. 3. If the backup source is a video file, each time the video is finished, the system will check if the primary source is recovered and will switch back if it is. |
| BackupSourceUrl | No | String | The URL of the backup source. You can specify only one backup source URL. |
| WatermarkList.N | No | Array of [PullPushWatermarkInfo](https://www.tencentcloud.com/document/api/267/30767#PullPushWatermarkInfo) | The information of watermarks to add. Notes: 1. You can add up to four watermarks to different locations of the video. 2. Make sure you use publicly accessible URLs for the watermark images. 3. Supported image formats include PNG, JPG, and GIF. |
| VodLocalMode | No | Integer | Whether to use local mode when the source type is video files. The default is `0`. 0: Do not use local mode 1: Use local mode Note: If you enable local mode, MP4 files will be downloaded to local storage, and the local files will be used for push. This ensures more reliable push. Pushing a local file will incur additional fees. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | The task ID. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateLivePullStreamTask
<Common request parameters>

{
    "SourceType": "PullLivePushLive",
    "DomainName": "5000.livepush.myqcloud.com",
    "SourceUrls": [
        "rtmp://5000.liveplay.myqcloud.com/live/stream1"
    ],
    "StreamName": "test",
    "AppName": "live",
    "StartTime": "2019-12-16T11:02:00Z",
    "Operator": "vinson",
    "EndTime": "2019-12-17T12:02:00Z"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskId": "10000",
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
| InvalidParameter.InvalidMixInputParam | Invalid input parameters for stream mixing. |
| InvalidParameter.InvalidOutputParam | Invalid output stream parameters. |
| InvalidParameter.InvalidSourceUrl | Invalid source URL. |
| InvalidParameter.InvalidTaskTime | The time period of the task exceeded the limit. |
| InvalidParameter.InvalidToUrl | Invalid destination URL. |
| InvalidParameter.InvalidWatermark | Invalid watermark parameter. |
| InvalidParameter.TaskNotExist | The task does not exist. |
| InvalidParameter.TaskNumMoreThanLimit | The number of tasks reached the limit. |
| InvalidParameter.ToUrlNoPermission | No permission to access the external URL. |
| InvalidParameterValue | Invalid parameter value. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.UserNotExist | The CSS service has not been activated. |


---
*Source: [https://www.tencentcloud.com/document/product/267/48357](https://www.tencentcloud.com/document/product/267/48357)*
