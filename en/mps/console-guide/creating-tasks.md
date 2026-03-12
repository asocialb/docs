# Creating Tasks

## Overview

Media Processing Service (MPS) supports three ways to initiate tasks:

- **Quickly creating tasks in the console**: Processing tasks are manually initiated by selecting files or entering live streams in the console.
- **Automatically triggering tasks**: Processing tasks are automatically initiated after files are uploaded to COS/AWS S3 buckets, without the need to manually create tasks in the console. Currently, only Video on Demand (VOD) files are supported.
- **Initiating tasks via API**: Tasks are initiated by calling the API, suitable for batch processing scenarios.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ecf763e2230911efa0b8525400db4520.png)

## Details

### Quickly Creating Tasks in the Console

- To process audio and video files stored in COS and AWS S3, you can click **Create VOD Processing Task**. If your video files are stored in other public cloud storage products, you can also provide a file download URL as the input source, but the output needs to use Tencent COS product.
- To process live streams, you can click **Create Live Stream Processing Task**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0fe8239b230a11ef90c35254006d3582.png)

#### Specify Input Files

- Select the audio and video files/live streams that need to be processed as the input source, and configure the save path for the processed output files.
- For VOD media processing, you can choose audio and video files from COS or AWS S3 buckets, or provide a file download URL address.

> **Note:**If you choose to input from COS or URL, you need to complete the [Prerequisites > COS Authorization](https://www.tencentcloud.com/document/product/1041/33482#.E6.AD.A5.E9.AA.A42.EF.BC.9A.E6.8E.88.E6.9D.83.E7.AE.A1.E7.90.86) steps to create a service role, allowing MPS to perform read and write operations such as downloading, transcoding, and uploading files in your COS bucket.If you choose to input from AWS S3, you do not need to complete COS authorization, but you need to refer to the [Using Amazon S3 Buckets with MPS](https://www.tencentcloud.com/document/product/1041/54516) document to create an AWS sub-account, S3 input and output buckets, SQS, etc.

- For live stream media processing, you need to enter the live stream URL address (it must be a live address, supporting RTMP, HLS, FLV, etc.).

> **Note:**You need to ensure that the live stream address is correctly entered. If the live stream fails to be pulled, it will retry 3 times. If it still cannot obtain the live stream, the task will be marked as failed.

#### Process Input Files

##### Create Orchestrations

- An orchestration is a combination of various MPS features, serving as an automated processing workflow. By clicking the ![](https://staticintl.cloudcachetci.com/cms/backend-cms/fc36ffa1190011ef8bfe5254002fd0a8.png) node, you can add the required features.
- At least one feature node must be added. You may also, according to your needs, arrange the rich features MPS offers in series or parallel. For example, if you need to perform enhancement operations, such as enhancing the image quality and deburring, on the input file and then reduce the bitrate through transcoding and compression, you can first add an audio/video enhancement node, followed by an audio/video transcoding node.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e6cc81ea230a11ef95b8525400e64ebc.png)

- If you need to perform transcoding and intelligent analysis on the input source at the same time, you can arrange the parallel task workflow as shown below.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5552f8d2230b11ef860b52540049c929.png)

- Each time you add a feature node, you need to set the specific parameters of that feature in the drawer floating layer.
- Taking the audio/video transcoding node as an example, you can choose system preset parameters or previously saved custom parameters by clicking **Select template**. You can also switch to **Custom** to directly edit the parameters. For detailed parameter configuration, refer to [Audio/Video Transcoding Template](https://www.tencentcloud.com/document/product/1041/48784).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fa8b2578231711ef91395254000a29ac.png)

> **Note:**Currently, only audio/video transcoding and audio/video enhancement nodes offer the option to switch to **Custom** to directly edit parameters without the need to save them as templates in advance.If you need to customize the parameters for other feature nodes such as intelligent analysis, identification, screenshot, etc., you can click **Create Custom Template** to enter the **Templates** page to create a template.![](https://staticintl.cloudcachetci.com/cms/backend-cms/180487d2231811ef90c35254006d3582.png)

##### Save the Orchestrations

- You can save the configured orchestrations for reuse later. The saved orchestrations can be viewed in **Orchestrations**.
- When saving, you need to configure the trigger bucket, trigger directory, and other input and output paths to facilitate the subsequent automatic trigger of tasks. For details, see [Automatically Triggering Tasks](#89c16fb9-90fe-43d8-92c9-e2fdcc20d929) below in this document.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2a2dac07231811ef95b8525400e64ebc.png)

##### Selecting Existing Orchestrations

That is, use the previously saved orchestration flow and feature node parameters.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3c61881c231811ef860b52540049c929.png)

##### Event Notification

Event notification can synchronize the progress and status of your tasks in real time during the task processing flow.

- If Tencent Cloud COS/URL is used as the input source, three event notification mechanisms are supported: TDMQ-CMQ callback, HTTP callback, and SCF callback. For detailed description, see [Configure Event Notification](https://www.tencentcloud.com/document/product/1041/58242#.E4.BA.8B.E4.BB.B6.E9.80.9A.E7.9F.A5.E9.85.8D.E7.BD.AE).
- If AWS S3 is used as the input source, two event notification mechanisms are supported: Amazon SQS callback and HTTP callback. For detailed description, see [Creating an SQS queue for transcoding callbacks](https://www.tencentcloud.com/document/product/1041/54516#4707e8a4-0e97-4922-a5aa-cb79022f8faf).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/49e6508b231811efbef6525400a8a0fb.png)

#### Specify Output Path

Specify the default save path for the output file of this task.

### ![](https://staticintl.cloudcachetci.com/cms/backend-cms/933acd29231811ef90c35254006d3582.png)

If you need to set the output path of a specific feature node in the orchestration separately, for example, you have added transcoding, enhancement, and screenshot features in the orchestration, and you expect the screenshot output file to be stored in a different path, you can click the screenshot node in the [Create Orchestrations](#bb57e8b3-7f91-4633-8677-b0c073b6a6e3) step mentioned earlier, and configure it in **More settings - Customize Screenshot Output Path**. You can also adjust the naming convention of different feature output files through this setting. For details, see [Filename Variable](https://www.tencentcloud.com/document/product/1041/33495).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b30fbb48231811ef860b52540049c929.png)

> **Note:**The priority order of the output paths is: **custom output path for each feature node in the orchestration** >**output path configured in the task** >**output path configured in the orchestration**.
> For example:During creation of a task, an existing orchestration was selected, with the output path configured as `[ap-guangzhou]test/output1/` in the orchestration.In the orchestration, an audio/video transcoding node and an audio/video enhancement node were configured, where the transcoding node had a custom transcoding output path configured as `[ap-guangzhou]test/output2/`.The specified output save path for this task is `[ap-guangzhou]test/output3/`.Therefore, in this task, the enhancement's output result will be saved in `[ap-guangzhou]test/output3/`, and the transcoding output result will be saved in `[ap-guangzhou]test/output2/`.

### Automatically Triggering Tasks

Processing tasks are automatically initiated after files are uploaded to COS/AWS S3 buckets, without the need to manually create tasks in the console. Currently, only VOD files are supported.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/01d0a24a231b11efa62352540003d080.png)

1. Click **Go to Configure** to enter the [Orchestrations > VOD Orchestration](https://console.tencentcloud.com/mps/workflows/vod) page, and then click **Create VOD Orchestration**.
2. Configure the trigger bucket and directory, output bucket and directory, the specific task workflow, etc. For detailed configuration instructions, see [VOD Orchestration Configuration Instructions](https://www.tencentcloud.com/document/product/1041/58242).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3b9a02ee231b11efbef6525400a8a0fb.png)

3. By default, auto-trigger is disabled for the orchestration. To enable it, go back to the **Orchestrations > VOD Orchestration** page and click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/fc5e5bca190011ef88ad5254002977b6.png) to enable the auto-trigger feature.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/984b31e6231b11efbef6525400a8a0fb.png)

4. By uploading the video file to be processed in the trigger bucket configured in the orchestration, the newly uploaded video will be processed automatically according to the task configuration in the orchestration, without the need to manually create tasks in the console.

On the **Orchestrations > COS Bucket** page, you can find the **trigger bucket** and **output bucket** configured in the orchestration, where you can conveniently perform operations on files, such as file upload, preview, and download:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/eeac61f0231b11efbef6525400a8a0fb.png)

> **Note:**After auto-trigger is enabled for the orchestration, it will only affect new video files uploaded to the trigger bucket; files previously stored in the trigger bucket will not be processed automatically.

### Initiating Tasks via API

#### VOD Media Processing

Initiate tasks through the API [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640). The following new features have not yet launched on the console but can be experienced via API:

- Media quality inspection: Supports video file format diagnosis, audio and video content detection (jitter, blur, low illumination, overexposure, black and white borders, black and white screens, screen tearing, noise, mosaic, QR code, etc.), and no-reference scoring.

#### Live Stream Media Processing

Initiate a single live stream processing task via the API [ProcessLiveStream](https://www.tencentcloud.com/document/product/1041/33641). It supports the following features:

- Intelligent auditing: Supports image pornography detection, sensitive information detection, and audio pornography detection.
- Intelligent identification: Supports identification of faces, objects, text, and speech. Automatic Speech Recognition (ASR) also supports intelligent translation and real-time subtitle conversion. It includes features such as game tagging.
- Intelligent analysis: Supports real-time news splitting and more.
- Quality inspection: Supports live stream format diagnosis, audio and video content detection (jitter, blur, low illumination, overexposure, black and white borders, black and white screens, screen tearing, noise, mosaic, QR code, etc.), and no-reference scoring among other features.
- Live stream recording.


---
*Source: [https://www.tencentcloud.com/document/product/1041/60692](https://www.tencentcloud.com/document/product/1041/60692)*
