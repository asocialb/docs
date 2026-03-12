# Moderation Templates

CSS offers a live stream moderation feature. You can configure moderation templates in the console. Once the streaming domain is associated with the template, this service will obtain live screenshots and the audio during streaming, storing any non-compliant screenshots or audio data in Tencent Cloud COS. If the streaming domain is linked to the callback configuration, Tencent Cloud will send a request to the customer's server once a callback event is triggered during the live stream. Customer's server is responsible for handling the request. After verification, a JSON packet containing the moderation callback information can be obtained. This document provides instructions on how to create, bind, unbind, modify, and delete moderation configuration templates via the console.

## Notes

- Live stream moderation is a paid feature. Image moderation is charged 0.2294 USD per thousand images, while audio moderation is charged 0.0021 USD per minute. For more information, please refer to [Live Stream Moderation](https://www.tencentcloud.com/document/product/267/58267).For more information, see Value-Added Services - Live Stream Moderation.
- Screenshots or audio flagged during live stream moderation are stored in Tencent Cloud COS, which will generate storage costs. For pricing details, please refer to [COS Product Pricing](https://intl.cloud.tencent.com/pricing/cos).
- If your COS bucket allows public read access and has politically sensitive, pornographic, or other inappropriate content, to avoid the bucket being blocked, please delete the content first.
- After a template is created, it can be bound with a push domain. For more information, see Live Stream Moderation Configuration. The association of the template is usually effective within 5-10 minutes.
- Binding, modifying, or unbinding a template only affects new live streams and not ongoing ones. To apply new rules to ongoing live streams, you need to stop them and push them again.
- To use a custom keyword library for image recognition, make sure "OCR" of "Image recognition" is selected. When OCR is on, the system will moderate the text in video screenshots. OCR-based moderation detects all non-compliant content regardless of the recognition policy configured.
- Smart moderation can be performed on the live stream image, audio, and text content. Users can customize moderation policies and flexibly configure identification dimensions to ensure live streaming content compliance.

## Prerequisites

- You have activated the Tencent CSS service and added a [push domain](https://www.tencentcloud.com/document/product/267/35970).
- You have created a COS bucket. For more details, see [Creating a Bucket](https://www.tencentcloud.com/document/product/436/13309?lang=zh&pg=).

## Creating Live Stream Moderation Templates

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and choose **Feature Configuration** >**Content moderation** from the left navigation bar.

> **Note:**CSS stores video screenshots and audio data in COS buckets. Therefore, if it's your first time creating a moderation template, you need to create a service role and grant CSS read and write access to COS.

2. Click **Create template**.
3. A pop-up window will appear for you to grant CSS authorization to access COS resources. Click **Authorize Now** to go to the **Role Management** page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4baf6c3194d111eeb6c6525400e46040.png)

4. On the **Role Management** page, click **Grant**. After authentication, CSS will have access to COS resources, and you can start using the live stream moderation feature.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4b81ca5294d111eeb6c6525400e46040.png)

5. After authorization, you will be redirected to the Create template page, where you can fill in the configuration items.

## Steps

### Step 1: Configuring Moderation

Click **Create template** to configure moderation:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a13529a2c50f11f099d952540099c741.png)

| Configuration Item | Description |
| --- | --- |
| Template Name | The template name can include up to 30 Chinese characters, letters, digits, underscores (_), and hyphens (-). |
| Template Description | The template description can include up to 100 Chinese characters, letters, digits, spaces, underscores (_), and hyphens (-). |

### Step 2: Configuring Screencapture/Segment Policy

In Screencapture/Segment policy, you can configure what content you want to moderate.

| Configuration Item | Required Item | Description |
| --- | --- | --- |
| Content type to moderate | Yes | Screenshot imagesScreencapture interval: The interval at which screenshots are taken during a live stream. The shorter the interval, the finer the moderation granularity, and the higher the cost.The screencapture interval can be 2-300 seconds. The default value is 2 seconds.AudioThe audio moderation feature only supports Chinese audio.Audio segment duration refers to the length of each audio segment extracted from a live stream. It determines the duration of the non-compliant audio segments returned and does not affect billing.The audio segment duration can be 15-60 seconds. The default value is 15 seconds.Audio text recognitionAudio text recognition is only used for features such as [smart erase](https://console.tencentcloud.com/live/config/examine/erasure) but will not trigger review.The Smart Erase feature utilizes its configured policies to identify and eliminate audio content that violates regulations. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8db247423b6f11f09bbe525400454e06.png)

### Step 3: Configuring Recognition Policy

1. On the recognition policy configuration page, you can configure policies for both **Image Recognition** and **Audio Recognition**.
2. You can expand each category of **Image Recognition** and **Audio Recognition** to select sub-categories for moderation.

> **Note:**The system will recognize and perform moderation on the content according to the categories you select. If no categories are selected, no recognition or moderation will be performed.To use a custom keyword library for image recognition, make sure "OCR" of "Image recognition" is selected.

Image Recognition Configuration

Audio Recognition Configuration

Audio text recognition configuration

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4f71d35c3b7011f0aa9f5254001c06ec.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6bdaa6b53b7011f0aa9f5254001c06ec.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/226bebbd3b7011f0b95f5254005ef0f7.png)

3. From the drop-down list of custom keyword libraries, you can select a custom library to use for image recognition or audio recognition.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd06a8903b7011f0b0ce5254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c9a67b2b3b7011f0aed2525400e889b2.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/acc1db973b7011f0b0ce5254007c27c5.png)

> **Note:**If you need to use a custom keyword library for content recognition, you need to configure one in the console first. For more information, see Custom Keyword Libraries.

4. Configure the storage path for saving screenshots or audio for moderation. Then, click **Save** to save the moderation template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0ff89aa23b7111f0b0ce5254007c27c5.png)

| Configuration Item | Required Item | Description |
| --- | --- | --- |
| Storage Location | _ | The screenshot will be stored in your configured COS bucket, and make sure that the COS bucket has authorized CSS write request. Please create a COS bucket and authorize, [reference documentation](https://www.tencentcloud.com/document/product/267/31316). |
| Storage path | Yes | Choose a COS bucket that you have created and authorized in COS.Region refers to the geographic information of the selected bucket, which cannot be edited. |
| Backup storage path | No | Backup storage is supported. If the primary bucket does not work properly, the moderation content will be automatically stored in the backup bucket. The backup bucket will be used only if the primary bucket is down, and only one copy of data will be stored. The primary Region and backup Region cannot be identical. |
| Folder | Yes | Click the input box to select a COS folder. The default is`/Audit/{Year}-{Month}-{Day}/`. Note: COS folder names only allow `[a-z, A-Z, 0-9]` characters and the symbols `-,!, _,., *` along with placeholders. |
| File Name | Yes | The file name format can be customized through parameter assembly. Default is:{StreamID}-Audit-{Hour}-{Minute}-{Second}{Ext}, wherein:{StreamID}: Stream ID {Audit}: Moderation{Hour}: Moderation time (Hour){Minute}: Moderation time (Minute){Second}: Moderation time (Second){Ext}: Extension (.jpg)Note: It only accepts [a-z, A-Z, 0-9], symbols `-,!,_,.,*`, and placeholders.For example, if you enter the file format as {Hour}-{Minute}-{Second}-{Ext}, a screenshot taken during a live stream at 14:00:00 will be stored in COS with the filename `140000.jpg`. |

## Binding Domain Names

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and choose **Feature Configuration** > **Content moderation** from the left navigation bar.
2. You can bind the moderation template to a push domain with the following methods:
  - **Directly bind a domain**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8a5bdd57c51011f0a62b5254007c27c5.png)

  - **Bind a domain after creating a new moderation template**: After successfully creating a moderation template, click **Bind Domain Name** in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/56ef03cbc51011f099d952540099c741.png)

3. In the Bind Domain Name window, select the **moderation template**and **push domain** **name**（Multiple push domain names can be bound simultaneously） you want to bind together, and click **Confirm** to bind them.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/69e02cb1c51011f0a2c65254005ef0f7.png)

## Unbinding

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and choose **Feature Configuration** > **Content moderation** from the left navigation bar.
2. Select the live stream moderation template from which you want to unbind the push domain and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/536bd68b3b7511f0be2052540099c741.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4b72981394d111eebd87525400c40977.png)

## Modifying a Template

1. From the left navigation bar, choose **Feature Configuration** > **Content moderation**.
2. Select the successfully created moderation template, click **Edit** on the right to go to modify the template information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bc87536e3b7511f0b95f5254005ef0f7.png)

## Deleting a Template

> **Note:**If the template is already bound to a push domain, you must first [unbind](https://www.tencentcloud.com/document/product/267/58265#fc56529b-3f7e-4bf8-90b5-8ee8eca29e5d) it before the template can be deleted.A deleted template cannot be recovered. Proceed with caution when deleting templates.

1. From the left navigation bar, choose **Feature Configuration** > **Content moderation**.
2. Select a previously created moderation template and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/efd4a1383b7511f0912c52540044a08e.png)

3. Click **Confirm** to permanently delete the template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4f822aa23c6611f0aa9f5254001c06ec.png)

## Related Operations

For detailed instructions and additional information on binding and unbinding moderation templates at the domain level, please refer to [Moderation Configuration](https://www.tencentcloud.com/document/product/267/58266).


---
*Source: [https://www.tencentcloud.com/document/product/267/58265](https://www.tencentcloud.com/document/product/267/58265)*
