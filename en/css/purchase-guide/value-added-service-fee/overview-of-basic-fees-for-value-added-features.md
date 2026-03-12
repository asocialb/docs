# Overview of Basic Fees for Value-Added Features

Cloud Streaming Services (CSS) offers a variety of value-added features, including standby streams, delayed playback, local relay mode, and stream mix matting. These features are paid value-added services. When using these value-added features, select appropriate value-added services based on your actual business needs. The specific pricing and billing rules are as follows:

## Notes

- In addition to value-added service fees, the use of standby streams may also incur [traffic and bandwidth fees](https://www.tencentcloud.com/document/product/267/2819).
- In instances where the duration of a single standby stream is less than 1 minute, it will be billed as 1 minute.
- In addition to value-added service fees, the use of the delayed playback feature may also incur [traffic and bandwidth fees](https://www.tencentcloud.com/document/product/267/2819).
- In addition to value-added service fees, the use of the local relay mode may also incur [relay fees](https://www.tencentcloud.com/document/product/267/41059).
- The CSS stream mix API offers stream mix matting capabilities. Using the stream mix matting feature will incur stream mix matting fees.
- Using Smart Erasing (Violation Mute) incurs Basic Fees for Value-Added Features as well as [Intelligent Identification](https://www.tencentcloud.com/document/product/1041/49204?lang=en#intelligent-content-recognition) charges under the [Media Processing Service (MPS)](https://console.tencentcloud.com/mps/index). For erasure durations of less than one minute, billing is rounded up to one full minute.

## Image Moderation Pricing

## Pricing

| Type | Price (USD/Billing Unit) |
| --- | --- |
| Unit price | 0.01515 |

**Ratio of billing duration to actual duration:**

| Value-added Feature | RatioBilling Duration (Billing Unit):Actual Duration (Minute) |
| --- | --- |
| Standby streams | 1.6 : 1 |
| Delayed playback | 0.05 : 1 |
| Local relay mode | 0.02 : 1 |
| Stream mix matting | 1 : 1 |
| Smart Erasing（Violation Mute） | 3.2 : 1 |
| GenerateEffect | 60 ：1 |
| SendEffect | 15 ：1 |

## Billing Details

- Item: Value-added feature
- Billing mode: Pay-as-you-go
- Billing cycle: Daily. The fee generated each day will be deducted from your account the following day. For the actual fee deduction and bill generation time, see your billing statement.

## Calculation Formula

- Billing duration = Actual duration x Ratio
- Fee = Unit price x Billing duration

## Billing Examples

### Billing Example of Standby Streams

The live domain names of streams A and B are configured with standby streams. On October 16, 2023, the streams were automatically switched to the standby stream input sources due to unexpected interruptions multiple times. The following table lists the start and end time of the standby streams:

| Stream ID | Standby Stream Start Time (Hour:Minute:Second) | Standby Stream End Time (Hour:Minute:Second) | Billing Duration (Actual Duration × Ratio) |
| --- | --- | --- | --- |
| A | 00:00:05 | 00:00:25 | 1 minute × 1.6 |
| A | 00:00:28 | 00:00:55 | 1 minute × 1.6 |
| B | 00:00:50 | 00:03:49 | 3 minutes × 1.6 |

- Stream A: Billing duration of the standby stream = (1 minute + 1 minute) × 1.6 billing units/minute = 3.2 billing units
- Stream B: Billing duration of the standby stream = 3 minutes × 1.6 billing units/minute = 4.8 billing units

### Billing Example of Delayed Playback

Assume that you used the delayed playback feature for a total of 60 minutes on June 15, 2023. The bill generated on June 16, 2023 would be as follows:

0.01515 (USD/billing unit) x 0.05 (billing unit/minute) x 60 (minutes) = 0.04545（USD）

### Billing Example of the Local Relay Mode

Assume that you enabled the local mode for a relay task on November 23, 2022. The duration of the task was 100 minutes, including 60 minutes of local files. On November 24, 2022, you would need to pay the following fees:

- Relay fee: 0.00032 (USD/minute) x 100 (minutes) = 0.032 (USD)
- Value-added feature fee: 0.01515 (USD/billing unit) x 0.02 (billing unit/minute) × 60 (minutes) = 0.01818 (USD)

### Billing Example of Stream Mix Matting

If you solely used the stream mix matting feature for a total of 60 minutes on November 13, 2024, the bill generated on November 14, 2024 would be as follows:

0.01515 (USD/billing unit) × 1 (billing unit/minute) × 60 (minutes) = 0.909 (USD)

### Billing Example for Smart Erasing (Violation Mute)

If you utilized the Smart Erasing feature on May 12, 2025, and muted the audio 6 times for a total of 10 minutes during a 20-minute live stream, the Basic Fees for Value-Added Features bill generated on May 13, 2025, would be as follows:

0.01515 (USD/billing unit) × 3.2 (billing unit/minute) × 10 (minutes) =  0.4848(USD)

### Billing Examples of Generate Effect and Send Effect

If you use the feature of generating a video with special effects from text twice and the feature of sending a video with special effects ten times on May 28, 2025, the bill amount you need to pay for using AI Cloud-based Effects on May 29, 2025 will be as follows:

- Basic fee for the value-added feature (Generate Effect): `0.01515 (USD/billing unit) × 60 (billing unit/times) × 2 times = 1.818 (USD)`
- Basic fee for the value-added feature (Send Effect): `0.01515 (USD/billing unit) × 15 (billing unit/times) × 10 times = 2.2725 (USD)`


---
*Source: [https://www.tencentcloud.com/document/product/267/51555](https://www.tencentcloud.com/document/product/267/51555)*
