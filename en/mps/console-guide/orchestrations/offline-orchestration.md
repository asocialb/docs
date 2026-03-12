# Offline Orchestration

## Operation Scenarios

Media processing supports orchestration functionality, offering users an intuitive visual canvas to seamlessly connect multiple media processing templates. These templates can be executed sequentially or based on specific conditions. By flexibly combining orchestration elements, users can achieve diverse media processing effects. Once **Offline orchestration** is configured, videos uploaded to the designated Bucket directory will automatically trigger the orchestration workflow, with output files written to the specified Bucket directory. Within the orchestration process, tasks such as audio and video transcoding, audio and video enhancement, screenshot generation, media AI, and media quality inspection can be configured.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/42bf96d4b3a911f0b96752540044a08e.png)

## Creating Offline Orchestration

### Go to the Creation Page

1. Log in to the [MPS Console](https://console.tencentcloud.com/mps), and click **Orchestrations** > **Offline Orchestration** > [Create Offline Service Orchestration](https://console.tencentcloud.com/mps/workflows/vod/add).
2. On the page that appears, create the orchestration based on the business scenario requirements and configure relevant information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/15bc5c5871cc11f09e39525400454e06.png)

### Configure Orchestration

| Configuration Item | Required | Configuration Description |
| --- | --- | --- |
| Trigger type | - | By default, "Tencent Cloud COS" is selected, indicating that the bucket that triggers the orchestration belongs to Tencent COS.When "AWS" is selected, the trigger bucket belongs to AWS S3. This option can be selected if the bucket is configured on AWS services. Refer to [Using Amazon S3 Buckets with MPS](https://www.tencentcloud.com/document/product/1041/54516) for detailed information. |
| Orchestration name | Yes | You can enter a combination of letters, digits, underscores, and hyphens (_). The length cannot exceed 128 characters. Example: "MPS". |
| Trigger bucket | Yes | You can select a bucket created under this `APPID` as the trigger bucket. Once the orchestration is enabled, video file upload to this bucket will automatically trigger the orchestration execution. |
| Trigger directory | No | The directory should end with a forward slash (/). If left unspecified, all directories of the trigger bucket can trigger the orchestration execution. |
| Trigger formats | - | For newly uploaded files in the trigger directory, the orchestration task will only be triggered if they match the specified file extensions, thereby preventing unintended activations.  By default, the **Preset** option is selected. For details on supported trigger formats under presets, please refer to the [Preset Trigger Formats](#formats) section below. Alternatively, you may switch to **Custom** to define your own list of extensions. If **No Extension Restrictions** is selected, all newly uploaded files in the trigger directory—regardless of their extensions or even the absence thereof—will trigger the orchestration task. |
| Output bucket | Yes | By default, the output bucket is the same as the trigger bucket. You can also select another bucket in the same region corresponding to the specified `APPID` as the output bucket. Newly generated video files will be stored in the selected bucket once the service orchestration is completed. |
| Output directory | No | The directory should end with a forward slash (/). If left unspecified, the trigger directory will be taken as the output directory. |
| Enable event notifications | - | Refer to the [Configure Event Notification](https://www.tencentcloud.com/document/product/1041/58242#.E4.BA.8B.E4.BB.B6.E9.80.9A.E7.9F.A5.E9.85.8D.E7.BD.AE) section below for details.Once enabled, the transcoding process and result data will be sent through the selected notification method. |
| Actions | - | Refer to the [Configure Actions](https://www.tencentcloud.com/document/product/1041/58242#.E4.BB.BB.E5.8A.A1.E6.B5.81.E7.A8.8B.E9.85.8D.E7.BD.AE) section below for details.You can quickly build a process by defining process nodes and templates of the service orchestration. |
| Associate Resource | No | This configuration option will only appear if cost allocation has been enabled in the **General Management > General Settings**. After resources are associated, cost allocation can be performed for the bill related to this orchestration based on the resource-bound tags. If you need to modify resources, go to [Cost Allocation Management](https://console.tencentcloud.com/mps/general/splitting). |

#### Preset Trigger Formats

When "Trigger Format" is set to **Preset**, the system will automatically initiate processing for newly uploaded files (including video, audio, or subtitle files) in the specified directory, provided their extensions fall within the list below:

| Category | File Extensions |
| --- | --- |
| Video File Extensions | .mp4, .avi, .mov, .wmv, .flv, .mkv, .mpg, .mpeg, .rm, .rmvb, .asf, .3gp, .webm, .ts, .m4v |
| Audio File Extensions | .mp3, .wav, .aac, .flac, .ogg, .m4a, .amr |
| Subtitle File Extensions | .vtt, .srt |

> **Note:**Only file formats supported by MPS functionality can be processed successfully; otherwise, the orchestration task will fail.**Example:**If an orchestration is configured with an audio/video transcoding node and a .vtt subtitle file is uploaded to the trigger directory, the orchestration will be triggered. However, since the audio/video transcoding feature only supports processing audio and video files, the orchestration task will fail and no charges will be incurred.

#### Configure Event Notification

This feature can provide real-time updates on the progress and status during task execution. You can enable and configure this feature to receive notifications. Currently, Tencent Cloud provides two event notification mechanisms: TDMQ-CMQ callbacks, HTTP callbacks, and SCF callbacks. Detailed information is as follows:

| Callback Type | Configuration Description |
| --- | --- |
| TDMQ-CMQ callbacks | To enable TDMQ-CMQ callback, go to the [TDMQ console](https://console.tencentcloud.com/tdmq/cmq-queue?rid=1) to activate the CMQ service and create a model. Once enabled, the specified CMQ service will receive event notifications from MPS. You need to fill in the following information:TDMQ-CMQ model: Queue model is selected by default.TDMQ-CMQ region: You can select Guangzhou, Shanghai, Beijing, Shanghai Finance, Shenzhen Finance, Hong Kong (China), Chengdu, North America, or West US.Queue name: Custom. |
| HTTP callbacks | When calling the event notification configuration API [TaskNotifyConfig](https://www.tencentcloud.com/document/product/1041/33690), specify the NotifyType parameter to URL and fill in the HTTP callback address in the NotifyUrl parameter. |

#### Configure Actions

You can define the entire service process, add various service nodes (such as **audio and video transcoding, audio and video enhancement, media AI, media quality inspection, and screenshot processing**, encompassing logical nodes.), and apply different templates to each node. The detailed configuration is described as follows:

1. Click the **+**  button to select the required action from the drop-down list and add it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3b2a9062713111f096685254001c06ec.png)

2. After the action is added, the action node is displayed. You can then configure detailed information on the node.

> **Note:**The configuration pages vary for different actions. The following figure shows the page of the **audio/video transcoding**action.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e3eb07d771cc11f0b9a25254007c27c5.png)

#### Execution Conditions

In the orchestration process, first add a media quality inspection node. Subsequently, you can include an "IF condition" node, which serves as a logical node. This node does not create any media processing subtasks but determines whether to execute subsequent nodes based on whether the media asset meets the conditions set within the node.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a4c88fb2713111f0b9a25254007c27c5.png)

> **Note：**The node evaluates whether the conditions are met; if so, it executes the corresponding workflow branch. Otherwise, it proceeds with the Else if workflow branch.Each branch condition supports the addition of multiple evaluation criteria (AND/OR) and allows for the configuration of multiple conditional branches. The priority of branch conditions can be set by dragging and adjusting the branch condition configuration panel.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c97da441713111f087e15254005ef0f7.png)

## Enabling an **Orchestration** to Activate Automatic Task Triggering

Once an orchestration is created, it is disabled by default.

- After the orchestration is enabled, automatic task triggering is activated. When files are uploaded to the trigger bucket configured for the orchestration, the system automatically initiates processing tasks, without the need to manually create tasks in the console.
- If the orchestration is disabled, MPS tasks will not be executed for video files uploaded to the trigger bucket.

> **Note:**Once the orchestration is enabled, it only takes effect in video files newly uploaded to the trigger bucket. Files previously stored in the trigger bucket will not be automatically processed.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/242fb7d7233011efa0b8525400db4520.png)

You can find the **trigger bucket**  &  **output bucket** configured for the orchestration in the menu  **Orchestration > COS Bucket**  page, to conveniently carry out operations such as file upload, preview, download, etc.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a43d8ea7b3a911f097b152540099c741.png)

## Editing and Deleting an **Orchestration**

**Editing an Offline Orchestration**

Click **Edit** in the operation column of the target orchestration to enter the **Orchestration Editing**page. Then, you can modify the orchestration name, trigger bucket, trigger directory, output bucket, output directory, event notification, and configuration items.

**Deleting an Offline Orchestration**

- Click **Delete** in the operation column of the target orchestration to delete it.
- After the orchestration is deleted, MPS tasks will not be executed for video files uploaded to the trigger bucket.

> **Note:**When the orchestration is enabled, it cannot be edited or deleted.


---
*Source: [https://www.tencentcloud.com/document/product/1041/58242](https://www.tencentcloud.com/document/product/1041/58242)*
