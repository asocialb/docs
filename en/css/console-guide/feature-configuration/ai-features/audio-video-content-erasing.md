# Audio-Video Content Erasing

Audio-video content erasing—Live stream moderation 2.0 can precisely identify non-compliant audio content and privacy-related images, such as faces and license plates, during live streaming and then automatically execute real-time erasing. This achieves full-process automated content risk control and management and guarantees content security and compliance of live streaming platforms.

This document describes how to create, modify, and delete Audio-video content erasin templates through the console.

## Notes

- After a template is created, it can be bound with a push domain. For more information, see [Audio-Video Content Erasing Configuration](https://www.tencentcloud.com/document/product/267/70285). The association of the template is usually effective within 5-10 minutes.
- Binding, modifying, or unbinding a template only affects new live streams and not ongoing ones. To apply new rules to ongoing live streams, you need to stop them and push them again.
- Audio-Video Content Erasing—Live stream moderation 2.0 can precisely identify non-compliant audio content during live streaming and automatically execute real-time muting. This achieves full-process automated content risk control and management and guarantees content security and compliance of live streaming platforms.
- The Audio-video content erasin feature is a paid value-added service. Using this feature during live streaming will incur value-added fees and intelligent identification fees for MPS. For billing rules, see [Live Stream Moderation](https://www.tencentcloud.com/document/product/267/58267).
- When Smart Erasing and the subtitle function are used simultaneously, they cannot both be active at the same time (only audio erasing can be synchronized with subtitles). If the user template is configured with both image erasing and audio erasing, and the subtitle function is enabled, only subtitles and audio erasing will be effective.

## Prerequisites for Use

The CSS service has been activated.

## Creating Audio-Video Content Erasing Template

1. Log in to the [CSS console](https://console.tencentcloud.com/live/config/examine/erasure). Choose **Feature Configuration**> **AI Features**> **Audio-Video Content Erasing.**

> **Note:**To use **Audio-Video Content Erasing** in the **AI ​​Features**, you need to create a service role and authorize the current account role to use the **Media Processing Service**(MPS) and **Cloud Object Storage** (COS) products on first creation.

2. Click **Authorize** to enter the CAM role management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b4efd5d2c9da11f08942525400e889b2.png)

3. On the role management page, click **Authorize**. After completing identity verification, you can authorize Media Processing Service and Cloud Object Storage (COS) and use the Media Processing Service and Cloud Object Storage services normally.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d5d7d47700b511f18e41525400ecee81.png)

4. After successful authorization, select the service agreement and click **Start**. The system will automatically activate the Media Processing Service product and Cloud Object Storage (COS), and will redirect you to the  Intelligent Summary management page.
5. Click **Create template** to enter the Audio-video content erasin template creation page and configure the template as follows:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/79126a9c00ca11f1a1eb52540073fd3b.png)

| Configuration Item |  | Description |
| --- | --- | --- |
| Template Name |  | Max 30 characters; supports letters, digits, underscores, and dashes. |
| Template Description |  | Max 100 characters; supports Chinese characters, letters, digits, spaces, _ and  -. |
|   Recognition Scheme | Erasing Type | Non-compliant audio, Recognize non-compliant text content in the live streaming audio and mute the corresponding audio segments to effectively guarantee live streaming content security.The development of erasure types for non-compliant images, logos, and privacy protection content is currently underway. Please stay tuned. |
|  | Non-compliant Audio Recognition Scheme | Bind a template in the live stream moderation module with Audio text recognition selected for Moderation Content Configuration.You can configure the inappropriate text content you wish to erase in the form of a custom vocabulary within the [Audio Text Recognition policy](https://www.tencentcloud.com/document/product/267/58265#084db3fe-6220-4f02-8a0e-702efbc95940). |
| Output Information |  | Output Content is Audio after erasing |

## Binding Domain Names

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Choose **Feature Configuration**> **AI Feature**> **Audio-Video Content Erasing**.
2. You can bind the moderation template to a push domain with the following methods:
  - **Directly bind a domain**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e4a107f500ca11f183755254001d6acc.png)

  - **Bind a domain after creating a new Audio-video content erasin template**: After successfully creating a Audio-video content erasin template, click **Bind** **Domain Name** in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b3ce377400ca11f18080525400074c32.png)

3. In the Bind Domain Name window, select the**Audio-video content erasin template** and **push domain name**（Multiple push domain names can be bound simultaneously） you want to bind together, and click **Confirm** to bind them.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/001edc4500cb11f1a616525400a31896.png)

## Unbinding

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Choose **Feature Configuration**> **AI Feature**> **Audio-Video Content Erasing**.
2. Select the Audio-video content erasin template from which you want to unbind the push domain and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/18d270f600cb11f18080525400074c32.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e38fbaecef6311f0a94d52540073fd3b.png)

## Modifying a Template

1. From the left navigation bar, Choose **Feature Configuration**> **AI Features**> **Audio-Video Content Erasing.**
2. Select the successfully created Audio-video content erasin template, click **Edit**on the right to go to modify the template information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5833cd8d00cb11f198c8525400370dda.png)

## Deleting a Template

> **Note:**If the template is already bound to a push domain, you must first [unbind](#cee4a59a-cba1-40f9-a4f5-1efecb3f35fe) it before the template can be deleted.A deleted template cannot be recovered. Proceed with caution when deleting templates.

1. From the left navigation bar, Choose**Feature Configuration**> **AI Feature**> **Audio-Video Content Erasing**.
2. Select a previously created Audio-video content erasin template and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6c08852200cb11f1a1eb52540073fd3b.png)

3. Click **Confirm** to permanently delete the template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b199d6b300cc11f18ab45254001d6acc.png)

## Related Operations

For detailed instructions and additional information on binding and unbinding Audio-Video Content Erasing templates at the domain level, please refer to [Audio-Video Content Erasing Configuration](https://www.tencentcloud.com/document/product/267/70285)**.**


---
*Source: [https://www.tencentcloud.com/document/product/267/76595](https://www.tencentcloud.com/document/product/267/76595)*
