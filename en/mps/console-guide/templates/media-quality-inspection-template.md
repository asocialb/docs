# Media Quality Inspection Template

## Overview

The media quality inspection service can comprehensively identify issues in media assets, verify whether the contents meet the requirements, and offer suggestions. Users may directly use the preset templates or create media quality inspection templates in the console to customize quality inspection parameters.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7bb1f3816f2011ef92db52540055f650.png)

The quality inspection contents include:

- **Format diagnosis**: Media diagnosis is a cloud-based audio and video processing service designed for real-time diagnosis of media streams. It can be used to analyze exceptions in stream information, temporal information, stream status, container encapsulation, and decoding.
- **No-reference scoring**: It refers to scoring the quality of a video without a reference, with scores ranging from 0 to 100.
- **Image quality**: It provides a variety of quality inspection features, including but not limited to detection of screen glitch, black screen, jitter, noise, mosaic, low light, QR code, barcode, and mini program code.
- **Sound detection**: It provides a variety of quality inspection features, including but not limited to detection of no voice, low voice, and high voice.

## Description of Quality Inspection Template Parameters

In the quality inspection template, you can enable inspection items and configure their parameters. For details on media quality inspection billing, please refer to [billing instructions](https://www.tencentcloud.com/document/product/1041/49204?lang=en&pg=#2bc42389-7247-4b15-a8c7-d4e4aa997853).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/32c107309a8211f09936525400e889b2.png)

| Detection Type | Detection Item | Parameter Description |
| --- | --- | --- |
| Format diagnosis | Format diagnosis | Media diagnosis is a cloud-based audio and video processing service for real-time diagnosis of media streams. It can be used to analyze exceptions in stream information, temporal information, stream status, container encapsulation, and decoding. |
| Quality score | No Reference Score for Video（MOS） | Once it is enabled, you need to enable low quality inspection as well. The corresponding issue is reported if the no-reference scoring result is lower than the set threshold.Scores for reference: 40–60: poor; 60–80: good; 80–100: excellent.Two parameters can be configured: "threshold" and "detection interval". The threshold corresponds to the score given by the no-reference scoring feature, and a report will be generated when the score falls below the set threshold. The detection interval is measured in milliseconds (ms). |
|  | Audio No Reference Score（MOS） | Once it is enabled, the audio quality will be detected. The threshold corresponds to the quality score of audio parts. When the score of any audio part is less than the threshold, a low score event is reported. |
| Image quality issues | Mosaic detection | Detect whether mosaic patterns exist in the image. Report when the detected confidence level is greater than or equal to the specified threshold.  Confidence level ranges from [0, 100];  Detection interval is measured in milliseconds (ms) and must exceed 500ms;  Duration ranges from 0 to 600,000ms. |
|  | Screen glitch detection | Detect visual anomalies such as damage, distortion, or disarray in the footage caused by transmission errors, decoding issues, or other factors. When the detected confidence level meets or exceeds the specified threshold, a report is generated.  Confidence level ranges from [0, 100].Detection interval is measured in milliseconds (ms) and must be greater than 500 ms.Duration range is 0–600,000 ms. |
|  | Blur detection | Detects image blurring caused by improper focus or object movement. The threshold serves as the evaluation criterion during detection; the higher the threshold, the more likely an image is deemed blurry.  Threshold value range: [0, 100];  Detection interval unit: milliseconds (ms), with a minimum value of 500 ms;  Duration range: 0–600,000 ms. |
|  | Jitter detection | Detects image jitter caused by the shaking of recording devices. The threshold serves as the criterion for determining jitter; the higher the threshold, the more severe the jitter. When the jitter intensity exceeds the set threshold, a report is generated.  Threshold value range: [1,10];  Detection interval is non-configurable;  Duration range: 0–600,000 ms. |
|  | Noise detection | Detects whether there is noise in the image. The threshold serves as the benchmark for determining noise. The higher the threshold is, the more obvious the noise will be. A report will be generated when the intensity level is greater than or equal to the set threshold. Threshold range: [0, 100];Detection interval is measured in milliseconds (ms) and must exceed 500 ms;Duration range: 0–600,000 ms. |
|  | QR code detection | Detects whether there is a QR code in the image. The threshold corresponds to the confidence level of QR code detection, and a report will be generated when the detected confidence level is greater than or equal to the set threshold. Threshold range: [0, 100];Detection interval is measured in milliseconds (ms) and must exceed 500 ms;Duration range: 0–600,000 ms. |
|  | Barcode detection | Detects whether there is a barcode in the image. The threshold corresponds to the confidence level of barcode detection, and a report will be generated when the detected confidence level is greater than or equal to the set threshold. Threshold range: [0, 100];Detection interval is measured in milliseconds (ms) and must exceed 500 ms;Duration range: 0–600,000 ms. |
|  | Mini program code detection | Detects whether there is a mini program code in the image. The threshold corresponds to the confidence level of mini program code detection, and a report will be generated when the detected confidence level is greater than or equal to the set threshold. Threshold range: [0, 100];Detection interval is measured in milliseconds (ms) and must exceed 500 ms;Duration range: 0–600,000 ms. |
| Solid color screen detection | Black and white edge detection | Detects whether there are black and white edges around the image.Threshold range: [0, 50];Detection interval is measured in milliseconds (ms) and must exceed 500 ms;Duration range: 0–600,000 ms. |
|  | Solid color screen detection | Detects whether the screen is a solid color screen.Threshold range: [90, 100];Detection interval is measured in milliseconds (ms) and must exceed 500 ms;Duration range: 0–600,000 ms. |
| Brightness detection | Low light detection | Detect whether the screen brightness is excessively low. The threshold is defined as the percentage of low-light pixels, and a report is triggered when the detected percentage is greater than or equal to the set threshold.  Threshold range: [80, 100];Detection interval is measured in milliseconds (ms) and must exceed 500 ms;Duration range: 0–600,000 ms. |
|  | Overexposure detection | Detect whether the screen brightness is excessively high. The threshold is defined as the percentage of overexposed pixels, and a report is triggered when the detected percentage meets or exceeds the set threshold.  Threshold range: [50, 100];  Detection interval is measured in milliseconds (ms) and must be greater than 500 ms; Duration range: 0–600,000 ms. |
| Sound detection | No voice detection | Detect whether silence exists in the audio.  The threshold value range is non-editable;  The detection interval is measured in milliseconds (ms) and must be greater than 0 ms;  The duration range is 0–600,000 ms. |
|  | Low voice detection | Detect whether there are segments with low volume in the audio. When the audio decibel level falls below the specified threshold, a report will be generated.  Loudness range: [0, 20];Detection interval unit: milliseconds (ms), the value must be greater than 0 ms;Duration range: 0–600,000 ms. |
|  | High voice detection | Detect whether the audio contains segments with excessively high volume. Report when the audio decibel level exceeds the specified threshold.  Loudness range: [70, 96];  Detection interval unit: milliseconds (ms), with a value greater than 0 ms;  Duration range: 0–600,000 ms. |

### Detection Settings

Detection settings offer customizable control over the scope of detection, as well as the method of recording detected issues.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/87e3128d712f11f096685254001c06ec.png)

#### Quality Inspection Issue Recording Method

By default, the system logs the time intervals during which quality inspection issues occur. If the option "Screenshots of start and end frames" is selected, the quality inspection report will additionally display two screenshots capturing the start and end points of the identified issue.

> **Note：**Enabling "Screenshots of start and end frames" will incur additional costs for screenshots and image storage, apart from the quality inspection fees.

#### Detection Scope

By default, quality inspection encompasses the entire video. However, it also supports the configuration of a custom detection scope. Once the custom scope is enabled, it will appear as illustrated below.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9b297afb712f11f0bcac525400e889b2.png)

- **Skip Intro:** At the initiation of each quality inspection task, the system will bypass a specified duration before commencing detection. This feature is particularly suitable for scenarios where video content includes a fixed intro, effectively preventing redundant detection of repeated video segments. The range for skipping the intro duration is between 1 and 1800 seconds.
- **Detection Duration:** The detection duration defines the length of time for each quality inspection action and serves as a critical parameter for sampling-based video quality inspection. For large volumes of video content, setting a detection duration can significantly reduce inspection costs. For instance, by specifying a detection duration of 300 seconds, the quality inspection task will analyze only 300 seconds of the video during execution, eliminating the need to inspect the entire video length. (The allowable range for the detection duration parameter is 10 to 86,400 seconds.)
- **Detection Interval:** By configuring the detection interval alongside the detection duration, quality inspection can achieve effects such as sampling 5 minutes of content for inspection within every hour of video. (The range for detection interval duration is between 10 and 3600 seconds.)
- **Loop Count:** This parameter is used to limit the number of cycles for repeated inspections. By default, looped inspections will continuously perform the "detect-wait interval-detect" operation until the entire video content has been inspected. When a loop count is set, the quality inspection will cease once the specified number of cycles has been reached.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a661889a712f11f081ce52540044a08e.png)


---
*Source: [https://www.tencentcloud.com/document/product/1041/64357](https://www.tencentcloud.com/document/product/1041/64357)*
