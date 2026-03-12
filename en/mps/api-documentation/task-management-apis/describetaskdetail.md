# DescribeTaskDetail

## 1. API Description

Domain name for API request: mps.intl.tencentcloudapi.com.

This API is used to query the details of execution status and result of a task submitted in the last 3 days by task ID.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/1041/33628).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: DescribeTaskDetail. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: 2019-06-12. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). This parameter is not required for this API. |
| TaskId | Yes | String | Video processing task ID. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskType | String | Task type. Valid values:WorkflowTask: video workflow processing task.EditMediaTask: video editing task.LiveStreamProcessTask: live stream processing task.ScheduleTask: orchestration processing task.EvaluationTask: evaluation task. |
| Status | String | Task status. Valid values: WAITING: Waiting;PROCESSING: Processing;FINISH: Completed. |
| CreateTime | String | Creation time of a task in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| BeginProcessTime | String | Start time of task execution in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| FinishTime | String | End time of task execution in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| EditMediaTask | [EditMediaTask](https://www.tencentcloud.com/document/api/1041/33690#EditMediaTask) | Video editing task information. This field has a value only when `TaskType` is `EditMediaTask`. |
| WorkflowTask | [WorkflowTask](https://www.tencentcloud.com/document/api/1041/33690#WorkflowTask) | Information of a video processing task. This field has a value only when `TaskType` is `WorkflowTask`. Note: This field may return null, indicating that no valid values can be obtained. |
| LiveStreamProcessTask | [LiveStreamProcessTask](https://www.tencentcloud.com/document/api/1041/33690#LiveStreamProcessTask) | Information of a live stream processing task. This field has a value only when `TaskType` is `LiveStreamProcessTask`. Note: This field may return null, indicating that no valid values can be obtained. |
| ExtractBlindWatermarkTask | [ExtractBlindWatermarkTask](https://www.tencentcloud.com/document/api/1041/33690#ExtractBlindWatermarkTask) | Extracts digital watermark task information. this field has a value only when TaskType is ExtractBlindWatermark. |
| TaskNotifyConfig | [TaskNotifyConfig](https://www.tencentcloud.com/document/api/1041/33690#TaskNotifyConfig) | Event notification information of a task. Note: This field may return null, indicating that no valid values can be obtained. |
| TasksPriority | Integer | Task flow priority. Value range: [-10, 10]. |
| SessionId | String | The ID used for deduplication. If there was a request with the same ID in the last seven days, the current request will return an error. The ID can contain up to 50 characters. If this parameter is left empty or an empty string is entered, no deduplication will be performed. |
| SessionContext | String | The source context which is used to pass through the user request information. The task flow status change callback will return the value of this field. It can contain up to 1,000 characters. |
| ExtInfo | String | Extended information field, used in specific scenarios. |
| ScheduleTask | [ScheduleTask](https://www.tencentcloud.com/document/api/1041/33690#ScheduleTask) | The information of a scheme. This parameter is valid only if `TaskType` is `ScheduleTask`. Note: This field may return null, indicating that no valid values can be obtained. |
| LiveScheduleTask | [LiveScheduleTask](https://www.tencentcloud.com/document/api/1041/33690#LiveScheduleTask) | The information of a live scheme. This parameter is valid only if `TaskType` is `LiveScheduleTask`. Note: This field may return null, indicating that no valid values can be obtained. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Obtaining Task Details

This example shows you how to querying task results.

#### Input Example

```
https://mps.intl.tencentcloudapi.com/?Action=DescribeTaskDetail
&TaskId=235303****-WorkflowTask-80108cc3380155d98b2e3573a48a******
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "TaskType": "WorkflowTask",
        "Status": "FINISH",
        "CreateTime": "2019-07-16T06:21:27Z",
        "BeginProcessTime": "2019-07-16T06:21:28Z",
        "FinishTime": "2019-07-16T06:21:46Z",
        "WorkflowTask": {
            "TaskId": "235303****-WorkflowTask-80108cc3380155d98b2e3573a48a******",
            "Status": "FINISH",
            "ErrCode": 0,
            "Message": "",
            "InputInfo": {
                "Type": "COS",
                "CosInputInfo": {
                    "Bucket": "vodtestbj-235303****",
                    "Region": "ap-beijing",
                    "Object": "/input/videoplayback.mp4"
                },
                "S3InputInfo": null,
                "UrlInputInfo": null
            },
            "MetaData": {
                "AudioDuration": 380.9465637207031,
                "AudioStreamSet": [
                    {
                        "Channel": 0,
                        "Bitrate": 95999,
                        "Codec": "aac",
                        "SamplingRate": 44100
                    }
                ],
                "Bitrate": 409657,
                "Container": "mov,mp4,m4a,3gp,3g2,mj2",
                "Duration": 380.9465637207031,
                "Height": 360,
                "Rotate": 0,
                "Size": 19626862,
                "VideoDuration": 380.8804931640625,
                "VideoStreamSet": [
                    {
                        "Bitrate": 313658,
                        "Codec": "h264",
                        "Codecs": "avc1.ffe100",
                        "Fps": 29,
                        "Height": 360,
                        "HdrType": "",
                        "ColorPrimaries": "",
                        "ColorSpace": "",
                        "ColorTransfer": "",
                        "Width": 480
                    }
                ],
                "Width": 480
            },
            "MediaProcessResultSet": [
                {
                    "Type": "Transcode",
                    "TranscodeTask": {
                        "Status": "SUCCESS",
                        "ErrCode": 0,
                        "Message": "SUCCESS",
                        "ErrCodeExt": "SUCCESS",
                        "Progress": 100,
                        "Input": {
                            "Definition": 210,
                            "WatermarkSet": [],
                            "MosaicSet": [],
                            "RawParameter": null,
                            "EndTimeOffset": 0,
                            "OverrideParameter": null,
                            "HeadTailParameter": null,
                            "StartTimeOffset": 0,
                            "OutputStorage": {
                                "Type": "COS",
                                "CosOutputStorage": {
                                    "Bucket": "vodtestgz-235303****",
                                    "Region": "ap-guangzhou"
                                },
                                "S3OutputStorage": null
                            },
                            "OutputObjectPath": "/hello/world/what/ever/videoplayback_transcode111_210",
                            "SegmentObjectName": "/hello/world/what/ever/no/problem/videoplayback_transcode11_210_{number}",
                            "ObjectNumberFormat": {
                                "InitialValue": 2,
                                "Increment": 3,
                                "MinLength": 1,
                                "PlaceHolder": "0"
                            }
                        },
                        "Output": {
                            "OutputStorage": {
                                "Type": "COS",
                                "CosOutputStorage": {
                                    "Bucket": "vodtestgz-235303****",
                                    "Region": "ap-guangzhou"
                                },
                                "S3OutputStorage": null
                            },
                            "Path": "/hello/world/what/ever/videoplayback_transcode111_210.m3u8",
                            "Definition": 210,
                            "Bitrate": 353297,
                            "Height": 240,
                            "Width": 320,
                            "Size": 5692,
                            "Duration": 380.9580078125,
                            "Container": "hls,applehttp",
                            "Md5": "ae0dfe7c7336291d6243463b7bb14fea",
                            "VideoStreamSet": [
                                {
                                    "Bitrate": 302307,
                                    "Codec": "h264",
                                    "Codecs": "avc1.ffe100",
                                    "Fps": 24,
                                    "Height": 240,
                                    "HdrType": "",
                                    "ColorPrimaries": "",
                                    "ColorSpace": "",
                                    "ColorTransfer": "",
                                    "Width": 320
                                }
                            ],
                            "AudioStreamSet": [
                                {
                                    "Channel": 0,
                                    "Bitrate": 50990,
                                    "Codec": "aac",
                                    "SamplingRate": 44100
                                }
                            ]
                        }
                    },
                    "AnimatedGraphicTask": null,
                    "SnapshotByTimeOffsetTask": null,
                    "SampleSnapshotTask": null,
                    "ImageSpriteTask": null,
                    "AdaptiveDynamicStreamingTask": null
                }
            ],
            "AiAnalysisResultSet": [],
            "AiRecognitionResultSet": [],
            "AiContentReviewResultSet": [],
            "AiQualityControlTaskResult": null
        },
        "TaskNotifyConfig": null,
        "EditMediaTask": null,
        "LiveStreamProcessTask": null,
        "ScheduleTask": null,
        "LiveScheduleTask": null,
        "TasksPriority": 0,
        "SessionId": "",
        "SessionContext": "",
        "ExtInfo": "",
        "RequestId": "04db7d25-f590-414a-a341-8f1584f15f84"
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
| InternalError | Internal error. |
| InvalidParameterValue | Incorrect parameter value. |
| ResourceNotFound | The resource does not exist. |
| UnauthorizedOperation | Unauthorized operation. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33644](https://www.tencentcloud.com/document/product/1041/33644)*
