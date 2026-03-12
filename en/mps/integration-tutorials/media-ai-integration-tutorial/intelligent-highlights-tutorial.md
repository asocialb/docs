# Intelligent Highlights Tutorial

## Overview

The Intelligent Highlights feature uses intelligent algorithms to automatically capture and generate highlights in a video, providing users with quick review and sharing.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f8bf9524a2fd11efb81c52540055f650.png)

#### Demo

1. Access the [Experience Center](https://mps.live/demo/ai/highlight) to navigate to the Intelligent Highlights page. On the right side, select either an offline video file or a live stream, specify the video content category, and click **One-Click Processing**.
2. Once the processing is complete, you can view the results.

> **Note:**The function of the MPS Demo is relatively simple, only for experiencing the basic effect, please use the API access to test the complete effect.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/014db0a8563211f090d5525400bf7822.png)

## Presetting Template

Media Processing Service (MPS) offers an Intelligent Highlights preset template ( **Template ID: 26**). You can initiate Intelligent Highlights tasks based on this template. For detailed steps, please refer to the section below [Initiating Intelligent Highlights Task](#Highlights).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8e65a222a19e11ef834b525400f69702.png)

## Initiating Intelligent Highlights Tasks

## **Scenario One: Processing Offline Video Files**

### Method 1: API Integration

#### 1. Quick Verification using API Explorer

First, please go to the [MPS console](https://console.tencentcloud.com/mps/index) to activate the service and confirm [COS Authorization](https://www.tencentcloud.com/document/product/1041/33482#.E6.AD.A5.E9.AA.A42.EF.BC.9A.E6.8E.88.E6.9D.83.E7.AE.A1.E7.90.86) is completed.

Then, navigate to the [API Explorer](https://console.intl.cloud.tencent.com/api/explorer?Product=mps&Version=2019-06-12&Action=ProcessMedia) online debugging page, select `ProcessMedia` interface, and fill in input/output paths, and template ID. Set `AiAnalysisTask` **Definition** to **26**  (Presetting template for intelligent highlights), and use **ExtendedParameter** for specific functionalities. Details on extended parameters are provided in the section below [Extended Parameters](#note).

> **Note:**API explorer will automatically convert, so you can directly fill in the corresponding json for ExtendedParameter without converting it into a string. However, if you directly call the API, you need to escape the JSON string. ExtendedParameter example: {"hht":{"top_clip":10, "force_cls":5003, "need_vad":1, "threshold":0.9, "merge_time":60, "merge_type":0, "res_save_type":1}}For the meaning of the parameters, please refer to the following section [Extended Parameter description](#note). To ensure the processing effect, it is recommended that you contact us to confirm the specific configuration offline.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/102b7daca30311efa5395254002693fd.png)

#### 2. Initiating via API

The above explained how to use the API explorer to call and debug the interface online. You can also directly initiate a POST request to Tencent Cloud. API request domain: mps.tencentcloudapi.com. While initiating a POST request, the definition is the preset intelligent highlight template ID (26). Below is a reference example for the request:

> **Note:**When directly calling the API, you need to escape the JSON string when inputting the ExtendedParameter parameter.

```
{    "InputInfo": {        "Type": "URL",        "UrlInputInfo": {            "Url": "https://mg-aidata-1258344699.cos-internal.ap-guangzhou.tencentcos.cn/test/hht_test/MyStoryForYouEP39.mp4"        }    },    "OutputStorage": {        "Type": "COS",        "CosOutputStorage": {            "Bucket": "mg-aidata-1258344699",            "Region": "ap-guangzhou"        }    },    "OutputDir": "/test_data/",    "AiAnalysisTask": {        "Definition": 26,        "ExtendedParameter": "{\\"hht\\":{\\"top_clip\\":10, \\"force_cls\\":5003, \\"need_vad\\":1, \\"threshold\\":0.9, \\"merge_time\\":60, \\"merge_type\\":0, \\"res_save_type\\":1}}"    }}
```

#### 3. Querying Task Results

- Task callback: When using [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) to initiate an MPS task, you can set callback information through the `TaskNotifyConfig` parameter. Once the task is processed, the task result will be called back through the configured callback information. You can parse the event notification results through [ParseNotification](https://www.tencentcloud.com/document/product/1041/33679).
- Query via the [DescribeTaskDetail](https://www.tencentcloud.com/document/product/1041/33644) API:
  - For tasks started with the API and a template as described in **Integration Method 1** above, use the `TaskId` from [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) (for example: 24000022-WorkflowTask-b20a8exxxxxxx1tt110253) to parse `AiAnalysisResultSet` in `WorkflowTask`.
  - For tasks started via [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) without a template but with a `ScheduleId`, the returned `TaskId` will include "ScheduleTask" (e.g. 24000022-ScheduleTask-774f101xxxxxxx1tt110253). In this scenario, use the `TaskId` to parse `ActivityResultSet` in `ScheduleTask`.
  - For tasks initiated from the console, as described in **Integration Method 2** below, go to  [Tasks -> VOD](https://console.tencentcloud.com/mps/tasks/vod-list) for the task ID and results. You can also parse the`ActivityResultSet` in `ScheduleTask` in the [DescribeTaskDetail](https://www.tencentcloud.com/document/product/1041/33644) API to obtain the task results.
- Console query task: Enter the console [VOD Processing Tasks](https://console.intl.cloud.tencent.com/mps/tasks/vod-list), the newly initiated tasks will be displayed in the Task List.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d8c192dfa61811efae7d5254002693fd.png)

When the subtask status is "Success", you can go to **COS Bucket > Output Bucket** to find your output directory, and the files starting with `hht` in the directory are the Intelligent Highlights output files, including video files and cover images.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e0a225e1a61811efb7b7525400bdab9d.png)

### Method 2: Console Task Initiation (Zero-Code Automatic Generation)

> **Note:**Initiating a task from the console requires a preset template (preset intelligent highlights parameters). Due to some special parameters in the highlights that cannot be configured in the template, it may affect the effect of the Intelligent Highlights. Therefore, it is recommended to use the API integration.

#### 1. Creating a Task

1.1. Go to [MPS console](https://console.intl.cloud.tencent.com/mps/tasks/create) and then click **Creating a Task > Quick Create a VOD Processing Task.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5c066820a1a011ef992f52540075b605.png)

1.2. First, specify the input video file. Currently, the Horizontal-to-Vertical Video Transformation feature supports two types of input sources: [Tencent Cloud Object Storage (COS)](https://www.tencentcloud.com/products/cos) and URL download link. AWS S3 is not supported.

1.3. Then, add **Intelligent Analysis** at the "Process Input Files" step.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4b936aaba1a011efa04c5254002693fd.png)

1.4. In the pop-up Intelligent Analysis Settings window, select the **Intelligent Highlights Preset Template (Template ID:26)**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/81afc2b1a1a011efa0b3525400bdab9d.png)

1.5. Finally, specify the output video save path, and click **Create**to initiate the task.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fc5dbbc4a1a011efa646525400329841.png)

#### **2. Querying Task Results**

Refer to the above text [3. Querying Task Results](#result).

#### 3. Automatically Triggering Tasks (Optional)

If you want to upload a video file to the COS bucket and achieve automatic Smart Erase according to preset parameters, you can:

3.1. Click **Save the Orchestration** when creating the task, and configure the Trigger Bucket, Trigger Directory, and other parameters in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb326c22a30411efb3de525400d5f8ef.png)

3.2. Then, go to the **VOD Orchestration List**, find the newly created orchestration, and enable it by clicking the **Enable** button. As for the subsequent new video files in the Trigger Directory, tasks will be automatically triggered according to the preset process and parameters in the orchestration, and the processed video files will be saved to the output path configured by the orchestration.

> **Note:**It takes 3-5 minutes to take effect after the orchestration is successfully enabled.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/214f1157a30611efa5395254002693fd.png)

## Scenario Two: Processing Live Streams

### 1. Initiating Requests

#### **Initiating Requests via API Explorer**

To initiate a live stream processing task by calling the API, you can refer to the [Initiate Processing on Live Streams](https://www.tencentcloud.com/document/product/1041/33641). You can click [API Explorer Debugging](https://console.tencentcloud.com/api/explorer?Product=mps&Version=2019-06-12&Action=ProcessLiveStream) in the file to enter the page, and fill in the relevant parameter information to initiate an online call.

The OutputStorage can be filled in by referring to the offline video scene processing above. An ExtendedParameter example is as follows, and the specific parameter meaning can be found in the [Extended Parameters](#note).

```
 {"hht":{"top_clip":10, "force_cls":5003, "need_vad":1, "res_save_type":1}}
```

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ad52d5a1a32a11efae16525400bdab9d.png)

#### **Initiating via API**

A POST request is initiated directly to Tencent Cloud, and the definition is the ID of the created video analysis template. Below is a request reference example:

```
{    "Url": "http://mps-pull.test.org/live/test.flv",    "TaskNotifyConfig": {        "NotifyType": "URL",        "NotifyUrl": "http://test.cloud.com/callback"    },    "OutputStorage": {        "Type": "COS",        "CosOutputStorage": {            "Bucket": "mg-aidata-1258344699",            "Region": "ap-guangzhou"        }    },    "OutputDir": "/output/",    "AiAnalysisTask": {        "Definition": 26,        "ExtendedParameter": "{\\"hht\\":{\\"top_clip\\":10, \\"force_cls\\":5003, \\"need_vad\\":1, \\"threshold\\":0.9, \\"merge_time\\":60, \\"merge_type\\":0, \\"res_save_type\\":1}}"    }}
```

### 2. Receiving Callbacks

Refer to [Parse Live Stream Processing Results](https://www.tencentcloud.com/document/product/1041/33680) to parse AiAnalysisResultInfo fields.

### 3. Task Termination Protocol

Refer to [Task Management Documentation](https://www.tencentcloud.com/document/product/1041/37462) to manage the initiated tasks.

## Extended Parameter Description

| Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| top_clip | No | int | Select the highlight clips with the highest confidence scores, with a default value of 5.  Example: `\\"top_clip\\":10` indicates outputting up to 10 highlight clips with the highest confidence scores. |
| force_cls | No | int | Specify the highlights category:5003: Variety/TV Series4001: Football4002: Basketball1001: Honor of Kings100101: Honor of Kings Competition1003: League of Legends |
| need_vad | No | int | VAD is used to identify the end of a sentence in video. VAD extension allows complete video speech, enabled by default.1: Use VAD0: Do not use |
| threshold | No | float | Confidence threshold. The clips below the threshold are filtered out, and each type of highlights has default threshold settings.Remarks: You are advised not to set this parameter for the first time. |
| res_save_type | No | int | Whether to save the results, which are saved by default.1: Save results0: Output the time period only |
| output_pattern | No | string | Output video naming format. {} indicates placeholder.{year}-{month}-{day}-{hour}-{minute}-{second}_{start_dts}-{end_dts}-{timestamp}-{session}.mp4Default output format:hht-{year}{month}{day}{hour}{minute}-{session}-{timestamp}-index.mp4 |
| image_pattern | No | string | image-{start_dts}.jpgThe parameters that can be used as placeholders are the same as above.Default output format:hht-{year}{month}{day}{hour}{minute}-{session}-{timestamp}-index.jpg |
| merge_type | No | int | **Note: Only available in offline scenarios. Do not merge for the default value 5003, and merge in other scenarios.**Whether to merge the results into one video:1: Merge (top_clip parameter does not take effect)0: Do not merge (merge_time parameter does not take effect) |
| merge_time | No | int | **Note: Only available in offline scenarios. The default value 5003 is the actual output and the time shall not be longer than one hour in other scenarios.**Specify the video output length when merging into one video. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/66043](https://www.tencentcloud.com/document/product/1041/66043)*
