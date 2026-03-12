# Billing Content Adjustment for Cloud Streaming Services Standard Transcoding and Top Speed Codec Transcoding

To provide a more streamlined and clear reconciliation experience, starting from **April 16, 2024, at midnight**, the Cloud Streaming Services (CSS) will modify the sub-product name, resource ID, component type, component name, price unit, usage, usage duration, and duration unit in the bill for the standard transcoding and the top speed codec transcoding, and add transcoding types to distinguish different transcoding billing intervals.

Taking the daily settlement billing standard transcoding H264_1080P as an example, the bill comparison before and after the adjustment is as follows:

| Before and After Bill Adjustment | ProductName | SubproductName | TransactionTime | Usage Start Time | Usage End Time | InstanceID | Region | ComponentType | ComponentName | Component List   Price | Component Contracted Price | Transcode Type | Component Price   Measurement Unit | Component Usage | Component Usage   Unit | Usage Duration | Duration Unit | Blended Discount   Multiplier | Total Cost (Including Tax) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Before Adjustment | Cloud Streaming Services | *live-domestic* | 2024/5/3 06:52 | 2024/5/2 00:00 | 2024/5/2 23:59 | *1234567888_101618_live_trans_20240502_liveprocessor_H264_1080P_1* | Regions Outside Chinese Mainland | *live_transcoding* | *live_transcoding_monthly* | 0.0111 | 0.0111 | - | *USD/3Minute/Minute* | *3* | Minute | *80000* | *Minute* | 1 | 888 |
| After Adjustment | Cloud Streaming Services | *live transcoding* | 2024/5/3 06:52 | 2024/5/2 00:00 | 2024/5/2 23:59 | *1234567888_301262_sv_live_transcode_daily_20240502_liveprocessor_H264_1080P_1* | Regions Outside Chinese Mainland | *Live Transcode Duration* | *Live Transcode Daily* | 0.0111 | 0.0111 | *Standard Transcode H.264_1080P* | *USD/Minute* | *80000* | Minute | *1* | *Day* | 1 | 888 |

> **Note:**Originally, the transcoding bill used price unit and usage to mark different transcoding billing intervals, and the actual usage was included in the usage duration, which could easily cause ambiguity during reconciliation. In the adjusted bill, the actual usage is included in the usage.This adjustment only changes the bill display content and does not affect the billing rules or the billing amount.

If you have any questions, feel free to [contact us](https://console.tencentcloud.com/workorder/category). We sincerely appreciate our users' trust and support for Tencent Cloud Cloud Streaming Services (CSS).

****

**2024-04-03**

**Tencent Cloud Cloud Streaming Services Team**


---
*Source: [https://www.tencentcloud.com/document/product/267/59865](https://www.tencentcloud.com/document/product/267/59865)*
