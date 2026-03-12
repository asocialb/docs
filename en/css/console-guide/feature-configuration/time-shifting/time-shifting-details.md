# Time Shifting Details

Tencent Cloud Live Broadcast supports time-shift management through index information, including functions such as viewing time-shift details, configuring time-shift playback, and live broadcast editing.

## Prerequisites

- You have logged in to the CSS console.
- You have created a [time shifting template](https://www.tencentcloud.com/document/product/267/53312), bound it to a push domain, and successfully pushed a stream.
- To use the live video editing and solidification capability, please make sure that you have activated the Tencent Cloud [MPS](https://console.intl.cloud.tencent.com/mps). The solidified content will be stored in the COS service, and activating the MPS service will automatically activate the COS service.

## Index Information Operation Guide

## Directions

1. Click **Feature Configuration** > **Time Shifting** on the left sidebar and select the [Time shifting details](https://console.tencentcloud.com/live/config/time-shift/meta) tab.
2. Select a domain or enter a stream ID, specify the time period (cannot be longer than 24 hours), and click **Query**.
3. Click **Details** to enter the details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/897796e4742111f0b9a25254007c27c5.png)

4. View the push URL and stream type in the **Basic Info** area.
5. You can move the mouse over the timeline in the**Index Details** page to view the position and time. By clicking on the timeline, you can mark the time.
6. Click the timeline to preview the video at a specific time point and mark that point.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/285c0c6f742211f096685254001c06ec.png)

> **Note:**To preview time-shifted content, the domain used for playback must have an HTTPS certificate. If your playback domain does not have an HTTPS certificate yet, add one in **Domain Management**> [Certificate Management](https://console.tencentcloud.com/live/domainmanage/certificate). Using the time shifting feature will incur playback traffic/bandwidth fees.

7. **Time Shifting and Live Clipping**can be configured as follows**:**

| Item |  | Description |
| --- | --- | --- |
| Select a feature | Time shifting | Generate a time shifting URL that delays live streaming playback by a specific time |
|  | Live clipping | Generate a clip from a live stream at the specified start and end time and store it permanently |
| Playback domain |  | Select a playback domain you added to CSS. |
| Select ABR Stream: （Adaptive Bitrate Streaming） |  | Mainstream is selected by default, and substream can be selected through the drop-down menu. |
| Generate time-shifting playback URL |  | Click **Generate Address**to generate a time-shifting playback URL and copy it.If you select the ABR stream as the main stream, the address will be generated based on the main stream. If you select the substream, the address will be generated based on the substream. |
| Navigate to the MPSfor fixed time-shifting content |  | The encapsulation format can be selected as either **MP4 type** or **HLS type**.When **Live clipping** is selected as the function mode, the mainstream encapsulation format is set to HLS type by default, and the substream encapsulation format is set to MP4 type by default. |

Time shifting

Live clipping

**Generate a time shifting URL that delays live streaming playback by a specific time**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7ae038f3742211f084fc525400bf7822.png)

**Generate a clip from a live stream at the specified start and end time and store it permanently**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b6ebcc17742211f084fc525400bf7822.png)

8. Select the function mode as **Live Clipping**. When you have chosen to navigate to the MPS for fixed time-shifting content, click **Configure storage** to enter **MPS** > **Tasks** > [VOD](https://console.tencentcloud.com/mps/tasks/vod). For more details, please refer to the[Live Streaming Highlights Clipping document](https://www.tencentcloud.com/document/product/267/57261) > [Create Clip Persistence Task](https://www.tencentcloud.com/document/product/267/57261#9302b3a3-4df5-4120-8b71-3ba9d601b777).


---
*Source: [https://www.tencentcloud.com/document/product/267/54302](https://www.tencentcloud.com/document/product/267/54302)*
