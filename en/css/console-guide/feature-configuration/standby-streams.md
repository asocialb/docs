# Standby Streams

This document shows you how to create, bind, unbind, modify, and delete a standby stream template. A standby stream shows a video or image that becomes active automatically when your live stream is interrupted, helping you improve viewing experience. Once the original stream is recovered, CSS will switch back.

## Notes

- After creating a template, you need to bind it to a push domain. The configuration takes effect 5-10 minutes after binding.
- Binding, unbinding, or modifying a template affects only new live streams and not ongoing ones. To make the change apply to ongoing live streams, you need to stop them and push them again.
- You can create up to **50** standby stream templates.
- The standby stream feature cannot differentiate between normal stream interruption and abnormal stream interruption. When the stream is interrupted, the standby stream service is triggered by the system.

## Prerequisites

You have activated CSS and added a [push domain](https://intl.cloud.tencent.com/document/product/267/35970).

## Creating a Standby Stream Template

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Select **Feature Configuration > Standby Streams** on the left sidebar.
2. Click **Create template**.
3. Enter a template name, which can be up to 30 characters long and can contain Chinese characters, letters, numbers, underscores (_), and hyphens (-).
4. Fill in the template description, which only supports Chinese, English, numbers, spaces, underscores, and hyphens, not exceeding 1024 bytes (Note: Chinese characters are counted as 3 bytes each).
5. Select the stream type, which can be image or video.
  - You can choose to upload images in JPG or PNG format, with a file size less than 5MB. The uploaded image file names only support: English, numbers, and the symbols` - ! _ . *`
  - You can enter a video URL, which supports FLV and MP4 format audio and video files. The required audio encoding format is AAC.
6. Set the stream interruption waiting time (the waiting duration after the stream interruption before playing the standby content) to a value between 0 and 6 seconds.
7. Set the maximum standby content duration, with a default value of 120 seconds. This is the maximum playback duration for the standby content. If the standby content is shorter than this duration, it will be looped. The value cannot be greater than 1,000,000.
8. Click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c2ddf1f4c51711f099d952540099c741.png)

## Binding a Domain Name

2. You can bind a domain to a template in one of two ways:
  - **Bind a domain to an existing template**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/223f4a1cc51811f0b88b525400bf7822.png)

  - **Bind a domain after creating a template**: After creating a standby stream template, click **Bind Domain Name** in the dialog box that pops up.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e1929c83c51711f086d9525400e889b2.png)

3. In the pop-up window, select a **standby stream template** and a **push domain name** （Multiple push domain names can be bound simultaneously） and then click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f64d9108c51711f0a2c65254005ef0f7.png)

## Unbinding a Domain Name

2. Select the target template and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9052b84f2a3011ef97da5254007d9c55.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9499a0c12a3011ef918f52540005b090.png)

## Modifying a Template

2. Select the target template and click **Edit** on the right to modify the template information.
3. After modification, click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9b1d68762a3011ef97da5254007d9c55.png)

## Deleting a Template

> **Note:**If the template is already associated, you need to [Unbind Template](https://www.tencentcloud.com/document/product/267/53400#unbinding-a-domain-name) before you can perform the delete operation.Once a template is deleted, it cannot be recovered. Please proceed with caution.

1. Go to **Feature Configuration** > [Standby Streams](https://console.tencentcloud.com/live/config/pad).
2. Select the template you want to delete and click **Delete** in the top right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a164416a2a3011ef918f52540005b090.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a553f33f2a3011ef9bb3525400ab9413.png)

## More

You can also **unbind** and **bind** domains and standby stream templates on the **Domain Management** page. For details, see [Standby Stream Configuration](https://intl.cloud.tencent.com/document/product/267/31064).


---
*Source: [https://www.tencentcloud.com/document/product/267/53400](https://www.tencentcloud.com/document/product/267/53400)*
