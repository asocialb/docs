# Announcement on the Official Billing for CSS Standby Streams Feature

Standby Stream will become a paid feature starting from **00:00 (UTC+8) on October 1, 2023.**See below for the pricing and billing details：

## Must-Knows

- Using the Standby Stream feature may not only incur extended feature fees but also [traffic/bandwidth costs](https://www.tencentcloud.com/document/product/267/2819).
- If the duration of a single Standby Stream is less than 1 minute, it will be billed as a 1-minute Standby Stream duration.

## Pricing

| Type | Unit cost |
| --- | --- |
| Price (USD/Billing Unit) | 0.01515 |

**Ratio of billing duration to actual duration:**

| Extended Feature | RatioBilling Duration (Billing Unit) : Actual Duration (Minutes) |
| --- | --- |
| Standby Stream | 1.6 : 1 |

## Billing Details

- Item: Extended feature
- Billing mode: Pay-as-you-go.
- Billing cycle: Daily. The fee generated each day will be deducted from your account the following day. For the actual fee deduction and bill generation time, see your billing statement.

## Calculation Formula

- Billing duration = Actual duration x Ratio
- Fee = Unit price x Billing duration

## Billing Example

A and B, two live streams with standby stream templates configured for their live stream domain names, have switched to standby input sources multiple times due to unexpected interruptions during the period of October 16, 2023. The specific start and end times of the standby streams are shown in the table below:

| Stream ID | Standby Stream Start Time | Standby Stream End Time | Billing duration (Actual duration x Ratio) |
| --- | --- | --- | --- |
| A | 00:00:05 | 00:00:25 | 1 Minute  × 1.6 |
| A | 00:00:28 | 00:00:55 | 1 Minute  × 1.6 |
| B | 00:00:50 | 00:03:49 | 3 Minutes × 1.6 |

- Live Stream A, `Standby Stream Billing Duration = (1 minute + 1 minute) × 1.6 billing units/minute = 3.2 billing units `
- Live Stream B, `Standby Stream Billing Duration = 3 minutes × 1.6 billing units/minute = 4.8 billing units`

On October 17, 2023, the extended feature fees bill you need to pay due to the standby streams is:

8 (billing units) × 0.01515 (USD/billing unit) = 0.1212 USD.

If you have any questions, please feel free to contact us at any time. We sincerely appreciate the trust and support of all users for Tencent Cloud Cloud Streaming Services (CSS) products!

**2023-08-31**

**Tencent Cloud Team**


---
*Source: [https://www.tencentcloud.com/document/product/267/56728](https://www.tencentcloud.com/document/product/267/56728)*
