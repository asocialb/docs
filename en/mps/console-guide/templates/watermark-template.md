# Watermark Template

## Overview

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4c190dbec9b011f087ad52540099c741.png)

Media Processing Service (MPS) supports the following types of watermarks:

| Type | Introduction |
| --- | --- |
| Digital watermark | Enables the embedding of custom text information invisible to the naked eye into videos without affecting the visual quality and integrity. Both basic digital watermark and NAGRA NexGuard digital watermark are supported. |
| Visible watermark | Supports adding images with specified formats, such as PNG and JPG, or custom text to videos in a visible form. This solution is suitable for scenarios such as copyright protection and brand promotion. |

This document primarily introduces the configuration parameters for watermark templates. For comprehensive guidance on initiating watermark tasks and detailed functional integration, please refer to [Digital Watermark and Visible Watermark Integration](https://www.tencentcloud.com/document/product/1041/74443).

## Digital Watermark Template

MPS digital watermark supports two versions: basic copyright watermark and NAGRA NexGuard forensics watermark.

| Version | Introduction |
| --- | --- |
| Basic copyright watermark | Basic version: embeds invisible text information into videos without affecting the visual quality and integrity. |
| NAGRA NexGuard forensics watermark | NAGRA NexGuard is a leading digital watermark solution worldwide, featuring strong concealment and possessing broadcasting-grade anti-removal capabilities. It is tailored for piracy tracking and copyright protection of high-value content, such as movies and dramas. |

1. Log in to the MPS console and go to the [watermark template](https://console.tencentcloud.com/mps/templates/watermarks?tab=implicitWatermark) page.
2. Click Create Watermark Template, select a watermark type, and enter the template name and watermark content to create a digital watermark template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a0646183c9b011f087ad52540099c741.png)

> **Note:**Each user can create up to 50 NexGuard forensics watermark templates. Once created, modification or deletion by users is not supported. To modify or delete templates, contact us for processing in the background.

## Visible Watermark Template

1. Navigate to the MPS console > [Watermark Templates](https://console.tencentcloud.com/mps/templates/watermarks) page.
2. Click **Create Visible Watermark Template**, which supports the following configurations:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d8bc21e5c9b011f09e745254007c27c5.png)

| Configuration Item |  | Description |
| --- | --- | --- |
| Template Name | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods |
| Watermark type |  | Supports both image watermark and text watermark. |
| For "image watermark" | Image | PNG or JPG images. For better visual experience, transparent images in PNG format are recommended. The image cannot exceed 200 KB in size or 200 × 200 px in dimensions. |
| For "text watermark" | Watermark Content | Only alphanumeric characters and standard English symbols are permitted; the percent sign (%) is not supported, and the maximum length must not exceed 100 characters. |
|  | Font | Supports `simkai.ttf` and `arial.ttf`. For additional font requirements, please contact our support team. |
|  | Font Size | The font size range is [0,1] or [8,4096]. |
|  | Color | Color of the watermark content. |
|  | Transparency | Transparency level of the watermark content, where 0% indicates complete transparency and 100% represents full opacity. |
| Reference position | Upper left (default), upper right, lower left, or lower right, based on which you can change the position of the watermark image by adjusting the vertical and horizontal offset | Upper left (default), upper right, lower left, or lower right, based on which you can change the position of the watermark image by adjusting the vertical and horizontal offset |
| Vertical offset | The percentage represents the ratio of the vertical distance between the watermark and reference position to the height of the video, which is used to specify the vertical position of the watermark. | The percentage represents the ratio of the vertical distance between the watermark and reference position to the height of the video, which is used to specify the vertical position of the watermark. |
| Horizontal offset | The percentage represents the ratio of the horizontal distance between the watermark and reference position to the width of the video, which is used to specify the horizontal position of the watermark. | The percentage represents the ratio of the horizontal distance between the watermark and reference position to the width of the video, which is used to specify the horizontal position of the watermark. |
| Image dimensions | You can choose to resize the watermark by percentage (%) or pixel (px). | You can choose to resize the watermark by percentage (%) or pixel (px). |

3. The templates created can be found in the watermark template list, which displays watermark previews and information including template name, format, type, reference position, dimensions, etc. You can also view the details of, edit, or delete a template on this page.


---
*Source: [https://www.tencentcloud.com/document/product/1041/48785](https://www.tencentcloud.com/document/product/1041/48785)*
