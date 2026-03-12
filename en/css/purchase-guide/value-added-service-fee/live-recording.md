# Live Recording

The Cloud Streaming Services (CSS) can be used to record live streams and store them in the Video On Demand (VOD) or Cloud Object Storage (COS). Using the recording feature will incur charges, which consist of the fees for peak number of recording channels and COS delivery service fees. The COS delivery service fees for recordings will only be incurred when recordings are stored in the COS. **The fees for peak number of recording channels are calculated by the peak number of concurrent recording channels during the month, while the COS delivery service fees are calculated by the total duration of live recording during the month.**

## Must-Knows

- The recording feature is disabled by default and can be enabled in the console or through TencentCloud APIs.
- Videos recorded are saved to the [VOD](https://console.tencentcloud.com/vod/overview) or [COS](https://console.tencentcloud.com/cos) by default, which will incur corresponding [VOD fees](https://www.tencentcloud.com/document/product/266/2838) or [COS fees](https://www.tencentcloud.com/document/product/436/16871). Ensure that the VOD service is in normal use after enabling the recording feature. Unavailability of the VOD service due to non-activation or overdue payment will make it impossible to record live streams, during which no recording files or charges will be generated.
- For information on how to calculate the peak number of recording channels, see [CSS Billing](https://intl.cloud.tencent.com/document/product/267/32479).

## Peak number of recording channels

### Pricing

| Billable Item | Price (USD/Channel/Month) |
| --- | --- |
| Peak number of recording channels | 5.2941 |

### Billing details

- Billable item: The number of live recording channels.
- Billing mode: Pay-as-you-go.
- Billing cycle: Monthly. The recording fees incurred each month are deducted within the first five days of the following month. For details, see your billing statement.

### Calculation formula

- Percentage of recording days = Number of days the recording feature is used during a month / Total number of days in that month.
- Recording fees = Peak number of concurrent recording channels in a month x Percentage of recording days x Unit price.

> **Note:** The peak number of concurrent recording channels during a month is the highest number of recording channels occurring at the same time during the month (the data is collected every five minutes). Each recording format is counted as one recording channel. For example, if the same stream is recorded into MP4 and HLS, they will count as two recording channels.

### Billing examples

Suppose a user bound recording templates to domain A and domain B in the CSS console. According to the templates, the streams of domain A are recorded into **one** format and those of domain B are recorded into **two** formats. Domain A had 11 live streams on April 2, 2020 and 10 live streams on another five days of that month. Domain B had one live stream on April 29, 2020. The recording days of domain A and domain B in April would be as follows:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/39c59266df5711eeb419525400ea3514.png)

- The number of peak recording channels on April 2, 2020 is **11** (11 channels for domain A x 1 format + 0 channels for domain B x 2 formats = 11 channels).
- The number of peak recording channels on April 29, 2020 is **12** (10 channels for domain A x 1 format + 1 channel for domain B x 2 formats = 12 channels).
- In April 2020, the number of recording days for domain A and domain B is 6 and 1 respectively. At the account level, the number of recording days is 6, and the percentage of recording days in April is 6 days / 30 days = 20%.

Therefore, the highest number of concurrent recording channels for April 2020 is 12, the percentage of recording days is 20%, and the live recording fees incurred is as follows:
Live recording fees for April = 5.2941 (USD/Channel/Month) x 0.2 x 12 channels = 12.70584 USD.

## Recording delivery to COS

### Pricing

If you record CSS streams to COS, an additional fee will be charged based on the recording duration of each recording channel.

| Billable Item | Price (USD/Min/Month) |
| --- | --- |
| Recording delivery to COS | 0.000096 |

### Billing details

- Billable item: Recording delivery to COS
- Billing mode: Pay-as-you-go
- Billing cycle: Monthly. The recording-delivery-to-COS fees incurred each month are deducted within the first five days of the following month. For details, see your billing statement.

### Billing examples

Suppose a user bound recording templates to domain A and domain B in the CSS console. According to the templates, the streams of domain A are recorded into one format and those of domain B are recorded into two formats. Domain A had 10 live streams on January 13, 2023, which lasted for 30 minutes. Domain B had one live stream on January 20, 2023, which lasted for 20 minutes. The recording-delivery-to-COS fee incurred for January 2023 would be as follows:
`0.000096 (USD/min/month) x (10 channels x 1 format x 30 minutes + 1 channel x 2 formats x 20 minutes) = 0.03264 USD`

## Recording Delivery to Third-Party Services

### Pricing

Fees are charged based on the total writing volume of recording files delivered to AWS S3 or GCS.

| Billable Item | Price ( `USD` /GB/Month) |
| --- | --- |
| Writing volume for recording delivery to third-party services | 0.11 |

### Billing Details

- Billable item: Recording delivery to third-party services.
- Billing mode: Pay-as-you-go.
- Billing cycle: Monthly. The recording-delivery-to-third-party-services fees incurred each month are deducted within the first five days of the following month. For details, see your billing statement.

### Billing Example

A user configured recording templates for domain names A and B (non-slow live streaming domain names) in the CSS console. According to the templates, the streams of domain name A were recorded in one format and those of domain name B were recorded in two formats. Domain name A had 10 live streams on November 13, 2024, resulting in 30 GB of recording files. Domain name B had one live stream on November 20, 2024, resulting in 20 GB of recording files. The fee of recording delivery to third-party services incurred in November 2024 is:

`0.11 (USD/GB/month) × (30 GB + 20 GB) = 5.5 USD` .


---
*Source: [https://www.tencentcloud.com/document/product/267/39605](https://www.tencentcloud.com/document/product/267/39605)*
