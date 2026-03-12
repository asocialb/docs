# Billing FAQs

## Live Streaming

### What are the billable items of CSS? What fees do I need to pay?

- **Basic service fees** are billed based on the downstream traffic/bandwidth consumed for connecting with cache origin servers. Traffic/bandwidth is consumed whenever your live streams are played.

> **Note**CSS provides two billing modes: bill-by-traffic and bill-by-bandwidth. For the billing details, see [Basic Services](https://intl.cloud.tencent.com/document/product/267/2818). To change your billing mode, see [Changing Billing Modes](https://intl.cloud.tencent.com/document/product/267/30411).

- **Value-added service fees** are incurred if you use the transcoding, recording, screencapture, or porn detection feature. The features are disabled by default. For details, see “Value-Added Service Fees” in [Pricing Overview](https://intl.cloud.tencent.com/document/product/267/2819#value-added-service-fees).
- **Extended service fees** are incurred if you use CSS features that rely on the capabilities of other Tencent Cloud products. The fees are charged according to the billing rules of the corresponding products. For details, see “Extended Service Fees” in [Pricing Overview](https://intl.cloud.tencent.com/document/product/267/2819#extended-service-fees).

### How can I know whether my account has overdue payments?

Log in to the [CSS console](https://console.tencentcloud.com/live) and click **Billing Center** in the top right corner to view your balance. Your account has overdue payments if the available balance is negative. To continue using CSS and other services, please make the payment in a timely manner.

### Will I be charged for pushing streams?

- Upstream Push is not billed by default.
- Upstream usage will also be billed if the ratio of downstream traffic to upstream traffic is smaller than 10:1 and the highest upstream bandwidth used in a day exceeds 100 Mbps.The billing method, tiered pricing rules, and billing regions for upstream traffic inside/outside the Chinese mainland are **the same as** those for [LVB downstream traffic](https://www.tencentcloud.com/document/product/267/2818#30ba7559-3d05-4e6f-90bc-f9f9fd86e56f). Upstream traffic became a billable item starting at 00:00 (UTC+08:00), July 1, 2021.

### When are value-added service fees incurred?

If you bind recording, screencapture, porn detection, or watermarking templates to push domains, fees are incurred when streams are pushed. If you bind the templates to playback domains, fees are incurred when streams are played. This means if you create a transcoding template and bind it to a playback domain name, as long as you do not use the domain for playback, no transcoding fees will be charged. Using the watermarking or stream mix feature may incur standard transcoding fees, which are based on the resolution of output streams.

### In Live Video Caster PGM output, what is the playlist type? What is the universal type?

- Playlist type: It means that the PGM output screen comprises only one stream, charged according to the [playlist type](https://www.tencentcloud.com/document/product/267/58538#).
- Universal type: It means that the PGM output screen comprises two or more streams, charged according to the [universal type](https://www.tencentcloud.com/document/product/267/58538#.E5.90.8E.E4.BB.98.E8.B4.B9.EF.BC.88.E6.8C.89.E4.BD.BF.E7.94.A8.E6.97.B6.E9.95.BF.E8.AE.A1.E8.B4.B9.EF.BC.89).

The figure on the left is the playlist type, and the figure on the right is the universal type:

### ![](https://staticintl.cloudcachetci.com/cms/backend-cms/31c5d880af9111ee9fd6525400bb593a.png)

### Are there two expenses for porn detection?

- CSS offers a free tier of 1,000 screenshots per month for the screencapture feature.
- CSS offers a free tier of 1,000 screenshots per month for porn detection.

For details, see [Live Screencapture](https://intl.cloud.tencent.com/document/product/267/39606) and [Intelligent Porn Detection](https://intl.cloud.tencent.com/document/product/267/39607).

### Can I track my usage of CSS packages in real time?

You can view your package usage in the [CSS console](https://console.tencentcloud.com/live/resources/package?type=traffic), but real-time usage statistics are not supported currently.
Your usage each day is not reflected in the data until billing is processed by the system the following day (the exact time may vary).

### Can I allow only paid users to access my content?

CSS cannot identify paid users currently. If you record your live streams and save them to VOD, you can allow only paid users to access your content by encrypting the videos.

### Why is the traffic usage data shown in the console different from the log data?

- TCP/IP headers: Each TCP/IP HTTP request packet can be up to 1,500 bytes, including 40-byte TCP and IP headers. The traffic consumed by headers (about 3% of the total) is not counted into application layer data.
- TCP retransmission: About 3-10% of packets are lost during transmission. The packets will be sent again by the server. Such traffic (about 3-7% of the total) is not counted by the application layer either.

As an industry standard, billable traffic is application-layer traffic plus the additional traffic described above. Tencent Cloud calculates the additional traffic as 10% of the total, so the traffic usage shown in the console is 110% of that recorded in logs.

## Prepaid Packages

### I purchased traffic packages. Why were fees still deducted from my account balance?

- If you are on daily bill-by-bandwidth mode, your traffic packages cannot be used for deduction. You can change your billing mode in the console. For details, see [Changing Billing Modes](https://intl.cloud.tencent.com/document/product/267/30411).
- If you are on daily bill-by-traffic mode and fees are still deducted from your account balance, check if you have used [value-added services](https://intl.cloud.tencent.com/document/product/267/2819) such as live transcoding, live recording, screencapture, and porn detection. Value-added services are billed based on usage. Your usage each day is billed the following day. You can also buy packages for value-added services. CSS offers three types of packages: traffic package, standard transcoding package, and Top Speed Codec (TSC) transcoding package. To learn more, see [Prepaid Packages](https://www.tencentcloud.com/document/product/267/52220).
- Fees are also incurred after you use up your packages. You can view the deduction details in [Bill Details](https://console.tencentcloud.com/expense/bill/summary). For detailed directions, see [Viewing Bills](https://intl.cloud.tencent.com/document/product/267/36278).

### I only bought traffic packages. Will CSS suspend services for my account after I use up the packages?

- If your billing mode for LVB is daily bill-by-traffic, downstream LVB traffic will be deducted from your traffic packages first, and the additional usage will be billed daily at tiered pay-as-you-go rates.
- After you use up your packages, make sure there is sufficient balance in your account to pay your daily pay-as-you-go charges. If you have overdue payments, please top up within 24 hours. Otherwise, services will be suspended for your account. We recommend you check your [account balance](https://console.tencentcloud.com/expense/overview) regularly.

> **Note**Traffic packages cannot be used for deduction if you are on monthly bill-by-traffic mode or monthly/daily bill-by-bandwidth mode.

## Transcoding

### How is live transcoding billed? How can I estimate the cost?

**Example:** Suppose on January 1, 2021, you transcoded stream A to H.264_720P (one hour) and added watermarks to stream B (30 minutes; output resolution: 480p).
On January 2, 2021, your transcoding fees would be 0.0057 (USD/min) x 60 (min) + 0.0028 (USD/min) x 30 (min) = 0.426 USD.

### I didn’t use the live transcoding feature. Why were transcoding fees incurred?

Transcoding services include live transcoding, stream mixing, and watermarking. Using the stream mixing or watermarking feature will also incur transcoding fees.

### Does stream mixing always incur transcoding fees?

## Live Recording

### How is live recording billed?

The billing for the live recording feature is based on the peak concurrent recording value for the month. If the recording is stored in COS, charges will also be applied for the total duration of the recording delivered to COS. Each live recording is considered as one recording channel; if you record in two formats (MP4 and HLS) and the recording lasts for one hour, it will be counted as two recording channels, and the total duration of the recording delivered to COS will be counted as two hours.

### How is the peak number of concurrent recording channels calculated?

One stream (stream ID) recorded in one format is counted as one recording channel. The number of concurrent recording channels is collected every five minutes, and the highest number each month is used for billing.
**Example:**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/79031266af9011eeb2a1525400170219.png)

> **Note**Yellow: Recording tasks for stream **A**.Green: Recording tasks for stream **B**.Blue: Recording tasks for stream **C**.

### Why was I charged 10.5882 USD after using live recording?


---
*Source: [https://www.tencentcloud.com/document/product/267/38284](https://www.tencentcloud.com/document/product/267/38284)*
