# ProcessMedia

## 1. API Description

Domain name for API request: mps.intl.tencentcloudapi.com.

This API is used to initiate a processing task for video URLs or media files in Cloud Object Storage (COS). Features include:

Audio/Video transcoding (such as standard transcoding, top speed codec (TSC) transcoding, audio/video enhancement, visible watermark addition, and digital watermark addition).
Adaptive bitrate streaming conversion for audios/videos.
Video-to-GIF conversion.
Time point screenshot of videos.
Sampled screenshot of videos.
Image sprite of video screenshots.
Media quality inspection (such as media format diagnosis, audio/video content detection, and scoring without reference, where audio/video content detection mainly covers jitter, blur, low light, overexposure, screen glitches, noise, mosaic, QR code, and other issues).
Smart subtitle (such as subtitle generation and translation).
Smart erasing (such as watermark removal, subtitle removal, and privacy protection).
Smart content moderation (such as pornography detection and sensitive information detection).
Smart content analysis (such as tags, classifications, covers, frame tags, video splitting, highlights, opening and ending clips, and marking points for games).
Smart content recognition (such as human faces, full texts, text keywords, full speech, speech keywords, speech translation, and object recognition).

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/1041/33628).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: ProcessMedia. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: 2019-06-12. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). This parameter is not required for this API. |
| InputInfo | Yes | [MediaInputInfo](https://www.tencentcloud.com/document/api/1041/33690#MediaInputInfo) | The information of the file to process. |
| OutputStorage | No | [TaskOutputStorage](https://www.tencentcloud.com/document/api/1041/33690#TaskOutputStorage) | Target storage for Media Processing Service output files. If left blank, it inherits the storage location in InputInfo.  Note: When InputInfo.Type is URL, this parameter is required. |
| OutputDir | No | String | The directory to save the media processing output file, which must start and end with `/`, such as `/movie/201907/`. If you do not specify this parameter, the file will be saved to the directory specified in `InputInfo`. |
| ScheduleId | No | Integer | Orchestration ID. Note 1: For parameters OutputStorage and OutputDir: When a sub-task node in service orchestration has OutputStorage and OutputDir configured, the output configured in this sub-task node is used as the output of the sub-task.When a sub-task node in service orchestration does not have OutputStorage and OutputDir configured, if the task creation API (ProcessMedia) has specified an output, it will override the default output of the original orchestration.The priority of output settings is: Orchestration sub-task node > Output specified by the task API > Corresponding configuration within an orchestration. Note 2: For the TaskNotifyConfig parameter, if the task creation API (ProcessMedia) has set this parameter, it will override the default callback of the original orchestration.  Note 3: The trigger configured for an orchestration is for automatically starting the orchestration. It stops working when you manually call this API to start an orchestration. |
| MediaProcessTask | No | [MediaProcessTaskInput](https://www.tencentcloud.com/document/api/1041/33690#MediaProcessTaskInput) | The media processing parameters to use. |
| AiContentReviewTask | No | [AiContentReviewTaskInput](https://www.tencentcloud.com/document/api/1041/33690#AiContentReviewTaskInput) | Type parameter of a video content audit task. |
| AiAnalysisTask | No | [AiAnalysisTaskInput](https://www.tencentcloud.com/document/api/1041/33690#AiAnalysisTaskInput) | Video content analysis task parameter. |
| AiRecognitionTask | No | [AiRecognitionTaskInput](https://www.tencentcloud.com/document/api/1041/33690#AiRecognitionTaskInput) | Type parameter of a video content recognition task. |
| AiQualityControlTask | No | [AiQualityControlTaskInput](https://www.tencentcloud.com/document/api/1041/33690#AiQualityControlTaskInput) | Media quality inspection type task parameters. |
| SmartSubtitlesTask | No | [SmartSubtitlesTaskInput](https://www.tencentcloud.com/document/api/1041/33690#SmartSubtitlesTaskInput) | Smart subtitle task. |
| SmartEraseTask | No | [SmartEraseTaskInput](https://www.tencentcloud.com/document/api/1041/33690#SmartEraseTaskInput) | Smart erase task parameter. |
| TaskNotifyConfig | No | [TaskNotifyConfig](https://www.tencentcloud.com/document/api/1041/33690#TaskNotifyConfig) | Event notification information of a task. If this parameter is left empty, no event notifications will be obtained. |
| TasksPriority | No | Integer | Task flow priority. The higher the value, the higher the priority. Value range: [-10, 10]. If this parameter is left empty, 0 will be used. |
| SessionId | No | String | Identification code for deduplication, up to 50 characters. If a request with the same identification code was made within the past 3 days, an error will be returned for the current request. If this parameter is not provided or is an empty string, deduplication will not be performed for this request. |
| SessionContext | No | String | The source context which is used to pass through the user request information. The task flow status change callback will return the value of this field. It can contain up to 1,000 characters. |
| TaskType | No | String | The task type.  `Online` (default): A task that is executed immediately. `Offline`: A task that is executed when the system is idle (within three days by default). |
| ResourceId | No | String | Resource ID. Ensure that the corresponding resource is enabled. The default value is the primary resource ID of the account. |
| SkipMateData | No | Integer | Whether to skip metadata acquisition. Valid values: 0: do not skip 1: skip Default value: 0 |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Task ID. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Initiating a Media Quality Inspection Task

#### Input Example

```
POST / HTTP/1.1
Host: mps.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ProcessMedia
<Common request parameters>

{
    "InputInfo": {
        "Type": "COS",
        "CosInputInfo": {
            "Bucket": "TopRankVideo-125xxx88",
            "Region": "ap-shanghai",
            "Object": "/image/lenna.jpeg"
        }
    },
    "OutputStorage": {
        "Type": "COS",
        "CosOutputStorage": {
            "Bucket": "TopRankVideo-125xxx88",
            "Region": "ap-shanghai"
        }
    },
    "OutputDir": "/data/share/",
    "AiQualityControlTask": {
        "Definition": 30
    }
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "4a72e698-ec27-4fc1-8e17-c1cbfce1a4a9",
        "TaskId": "2600007696-WorkflowTask-67771a50b24d08baaf6165da23461e36tt7"
    }
}
```

### Example2 Initiating an Adaptive Bitrate Streaming Task

This example shows you how to initiate a transcoding task for a COS endpoint to transcode videos according to the transcoding templates 20, 30, and 40.

#### Input Example

```
POST / HTTP/1.1
Host: mps.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ProcessMedia
<Common request parameters>

{
    "InputInfo": {
        "Type": "COS",
        "CosInputInfo": {
            "Bucket": "TopRankVideo-125xxx88",
            "Region": "ap-shanghai",
            "Object": "/video/lego-city-vehicles.mp4"
        }
    },
    "OutputDir": "/share/output/",
    "MediaProcessTask": {
        "AdaptiveDynamicStreamingTaskSet": [
            {
                "Definition": 10,
                "OutputObjectPath": "{inputName}_adaptiveDynamicStreaming.{format}",
                "SubStreamObjectName": "{inputName}_adaptiveDynamicStreaming_{definition}_{subStreamNumber}.{format}",
                "SegmentObjectName": "{inputName}_adaptiveDynamicStreaming_{definition}_{subStreamNumber}_{segmentNumber}.{format}"
            }
        ]
    }
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "be6954ba-1e0e-4b36-9da1-d79aaaaccb0d",
        "TaskId": "2600007696-WorkflowTask-7bc4b70f5bda4b4fef4ad29d2d168bdftt7"
    }
}
```

### Example3 Initiating a Transcoding Task

This example shows you how to initiate a transcoding task for a video at a specified COS address and transfer it into three formats: 20, 30, and 40.

#### Input Example

```
POST / HTTP/1.1
Host: mps.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ProcessMedia
<Common request parameters>

{
    "MediaProcessTask": {
        "TranscodeTaskSet": [
            {
                "Definition": "30"
            },
            {
                "Definition": "20"
            },
            {
                "Definition": "40"
            }
        ]
    },
    "InputInfo": {
        "Type": "COS",
        "CosInputInfo": {
            "Region": "ap-chongqing",
            "Object": "/movie/201907/WildAnimal.mov",
            "Bucket": "TopRankVideo-125xxx88"
        }
    }
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "6ca31e3a-6b8e-4b4e-9256-fdc700064ef3",
        "TaskId": "125xxx65-procedurev2-bffb15f07530b57bc1aabb01fac74bca"
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
| InvalidParameterValue.SessionContextTooLong | `SessionContext` is too long. |
| InvalidParameterValue.SessionId | The deduplication ID already exists. The request is removed due to duplication. |
| InvalidParameterValue.SessionIdTooLong | `SessionId` is too long. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33640](https://www.tencentcloud.com/document/product/1041/33640)*
