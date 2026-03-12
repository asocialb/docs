# Overview

In the CSS console, you can manage domain name and streams, configure transcoding, recording, and acceleration, as well as push streams (web) and monitor resources.

## Prerequisites

- You have activated [CSS](https://intl.cloud.tencent.com/product/css).
- You have logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).

## Overview

Click [Overview](https://console.tencentcloud.com/live/livestat) in the left navigation bar.

- **Quickly establish** your personalized live streaming service. You may refer to the relevant guidelines, add domains, generate URLs, explore the live streaming development guide, and swiftly navigate to live streaming features.
- You can click the "**Health Report**" card located at the upper-right corner of the Overview page to access the Live Health Report. For more details, please refer to [Health Report.](https://www.tencentcloud.com/document/product/267/70558#)
- You can view relevant data, including real-time downstream bandwidth, today's downstream traffic, the current number of pushes, concurrent connections, and trends for billed bandwidth, billed traffic, and the number of pushes over the past 30 days. Additionally, you can view**Health Report** and **Plans** consumption details. You can switch **Billing Mode** or change the time granularity as needed. For beginner's guidance, you can click the **Guide** in the upper right corner to view instructions for getting started with CSS.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/193a03a8533711f0989352540044a08e.png)

### Today's Data

This section displays the downstream peak bandwidth, downstream traffic usage, the current number of push channels, and the number of concurrent connections of the day.

| Item | Description |
| --- | --- |
| Current Downstream Bandwidth | The peak bandwidth consumed for acceleration by all playback domain names. |
| Today's Downstream Traffic | The total traffic consumed for acceleration by all playback domain names on the current day. |
| Current Push Channels | The number of current push channels. |
| Concurrent Connections | If the playback protocol is RTMP or FLV, **Concurrent Connections** indicates the number of online viewers.If the playback protocol is HLS, **Concurrent Connections** cannot be used as an indication of the number of online viewers. |

### Usage Trends

This section displays usage trends ( **Bandwidth Trend**, **Traffic Trend**, and **Push Channels**) for today, yesterday, the last 7 days, and the last 30 days.

| Item | Description |
| --- | --- |
| Bandwidth Trend | The sum of the peak bandwidth consumed for acceleration by all playback domain names in the query period. |
| Traffic Trend | The total traffic consumed for acceleration by all playback domain names in the query period. |
| Push Channels | The number of push channels under the selected domain names in the query period. |

#### Changing the Granularity

You can click the drop-down list box next to **Granularity** to change the granularity of the usage trend data.

Bandwidth Trend

Traffic Trend

Push Channels

![](https://staticintl.cloudcachetci.com/cms/backend-cms/339f85d0533711f095fc5254001c06ec.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/43057264533711f090d5525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5b939ed4533711f0abce52540099c741.png)

### Resource Package

> **Note:**The remaining amount of resource packages displayed on the overview page is not real-time data. The update time coincides with the settlement time of the account statement.

#### Viewing Resource Package Consumption Details

- Click  **Manage**  on the right to enter the [Resource Package/Plugin Management](https://console.tencentcloud.com/live/resources/package?type=traffic) page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/82a35d4e533711f0989352540044a08e.png)

- You can view the  **Usage** ,  **Creation Time** ,  **Expiration Time** ,  **Status** , and  **Auto-renewal** of traffic resource packages/transcoding resource packages.
- Auto-renewal (renew automatically when it is exhausted or expired) is supported for streaming traffic resource packages and streaming transcoding resource packages (including standard transcoding and top speed codec transcoding). For details, see [Renewal](https://www.tencentcloud.com/document/product/267/53309) documentation.
- **Purchasing Traffic Resource Package:**  Click Buy under the traffic package statistics, and you will enter the [CSS Traffic Resource Package Purchase Page](https://buy.intl.cloud.tencent.com/live?type=transcode) to purchase related packages.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b0564898533711f090d5525400bf7822.png)

> **Note:** For information on billing prices, see [Billing Overview](https://intl.cloud.tencent.com/document/product/267/2819).

### Billing

- **Switching Billing Mode** 
Based on your actual business needs, if your current billing mode is daily bill-by-traffic or daily bill-by-bandwidth, you can click  **Switch**  to change the billing mode.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/db3702cb119611ef9483525400720cb5.png)

- To view billing switch reminders, click  **Confirm**  to complete the switch of billing mode. For more detailed information on billing changes, see [Changing Billing Modes](https://intl.cloud.tencent.com/document/product/267/30411).

Chinese Mainland Billing Mode:

Outside Chinese Mainland Billing Mode:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d72fcdc3533711f0a63e525400e889b2.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e2a6f800533711f090d5525400bf7822.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/31054](https://www.tencentcloud.com/document/product/267/31054)*
