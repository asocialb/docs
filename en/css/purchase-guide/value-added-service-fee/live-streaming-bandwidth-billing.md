# Live Streaming Bandwidth Billing

Tencent Cloud provides a bandwidth guarantee for customers during business peak hours, such as business deployment, business launch, and operation activity promotion. In this way, the stable and efficient operation of customer systems on the cloud can be ensured, and the need for coping with customer business peaks can be met.

If the business is expected to experience a large-scale surge, contact the account manager at least three working days in advance to apply for a bandwidth guarantee. You can apply for a bandwidth guarantee in advance for any of the following large-scale surge scenarios.

- The daily peak bandwidth increase is greater than 500 Gbps.
- The number of requests exceeds 3 times the monthly average of daily peaks in the last month, and the monthly average of daily peaks is not less than 50 Gbps.
- The increase exceeds 100% of the monthly average of daily bandwidth peaks in the last month, and the increased bandwidth exceeds 200 Gbps.

## Must-Knows

- A bandwidth guarantee can be applied only when LVB in monthly billing mode is used for downstream playback.
- The guaranteed bandwidth cannot be less than 200 Gbps.

## Pricing

| Region | Price (USD/Mbps/Day) |
| --- | --- |
| Chinese mainland | 0.1024 |
| Hong Kong (China), Macao (China), Taiwan (China), and regions outside the Chinese mainland | 0.1789 |

## Billing Overview

- Billing item: Live streaming bandwidth peak.
- Billing mode: Daily postpaid billing.
- Billing rules: Calculate separately the daily LVB peak downstream bandwidth on the day of bandwidth guarantee of regions in the Chinese mainland and regions outside the Chinese mainland, including Hong Kong (China), Macao (China), and Taiwan (China). If the peak bandwidth exceeds the set guaranteed bandwidth, the billing is based on the actual daily peak bandwidth. If it does not exceed the set guaranteed bandwidth, the billing is based on the set guaranteed bandwidth.

## Billing Examples

LVB is billed monthly by traffic in regions in the Chinese mainland and billed monthly by bandwidth in regions outside the Chinese mainland, including Hong Kong (China), Macao (China), and Taiwan (China). On June 6, 2023, the guaranteed bandwidths of 500 Gbps and 700 Gbps were set for regions in and outside the Chinese mainland, respectively. The actual daily peak bandwidth was 550 Gbps in regions in the Chinese mainland and 600 Gbps in regions outside the Chinese mainland. The bandwidth guarantee fee incurred on June 7, 2023 is as follows:

550 Gbps x 1,000 x 0.1024 (USD/Mbps/day) + 700 Gbps x 1,000 x 0.1789 (USD/Mbps/day) = 181,550 USD

Before the monthly LVB bill is issued on July 1, 2023, the actual usage on June 6, 2023 will be removed first before the LVB bandwidth usage of June 2023 is calculated.


---
*Source: [https://www.tencentcloud.com/document/product/267/69871](https://www.tencentcloud.com/document/product/267/69871)*
