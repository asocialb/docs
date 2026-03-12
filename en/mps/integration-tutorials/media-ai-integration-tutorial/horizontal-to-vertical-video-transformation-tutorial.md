# Horizontal-to-Vertical Video Transformation Tutorial

## Overview

### About Horizontal-to-Vertical Video Transformation

Horizontal-to-vertical video transformation is not merely a rotation but involves identifying the region of interest (ROI) and cropping a video to a certain proportion suitable for playback on mobile devices. Horizontal-to-vertical video transformation enables batch generation of short videos and allows existing horizontal video resources to be converted into vertical video resources.

![Intelligent cropping is performed by following the ROI (typically the location of the ball in sports videos) when the video is converted into a vertical one.](https://staticintl.cloudcachetci.com/cms/backend-cms/dd33d330ad3511ef9b4c525400bdab9d.png)

### Demo

1. Access the [Experience Center](https://mps.live/demo/ai/htv) to navigate to the Horizontal to vertical page. On the right side, select an offline video file, specify the scenario type and ratio, and click **One-Click Processing**.
2. Once the processing is complete, you can view the results.

> **Note:**The function of the MPS Demo is relatively simple, only for experiencing the basic effect, please use the API access to test the complete effect.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b3ec6b18564b11f09a935254007c27c5.png)

### Input and Output Formats

The input video files support the following formats:

- Encoding standards: MPEG, H.264, and H.265.
- Container formats: .mp4, .avi, .mkv, .mov, and .mpg.

The output video files are uniformly encoded in H.264 and formatted in .mp4. You can preview videos using the Google Chrome browser. If you require transcoding and remuxing of formats, you can process it locally or use the audio/video transcoding feature provided by Media Processing Service (MPS).

## Integration Method 1: Initiating a Task via API

### 1. Calling an API

You can directly initiate a POST request to Tencent Cloud. The API request domain name is mps.tencentcloudapi.com. Call the [MPS API](https://www.tencentcloud.com/document/product/1041/33640), select **AiAnalysisTask**, and set Definition to **28 (preset horizontal-to-vertical video transformation template).** ExtendedParameter is an extended parameter, and its value is an **escaped JSON string**. For specific parameter meanings, see [Extended Parameter Description](#note) below.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fe38bf01ad3511ef897b52540075b605.png)

#### **Request Example**

> **Note:**Currently, the horizontal-to-vertical video transformation feature supports two input sources: [Tencent Cloud Object Storage (COS)](https://www.tencentcloud.com/products/cos) and URL download addresses. AWS S3 is currently not supported.

```
{    "Action": "ProcessMedia",    "Version": "2019-06-12",    "InputInfo": {        "Type": "URL",        "UrlInputInfo": {            "Url": "https://..." // Replace it with the URL of the video that needs horizontal-to-vertical transformation, or refer to the "ProcessMedia" API document.        }    },    "OutputStorage": {        "CosOutputStorage": {            "Bucket": "BucketName",            "Region": "BucketRegion"        },        "Type": "COS"    },    "OutputDir": "/mycos/htv_test/result/",    "AiAnalysisTask": {        "Definition": 28, // Preset horizontal-to-vertical video transformation template ID.        "ExtendedParameter": "{\\"htv\\": {\\"AlgorithmType\\": 1}}"    }     "TaskNotifyConfig": {        "NotifyType": "URL",        "NotifyUrl": "http://callback_url"    }}
```

### 2. API Explorer Quick Verification

You can perform quick verification through [API Explorer](https://console.intl.cloud.tencent.com/api/explorer?Product=mps&Version=2019-06-12&Action=ProcessMedia). After filling in relevant parameter information on the page, you can initiate an online API call.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/052fca29a64911efbd5752540055f650.png)

> **Note:**API Explorer will automatically convert the format. You only need to enter the corresponding ExtendedParameter in JSON format without converting it to a string. If calling the API directly, you need to escape the JSON string.

### 3. Extended Parameter Description

Extended parameters can enable specific capabilities. Since the MPS API cannot parse extended parameters, the value of ExtendedParameter is a **serialized JSON string**. The ExtendedParameter for horizontal-to-vertical video transformation should be placed under htv. Below is an example of a JSON before serialization. Input the escaped parameters when using the API:

```
{    "htv": {      "AlgorithmType": 2,	      "SmoothWeight":  0.75,      "Ratio": "9:16"    }}// After escaping (required when the API is called directly): {\\"htv\\": {\\"AlgorithmType\\": 2, \\"SmoothWeight\\": 0.75, \\"Ratio\\": \\"9:16\\" }}
```

| Name | Type | Description |
| --- | --- | --- |
| AlgorithmType | Integer | Designated Algorithm Categories:1: a general model with a relatively rapid processing speed.2: supports a variety of models and is tailored for optimization.3: Utilizes a precise face detection algorithm; when two faces are detected, they are displayed in a split-screen format, with efforts made to center the faces as much as possible.5: Scale the video directly and center it on the portrait screen. Use an image processed with a frosted glass effect as the background. |
| Ratio | String | Video aspect ratio, which is a string and parsed internally. If parsing fails, the default value of 9**:**16 is used for cropping (for example, "9**:**16" indicates converting to a video with an aspect ratio of 9**:**16, taking the original video's height). |
| FaceDetectConfig | Object | Face detection configurations. |
| OutputPattern | String | For customizing the filename, `timestamp` and `sessionId` serve as available substitution parameters.For instance, `"htv-{sessionId}-{timestamp}"` would result in the output file being named "htv-xxxx-202412250000", where "xxxx" represents the actual sessionId of the task.If not specified, the default output filename will be `"htv-{sessionId}"`. |
| BlurWeight | Integer | Blurring parameter: the higher the value, the more pronounced the blurring effect. **Excessively high parameter values may impede processing speed.** |
| SmoothWeight | Float | A floating-point number between 0 and 1, which controls the parameter for smoothing speed. The smaller the value, the faster the camera moves. |

##### FaceDetectConfig

| Name | Type | Description |
| --- | --- | --- |
| FaceScoreThd | Integer | The recognition threshold for the face detection algorithm. A face is considered valid only when the recognition score exceeds this threshold. |
| FaceAccuracy | String | Optional, the number of executions for the face detection algorithm, defaults to "Balance". Other selectable options include "Efficiency" and "Precision". |
| FallbackConfig | Object | The fallback strategy for face detection includes scenarios with "NoFaceDetect" (no faces detected) and "DoubleFace" (two faces detected). |

##### FallbackConfig

| Name | Type | Description |
| --- | --- | --- |
| NoFaceDetect | String | Options: "Scale", "ScaleWithoutBlur" (default). |
| DoubleFace | String | Options: "Scale", "ScaleWithoutBlur", "SplitScreenVertical" (default). |

- Scale: Center the frame through scaling, and replace the background with an image treated with a frosted glass effect.
- ScaleWithoutBlur: Center the frame through scaling, and replace the background with pure black.
- SplitScreenVertical: The default processing logic for dual faces involves splitting the screen vertically, with each face centered in the top and bottom areas respectively.

### 4. Querying Task Results

- Task callbacks: When initiating an MPS task using [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640), you can set callback information through the TaskNotifyConfig parameter. After the task is completed, the task results will be called back through the configured callback information. You can parse the event notification results through [ParseNotification](https://www.tencentcloud.com/document/product/1041/33679). The [related data structures](#Data) listed below are provided for reference.
- Query via the [DescribeTaskDetail](https://www.tencentcloud.com/document/product/1041/33644) API:
  - For tasks started with the API and a template as described in **Integration Method 1** above, use the `TaskId` from [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) (for example: 24000022-WorkflowTask-b20a8exxxxxxx1tt110253) to parse `AiAnalysisResultSet` in `WorkflowTask`. The [related data structures](#Data) listed below are provided for reference.
  - For tasks started via [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) without a template but with a `ScheduleId`(the subsequent section on [automatic task triggering](https://www.tencentcloud.com/document/product/1041/66045#13338cae-b5e9-416d-84d5-2117b39ef602) explains how to create a schedule), the returned `TaskId` will include "ScheduleTask" (e.g. 24000022-ScheduleTask-774f101xxxxxxx1tt110253). In this scenario, use the `TaskId` to parse `ActivityResultSet` in `ScheduleTask`.
  - For tasks initiated from the console, as described in **Integration Method 2** below, go to  [Tasks -> VOD](https://console.tencentcloud.com/mps/tasks/vod-list) for the task ID and results. You can also parse the`ActivityResultSet` in `ScheduleTask` in the [DescribeTaskDetail](https://www.tencentcloud.com/document/product/1041/33644) API to obtain the task results.
- Query via console: Log in to the console and go to [VOD Processing Tasks](https://console.tencentcloud.com/mps/tasks/vod-list), where the newly initiated tasks are displayed in the task list.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b63e2174a65b11ef9ec3525400f69702.png)

When the subtask status is "Successful", you can go to **COS Bucket > Output Bucket**, find your output directory, and locate the files starting with htv- in the directory, which are the output videos after horizontal-to-vertical video transformation.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c7340c1ea65b11efba3e5254002693fd.png)

### Related Data Structures

##### AiAnalysisTaskHorizontalToVerticalResult

Horizontal-to-vertical video transformation result type.

Referenced by the following APIs: DescribeTaskDetail and ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCode | Integer | Error code. 0: Successful; other values: Failed. |
| Message | String | Error message. |
| Input | AiAnalysisTaskHorizontalToVerticalInput | Horizontal-to-vertical video transformation task input. |
| Output | AiAnalysisTaskHorizontalToVerticalOutput | Horizontal-to-vertical video transformation task output. Note: This field may return null, indicating that no valid value is obtained. |

##### AiAnalysisTaskHorizontalToVerticalInput

Horizontal-to-vertical video transformation task input type.

Referenced by the following APIs: DescribeTaskDetail and ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Horizontal-to-vertical video transformation template ID. |

##### AiAnalysisTaskHorizontalToVerticalOutput

Horizontal-to-vertical video transformation result information.

Referenced by the following APIs: DescribeTaskDetail and ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Path | String | Horizontal-to-vertical video transformation list. |
| OutputStorage | TaskOutputStorage | Storage location of videos after horizontal-to-vertical transformation. Note: This field may return null, indicating that no valid value is obtained. |

## Integration Method 2: Initiating a Task from Console (Zero Code)

### 1. Creating a Task

  1.1. Log in to the [MPS console](https://console.tencentcloud.com/mps) and click **Create Task > Create VOD Processing Task**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f00042d4a65011efae7d5254002693fd.png)

  1.2. Specify an input video file. Currently, the horizontal-to-vertical video transformation feature supports two input sources: [Tencent Cloud COS](https://www.tencentcloud.com/products/cos) and URL download addresses. AWS S3 is currently not supported.
  1.3. In the "Process Input File" step, add the **Intelligent Analysis** node.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ffc9cd6da65011efae7d5254002693fd.png)

In the intelligent analysis settings drawer that pops up, select the **preset horizontal-to-vertical video transformation template (template ID: 28)**.

> Note:If you need to enable the horizontal-to-vertical video transformation feature for a custom intelligent analysis template, you can contact us and provide the **template ID**, and Tencent Cloud MPS developers will configure and enable the horizontal-to-vertical video transformation feature for you.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1a00bd8dad3711ef804852540055f650.png)

  1.4. After specifying the save path for the output video, click **Create** to initiate the task.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1c5e41a9a65111ef888a52540075b605.png)

### **2. Querying Task Results**

Refer to the above [Querying Task Results](#result).

### 3. Automatically Triggering a Task (Optional Capability)

If you require automatically performing horizontal-to-vertical video transformation according to the preset parameters after a video file is uploaded in the COS bucket, you can:

3.1 When creating a task, click **Save The Orchestration**, and configure parameters such as Trigger Bucket and Trigger Directory in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/23d29e7ba65111efb7b7525400bdab9d.png)

3.2 Go to the **VOD Orchestration** list, find the new orchestration, and turn on the switch at **Enable**. Subsequently, any new video files added to the trigger directory will automatically initiate tasks according to the preset process and parameters of the orchestration, and the processed video files will be saved to the output path configured in the orchestration.

> **Note:**It takes 3-5 minutes for the orchestration to take effect after being enabled.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/47a1b6d9ad3711ef804852540055f650.png)


---
*Source: [https://www.tencentcloud.com/document/product/1041/66045](https://www.tencentcloud.com/document/product/1041/66045)*
