# Billing of LVB

## Overview

- Billing mode: Daily pay-as-you-go
- Billing cycle: Daily billing cycle. Traffic fees generated each day are deducted the following day. For the actual fee deduction and bill generation time, see your billing statement.
- After a new user activates Cloud Streaming Services, the [live broadcast downstream playback](https://www.tencentcloud.com/document/product/267/2818#30ba7559-3d05-4e6f-90bc-f9f9fd86e56f)and [upstream push](https://www.tencentcloud.com/document/product/267/2818#cfac37fd-ceab-4431-bcc1-cdd283719c91) will be billed by traffic by default.
- We offer **prepaid traffic packages**. A traffic package deducts LVB downstream traffic in the Chinese mainland at a ratio of 1:1. Different deduction ratios are applied to **LVB downstream traffic outside the Chinese mainland, LEB downstream traffic in the Chinese mainland, LEB downstream traffic outside the Chinese mainland, and upstream traffic inside and outside the Chinese mainland**. For details, see [Prepaid Packages](https://www.tencentcloud.com/document/product/267/52220).
- **Billing regions outside the Chinese mainland:**
  - Asia Pacific 1: Hong Kong (China), Singapore, Macao (China), Vietnam, Thailand, Nepal, Cambodia, Pakistan, Laos, Myanmar, Kazakhstan, Uzbekistan, Kyrgyzstan, Brunei, Bangladesh, Azerbaijan, Mongolia.
  - Asia Pacific 2: Taiwan (China), Japan, Malaysia, Indonesia, South Korea.
  - Asia Pacific 3: Philippines, India, Australia, New Zealand, Maldives.
  - North America: United States, Mexico, Canada.
  - Europe: Netherlands, Germany,  United Kingdom, Ireland, Italy, Spain, France, Sweden, Bulgaria, Poland,  Finland.
  - Middle East: United Arab Emirates, Türkiye, Qatar, Saudi Arabia, Bahrain, Iraq, Oman, Kuwait, Jordan, Lebanon.
  - Africa: South Africa, Egypt, Algeria, Morocco, Tunisia, Kenya.
  - South America: Brazil, Colombia, Argentina, Chile, Peru, Ecuador.
- The conversion factor for units of traffic/bandwidth is 1,000. For example, 1 TB = 1,000 GB.
- A CSS service day is 00:00-23:59 (UTC+08:00).
- **At 00:00 (UTC+08:00), January 4, 2022**, CSS adjusted the daily billing prices and pricing tiers of LVB’s basic services and started billing usage outside the Chinese mainland by region instead of at a unified price. For details, see [Notice: CSS to Adjust Prices of Basic Services](https://www.tencentcloud.com/document/product/267/43055).

## Live Video Broadcasting (LVB) downstream playback billing

### Traffic/Bandwidth Usage in the Chinese Mainland

LVB is a basic service of CSS and is billed based on the downstream traffic/bandwidth consumed during live streaming. LVB provides two daily pay-as-you-go billing modes: [bill-by-traffic](#flow) and [bill-by-bandwidth](#bandwidth). You can choose whichever suits your needs.

#### Bill-by-traffic

##### Pricing

We bill LVB traffic on a daily basis and adopt a tiered pricing approach. See below for the pricing tiers:

| Traffic Tier | Price (USD/GB) |
| --- | --- |
| 0-2 TB | 0.0423 |
| 2 TB (inclusive) - 10 TB | 0.0407 |
| 10 TB (inclusive) - 50 TB | 0.0390 |
| 50 TB (inclusive) - 100 TB | 0.0358 |
| 100 TB (inclusive) - 1 PB | 0.0309 |
| ≥ 1 PB | 0.0260 |

##### Billing details

- Billable item: Downstream traffic consumed during LVB playback in the Chinese mainland.
- Billing rules: Fees are calculated by multiplying the total traffic consumed in a day by the unit price of the corresponding tier.
- Calculation formula: Consumed traffic = Bitrate/8 × Total playback duration.

> **Note:**Total playback duration = Daily number of online viewers × Average playback duration per viewer. That is to say, the total playback duration is the same if 1 viewer watches for 60 minutes and 60 viewers watch for 1 minute each.Traffic fees = Consumed traffic × Unit price of the corresponding tier.

##### Billing example

- Assume that a live streaming session lasted for 2 hours and the bitrate was 1 Mbps (This is the sum of the audio bitrate and video bitrate. If you transcode the stream to a specific video bitrate, the sum of this video bitrate and the audio bitrate will be used for billing). If 100 viewers watched the live stream for 1 hour each and 50 viewers watched it for 2 hours each, the consumed traffic would be:

1 (Mbps)/8 x 7,200 (s) x 50 (Viewers) + 1 (Mbps)/8 x 3,600 (s) x 100 (Viewers) = 90,000 (MB) = 90 GB.

- Assume that you used the LVB service on January 4, 2022 and consumed 90 GB of downstream traffic. On January 5, 2022, the following traffic fee would be billed:

0.0423 (USD/GB) x 90 (GB) = 3.807 USD.

- Downstream playback charges, however, upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the peak upstream bandwidth used in a day exceeds 100 Mbps. Upstream Push charges support on-demand configuration and push streaming Use usage-to-gradient independent billing.

#### Bill-by-bandwidth

##### Pricing

We bill LVB bandwidth usage on a daily basis and adopt a tiered pricing approach. The fee is based on your peak bandwidth usage in a day. See below for the pricing tiers:

| Bandwidth Tier | Price (USD/Mbps/Day) |
| --- | --- |
| 0-500 Mbps | 0.1057 |
| 500 Mbps (inclusive) - 5 Gbps | 0.1024 |
| 5 Gbps (inclusive) - 20 Gbps | 0.0992 |
| ≥ 20 Gbps | 0.0943 |

##### Billing details

- Billable item: Downstream bandwidth used during LVB playback in the Chinese mainland.
- Billing rules: Fees are calculated by multiplying the highest bandwidth used in a day by the unit price of the corresponding tier.

##### Billing example

- Assume that the bitrate of a live streaming session was 500 Kbps (This is the sum of the audio bitrate and video bitrate. If you transcode the stream to a specific video bitrate, the sum of this video bitrate and the audio bitrate will be used for billing), and there were 100 concurrent viewers at the peak, the highest bandwidth used would be:

500 (Kbps) x 100 = 50,000 (Kbps) = 50 Mbps.

- Assume that you used the LVB service on January 4, 2022 and your bandwidth usage reached 50 Mbps at the highest. On January 5, 2022, the following bandwidth fee would be billed:

0.1057 (USD/Mbps/Day) x 50 (Mbps) = 5.285 USD.

- Downstream playback charges, however, upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the peak upstream bandwidth used in a day exceeds 100 Mbps. Upstream Push charges support on-demand configuration and push streaming Use usage-to-gradient independent billing.

> **Note:**If you have a large-scale live streaming business and your spending on Tencent Cloud resources has exceeded or is expected to exceed 10,000 USD, then a daily billing mode may not meet your needs. Please [contact](https://www.tencentcloud.com/contact-us) the Tencent Cloud sales team or [submit a ticket](https://console.tencentcloud.com/workorder/category) for other billing options.

### Traffic/Bandwidth Usage Outside the Chinese Mainland

Traffic/Bandwidth usage outside the Chinese mainland is the downstream traffic/bandwidth used when users connect to Tencent Cloud’s acceleration servers outside the Chinese mainland. You can choose to be billed [by traffic](#overseas_flow) or [by bandwidth](#overseas_bandwidth). By default, new users are billed by traffic.

#### Bill-by-traffic

##### Pricing

We bill traffic outside the Chinese mainland by region on a daily basis and adopt a tiered pricing approach. See below for the pricing tiers:

| Traffic Tier | Price (USD/GB) |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Asia Pacific 1 | Asia Pacific 2 | Asia Pacific 3 | North America | Europe | Middle East | Africa | South America |
| 0-2 TB | 0.0748 | 0.1236 | 0.1138 | 0.0715 | 0.0715 | 0.1951 | 0.1951 | 0.1675 |
| 2 TB (inclusive) - 50 TB | 0.0699 | 0.1138 | 0.1041 | 0.0634 | 0.0634 | 0.1789 | 0.1789 | 0.1593 |
| 50 TB (inclusive) - 100 TB | 0.0585 | 0.1057 | 0.0911 | 0.0504 | 0.0504 | 0.1675 | 0.1675 | 0.1463 |
| 100 TB (inclusive) - 1 PB | 0.0504 | 0.0911 | 0.0813 | 0.0325 | 0.0325 | 0.1545 | 0.1545 | 0.1382 |
| ≥ 1 PB | 0.0455 | 0.0846 | 0.0715 | 0.0260 | 0.0260 | 0.1382 | 0.1382 | 0.1301 |

##### Billing details

- Billable item: Downstream traffic generated during LVB playback outside the Chinese mainland
- Billing rules: Fees are calculated by multiplying the total traffic consumed in a day in a billing region by the unit price of the corresponding tier.

##### Billing example

- Assume that you used the LVB service on January 4, 2022 and consumed 1 TB of downstream traffic in Hong Kong (China) and 6 TB of downstream traffic in France. On January 5, 2022, the following traffic fee would be billed:

0.0748 (USD/GB) x 1000 (GB) + 0.0634 (USD/GB) x 6000 (GB) = 445.2 USD.

- Downstream playback charges, however, upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the peak upstream bandwidth used in a day exceeds 100 Mbps. Upstream Push charges support on-demand configuration and push streaming Use usage-to-gradient independent billing.

#### Bill-by-bandwidth

##### Pricing

We bill bandwidth usage outside the Chinese mainland by region on a daily basis and adopt a tiered pricing approach. The fee is based on your peak bandwidth usage in a day. See below for the pricing tiers:

| Bandwidth Tier | Price (USD/Mbps/Day) |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Asia Pacific 1 | Asia Pacific 2 | Asia Pacific 3 | North America | Europe | Middle East | Africa | South America |
| 0-500 Mbps | 0.2049 | 0.6016 | 0.6228 | 0.1984 | 0.1984 | 0.9333 | 0.9333 | 0.8455 |
| 500 Mbps (inclusive) - 5 Gbps | 0.1854 | 0.5415 | 0.6049 | 0.1805 | 0.1805 | 0.9203 | 0.9203 | 0.8276 |
| 5 Gbps (inclusive) - 20 Gbps | 0.1707 | 0.4829 | 0.5561 | 0.1681 | 0.1681 | 0.9008 | 0.9008 | 0.8065 |
| ≥ 20 Gbps | 0.1626 | 0.4228 | 0.5041 | 0.1593 | 0.1593 | 0.8911 | 0.8911 | 0.7967 |

##### Billing details

- Billable item: Downstream bandwidth used during LVB playback outside the Chinese mainland
- Billing rules: Fees are calculated by multiplying the highest bandwidth used in a day in a billing region by the unit price of the corresponding tier.

##### Billing example

- Assume that you used the LVB service on January 4, 2022 for playback in Macao (China) and your bandwidth usage reached 600 Mbps at the highest. On January 5, 2022, the following bandwidth fee would be billed:

0.1854 (USD/Mbps) x 600 (Mbps) = 111.24 USD.

- Downstream playback charges, however, upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the peak upstream bandwidth used in a day exceeds 100 Mbps. Upstream Push charges support on-demand configuration and push streaming Use usage-to-gradient independent billing.

## **Upstream Push Billing**

- Upstream Push is not billed by default.
- Upstream usage will only be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the highest upstream bandwidth used in a day exceeds 100 Mbps.The billing method, tiered pricing rules, and billing regions for upstream traffic inside/outside the Chinese mainland are **the same as** those for [LVB downstream traffic](https://www.tencentcloud.com/document/product/267/2818#30ba7559-3d05-4e6f-90bc-f9f9fd86e56f). Upstream traffic became a billable item starting at 00:00 (UTC+08:00), July 1, 2021.
- For example:

Suppose you consumed 9 GB of downstream traffic and 1 GB of upstream traffic in **Asia Pacific 1** one day, and the peak bandwidth on that day was 101 Mbps. Because the ratio of downstream traffic to upstream traffic is 9:1, which is smaller than 10:1, and the peak upstream bandwidth usage is higher than 100 Mbps, the following traffic fee would be billed:

Upstream traffic fees + Downstream traffic fees = 0.0748 (USD/GB) x (9 GB + 1 GB) = 0.748 USD.

## **Channel Service Billing**

- By default, Cloud Streaming Services do **not charge** for channel services. However, if your peak monthly channel count exceeds 100 (i.e., the peak concurrent push streams in a month exceed 100) and the resource utilization is relatively low, such as in video surveillance scenarios or exam proctoring scenarios, Tencent Cloud's business representatives will contact you to negotiate the payment for channel service fees. **If you have not received any related notifications, there is no need to be concerned.**
- Channel Service Price: 8.34 USD/Peak Channel Count/Month. Channel Service Fee = Channel Service Price (USD/Channel/Month) × Peak Channel Count (Channels) × Monthly Valid Days Coefficient (Months).
- For example:

User A is in a video surveillance scenario and uses Cloud Streaming Services in June. The peak channel count for the month is 300 channels, and the channel resource utilization is extremely low. The valid number of days for channel service in the month is 10 days (if the daily channel count is not 0, it is considered a valid day).

Channel Service Fee = 8.34 (USD/Channel/Month) × 300 (Channels) × (10 / 30) (Months) = 834 USD.


---
*Source: [https://www.tencentcloud.com/document/product/267/2818](https://www.tencentcloud.com/document/product/267/2818)*
