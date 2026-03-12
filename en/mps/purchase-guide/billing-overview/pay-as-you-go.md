# Pay-As-You-Go

## Billing Cycle

Media Processing Service (MPS) supports daily and monthly (settled monthly) billing for the pay-as-you-go mode. The default billing cycle is daily. If you want to switch to the monthly billing, please contact our business team.

Your MPS bills contain only the fees incurred for using media processing services such as transcoding and remuxing. **Fees for COS are not included**. You can view detailed usage through [Console Usage Statistics](https://console.tencentcloud.com/mps/statistics?tab=transcode).

## Daily Billing (default)

Each day, MPS calculates your usage in the previous day, sends you the bill, and deducts the fee from your account balance.

- Billing cycle: Daily. The fees incurred each day are billed and deducted from your account balance between 12:00 and 18:00 the following day.
- Billing mode: **Pay-as-you-go**.

## Monthly Billing

> **Note:**The default billing cycle is daily. If you want to switch to monthly billing, please contact our business team.

On the first day of each month, MPS calculates your usage in the previous month, sends you a bill, and deducts the fee from your balance account.

- Billing cycle: Monthly. The fees incurred each month are billed and deducted from your account balance on the first day of the following month.
- Payment method: **Pay-as-you-go**.
- For monthly billing, the unit prices specified in your contract with Tencent Cloud will apply. For more information, please contact our business team.

## Audio/Video Transcoding

With the most comprehensive audio and video encoding and compression standard in the industry, we provide multiple transcoding methods including Top Speed Codec (TSC) Transcoding, Transcoding to Adaptive Bitrate Streaming, Remuxing, and Audio Transcoding, helping to save playback bandwidth and costs.

### General Transcoding

Pricing: Fees are calculated by video duration (minutes) after transcoding by the corresponding unit price (USD/min).

| Type | Codec | Resolution | Chinese Mainland | Hong Kong (China), Tokyo, Frankfurt, Silicon Valley, Virginia | Singapore,  Seoul, Bangkok |
| --- | --- | --- | --- | --- | --- |
| General Transcoding | H.264 | 4K (short side ≤ 2160 px) | 0.0421 | 0.0441 | 0.0480 |
|  | H.264 | 2K (short side ≤ 1440 px) | 0.0206 | 0.0316 | 0.0355 |
|  | H.264 | FHD (short side ≤ 1080 px) | 0.0095 | 0.0215 | 0.0230 |
|  | H.264 | HD (short side ≤ 720 px) | 0.0049 | 0.0109 | 0.0105 |
|  | H.264 | SD (short side ≤ 480 px) | 0.0024 | 0.0079 | 0.0074 |
|  | H.265 | 8K (short side ≤ 4320 px) | 0.8642 |  |  |
|  | H.265 | 4K (short side ≤ 2160 px) | 0.2121 | 0.2128 | 0.2480 |
|  | H.265 | 2K (short side ≤ 1440 px) | 0.1136 | 0.1564 | 0.1855 |
|  | H.265 | FHD (short side ≤ 1080 px) | 0.0472 | 0.0494 | 0.1230 |
|  | H.265 | HD (short side ≤ 720 px) | 0.0246 | 0.0248 | 0.0605 |
|  | H.265 | SD (short side ≤ 480 px) | 0.0145 | 0.0127 | 0.0449 |
|  | AV1 | 8K (short side ≤ 4320 px) | 1.7284 |  |  |
|  | AV1 | 4K (short side ≤ 2160 px) | 0.4729 |  |  |
|  | AV1 | 2K (short side ≤ 1440 px) | 0.2364 |  |  |
|  | AV1 | FHD (short side ≤ 1080 px) | 0.1098 |  |  |
|  | AV1 | HD (short side ≤ 720 px) | 0.0550 |  |  |
|  | AV1 | SD (short side ≤ 480 px) | 0.0282 |  |  |
|  | MV-HEVC | 8K (short side ≤ 4320 px) | 2.5926 |  |  |
|  | MV-HEVC | 4K (short side ≤ 2160 px) | 0.6363 |  |  |
|  | MV-HEVC | 2K (short side ≤ 1440 px) | 0.3408 |  |  |
|  | MV-HEVC | FHD (short side ≤ 1080 px) | 0.1416 |  |  |
| Audio transcoding | - | - | 0.0008 | 0.0017 | 0.0019 |
| Remuxing | - | - | 0.0011 | 0.0026 | 0.0028 |

#### **Billing Details**

Transcoding services are billed daily based on the codec used, the output resolution, and the video duration.

- Billing formula: Video Transcoding Fees = Output Video Duration (minutes) × Unit Price of Transcoding with Different Codecs and Resolutions (USD/minute)
  - Each transcoding task is billed only once.
  - In case of daily billing, the system counts the total seconds per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

#### **Billing Example**

Suppose you used the general transcoding service in Singapore on January 1 to process the video resources in the COS bucket and generated two videos. One was 100 minutes long and had a resolution of 2560 × 1440 px. The other was 100 minutes long and had a resolution of 1280 × 640 px. The codec used was H.264. Besides, you generated another video that was 100 minutes long through general audio transcoding.

- For the video with a resolution of 2560 × 1440 px and the short side in 2K (short side ≤ 1440px), the corresponding unit price in Singapore is 0.0355 (USD/minute).
- For the video with a resolution of 1280 × 640 px and the short side lower than HD (720px and below) but greater than SD (480px and below), the corresponding unit price in Singapore is 0.0105 (USD/min).
- The unit price for general audio transcoding in Singapore is 0.0019 (USD/min).

On January 2, the transcoding fee deducted would be as follows: 0.0355 (USD/minute) × 100 (minutes) + 0.0105 (USD/minute) × 100 (minutes) + 0.0019 (USD/minute) × 100 (minutes) = 4.79 (USD).

### Top Speed Codec(TSC) Transcoding

TSC adopts intelligent dynamic encoding technology, which can achieve higher image quality while reducing the bitrate, with the VMAF value increased by 3 to 5 points.

Pricing: Fees are calculated by video duration (minutes) after transcoding by the corresponding unit price (USD/min).

| Type | Codec | Resolution | Chinese Mainland | Hong Kong (China), Tokyo, Frankfurt, Silicon Valley, Virginia | Singapore, Seoul, Bangkok |
| --- | --- | --- | --- | --- | --- |
| TSC Transcoding | H.264 | 4K (short side ≤ 2160 px) | 0.1493 | 0.1467 | 0.1533 |
|  | H.264 | 2K (short side ≤ 1440 px) | 0.0747 | 0.0733 | 0.0767 |
|  | H.264 | FHD (short side ≤ 1080 px) | 0.0347 | 0.0340 | 0.0356 |
|  | H.264 | HD (short side ≤ 720 px) | 0.0176 | 0.0173 | 0.0181 |
|  | H.264 | SD (short side ≤ 480 px) | 0.0117 | 0.0115 | 0.0120 |
|  | H.265 | 8K (short side ≤ 4320 px) | 1.7284 |  |  |
|  | H.265 | 4K (short side ≤ 2160 px) | 0.7467 | 0.7333 | 0.7667 |
|  | H.265 | 2K (short side ≤ 1440 px) | 0.3733 | 0.3667 | 0.3833 |
|  | H.265 | FHD (short side ≤ 1080 px) | 0.1739 | 0.1708 | 0.1785 |
|  | H.265 | HD (short side ≤ 720 px) | 0.0869 | 0.0854 | 0.0893 |
|  | H.265 | SD (short side ≤ 480 px) | 0.0581 | 0.0571 | 0.0597 |
|  | AV1 | 8K (short side ≤ 4320 px) | 3.4568 |  |  |
|  | AV1 | 4K (short side ≤ 2160 px) | 1.4815 |  |  |
|  | AV1 | 2K (short side ≤ 1440 px) | 0.7407 |  |  |
|  | AV1 | FHD (short side ≤ 1080 px) | 0.3450 |  |  |
|  | AV1 | HD (short side ≤ 720 px) | 0.1725 |  |  |
|  | AV1 | SD (short side ≤ 480 px) | 0.1153 |  |  |
|  | MV-HEVC | 8K (short side ≤ 4320 px) | 5.1852 |  |  |
|  | MV-HEVC | 4K (short side ≤ 2160 px) | 2.2401 |  |  |
|  | MV-HEVC | 2K (short side ≤ 1440 px) | 1.1199 |  |  |
|  | MV-HEVC | FHD (short side ≤ 1080 px) | 0.5217 |  |  |
| Audio TSC Transcoding | - | - | 0.005 |  |  |

##### **Billing Details**

Transcoding services are billed daily based on the codec used, the output resolution, and the video duration.

- Billing formula: Video Transcoding Fees = Output Video Duration (minutes) × Unit Price of Transcoding with Different Codecs and Resolutions (USD/minute)
  - Each transcoding task is billed only once.
  - In case of daily billing, the system counts the total seconds per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

#### TSC Transcoding - Extreme Compress Strategy

TSC Transcoding supports  **Standard Compress** and  **Extreme Compress** two compression strategies. Different strategies have different underlying transcoding models, which will affect the bitrate, image quality, and other results.

- Standard compress: It is the standard TSC transcoding, providing three options:
  - Low Compress - to ensure image quality
  - Medium Compress - for overall optimal
  - High Compress - to reduce bitrate

From top to bottom, the higher the compression degree, the smaller the output video file size, and the greater the image quality loss. For use of any option in this strategy,  **only the** [TSC Transcoding Fees](#tsc-transcoding) will be charged.

- Extreme Compress: It is the "upgraded version" of the standard compression,  **with the highest compression degree,** which can maximize the bitrate compression while ensuring a certain level of image quality, greatly saving bandwidth and storage costs. For use of this strategy,  **you will be charged for** [TSC Transcoding](#tsc-transcoding) **+** [Audio/Video Enhancement - Artifacts Removal](#Artifacts) **.**

> **Note:**If the output video needs to be provided for users to watch on TV, it is not recommended to use the extreme compress strategy.

##### **Billing Example**

Suppose you used the TSC transcoding service in Singapore on January 1 to process the video resources in the COS bucket and used the standard compress (high compress) strategy to transcode a video that was 100 minutes long and had a resolution of 2560 × 1440 px at 60fps, and used the extreme compress strategy to transcode a video that was 100 minutes long and had a resolution of 2560 × 1440 at 60 fps. The codec used was H.264.

- For the part using the standard compress strategy, only the TSC transcoding fees will be charged. With the video short side of 1440 in 2K (short side ≤ 1440 px), the unit price in Singapore is 0.0767 (USD/min).
- For the part using the extreme compress strategy, in addition to the TSC transcoding fees, the Audio and Video Enhancement - Artifacts Removal fees will be charged. The unit price of Artifacts Removal for the 2K and 60fps level is 0.1235 (USD/min).

On January 2, the transcoding fee deducted would be as follows: 0.0767 (USD/minute) × 100 (minutes) + 0.0767 (USD/minute) × 100 (minutes) + 0.1235 (USD/minute) × 100 (minutes) = 27.69 (USD).

### Hybrid Cloud Transcoding

#### Hybrid Cloud General Transcoding

| Codec | Resolution | Price (USD/min) |
| --- | --- | --- |
| H.264 | 4K (short side ≤ 2160 px) | 0.03 |
| H.264 | 2K (short side ≤ 1440 px) | 0.0192 |
| H.264 | FHD (short side ≤ 1080 px) | 0.015 |
| H.264 | HD (short side ≤ 720 px) | 0.0128 |
| H.264 | SD (short side ≤ 480 px) | 0.0085 |
| H.265 | 4K (short side ≤ 2160 px) | 0.096 |
| H.265 | 2K (short side ≤ 1440 px) | 0.0667 |
| H.265 | FHD (short side ≤ 1080 px) | 0.048 |
| H.265 | HD (short side ≤ 720 px) | 0.0286 |
| H.265 | SD (short side ≤ 480 px) | 0.014 |
| AV1 | 4K (short side ≤ 2160 px) | 0.6457 |
| AV1 | 2K (short side ≤ 1440 px) | 0.3191 |
| AV1 | FHD (short side ≤ 1080 px) | 0.1614 |
| AV1 | HD (short side ≤ 720 px) | 0.0797 |
| AV1 | SD (short side ≤ 480 px) | 0.0386 |
| MV-HEVC | 8K (short side ≤ 4320 px) | 1.1733 |
| MV-HEVC | 4K (short side ≤ 2160 px) | 0.288 |
| MV-HEVC | 2K (short side ≤ 1440 px) | 0.2001 |
| MV-HEVC | FHD (short side ≤ 1080 px) | 0.144 |
| Audio transcoding | - | 0.002 |
| Remuxing | - | 0.0031 |

#### Hybrid Cloud TSC Transcoding

| Codec | Resolution | Price (USD/min) |
| --- | --- | --- |
| H.264 | 4K (short side ≤ 2160 px) | 0.09 |
| H.264 | 2K (short side ≤ 1440 px) | 0.0577 |
| H.264 | FHD (short side ≤ 1080 px) | 0.045 |
| H.264 | HD (short side ≤ 720 px) | 0.0383 |
| H.264 | SD (short side ≤ 480 px) | 0.0256 |
| H.265 | 4K (short side ≤ 2160 px) | 0.288 |
| H.265 | 2K (short side ≤ 1440 px) | 0.2002 |
| H.265 | FHD (short side ≤ 1080 px) | 0.144 |
| H.265 | HD (short side ≤ 720 px) | 0.0857 |
| H.265 | SD (short side ≤ 480 px) | 0.0419 |
| AV1 | 4K (short side ≤ 2160 px) | 1.9372 |
| AV1 | 2K (short side ≤ 1440 px) | 0.9573 |
| AV1 | FHD (short side ≤ 1080 px) | 0.4843 |
| AV1 | HD (short side ≤ 720 px) | 0.2392 |
| AV1 | SD (short side ≤ 480 px) | 0.1158 |
| MV-HEVC | 8K (short side ≤ 4320 px) | 2 |
| MV-HEVC | 4K (short side ≤ 2160 px) | 0.864 |
| MV-HEVC | 2K (short side ≤ 1440 px) | 0.6006 |
| MV-HEVC | FHD (short side ≤ 1080 px) | 0.432 |

### Edit Media

The Edit Media feature, as detailed in the [related API documentation](https://www.tencentcloud.com/document/product/1041/37460), is billed in accordance with the aforementioned [General Transcoding](#general-transcoding).

##### Billing Examples

Suppose you used the edit media service on January 1st to merge videos within a COS bucket located in Singapore, specifically video A (10 minutes in duration, with a resolution of 640 × 480) and video B (15 minutes in duration, with a resolution of 1280 × 720), resulting in the creation of video C (25 minutes in duration, encoded in H.264, with a resolution of 1280 × 720).

- The shorter dimension of the output video C is 720 px, and the corresponding general transcoding unit price in the Singapore region is 0.0105 (USD/minute).

On January 2nd, the transcoding fee deducted would be as follows: 25 (minutes) × 0.0105 (USD/minute) = 0.2625 (USD).

## Audio/Video Enhancement

The industry-leading audio and video AI enhancement algorithm and various business scenario application models comprehensively improve the audio and video quality and support distributed real-time image quality enhancement, including Artifacts Removal, Noise Reduction, Color Enhancement, Detail Enhancement, Face Enhancement, SDR2HDR, and other features.

Video enhancement is billed according to the duration of the output file. The unit price (USD/min) is the same regardless of the codec.

> **Note:**Audio/Video enhancement is based on transcoding. Therefore, initiating an audio and video enhancement task will incur two charges: audio/video enhancement + audio/video transcoding (general transcoding or TSC transcoding). For details, please refer to the following [Billing Example](#example).

### Video Enhancement

Billing is based on the duration after audio and video enhancement, with different rates for different resolutions and frame rates. **The billing unit is USD/minute.**

The specific billing details are as follows:

| Enhance Type | Billing Item Name | Resolution | Frame Rate |  |  |
| --- | --- | --- | --- | --- | --- |
|  |  |  | ≤ 30 fps | ≤ 60 fps | ≤ 120 fps |
| Basic Image Quality Enhancement | Artifacts Removal | Resolution ≤ 720P | 0.0176 | 0.0353 | 0.0705 |
|  |  | 720 < Resolution ≤ 1080P | 0.0353 | 0.0705 | 0.1411 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.0705 | 0.1235 | 0.2469 |
|  |  | 2K < Resolution ≤ 4K | 0.1411 | 0.2822 | 0.5644 |
|  |  | 4K < Resolution ≤ 8K | 0.5644 | 1.1287 | 2.2575 |
|  | Comprehensive Enhancement | Resolution ≤ 720P | 0.1411 | 0.2822 | 0.5644 |
|  |  | 720 < Resolution ≤ 1080P | 0.3175 | 0.6349 | 1.2698 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.5644 | 1.1287 | 2.2575 |
|  |  | 2K < Resolution ≤ 4K | 1.2698 | 2.5397 | 5.0794 |
|  |  | 4K < Resolution ≤ 8K | 5.0794 | 10.1587 | 20.3175 |
|  | Diffusion Transformer Enhancement*（*Charges for "Comprehensive Enhancement" + "Super Resolution" + "Noise Reduction" services apply）* | Resolution ≤ 720P | 0.2293 | 0.4409 | 0.9171 |
|  |  | 720 < Resolution ≤ 1080P | 0.5115 | 1.0229 | 2.0458 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.9171 | 1.8166 | 3.6508 |
|  |  | 2K < Resolution ≤ 4K | 2.0458 | 4.0918 | 8.1834 |
|  |  | 4K < Resolution ≤ 8K | 8.1834 | 16.3668 | 32.7337 |
| Extended Enhancement Capability | SDR 2 HDR | - | 0.0705 |  |  |
|  | Frame Interpolation | Resolution ≤ 720P | 0.1058 | 0.2116 | 0.4233 |
|  |  | 720 < Resolution  ≤ 1080P | 0.2381 | 0.4762 | 0.9524 |
|  |  | 1080P ＜ Resolution  ≤ 2K | 0.4233 | 0.8466 | 1.6931 |
|  |  | 2K < Resolution  ≤ 4K | 0.9524 | 1.9048 | 3.8095 |
|  |  | 4K < Resolution ≤ 8K | 3.8095 | 7.6190 | 15.2381 |
|  | Super Resolution | Resolution ≤ 720P | 0.0529 | 0.0882 | 0.1940 |
|  |  | 720 < Resolution ≤ 1080P | 0.1058 | 0.2116 | 0.4233 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.1940 | 0.3704 | 0.7584 |
|  |  | 2K < Resolution ≤ 4K | 0.4233 | 0.8466 | 1.6931 |
|  |  | 4K < Resolution ≤ 8K | 1.6931 | 3.3862 | 6.7725 |
|  | Noise Reduction | Resolution ≤ 720P | 0.0353 | 0.0705 | 0.1587 |
|  |  | 720 < Resolution ≤ 1080P | 0.0882 | 0.1764 | 0.3527 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.1587 | 0.3175 | 0.6349 |
|  |  | 2K < Resolution ≤ 4K | 0.3527 | 0.7055 | 1.4109 |
|  |  | 4K < Resolution ≤ 8K | 1.4109 | 2.8219 | 5.6437 |
|  | Color Enhancement | Resolution ≤ 720P | 0.0176 | 0.0353 | 0.0705 |
|  |  | 720 < Resolution ≤ 1080P | 0.0353 | 0.0705 | 0.1411 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.0705 | 0.1235 | 0.2469 |
|  |  | 2K < Resolution  ≤ 4K | 0.1411 | 0.2822 | 0.5644 |
|  |  | 4K < Resolution ≤ 8K | 0.5644 | 1.1287 | 2.2575 |
|  | Scratches Removal | Resolution ≤ 720P | 0.1764 | 0.3527 | 0.7231 |
|  |  | 720 < Resolution ≤ 1080P | 0.4056 | 0.8113 | 1.6226 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.7231 | 1.4462 | 2.8924 |
|  |  | 2K < Resolution ≤ 4K | 1.6226 | 3.2451 | 6.4903 |
|  |  | 4K < Resolution ≤ 8K | 6.4903 | 12.9806 | 25.9612 |
|  | Detail Enhancement | Resolution ≤ 720P | 0.0071 | 0.0159 | 0.0317 |
|  |  | 720 < Resolution ≤ 1080P | 0.0176 | 0.0353 | 0.0705 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.0317 | 0.0635 | 0.1252 |
|  |  | 2K < Resolution ≤ 4K | 0.0705 | 0.1411 | 0.2822 |
|  |  | 4K < Resolution ≤ 8K | 0.2822 | 0.5644 | 1.1287 |
|  | Low-Light Enhancement | Resolution ≤ 720P | 0.0176 | 0.0353 | 0.0705 |
|  |  | 720 < Resolution ≤ 1080P | 0.0353 | 0.0705 | 0.1411 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.0705 | 0.1235 | 0.2469 |
|  |  | 2K < Resolution ≤ 4K | 0.1411 | 0.2822 | 0.5644 |
|  |  | 4K < Resolution ≤ 8K | 0.5644 | 1.1287 | 2.2575 |
|  | Face Enhancement | Resolution ≤ 720P | 0.1235 | 0.2293 | 0.4762 |
|  |  | 720 < Resolution ≤ 1080P | 0.2646 | 0.5291 | 1.0582 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.4762 | 0.9347 | 1.8871 |
|  |  | 2K < Resolution ≤ 4K | 1.0582 | 2.1164 | 4.2328 |
|  |  | 4K < Resolution ≤ 8K | 4.2328 | 8.4656 | 16.9312 |
|  | Font Enhancement | Resolution ≤ 720P | 0.0705 | 0.1235 | 0.2469 |
|  |  | 720 < Resolution ≤ 1080P | 0.1411 | 0.2646 | 0.5291 |
|  |  | 1080P ＜ Resolution ≤ 2K | 0.2469 | 0.4762 | 0.9524 |
|  |  | 2K < Resolution ≤ 4K | 0.5291 | 1.0582 | 2.1164 |
|  |  | 4K < Resolution  ≤ 8K | 2.1164 | 4.2328 | 8.4656 |

#### **Billing Details**

Charges are based on the resolution and duration of the video after enhancement.

- Billing formula: Video Enhancement Processing Fee = Output file duration (minutes) × Unit Price of different resolutions (USD/minute).
  - For each video enhancement task executed, only one fee is charged.
  - In case of daily billing, the system counts the total seconds per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

#### **Billing Example**

Suppose you used the MPS video enhancement service in Singapore on January 1 to process video resources in the COS bucket, and used the comprehensive enhancement capability to generate a video. It was 100 minutes long and had a resolution of 2560 × 1440 px, at 60 fps. The codec used was H.264. Besides, you used the audio enhancement service and enabled the audio beautification feature, and generated another video that was 100 minutes long.

- For the video with a 2K short side (short side ≤ 1440px) and a frame rate of 60, the unit price of the corresponding comprehensive enhancement sub-capability is 1.1287 (USD/minute).
- Video enhancement relies on video transcoding, which incurs an additional video transcoding fee. The unit price for general transcoding for H.264 at 2K (Singapore) is 0.0355 (USD/minute).
- The unit price of audio beautification is 0.0176 (USD/minute).
- Audio enhancement also relies on audio transcoding, which incurs an additional audio transcoding fee. The unit price for general audio transcoding in Singapore is 0.0019 (USD/minute).

On January 2, the cost you need to pay would be as follows: (1.1287 + 0.0355) (USD/minute) × 100 (minutes) + (0.0176 + 0.0019) (USD/minute) × 100 (minutes) = 118.37 (USD).

### Audio Enhancement

| Billable Item | Price (USD/min) |
| --- | --- |
| Audio noise reduction | 0.0176 |
| Audio separation | 0.0176 |
| Audio equalization | 0.0176 |
| Audio improvement | 0.0176 |

#### **Billing Details**

Audio enhancement is billed daily according to the output duration.

- Billing formula: Audio enhancement fees = Output file duration (minutes) × Unit price of different billing items (USD/minute)
  - Each audio enhancement task is billed only once.
  - In case of daily billing, the system counts the total seconds per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

## Media AI

Intelligent media includes features such as Smart Subtitles, Smart Erase, LLM Summarize, Horizontal-to-Vertical Video Transformation, and Intelligent Identification. With extensive experience in industries such as live streaming, pan-entertainment, and education, it can meet the needs of various scenarios, including short drama going abroad, video conferencing, online education, and platform live streaming.

### Smart Captions and Subtitles

The smart captions and subtitles support ASR/OCR-generated subtitle files, subtitle translation, and other features. See [Integration Instructions](https://www.tencentcloud.com/document/product/1041/54517) for details.

Billing is based on the duration of Smart Captions and Subtitles processing. Billing unit: USD/minute. Detailed pricing is as follows:

| Billing Item | Feature Description | Price (USD/Minute) |
| --- | --- | --- |
| ASR Speech Recognition | Input supports audio files, video files, live streams, and real-time audio streams.ASR recognizes the speech and generates a subtitle file in the source language. | 0.0053 |
| ASR Speech Translation | ASR recognizes the speech and uses a Large Language Model (LLM) to translate it into a specified language, generating a subtitle file in the target language. | 0.0529 |
| OCR Subtitle Extraction | Input supports video files (with hard subtitles embedded in the frames)Leveraging OCR text recognition technology to extract subtitle content from video frames and generate subtitle files. | 0.0896 |
| OCR Subtitle Extraction + Translation | Based on the OCR Extract Subtitles, activate the translation feature.Generate translated language subtitles. | 0.1194 |
| Subtitle Embedding | Renders subtitle onto the video. | 0.0094 |
| Subtitle Translation | The input should be a subtitle file, which is translated into a specified language via an LLM, generating a subtitle file in the target language or a bilingual subtitle file. Duration = End timestamp of the last sentence of the subtitle file – Start timestamp of the first sentence. | 0.0299 |
| Subtitle Translation (Extra Languages) | When a subtitle file is translated into more than one language, an additional fee will be charged for each additional language. | 0.0075 |

> **Note:**If you use the [live subtitling feature](https://www.tencentcloud.com/document/product/267/58144) of Cloud Streaming Services (CSS) to process live streams, in addition to the [live transcoding](https://www.tencentcloud.com/document/product/267/39604) fee, the speech recognition or speech translation fee of Media Processing Service (MPS) will also be incurred.

#### Billing **Details**

Fees are calculated based on the duration of the input file.

- **Billing Formula**: Intelligent Subtitles processing fee = Input file duration (minutes) × Unit price per billing item (USD/minute).
  - Each Smart Captions and Subtitles task incurs a one-time charge.
  - In case of daily billing, the system counts the total seconds per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

#### Billing Example

The specific billing items depend on the processing type, whether translation is enabled, the number of target languages for translation, and other configuration settings.

##### **Example 1:** **Generate Subtitles Based on ASR Is Selected as the Processing Type with** Only the Source Language Recognized and Speech Recognition Fee Charged

On January 1, you performed smart subtitling on a 100-minute video by using Generate Subtitles Based on ASR as the processing type, without enabling translation. This resulted in generating subtitles in the source language.

The speech recognition fee is charged at a unit price of 0.0053 USD/minute. The fee you need to pay on January 2 is calculated as follows: 0.0053 USD/minute × 100 minutes = 0.53 USD.

##### **Example 2:** Generate Subtitles Based on ASR **Is Selected as the Processing Type with** Subtitles Translated to a Target Language and the Speech Translation Fee Charged

On January 1, you performed smart subtitling on a 100-minute video by using Generate Subtitles Based on ASR as the processing type, enabling translation, and selecting a target language for translation. This resulted in generating subtitles in the target language.

The speech translation fee is charged at a unit price of 0.0529 USD/minute. The fee you need to pay on January 2 is calculated as follows: 0.0529 USD/minute × 100 minutes = 5.29 USD.

##### **Example 3:** Translate Subtitle Files **Is Selected as the Processing Type** with Subtitles Translated to a Target Language and the Subtitle Translation Fee Charged

On January 1, you translated a 100-minute subtitle file by using Subtitle Translation as the processing type and selecting a target language for translation. This resulted in generating subtitles in the target language.

The subtitle translation fee is charged at a unit price of 0.0299 USD/minute. The fee you need to pay on January 2 is calculated as follows: 0.0299 USD/minute × 100 minutes = 2.99 USD.

##### **Example 4:** Generate Subtitles Based on ASR Is Selected as the Processing Type with More Than One Target Language Selected and the Subtitle Translation (Extra Languages) Fee Charged for Each Additional Language

Billing formula: Speech translation fee × 1 + Subtitle translation (extra languages) fee × (n – 1), where n is the number of target languages for translation.

On January 1, you performed smart subtitling on a 100-minute video in Chinese, with subtitles generated in four target languages: English, Japanese, Korean, and French.

- The speech translation fee is charged for the first language at a unit price of 0.0529 USD/minute.
- The subtitle translation (extra languages) fee is charged for the other three languages at a unit price of 0.0075 USD/minute.

The fee you need to pay on January 2 is calculated as follows: 0.0529 USD/minute × 100 minutes × 1 + 0.0075 USD/minute × 100 × 3 = 7.54 USD.

##### **Example 5: Translate Subtitle Files Is Selected as the Processing Type** with More Than One Target Language Selected and the Subtitle Translation (Extra Languages) Fee Charged for Each Additional Language

Billing formula: Subtitle translation fee × 1 + Subtitle translation (extra languages) fee × (n – 1), where n is the number of target languages.

On January 1, you translated a 100-minute subtitle file into four target languages: English, Japanese, Korean, and French.

- The subtitle translation fee is charged for the first language at a unit price of 0.0299 USD/minute.
- The subtitle translation (extra languages) fee is charged for the other three languages at a unit price of 0.0075 USD/minute.

The fee you need to pay on January 2 is calculated as follows: 0.0299 USD/minute × 100 minutes × 1 + 0.0075 USD/minute × 100 × 3 = 5.24 USD.

### Smart Erase

Smart Erase can achieve features such as watermark erasure, specified area erasure, subtitle erasure, and sensitive information blurring. Click to view [Access Instructions](https://www.tencentcloud.com/document/product/1041/58269).

Charging is based on the duration of the video processed by Smart Erase, regardless of the codec. Billing unit: USD/minute. The specific billing details are as follows:

| Billable Item | Description | Resolution | Price (USD/min) |
| --- | --- | --- | --- |
| Watermark Removal - Basic Version | Basic version.Blur the watermark, suitable for animations or videos with a clean background. | 8K (Short side ≤ 4320px) | 0.41 |
|  |  | 4K (Short side ≤ 2160px) | 0.21 |
|  |  | 2K (Short side ≤ 1440px) | 0.1 |
|  |  | FHD (Short side ≤ 1080px) | 0.05 |
|  |  | HD (Short side ≤ 720px) | 0.03 |
|  |  | SD (Short side ≤ 480px) | 0.02 |
| Watermark Removal - Advanced Version | Advanced versionThe watermark removal feature is enhanced, particularly suitable for short dramas and other videos with a realistic style. | 4K (Short side ≤ 2160px) | 0.8955 |
|  |  | 2K (Short side ≤ 1440px) |  |
|  |  | FHD (Short side ≤ 1080px) | 0.4478 |
|  |  | HD (Short side ≤ 720px) | 0.2239 |
| Subtitle Removal | Remove text subtitles from the video frames.Supports seamless effects. | 4K (Short side ≤ 2160px) | 0.8955 |
|  |  | 2K (Short side ≤ 1440px) |  |
|  |  | FHD (Short side ≤ 1080px) | 0.4478 |
|  |  | HD (Short side ≤ 720px) | 0.2239 |
| Privacy Protection Processing (Face and License Plate) | Identify faces and license plates within video frames, and apply blurring or mosaic effects to safeguard privacy information. | 4K (Short side ≤ 2160px) | 0.597 |
|  |  | 2K (Short side ≤ 1440px) |  |
|  |  | FHD (Short side ≤ 1080px) | 0.2985 |
|  |  | HD (Short side ≤ 720px) | 0.1493 |
| OCR Extract Subtitles | Leveraging OCR (Optical Character Recognition), extract subtitle content from video frames to generate subtitle files. | - | 0.0896 |
| OCR Extract Subtitles and Translate | Based on the OCR Extract Subtitles, activate the translation feature.Generate translated language subtitles. | - | 0.1194 |
| Subtitle Embedding | Renders the translated subtitle onto the video. | - | 0.0094 |

#### **Billing Details**

Smart Erase service is billed based on the output file duration and resolution after using the service. The video specification depends on the resolution range of the video short side.

- Billing formula: Smart Erase Fees = Output Video Duration (minutes) × Unit Price of Resolution Range of Output Video Short Side (USD/minute)
  - Each Smart Erase task is billed only once.
  - In case of daily billing, the system counts the total seconds per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

#### **Billing Example**

Suppose you used the MPS Smart Erase service and enabled the Subtitle Removal sub-capability to process two videos that were 100 minutes long and had a resolution of 2560 × 1440 px and 1280 × 640 px respectively.

- For the video with a resolution of 2560 × 1440 px, the unit price of the Subtitle Removal sub-capability is 0.8955 (USD/minute).
- For the video with a resolution of 1280 × 640 px, the unit price of the Subtitle Removal sub-capability is 0.2239 (USD/minute).

On January 2, the cost you need to pay would be as follows: 0.8955 (USD/minute) × 100 (minutes) + 0.2239 (USD/minute) × 100 (minutes) = 111.94 (USD).

### AI Dubbing

The AI Dubbing feature takes seamless videos, translated language subtitles, and speaker-tagged files as input. It replaces the original audio with AI-generated voiceovers in the target language and embeds translated subtitles onto the video. Click to view [AI Dubbing Tutorial](https://www.tencentcloud.com/document/product/1041/74378).

| Billing Item | Description | Unit Price (USD/minute) |
| --- | --- | --- |
| AI Dubbing (Standard Voice) | Replaces the original audio with AI-generated voiceovers in the target language. Standard voice, currently supports Chinese, English, and Japanese. | 0.0746 |
| AI Dubbing (Cloned Voice) | Replaces the original audio with AI-generated voiceovers in the target language. Cloned voice, leveraging cutting-edge AI voice cloning technology to replicate vocal characteristics. Supports dozens of languages. | 1.34 |
| Subtitle Embedding | Renders the translated subtitle onto the video. | 0.0094 |

#### **Billing Details**

Charges are based on the duration of the output file after AI dubbing.

- **Billing Formula**: AI Dubbing Cost = Output File Duration (minutes) × Unit Price of Relevant Billing Items (USD/minute)
  - Each AI dubbing task incurs a one-time charge.
  - For daily billing, the system aggregates the total output duration in seconds per day. At the end of each day, the total seconds are converted to minutes and rounded up (any partial minute is billed as a full minute).
  - For monthly billing, the system aggregates the total output duration in seconds per month. On the 1st of each month, the total seconds are converted to minutes and rounded up (any partial minute is billed as a full minute).

#### **Billing Example**

On January 1st, you used the AI Dubbing service with cloned voice and enabled subtitle embedding, processing 100 minutes of video.

- AI Dubbing (Cloned Voice): Unit price = 1.34 USD/minute
- Subtitle Embedding: Unit price = 0.0094 USD/minute

**Total Cost on January 2nd**: 1.34 × 100 + 0.0094 × 100 = 134.94 USD

### Video Localization

The Video Localization feature integrates multiple powerful capabilities of MPS, including subtitle removal, extraction, translation, embedding, and AI dubbing. It supports two modes: **Subtitle-Level Localization** and **Dubbing-Level Localization**.

#### **Subtitle-Level Localization**

Translates the original subtitles on the video into the target language. For integration, refer to [Smart Removal - Subtitle-Level Localization Integration](https://www.tencentcloud.com/document/product/1041/73595#subtitle-level-localization-(simultaneous-subtitle-removal-.2B-ocr-extraction-.2B-subtitle-translation-.2B-subtitle-embedding)).

| Billing Item | Description | Resolution | Unit Price (USD/minute) |
| --- | --- | --- | --- |
| Subtitle Removal | - Removes text subtitles from the video. - Supports seamless processing. | 4K (short edge ≤ 2160px) | 0.8955 |
|  |  | 2K (short edge ≤ 1440px) | 0.8955 |
|  |  | Full HD (FHD, short edge ≤ 1080px) | 0.4478 |
|  |  | HD (short edge ≤ 720px) | 0.2239 |
| OCR Subtitle Extraction + Translation | - Extracts subtitles via OCR and translates them. - Generates subtitles in the target language. | - | 0.1194 |
| OCR Subtitle Extraction + Translation + Embedding | - Extracts subtitles via OCR, translates them, and embeds them. - Generates and embeds subtitles in the target language onto the video. | - | 0.1288 |

#### **Billing Example**

On January 1st, you used the Subtitle-Level Localization service to process a 100-minute video (1920 × 1080 resolution) with original subtitles, performing subtitle removal, OCR extraction, translation, and embedding (without AI dubbing).

- Subtitle Removal (1080p): 0.4478 USD/minute
- OCR Extraction + Translation + Embedding: 0.1288 USD/minute

**Total Cost on January 2nd**: 0.4478 × 100 + 0.1288 × 100 = **57.66 USD**

#### **Dubbing-Level Localization**

Extends Subtitle-Level Localization by replacing the original audio with translated voiceovers. For integration, refer to [Dubbing-Level Video Localization Tutorial](https://www.tencentcloud.com/document/product/1041/74090).

| Billing Item | Description | Resolution | Unit Price (USD/minute) |
| --- | --- | --- | --- |
| Subtitle Removal | - Removes text subtitles from the video. - Supports seamless processing. | 4K (short edge ≤ 2160px) | 0.8955 |
|  |  | 2K (short edge ≤ 1440px) | 0.8955 |
|  |  | Full HD (FHD, short edge ≤ 1080px) | 0.4478 |
|  |  | HD (short edge ≤ 720px) | 0.2239 |
| OCR Subtitle Extraction + Translation | - Extracts the original subtitle via OCR and translates it.- Generates a subtitle file in the target language. | - | 0.1194 |
| OCR Subtitle Extraction + Translation + Embedding | - Extracts the original subtitle via OCR and translates it. And embeds the subtitle in the target language onto the video. | - | 0.1288 |
| ASR Speech Translation | - Extracts the original subtitle via ASR and translates it.- Generates a subtitle file in the target language. | - | 0.0529 |
| ASR Speech Translation + Embedding | - Extracts the original subtitle via ASR and translates it. And embeds the subtitle in the target language onto the video. | - | 0.0623 |
| AI Dubbing (Standard Voice) | - Replaces the original audio with AI-generated voiceovers in the target language. - Standard voice, currently supports Chinese, English, and Japanese. | - | 0.0746 |
| AI Dubbing (Cloned Voice) | - Replaces the original audio with AI-generated voiceovers in the target language.- Cloned voice, leveraging cutting-edge AI voice cloning technology to replicate vocal characteristics. Supports dozens of languages. | - | 1.34 |

#### **Billing Example**

On January 1st, you used the Dubbing-Level Localization service to process a 100-minute video (1920 × 1080 resolution) with original subtitles, performing subtitle removal, OCR extraction, translation, embedding, and AI dubbing (cloned voice).

- Subtitle Removal (1080p): 0.4478 USD/minute
- OCR Extraction + Translation + Embedding: 0.1288 USD/minute
- AI Dubbing (Cloned Voice): 1.34 USD/minute

**Total Cost on January 2nd**:0.4478 × 100 + 0.1288 × 100 + 1.34 × 100 = 191.66 USD

### Video Splitting

The Video Splitting feature can segment a complete long video, such as splitting full news broadcast material into multiple news event videos. Video Splitting can significantly improve the quality of news and sports Video Splitting, promoting secondary creation, and saving labor and hardware costs. Click to view [Access Instructions](https://www.tencentcloud.com/document/product/1041/66044).

The specific billing details are as follows:

| Billable Item | Chinese Mainland | Hong Kong (China), Tokyo, Frankfurt, Silicon Valley, Virginia | Singapore, Seoul, Bangkok |
| --- | --- | --- | --- |
| Video Splitting | 0.0071 |  |  |
| Video Splitting - Advanced Version | 0.0511 | 0.0572 | 0.0562 |

#### **Billing Details**

> **Note:**The Video Splitting feature supports model training based on the customer's video scenario to achieve splitting results of higher quality. This service will be billed according to the "Video Splitting - Advanced Edition".If customized model training is not involved, the service can be billed according to "Video Splitting". Please refer to the actual business quotation.

Billing is based on the  **Source Video**  duration.

- Billing formula: Video Splitting Fees = Video  **Source Video**  Duration (minutes) × Unit Price of Video Splitting or Video Splitting (Advanced Version) (USD/minute)
  - Each Video Splitting task is billed only once.
  - In case of daily billing, the system counts the total seconds of the  **Source Video**  per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds of the  **Source Video**  per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

### LLM Summarize

Paragraph topics and summary information in the video are generated through the LLM capability, applicable to various scenarios such as meetings, training, and courses. Click to view [Access Instructions](https://www.tencentcloud.com/document/product/1041/66042).

| Billable Item | Chinese Mainland | Hong Kong (China), Tokyo, Frankfurt, Silicon Valley, Virginia | Singapore, Seoul, Bangkok |
| --- | --- | --- | --- |
| LLM Summarize | 0.0511 | 0.0572 | 0.0562 |

#### **Billing Details**

Billing is based on the  **Source Video**  duration.

- Billing formula: LLM Summarize Fees = Video  **Source Video**  Duration (Minutes) × Unit Price of LLM Summarize (USD/Minute)
  - Each LLM Summarize task is billed only once.
  - In case of daily billing, the system counts the total seconds of the  **Source Video**  per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds of the  **Source Video**  per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

### Intelligent Highlights

Intelligent algorithms are used to automatically capture and generate highlights in a video, providing users with quick review and sharing. Click to view [Access Instructions](https://www.tencentcloud.com/document/product/1041/66043).

| Billable Item | Chinese Mainland | Hong Kong (China), Tokyo, Frankfurt, Silicon Valley, Virginia | Singapore, Seoul, Bangkok |
| --- | --- | --- | --- |
| Intelligent Highlights | 0.0176 |  |  |
| Intelligent Highlights - Advanced Version | 0.0511 | 0.0572 | 0.0562 |

#### **Billing Details**

> **Note:**The Intelligent Highlights feature supports model training based on the customer's video scenario to achieve highlights of higher quality. This service will be billed according to the "Intelligent Highlights - Advanced Version".If customized model training is not involved, the service can be billed according to "Intelligent Highlights". Please refer to the actual business quotation.

Billing is based on the  **Source Video**  duration.

- Billing formula: Intelligent Highlights Fees = Video **Source Video**  Duration (Minutes) × Unit Price of Intelligent Highlights or Intelligent Highlights (Advanced Edition) (USD/Minute)
  - Each Intelligent Highlights task is billed only once
  - In case of daily billing, the system counts the total seconds of the  **Source Video**  per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds of the  **Source Video**  per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

### Horizontal-to-Vertical Video Transformation

Horizontal-to-vertical video transformation is not just simple rotation; it identifies the Region of Interest (ROI) and clips the video to a suitable ratio for playback on mobile devices. Horizontal-to-vertical video transformation provides the capability to generate short videos in batches and convert existing horizontal video resources into vertical video resources. Click to view [Access Instructions](https://www.tencentcloud.com/document/product/1041/66045).

| Billable Item | Chinese Mainland | Hong Kong (China), Tokyo, Frankfurt, Silicon Valley, Virginia | Singapore, Seoul, Bangkok |
| --- | --- | --- | --- |
| Horizontal-to-Vertical Video Transformation | 0.0511 | 0.0572 | 0.0562 |

#### **Billing Details**

Billing is based on the  **Source Video**  duration.

- Billing formula: Horizontal-to-Vertical Video Transformation Fees = Video  **Source Video**  Duration (Minutes) × Unit Price of Horizontal-to-Vertical Video Transformation (USD/Minute)
  - Each Horizontal-to-vertical video transformation task is billed only once.
  - In case of daily billing, the system counts the total seconds of the  **Source Video**  per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds of the  **Source Video**  per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

### Intelligent Identification

> **Note:**Intelligent identification service is billed according to the [Intelligent Identification Billing Items (by Sub-Capabilities)] by default, and the fees are calculated based on which sub-capabilities are used. If you want to adjust to billing based on the unified [Intelligent Identification] regardless of which sub-capabilities are actually used, please contact our business team.

The intelligent identification feature supports recognizing video content with AI technologies, including text recognition, speech recognition, opening and closing credits recognition, and intelligent frame-by-frame tagging. The billing unit is USD/minute.

**Billing rules:**

- Payment mode: Pay-as-you-go.
- If the original duration is less than one minute, it will be calculated as one minute.

**The specific billing details are as follows:**

| Billable Item | Chinese Mainland | Hong Kong (China), Tokyo, Frankfurt, Silicon Valley, Virginia | Singapore, Seoul, Bangkok |
| --- | --- | --- | --- |
| Intelligent identification | 0.0511 | 0.0572 | 0.0572 |

Billing formula: Intelligent identification fees = Source video duration (minutes) × Unit price of intelligent identification (USD/minute)

#### Intelligent Identification Billing Items (by Sub-Capabilities)

The intelligent identification feature supports recognizing video content with AI technologies, including face recognition, text recognition, speech recognition, speech translation, and object recognition.  **The billing unit is USD/minute.**

The specific billing details are as follows:

| Billing Item | Price (USD/min) |
| --- | --- |
| Face recognition | 0.0088 |
| Text recognition | 0.0176 |
| Speech recognition | 0.0053 |
| Speech translation | 0.0529 |
| Music Recognition | 0.44 |
| Object recognition (Basic fees*)*If customized model training is involved, an additional fee for [Object Recognition Customized Content](#recognition) will be charged. | 0.0176 |
| Highlight recognition | 0.0265 |

#### **Billing Details**

Billing is based on the  **Source Video**  duration.

- **Billing formula:** Intelligent identification fees = Source video duration (minutes) × Atomic item unit price of intelligent identification (USD/minute)
  - For each intelligent identification task executed, only one fee is charged.
  - In case of daily billing, the system counts the total seconds of the  **Source Video**  per day. The total seconds of the previous day are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).
  - In case of monthly billing, the system counts the total seconds of the  **Source Video**  per month. On the first day of each month, the total seconds of the previous month are converted into minutes for billing, rounded up (If the duration is less than one minute, it will be counted as one minute).

#### **Object Recognition Customized Content**

This feature recognizes the specific content in the video. The specific billing details are as follows::

| Billable Item | Price (USD/item) |
| --- | --- |
| Object recognition (customized content) | 8800 |

> **Note:**The object recognition customization fee is only for training. When it is used in a formal environment, billing is made based on the object recognition duration.

### Intelligent Analysis

> **Note:**The intelligent analysis feature is billed based on [Intelligent Analysis Billing Items (by sub-capabilities)] by default, and the fees are calculated based on which sub-capabilities are used. If you want to adjust to billing based on the unified [Intelligent Analysis] regardless of which sub-capabilities are actually used, please contact our business team.

The intelligent analysis feature supports analyzing and processing video content with AI technologies and mass samples, including intelligent tagging, intelligent classification, intelligent thumbnail, intelligent highlights, intelligent video summary, and segmentation recognition. The billing unit is USD/minute.

**Billing rules:**

- Payment method: Pay-as-you-go.
- If the original duration is less than one minute, it will be calculated as one minute.

**The specific billing details are as follows:**

| Billable Item | Chinese Mainland | Seoul, Bangkok | Hong Kong (China), Tokyo, Frankfurt | Silicon Valley, Virginia | Singapore |
| --- | --- | --- | --- | --- | --- |
| Intelligent analysis | 0.0511 | 0.0562 | 0.0572 | 0.0572 | 0.0562 |

Billing formula: Intelligent analysis fees = Source video duration (minutes) × Unit price of intelligent analysis (USD/minute)

#### Intelligent Analysis Billing Items (by sub-capabilities)

The intelligent analysis feature supports analyzing and processing video content with video AI technologies and mass samples, including video tagging, video classification, intelligent thumbnail, frame-by-frame tagging, video segmentation, highlights, and opening and closing credits analysis.  **The billing unit is USD/minute.**

| Billing Item | Price (USD/min) |
| --- | --- |
| Video tagging | 0.0071 |
| Video classification | 0.0071 |
| Smart cover | 0.0071 |
| Frame-by-frame tagging | 0.0265 |
| Video splitting | 0.0071 |
| Intelligent highlights | 0.0176 |
| Opening and closing credits analysis | 0.0026 |
| Music Analysis | 0.0746 |

**Billing Details**

- Billing formula: Intelligent analysis fees = Source video duration (minutes) × Unit price of intelligent analysis (USD/minute)
- For each intelligent analysis task executed, only one fee is charged. Within a billing cycle, if the duration is less than one minute, it will be calculated as one minute.

### Intelligent Auditing

The audio/video intelligent auditing feature supports smart moderation of images, voice, and text in the video content, to filter any inappropriate content and output the result as required by the customer. Billing is based on the services used by the user and the duration of intelligent auditing. The billing unit is USD/minute.

**Billing rules:**

- Payment mode: Pay-as-you-go.
- If the duration is less than one minute, it will be calculated as one minute.

**The specific billing details are as follows:**

| Billable Item | Billed By | Price |
| --- | --- | --- |
| Intelligent auditing | Source file duration | 0.016 |

Billing formula: Intelligent auditing fees = Source video duration (minutes) × Unit price of intelligent auditing (USD/minute)

## Media Quality Inspection

The media quality inspection feature supports inspecting the audio and video quality. Billing is based on the service used by the user and the duration of video quality inspection.  **The billing unit is USD/minute.**The specific billing details are as follows:

| Billable Item | Billed By | Price (USD/min) |
| --- | --- | --- |
| Media quality inspection | The duration of the file checked | 0.0265 |

#### **Billing Details**

- Billing formula : Media quality inspection fees = Source video duration (minutes) × Unit price of media quality inspection (USD/minute)
- If the duration is less than one minute, it will be calculated as one minute.

## Screenshot

MPS can take screenshots from a video and save them in COS. The Screenshot feature is billed according to the number of screenshots taken. The specific billing details are as follows:

| Item | Billed By | Price (USD/1,000 screenshots) |
| --- | --- | --- |
| Screenshot | Number of screenshots | 0.0176 |

#### Billing Details

- Billing formula: Screenshot fees = The number (thousand) of screenshots taken × Unit price (USD/1,000 screenshots)
- The number of screenshots is calculated each day and is rounded up to the nearest thousand.

## Animated screenshot generation

MPS can take animated screenshots from a video. Using this feature will incur animated screenshot generation fees. The billing unit is USD/minute. Below are the pricing details:

| Output Resolution | Price (USD/min) |
| --- | --- |
| 4K (short side ≤ 2160 px) | 0.0421 |
| 2K (short side ≤ 1440 px) | 0.0206 |
| FHD (short side ≤ 1080 px) | 0.0095 |
| HD (short side ≤ 720 px) | 0.0049 |
| SD (short side ≤ 480 px) | 0.0024 |

#### **Billing Details**

- Billing formula: Animated screenshot generation fees = Screenshot duration (minutes) × Unit price (USD/minute)
- Each screenshot generation task is billed only once. If the duration is less than one minute, it will be calculated as one minute.

## **Digital Watermarks**

### Add Digital Watermark

| Billing Item | Digital Watermark Version | Output Resolution | Output Frame Rate | Price (USD/Minute) |
| --- | --- | --- | --- | --- |
| Add Digital Watermark | NAGRA NexGuard | SD (short side ≤ 480 px) | Not differentiated | 0.43 |
|  |  | HD (short side ≤ 720 px) |  | 0.48 |
|  |  | FHD (short side ≤ 1080 px) |  | 0.51 |
|  |  | 2K (short side ≤ 1440 px) |  | 0.54 |
|  |  | 4K (short side ≤ 2160 px) |  | 0.58 |
|  |  | 8K (short side ≤ 4320 px) |  | 0.59 |
|  | Basic digital watermarks | SD (short side ≤ 480 px) | 30 FPS | 0.056 |
|  |  | HD (short side ≤ 720 px) |  | 0.070 |
|  |  | FHD (short side ≤ 1080 px) |  | 0.084 |
|  |  | 2K (short side ≤ 1440 px) |  | 0.098 |
|  |  | 4K (short side ≤ 2160 px) |  | 0.105 |
|  |  | 8K (short side ≤ 4320 px) |  | 0.120 |
|  |  | SD (short side ≤ 480 px) | 60 FPS | 0.112 |
|  |  | HD (short side ≤ 720 px) |  | 0.139 |
|  |  | FHD (short side ≤ 1080 px) |  | 0.167 |
|  |  | 2K (short side ≤ 1440 px) |  | 0.195 |
|  |  | 4K (short side ≤ 2160 px) |  | 0.209 |
|  |  | 8K (short side ≤ 4320 px) |  | 0.240 |
|  |  | HD (short side ≤ 720 px) | 120 FPS | 0.278 |
|  |  | FHD (short side ≤ 1080 px) |  | 0.334 |
|  |  | 2K (short side ≤ 1440 px) |  | 0.390 |
|  |  | 4K (short side ≤ 2160 px) |  | 0.418 |
|  |  | 8K (short side ≤ 4320 px) |  | 0.480 |

#### **Billing Instructions**

Billing formula: Add Digital Watermark fee = Output video duration (minutes) × Unit price for add digital watermark (USD/minute) + Output video duration (minutes) × Unit price for audio/video transcoding (USD/minute).

- Digital Watermark Addition depends on the Audio/Video Transcoding feature. When initiating a transcoding task, you need to associate a digital watermark template to apply the watermark. As a result, both add digital watermark and audio/video transcoding fees will be incurred.
- If the billing cycle is daily, the system calculates the total number of seconds per day. The total number of seconds from the previous day is converted into minutes for billing, rounded up (any part of a minute is charged as one full minute).
- If the billing cycle is monthly, the system calculates the total number of seconds per month. On the first day of each month, the total number of seconds from the previous month is converted into minutes for billing, rounded up (any part of a minute is charged as one full minute).

#### **Billing Example**

On January 1, you used MPS to initiate a standard video transcoding task and added a basic digital watermark. The video was output in H.264 encoding format, with a resolution of 1920 × 1080 px and 60 FPS, for a duration of 100 minutes.

- The unit price of standard video transcoding (H.264 and 1920 × 1080 px) is 0.0095 USD/minute.
- The unit price for adding basic digital watermarks (1920 × 1080 px and 60 FPS) is 0.167 USD/minute.

The fee you need to pay on January 2 is calculated as follows: 0.0095 USD/minute × 100 minutes + 0.167 USD/minute × 100 minutes = 17.65 USD.

### Extract Digital Watermark

| Billing Item | Digital Watermark Version | Frame Rate | Price (USD/Time) |
| --- | --- | --- | --- |
| Extract Digital Watermark | NAGRA NexGuard | Not differentiated | 37 |
|  | Basic digital watermarks | 30FPS | 2.1 |
|  |  | 60FPS | 4.2 |
|  |  | 120FPS | 8.4 |

> **Note:**The console and API only support the Basic Digital Watermarks extraction feature. To extract NAGRA NexGuard Digital Watermarks, contact the business team or [submit a ticket](https://console.tencentcloud.com/workorder/category), and attach the video file involving suspected unauthorized playback.

#### **Billing Instructions**

Billing formula: Extract Digital Watermark fee = Number of calls × Unit price for extract digital watermark (USD/time).

Each extraction task supports only a single video, and the fee is charged based on the number of extractions.

#### **Billing Example**

On January 1, you used MPS to perform basic digital watermark extraction once on a 10-minute video with a resolution of 1920 × 1080 px and 60 FPS.

The unit price for extracting basic digital watermarks from a 60 FPS video is 4.2 USD/time. The fee you need to pay on January 2 is calculated as follows: 1 × 4.2 = 4.2 USD.

## LVB Recording

By using the media processing live stream recording function, you only need to provide the video stream address, and the recording result can be stored in the object storage COS. Using the recording function will incur charges, **and the billing unit is USD/minute.** The specific billing details are as follows:

| Item | Billed By | Price (USD/min) |
| --- | --- | --- |
| LVB recording | Stream record duration | 0.0032 |

#### Billing Details

- Billing formula: Stream record fees = Stream record duration (minutes) × Unit price (USD/minute)
- Duration is rounded up to the nearest minute.

## Image Processing

Image processing enables functionalities such as image compression, facial enhancement, detail enhancement, and color enhancement. Charges for image processing are based on the resolution tier of the images and the number of images processed.

> **Note：**Image processing is billed based on the resolution of the output image.

| Billable Item | Specification | Price（USD/pic） |
| --- | --- | --- |
| Image Compression (Format Conversion) | All resolutions | 0.00005 |
| Advanced Image Compression(Format HEIF/TPG/ASTC/AVIF/SVG) | Short side ≤ 720px | 0.00015 |
|  | 720px < Short side ≤ 1080px | 0.000225 |
|  | 1080px < Short side ≤ 1440px | 0.00027 |
|  | 1440px < Short side ≤ 2160px | 0.0003 |
|  | 2160px < Short side ≤ 4320px | 0.000375 |
| Image Watermark Addition | All resolutions | 0.003 |
| Image Enhancement | Short side ≤ 720px | 0.003 |
|  | 720px < Short side ≤ 1080px | 0.006 |
|  | 1080px < Short side ≤ 1440px | 0.012 |
|  | 1440px < Short side ≤ 2160px | 0.024 |
|  | 2160px < Short side ≤ 4320px | 0.048 |
| Image Super-Resolution | Short side ≤ 720px | 0.003 |
|  | 720px < Short side ≤ 1080px | 0.006 |
|  | 1080px < Short side ≤ 1440px | 0.012 |
|  | 1440px < Short side ≤ 2160px | 0.024 |
|  | 2160px < Short side ≤ 4320px | 0.048 |
| Image Clarity Score | Short side ≤ 720px | 0.0015 |
|  | 720px < Short side ≤ 1080px | 0.003 |
|  | 1080px < Short side ≤ 1440px | 0.006 |
|  | 1440px < Short side ≤ 2160px | 0.012 |
|  | 2160px < Short side ≤ 4320px | 0.024 |
| Remove Image Watermark | Short side ≤ 720px | 0.0015 |
|  | 720px < Short side ≤ 1080px | 0.003 |
|  | 1080px < Short side ≤ 1440px | 0.006 |
|  | 1440px < Short side ≤ 2160px | 0.012 |
|  | 2160px < Short side ≤ 4320px | 0.024 |
| Advanced Image Edit | 720P（Short side ≤ 720px） | 0.015 |
|  | 1080P（720px < Short side ≤ 1080px） | 0.03 |
|  | 2K（1080px < Short side ≤ 1440px） | 0.06 |
|  | 4K（1440px < Short side ≤ 2160px） | 0.12 |
|  | 8K（2160px < Short side ≤ 4320px） | 0.24 |
| AI processing of images | Short side ≤ 720px | 0.046 |
|  | 720px < Short side ≤ 1080px | 0.135 |
|  | 1080px < Short side ≤ 1440px | 0.135 |
|  | 1440px < Short side ≤ 2160px | 0.24 |

## Video Evaluation

The video evaluation feature currently supports video quality evaluation and BD-rate evaluation. Users can create evaluation tasks on the console video evaluation page to compare the quality of video transcoding and the effect of transcoding templates, and support visualized data result display. Below are the pricing details:

| Billable Item | Billing Mode | Price (USD/1,000 frames) |
| --- | --- | --- |
| Transcoding Evaluation | Charged by the number of evaluated frames | 0.105 |

#### Billing Details

- **Billing Formula:**Evaluation Cost = Total evaluation frames (frames)/1000 × Unit price of evaluation  (USD/1,000 frames)
- **Source video frames are not included in the total evaluation frames.**
- **For multiple contrast videos, or various evaluation methods, the evaluation frame count will be recalculated.**

## AI-Generated Content (AIGC)

AIGC (Artificial Intelligence Generated Content) leverages intelligent content creation capabilities powered by multimodal large models. It enables the generation of video and image outputs by processing input content such as text, images, and videos. MPS integrates multiple large model vendors to provide a one-stop solution.。

### AI Video Generation

When using AI video generation feature through the Media Processing Service, the billing duration is calculated based on the output video duration, with charges applied per second.

| Model name and version | Specification & Price（USD/Second） |  |  |  |
| --- | --- | --- | --- | --- |
|  | 720P | 1080P | 2K | 4K |
| HY Video 1.5 | 0.046 | 0.077 | 0.115 | 0.172 |
| Hailuo02（Minimax02） | 0.044 | 0.093 | 0.133 | 0.200 |
| Hailuo2.3（Minimax2.3） | 0.044 | 0.077 | 0.124 | 0.200 |
| Hailuo2.3 Fast（Minimax2.3 Fast） | 0.030 | 0.051 | 0.077 | 0.116 |
| Kling2.1 | 0.053 | 0.093 | 0.133 | 0.200 |
| Kling2.5 Pro | 0.046 | 0.077 | 0.115 | 0.172 |
| Kling2.6 | - | 0.077 | 0.115 | 0.172 |
| Kling2.6（with sound） | - | 0.154 | 0.231 | 0.346 |
| KlingO1 | 0.138 | 0.185 | 0.277 | 0.415 |
| vidu q2 | 0.049 | 0.072 | 0.108 | 0.162 |
| vidu q2-pro | 0.054 | 0.108 | 0.154 | 0.231 |
| vidu q2-turbo | 0.039 | 0.072 | 0.108 | 0.162 |
| vidu q2-pro reference to video | 0.0563 | 0.1438 | 0.2157 | 0.3236 |
| vidu q3-pro | 0.1500 | 0.1600 | 0.1920 | 0.2304 |
| Wan 2.2 | - | 0.093 | 0.133 | 0.200 |
| MingMou1.0 | 0.046 | 0.077 | 0.115 | 0.172 |

### AI Image Generation

The media processing product invokes the AI image generation function, and the number of successfully generated images is counted, with the billing unit being per image.

| Model name and version | Specification & Price（USD/Image） |  |  |  |
| --- | --- | --- | --- | --- |
|  | 720P | 1080P | 2K | 4K |
| HY Image 3.0 | 0.031 | 0.031 | 0.043 | 0.055 |
| Qwen Image Edit | 0.046 | 0.046 | 0.058 | 0.071 |
| MingMou1.0 | 0.046 | 0.046 | 0.058 | 0.071 |
| vidu q2 text to image | 0.030 | 0.030 | 0.040 | 0.050 |
| vidu q2 reference to image（with 1～3 reference images） | 0.040 | 0.040 | 0.060 | 0.070 |
| vidu q2 reference to image（with 4～7 reference images） | 0.050 | 0.050 | 0.100 | 0.150 |
| Kling 2.0 text to image | 0.016 | 0.016 | 0.016 | 0.0416 |
| Kling 2.1 text to image | 0.016 | 0.016 | 0.016 | 0.0416 |
| Kling 2.0 image to image | 0.032 | 0.032 | 0.0448 | 0.0576 |
| Kling 2.0 reference to image | 0.064 | 0.064 | 0.0768 | 0.0896 |
| Kling 2.1 reference to image | 0.064 | 0.064 | 0.0768 | 0.0896 |


---
*Source: [https://www.tencentcloud.com/document/product/1041/49204](https://www.tencentcloud.com/document/product/1041/49204)*
