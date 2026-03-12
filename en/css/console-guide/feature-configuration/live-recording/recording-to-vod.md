# Recording to VOD

CSS supports recording live streams and storing recording files in VOD for download and preview. This document describes how to create, bind, unbind, modify, and delete recording templates.
You can create a recording template in two ways:

- In the CSS console: For detailed directions, see [Creating a Recording Template](#C_record).
- Using an API: For the API parameters and examples, see [CreateLiveRecordTemplate](https://intl.cloud.tencent.com/document/product/267/30845).

## Notes

- Recording files are saved in [VOD](https://console.tencentcloud.com/vod/overview) by default. Please activate VOD first. To avoid service suspension due to overdue payments, you can also buy VOD storage packages in advance. For more information, see [Getting Started with VOD](https://www.tencentcloud.com/document/product/266/8757).
- After enabling the recording feature, please make sure that your VOD service is in normal status. If it is not activated or is suspended due to overdue payments, live recording will fail. No recording files will be generated. Nor will fees be incurred.
- A recording file is available in about five minutes after recording ends. For example, if you start recording a live stream at 12:00 and stop at 12:30, you can get the recording at around 12:35.
- Limited by the support of audio and video file formats (FLV/MP4/HLS) for codec types, you can only use the H.264 and H.265 video codec and the AAC audio codec.
- After creating a recording template, you can bind it with push domain names. For detailed directions, see [Recording Configuration](https://intl.cloud.tencent.com/document/product/267/34224). The binding takes effect in about 5-10 minutes.
- For the naming rules of generated recording files, see [VodFileName](https://intl.cloud.tencent.com/document/product/267/30767#RecordParam).
- Binding, unbinding, or modifying a template affects only new live streams and not ongoing ones. To make the change apply to ongoing live streams, you need to stop them and push them again.
- Mixed-stream recording does not support mixing streams inside the Chinese mainland with those outside. It will cause an error and playback will fail.

## Prerequisites

- You have activated CSS and added a [push domain](https://intl.cloud.tencent.com/document/product/267/35970).
- You have activated the [VOD service](https://intl.cloud.tencent.com/document/product/266/8757#.E6.AD.A5.E9.AA.A41.EF.BC.9A.E5.BC.80.E9.80.9A.E4.BA.91.E7.82.B9.E6.92.AD).

## Creating a Recording Template

1. Log in to the CSS console and select **Feature Configuration** > [Live Recording](https://console.tencentcloud.com/live/config/record) on the left sidebar.
2. In the live recording settings, choose  **Save to VOD** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e7500372c4f511f0a7ca5254001c06ec.png)

3. Click  **Create template**  to set the template information and proceed with the following configurations:
  - Basic recording configuration: This includes the template name, recording content, recording format, and other configuration items. For details, see [Basic Recording Configuration Instructions](https://www.tencentcloud.com/document/product/267/34223#a9fb1c47-c9fd-4033-b603-6536d57cce40).
  - Basic recording format configuration: This includes HLS file segmentation, max recording time per file, resumption timeout, and other configuration items. For details, see [Basic Recording Format Configuration Instructions](https://www.tencentcloud.com/document/product/267/34223#880da2a2-947b-4fee-9423-79e51e9fd843).
  - (Optional) Advanced recording format configuration: By clicking  **Advanced Configuration** , you can access and select additional configurations. For details, see [Advanced Recording Format Configuration Instructions](https://www.tencentcloud.com/document/product/267/34223#a3a869a0-9854-4f6c-92ae-22f54b8a7b9b).
- Upon completion, click  **Save** .

### Basic Recording Configuration Instructions

> **Note:**When recording the original stream via WebRTC streaming, both HLS and MP4 formats can record and play audio normally, but the FLV format will lose audio. It is recommended to select HLS or MP4 format.When an audio-only transcoding template is selected during specified transcoded stream recording, the HLS/FLV/MP4 recording file will miss the initial 2 seconds of content due to format conversion. Please plan your push and recording schedule accordingly.Initiating a transcoding task is required for recording transcoded streams, which will incur additional transcoding costs. However, if the same transcoding template is used for playback, charges will not be duplicated.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/21c2ed40766611f0b9a25254007c27c5.png)

| Basic Configuration Item |  | Description |
| --- | --- | --- |
| Template Name |  | The template name, which can contain Chinese characters, letters, digits, underscores (_), and hyphens (-). |
| Template Description |  | The template description, which can contain Chinese characters, letters, digits, underscores (_), and hyphens (-). |
| Recording Content | Original stream | Record videos before transcoding, watermarking, and stream mixing.Videos will be recorded before transcoding, watermarking, and stream mixing. Please note that for WebRTC streams, recording the original stream may cause audio playback to fail,  We recommend you select "Watermarked stream" or "Transcoded and watermarked stream". |
|  | Watermarked stream | Videos will be recorded after they are watermarked according to the specified watermark template. If a watermark template is not specified, the original stream will be recorded. |
|  | Transcoded and watermarked stream | Click  **Transcoded and watermarked stream**. You can select an existing transcoding template or click the name of a template to modify its configuration. Videos will be recorded after they are transcoded according to the specified transcoding template. If the template is deleted, the settings for recording watermarked streams will apply. |
| Record Standby Stream Content |  | The "Record Standby Stream Content" toggle is displayed only when the Recording Content includes either a Watermarked stream or a Transcoded and watermarked stream. By default, this toggle is set to off.If it is enabled, the recording files will contain the standby stream content. For operations related to standby streams, see [Standby streams](https://cloud.tencent.com/login/subAccount?s_url=https%3A%2F%2Fconsole.tencentcloud.com%2Flive%2Fconfig%2Fpad). Only when you record the watermarked stream, and transcoded and watermarked stream can the recorded files contain standby stream content.If it is not enabled, the recording file will not include the standby stream content. For operations related to standby streams, see [Standby streams](https://cloud.tencent.com/login/subAccount?s_url=https%3A%2F%2Fconsole.tencentcloud.com%2Flive%2Fconfig%2Fpad).**Note:**When utilizing a watermarked stream, the Standby Stream Content may undergo segmented recording due to differences in resolution and encoding methods from the live stream. To circumvent this issue, it is advisable to designate a transcoded stream for recording. This ensures that the Standby Stream Content undergoes transcoding, effectively preventing segmentation and pixelation issues. |
|  Time zone |  | You can select  **UTC+8**  or  **UTC** .When UTC+8 is selected as the timezone, the naming of the recording files will use the UTC+8 time.When UTC is selected as the timezone, the naming of the recording files will use the UTC time. |
| Recording Format |  | Videos can be output in formats of HLS, MP4, FLV, and AAC (for audio-only recording).The VOD task flow processing service is provided by VOD. Enable the VOD task flow processing service and bind VOD task flows. After the recording file is generated, the VOD task flow template is executed. Currently, post-recording processing is not supported when the recording content is at adaptive bitrates. A compatible solution is under development. Stay tuned. |

#### Basic Recording Format Configuration Instructions

> **Note:**Since the recording file is uploaded as it is recorded, it is impossible to ascertain the end time before uploading, preventing the inclusion of the end time in the file name.Enabling simultaneous recording and uploading ensures files are uploaded immediately after recording ends. A single recording file supports a duration of up to 12 hours and enhances FLV recording's disaster recovery capability. Playback files may experience lag when being dragged for online playback, but this does not affect local playback.

1. Select the recording content and formats and complete the following settings:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7a633690766611f0b9a25254007c27c5.png)

| Basic Recording Format Configuration Item |  | Description |
| --- | --- | --- |
| HLS File Segmentation |  | The HLS file segmentation feature is disabled by default. If post-processing services are needed, it is recommended to enable HLS file segmentation and set the duration of individual HLS recording files.If HLS file segmentation is enabled, the duration of individual HLS recording files can be configured, allowing for the definition of the duration of files produced by post-recording processing.If HLS file segmentation is disabled, recording will continue uninterrupted until the live stream ends. If post-recording processing has been configured, it will be initiated after the recording is complete. |
| Max Recording Time Per File (min) |  | Audio/Video - HLS formatThere is no upper limit on the recording duration of a file in HLS format. If the waiting time for continuation of recording is exceeded, a new recording file will be generated to continue recording.When an HLS recording file is saved to VOD, the duration of a single TS file is set to 60 seconds by default.When HLS file segmentation is enabled, the duration of a single HLS recording file can range from 1 to 720 minutes.Audio/Video - FLV formatThe duration of a single file recorded in FLV format is limited to 1 to 720 minutes.Audio/Video - MP4 formatThe duration of a single file recorded in MP4 format is limited to 1 to 720 minutes.Audio-only - AAC FormatThe duration of a single file recorded in AAC format is limited to 1 to 120 minutes. |
| Resumption Timeout (sec) |  | The resumption timeout period directly affects the time it takes to generate a recording file.When the interval of stream interruption does not exceed the set resumption timeout period, a single live stream will generate only one file. However, the recording file will be received after the resumption timeout period has elapsed, and recording costs will be incurred during the resumption timeout period. Please set a reasonable resumption timeout period. **Only HLS format**  supports resuming recording after stream interruptions, with the resumption timeout period being configurable from 1 to 1,800 seconds. |
| Storage Period (days) |  | You can select Permanent to save a recording file permanently or Custom to specify a storage period (up to 1,500 days). If you set the period to 0, recording files will be saved permanently.If a specified time is chosen, in accordance with national regulations, operators must record live video content and ensure storage backup. It is recommended to store recording files for 60 days to 3 years. |
| VOD Subapplication/Category |  | Recording to a specified VOD category in VOD [application](https://console.tencentcloud.com/vod/app-manage) is supported. By default, the recording is stored in the main application of the account, and only applications with an open write status are supported. |

2. Click **Save**.

#### Advanced Recording Format Configuration Instructions

1. You can switch between different tabs to view the configuration requirements for Audio/Video - HLS format, Audio/Video - FLV format, Audio/Video - MP4 format, and Audio-only - AAC format.

Audio/Video - HLS Format

Audio/Video - FLV Format

Audio/Video - MP4 Format

Audio-only - AAC Format

![](https://staticintl.cloudcachetci.com/cms/backend-cms/da87573a766711f09f3d52540099c741.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/00395fff766811f084fc525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/271ae675766811f096685254001c06ec.png)

**After you select this format, AAC files will be generated when audio-only or quasi-audio/video live streams are pushed.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5721fb4e766811f0bcac525400e889b2.png)

| Advanced Configuration Item | Description |
| --- | --- |
| Post-Recording Process Configuration | The post-recording processing feature is disabled by default. You can manually enable this feature based on your business needs.After enabling post-recording processing, no post-recording process content is selected by default. You need to manually select the corresponding process content.When HLS, FLV, MP4, and AAC audio and video formats are enabled with post-recording processing, the on-demand task flow cannot be empty.You can cancel or change the  **VOD task flow** . You can click to select the bound task flow and choose a task flow already created under the VOD application, or click the task flow name on the current VOD task flow selection page to go to the VOD console to add/modify the task flow configuration.After the task flow is successfully bound, the VOD task flow template will be executed after the recording file is generated, incurring corresponding [video on demand fees](https://tencentcloud.com/document/product/266/2838). |
| Upload while recording | The upload while recording feature is disabled by default. You can manually enable this feature based on your business needs.Currently, only the FLV format supports the upload while recording feature. Once enabled, it allows immediate upload of files after recording ends, supports a recording file duration of up to 12 hours, and enhances FLV recording's disaster recovery capability. Playback files may experience lag when being dragged for online playback, but this does not affect local playback. |

## Binding a Domain Name

  - **Bind a domain to an existing template**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9205a19dc4f611f0a1dc52540044a08e.png)

  - **Bind a domain after creating a template**: After [creating a template](#creating-a-recording-template), click **Bind Domain Name** in the dialog box that pops up.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2af40955c4f611f0a84e5254005ef0f7.png)

2. In the pop-up window, select a **recording template** and a **push domain name** （Multiple push domain names can be bound simultaneously）and then click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/43a0d717c4f611f085c7525400454e06.png)

## Unbinding a Domain Name

2. Select a recording template bound with domain names, find the target domain name, and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/138afea0766911f096685254001c06ec.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9fb779c9f4b011ee941952540085f884.png)

> **Note:**Unbinding a recording template will not affect ongoing live streams.To cancel recording for ongoing streams, stop the streams and push them again.

## Modifying a Template

2. Select the target recording template, click **Edit** on the right, modify the settings, and click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/54b32eef766911f081ce52540044a08e.png)

## Deleting a Template

> **Note:**If domain names are bound to a template, you need to [unbind](#unbinding-a-domain-name) them before you can delete the template.Once a template is deleted, it cannot be restored. Please proceed with caution.In the console, recording templates are managed at the domain level. To unbind recording rules bound to streams by APIs, call [DeleteLiveRecordRule](https://intl.cloud.tencent.com/document/product/267/30843).

2. Select the target recording template, and click **Delete** in the upper right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/83ca74ec766911f09f3d52540099c741.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/98efb5c8766911f0b9a25254007c27c5.png)

## More

For more information about **binding** and **unbinding** a domain name, see [Recording Configuration](https://intl.cloud.tencent.com/document/product/267/34224).

## FAQs

#### How are recording files named?

**Fields:**

| Placeholder | Description |
| --- | --- |
| {StreamID} | The stream ID. |
| {StartYear} | The start time - year. |
| {StartMonth} | The start time - month. |
| {StartDay} | The start time - day. |
| {StartHour} | The start time - hours. |
| {StartMinute} | The start time - minutes. |
| {StartSecond} | The start time - seconds. |
| {EndYear} | The end time - year. |
| {EndMonth} | The end time - month. |
| {EndDay} | The end time - day. |
| {EndHour} | The end time - hours. |
| {EndMinute} | The end time - minutes. |
| {EndSecond} | The end time - seconds. |


---
*Source: [https://www.tencentcloud.com/document/product/267/34223](https://www.tencentcloud.com/document/product/267/34223)*
