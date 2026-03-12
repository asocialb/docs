# ROI Intelligent Recognition

ROI (region of interest) recognition can identify the positions of important visual elements in a video in real time, such as faces, game characters, or streaming hosts, and send this information along with the video to the playback device. Using the ROI information, the player can do things like blur the background in a scene and prevent on-screen comments from covering important elements of the video. This document explains how to create, modify, and delete ROI recognition templates in the console.

## Notes

- A template takes effect about 5-10 minutes after it is created.
- To use the ROI recognition feature, you need to add the parameter `roirecognition`= ROI configuration name to your streaming URL. This lets the player access and process ROI data from the live stream, which can enable features like background blur and preventing on-screen comments from covering important parts of the video. For detailed instructions, see [ROI Intelligent Recognition Feature Practice](https://www.tencentcloud.com/document/product/267/60146). Example streaming URL:

`rtmp://domain/AppName/StreamName?`

`txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)&roirecognition=Template Name`

- The ROI recognition feature is a **paid value-added service**. Using this feature incurs live transcoding fees and Media Processing Service (MPS) intelligent content recognition fees. For specific billing rules, refer to the billing documentation.

## Prerequisites

You have activated Tencent Cloud Streaming Services.

## Creating an ROI Configuration Template

1. Log in to the [CSS Console](https://console.tencentcloud.com/live/livestat) and navigate to **AI Features >** **ROI Intelligent Recognition.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f9801263ca7511f0a7775254005ef0f7.png)

> **Note:**To use the ROI intelligent recognition feature in the Live Streaming Lab, **the first time** you create a template, you will also need to create a service role and authorize the current account to use MPS. Click **Authorize Now** to enter the CAM for authorization.

2. Click **Authorize Now** to enter the CAM role management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/133b6c3efdf111ee9f79525400a7e516.png)

3. On the role management page, click **Grant**to complete the identity verification and finalize the Media Processing Service authorization, enabling normal use of the Media Processing Service.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4c3a2e68fe0111ee83bb525400ae4d13.png)

4. After successful authorization, check the service agreement and click **Start**, and the system will automatically activate the MPS product and open the Intelligent Streaming Media Processing management page.
5. Enter the ROI Intelligent Recognition management page, and click **Create ROI template**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1f0fa4ebca7611f09e745254007c27c5.png)

6. Enter the ROI configuration page and proceed with the following configuration:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2ef6b341349711f0a927525400e889b2.png)

| Configuration Item | Description |
| --- | --- |
| Name | The default prefix "roi" is added to the template name. The template name can be 1-10 characters long (only combinations of letters and digits are supported). |
| Description | Supports only Chinese, English, digits, spaces, underscores (_), hyphens (-) and can be up to 100 characters long. |
| Training Model | Default is **General**. Supported training models include: Honor of Kings, NBA2K Game, and Live Shows.General: Capable of recognizing common areas of human eye focus in different environments.Honor of Kings: Capable of recognizing hero roles and zones in different environments within the Honor of Kings game.NBA2K Game: Capable of recognizing players, basketballs, scoreboards, and other zones in different environments within the NBA2K game.Live Shows: Capable of recognizing the host's face.**Note:**The system can identify elements such as faces and game characters within the video. Selecting an appropriate training model for the scenario can greatly improve the accuracy of ROI intelligent recognition. If the models provided do not meet the needs of your specific scenario, you can [submit a ticket](https://console.tencentcloud.com/workorder/category) to request a model. |

7. After filling in the configuration items, click **Confirm**to complete.

## Modifying a Template

1. Log in to the [CSS Console](https://console.tencentcloud.com/live/livestat) and navigate to **AI Features >** **ROI Intelligent Recognition**.
2. Select your successfully created ROI configuration template, and click **Edit** on the right to modify the template information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/472f5567ca7611f09e745254007c27c5.png)

3. Click **Confirm** to complete.

## Deleting a Template

1. Log in to the [CSS Console](https://console.tencentcloud.com/live/livestat) and navigate to **AI Features > ROI Intelligent Recognition**.
2. Select your successfully created ROI configuration template, and click **Delete**to the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/600ef85dca7611f0b011525400bf7822.png)

3. Click **OK**to confirm that you want to delete the template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/74c1833d9aa411f0b8b9525400454e06.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/60145](https://www.tencentcloud.com/document/product/267/60145)*
