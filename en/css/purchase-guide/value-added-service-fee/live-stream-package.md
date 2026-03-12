# Live Stream Package

CSS offers live stream package capabilities, supporting various playback protocols such as LL-HLS and DASH. By encapsulating configurations, it enables the segmentation of live streams into smaller fragments, delivering a significantly lower-latency streaming experience.

The billing rules for utilizing the Live Stream Package feature are outlined as follows:

## Must-Knows

- To utilize the packaging feature, it is necessary to complete the packaging configuration in advance. Packaging charges are triggered upon stream pulling. If the pulled stream is a transcoded stream, only [transcoding fees](https://www.tencentcloud.com/document/product/267/39604) will be incurred, with no packaging fees. However, if the pulled stream is an original stream, **packaging fees** will be applied.
- The live streaming encapsulation protocols include HLS - CMAF, DASH - ISO, DASH - CMAF, LL-HLS - TS, LL-HLS - CMAF, as well as DRM encapsulation when utilizing DRM functionality. Each encapsulated stream is billed separately.
- When the duration of a Live Stream Package task is less than one minute, billing will be calculated based on a minimum duration of one minute for the Live Stream Package.

## Pricing

Billing is based on the duration of pulling the original encapsulated stream.

| Billable Item | Price (USD/Min) |
| --- | --- |
| Live Stream Package | 0.005 |

### Billing details

- Billable item: Duration of Live Stream Package Tasks.
- Billing mode: Pay-as-you-go
- Billing cycle: Daily billing. The fees generated each day are deducted at 10:00 AM or whenever your daily bill is generated the following day.
- Billing rules: Charges for the Live Stream Package task are based on its duration, with any time less than one minute rounded up to a full minute.

### Billing examples

Suppose you utilized the Live Stream Package feature on June 1, 2025, and retrieved the original encapsulated streams, including pulling the HLS-CMAF original stream for 50 minutes and the LL-HLS-TS original stream for 50 minutes. The billing statement generated on June 2, 2025, would be as follows:

0.005（USD/minute）×（ 50+ 50 ）（minutes）= 0.5 (USD)

> **Note:**If your business volume is large and daily billing cannot meet your needs, you are welcome to contact us to request special pricing and billing methods. Please feel free to [submit a ticket](https://console.tencentcloud.com/workorder/category) for further consultation.


---
*Source: [https://www.tencentcloud.com/document/product/267/72669](https://www.tencentcloud.com/document/product/267/72669)*
