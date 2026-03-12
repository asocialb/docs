# Template

Time shifting is powered by the recording capability of CSS. It allows users to rewind and play earlier parts of a live stream. This is commonly used to play back highlights of live streamed sports events.

## Notes

- After creating a time shifting template, you need to bind it to a push domain. The configuration takes effect 5-10 minutes after binding.
- When enabling the new live time-shifting feature, billing will be based on the [Time-shift Data Write Volume](https://www.tencentcloud.com/document/product/267/53262). Using the new live time-shifting feature will also generate [Live Streaming Traffic Bandwidth Fees](https://www.tencentcloud.com/document/product/267/2819) and [Live Transcoding Fees](https://www.tencentcloud.com/document/product/267/39604).
- To timeshift a transcoded live stream, you need to configure a transcoding task for the stream in advance. This will incur transcoding fees. Please make sure the transcoding template used is not deleted.
- When writing time-shift transcoded stream data, transcoding will be initiated first, generating [Live Transcoding Fees](https://www.tencentcloud.com/document/product/267/39604). Please make sure that the selected transcoding template has not been accidentally deleted, otherwise, the accidentally deleted time-shift transcoded stream will not be playable. No transcoding fees will be generated when playing the time-shift transcoded stream.

## Prerequisites

You have activated CSS and added a [push domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Creating a Time Shifting Template

1. Log in to the CSS console and select **Feature Configuration** > [Time Shifting](https://console.tencentcloud.com/live/config/time-shift/template) on the left sidebar.
2. Click **Create template** to set the template information and configure the following settings:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ebc52825c4f911f0a1dc52540044a08e.png)

| Item |  | Description |
| --- | --- | --- |
| Template Name |  | The time shifting template name, which can be 1-10 characters long and can contain Chinese characters, letters, numbers, and _- |
| Template Description |  | The introduction and description of the live broadcast time shift template can be customized (only Chinese, English, numbers, spaces, _, - are supported). |
| Region |  | By default, outside Chinese mainland, Hong Kong, Macao, and Taiwan regions are supported, with the option to select Chinese mainland. Please bind the correct time-shift playback acceleration region, as cross-regional time-shift playback may result in lagging or inability to pull the stream. |
| Stream type | Original stream | If you choose this configuration, the time-shift content will not have transcoding, watermark, or mixed-stream effects. For time-shift content with WebRTC push, the audio may not be compatible with some players. It is recommended to choose "Watermarked Stream" or "Transcoded Stream". |
|  | Watermarked stream | The watermarked stream (watermarked as specified in the selected watermark template) is timeshifted. |
|  | Transcoded stream | When selecting this configuration, the time-shift video content will be the content after transcoding according to the transcoding template ID. If the transcoding template is deleted, the time-shift playback content will become invalid. Transcoded streams will generate [Transcoding Fees](https://www.tencentcloud.com/document/product/267/39604). |
| Time-shift days |  | The default is 7 days, with options to choose 1 day, 3 days, 15 days, and 30 days. |
| TS segment length |  | The default length is five seconds. You can set it to a value between 3 and 10. |

3. After completing the input, click **Save** to confirm.

## Binding a Domain Name

1. Log in to the CSS console, and select **Feature Configuration** > [Time Shifting](https://console.tencentcloud.com/live/config/time-shift/template) on the left sidebar.
  - **Bind a domain to an existing template**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3ee6bcd6c4fa11f0a7ca5254001c06ec.png)

  - **Bind a domain after creating a template**: After [creating a template](https://www.tencentcloud.com/document/product/267/53312#creating-a-time-shifting-template), click **Bind Domain Name** in the dialog box that pops up.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1239dc74c4fa11f0a7ca5254001c06ec.png)

2. In the pop-up window, select a **time shifting template** and a **push domain** **name**（Multiple push domain names can be bound simultaneously） and then click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/24b6e5abc4fa11f085c7525400454e06.png)

## Unbinding a Domain Name

1. Log in to the CSS console, and select **Feature Configuration** > [Time Shifting](https://console.tencentcloud.com/live/config/time-shift/template) on the left sidebar.
2. Select a time shifting template bound with domain names, find the target domain name, and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/58cea842425111efa24b525400a9236a.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c7f8c7fa594011ee9ff8525400d917da.png)

> **Note：**Unbinding a time shifting template will not affect ongoing live streams.

## Modifying a Template

2. Select the target time shifting template, click **Edit** on the right, modify the settings, and click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6dbec20b425111ef98fd52540075b605.png)

## Deleting a Template

2. Select the target time shifting template, and click **Delete** in the upper right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7a3478d1425111efa24b525400a9236a.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/86f68b00425111efa24b525400a9236a.png)

> **Note:**If domain names are bound to a template, you need to [unbind](https://www.tencentcloud.com/document/product/267/53312#unbinding-a-domain-name)them before you can delete the template.In the console, time shifting templates are managed at the domain level. You cannot unbind time shifting rules bound to streams by APIs.

## More

You can also **unbind** and **bind** domains and time shifting templates on the **Domain Management** page. For details, see [Time Shifting Configuration](https://www.tencentcloud.com/document/product/267/52829).


---
*Source: [https://www.tencentcloud.com/document/product/267/53312](https://www.tencentcloud.com/document/product/267/53312)*
