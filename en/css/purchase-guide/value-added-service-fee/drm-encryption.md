# DRM Encryption

CSS offers live streaming encryption, anti-recording, hotlink protection and other services based on DRM technologies like Widevine and FairPlay, safeguarding the security of live content. DRM encryption fees are calculated based on the number of successful Widevine or FairPlay playback requests each day.

## Must-Knows

- The DRM encryption is based on live transcoding. Using the DRM encryption feature will incur [live transcoding](https://www.tencentcloud.com/document/product/267/39604) fees.
- The DRM encryption feature is disabled by default. You can enable it in a transcoding template or using a TencentCloud API.
- The DRM encryption feature is a paid value-added service. The use of this feature will be charged based on the number of DRM License requests.

## Pricing

| Billable Item | Price (USD/Request/Day) |
| --- | --- |
| Number of DRM License requests | 0.0012 |

## Billing Details

- Billable item: Number of DRM License requests.
- Billing mode: Pay-as-you-go.
- Billing cycle: Daily billing. The DRM encryption fees each day will be deducted the next day when the bill is generated. The actual fee deduction and bill generation time may vary.

## Calculation Formula

DRM encryption fees = Daily number of DRM License requests × Unit price (USD/Request/Day).

## Billing Example

On August 15, 2024, a customer used the DRM encryption service. On this day, a total of 200 Widevine licenses and 300 FairPlay licenses were requested and successfully issued. The bill generated on August 16, 2024 is as follows:

DRM encryption fees: `200 + 300 (requests) x 0.0012 (USD/Request/Day) = 0.6 USD`.

> **Note:**If your business volume is large and the daily billing mode cannot meet your needs, you can contact our sales personnel. If you have any questions, please [submit a ticket](https://console.tencentcloud.com/workorder/category).


---
*Source: [https://www.tencentcloud.com/document/product/267/63267](https://www.tencentcloud.com/document/product/267/63267)*
