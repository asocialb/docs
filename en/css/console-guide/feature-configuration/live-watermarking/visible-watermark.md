# Visible Watermark

Visible watermarks are achieved by overlaying visible markings (such as images, text, or icons) onto content such as images, text, or videos. They are primarily used to declare copyright, identify sources, or conduct brand promotion, and can intuitively display the ownership information of the content.

In video applications, visible watermarks can effectively enhance brand recognition and provide some copyright warning functionality. However, visible watermarks have relatively low security and are primarily used for identification and promotion, with limited capabilities in preventing data leaks and tracing origins. As a visible layer, visible watermarks are easily cropped, covered, or removed through image processing by third-party tools. For critical scenarios, it is recommended to use them in conjunction with [Invisible Watermark（Digital watermark）](https://www.tencentcloud.com/document/product/267/74854).

CSS supports the watermark feature. It adds watermarks to the live streaming screen to protect video content from theft. This document describes how to create, modify, bind, unbind, and delete a watermark template in the console.

**You can create a watermark template in the following ways:**

- Create a watermark template in the CSS console. For more information, please see [Creating Visible Watermark Template](#Watermark).
- Create a watermark template by calling an API. For more information, please see [AddLiveWatermark](https://www.tencentcloud.com/document/product/267/30826).

## Notes

- After creating a template, you can bind it to a push domain name. The binding will take effect in 5–10 minutes.
- Binding, unbinding, and modifying a template affect only new live streams after the update but not ongoing ones. To make the new rule take effect for ongoing live streams, you need to interrupt them and push them again.
- The visible watermark feature is a paid value-added service. Using the visible watermark service during push generates a transcoding bill. For billing rules, see [Billing Documentation](https://www.tencentcloud.com/document/product/267/39604)

## Prerequisites

You have activated the CSS service and added a [push domain name](https://www.tencentcloud.com/document/product/267/35970).

## Creating Visible Watermark Template

1. Log in to the CSS console and select **Feature Configuration** > [Live Watermarking](https://console.tencentcloud.com/live/config/watermark). Access the Live Streaming Copyright Protection page.
2. Select **Visible Watermark** and click **Create Template** to access the **Visible Watermark** template creation page, then proceed with the following configurations:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b85e1b71d04711f093295254001c06ec.png)

| Configuration Item | Configuration description |
| --- | --- |
| Watermark Name | Enter a watermark name, customizable, Max 30 characters; supports letters, digits, underscores, and dashes |
| Image Upload | Click **Select Image** to upload a watermark image. The size of the watermark image supports stretching to full window dimensions.**Note:**For a better visual experience, we recommend you use a transparent PNG image not larger than 2 MB. The filename of the image can only contain letters, numbers, and special characters - ! _ . * |
| Preview window size | Set the watermark image preview window size:Default width and height values: Width 1920px, Height 1080px.Width and height value range: 360px - 4096px.Clicking **Update** on the right side will automatically validate and synchronize the update of the watermark image preview window. |
| X-axis | Specify the watermark location in the following ways:Drag the watermark image in the configuration pane.Adjust the coordinates of the X axis and Y axis. |
| Y-axis |  |

3. Click **Save**.

## Binding Domain Name

1. Log in to the CSS console and select **Feature Configuration** > **Live Watermarking** > [Visible Watermark](https://console.tencentcloud.com/live/config/watermark/light).
2. Enter the domain name binding page in either of the following ways:
  - **Directly bind a domain name**: click **Bind Domain Name** in the top-left corner.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a038408fd04a11f0b638525400e889b2.png)

  - **Bind a domain name after creating the visible watermark template**: after the [visible watermark template is created](#Watermark), click **Bind Domain Name** in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/280c4c7dd04a11f08823525400454e06.png)

3. In the pop-up window, select a **visible watermark template**and a **push domain name** (Multiple push domain names can be bound simultaneously)  in the domain name binding window and then click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4fd6b01dd04a11f093295254001c06ec.png)

## Unbinding

1. Log in to the CSS console and select **Feature Configuration** > **Live Watermarking**> [Visible Watermark](https://console.tencentcloud.com/live/config/watermark/light).
2. Select domain names bound to the visible watermark template and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cfaef019d04c11f08e5c52540044a08e.png)

3. Confirm whether to unbind the domain name and click **Confirm** to unbind it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1c762995d04d11f0a808525400bf7822.png)

## Modifying Template

1. Log in to the CSS console and select **Feature Configuration** > **Live Watermarking**> [Visible Watermark](https://console.tencentcloud.com/live/config/watermark/light).
2. Select the target visible watermark template and click **Edit** on the right to modify the template information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/76559202d0ec11f08e5c52540044a08e.png)

3. Click **Save**.

> **Note:**You can click **Preview** to view how the visible watermark will be displayed on the screen.

## Deleting Template

> **Note:**If the template is already associated, you need to [Unbind](#unbinding) it first before you can perform the delete operation.Once the template is deleted, it cannot be recovered. Please proceed with caution.

1. Log in to the CSS console and select **Feature Configuration** > **Live Watermarking**> [Visible Watermark](https://console.tencentcloud.com/live/config/watermark/light).
2. Select the visible watermark template you have successfully created, and click **Delete** in the upper right corner.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e4fd38fbd04d11f093295254001c06ec.png)

3. In the pop-up dialog box, click **Confirm** to confirm the deletion.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f0af1823d04d11f093295254001c06ec.png)

## Relevant Operations

For more information on how to **bind/unbind** a **domain name** to/from a visible watermark template, please see [Visible Watermark Configuration](https://www.tencentcloud.com/document/product/267/31064).


---
*Source: [https://www.tencentcloud.com/document/product/267/31073](https://www.tencentcloud.com/document/product/267/31073)*
