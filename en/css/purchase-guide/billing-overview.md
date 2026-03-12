# Billing Overview

> **Note:**You can use the [CSS price calculator](https://buy.tencentcloud.com/price/css/calculator) to estimate your LVB and LEB fees.

Billable items of CSS include basic services and value-added services. You may also incur extended service fees if you use CSS features that rely on the capabilities of other Tencent Cloud products.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7fdf82d5df5211eea462525400bb593a.png)

- [Basic service fees](#base) are the fees for using LVB and LEB and are charged based on either traffic or peak bandwidth usage.
- [Value-added service fees](#appreciation) are the fees for using value-added features, such as transcoding, recording, time shifting, screencapture, audit, delay playback, LVC, and relay. These features are disabled by default and are billed only when enabled.
- [Extended service fees](#extensions) are the fees for using the capabilities of other Tencent Cloud products and are charged according to the billing rules of the corresponding products.

## Basic Service Fees

Basic service fees include LVB fees and LEB fees.

| Billable Item | Description | Billing Mode |
| --- | --- | --- |
| LVB traffic (default) | LVB traffic fees are charged based on the downstream and/or upstream traffic consumed. By default, only downstream traffic is billed.Prices differ for regions inside and outside the Chinese mainland. | [Prepaid packages](https://www.tencentcloud.com/document/product/267/52220#.E6.A0.87.E5.87.86.E8.BD.AC.E7.A0.81.E8.B5.84.E6.BA.90.E5.8C.85)[Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/2818#flow)Monthly pay-as-you-go |
| LVB peak bandwidth | LVB bandwidth fees are charged based on the downstream and/or upstream bandwidth consumed. By default, only downstream bandwidth is billed.Prices differ for regions inside and outside the Chinese mainland. | [Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/2818#bandwidth)Monthly pay-as-you-go |
| LEB traffic (default) | LEB traffic fees are charged based on the downstream and/or upstream traffic consumed. By default, only downstream traffic is billed.Prices differ for regions inside and outside the Chinese mainland. | [Prepaid packages](https://www.tencentcloud.com/document/product/267/52220#.E6.A0.87.E5.87.86.E8.BD.AC.E7.A0.81.E8.B5.84.E6.BA.90.E5.8C.85)[Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/39969#flow)Monthly pay-as-you-go |
| LEB peak bandwidth | LEB bandwidth fees are charged based on the downstream and/or upstream bandwidth consumed. By default, only downstream bandwidth is billed.Prices differ for regions inside and outside the Chinese mainland. | [Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/39969#bandwidth)Monthly pay-as-you-go |

> **Note:**Because LEB uses channels with ultra-low latency, its traffic/bandwidth fees are slightly higher than those of LVB.CSS provides the monthly billing mode for customers with high demand. To change to monthly billing, please contact your sales rep.For more information about billing modes, see [Changing Billing Modes](https://intl.cloud.tencent.com/document/product/267/30411).

## Value-Added Service Fees

| Billable Item |  | Description | Billing Mode |
| --- | --- | --- | --- |
| Live transcoding | Standard transcoding | The fees for using the standard transcoding capability.Standard transcoding fees will be incurred if you use the [watermarking](https://www.tencentcloud.com/document/product/267/31064), [standard transcoding](https://www.tencentcloud.com/document/product/267/31071), or [stream mixing](https://www.tencentcloud.com/document/product/267/37665) features.The fees are based on the **transcoding duration** and resolution of the output stream. | [Prepaid packages](https://www.tencentcloud.com/document/product/267/52220)[Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/39604)Monthly pay-as-you-go |
|  | Top Speed Codec (TSC) transcoding | The fees for using the TSC transcoding capability.TSC transcoding fees will be incurred if you use the [TSC transcoding](https://www.tencentcloud.com/document/product/267/31071#C_topspeed) feature.The fees are based on the **transcoding duration** and resolution of the output stream. | [Prepaid packages](https://www.tencentcloud.com/document/product/267/52220)[Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/39604#.E6.9E.81.E9.80.9F.E9.AB.98.E6.B8.85.E8.BD.AC.E7.A0.81)Monthly pay-as-you-go |
|  | Audio transcoding | The fees for using the audio transcoding capability.Audio transcoding fees will be incurred if you use the [audio transcoding](https://www.tencentcloud.com/document/product/267/31071#C_audio) or audio mixing feature.The fees are based on the **audio transcoding duration**. | [Prepaid packages](https://www.tencentcloud.com/document/product/267/52220#standard_pag)[Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/39604#a_trans)Monthly pay-as-you-go |
| Live recording | Recording fees | The fees are based on the peak number of concurrent recording channels. | [Monthly pay-as-you-go](https://www.tencentcloud.com/document/product/267/39605) |
|  | Recording-to-COS fees | If you record to COS, recording-to-COS fees will be charged based on the recording duration. | [Monthly pay-as-you-go](https://www.tencentcloud.com/document/product/267/39605#.E5.BD.95.E5.88.B6.E6.8A.95.E9.80.92-cos-.E6.9C.8D.E5.8A.A1) |
| Time shifting | Live streaming traffic | If you create a time shifting template in the CSS console and bind it to a push domain, using the domain for live streaming will incur time shifting fees, which are based on the live streaming traffic. | [Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/53262) |
|  | Total time-shift period | If you have submitted a ticket to enable the time shifting feature, time shifting fees will be based on the total time-shift period. | [Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/47534) |
| Live screencapture |  | Screenshots of a live stream are taken at times specified in a template and saved to COS.Screencapture is billed based on **the number of screenshots taken**. We offer a free tier of 1,000 screenshots per month. | [Monthly pay-as-you-go](https://www.tencentcloud.com/document/product/267/39606) |
| Live stream moderation | Image review | By using the image review feature, screenshots that hit the review criteria will be stored in COS.The review of images is calculated based on the number of images, with the first 1,000 images free of charge each month. | [Monthly pay-as-you-go](https://www.tencentcloud.com/document/product/267/58267) |
|  | Audio auditing | By using the audio auditing feature, the actual audio will be stored in COS. The calculation is based on the length of time. | [Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/58267)Monthly pay-as-you-go |
| Intelligent porn detection |  | Using the porn detection feature will incur screencapture and porn detection fees.Porn detection is billed based on **the number of screenshots analyzed**. We offer a free tier of 1,000 screenshots for porn detection per month.Screencapture is billed based on**the number of screenshots taken**. We offer a free tier of 1,000 screenshots per month. | [Monthly pay-as-you-go](https://www.tencentcloud.com/document/product/267/39607) |
| LVC | LVC output duration | LVC PGM output is billed based on the video stream resolution, output screen type, and output duration. | [Prepaid package](https://www.tencentcloud.com/document/product/267/58538)[Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/58538) |
|  | Billing for relay to third parties | LVC uses the relay feature and the fees are billed based on the third-party bandwidth. | [Monthly pay-as-you-go](https://www.tencentcloud.com/document/product/267/58538#.E8.BD.AC.E6.8E.A8.E7.AC.AC.E4.B8.89.E6.96.B9.E8.AE.A1.E8.B4.B9) |
| Relay | Relay task duration | Relay fees are billed based on the duration of relay tasks. | [Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/41059#time) |
|  | Third-party relaying bandwidth | The fees for relaying to a URL that does not belong to the current Tencent Cloud account. | [Monthly pay-as-you-go](https://www.tencentcloud.com/document/product/267/41059#third-party-relaying-bandwidth) |
|  | Local mode | Additional fees will be incurred if you enable the local mode for relay. | [Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/51555) |
| Delayed playback |  | When the [delayed playback](https://www.tencentcloud.com/document/product/267/55264) feature is used, additional feature fees will be incurred. | [Daily pay-as-you-go](https://www.tencentcloud.com/document/product/267/54973) |

## Extended Service Fees

| Billable Item | Description | Billing Mode |
| --- | --- | --- |
| VOD storage | Saving recording files to VOD will incur VOD storage fees, which are based on the actual storage duration and storage space used. | [VOD pay-as-you-go](https://intl.cloud.tencent.com/document/product/266/14666#media_storage) |
| COS storage | Saving recording files to COS will incur COS storage fees, which are based on the actual storage duration and storage space used. | [COS pay-as-you-go](https://intl.cloud.tencent.com/document/product/436/40099) |
| Storing screenshots | Screenshots generated by live screencapture and porn detection are saved to COS, which incurs COS storage fees. The fees are billed based on the actual storage duration and storage space used. | [COS pay-as-you-go](https://intl.cloud.tencent.com/document/product/436/32534) |


---
*Source: [https://www.tencentcloud.com/document/product/267/2819](https://www.tencentcloud.com/document/product/267/2819)*
