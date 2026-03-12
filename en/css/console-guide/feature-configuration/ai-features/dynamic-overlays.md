# Dynamic Overlays

The system supports overlaying dynamic overlays onto live streams, enabling effects such as adding advertisements, scoreboards, and character introductions to the live stream visuals.

This document will introduce how to create, modify, and delete dynamic overlay templates using the console.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1374a4b9e9ee11ef840e52540044a08e.png)

## Must-Knows

- The template will take approximately 5 to 10 minutes to take effect after being successfully created.
- The dynamic overlay feature is currently in the beta testing phase. At present, only [transcoding fees](https://www.tencentcloud.com/document/product/267/39604) are charged.
- It is strictly prohibited to use images, videos, or text containing inappropriate content, such as pornography, illegal activities, or other violations, as dynamic overlay material.
- The dynamic overlay effect on live streams can be achieved using the following two methods:
  - Configure the live stream and dynamic overlay input sources in the broadcast console.
  - Add the streaming parameter overlay_url (set to the dynamic overlay preview address) when pushing the stream. An example of a streaming address is as follows:

`rtmp://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)&overlay_url=dynamic overlay preview address`

## Prerequisites

Tencent Cloud Streaming Services (CSS) has been enabled.

## Dynamic Overlay Configuration Management (Administrative Side)

### **Adding Dynamic Overlays**

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and navigate to **Feature Configuration**> **AI Features > Dynamic Overlays**.
2. Click **Add Dynamic Overlays** to open the addition window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dce1573800cc11f18ab45254001d6acc.png)

3. You can select **News**, **Event Scoreboard**, **General Images and Videos**, Or opt for all three options simultaneously.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f320e06f3c6d11f0b95f5254005ef0f7.png)

### Editing

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and navigate to **Feature Configuration**> **AI Features**> **Dynamic Overlays**.
2. In the overlay list, select the dynamic overlay you want to edit based on your business requirements, and click **Edit**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/13e142ef00cd11f18e41525400ecee81.png)

3. After entering the Dynamic Overlay Configuration Management System page, you can customize styles, adjust the content, or copy the control address and preview address as needed. This allows live room managers to share and collaborate effectively.
4. Program Package, Event Scoreboard, and General Images and Videos are enabled by default, but you can manually disable it based on your business requirements. Additionally, you can independently customize program control, subtitle design, tag design, scrolling bar design, event control, event settings, scoreboard design,content control,  image design,video design ,  and text design.

News

Event Scoreboard

General Images and Videos

You can customize the dynamic overlays for the news based on your business requirements.

- **Program Control**
  - The content of tags, program names, and titles can be customized. Both Chinese and English characters, as well as special characters, are supported, with a maximum limit of 30 characters.
  - The content summary and scrolling bar content can be customized, supporting Chinese and English characters as well as special characters, with a maximum limit of 100 characters. The scrolling bar can display multiple items, with an adjustable order and the option to delete any item. The items will scroll and display sequentially.
  - Tags, program names, titles, dates and times, content summaries, and scrolling bars are enabled by default but can be manually disabled.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4599c297e9ea11ef922c5254001c06ec.png)

- **Subtitle Design**
  - Default values can be used in the background color and font color of program names, titles, dates and times, and content summaries. You can also adjust the colors and transparency as needed.
  - Horizontal and vertical positions: The proportion of the screen's total width that the lower-left corner of the material is offset from the left side of the screen. The default value is 0, and the range for the horizontal position is 0 to 100. Improper settings may result in incomplete display of the scoreboard. Clicking Reset will reset both the horizontal and vertical positions to their default values.
  - The size, including width and height, should be set within the range of 0 to 100. Exceeding this range may result in abnormal display of the scoreboard. Clicking Reset will reset both height and width to their default values.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5ad5fb52e9ea11ef9e13525400454e06.png)

- **Tag Design**
  - Default values can be used in the background color and font color of tags. You can also adjust the colors and transparency as needed.
  - Horizontal and vertical positions: The proportion of the screen's total width that the lower-left corner of the material is offset from the left side of the screen. The default value is 0, and the range for the horizontal position is 0 to 100. Improper settings may result in incomplete display of the scoreboard. Clicking Reset will reset both the horizontal and vertical positions to their default values.
  - The size, including width and height, should be set within the range of 0 to 100. Exceeding this range may result in abnormal display of the scoreboard. Clicking Reset will reset both height and width to their default values.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6e8b55abe9ea11ef840e52540044a08e.png)

- **Scrolling Bar Design**
  - Default values can be used in the background color and font color of the scrolling bar title and content. You can also adjust the colors and transparency as needed.
  - Horizontal and vertical positions: The proportion of the screen's total width that the lower-left corner of the material is offset from the left side of the screen. The default value is 0, and the range for the horizontal position is 0 to 100. Improper settings may result in incomplete display of the scoreboard. Clicking Reset will reset both the horizontal and vertical positions to their default values.
  - The size, including width and height, should be set within the range of 0 to 100. Exceeding this range may result in abnormal display of the scoreboard. Clicking Reset will reset both height and width to their default values.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/855c171fe9ea11ef93475254005ef0f7.png)

You can customize the dynamic overlay for the event scoreboard based on your business requirements.

- **Event Control**
  - The scores for the home team and the away team are integers, ranging from 0 to 100.
  - The minutes and seconds for event timing are integers. The range for seconds is 0 to 59.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/00107860e9eb11efaef452540099c741.png)

- **Event Settings**
  - The home team name, away team name, and event title support Chinese and English characters as well as special characters, with a maximum limit of 10 characters.
  - The home and away team logos support local file uploads.
  - The default timing method is clockwise, with an option to select counterclockwise.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2051fe0ce9eb11ef93475254005ef0f7.png)

- **Scoreboard Design**
  - Default values can be used in the background color and font color of the home team, score, away team, timer/session, and event title. You can also adjust the colors and transparency as needed.
  - Horizontal and vertical positions: The proportion of the screen's total width that the lower-left corner of the material is offset from the left side of the screen. The default value is 0, and the range for the horizontal position is 0 to 100. Improper settings may result in incomplete display of the scoreboard. Clicking Reset will reset both the horizontal and vertical positions to their default values.
  - The size, including width and height, should be set within the range of 0 to 100. Exceeding this range may result in abnormal display of the scoreboard. Clicking Reset will reset both height and width to their default values.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/344c4e67e9eb11ef93475254005ef0f7.png)

You can customize dynamic stickers for general images and videos according to your specific business requirements.

- **Content Control**
  - The content of images can be customized.
  - The text content supports both Chinese and English characters, as well as special symbols, with a maximum limit of 100 characters. Multiple text entries can be added.
  - The video content supports customization. You can choose whether to enable audio, which is disabled by default but can be manually activated. Once enabled, the audio from the video will also be integrated into the live stream.
  - Layer Order: Allows users to adjust the layering sequence of images, videos, and text by dragging elements within the console. By default, the order is set to images, videos, and text, with text positioned on the outermost layer.
  - Images, videos, and text content are enabled by default, though they can be manually disabled.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b47731673c6f11f0b95f5254005ef0f7.png)

- Image Design
  - Supports configuring position and size ratios.
  - The horizontal and vertical positions are adjustable. By clicking "**Reset**" , the horizontal and vertical positions will be restored to their default settings.
  - The size settings encompass both height and width. By clicking "**Reset**",  the height and width will be restored to their default values.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c6a618be3c6f11f0aa9f5254001c06ec.png)

- Video Design
  - Supports configuring position and size ratios.
  - The horizontal and vertical positions are adjustable. By clicking "**Reset**", the horizontal and vertical positions will be restored to their default settings.
  - The size settings encompass both height and width. By clicking "**Reset**", the height and width will be restored to their default values.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d6cccf363c6f11f0912c52540044a08e.png)

- Text Design
  - The background color and font color can be set to their default values. Alternatively, you may customize the colors and adjust their transparency as needed.
  - Supports the adjustment of text size, encompassing font size, positioning, and scaling proportions.
  - The horizontal and vertical positions are adjustable. By clicking "**Reset**", the horizontal and vertical positions will be restored to their default settings.
  - The size settings encompass both height and width. By clicking "**Reset**", the height and width will be restored to their default values.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e73f1b9d3c6f11f0aed2525400e889b2.png)

5. Users can click the background option to select a local image or enter a pull stream address to preview the dynamic overlay effect.

News Effect Preview

Event Scoreboard Effect Preview

General Images and Videos preview

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9e5d560ee9ea11efa1f2525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bba2686ee9ea11efab2f5254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/09c82afd3c7911f09bbe525400454e06.png)

6. After completing the configuration, click **Share and collaborate** to copy the configuration output link and share it with the live room manager.

News

Event Scoreboard

General Images and Videos

![](https://staticintl.cloudcachetci.com/cms/backend-cms/44464c3be9ec11efab2f5254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5e5485b0e9ec11efaef452540099c741.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5f577a953c7a11f0912c52540044a08e.png)

### Preview

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and navigate to **Feature Configuration**> **AI Features > Dynamic Overlays**.
2. In the overlay list, select the dynamic overlay you want to preview based on your business requirements and click **Preview** to open the real-time preview window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/38a1a98f00cd11f1b5ce525400074c32.png)

### Renaming

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and navigate to **Feature Configuration**> **AI Features**> **Dynamic Overlays**.
2. In the overlay list, select the corresponding dynamic overlay based on your business requirements and click **Rename**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/51408cdb00cd11f1a1eb52540073fd3b.png)

3. After renaming the dynamic overlay, click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/71709c7900cd11f18e41525400ecee81.png)

### Deleting

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and navigate to **Feature Configuration**> **AI Features > Dynamic Overlays**.
2. In the overlay list, select the dynamic overlay you want to delete based on your business requirements and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9cedd23100cd11f18e41525400ecee81.png)

3. Operate with caution. Once deleted, the dynamic overlay cannot be recovered. If you are certain about the deletion, click **Delete** again to confirm.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b0a1613600cd11f1a616525400a31896.png)

### Copying Address

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and navigate to **Feature Configuration**> **AI Features**> **Dynamic Overlays**.
2. In the overlay list, select the corresponding dynamic overlay based on your business requirements, click **More** to expand, and copy the control address and preview address.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/69d5476c00ce11f1a1eb52540073fd3b.png)

> **Note:**Share the control address with the live room manager. After the control address is opened, the dynamic overlay effects can be customized, and content can be adjusted in real time according to the live room requirements. The adjusted effects will be synchronized in real time to the live stream with the overlay.When you implement the dynamic overlay effect on live streams, the value used for the `overlay_url` parameter in the streaming address or the dynamic overlay input source added in the broadcast console corresponds to the **preview address**.

## Live Room Manager

1. Open the control address shared by the administrative side to customize the dynamic overlay effects as needed and adjust the overlay content according to live stream requirements.
2. By using the preview address shared by the administrative side in the broadcast console or by including it as a streaming parameter in the streaming address, the live stream can be overlaid with dynamic overlays. This enables effects such as scoreboards, character introductions, advertisements, and announcements in the live stream.


---
*Source: [https://www.tencentcloud.com/document/product/267/67937](https://www.tencentcloud.com/document/product/267/67937)*
