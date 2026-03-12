# Getting Started

This document helps you quickly understand and integrate the Media Processing Service (MPS). The main steps to use the MPS are as follows:

## Prerequisites

### Sign-up and Login

1. [Sign up for a Tencent Cloud account](https://www.tencentcloud.com/document/product/378/17985).
2. Log in to the Tencent Cloud website, and select **Cloud Products** > **Video Services** > [MPS](https://console.tencentcloud.com/mps) to enter the MPS console and activate the service for free.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/14458f40222211efbef6525400a8a0fb.png)

### Authorization

#### 1. Service Role Authorization

Currently, MPS supports four types of file sources: [Cloud Object Storage (COS)](https://www.tencentcloud.com/products/cos), [Video on Demand Pro (VOD Pro)](https://www.tencentcloud.com/document/product/266/67977), Amazon Simple Storage Service (Amazon S3), and URL download address.

- To use COS, you need to complete COS service role authorization to allow MPS to perform read and write operations (such as downloading, transcoding, and uploading) on files in your COS bucket.
- To use VOD Pro, you need to complete VOD service role authorization to allow MPS to perform read and write operations (such as downloading, transcoding, and uploading) on files in your VOD Pro application.
- To use Amazon S3, you can skip service role authorization, but you need to complete [AWS Integration with MPS](https://www.tencentcloud.com/document/product/1041/54516).
- To use a URL download address, you need to ensure that the URL is publicly accessible and enables direct download. Currently, Chunked mode is not supported. For this input method, the output methods currently only support COS and VOD Pro. Therefore, you also need to complete service role authorization.

> **Note**If you have not completed the authorization, you cannot perform COS-related operations in the MPS console and cannot enable the [event notification feature](https://www.tencentcloud.com/en/document/product/1041/58242#.E4.BA.8B.E4.BB.B6.E9.80.9A.E7.9F.A5.E9.85.8D.E7.BD.AE).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/61a11b54cf2811f0b638525400e889b2.png)

#### 2. Sub-account Authorization

If you use a Tencent Cloud sub-account, you need to ask the owner of the root account to grant the MPS read and write operation permissions to your sub-account. Otherwise, the sub-account cannot use MPS normally. For detailed instructions, see [Account Authorization](https://www.tencentcloud.com/document/product/1041/69220).

## Operation Steps

MPS can process your audio and video files or live streams.

- Offline media processing: Process **offline audio and video files**.
- Live stream media processing: Perform real-time media processing such as recording, intelligent identification and analysis, and quality inspection on **live streams**.

### Offline File Processing

#### Step 1: Initiate a Task

Currently, you can initiate an Offline file processing task by three methods:

- Quickly creating a task in the console: Manually select files in the console and initiate a processing task.
- Automatically triggering a task: After files are uploaded to COS/AWS S3 buckets, a processing task will be automatically initiated, with no need to manually create a task in the console.
- Initiating a task via an API: A task is initiated by calling the API. It is applicable to batch processing of uploaded files.

##### Method 1: Quickly Creating a Task in the Console

1. Go to the [Console Task Creation page](https://console.tencentcloud.com/mps/tasks/create), and click**Create Offline Processing Task**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5f832602c52511f085c7525400454e06.png)

2. Fill in the following information on the Quickly Create Offline File Processing Task page:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/753b9670c52511f086d9525400e889b2.png)

  2.1. **Specify an input file**

Specify the file path or URL address that needs media processing.

  2.2. **Scheme Processing Workflow**
  - With a scheme, you can combine various features to form an automatic processing workflow.
  - Click **Add Feature Node**, to edit the parameters in the opened drawer floating layer.
    - Select a template: Use template parameters preset in the system or saved previously.
    - Custom: Custom parameters.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/27b6c418222411ef95b8525400e64ebc.png)

  2.3. **Specify the output path**

Specify the default save path for the processed output file.

If you need to set a separate output path for a certain feature node in the scheme, e.g., when you add three features, namely transcoding, enhancement, and screencapturing in the scheme, and you expect the output files of screencapturing to be saved in different paths, you can click on the screencapturing node in [Step 2](#.E6.AD.A5.E9.AA.A44.EF.BC.9A.E5.88.9B.E5.BB.BA.E6.9C.8D.E5.8A.A1.E7.BC.96.E6.8E.92), and configure it in **More Settings** > **Custom Screencapturing Output Path**. You can also adjust the naming method of the output files for different features. For details, see the description of [Filename Variable](https://www.tencentcloud.com/document/product/1041/33495).

##### Method 2: Automatically Triggering a Task

1. Go to the [Orchestrations > Offline Orchestration](https://console.tencentcloud.com/mps/workflows/vod) page, and click **Create Offline Service Orchestration**.
2. Configure the trigger bucket and directory, output bucket and directory, specific task flow, etc. For configuration details, refer to [Offline Orchestration](https://www.tencentcloud.com/document/product/1041/58242).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/390bd833224b11efb2cb5254006568c0.png)

3. By default, auto-trigger is not enabled for the scheme. Go back to the **Orchestrations** > **Offline Orchestration** page and click **Enable** to enable the auto-trigger feature.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/103ab610c52611f086d9525400e889b2.png)

4. Upload a video file that needs processing to the trigger bucket configured in the scheme. The newly uploaded video will then be automatically processed according to the tasks configured in the scheme, with no need to manually create a task in the console.

> **Note**After auto-trigger is enabled for the scheme, it will only take effect in video files newly uploaded to the trigger bucket. Files previously stored in the trigger bucket will not be processed automatically.

##### Method 3: Initiating a task via an API

Refer to [Proactively Initiate Transcoding](https://www.tencentcloud.com/document/product/1041/33493), and initiate tasks through an API [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640).

#### Step 2: Manage Tasks

1. By entering the [Offline Task Management](https://console.tencentcloud.com/mps/tasks/vod-list) page, you can see a list of all tasks you have initiated.
2. You can filter tasks to be processed by task status, Task ID, etc. You can also click **View details** to view subtask information, click the Restart button to restart tasks queuing up, play the source video, and perform other operations.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3122944fc52611f086d9525400e889b2.png)

3. By expanding the subtask list, you can view subtask information, play/view subtask files, download subtask output files, view subtask details, and perform other operations.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b687a637225311ef90c35254006d3582.png)

### Live Stream Processing

#### Step 1: Initiate a Task

Currently, you can initiate a live stream processing task by two methods:

- Quickly creating a task in the console: Manually configure and initiate a processing task in the console.
- Initiating a task via an API: A task is initiated by calling an API.

##### Method 1: Quickly Creating a Task in the Console

1. Go to the [Console Task Creation page](https://console.tencentcloud.com/mps/tasks/create), and click**Create Live Processing Task**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/46cce94ac52611f0a1dc52540044a08e.png)

2. Follow the page instructions to configure the live stream address, scheme, and output save path. Currently, the console supports real-time recording of live streams. For detailed template configurations, refer to [Live Stream Recording Template](https://www.tencentcloud.com/document/product/1041/56732).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7117330e224e11ef95b8525400e64ebc.png)

> **Note:**When creating a live stream recording task, ensure that the live stream address is correctly entered. If the live stream fails to be pulled the first time, the pulling operation will be retried three times. If the operation still fails, a message of failure will be returned for the recording task.

##### Method 2: Initiating a Task via an API

Initiate a single live stream processing task via the API [ProcessLiveStream](https://www.tencentcloud.com/document/product/1041/33641). It supports the following features:

- Smart Moderation: Supports recognition of pornographic content in images and sounds, and detection of sensitive information.
- Intelligent Identification: Supports recognition of faces, objects, text, and speech. Speech recognition also supports intelligent translation and real-time subtitle conversion. It includes features such as game tagging.
- Intelligent Analysis: Supports real-time news segmentation and other features.
- Quality Inspection: Supports live stream format diagnosis, video image content detection (shaking, blur, low light, overexposure, black and white edges, black and white screens, image glitch, noise, mosaic, QR code, etc.), no-reference scoring, and other features.
- Live Stream Recording.

#### Step 2: Manage Tasks

Go to the [Live Stream Task Management](https://console.tencentcloud.com/mps/tasks/live-list) page, where you can see a list of all the live stream processing tasks you have initiated. You can view task details, terminate tasks, and perform other operations.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/93b9ae4b224e11ef95b8525400e64ebc.png)

## Feature Integration Tutorials

The previous section describes how to initiate offline media processing and live stream media processing in the MPS console. Features such as transcoding, enhancement, and media AI can all be accessed and used through the above process. For easy integration, detailed integration guides for each feature can be found in the following table:

| **Processing Type** | **Supported Feature** |  | **Integration Tutorial** |
| --- | --- | --- | --- |
| **Offline Media Processing (Offline Audio/Video File Processing)** | Audio/Video transcoding |  | [Audio/Video Transcoding Integration](https://www.tencentcloud.com/document/product/1041/70464) |
|  | Audio/Video enhancement |  | [Audio/Video Enhancement Integration](https://www.tencentcloud.com/document/product/1041/70463) |
|  | Media AI | Smart subtitle | [Smart Subtitle Integration](https://www.tencentcloud.com/document/product/1041/54517) |
|  |  | Smart erasing | [Smart Erasing Integration (New)](https://www.tencentcloud.com/document/product/1041/73595) |
|  |  | Large Language Model (LLM) video summary | [LLM Video Summary Integration](https://www.tencentcloud.com/document/product/1041/66042) |
|  |  | Intelligent highlights | [Highlight Integration](https://www.tencentcloud.com/document/product/1041/66043) |
|  |  | Intelligent video splitting | [Integration of Intelligent Video Splitting](https://www.tencentcloud.com/document/product/1041/66044) |
|  |  | Intelligent horizontal-to-vertical video transformation | [Integration of Intelligent Horizontal-to-Vertical Video Transformation](https://www.tencentcloud.com/document/product/1041/66045) |
|  | Media quality inspection |  | [Integration of Media Quality Inspection](https://www.tencentcloud.com/document/product/1041/67727) |
| **Live Stream Media Processing (Live Stream Processing)** | Media quality inspection |  | [Integration of Media Quality Inspection](https://www.tencentcloud.com/en/document/product/1041/67727#76addff2-aa07-4022-9b85-9433a457642d) |
|  | Live stream recording |  | [Live Stream Recording Integration](https://www.tencentcloud.com/document/product/1041/57048) |
|  | Media AI | Smart subtitle | [Smart Subtitle Integration](https://www.tencentcloud.com/en/document/product/1041/54517#b72f01f5-1922-4ae1-815d-e235acdf346c) |
|  |  | Intelligent highlights | [Highlight Integration](https://www.tencentcloud.com/en/document/product/1041/66043#633b8b8a-818c-4926-b130-8849579d3104) |
|  |  | Intelligent auditing | Currently, the task can only be initiated by calling the [ProcessLiveStream API](https://www.tencentcloud.com/document/product/1041/33641). |
|  |  | Intelligent identification | Currently, the task can only be initiated by calling the [ProcessLiveStream API](https://www.tencentcloud.com/document/product/1041/33641). |
|  |  | Intelligent analysis | Currently, the task can only be initiated by calling the [ProcessLiveStream API](https://www.tencentcloud.com/document/product/1041/33641). |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33482](https://www.tencentcloud.com/document/product/1041/33482)*
