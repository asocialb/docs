# Live Streaming Highlights Editing

Live streaming highlights rely on the time-shifting capabilities, which means that during or after the live stream, a user can select an exciting segment from the past live content, generate a time-shifted playback address, and conveniently redistribute the highlights. Additionally, through media processing capabilities, live streaming highlights can be solidified into object storage for long-term preservation.

This article introduces how to use live streaming time-shifting to create highlights from live content, as well as how to use media processing capabilities to solidify and store live streaming highlight clips.

## Prerequisites

- Using the live streaming highlights clipping feature, please make sure you have created a [time-shift template](https://www.tencentcloud.com/document/product/267/53312), bound the streaming domain, and successfully streamed.
- To use the live broadcast editing and curing capability, please make sure you have activated the Tencent Cloud [MPS](https://console.intl.cloud.tencent.com/mps) service. The solidified content will be stored in the [COS Service](https://www.tencentcloud.com/document/product/436/32955?has_map=1&lang=zh&pg=), and activating the MPS service will automatically activate the COS service.

## Live Streaming Highlights Editing

### Console operation guide

Based on your business needs, you can configure time-shifted playback. For more details, please refer to the [Live Streaming Time-Shift Index Information](https://www.tencentcloud.com/document/product/267/54302?has_map=1) document.

#### Directions

1. After using the domain name bound to the time-shifting template for streaming, select**Feature Configuration** > **Time shifting** > [Time shifting details](https://console.intl.cloud.tencent.com/live/config/time-shift/meta) in the left menu bar to enter the index information page.
2. Select the live stream you want to clip, and click on **Details** on the right side to enter the time-shift details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e4a5312c742211f087e15254005ef0f7.png)

3. You can view the push address and time-shifted content in**Basic Info**.
4. You can move the mouse in the timeline of the**Index Details** to view the position time. Click on the **timeline** to **mark the time**.
5. Click on the timeline to mark the time and preview the time-shifted content.
6. Configure playback domain name: Select the corresponding time-shift playback domain name.
7. Select ABR Stream: Mainstream is selected by default, and substream can be selected through the drop-down menu.
8. To generate a time-shift playback address: Click **Generate Address** to create a time-shift playback address, which supports one-click copying of the address.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/11534b07742311f084fc525400bf7822.png)

### Splice the Address Yourself

You can refer to the [Time Shifting Function Practice](https://www.tencentcloud.com/document/product/267/31565) document to splice the addresses of live broadcast highlight clips according to the rules. You can also refer to the following splicing rules to assemble the addresses of live broadcast highlight clips by yourself.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f18c48e36bfa11eebb14525400c5de2a.png)

## Live Clip Solidification

### Create Clip Persistence Task

1. **Navigate to MPS solidification of time-shifted content**: Choose the solidification file format, eithe**r MP4 type** or**HLS type**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/42fbdada742311f087e15254005ef0f7.png)

2. When you click on **Configure storage**, the system will automatically redirect you to the**MPS** > **Create Task** page. On this page, the system will automatically fill in the time-shift highlights clip address and the corresponding transcoding service orchestration template. You can configure the task according to your business needs.
3. Select the output path and click **Create**. For more details, please refer to the [Task Management](https://www.tencentcloud.com/document/product/1041/48778?has_map=1&lang=en&pg=) document.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8f62e539742311f087e15254005ef0f7.png)

4. Once the task creation is completed, you can view the execution status and results of the video editing task. You can enter the corresponding directory in [COS](https://console.intl.cloud.tencent.com/cos/bucket), and in that directory, you can search for the edited and solidified files. Typically, the file name and path will be determined according to the output parameters you set when creating the task.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/68e21444742411f0bcac525400e889b2.png)

### Create a video editing and solidification task through the API

You can create a video editing and solidification task by initiating a Media Processing Service (MPS) API request:

Enter the input and arrangement ID to initiate the task, and then click [View API Information](https://www.tencentcloud.com/document/product/1041/33640?has_map=1&lang=zh&pg=).

> **Note:**Tencent Cloud provides you with default video editing and solidification remuxing service arrangement templates. The default MP4 remuxing arrangement template ID is 10101, and the default HLS remuxing arrangement template ID is 10100.You can customize and create video transcoding templates based on your business needs. Click [Create Video Transcoding Template](https://console.intl.cloud.tencent.com/mps/templates/avs?tab=video) to enter the template customization settings. For more information, please refer to the[Audio and Video Transcoding Templates](https://www.tencentcloud.com/document/product/1041/48784?has_map=1&lang=en&pg=) documentation.MPS will charge you based on your task type. For more information, please refer to the [Media Processing Service Billing](https://www.tencentcloud.com/document/product/1041/49204?has_map=1&lang=en&pg=) documentation.

Example:

```
{    "InputInfo": {        "Type": "URL",     "UrlInputInfo": {      "Url": "http://domain/AppName/StreamName.m3u8?txTimeshift=on&tsFormat=human_s_8&tsStart=20230202095635&tsEnd=20230202095705&tsCodecname=transcode"    }  },  "OutputStorage": {    "Type": "COS",    "CosOutputStorage": {      "Bucket": "test-130000000",      "Region": "ap-nanjing"    },  },  "OutputDir": "/Liveclip/",  "ScheduleId": 10101,    "Action": "ProcessMedia",     "Version": "2019-06-12"}
```

Should a callback URL be configured, please refer to the documentation for the response package: [Parsing Event Notifications](https://www.tencentcloud.com/document/product/1041/33679?has_map=1).


---
*Source: [https://www.tencentcloud.com/document/product/267/57261](https://www.tencentcloud.com/document/product/267/57261)*
