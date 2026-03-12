# Live Screencapture

Cloud Streaming Services (CSS) provides a screenshot feature, supporting the use of screenshot templates configured through the console. After the template is associated with the push domain name, it captures the live streaming screen during the push process and stores the live screenshot data in Tencent Cloud Object Storage (COS). If the push domain name is already associated with a callback configuration, Tencent Cloud will send a request to the customer's server during the live streaming when a callback event is triggered, and the customer's server is responsible for responding to the request. After verification, the customer can obtain a JSON packet containing the screenshot callback information.
This document describes how to create, bind, unbind, modify, and delete screenshot templates through the console.

There are two ways to create a screenshot template:

- To create a template via the CSS console, for specific operation steps, see [Creating a Screenshot Template](https://www.tencentcloud.com/document/product/267/31072#.E5.88.9B.E5.BB.BA.E6.88.AA.E5.9B.BE.E9.89.B4.E9.BB.84.E6.A8.A1.E6.9D.BF).
- Call the CreateLiveSnapshotTemplate API to create a template. For information on the parameters and request sample, see [CreateLiveSnapshotTemplate](https://intl.cloud.tencent.com/document/product/267/30834).

## Must-Knows

- The screenshot feature can be used independently, but the porn detection feature can only be enabled after the screenshot feature is enabled and cannot be used independently. Live stream porn detection has been fully upgraded to live stream moderation, which no longer relies on the live screenshot capability. For a better product experience, it is recommended to use the live stream moderation feature. For details, see [Live Stream Moderation](https://www.tencentcloud.com/document/product/267/58265).
- The screencapture and porn detection features are priced at 0.0176 USD and 0.2294 USD per 1,000 screenshots respectively. For details, see [Intelligent Porn Detection](https://intl.cloud.tencent.com/document/product/267/39607).
- The screenshots and porn detection results are stored in your COS bucket, which will incur COS storage fees. For more information, see [COS Pricing](https://intl.cloud.tencent.com/pricing/cos).
- Screencapturing will fail for audio-only streams, in which case no screencapturing costs will be incurred.
- If you want to store the data in a COS bucket of **another account**, you need to first grant CSS the permission to write to that COS bucket. For more information, see [Authorizing CSS to Store Screenshots in a COS Bucket](https://intl.cloud.tencent.com/document/product/267/33384).
- If your COS bucket allows public read access and has politically sensitive, pornographic, or other inappropriate content, to avoid the bucket being blocked, please delete the content first.
- After creating a template, you need to bind it to a push domain. For more information, see [Screencapture and Porn Detection Configuration](https://www.tencentcloud.com/document/product/267/31063). The configuration takes effect in about 5-10 minutes.
- The screenshot template management in the console is at the domain name level and currently, it is not possible to cancel the rules created via API. For screenshot rules bound to specific streams by an API, you need to call [DeleteLiveSnapshotRule](https://intl.cloud.tencent.com/document/product/267/30833) to unbind them.
- Binding, unbinding, or modifying a template affects only new live streams but not ongoing ones. To apply new rules to ongoing streams, you need to stop them and push them again.

## Prerequisites

- You have activated CSS and added a [push domain](https://intl.cloud.tencent.com/document/product/267/35970).
- You have created a COS bucket. For detailed directions, see [Creating Bucket](https://www.tencentcloud.com/document/product/436/13309).

## Creating a Screenshot Template

1. Log in to the CSS console, and choose **Feature Configuration**  > [Live Screencapture](https://console.tencentcloud.com/live/config/jtjh).

> **Note:**Because the CSS screenshot service needs to store screenshots in COS buckets, when creating a screenshot template for  **the first time** , you need to create a service role and authorize CSS to have read and write permissions for COS.

2. Click  **Create template** .
3. The console will pop up a window to request resource authorization. Click  **Authorize Now**  to enter the Role Management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d0194f3a2a2211ef97da5254007d9c55.png)

4. On the Role Management page, click  **Grant** . After identity verification is completed, you can complete the COS resource authorization and use the live screenshot service normally. Upon successful authorization, you will be redirected to the page for creating screenshot templates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d970fc192a2211ef918f52540005b090.png)

5. Click  **Create template**  to go to the screenshot template creation page and proceed with the following configuration:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/70ddb76fc50e11f0a7ca5254001c06ec.png)

| Configuration Item |  | Required | Description |
| --- | --- | --- | --- |
| Template Name |  | Yes | The name of the screencapture and porn detection template, which can contain up to 30 Chinese characters, letters, numbers, underscores (_), and hyphens (-). |
| Template Description |  | No | Description of the screenshot template, which can contain up to 100 Chinese characters, letters, digits, spaces, underscores (_), and hyphens (-). |
| Screencapture Interval |  | Yes | The screencapture interval, which is 2 seconds by default. Value range: 2-300 seconds. |
| Video Resolution |  | Yes | By default, the original resolution is maintained, but you have the option to set the screenshot height.The input height range is from 1 px to 2,000 px, and the other side will automatically scale in proportion to the resolution by default. |
| Intelligent Porn Detection |  | No | The intelligent porn detection feature is disabled by default and can be enabled manually.After enabling intelligent porn detection, you must configure a callback to receive the results. |
| COS Account |  | Yes | **Current Account** or **Other Account.** |
| AppId |  | Yes | This is required only if you select **Other Account**. You can view the `APPID` of an account on the [Account Information](https://console.tencentcloud.com/developer) page of the console. To save data to a COS bucket of another account, you need to first grant CSS read and write access to that bucket. For details, see [Authorizing CSS to Store Screenshots in a COS Bucket](https://www.tencentcloud.com/en/document/product/267/33384#authorizing-css-to-store-screenshots-in-cos). |
| Storage Path | Bucket | Yes | You can select a COS bucket in Bucket, which you have already created and authorized in  **COS** . |
|  | Region | Yes | The region corresponds to the regional information of the aforementioned bucket and cannot be modified. |
|  | Folder | No | Click the box to choose a COS folder. The default is: {Year}-{Month}-{Day}/. Note: COS folder names can only contain [a-z, A-Z, 0-9] and the symbols -, !, _, ., * as well as placeholders. |
| Backup Storage Path |  | No | The backup storage path feature is disabled by default. You can manually enable this feature based on your business needs.When network jitter prevents the screenshot from being stored in the primary storage path, the system will automatically store the file to the backup storage path to prevent file loss. Once the primary storage path is restored, screenshots under the backup storage path will be automatically synchronized to the primary storage path. Primary and backup storage paths should be in different regions. |
| File Name |  | No | The format of screenshot filenames. You can customize your own format. The default is `{StreamID}-screenshot-{Hour}-{Minute}-{Second}-{Width}x{Height}{Ext}`:{AppName}: The push app name.{PushDomain}: The push domain.{StreamID}: The stream ID.{Year}: The screenshot time (year).{Month}: The screenshot time (month).{Day}: The screenshot time (day).{Hour}: The screenshot time (hour).{Minute}: The screenshot time (minute).{Second}: screenshot time (second){Width}: The width of the screenshot.{Height}: The height of the screenshot.{Ext}: The extension (.jpg).**Note:** The filename can contain only letters, digits, placeholders, and symbols (-, !, _, ., *).**Example:** If the filename format is  `{Year}-{Month}-{Day}- {Hour}-{Ext}`, a screenshot captured at 14:00:00 on January 1, 2020 would be named `2020010114.jpg` in COS. |

6. Click  **Save**  to save the current template.

## Binding a Domain Name

1. Log in to the CSS console, and choose **Feature Configuration**  > [Live Screencapture](https://console.tencentcloud.com/live/config/jtjh).
2. Bind a domain name in either of two ways:
  - **Bind a domain to an existing template**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1ab0f825c50f11f085c7525400454e06.png)

  - **Bind a domain name after successfully creating a screenshot template: After successfully** [Creating a Screenshot Template](#.E5.88.9B.E5.BB.BA.E6.88.AA.E5.9B.BE.E9.89.B4.E9.BB.84.E6.A8.A1.E6.9D.BF), click  **Bind Domain Name** in the reminder box .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d1b1f99dc50e11f0a7ca5254001c06ec.png)

3. In the domain binding window, select the  **screenshot template**  and  **push domain name** （Multiple push domain names can be bound simultaneously） you need to bind, and then click  **Confirm** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ea79e32dc50e11f0a1dc52540044a08e.png)

## Unbinding a Domain Name

1. Log in to the CSS console, and choose  **Feature Configuration**  > [Live Screencapture](https://console.tencentcloud.com/live/config/jtjh).
2. Select the target screencapture and porn detection template, find the domain you want to unbind, and click **Unbind**.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/203bc9f52a2311efa4f552540077de32.png)
3. In the pop-up window, click **Confirm**.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/248007932a2311efb8c45254005a8b94.png)

## Modifying a Template

1. Log in to the CSS console, and choose  **Feature Configuration**  > [Live Screencapture](https://console.tencentcloud.com/live/config/jtjh).
2. Select a screencapture and porn detection template, click **Edit** on the right, and modify its information.
3. Click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0ebe9926df7c11eea462525400bb593a.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2abd65162a2311ef9130525400bf8054.png)

## Deleting a Template

> **Note:**If a template has been bound to domains, you need to [unbind](#unbinding-a-domain-name) them before you can delete the template.Note that once a template is deleted, it cannot be recovered. Proceed with caution.

1. Log in to the CSS console, and choose  **Feature Configuration**  > [Live Screencapture](https://console.tencentcloud.com/live/config/jtjh).
2. Select the screenshot template you have successfully created and click  **Delete**  above.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/30d29f6b2a2311ef9bb3525400ab9413.png)

3. Confirm that you want to delete the current screenshot template, and click  **Confirm**  to delete it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/38461bed2a2311ef918f52540005b090.png)

## More

For specific operations and related instructions on **binding and unbinding screenshot templates at the domain name level**, refer to [Screenshot Configuration](https://intl.cloud.tencent.com/document/product/267/31063).


---
*Source: [https://www.tencentcloud.com/document/product/267/31072](https://www.tencentcloud.com/document/product/267/31072)*
