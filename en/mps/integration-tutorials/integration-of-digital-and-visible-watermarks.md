# Integration of Digital and Visible Watermarks

## Watermark Feature Introduction

### Overview

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1e2f676cc45c11f0a0935254007c27c5.png)

Media Processing Service (MPS) supports the following types of watermarks:

| Type | Introduction |
| --- | --- |
| Digital watermark | Enables the embedding of custom text information invisible to the naked eye into videos without affecting the visual quality and integrity. Both basic digital watermark and NAGRA NexGuard digital watermark are supported. |
| Visible watermark | Supports adding images with specified formats, such as PNG and JPG, or custom text to videos in a visible form. This solution is suitable for scenarios such as copyright protection and brand promotion. |

### Integration Prerequisites

Before using this feature, you need to complete the following preliminary operations:

- Register/Log in to a Tencent Cloud account, activate MPS, and complete the service role authorization**.**
- If you use a Tencent Cloud sub-account, ensure the account has sufficient permissions to use MPS.

For detailed guidance, see [Quick Start](https://www.tencentcloud.com/document/product/1041/33482). For account authorization issues, see [Account Authorization](https://www.tencentcloud.com/document/product/1041/69220).

## Digital Watermark

MPS digital watermark supports two versions: **basic copyright watermark** and **NAGRA NexGuard forensics watermark**.

| Version | Introduction |
| --- | --- |
| Basic copyright watermark | Basic version: embeds invisible text information into videos without affecting the visual quality and integrity. |
| NAGRA NexGuard forensics watermark | NAGRA NexGuard is a leading digital watermark solution worldwide, featuring strong concealment and possessing broadcasting-grade anti-removal capabilities. It is tailored for piracy tracking and copyright protection of high-value content, such as movies and dramas. |

### Billing Instructions

#### Digital Watermark Addition

"Digital watermark addition" is billed based on the duration of the output video. For pricing details, see [Billing Instructions](https://www.tencentcloud.com/document/product/1041/49204#b68ac422-cfed-4dbb-852c-95aa418d61cc). Since the "digital watermark addition" feature depends on the "audio/video transcoding" or "audio/video enhancement" features, you need to associate a digital watermark template when initiating a transcoding or enhancement task to implement digital watermark addition. Therefore, fees for both "digital watermark addition" and "audio/video transcoding"/"audio/video enhancement" features will be incurred.

#### Digital Watermark Extraction

Watermark extraction is billed based on the number of calls, with each extraction task supporting only a single video. For pricing details, see [Billing Instructions](https://www.tencentcloud.com/document/product/1041/49204#b68ac422-cfed-4dbb-852c-95aa418d61cc).

### Digital Watermark Template Creation

1. Log in to the **MPS console** and go to the [**watermark template**](https://console.tencentcloud.com/mps/templates/watermarks?tab=implicitWatermark) page.
2. Click **Create Watermark Template**, select a watermark type, and enter the template name and watermark content to create a digital watermark template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/20a61d23c45b11f0aa02525400e889b2.png)

> **Note:**Each user can create up to 50 NexGuard forensics watermark templates. Once created, modification or deletion by users is not supported. To modify or delete templates, contact us for processing in the background.

### Initiation of Digital Watermark Addition Tasks

The digital watermark addition feature needs to depend on the audio/video transcoding feature. You can add a digital watermark by associating a digital watermark template when initiating a transcoding task.

Log in to the **MPS console**, go to the [**Create Task**](https://console.tencentcloud.com/mps/tasks/create) page, create an offline file processing task, select an audio/video transcoding node, enable the digital watermark feature in the pop-up settings panel, and associate a digital watermark template.

> **Note:**When using the [audio/video enhancement](https://www.tencentcloud.com/document/product/1041/70463) feature, you can also enable the digital watermark addition feature.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/37ddfcd1c45b11f0b35752540099c741.png)

If the [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) API is called to initiate a task, the parameter example is as follows:

```
{  "InputInfo": {    "Type": "URL",    "UrlInputInfo": {      "Url": "https://test-1234567.cos.ap-guangzhou.myqcloud.com/video/test.mp4"// Replace it with the video URL to be processed.    }  },  "OutputStorage": {    "Type": "cos",    "CosOutputStorage": {      "Bucket": "test-1234567",      "Region": "ap-guangzhou"    }  },  "MediaProcessTask": {    "TranscodeTaskSet": [      {        "Definition": 101005, //101005 is the preset template ID for video transcoding. It can be replaced with the custom audio/video transcoding template ID you create in the console.        "BlindWatermark": {          "Definition": "1234" //Enter the custom digital watermark template ID you create in the console. 1234 is an example and has no practical significance.        }      }    ]  }}
```

### Automatic Triggering of Tasks

If you want to upload a video file to the Cloud Object Storage (COS) bucket and achieve automatic MPS audio/video transcoding and digital watermark addition according to preset parameters, you can:

1. Click Save This Orchestration when creating a task, and configure parameters such as the triggering bucket and directory in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7123de37c45b11f0a0935254007c27c5.png)

2. Then, enter the [offline orchestration list](https://console.tencentcloud.com/mps/workflows/vod), find the newly created orchestration, and enable the switch in the column.
3. For video files that are added subsequently under the triggering directory, tasks will be initiated automatically according to the preset process and parameters of the orchestration, and the processed video files are saved to the output path configured by the orchestration.

> **Note:**It takes 3 to 5 minutes for the orchestration to take effect after being enabled.

### Digital Watermark Extraction

Through the detection and extraction of digital watermarks in the transmitted video, the identity of the plagiarist can be recognized, providing a key basis for copyright protection.

> **Note:**The console currently only supports extracting "basic copyright watermarks". To extract "NexGuard forensics watermarks", [submit a ticket](https://console.tencentcloud.com/workorder/category) to contact us and attach the video file involving suspected unauthorized playback.

Log in to the **MPS console**, go to the [**Digital Watermark Extraction**](https://console.tencentcloud.com/mps/extract_watermark) page, select a video for watermark extraction, and click **Extract Watermark**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/868d9720c45b11f0aa02525400e889b2.png)

When invoking the [ExtractBlindWatermark](https://www.tencentcloud.com/document/product/1041/74705) API to initiate a task, the following serves as a parameter example:

```
{    "Type": "blind-basic",    "InputInfo": {        "Type": "COS",        "CosInputInfo": {            "Bucket": "mycos-123456789",            "Region": "ap-nanjing",            "Object": "/mps_output/blind_watermark/test.mp4"        }    }}
```

## Visible Watermark

### Billing Instructions

There are no additional fees for adding a visible watermark.

### Visible Watermark Template Creation

Log in to the **MPS console**, and go to the [**Watermark Template**](https://console.tencentcloud.com/mps/templates/watermarks) page to create a visible watermark template. Image and text watermarks are supported.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cbff067cc45b11f0aa02525400e889b2.png)

### Initiation of Visible Watermark Addition Tasks

The visible watermark addition feature needs to depend on the audio/video transcoding feature. You can add a visible watermark by associating a visible watermark template when initiating a transcoding task.

Log in to the **MPS console**, go to the [**Create Task**](https://console.tencentcloud.com/mps/tasks/create) page, create an offline file processing task, select an audio/video transcoding node, enable the visible watermark feature in the pop-up settings panel, and associate a visible watermark template.

Up to 10 visible images or text watermarks can be added.

> **Note:**When using the [audio/video enhancement](https://www.tencentcloud.com/document/product/1041/70463) or screenshot feature, you can also enable the visible watermark addition feature.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f301bd68c45b11f09c26525400bf7822.png)

If the [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) API is called to initiate a task, the parameter example is as follows:

```
{  "InputInfo": {    "Type": "URL",    "UrlInputInfo": {      "Url": "https://test-1234567.cos.ap-guangzhou.myqcloud.com/video/test.mp4"// Replace it with the video URL to be processed.    }  },  "OutputStorage": {    "Type": "cos",    "CosOutputStorage": {      "Bucket": "test-1234567",      "Region": "ap-guangzhou"    }  },  "MediaProcessTask": {    "TranscodeTaskSet": [      {        "Definition": 101005, //101005 is the preset template ID for video transcoding. It can be replaced with the custom audio/video transcoding template ID you create in the console.        "WatermarkSet": [          {            "Definition": 1234 //Enter the custom watermark template ID you create in the console. 1234 is an example and has no practical significance.          }        ]      }    ]  }}
```

### Automatic Triggering of Tasks

See the [Automatic Triggering of Tasks](#21ac3118-30cf-4ea7-961b-0c36f4dc3b29) section above.

#### ******


---
*Source: [https://www.tencentcloud.com/document/product/1041/73675](https://www.tencentcloud.com/document/product/1041/73675)*
