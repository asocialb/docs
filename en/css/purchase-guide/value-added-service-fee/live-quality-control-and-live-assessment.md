# Live Quality Control and Live Assessment

## Overview

CSS offers **Live Quality Control** and **Live Assessment**capabilities, enabling you to comprehensively identify quality issues within live streams and evaluate performance scores during live broadcasts, while providing corresponding recommendations.

#### Live Quality Control

Provides capabilities for **Format Diagnosis** and **Content Quality Inspection**:

| Capability |  | Description |
| --- | --- | --- |
| **Format Diagnosis** |  | A cloud-based audio and video processing service designed for real-time diagnostics of live streams, capable of analyzing issues such as stream information anomalies, timestamp irregularities, stream status abnormalities, container encapsulation errors, and decoding failures. |
| Content Quality Inspection | Common Image Issue | Supports the detection of various live streaming quality issues, including mosaic artifacts, crash screens, image blurring, screen jitter, and visual noise. |
|  | Recognition Code Detection | Supports detection capabilities for QR codes, barcodes, applet codes, and other identification codes. |
|  | Solid Color Screen and Brightness Detection | Supports the detection of scenarios in live streaming such as black/white edges, solid color screens, low light conditions, and overexposure. |
|  | Common Sound Issue | Supports various live audio quality detection features, including Silence, Low Voice, and High Voice. |

#### Live Assessment

Includes **Scoring Without Reference** and **Scoring With Reference**:

- **Scoring Without Reference**：The algorithm objectively evaluates the quality of live streams without relying on comparative references, directly providing assessment scores.
- **Scoring With Reference**：Typically, the transcoded stream is evaluated and scored by comparing it against the original stream or the watermark stream. The capabilities are outlined in the table below:

| Capability | Description |
| --- | --- |
| PSNR | Peak Signal-to-Noise Ratio: Perform scoring with reference on the transcoding stream quality by calculating the mean square error between the original/watermark stream and the transcoding stream to measure the compression or repair quality of the live streaming image. |
| SSIM | Structural Similarity Index: Perform scoring with reference on the transcoding stream quality by comparing brightness, contrast, and structural information between the transcoding stream and the original/watermark stream and simulating human visual system perception of image quality. |
| VMAF | Video Multimethod Assessment Fusion: Perform objective scoring with reference on the transcoding stream quality based on multiple basic metrics and machine learning models. |

## Must-Knows

- If the Original stream, Watermarked stream, and Transcoded stream are simultaneously configured as detection content within the Live Quality Control and Live Assessment Template, Live Quality Control and Scoring Without Reference will initiate Quality Control and Assessment tasks for the Original stream, Watermarked stream (if applicable), and Transcoded stream. Scoring With Reference, however, will only initiate Assessment tasks for the Transcoded stream.
- Live Quality Control and Live Assessment are both triggered by stream pushing.
- The minimum task unit for Quality Control and Assessment is one minute. Tasks shorter than one minute will be billed as one minute.

## Pricing

| Billable Item | Function Type |  |  |  | Price (USD/Min) |  |
| --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  | Resolution(2K and below) | Resolution(More than 2K) |
| Duration of Live Quality Control | Quality Control | Format Diagnosis | Format Diagnosis | Format Diagnosis | 0.008 | 0.027 |
|  |  | Content Quality Inspection | Common Image Issue | Mosaic detection | 0.008 | 0.027 |
|  |  |  |  | Crash screen detection | 0.008 | 0.027 |
|  |  |  |  | Blur detection | 0.008 | 0.027 |
|  |  |  |  | Video jitter detection | 0.008 | 0.027 |
|  |  |  |  | Video noise detection | 0.008 | 0.027 |
|  |  |  | Recognition Code Detection | QR code/Barcode detection/Applet code detection | 0.008 | 0.027 |
|  |  |  | Solid Color Screen and Brightness Detection | Black/White edge detection | 0.008 | 0.027 |
|  |  |  |  | Solid color screen detection | 0.008 | 0.027 |
|  |  |  |  | Low light/Overexposure detection | 0.008 | 0.027 |
|  |  |  | Common Sound Issue | Silence/Low voice/High voice detection | 0.008 |  |
|  |  Evaluation | Scoring Without Reference | Scoring Without Reference | Scoring Without Reference | 0.016 | 0.11 |
|  |  | Scoring With Reference | PSNR/SSIM | PSNR/SSIM | 0.016 | 0.11 |
|  |  |  | VMAF | VMAF | 0.016 | 0.11 |

## Billing details

- Billable item: Duration of Live Quality Control
- Billing mode: Pay-as-you-go
- Billing cycle: Daily billing. Hourly billing. Billing is issued and fees are deducted hourly. Detailed billing and billing time are subject to the actual billing invoice.

## Billing examples

If you utilize the Quality Control and Assessment services on June 1, 2025, with the detection content configured in the template as Original Stream and Transcoded Stream (single transcoding template), both live stream resolutions set to 1080P, and enable Quality Control capabilities including Format Diagnosis, Crash Screen Detection, QR Code Detection, Barcode Detection, Silence Detection, High Voice Detection, as well as Evaluation capabilities such as PSNR and SSIM, for a total live streaming duration of 1 hour with continuous detection enabled throughout, the billing amount will be:

- Quality Control Fees:
  - Format diagnosis fees = 0.008(USD/minute) × 60(minutes) (Original stream) + 0.008(USD/minute) × 60(minutes) (Transcoded stream) = 0.96USD
  - Crash screen detection fees = 0.008(USD/minute) × 60(minutes) (Original stream) + 0.008(USD/minute) × 60(minutes) (Transcoded stream) = 0.96USD
  - Recognition code detection fees(including QR code and Barcode detection) = 0.008(USD/minute) × 60( minutes) (Original stream) + 0.008 (USD/minute) × 60( minutes) (Transcoded stream) = 0.96USD
  - Common sound issue fees (including silence and high voice detection) = 0.008(USD/minute) × 60(minutes) (Original stream) + 0.008(USD/minute) × 60(minutes) (Transcoded stream) = 0.96USD
- Evaluation fees ：Scoring With Reference fees(including PSNR and SSIM) = 0.016(USD/minute) × 60(minutes) (Transcoded stream)= 0.96USD


---
*Source: [https://www.tencentcloud.com/document/product/267/73198](https://www.tencentcloud.com/document/product/267/73198)*
