# Live Quality Control and Live Assessment Template

## Overview

CSS offers**Live Quality Control** and **Live Assessment**capabilities, enabling you to comprehensively identify quality issues within live streams and evaluate performance scores, while providing corresponding recommendations.

#### Live Quality Control

The**Live Quality Control**feature encompasses **format diagnostics** and **content quality inspection**:

- **Format Diagnosis**:  A cloud-based audio and video processing service designed for real-time diagnostics of live streams, capable of analyzing issues such as stream information anomalies, timestamp irregularities, stream status abnormalities, container encapsulation errors, and decoding failures.
- **Content Quality Inspection**
  - **Common Image Issue**: Supports the detection of various live streaming quality issues, including mosaic artifacts, crash screens, image blurring, screen jitter, and visual noise.
  - **Recognition Code Detection**: Supports detection capabilities for QR codes, barcodes, applet codes, and other identification codes.
  - **Solid Color Screen and Brightness Detection**: Supports the detection of scenarios in live streaming such as black/white edges, solid color screens, low light conditions, and overexposure.
  - **Common Sound Issue**: Supports various live audio quality detection features, including Silence, Low Voice, and High Voice.

#### Live Assessment

The **Live Assessment**feature encompasses two distinct capabilities: **Scoring Without Reference** and **Scoring With Reference**.

- **Scoring Without Reference**：The algorithm objectively evaluates the quality of live streams without relying on comparative references, directly providing assessment scores.
- **Scoring With Reference**：Typically, the transcoded stream is evaluated and scored by comparing it against the original stream or the watermark stream.
  - **PSNR（**Peak Signal-to-Noise Ratio**）**: Perform scoring with reference on the transcoding stream quality by calculating the mean square error between the original/watermark stream and the transcoding stream to measure the compression or repair quality of the live streaming image.
  - **SSIM（**Structural Similarity Index**）**: Perform scoring with reference on the transcoding stream quality by comparing brightness, contrast, and structural information between the transcoding stream and the original/watermark stream and simulating human visual system perception of image quality.
  - **VMAF（**Video Multimethod Assessment Fusion**）**: Perform objective scoring with reference on the transcoding stream quality based on multiple basic metrics and machine learning models.

## Notes

- After creating a time shifting template, you need to bind it to a push domain.
- Both Quality Control and Scoring Without Reference can perform detection on Original streams, Watermarked streams, and Transcoded streams. Scoring With Reference, however, is exclusively applied to Transcoded streams—comparing them with Watermarked streams when watermarked content is present, and with Original streams when no watermark exists.

## Prerequisites

You have activated CSS and added a [push domain](https://intl.cloud.tencent.com/document/product/267/35970).

## Creating a Live Quality Control and Live Assessment Template

1. Log in to the CSS console. Select **Feature Configuration >**[Live Quality Control and Live Assessment](https://console.tencentcloud.com/live/config/quality-inspection/template) on the left sidebar.
2. Click **Create template** to set the Live Quality Control and Live Assessment Template information and configure the following:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8fbda62283d711f093f45254005ef0f7.png)

| Configuration Item |  | Description |
| --- | --- | --- |
| Template Name |  | Template name, which can be customized, Max 30 characters; supports letters, digits, underscores, and dashes. |
| Template Description |  | Template description, customizable,Max 100 characters; supports letters, digits, underscores, and dashes. |
| Detection Content |  | Detection Content is required. You can select the following content types (single or multiple selections):Original stream: Detects the original live stream that has not been transcoded, watermarked, or muxed.Watermarked stream: Detects the watermarked live stream configured with the watermark template.Transcoded stream: Detection is generated based on the transcoding template ID you specify, and the system will analyze the transcoded live content.**Note:**When both the Live Quality Control and Live Assessment Template are configured with Original Stream, Watermarked Stream, and Transcoded Stream as Detection Content, the Live Quality Control and Scoring Without Reference will initiate Quality Control and Assessment tasks for the Original Stream, Watermarked Stream (if present), and Transcoded Stream. The Scoring With Reference will only initiate Assessment tasks for the Transcoded Stream. |
|  Live Quality Control Configuration | Format Diagnosis | Format Diagnosis is a cloud-based audio and video processing service that provides real-time diagnostics for live streams. It analyzes issues such as stream information anomalies, timing anomalies, stream status anomalies, container encapsulation anomalies, and decoding anomalies. This feature can be manually enabled based on your business needs. |
|  | Common Image Issue | You can select Mosaic detection, Crash screen detection, Blur detection, Video jitter detection, or Video noise detection based on your actual business needs.**Mosaic detection**: Check whether there is a Mosaic on the Detection screen.**Crash screen detection**: Detect image damage, distortion, and other effects caused by transmission errors or decoding errors.**Blur detection**: Detects image blur caused by factors such as improper focus or object motion.**Video jitter detection**: Detects image jitter caused by shaking of the recording device.**Video noise detection**: Detection Checks whether the image has randomly distributed black and white spots, noise, or other snowflake-like effects. |
|  |  | After selecting the configuration, the chosen settings will be displayed on the right side of the page, where you may modify the parameter configurations as needed.**Detection Interval**: Perform a detection at the configured time interval.The valid range is [500, 10000] milliseconds, with a default value of 1000 milliseconds.**Detection Threshold**: When the detection score falls below the threshold, it will be identified as matching the specified issue.The value range is [0,100] points, with a default value of 60 points.Reference Score Range:  [0, 60): Poor (Bad);  [60, 80): Average (Normal);  [80, 100]: Excellent (Good).**Detection Duration**: When the detection score falls below the threshold and persists for the specified duration, the issue will be logged and reported.The valid range is [0,600] seconds, with a default value of 1 second.When the duration is set to 0, it indicates that issues will be reported immediately upon detection. |
|  | Recognition Code Detection | You may select QR code detection, barcode detection, or applet code detection based on your specific business requirements.**QR code detection**: Detect the presence of QR codes within the image.**Barcode detection**: Detect the presence of barcodes within the image.**Applet code detection**: Detect whether Applet code exists in the image. |
|  |  | After selecting the configuration, the chosen settings will be displayed on the right side of the page, where you may modify the parameter configurations as needed.**Detection Interval**: Perform a detection at the configured time interval.The valid range is [500, 10000] milliseconds, with a default value of 1000 milliseconds.**Detection Threshold**: When the detection score falls below the threshold, it will be identified as matching the specified issue.The value range is [0,100] points, with a default value of 60 points.Reference Score Range:  [0, 60): Poor (Bad);  [60, 80): Average (Normal);  [80, 100]: Excellent (Good).**Detection Duration**: When the detection score falls below the threshold and persists for the specified duration, the issue will be logged and reported.The valid range is [0,600] seconds, with a default value of 1 second.When the duration is set to 0, it indicates that issues will be reported immediately upon detection. |
|  | Solid Color Screen and Brightness Detection | You may select from Black/White Edge Detection, Solid Color Screen Detection, Light Detection, or Overexposure Detection based on your specific business requirements.**Black/White edge detection**: Detect whether there are black or white borders around the edges of the image.**Solid color screen detection**: Detect whether the image consists of a single color.**Light detection**: Detect whether the screen brightness is too low.**Overexposure detection**:  Detect whether the screen brightness is excessively high. |
|  |  | After selecting the configuration, the chosen settings will be displayed on the right side of the page, where you may modify the parameter configurations as needed.**Detection Interval**:  Perform a detection at the configured time interval.The valid range is [500, 10000] milliseconds, with a default value of 1000 milliseconds.**Detection Threshold**:  When the detection score falls below the threshold, it will be identified as matching the specified issue.The value range is [0,100] points, with a default value of 60 points.Reference Score Range:  [0, 60): Poor (Bad);  [60, 80): Average (Normal);  [80, 100]: Excellent (Good).**Detection Duration**:  When the detection score falls below the threshold and persists for the specified duration, the issue will be logged and reported.The valid range is [0,600] seconds, with a default value of 1 second.When the duration is set to 0, it indicates that issues will be reported immediately upon detection. |
|  | Common Sound Issue | You may select detection items based on your actual business requirements, including Silence Detection, Voice Detection, and High Voice Detection.**Silence detection**:  Detect the presence of silent segments within the audio.**Low Voice Detection**:  Detect whether the audio exhibits insufficient volume levels.**High voice detection**:  Detect whether the audio exhibits excessive volume levels. |
|  |  | After selecting the configuration, the chosen settings will be displayed on the right side of the page, where you may modify the parameter configurations as needed.**Detection Interval**:  Perform a detection at the configured time interval.The valid range is [500, 10000] milliseconds, with a default value of 1000 milliseconds.**Detection Threshold**:  When the detection score falls below the threshold, it will be identified as matching the specified issue.The value range is [0,100] points, with a default value of 60 points.Reference Score Range:  [0, 60): Poor (Bad);  [60, 80): Average (Normal);  [80, 100]: Excellent (Good).**Detection Duration**:  When the detection score falls below the threshold and persists for the specified duration, the issue will be logged and reported.The valid range is [0,600] seconds, with a default value of 1 second.When the duration is set to 0, it indicates that issues will be reported immediately upon detection. |
|  Evaluation Configuration | Scoring Without Reference | Scoring Without Reference refers to evaluating the quality of live streaming video content on a percentile scale based on multi-dimensional detection criteria, without requiring comparative scoring data as a reference.**VQA (Video Quality Assessment):** Perform scoring without reference on the live stream if this option is selected. The thresholds correspond to scores of scoring without reference. The score is reported if it is less than a set threshold. **Detection Interval**:  Perform a detection at the configured time interval.The valid range is [500, 10000] milliseconds, with a default value of 1000 milliseconds.**Detection Threshold**:  When the detection score falls below the threshold, it will be identified as matching the specified issue.The value range is [0,100] points, with a default value of 60 points.Reference Score Range:  [0, 60): Poor (Bad);  [60, 80): Average (Normal);  [80, 100]: Excellent (Good).**Detection Duration**:  When the detection score falls below the threshold and persists for the specified duration, the issue will be logged and reported.The valid range is [0,600] seconds, with a default value of 1 second.When the duration is set to 0, it indicates that issues will be reported immediately upon detection. |
|  | Scoring With Reference | Scoring with Reference typically evaluates the transcoded stream by comparing it against the original stream or watermarked stream, thereby providing an assessment score for the transcoded stream.**PSNR (Peak Signal-to-Noise Ratio):** Perform scoring with reference on the transcoding stream quality by calculating the mean square error between the original/watermark stream and the transcoding stream to measure the compression or repair quality of the live streaming image. **Detection Interval**:  Perform a detection at the configured time interval.The valid range is [500, 10000] milliseconds, with a default value of 1000 milliseconds.**Detection Threshold**:  When the detection score falls below the threshold, it will be identified as matching the specified issue.The valid range is [0,60] minutes, with a default value of 30 minutes.Reference Score Ranges:[0,30): Poor (bad);[30,38): Average (normal);[38,60]: Excellent (good).**Live Assessment Cycle**:  Indicates the evaluation duration for each live stream assessment. Upon reaching the evaluation cycle, all assessment scores within this period will be reported.The valid range is [10,600] seconds, with a default value of 10 seconds. |
|  |  | **SSIM (Structural Similarity Index)**: Perform scoring with reference on the transcoding stream quality by comparing brightness, contrast, and structural information between the transcoding stream and the original/watermark stream and simulating human visual system perception of image quality. **Detection Interval**:  Perform a detection at the configured time interval.The valid range is [500, 10000] milliseconds, with a default value of 1000 milliseconds.**Detection Threshold**: When the detection score falls below the threshold, it will be identified as matching the specified issue.The valid range is [0,1], with a default value of 0.8 points.Reference Score Ranges:[0, 0.8): Poor (bad);[0.8, 0.95): Average (normal);[0.95-1]: Excellent (good).**Live Assessment Cycle**:  Indicates the evaluation duration for each live stream assessment. Upon reaching the evaluation cycle, all assessment scores within this period will be reported.The valid range is [10,600] seconds, with a default value of 10 seconds. |
|  |  | VMAF (Video Multimethod Assessment Fusion): Perform objective scoring with reference on the transcoding stream quality based on multiple basic metrics and machine learning models. **Detection Interval**:  Perform a detection at the configured time interval.The valid range is [500, 10000] milliseconds, with a default value of 1000 milliseconds.**Detection Threshold**:  When the detection score falls below the threshold, it will be identified as matching the specified issue.The valid range is [0,100], with a default value of 60 points.Reference Score Range:  [0, 60): Poor (Bad);  [60, 80): Average (Normal);  [80, 100]: Excellent (Good).**Live Assessment Cycle**:  Indicates the evaluation duration for each live stream assessment. Upon reaching the evaluation cycle, all assessment scores within this period will be reported.The valid range is [10,600] seconds, with a default value of 10 seconds. |
|  Quality Issue Storage | Storage Scope | You can select Record events only and Take screenshots and retain them. |
|  | Storage Path | Select the COS bucket you have created and authorized in Cloud Object Storage.The Region denotes the geographical location information of the aforementioned Bucket and cannot be modified.FolderCOS folder names Only support lowercase letters (a–z), uppercase letters (A–Z), digits (0–9), special characters (- ! _ . *), and placeholders.Click the input field to select a COS folder. Default value:`/QualityControlAndAssessment/{Domain}/{Appname}/{StreamID}/{QCFunction}/{Year}-{Month}-{Day}-{Hour}-{Minute}-{Second}-{MilliSecond}-{QCclass}-{Score}{EXT}` |
|  | Time zone | You may select either UTC+8 or UTC.When selecting the time zone parameter as UTC+8,The quality inspection file is named based on the UTC+8 time parameter.When the time zone parameter is set to UTC,The live quality control file is named based on the UTC time parameter. |

3. After filling in the form, click **Save** in the lower right corner and view the Billing Details. If you need to know the relevant billing information, click **Billing Details**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4e7ec72379c011f0bda35254007c27c5.png)

## Binding a Domain Name

1. Log in to the CSS console. Select **Feature Configuration >**[Live Quality Control and Live Assessment](https://console.tencentcloud.com/live/config/quality-inspection/template) on the left sidebar.
  - **Bind a domain to an existing template**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6623142783d611f0b321525400e889b2.png)

  - **Bind a domain after creating a new Live Quality Control and Live Assessment Template**: After successfully creating a Live Quality Control and Live Assessment Template, click **Bind Domain Name** in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/77b530687e7411f0bd33525400454e06.png)

2. In the Bind Domain Name window, select the **live quality control and live assessment template** and **push domain** you want to bind together, and click Confirm to bind them.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b43ba3d97e7411f0914f52540099c741.png)

> **Note:**You can click **Add** to bind multiple push domains to the current template.

## Unbinding

1. Log in to the CSS console. Select **Feature Configuration >**[Live Quality Control and Live Assessment](https://console.tencentcloud.com/live/config/quality-inspection/template) on the left sidebar.
2. Select the live quality control and live assessment template from which you want to unbind the push domain and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ca23082f83d611f0992e52540044a08e.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1d765b1179c111f0bd33525400454e06.png)

> **Note:**After quality control and assessment are unbound, the live stream will not be affected.

## Modifying a Template

1. Log in to the CSS console. Select **Feature Configuration >**[Live Quality Control and Live Assessment](https://console.tencentcloud.com/live/config/quality-inspection/template) on the left sidebar.
2. Select the Live Quality Control and Live Assessment Template you have successfully created and click **Edit** on the right to modify the template information. After modification, click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f0fd9e3583d611f0bd05525400454e06.png)

## Deleting a Template

1. Log in to the CSS console. Select **Feature Configuration >**[Live Quality Control and Live Assessment](https://console.tencentcloud.com/live/config/quality-inspection/template) on the left sidebar.
2. Select a previously created  live quality control and live assessment template and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0d369a8083d711f0992e52540044a08e.png)

3. Click **Confirm** to permanently delete the template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1ea570c583d711f093f45254005ef0f7.png)

> **Note****：**If the template is already bound to a push domain, you must first [unbind](#.E8.A7.A3.E9.99.A4.E7.BB.91.E5.AE.9A) it before the template can be deleted.The live quality control and live assessment template management of the CSS console is based on the domain name dimension. Rules created by the associated interface cannot be canceled for the time being.

## Related Operations

For detailed instructions and additional information on binding and unbinding live quality control and live assessment template at the domain level, please refer to [Live Quality Control Configuration](https://www.tencentcloud.com/document/product/267/73201)**.**


---
*Source: [https://www.tencentcloud.com/document/product/267/73200](https://www.tencentcloud.com/document/product/267/73200)*
