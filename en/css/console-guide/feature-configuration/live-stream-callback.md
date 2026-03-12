# Live Stream Callback

CSS supports callbacks. To use this feature, you need to create a callback template in the console, configure an address to receive callbacks for an event, and then bind the template with your push domain name. If the event triggers a callback during live streaming, Tencent Cloud will send a request to your server, which is responsible for responding to the request. After successful verification, the server will obtain a JSON packet of the callback through the address configured.
This document describes how to create, modify and delete a callback template in the console.

**You can create a callback template in the following ways:**

- Create a template in the CSS console. For details, see [Creating a Callback Template](#Callback).
- Create a template with APIs. For the parameters and request sample, see [CreateLiveCallbackTemplate](https://intl.cloud.tencent.com/document/product/267/30815).

## Must-knows

- After creating a template, you need to [bind it with a push domain name](https://intl.cloud.tencent.com/document/product/267/31065). The binding takes effect in about 5-10 minutes.
- Make sure the HTTP or HTTPS server you use to receive callbacks is able to receive requests and respond normally.
- In the console, you can only bind and unbind callback templates at the domain level. For callback rules bound to specific streams by APIs, you need to call [DeleteLiveCallbackRule](https://intl.cloud.tencent.com/document/product/267/30814) to unbind them.
- For information on callback protocols, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).
- For information about the parameters in a callback, see the following documents:
  - [Stream pushing](https://intl.cloud.tencent.com/document/product/267/38081)
  - [Stream interruption](https://www.tencentcloud.com/document/product/267/38081)
  - [Recording Event Notification](https://www.tencentcloud.com/document/product/267/38082)
  - [Recording Status Event Notification](https://www.tencentcloud.com/document/product/267/58590)
  - [Screencapturing Event Notification](https://www.tencentcloud.com/document/product/267/38083?lang=zh&pg=)
  - [Image Audit Event Notification](https://intl.cloud.tencent.com/document/product/267/38083)
  - [Audio Auditing Service Event Notification](https://www.tencentcloud.com/document/product/267/58643?lang=en&pg=)
  - [Relay](https://intl.cloud.tencent.com/document/product/267/42525)
  - [Push errors](https://www.tencentcloud.com/document/product/267/53310)
  - [Recording Error Event Notifications](https://www.tencentcloud.com/document/product/267/68622)
  - [Smart Erasing Event Notification](https://www.tencentcloud.com/document/product/267/73169)
  - [Live subtitles Event Notification](https://www.tencentcloud.com/document/product/267/73170)
  - [Quality Control Event Notification](https://www.tencentcloud.com/document/product/267/73166)
  - [Evaluation Threshold Event Notification](https://www.tencentcloud.com/document/product/267/73167)
  - [Average Score Evaluation Event Notification](https://www.tencentcloud.com/document/product/267/73168)
  - [Live Streaming Summary Event Notification](https://www.tencentcloud.com/document/product/267/74671)
  - [Smart Highlight Event Notification](https://www.tencentcloud.com/document/product/267/74672)

## Creating a Callback Template

Recording Event Notification

2. Select **Feature Configuration**> [Live Stream Callback](https://console.tencentcloud.com/live/config/callback) in the left sidebar.
3. Click **Create Template**, fill in the information, select the types of callbacks you want to receive, enter the callback URLs, and click **Save**.

Callback Type-Standard callbacks

Callback Type-Error callbacks

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c3a1755a7d9511f0960452540044a08e.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dd0b0dcd7d9511f09a9a5254001c06ec.png)

| Configuration Item |  | Description |
| --- | --- | --- |
| Template Name |  | The callback template name, which can contain up to 30 Chinese characters, letters, numbers, underscores (_), and hyphens (-). |
| Template Description |  | The description of the callback template, which can contain up to 100 Chinese characters, letters, numbers, underscores (_), and hyphens (-). |
| Callback Key |  | A custom callback key. It can contain up to 32 letters and numbers. For details, see [Common callback parameters](https://intl.cloud.tencent.com/document/product/267/38081#.E5.9B.9E.E8.B0.83.E5.85.AC.E5.85.B1.E5.8F.82.E6.95.B0). |
| Callback Type | Standard callbacks | Push Callback: Enter an HTTP or HTTPS address to receive push callbacks. |
|  |  | Interruption Callback: Enter an HTTP or HTTPS address to receive push interruption callbacks. |
|  |  | Recording file callback: Enter an HTTP or HTTPS address to receive push Recording file callback. |
|  |  | Recording status callback: Enter an HTTP or HTTPS address to receive push Recording status callback. |
|  |  | Recording Callback: Enter an HTTP or HTTPS address to receive recording callbacks. |
|  |  | Screencapture Callback: Enter an HTTP or HTTPS address to receive screencapture callbacks. |
|  |  | Porn Detection Callback: Enter an HTTP or HTTPS address to receive porn detection callbacks. |
|  |  | Quality Control Callback: Enter an HTTP or HTTPS address to receive quality control callbacks. |
|  |  | Evaluation Threshold Callback: Enter the HTTP or HTTPS address to receive evaluation threshold callbacks. |
|  |  | Average Score Evaluation Callback: Enter the HTTP or HTTPS address to receive average score evaluation callbacks. |
|  |  | Smart Wipe Callback: Enter the HTTP or HTTPS address to receive smart erasing callback. |
|  |  | Live subtitles Callback: The callback information is returned only when a subtitle stream is pulled.Live subtitles Callback: Enter the HTTP or HTTPS address to receive live subtitles callbacks. |
|  |  | Live Streaming Summary Callback：Enter the HTTP or HTTPS address to receive  live streaming summary callbacks. |
|  |  | Smart Highlight Callback：Enter the HTTP or HTTPS address to receive smart highlight callbacks. |
|  | Error callbacks | Error callbacks: Enter an HTTP or HTTPS address to receive push error callbacks. |
|  |  | Recording Error Callback: Enter an HTTP or HTTPS address to receive push Recording callbacks.The Recording Exception Level defaults to "Error", but supports the selection of "Alarm" and allows multiple selections. |

## Binding a Domain Name

1. Log in to the CSS console and select **Feature Configuration** >[Live Stream Callback](https://console.tencentcloud.com/live/config/callback) on the left sidebar.
2. You can bind a domain to a template in one of two ways:
  - **Bind a domain to an existing template**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/73b914e77d9611f0960452540044a08e.png)

  - **Bind a domain after creating a template**: after successfully [creating a Callback template](https://www.tencentcloud.com/document/product/267/31074#creating-a-callback-template.5B.5D(id.3Acallback))，click **Bind Domain Name** in the dialog box that pops up.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d208a74c7d9611f0960452540044a08e.png)

3. In the Bind Domain Name window, select the desired **Live Callback template** and **Push Domain** **name**（Multiple push domain names can be bound simultaneously） , then click on Confirm to successfully bind them.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b008a8907d9611f0bda35254007c27c5.png)

## Unbinding

1. Log in to the CSS console and select **Feature Configuration** >[Live Stream Callback](https://console.tencentcloud.com/live/config/callback) on the left sidebar.
2. Select the Callback template of the bound domain that you want to unbind, then click**Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2d63b3e77d9f11f09cab525400bf7822.png)

3. Confirm it if you wish to unbind the current linked domain, and click **Confirm** to proceed with unbinding.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9710b1b58aca11ef80ff525400d5f8ef.png)

## Modifying a Callback Template

1. Log in to the CSS console and select **Feature Configuration** >[Live Stream Callback](https://console.tencentcloud.com/live/config/callback) on the left sidebar.
2. Select the target callback template and click **Edit** to modify its information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6cfd55407d9f11f0960452540044a08e.png)

3. After modification, click **Save**.

## Deleting a Callback Template

> **Note:**If the template has been associated, you must first [Unbinding](https://www.tencentcloud.com/document/product/267/31074#fc56529b-3f7e-4bf8-90b5-8ee8eca29e5d) it before performing a deletion process.Note that a deleted template cannot be recovered. Proceed with caution.

1. Log in to the CSS console and select **Feature Configuration** >[Live Stream Callback](https://console.tencentcloud.com/live/config/callback) on the left sidebar.
2. Select the successfully created callback template, click **Delete** in the upper part.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8eff41047d9f11f09a9a5254001c06ec.png)

3. Confirm it if you wish to delete the callback template, click **Confirm** to delete successfully.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ac9a0c2c7d9f11f0bd33525400454e06.png)

## Related Operations

You can also unbind and bind domains and callback templates on the Domain Management page. For details, see [Callback Configuration](https://www.tencentcloud.com/document/product/267/31065?lang=en&pg=).


---
*Source: [https://www.tencentcloud.com/document/product/267/31074](https://www.tencentcloud.com/document/product/267/31074)*
