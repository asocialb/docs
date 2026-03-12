# CSS to Support H.265 8K and AV1 8K Transcoding

Starting from 00:00 on April 30, 2023, standard transcoding and Top Speed Codec (TSC) transcoding will support H.265 8K and AV1 8K. They will be priced differently from other resolutions and will be deducted from standard and TSC transcoding packages at different ratios.

## Pay-As-You-Go Rates

For billing details about the value-added service of live transcoding, see [Live Transcoding (Watermarking, Stream Mixing)](https://www.tencentcloud.com/document/product/267/39604).

### Standard transcoding

| Codec | Resolution | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- |
| H.265 | 4K | 0.2366 | Long side ≤ 4096 and short side ≤ 2160 |
| H.265 | 8K | 0.8642 | Long side > 4096 or short side > 2160 |
| AV1 | 4K | 0.4732 | Long side ≤ 4096 and short side ≤ 2160 |
| AV1 | 8K | 1.7284 | Long side > 4096 or short side > 2160 |

### TSC transcoding

| Codec | Resolution | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- |
| H.265 | 4K | 0.5317 | Long side ≤ 4096 and short side ≤ 2160 |
| H.265 | 8K | 1.7284 | Long side > 4096 or short side > 2160 |
| AV1 | 4K | 1.0634 | Long side ≤ 4096 and short side ≤ 2160 |
| AV1 | 8K | 3.4568 | Long side > 4096 or short side > 2160 |

### Audio/Video enhancement

| Codec | Resolution | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- |
| H.265 | 4K | 2.3893 | Long side ≤ 4096 and short side ≤ 2160 |
| H.265 | 8K | 7.7708 | Long side > 4096 or short side > 2160 |
| AV1 | 4K | 2.9207 | Long side ≤ 4096 and short side ≤ 2160 |
| AV1 | 8K | 9.4992 | Long side > 4096 or short side > 2160 |

## Package Deduction

For details about how deduction works for transcoding packages, see [Prepaid Packages](https://www.tencentcloud.com/document/product/267/52220).

#### Standard transcoding package

| Package Price (USD) |  | 0.69 | 13.43 | 134.18 | 1193.88 | 5970 | 7462.54 | Pay-As-You-Go Rate (USD/Min) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| H.264 | 480p (default) | 5 hours | 100 hours | 1,000 hours | 10,000 hours | 50,000 hours | 100,000 hours | 0.0028 |
| H.265 | 8K | Deductible duration for a specific resolution = Package duration x Pay-as-you-go rate of H.264_480p ÷ Pay-as-you-go rate of the resolution |  |  |  |  |  | 0.8642 |
| AV1 | 8K |  |  |  |  |  |  | 1.7284 |

#### TSC transcoding package

| Package Price (USD) |  | 22.24 | 44.63 | 268.71 | 2,238.66 | 1,4925.22 | Pay-As-You-Go Rate (USD/Min) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TSC H.264 | 480p (default) | 50 hours | 100 hours | 1,000 hours | 10,000 hours | 100,000 hours | 0.0116 |
| TSC H.265 | 8K | Deductible duration for a specific resolution = Package duration x Pay-as-you-go rate of TSC H.264_480p ÷ Pay-as-you-go rate of the resolution |  |  |  |  | 1.7284 |
| TSC AV1 | 8K |  |  |  |  |  | 3.4568 |
| Audio/Video enhancement H.265 | 8K |  |  |  |  |  | 7.7708 |
| Audio/Video enhancement AV1 | 8K |  |  |  |  |  | 9.4992 |

If you have any questions, feel free to [contact us](https://console.tencentcloud.com/workorder/category).

**2023-03-30**

**Tencent Cloud CSS Team**


---
*Source: [https://www.tencentcloud.com/document/product/267/54676](https://www.tencentcloud.com/document/product/267/54676)*
