# Billing of LEB

## Overview

- Billing mode: **Daily pay-as-you-go**
- Billing cycle: Daily billing cycle. Traffic fees generated each day are deducted the following day. For the actual fee deduction and bill generation time, see your billing statement.
- After a new user activates Cloud Live Broadcast, the [LEB downstream playback](https://www.tencentcloud.com/document/product/267/39969#30ba7559-3d05-4e6f-90bc-f9f9fd86e56f) and [upstream push](https://www.tencentcloud.com/document/product/267/39969#cfac37fd-ceab-4431-bcc1-cdd283719c91) will be billed by traffic by default.
- We offer prepaid traffic packages. A traffic package deducts LVB downstream traffic in the Chinese mainland at a ratio of 1:1. Different deduction ratios are applied to LVB downstream traffic outside the Chinese mainland, LEB downstream traffic in the Chinese mainland, LEB downstream traffic outside the Chinese mainland, and upstream traffic inside and outside the Chinese mainland. For details, see [Prepaid Packages](https://www.tencentcloud.com/document/product/267/52220).
- **Billing regions outside the Chinese mainland**:
  - Asia Pacific 1: Hong Kong (China), Singapore, Macao (China), Vietnam, Thailand, Nepal, Cambodia, Pakistan, Laos, Myanmar, Kazakhstan, Uzbekistan, Kyrgyzstan, Brunei, Bangladesh, Azerbaijan, Mongolia.
  - Asia Pacific 2: Taiwan (China), Japan, Malaysia, Indonesia, South Korea.
  - Asia Pacific 3: Philippines, India,  Australia, New Zealand,  Maldives.
  - North America: United States, Mexico, Canada.
  - Europe: Netherlands, Germany,  United Kingdom, Ireland, Italy, Spain, France, Sweden, Bulgaria, Poland,  Finland.
  - Middle East: United Arab Emirates, Türkiye, Qatar, Saudi Arabia, Bahrain, Iraq, Oman, Kuwait, Jordan, lebanon.
  - Africa: South Africa, Egypt, Algeria, Morocco, Tunisia, Kenya.
  - South America: Brazil, Colombia, Argentina, Chile, Peru, Ecuador.
- The conversion factor for units of traffic/bandwidth is 1,000. For example, 1 TB = 1,000 GB.
- A CSS service day is 00:00-23:59 (UTC+08:00).
- Because LEB uses channels with ultra-low latency, its traffic/bandwidth fees are slightly higher than those of LVB.
- LEB does not support live streams with B-frames. If a stream contains B-frames, the system will automatically remove them through transcoding, which will incur transcoding fees.
- Browser playback only supports the standard WebRTC protocol and does not support AAC. If a stream contains audio in AAC format, the system will automatically transcode the audio into Opus format, which will incur audio transcoding fees.
- **On 00:00 (UTC+08:00), January 4, 2022**, CSS adjusted the daily billing prices and pricing tiers of LEB and started billing usage outside the Chinese mainland by region instead of at a unified price. For details, see [Notice: CSS to Adjust Prices of Basic Services](https://www.tencentcloud.com/document/product/267/43055).

## LEB downstream playback billing

### Traffic/Bandwidth Usage in the Chinese Mainland

LEB is a basic service of CSS and is billed based on the downstream traffic/bandwidth consumed during live streaming.

LEB provides two daily pay-as-you-go billing modes: [bill-by-traffic](#flow) and [bill-by-bandwidth](#bandwidth). You can choose whichever suits your needs. **The default mode for new users of LEB is bill-by-traffic.**

#### Bill-by-traffic

##### Pricing

We bill LEB traffic on a daily basis and adopt a tiered pricing approach. See below for the pricing tiers:

| Traffic Tier | Price (USD/GB) |
| --- | --- |
| 0-2 TB | 0.0846 |
| 2 TB (inclusive) - 10 TB | 0.0813 |
| 10 TB (inclusive) - 50 TB | 0.0780 |
| 50 TB (inclusive) - 100 TB | 0.0715 |
| 100 TB (inclusive) - 1 PB | 0.0618 |
| ≥ 1 PB | 0.0520 |

##### Billing details

- Billable item: Downstream traffic consumed during LEB playback in the Chinese mainland
- Billing rules: Fees are calculated by multiplying the total traffic consumed in a day by the unit price of the corresponding tier.

##### Billing example

- Assume that the bitrate of a live streaming session was 500 Kbps (This is the sum of the audio bitrate and video bitrate. If you transcode the stream to a specific video bitrate, the sum of this video bitrate and the audio bitrate will be used for billing), and there were 100 concurrent viewers at the peak, the traffic consumed would be 500/8 x 3,600 x 100 = 22,500,000 KB = 22.5 GB.
- Assume that you used the LEB service on January 4, 2022 and consumed 22.5 GB of downstream traffic. On January 5, 2022, you would be charged:
- 0.0846 (USD/GB) x 22.5 (GB) = 1.9035 USD.
- Downstream playback charges, however, upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the peak upstream bandwidth used in a day exceeds 100 Mbps. Upstream Push charges support on-demand configuration and push streaming Use usage-to-gradient independent billing.

#### Bill-by-bandwidth

##### Pricing

We bill LEB bandwidth usage on a daily basis and adopt a tiered pricing approach. The fee is charged based on your peak bandwidth usage in a day. See below for the pricing tiers:

| Bandwidth Tier | Price (USD/Mbps/Day) |
| --- | --- |
| 0 - 500 Mbps | 0.2114 |
| 500 Mbps (inclusive) - 5 Gbps | 0.2049 |
| 5 Gbps (inclusive) - 20 Gbps | 0.1984 |
| ≥ 20 Gbps | 0.1886 |

##### Billing details

- Billable item: Downstream bandwidth used during LEB playback in the Chinese mainland
- Billing rules: Fees are calculated by multiplying the highest bandwidth used in a day by the unit price of the corresponding tier.

##### Billing example

- Assume that the bitrate of a live streaming session was 500 Kbps (This is the sum of the audio bitrate and video bitrate. If you transcode the stream to a specific video bitrate, the sum of this video bitrate and the audio bitrate will be used for billing), and there were 100 concurrent viewers at the peak, the highest bandwidth used would be:

500 Kbps x 100 = 50,000 Kbps = 50 Mbps.

- Assume that you used the LEB service on January 4, 2022 and your bandwidth usage reached 50 Mbps at the highest. On January 5, 2022, the following bandwidth fee would be billed:

0.2114 (USD/Mbps/Day) x 50 (Mbps) = 10.57 USD.

- Downstream playback charges, however, upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the peak upstream bandwidth used in a day exceeds 100 Mbps. Upstream Push charges support on-demand configuration and push streaming Use usage-to-gradient independent billing.

> **Note:**If you have a large-scale live streaming business, then a daily billing mode may not meet your needs. Please contact the Tencent Cloud sales team or [submit a ticket](https://console.tencentcloud.com/workorder/category) for other billing options.

### Traffic/Bandwidth Usage Outside the Chinese Mainland

Traffic/Bandwidth usage outside the Chinese mainland is the downstream traffic/bandwidth used when users connect to Tencent Cloud’s acceleration servers outside the Chinese mainland. You can choose to be billed [by traffic](#overseas_flow) or [by bandwidth](#overseas_bandwidth). By default, new users are billed by traffic.

> **Note:**The LEB billing rules for regions outside the Chinese mainland took effect on April 20, 2021. They apply to bills generated on April 21 and afterward.

#### Bill-by-traffic

##### Pricing

We bill traffic outside the Chinese mainland by region on a daily basis and adopt a tiered pricing approach. See below for the pricing tiers:

| Traffic Tier | Price (USD/GB) |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Asia Pacific 1 | Asia Pacific 2 | Asia Pacific 3 | North America | Europe | Middle East | Africa | South America |
| 0-2 TB | 0.1496 | 0.2472 | 0.2276 | 0.1431 | 0.1431 | 0.3902 | 0.3902 | 0.3350 |
| 2 TB (inclusive) - 50 TB | 0.1398 | 0.2276 | 0.2081 | 0.1268 | 0.1268 | 0.3577 | 0.3577 | 0.3187 |
| 50 TB (inclusive) - 100 TB | 0.1171 | 0.2114 | 0.1821 | 0.1008 | 0.1008 | 0.3350 | 0.3350 | 0.2927 |
| 100 TB (inclusive) - 1 PB | 0.1008 | 0.1821 | 0.1626 | 0.0650 | 0.0650 | 0.3089 | 0.3089 | 0.2764 |
| ≥ 1 PB | 0.0911 | 0.1691 | 0.1431 | 0.0520 | 0.0520 | 0.2764 | 0.2764 | 0.2602 |

##### Billing details

- Billable item: Downstream traffic consumed during LEB playback outside the Chinese mainland.
- Billing rules: Fees are calculated by multiplying the total traffic consumed in a day in a billing region by the unit price of the corresponding tier.

##### Billing example

- Assume that the bitrate of a live streaming session was 500 Kbps (This is the sum of the audio bitrate and video bitrate. If you transcode the stream to a specific video bitrate, the sum of this video bitrate and the audio bitrate will be used for billing), and there were 100 concurrent viewers at the peak, the traffic consumed would be 500/8 × 3,600 × 100 = 22,500,000 KB = 22.5 GB.
- Assume that you used the LEB service on January 4, 2022 and consumed 22.5 GB of downstream traffic. On January 5, 2022, the following traffic fee would be incurred:

0.1496 (USD/GB) × 22.5 (GB) = 3.366 USD.

- Downstream playback charges, however, upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the peak upstream bandwidth used in a day exceeds 100 Mbps. Upstream Push charges support on-demand configuration and push streaming Use usage-to-gradient independent billing.

#### Bill-by-bandwidth

##### Pricing

We bill bandwidth usage outside the Chinese mainland by region on a daily basis and adopt a tiered pricing approach. The fee is based on your peak bandwidth usage in a day. See below for the pricing tiers:

| Bandwidth Tier | Price (USD/Mbps/Day) |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Asia Pacific 1 | Asia Pacific 2 | Asia Pacific 3 | North America | Europe | Middle East | Africa | South America |
| 0-500 Mbps | 0.4098 | 1.2033 | 1.2455 | 0.3967 | 0.3967 | 1.8667 | 1.8667 | 1.6911 |
| 500 Mbps (inclusive) - 5 Gbps | 0.3707 | 1.0829 | 1.2098 | 0.3610 | 0.3610 | 1.8407 | 1.8407 | 1.6553 |
| 5 Gbps (inclusive) - 20 Gbps | 0.3415 | 0.9659 | 1.1122 | 0.3363 | 0.3363 | 1.8016 | 1.8016 | 1.6130 |
| ≥ 20 Gbps | 0.3252 | 0.8455 | 1.0081 | 0.3187 | 0.3187 | 1.7821 | 1.7821 | 1.5935 |

##### Billing details

- Billable item: Downstream bandwidth used during LEB playback outside the Chinese mainland.
- Billing rules: Fees are calculated by multiplying the highest bandwidth used in a day in a billing region by the unit price of the corresponding tier.

##### Billing example

- Assume that the bitrate of a live streaming session was 500 Kbps (This is the sum of the audio bitrate and video bitrate. If you transcode the stream to a specific video bitrate, the sum of this video bitrate and the audio bitrate will be used for billing), and there were 100 concurrent viewers at the peak, the highest bandwidth used would be:

500 (Kbps) × 100 = 50,000 (Kbps) = 50 Mbps.

- Assume that you used the LEB service on January 4, 2022 for playback in Macao (China) and your bandwidth usage reached 50 Mbps at the highest. On January 5, 2022, the following bandwidth fee would be billed:

0.4098 (USD/Mbps/Day) × 50 (Mbps) = 20.49 USD.

- Downstream playback charges, however, upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the peak upstream bandwidth used in a day exceeds 100 Mbps. Upstream Push charges support on-demand configuration and push streaming Use usage-to-gradient independent billing.

## **Upstream Push Billing**

- Upstream Push is not billed by default.
- Upstream usage will only be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the highest upstream bandwidth used in a day exceeds 100 Mbps.The billing method, tiered pricing rules, and billing regions for upstream traffic inside/outside the Chinese mainland are **the same as** those for [LVB downstream traffic](https://www.tencentcloud.com/document/product/267/2818#30ba7559-3d05-4e6f-90bc-f9f9fd86e56f). Upstream traffic became a billable item starting at 00:00 (UTC+08:00), July 1, 2021.
- For example:

Suppose you consumed 9 GB of LEB downstream traffic and 1 GB of LEB upstream traffic in **Asia Pacific 1** one day, and the peak bandwidth on that day was 101 Mbps. Because the ratio of downstream traffic to upstream traffic is 9:1, which is smaller than 10:1, and the peak upstream bandwidth usage is higher than 100 Mbps, the following traffic fee would be billed:

Upstream traffic fees + Downstream traffic fees = 0.1496 (USD/GB) x (9 GB + 1 GB) = 1.496 USD.

## **Channel Service Billing**

- By default, Cloud Streaming Services do **not charge** for channel services. However, if your peak monthly channel count exceeds 100 (i.e., the peak concurrent push streams in a month exceed 100) and the resource utilization is relatively low, such as in video surveillance scenarios or exam proctoring scenarios, Tencent Cloud's business representatives will contact you to negotiate the payment for channel service fees. **If you have not received any related notifications, there is no need to be concerned**.
- Channel Service Price: 8.34 USD/Peak Channel Count/Month. Channel Service Fee = Channel Service Price (USD/Channel/Month) × Peak Channel Count (Channels) × Monthly Valid Days Coefficient (Months).
- For example:

User A is in a video surveillance scenario and uses Cloud Streaming Services in June. The peak channel count for the month is 300 channels, and the channel resource utilization is extremely low. The valid number of days for channel service in the month is 10 days (if the daily channel count is not 0, it is considered a valid day).

Channel Service Fee = 8.34 (USD/Channel/Month) × 300 (Channels) × (10 / 30) (Months) = 834 USD.


---
*Source: [https://www.tencentcloud.com/document/product/267/39969](https://www.tencentcloud.com/document/product/267/39969)*
