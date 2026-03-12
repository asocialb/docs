# Live Stream Moderation

CSS enables intelligent moderation and audiovisual erasure of live streams (including sensitive word muting and privacy frame removal), comprising three cost components: [Image Moderation](#cc7ba988-9fe1-4672-af6e-e3e6c2e23537), [Streaming Audio Moderation Service](#084fabcd-284e-4a9c-ab52-da06db07be02), and [Basic Fees for Value-Added Features](#5aac5a2e-c2ca-44db-a663-3230b1bd6df3).Image Moderation fees are calculated based on the total number of images reviewed during the month, Streaming Audio Moderation Service fees are determined by the total duration of audio reviewed daily, Violation Mute function is settled based on the total duration of muting, and the Frame Removal function is settled based on the usage duration.

## Notes

- The screenshots and audio flagged during image moderation and audio moderation are stored in COS and will incur COS storage fees. For detailed pricing, refer to [COS Product Pricing](https://intl.cloud.tencent.com/pricing/cos).
- While using the image moderation service, the first 1,000 screenshots moderated per month are free. Any additional image moderation beyond this quota will be billed separately.
- Usage deduction for screen audit occurs during use. You must ensure that your account is not overdue. If your account is in an overdue state (negative balance and overdue credit account), the usage deduction will fail.
- Using Smart Erasing (Violation Mute) incurs Basic Fees for Value-Added Features as well as [Intelligent Identification](https://www.tencentcloud.com/document/product/1041/49204?lang=en#intelligent-content-recognition) charges under the [Media Processing Service (MPS)](https://console.tencentcloud.com/mps/index). For erasure durations of less than one minute, billing is rounded up to one full minute.

## Image Moderation Pricing

| Number of screenshots used for moderation | Price (USD/thousand images) | Note |
| --- | --- | --- |
| ≤ 1,000 | 0 USD | The first 1,000 screenshots per month are free. |
| > 1,000 | 0.2294 USD | If the number of screenshots is less than 1,000, it will be considered as 1,000 for billing purpose. |

> Note:If screenshots used for image moderation are stored in a COS bucket located outside the Mainland China region, additional [COS](https://www.tencentcloud.com/document/product/436/6222) public network downstream traffic fees will be incurred. For detailed pricing of each billable item in COS,  refer to [COS Product Pricing](https://buy.tencentcloud.com/price/cos/overview).

### Billing Overview

- Billable Item: Number of screenshots
- Billing Mode: Pay-as-you-go
- Billing Cycle: Monthly billing. The fees incurred in the previous calendar month are billed and charged between the 1st and 5th day of each month. Detailed billing and invoice schedules are based on the actual bills.
- Billing Rule: The number of screenshots used for image moderation within a calendar month, minus the free quota of 1,000 screenshots, multiplied by the unit price.

### Billing Example

Suppose you used the image moderation service from January 1 to February 1, 2023, and the total number of screenshots for the month was 168,000. The image moderation fee you would need to pay on February 2, 2023, would be calculated as follows: January image moderation fee = 0.2294 (USD/1,000 images) x (168 - 1) thousand images = 38.3098 USD.

## Audio Moderation Pricing

Live stream audio moderation supports both daily and monthly billing modes. The default billing mode is daily billing.

Billing Mode: Charges are calculated based on the original AAS duration.

| Billable Item | Price (USD/Minute) |
| --- | --- |
| Duration of moderated audio segments | 0.0021 |

### Billing Overview

- Billable Item: Duration of moderated audio segments.
- Billing Mode: Pay-as-you-go.
- Billing Cycle: For daily billing, costs incurred on the previous day are settled and charged from your account at 10:00 AM every day. For monthly billing, the costs incurred during the previous month are settled and charged from your account between the 1st and 5th day of each month. Detailed billing and invoice schedules are based on the actual bills.

#### Billing Example

Suppose, on January 1, 2023, you used the audio moderation service for a total duration of 100 minutes. The fee you would need to pay on January 2, 2023, would be calculated as follows:

January audio moderation fee = 0.0021 (USD/min) × 100 (min) = 0.21 USD.

> Note:If your usage of the audio moderation service is extensive and a daily billing mode is unable to meet your requirements, you are welcome to contact us to request special pricing and billing methods. Please feel free to [submit a ticket](https://console.tencentcloud.com/workorder/category) for further consultation.

## Basic Fees for Value-Added Features

Cloud Streaming Services (CSS) Basic Fees for Value-Added Features include Standby streams, Delayed playback, and other types. The following describes the Basic Fees for Value-Added Features generated when using the Smart Erasing feature. For more details, see the [Basic Fees for Value-Added Features](https://www.tencentcloud.com/document/product/267/51555).

### Pricing

| Type | Price (USD/Billing Unit) |
| --- | --- |
| Unit price | 0.01515 |

**Ratio of billing duration to actual duration**:

| Value-added Feature | RatioBilling Duration (Billing Unit):Actual Duration (Minute) |
| --- | --- |
| Smart Erasing（Violation Mute） | 3.2 **:** 1 |
| Smart Erasing（Frame Removal） | 20 **:** 1 |

### Billing Details

- Item: Value-added feature
- Billing mode: Pay-as-you-go
- Billing cycle: Daily. The fee generated each day will be deducted from your account the following day. For the actual fee deduction and bill generation time, see your billing statement.

### Calculation Formula

- Billing duration = Actual duration × Ratio
- Fee = Unit price × Billing duration

#### Billing Examples

If you used both the Violation Mute and privacy frame removal functions of Smart Erasing on February 5, 2026, and during a 20-minute live stream there were 6 muting instances recorded as 10 minutes in total, while the frame removal function was active for 15 minutes, the Basic Fee for Value-Added Features bill generated on February 6, 2026, would be as follows:

0.01515 (USD/billing unit) × 3.2 (billing unit/minute) × 10 (minutes)  + 0.01515 (USD/billing unit) × 20 (billing unit/minute) × 15 (minutes)  = 5.0298 USD.


---
*Source: [https://www.tencentcloud.com/document/product/267/58267](https://www.tencentcloud.com/document/product/267/58267)*
