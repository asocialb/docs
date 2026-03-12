# Smart Erase Tutorial (New)

> **Notes:**Starting from September 2025, the Smart Erase module is added to the console and API. This tutorial introduces the methods for accessing each feature based on the Smart Erase template. For customers who use the Intelligent Analysis template to access the erasing capability, see the [Smart Erase Tutorial (Old)](https://www.tencentcloud.com/document/product/1041/58269) document.The Smart Erase module supports more custom configurations and is more flexible than the Intelligent Analysis template. The two modules only differ in feature usage. They share the same pricing and incur no billing adjustments.

## Introduction to the Smart Erase Feature

Smart Erase enables blurring, mosaic, or seamless processing of elements like logos, subtitles, human faces, and license plates in video images, thereby making it easy to spread and share content. The feature is widely used in multiple fields, such as short drama platforms, short video platforms, cross-border e-commerce, and independent media studios. For pricing, see [Smart Erase Billing Instructions](https://www.tencentcloud.com/document/product/1041/49204#b71b5f78-d20e-4560-8b9e-a4f02f0d75cf).

| Smart Erase Support Capability |  | Feature Description |
| --- | --- | --- |
| Subtitle removal |  | Removes text subtitles from video images.Seamless processing effect. |
| Logo removal | Basic Edition | Logo removal feature in the Basic Edition.Blur effect. |
|  | Advanced Edition | Logo removal feature in the Advanced Edition.Seamless processing effect. |
| OCR-based subtitle extraction | Extraction only | Extracts subtitle content from the video images based on Optical Character Recognition (OCR) to generate a subtitle file. |
|  | Extraction and translation | Extracts the original subtitles and translates them to generate a subtitle file in the target language. |
|  | Extraction, translation, and embedding | Extracts the original subtitles, translates them to generate subtitles in the target language, and embeds the subtitles into the video images. |
| AI voice replacement (AI dubbing) | Standard timbre | Inputs a video and a translated subtitle file in the target language to generate dubbed audio in the target language and replace the original audio track. This is suitable for scenarios such as video translation.Standard timbre. Only Chinese, English, and Japanese are supported. |
|  | Cloning timbre | Cloning timbre with leading AI voice cloning technology that realistically reproduces voice features. Dozens of languages are supported. |
| Privacy protection processing (human faces and license plates) |  | Recognizes human faces and license plates in video images and performs blurry or mosaic processing to protect privacy information. |

#### Free Trial

Open [Experience Hall](https://mps.live/demo/ai/erase) to go to the Smart Erase experience page. Select a file and erasing type on the right, and click **One-Click Processing**. Wait for processing to complete and view the result.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4e497ff88a2b11f0814e525400bf7822.png)

> **Note:**Note: The Experience Hall feature is relatively simple and only used to experience the basic effects. For a complete test of all features, see the instructions in this document for access with the console and API.

## Access Prerequisites

Before accessing Smart Erase, you need to complete the following prerequisites for using the Media Processing Service (MPS) product: **Register and log in to a Tencent Cloud account**, **activate the MPS product and authorize service roles**.

For detailed guidance, see [Quick Start](https://www.tencentcloud.com/document/product/1041/33482). For account authorization issues, see the [Account Authorization](https://www.tencentcloud.com/document/product/1041/69220) document.

## Integration Step 1: Configuring Template Parameters

Go to the Smart Erase Template page in the console. For parameter descriptions, see [Smart Erase Template](https://www.tencentcloud.com/document/product/1041/72674). To facilitate understanding, the following sections provide template configuration examples categorized by feature and use case.

### Subtitle Removal

#### Billing Overview

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e1a33f08827211f0854e5254001c06ec.png)

Pass the following unescaped JSON to ExtendedParameter (for field details, see [Appendix: Description of ExtendedParameter Fields](/document/product/179424395149918208#1d72953b-1fb8-4cc5-b9c2-a1caf59aa176)).

```
{    "delogo": {        "cluster_id": "gpu_zhiyan",        "CustomerAppId": "subtitle_erase_fast",        "custom_objs": {            "type": 0,            "time_objs": [                {                    "objs": [                        {                            "type": 2,                            "score": 100,                            "rect": {                                "lt_x": 53,                                "lt_y": 228,                                "rb_x": 137,                                "rb_y": 644                            }                        }                    ]                }            ]        }    }}
```

When you use the subtitle removal feature, including automatic erasing, specified area erasing, and secondary processing for missed areas, a "subtitle removal" fee will be charged without distinguishing between the "Area Edition" and "Standard Edition" models. For pricing, see [Smart Erase Billing Instructions](https://www.tencentcloud.com/document/product/1041/49204#b71b5f78-d20e-4560-8b9e-a4f02f0d75cf).

#### Template Configuration Scenario 1: Automatic Erasing (Default Parameters)

Use the default parameters of the template. As shown in the figure below, the system will use an AI model to recognize subtitle text content in the lower central part of the video image, perform seamless erasing, and generate a new video.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/da662b6892af11f087025254001c06ec.png)

The default parameters are suitable for videos with standard subtitle styles and less background interference.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/debd137b92b011f097255254005ef0f7.png)

#### Template Configuration Scenario 2: Adjusting the Automatic Erasing Area to Protect the Video Areas That Do Not Require Erasing and **Reducing Incorrect Erasing Issues**

In automatic erasing mode, the system automatically recognizes existing text areas in the entire video image based on OCR and erases text within the automatic erasing area.

If your video is similar to the example below and has other text content in the lower central part of the image that does not require erasing, you can configure Auto Erase Area to **reduce incorrect erasing issues.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/080b90c992b111f097255254005ef0f7.png)

##### Processing Effect Example

![Left: original video (no need to erase "Love You at All Costs" at the bottom). Middle: Use Auto Erase Area to specify the erasing effect on the subtitle position. Right: erasing effect without specifying Auto Erase Area.](https://staticintl.cloudcachetci.com/cms/backend-cms/e1b70b9e827211f0b3fe525400bf7822.png)

#### Template Configuration Scenario 3: Directly Specifying the Erasing Area at Fixed Subtitle Positions to Reduce Missed Erasing Issues

Usually, when Automatic Erasing is selected as the erase method, the system can automatically recognize the subtitle position accurately. But in specific cases, missed erasing issues may occur, as shown in the figure below:

![The subtitle in the red box has too low background contrast.](https://staticintl.cloudcachetci.com/cms/backend-cms/0a1d0ad387dc11f0814e525400bf7822.png)

Therefore, if your subtitle position is fixed, it is recommended that you select the Specified Area Erasing method. By selecting the area that requires erasing, you can reduce missed erasings to the maximum extent.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/282f0e7892b111f0bdaa525400bf7822.png)

##### Processing Effect Example

![Left: original video. Middle: specified target erasing area in the green box. Right: erasing effect.](https://staticintl.cloudcachetci.com/cms/backend-cms/35996abe87dc11f088af5254005ef0f7.png)

#### Template Configuration Scenario 4: Using the Area Edition Model for Special Subtitle Styles (with Background Shadows, Cursive Fonts, and Dynamic Effects)

Subtitle removal provides two model editions, suitable for different subtitle styles:

- **Standard Edition (recommended)**: Usually, this edition is recommended. It is applicable for videos with standard subtitle styles, providing a better removal effect and superior detail restoration.

![Left: original video. Middle: processing effect of the Area Edition. Right: processing effect of the Standard Edition. If the subtitle style in your video is similar to that in this example, choose the Standard Edition.](https://staticintl.cloudcachetci.com/cms/backend-cms/a45c916587dc11f084bd5254007c27c5.png)

- **Area Edition**: It is applicable for subtitles with special styles (such as background shadows, cursive fonts, and dynamic effects), with a larger erasing area but poorer removal effect compared with the Standard Edition.

![Left: original video. Middle: specified target erasing area in the green box. Right: erasing effect of using the Area Edition model of subtitle removal.](https://staticintl.cloudcachetci.com/cms/backend-cms/db7c1e3e87dd11f088af5254005ef0f7.png)

It is recommended to use the Area Edition model when the Specified Area Erasing method is used.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4aea256392b111f08e0452540044a08e.png)

#### Template Configuration Scenario 5: Adding Additional Erasing Areas on Top of Automatic Erasing

Once this feature is enabled, you can add rectangle boxes. The system erases text content in these boxes on the basis of automatic erasing. This feature is mainly used to specify fixed text areas for erasing to reduce missed erasing issues.

In the following example, except for the automatic erasing area (subtitle position), two additional erasing areas (the warning text area in the upper left corner and the show title area at the bottom) are added to ensure that text in these fixed areas is erased.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/90fb350487e111f0ae9d5254001c06ec.png)

### Subtitle Removal and OCR-based Subtitle Extraction

In addition to subtitle removal, OCR text recognition is supported to extract the original subtitles from the video and translate them.

> **Note:**In the erasing scenario, the original video usually comes with original subtitles. Using OCR for subtitle extraction delivers better and more accurate results. Therefore, the smart erase feature only integrates OCR capabilities. If you wish to generate subtitle files via Automatic Speech Recognition (ASR), you can use the smart subtitle feature. See [Smart Subtitle Access Tutorial](https://www.tencentcloud.com/document/product/1041/54517) for details.

#### Billing Overview

The fees for subtitle removal and OCR-based subtitle extraction (subtitle translation not enabled) or the fees for subtitle removal and OCR-based subtitle extraction and translation (subtitle translation enabled) are charged. For pricing, see [Smart Erase Billing Instructions](https://www.tencentcloud.com/document/product/1041/49204#b71b5f78-d20e-4560-8b9e-a4f02f0d75cf).

#### Template Configuration Example

Specify the subtitle positions to extract and erase in the automatic erasing area, enable OCR-based subtitle extraction, and enable translation as needed.

> **Notes:**If subtitles are in Chinese, English, or both, using OCR for extraction can achieve the best effect. Only text in the automatic erasing area is identified. The text in other areas is not extracted or erased.When multiple text areas exist in the automatic erasing area, the system selects only **one** text area for extraction and erasing, typically the most stable one that exists for the longest time.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/702e3d0f92b111f097255254005ef0f7.png)

##### Effect Example:

![Left: original video. The green box shows the custom automatic erasing area. Right: erasing effect and extracted subtitle file.](https://staticintl.cloudcachetci.com/cms/backend-cms/6455437087f311f084bd5254007c27c5.png)

### OCR-based Subtitle Extraction

No erasing is performed. Subtitles are extracted and translated based solely on OCR text recognition.

#### Billing Overview

If only the original subtitles are extracted, the OCR-based subtitle extraction fee is charged. If subtitle translation is enabled, the OCR-based subtitle extraction and translation fees are charged. For pricing, see [Smart Erase Billing Instructions](https://www.tencentcloud.com/document/product/1041/49204#b71b5f78-d20e-4560-8b9e-a4f02f0d75cf).

#### Template Configuration Example

Currently, the standalone OCR-based subtitle extraction feature does not support custom configuration in the console. You can use Template 25 under the Intelligent Analysis feature of MPS and initiate it via extended parameters. For details, see the OCR-based Subtitle Extraction section in [Smart Erase Tutorial (Old)](https://www.tencentcloud.com/document/product/1041/58269#136f7c0e-1b0a-4150-b63b-a5c05994d31e).

### Subtitle-Level Localization (Simultaneous Subtitle Removal + OCR-based Subtitle Extraction + Subtitle Translation + Subtitle Embedding)

Input a video with subtitles in the original language, and output a video with subtitles in the target language (excluding AI dubbing).

![The left figure: original short video in Chinese. The right figure: Processed output video with English subtitles.](https://staticintl.cloudcachetci.com/cms/backend-cms/11b563bf887911f084bd5254007c27c5.png)

> **Note:**If you wish to use subtitle embedding separately, you can implement it via the audio/video transcoding feature. For details, see [Subtitle Embedding](https://www.tencentcloud.com/document/product/1041/70464#8aad65a1-9588-4230-94fe-e352f675b27a) and [External Subtitles](https://www.tencentcloud.com/document/product/1041/70464#7680e1c7-6c55-4ef2-bd27-70fa21d5efb3) in Audio/Video Transcoding Integration.

#### Billing Overview

The "subtitle removal" + "OCR-based subtitle extraction and translation + subtitle embedding" fee will be charged. For pricing, see [Smart Erase Billing Instructions](https://www.tencentcloud.com/document/product/1041/49204#b71b5f78-d20e-4560-8b9e-a4f02f0d75cf).

#### Template Configuration Example

Currently, the feature does not support custom configuration in the console. You can use Template 25 under the Intelligent Analysis feature of MPS and initiate it via extended parameters. For details, see [Smart Erase Integration (Old)](https://www.tencentcloud.com/document/product/1041/58269#0e191202-ab06-47f5-a048-b0daeec29f74).

### Dubbing-Level Video Localization (Subtitle-Level Localization + AI Dubbing)

![Left: Original video with Chinese subtitles and audio. Right: Processed video with translated subtitles and AI-generated voiceover](https://staticintl.cloudcachetci.com/cms/backend-cms/386ca351c91911f0a93d52540044a08e.png)

The dubbing-level video localization feature automatically identifies original subtitles within videos, performs precise removal and advanced model-based translation, seamlessly embeds translated subtitles into the video, while providing natural and fluent AI-generated voiceovers to enhance viewing experience.

#### Template Configuration Example

Currently, this feature does not support custom configuration via the console. You may utilize Template #25 under MPS's "Intelligent Analysis" function and initiate the process through extended parameters. For detailed instructions, please refer to [Dubbing-Level Video Localization Tutorial](https://www.tencentcloud.com/document/product/1041/74090).

### Logo Removal

Logo removal means erasing graphic content such as logos, icons, and user profile photos in video images. It supports two modes: Basic Edition and Advanced Edition.

- Basic Edition: provides a basic blur effect. It is cost-effective and suitable for animation or videos with a clean background. The "basic fee of smart erase (Logo Removal - Basic Edition)" fee will be charged.
- Advanced Edition: provides a better erasing effect, suitable for reality-style videos such as short dramas. The "Logo Removal - Advanced Edition" fee will be charged.

![Left: original video. The red box shows the logo position. Middle: Basic Edition processing effect. Right: Advanced Edition processing effect.](https://staticintl.cloudcachetci.com/cms/backend-cms/a77764af887911f0b321525400e889b2.png)

#### Billing Overview

The fee for "Logo Removal - Advanced Edition" and "Logo Removal - Basic Edition" is charged. For pricing, see [Smart Erase Billing Instructions](https://www.tencentcloud.com/document/product/1041/49204#b71b5f78-d20e-4560-8b9e-a4f02f0d75cf).

#### Template Configuration Example

Logo removal supports automatic erasing and specified area erasing.

![Red box: dynamic logo that is constantly moving. It is recommended to use automatic erasing (model training required for uncommon Internet logos). Green box: static logo with a fixed position, which can be removed by using specified area erasing.](https://staticintl.cloudcachetci.com/cms/backend-cms/e7b77dda88a011f0bd05525400454e06.png)

- **For common Internet logos or custom logos already in the MPS model library, automatic erasing can be used.**

**Automatic erasing:**AI models are used to automatically recognize and erase logos in full-screen video images, supporting both static and dynamic logos.

Currently, we support more than ten common Internet logos. For logos not in the supported range, we also offer customized training services, which will be charged separately as a model training fee.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/918eee9a92b111f090a8525400e889b2.png)

When Auto-Detection is selected for Auto Erase Area, the system identifies watermarks in full-screen mode by default. If there are watermarks in the image that do not require erasing, you can adjust the automatic erasing area to protect the parts that do not require erasing.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ddfc631a92b111f090a8525400e889b2.png)

##### Effect Example:

![Left: original video. Right: erasing effect.](https://staticintl.cloudcachetci.com/cms/backend-cms/a9fc6ef288a411f088af5254005ef0f7.png)

- **For logos with a fixed position, specified area erasing can be used.**

**Specified area erasing:**For static logos with a fixed position, it is recommended to use specified area erasing to reduce missed or incorrect erasing issues. In addition, image interference may negatively impact automatic erasing. This can be fixed through specified area erasing.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f49090ff92b111f0aa79525400454e06.png)

##### Effect Example:

![Left: original video. Right: erasing effect.](https://staticintl.cloudcachetci.com/cms/backend-cms/7c81338588b711f0814e525400bf7822.png)

### Subtitle Removal and Logo Removal

#### Billing Overview

If you use both subtitle removal and logo removal, the "Logo Removal - Advanced Edition" fee and the "Subtitle Removal" fee are charged. For pricing, see billing instructions in [Smart Erase](https://www.tencentcloud.com/document/product/1041/49204#b71b5f78-d20e-4560-8b9e-a4f02f0d75cf).

#### Template Configuration Example

Currently, the feature does not support custom configuration in the console. You can use Template 25 under the Intelligent Analysis feature of MPS and initiate it via extended parameters. For details, see [Smart Erase Integration (Old)](https://www.tencentcloud.com/en/document/product/1041/58269#cd6852f2-229a-4bb6-9756-f24790fce329).

### Privacy Protection Processing (Human Faces and License Plates)

#### Billing Overview

If you use the privacy protection processing feature, the "Privacy Protection Processing (Face and License Plate)" fee is charged. For pricing, see billing instructions in [Smart Erase](https://www.tencentcloud.com/document/product/1041/49204#b71b5f78-d20e-4560-8b9e-a4f02f0d75cf).

#### Template Configuration Example

Blurring or mosaic effects can be applied to faces and license plates. Simply configure the processing target and desired effect in the template settings.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0037462192b211f087025254001c06ec.png)

##### Effect Example:

![The left figure: raw video image. The right figure: face blurring.](https://staticintl.cloudcachetci.com/cms/backend-cms/20f195e488b811f0814e525400bf7822.png)

## Integration Step 2: Initiating a Task

There are three ways to initiate a task: task creation through the console, task initiation via an API, and automatic task triggering. See the following table for details.

| Initiation Method | Brief Description | Brief Operation Description |
| --- | --- | --- |
| Task creation through the console | Creating a task through the console requires zero coding. It allows you to manually select a single video to initiate a task each time, making it ideal for the testing phase. | To initiate a task, go to the Create Task page of the console, select the input file path, configure the processing workflow and parameters, and specify the output path. |
| Task initiation via an API | Initiating a task via an API involves calling the API to trigger the task. This method is suitable for integration with business processes and batch processing. | To initiate a task, call the API for [initiating the media processing service](https://www.tencentcloud.com/document/product/1041/33640), configure the input file path, smart erase template ID or orchestration ID, and output path. |
| Auto-triggering task | Automatic task triggering requires zero coding. When a new file is uploaded to a specified Cloud Object Storage (COS) path, the task is automatically initiated according to the preset workflow and parameters. This method is ideal for batch automation operations. | Go to the Orchestration Management page of the console, create an orchestration, and enable automatic triggering. |

### Task Initiation Through the Console

1. Go to the [Create Task](https://console.tencentcloud.com/mps/tasks/create) page of the console, and click **Quickly Create VOD Processing Task**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0d171ff392b211f087025254001c06ec.png)

2. Configure the input file path, task processing workflow, and output path sequentially.

In the task processing workflow, add the **Smart Erase** node and select a smart erase template or customize erasing parameters.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3a6b354d92b211f0aa79525400454e06.png)

3. After making the configurations, click **Create** to initiate the task.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/68448f2e92b211f089d25254007c27c5.png)

### Auto-Triggering Task

1. Go to the [VOD Orchestration](https://console.tencentcloud.com/mps/workflows/vod) page of the console and click **Create Video on Demand Service Orchestration**.
2. Configure the trigger directory, output directory, and task configuration on the page to create the orchestration.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9019e34492b211f087025254001c06ec.png)

3. After the orchestration is created, go to the Video on Demand (VOD) orchestration list and **enable** the orchestration. Once the orchestration is enabled, whenever a video file is uploaded to the trigger directory, it will be automatically processed according to the task configuration in the orchestration. There is no need to manually create tasks in the console.

> **Note:**The orchestration takes effect and is automatically triggered in about 3 to 5 minutes after it is enabled. The system will only process new video files uploaded to the trigger directory. Files previously stored in the directory will not be automatically processed.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a5ac328692b211f097255254005ef0f7.png)

### Task Initiation via an API

#### Associated Template ID

Call the [ProcessMedia API](https://www.tencentcloud.com/document/product/1041/33640), select the **SmartEraseTask** task, and set **Definition** to your desired smart erase template ID. The JSON example for **ProcessMedia** is as follows:

```
{   "InputInfo":{ //Input video path. Replace it with your original video.      "Type":"URL",      "UrlInputInfo":{         "Url":"https://test-1234567.cos.ap-nanjing.myqcloud.com/mps_test/myvideo.mp4"      }   },   "OutputStorage":{ //Output COS bucket. Replace it.      "Type":"COS",      "CosOutputStorage":{         "Bucket":"test",         "Region":"ap-nanjing"      }   },   "OutputDir":"/mps_test/output/",//Output folder path. Replace it.   "SmartEraseTask":{      "Definition": 00000 //Replace it with a smart erase template ID. 00000 is a sample code and has no practical significance.   },   TaskNotifyConfig":{ //Optional. Event callback notification configuration.      "NotifyType":"URL",      "NotifyUrl":"http://www.qq.com/callback"   }}
```

#### Associated Orchestration ID

If you have created an orchestration, you can also call the [ProcessMedia API](https://www.tencentcloud.com/document/product/1041/33640), and set **ScheduleId** to your orchestration ID to initiate a task. The JSON example for **ProcessMedia** is as follows:

```
{   "InputInfo":{ //Input video path. Replace it with your original video.      "Type":"URL",      "UrlInputInfo":{         "Url":"https://test-1234567.cos.ap-nanjing.myqcloud.com/mps_test/myvideo.mp4"      }   },   "OutputStorage":{ //Output COS bucket. Replace it.      "Type":"COS",      "CosOutputStorage":{         "Bucket":"test",         "Region":"ap-nanjing"      }   },   "OutputDir":"/mps_test/output/",//Output folder path. Replace it.   "ScheduleId": 12345, //Replace it with a custom orchestration ID. 12345 is a sample code and has no practical significance.   TaskNotifyConfig":{ //Optional. Event callback notification configuration.      "NotifyType":"URL",      "NotifyUrl":"http://www.qq.com/callback"   }}
```


---
*Source: [https://www.tencentcloud.com/document/product/1041/73595](https://www.tencentcloud.com/document/product/1041/73595)*
