# Announcement on the Price Adjustment of CSS Audio/Video Enhancement Feature

Starting from October 1, 2023, CSS will charge for Audio/Video Enhancement based on enhancement features, resolution, and frame rate dimensions, to meet your needs for using individual or multiple enhancement features separately and billing them individually.

## Notes

- The adjusted price will take effect from 00:00 on October 1, 2023. That is, from 00:00 on October 1, 2023, Audio/Video Enhancement will be billed separately based on features, resolution, and frame rate dimensions, and the bill will be issued on October 2.
- The original billing item included both Top Speed Codec Transcoding (TSC Transcoding) fees and Audio/Video Enhancement fees. After the adjustment, the billing item will only apply to Audio/Video Enhancement separately, while the TSC Transcoding fees will be billed separately.
- After the adjustment, the Top Speed Codec Transcoding Package can still be used to deduct the TSC Transcoding usage, but it cannot be used to deduct the Audio/Video Enhancement usage.
- If you have a special agreement with Tencent Cloud regarding product prices, you can contact us through your business representative or by [Submit a Ticket](https://console.tencentcloud.com/workorder)to determine the specific strategy for implementing subsequent prices.

## Audio/Video enhancement

### Billing Overview

- Billing Item: Audio/Video Enhancement (prices vary based on enhancement features, resolution, and frame rate).
- Billing Rules: By default, it is daily billing. The fees are calculated based on the Audio/Video Enhancement features used and the enhanced resolution and frame rate. The billing is calculated by multiplying the duration of Audio/Video Enhancement at a specific resolution within a natural day by the corresponding unit price.

### Billing formula

Audio/Video Enhancement cost = Audio/Video Enhancement duration × corresponding enhancement feature (resolution, frame rate) price.

## Adjustment Details

### Price before adjustment

| Codec | Resolution | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- |
| H.264 | 480P | 0.0028 | Long side ≤ 640 and short side ≤ 480 |
|  | 720P | 0.0057 | Long side ≤ 1280 and short side ≤ 720 |
|  | 1080P | 0.0111 | Long side ≤ 1936 and short side ≤ 1088 |
|  | 2K | 0.024 | Long side ≤ 2560 and short side ≤ 1440 |
|  | 4K | 0.0491 | Long side > 2560 or short side > 1440 |
| H.265 | 480P | 0.0141 | Long side ≤ 640 and short side ≤ 480 |
|  | 720P | 0.0275 | Long side ≤ 1280 and short side ≤ 720 |
|  | 1080P | 0.0549 | Long side ≤ 1936 and short side ≤ 1088 |
|  | 2K | 0.1183 | Long side ≤ 2560 and short side ≤ 1440 |
|  | 4K | 0.2366 | Long side ≤ 4096 and short side ≤ 2160 |
|  | 8K | 0.8642 | Long side > 4096 or short side > 2160 |
| AV1 | 480P | 0.0282 | Long side ≤ 640 and short side ≤ 480 |
|  | 720P | 0.0550 | Long side ≤ 1280 and short side ≤ 720 |
|  | 1080P | 0.1098 | Long side ≤ 1936 and short side ≤ 1088 |
|  | 2K | 0.2366 | Long side ≤ 2560 and short side ≤ 1440 |
|  | 4K | 0.4732 | Long side ≤ 4096 and short side ≤ 2160 |
|  | 8K | 1.7284 | Long side > 4096 or short side > 2160 |

#### Price after adjustment

##### SDR2HDR

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) |
| --- | --- | --- | --- |
| SDR2HDR | Unlimited | Unlimited | 0.0705 |

##### Frame Interpolation

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Frame Interpolation | 720P | 30fps | 0.1058 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.2116 |  |
|  |  | 120fps | 0.4233 |  |
|  | 1080P | 30fps | 0.2381 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.4762 |  |
|  |  | 120fps | 0.9524 |  |
|  | 2K | 30fps | 0.4233 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.8466 |  |
|  |  | 120fps | 1.6931 |  |
|  | 4K | 30fps | 0.9524 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 1.9048 |  |
|  |  | 120fps | 3.8095 |  |
|  | 8K | 30fps | 3.8095 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 7.619 |  |
|  |  | 120fps | 15.2381 |  |

##### Super Resolution

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Super Resolution | 720P | 30fps | 0.0529 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0882 |  |
|  |  | 120fps | 0.194 |  |
|  | 1080P | 30fps | 0.1058 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.2116 |  |
|  |  | 120fps | 0.4233 |  |
|  | 2K | 30fps | 0.194 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.3704 |  |
|  |  | 120fps | 0.7584 |  |
|  | 4K | 30fps | 0.4233 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.8466 |  |
|  |  | 120fps | 1.6931 |  |
|  | 8K | 30fps | 1.6931 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 3.3862 |  |
|  |  | 120fps | 6.7725 |  |

##### Overall Enhancement

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Overall Enhancement | 720P | 30fps | 0.1411 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.2822 |  |
|  |  | 120fps | 0.5644 |  |
|  | 1080P | 30fps | 0.3175 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.6349 |  |
|  |  | 120fps | 1.2698 |  |
|  | 2K | 30fps | 0.5644 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 1.1287 |  |
|  |  | 120fps | 2.2575 |  |
|  | 4K | 30fps | 1.2698 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 2.5397 |  |
|  |  | 120fps | 5.0794 |  |
|  | 8K | 30fps | 5.0794 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 10.1587 |  |
|  |  | 120fps | 20.3175 |  |

##### Noise Reduction

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Noise Reduction | 720P | 30fps | 0.0353 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0705 |  |
|  |  | 120fps | 0.1587 |  |
|  | 1080P | 30fps | 0.0882 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.1764 |  |
|  |  | 120fps | 0.3527 |  |
|  | 2K | 30fps | 0.1587 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.3175 |  |
|  |  | 120fps | 0.6349 |  |
|  | 4K | 30fps | 0.3527 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.7055 |  |
|  |  | 120fps | 1.4109 |  |
|  | 8K | 30fps | 1.4109 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 2.8219 |  |
|  |  | 120fps | 5.6437 |  |

##### Color Enhancement

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Color Enhancement | 720P | 30fps | 0.0176 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0353 |  |
|  |  | 120fps | 0.0705 |  |
|  | 1080P | 30fps | 0.0353 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.0705 |  |
|  |  | 120fps | 0.1411 |  |
|  | 2K | 30fps | 0.0705 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.1235 |  |
|  |  | 120fps | 0.2469 |  |
|  | 4K | 30fps | 0.1411 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.2822 |  |
|  |  | 120fps | 0.5644 |  |
|  | 8K | 30fps | 0.5644 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 1.1287 |  |
|  |  | 120fps | 2.2575 |  |

##### Scratches Removal

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Scratches Removal | 720P | 30fps | 0.1764 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.3527 |  |
|  |  | 120fps | 0.7231 |  |
|  | 1080P | 30fps | 0.4056 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.8113 |  |
|  |  | 120fps | 1.6226 |  |
|  | 2K | 30fps | 0.7231 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 1.4462 |  |
|  |  | 120fps | 2.8924 |  |
|  | 4K | 30fps | 1.6226 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 3.2451 |  |
|  |  | 120fps | 6.4903 |  |
|  | 8K | 30fps | 6.4903 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 12.9806 |  |
|  |  | 120fps | 25.9612 |  |

##### Banding Removal

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Banding Removal | 720P | 30fps | 0.0176 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0353 |  |
|  |  | 120fps | 0.0705 |  |
|  | 1080P | 30fps | 0.0353 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.0705 |  |
|  |  | 120fps | 0.1411 |  |
|  | 2K | 30fps | 0.0705 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.1235 |  |
|  |  | 120fps | 0.2469 |  |
|  | 4K | 30fps | 0.1411 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.2822 |  |
|  |  | 120fps | 0.5644 |  |
|  | 8K | 30fps | 0.5644 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 1.1287 |  |
|  |  | 120fps | 2.2575 |  |

##### Detail Enhancement

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Detail Enhancement | 720P | 30fps | 0.0071 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0159 |  |
|  |  | 120fps | 0.0317 |  |
|  | 1080P | 30fps | 0.0176 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.0353 |  |
|  |  | 120fps | 0.0705 |  |
|  | 2K | 30fps | 0.0317 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.0635 |  |
|  |  | 120fps | 0.1252 |  |
|  | 4K | 30fps | 0.0705 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.1411 |  |
|  |  | 120fps | 0.2822 |  |
|  | 8K | 30fps | 0.2822 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 0.5644 |  |
|  |  | 120fps | 1.1287 |  |

##### Low-Light Enhancement

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Low-Light Enhancement | 720P | 30fps | 0.0176 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0353 |  |
|  |  | 120fps | 0.0705 |  |
|  | 1080P | 30fps | 0.0353 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.0705 |  |
|  |  | 120fps | 0.1411 |  |
|  | 2K | 30fps | 0.0705 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.1235 |  |
|  |  | 120fps | 0.2469 |  |
|  | 4K | 30fps | 0.1411 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.2822 |  |
|  |  | 120fps | 0.5644 |  |
|  | 8K | 30fps | 0.5644 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 1.1287 |  |
|  |  | 120fps | 2.2575 |  |

##### Face Enhancement

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Face Enhancement | 720P | 30fps | 0.1235 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.2293 |  |
|  |  | 120fps | 0.4762 |  |
|  | 1080P | 30fps | 0.2646 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.5291 |  |
|  |  | 120fps | 1.0582 |  |
|  | 2K | 30fps | 0.4762 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.9347 |  |
|  |  | 120fps | 1.8871 |  |
|  | 4K | 30fps | 1.0582 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 2.1164 |  |
|  |  | 120fps | 4.2328 |  |
|  | 8K | 30fps | 4.2328 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 8.4656 |  |
|  |  | 120fps | 16.9312 |  |

##### Font Enhancement

| Enhancement Features | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Font Enhancement | 720P | 30fps | 0.0705 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.1235 |  |
|  |  | 120fps | 0.2469 |  |
|  | 1080P | 30fps | 0.1411 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.2646 |  |
|  |  | 120fps | 0.5291 |  |
|  | 2K | 30fps | 0.2469 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.4762 |  |
|  |  | 120fps | 0.9524 |  |
|  | 4K | 30fps | 0.5291 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 1.0582 |  |
|  |  | 120fps | 2.1164 |  |
|  | 8K | 30fps | 2.1164 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 4.2328 |  |
|  |  | 120fps | 8.4656 |  |

## Billing Example

If you initiate a 100-minute live stream on October 1, 2023, and use two Audio/Video enhancement capabilities, Font Enhancement and Low-Light Enhancement, during the live stream. After Top Speed Codec (TSC) Transcoding, the output live stream is in**H.264 codec format**, **1080P resolution**, and **30fps**. On October 2, 2023, your live Audio/Video enhancement bill will be as follows:

**Top Speed Codec (TSC) Transcoding** Fee = 0.0443 (USD/minute) × 100 (minutes) = 4.43 USD;

**Font Enhancement**Fee = 0.1411 (USD/minute) × 100 (minutes) = 14.11 USD;

**Low-Light Enhancement** Fee = 0.0353 (USD/minute) × 100 (minutes) = 3.53 USD;

The effective date of this price adjustment is October 1, 2023. Please pay attention to the new billing method.

Please pay attention to the new billing method. If you have any questions, feel free to contact us at any time. We sincerely appreciate the trust and support from all users for Tencent Cloud Cloud Streaming Services (CSS) product!

**2023-08-31**

**Tencent Cloud Team**


---
*Source: [https://www.tencentcloud.com/document/product/267/56725](https://www.tencentcloud.com/document/product/267/56725)*
