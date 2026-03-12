# Smart Erasing

The Smart Erasing feature allows users to configure Smart Erase templates via the console. Once a Push Domain is linked to a template, it captures audio during streaming, identifies inappropriate content, and mutes it accordingly, ensuring a positive and well-maintained live streaming environment.

This document describes how to create, modify, and delete smart erase templates through the console.

## Notes

- After a template is created, it can be bound with a push domain. For more information, see [Smart Erase Configuration](https://www.tencentcloud.com/document/product/267/70285). The association of the template is usually effective within 5-10 minutes.
- Binding, modifying, or unbinding a template only affects new live streams and not ongoing ones. To apply new rules to ongoing live streams, you need to stop them and push them again.
- Smart Erase—Live stream moderation 2.0 can precisely identify non-compliant audio content during live streaming and automatically execute real-time muting. This achieves full-process automated content risk control and management and guarantees content security and compliance of live streaming platforms.
- The smart erase feature is a paid value-added service. Using this feature during live streaming will incur value-added fees and intelligent identification fees for MPS. For billing rules, see [Live Stream Moderation](https://www.tencentcloud.com/document/product/267/58267).
- When Smart Erasing and the subtitle function are used simultaneously, they cannot both be active at the same time (only audio erasing can be synchronized with subtitles). If the user template is configured with both image erasing and audio erasing, and the subtitle function is enabled, only subtitles and audio erasing will be effective.

## Prerequisites for Use

The CSS service has been activated.

## Creating Smart Erase Template

1. Log in to the [CSS console](https://console.tencentcloud.com/live/config/examine/erasure). Choose **Feature Configuration** >**Content moderation** > **Smart Erasing.**

> **Note:**Due to the use of the smart erase function, creating a service role and authorizing the current account role to use MPS product services are required for the**first** creation of a smart erase template.

2. Click **Grant access** to enter the CAM role management page.
3. On the role management page, click **Grant**. After completing identity authentication to finish the MPS authorization, you can utilize the MPS service normally.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cdca529e3d0811f0912c52540044a08e.png)

4. After successful authorization, select the service agreement and click **Start**. The system will automatically activate the MPS product and open the Smart Erasing management page.
5. Click **Create template** to enter the smart erase template creation page and configure the template as follows:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c9f47fe7c51211f0a2c65254005ef0f7.png)

| Configuration Item |  | Description |
| --- | --- | --- |
| Template Name |  | Max 30 characters; supports letters, digits, underscores, and dashes. |
| Template Description |  | Max 100 characters; supports Chinese characters, letters, digits, spaces, and `_-`. |
|   Recognition Scheme | Erasing Type | Non-compliant audio，Recognize non-compliant text content in the live streaming audio and mute the corresponding audio segments to effectively guarantee live streaming content security.The development of erasure types for non-compliant images, logos, and privacy protection content is currently underway. Please stay tuned. |
|  | Non-compliant Audio Recognition Scheme | Bind a template in the live stream moderation module with Audio text recognition selected for Moderation Content Configuration.You can configure the inappropriate text content you wish to erase in the form of a custom vocabulary within the [Audio Text Recognition policy](https://www.tencentcloud.com/document/product/267/58265#084db3fe-6220-4f02-8a0e-702efbc95940). |
| Output Information |  | Output Content is Audio after erasing |

## Binding Domain Names

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and choose **Feature Configuration** > **Content moderation**> **Smart Erasing**from the left navigation bar.
2. You can bind the moderation template to a push domain with the following methods:
  - **Directly bind a domain**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/743a17c7c51311f0b88b525400bf7822.png)

  - **Bind a domain after creating a new smart erase template**: After successfully creating a smart erase template, click **Bind** **Domain Name** in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f4e46ca7c51211f0a62b5254007c27c5.png)

3. In the Bind Domain Name window, select the **smart erase template** and **push domain name**（Multiple push domain names can be bound simultaneously） you want to bind together, and click **Confirm** to bind them.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5ba2cee2c51311f0a7ca5254001c06ec.png)

## Unbinding

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and choose **Feature Configuration** > **Content moderation**> **Smart Erasing** from the left navigation bar.
2. Select the smart erase template from which you want to unbind the push domain and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3580d1d13b6c11f08806525400bf7822.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4318986e3b6c11f0be2052540099c741.png)

## Modifying a Template

1. From the left navigation bar, choose **Feature Configuration** > **Content moderation>Smart Erasing**.
2. Select the successfully created smart erase template, click **Edit**on the right to go to modify the template information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5699afc03b6c11f0be2052540099c741.png)

## Deleting a Template

> **Note:**If the template is already bound to a push domain, you must first [unbind](https://www.tencentcloud.com/document/product/267/70286#cee4a59a-cba1-40f9-a4f5-1efecb3f35fe) it before the template can be deleted.A deleted template cannot be recovered. Proceed with caution when deleting templates.

1. From the left navigation bar, choose **Feature Configuration** > **Content moderation**> **Smart Erasing**.
2. Select a previously created smart erase template and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6f542ca53b6c11f0912c52540044a08e.png)

3. Click **Confirm** to permanently delete the template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e164060d476711f089d45254001c06ec.png)

## Related Operations

For detailed instructions and additional information on binding and unbinding Smart Erase templates at the domain level, please refer to [Smart Erase Configuration](https://www.tencentcloud.com/document/product/267/70285)**.**


---
*Source: [https://www.tencentcloud.com/document/product/267/70286](https://www.tencentcloud.com/document/product/267/70286)*
