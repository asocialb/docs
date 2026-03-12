# Media Quality Inspection Integration

## Scenario 1: VOD File Quality Inspection

### Method 1: Initiating a Task in the Console

#### Step 1: Creating VOD Orchestration

1. Log in to the MPS console, click [Create VOD Orchestration](https://console.tencentcloud.com/mps/workflows/vod/add), and add a Media Quality Inspection node in the Actions field.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/41f303d771d611f0b9a25254007c27c5.png)

2. After the node is added, a new page pops up. Select a predefined system template or create a custom template based on the actual business scenario on this page. Then, save the settings.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4276b9bd9a8311f09936525400e889b2.png)

3. Click **Create** at the bottom of the page after node configuration is completed to complete orchestration creation.
4. Return to the VOD orchestration list after the orchestration is created, find the newly created orchestration in the list, and click the switch to enable it. The orchestration will take effect in about 3-5 minutes after it is enabled.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f83f96d3d2e811ef81865254005ef0f7.png)

#### Step 2: Initiating a VOD Quality Inspection Task

Upload VOD files requiring quality inspection to the trigger directory specified in the orchestration configuration after the orchestration takes effect. The uploaded files will be processed for quality inspection according to the configured node and template of the orchestration.

#### Step 3: Managing VOD Quality Inspection Tasks

Quality inspection tasks can be viewed on the [VOD Processing Tasks](https://console.tencentcloud.com/mps/tasks/vod-list) page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0d36d57be43411efb98e525400e889b2.png)

### Method 2: Calling the API for Processing

#### Step 1: Initiating a VOD Quality Inspection Task

To initiate a processing task for video URLs or media files in COS, see [ProcessMedia](https://www.tencentcloud.com/zh/document/product/1041/33640) in API Documentation.

Request example:

```
POST / HTTP/1.1Host: mps.tencentcloudapi.comContent-Type: application/jsonX-TC-Action: ProcessMedia
```

```
{  "InputInfo": {    "Type": "COS",    "CosInputInfo": {      "Bucket": "test-<appid>",      "Region": "ap-shanghai",      "Object": "/video/test.mp4"    }  },  "AiQualityControlTask": {    "Definition": 10  }}
```

Example description:

1. Type can be set to COS or URL. Fill in the source file path based on the Type value.
2. Definition indicates the ID of the template configured in the task. Templates are created by calling CreateQualityControlTemplate.

Response example:

```
}  "Response": {    "TaskId": "26000002-ScheduleTask-8c0bb3a13e10462fc405262c623aeff4tt7"  }}
```

Example description: TaskId indicates the unique ID of the task, which is used to query and manage tasks.

#### Step 2: Querying the Task Details

You can query the execution status and detailed result of a task by task ID. For more information, see [DescribeTaskDetail](https://www.tencentcloud.com/zh/document/product/1041/33644) in API Documentation.

Request example:

```
POST / HTTP/1.1Host: mps.tencentcloudapi.comContent-Type: application/jsonX-TC-Action: DescribeTaskDetail
```

```
{  "TaskId": "26000002-ScheduleTask-8c0bb3a13e10462fc405262c623aeff4tt7"}
```

Response example:

```
}  "Response": {    "WorkflowTask": {      "Output": {        "QualityControlResultSet": [          {            "Type": "BackWhiteEdge",            "QualityControlItems": [              {                "Confidence": 100,                "StartTimeOffset": 12,                "EndTimeOffset": 12              }            ]          }        ],        "ContainerDiagnoseResultSet": [          {            "Category": "StreamAbnormalCharacteristics",            "DateTimeSet": [],            "SeverityLevel": "Warning",            "TimestampSet": [              11.006            ],            "Type": "AudioDuplicatedFrame"          }        ],        "QualityEvaluationScore": 68      }    }  }}
```

### Viewing Quality Inspection Results

After initiating a quality inspection task, you can view the quality inspection result report on the [VOD Task Management](https://console.tencentcloud.com/mps/tasks/vod-list) page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/469b4fbb71df11f09f3d52540099c741.png)

#### Quality Inspection Results Report

The Quality Inspection Results Report shows inspection outcomes, offering video information and previews. Enabled inspection items allow users to check quality issue frequency and overall video rating.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/60ee60c871df11f081ce52540044a08e.png)

If any issues are detected during video quality inspection, the specific time segments where problems occur will be displayed. You can click on the timeline with your mouse to jump directly to the corresponding video segment and review the specific issue.

On the quality inspection issue list page, you can view the precise reporting time for each quality inspection problem, enabling you to further pinpoint and analyze the issues.

## Scenario 2: Live Stream Quality Inspection

### Method 1: Initiating a Task in the Console

#### Step 1: Creating Live Stream Orchestration

1. Log in to the MPS console, click [Create Live Orchestration](https://console.tencentcloud.com/mps/workflows/live/add), and add the Media Quality Inspection node in the Actions field.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6e71928d71d611f0b9a25254007c27c5.png)

2. After the node is added, a new page pops up. Select a predefined system template or create a custom template based on the actual business scenario on this page. Then, save the settings.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6de58c53d2e911ef82a5525400e889b2.png)

3. Click **Create** at the bottom of the page after node configuration is completed to complete orchestration creation.
4. Return to the live stream orchestration list after the orchestration is created, and find the newly created orchestration in the list.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8fd0f8d4d2e911efb1a552540099c741.png)

#### Step 2: Creating a Live Stream Quality Inspection Task

Go to the [Live Processing Tasks](https://console.tencentcloud.com/mps/tasks/live-list) page, click **Create task**, enter the live stream address to be processed on the task creation page, select the live stream orchestration created in the previous step, complete other information as needed, and click **Create** to complete the creation.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d8ca694871d611f096685254001c06ec.png)

#### Step 3: Managing Live Stream Quality Inspection Tasks

Quality inspection tasks can be viewed on the [Live Processing Tasks](https://console.tencentcloud.com/mps/tasks/live-list) page.

### Method 2: Calling the API for Processing

#### Step 1: Initiating a Live Stream Quality Inspection Task

To initiate a live stream processing task, see [ProcessLiveStream](https://www.tencentcloud.com/zh/document/product/1041/33641) in API Documentation.

Request example:

```
POST / HTTP/1.1Host: mps.tencentcloudapi.comContent-Type: application/jsonX-TC-Action: ProcessLiveStream
```

```
{  "Url": "rtmp://tlivecloud.com/live/test",  "TaskNotifyConfig": {    "NotifyType": "URL",    "NotifyUrl": "http://tlivecloud.com/callback"  },  "AiQualityControlTask": {    "Definition": 10  }}
```

Example description:

1. Url indicates the live stream address.
2. TaskNotifyConfig indicates the callback service address. When an issue is detected in the video stream, the issue information will be sent to this address in real time.

Response example:

```
}    "Response": {        "TaskId": "24000002-live-procedure-813dc41e6fdc22dcf24aa6e9c61cp92"    }}
```

Example description: TaskId indicates the unique ID of the task, which is used to query and manage tasks.

#### Step 2: Parsing Live Stream Notifications and Performing Callback for Issues

After a message is received, the content of an MPS live stream processing event notification is parsed from the msgBody field in the message. For details, see [ParseLiveStreamProcessNotification](https://www.tencentcloud.com/zh/document/product/1041/33680).

If TaskNotifyConfig is set when a live stream quality inspection task is initiated, the information on detected live stream issues detected will be sent to the configured address in real time.

Callback request example:

```
POST / HTTP/1.1Content-Type: application/json
```

```
{  "NotificationType": "AiQualityControlResult",  "TaskId": "24000002-procedure-live-813dc41e6fdc22dcf24aa6e9c61cp92",  "AiQualityControlResultInfo": {    "QualityControlResultSet": [      {        "Type": "BackWhiteEdge",        "QualityControlItems": [          {            "Confidence": 100,            "StartTimeOffset": 12,            "EndTimeOffset": 12          }        ]      }    ],    "DiagnoseResultSet": [      {        "Category": "StreamStatusException",        "Type": "StreamOpenFailed",        "Timestamp": 0,        "Description": "Open url failed.",        "DateTime": "2023-11-06T06:37:28Z",        "SeverityLevel": "Fatal"      }    ]  }}
```

Example description: QualityControlResultSet indicates the information on issues detected through content quality inspections. DiagnoseResultSet indicates the information on issues detected through format diagnosis.


---
*Source: [https://www.tencentcloud.com/document/product/1041/67727](https://www.tencentcloud.com/document/product/1041/67727)*
