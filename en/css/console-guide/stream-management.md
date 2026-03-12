# Stream Management

Log in to the  CSS console and enter [Stream Management](https://console.tencentcloud.com/live/streammanage). Stream Management includes interrupting live streams and disabling live streams, as well as viewing **Live Streams**, **Primary/Backup Streams**, **Stream History**, **Disabled Streams**, and their detailed information. Here is a brief introduction and usage of these features:

## Live Streams Management

Log in to the CSS console, then navigate to [Stream Management](https://console.intl.cloud.tencent.com/live/streammanage) >**Live Streams**, and perform operations according to your actual business needs.

#### Preview live stream

In the Live Streams list, you can select the domain and corresponding online stream you want to query. Click "Preview" on the right to view the real-time live streaming image, Smart Highlight, and Smart Highlight information.

> **Note:**Smart Highlight and Summary are expected to be generated 5 minutes after the Live Stream begins.To view Smart Highlight and Intelligent Summary, you need to enable the [Smart Highlight](https://www.tencentcloud.com/document/product/267/74572) and [Intelligent Summary](https://www.tencentcloud.com/document/product/267/74570) features first.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fee53b28ca7911f09e745254007c27c5.png)

#### View streaming data

Click on the **streaming data** on the right side to view detailed information of the online live stream, such astraffic, bandwidth, frame rate, bitrate, etc.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7e4ec7d1ca9211f0b011525400bf7822.png)

#### Interrupt live stream

Click **Stream Interruption** on the right to interrupt the current live stream publishing.

> **Note:**After the interruption, the current live stream will stop publishing. You can resume the live stream by republishing with the same Stream Name.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/94955bb9ca9211f087ad52540099c741.png)

### Disable live stream

Click **Disable** to disable the live stream.

> **Note:**After disabling, the current live stream will stop publishing (republishing is not possible for the current Stream Name until it is re-enabled). You can manually resume it or it will be automatically enabled after 7 days by default.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b7bea8b2ca9211f0aedb525400454e06.png)

## Primary and backup stream management

The primary and backup stream feature refers to the system's ability to automatically merge and output two live streams with the same **Stream ID**. The primary stream's content is prioritized for playback. If there are issues with the primary stream's content, you can **automatically** or **manually** switch to the backup stream content to ensure the stability of the live image. The primary and backup streams can be enabled or disabled for optimal scheduling. When optimal scheduling is enabled, the system will dynamically evaluate the quality of each stream and select the highest-quality stream as the primary stream,

The primary and backup streams automatically become invalid after they end.

Log in to the CSS console, then navigate to [Stream Management](https://console.intl.cloud.tencent.com/live/streammanage) >**Primary/Backup streams**, and perform operations according to your actual business needs.

#### Preview live stream

Click **Preview**on the right to view the real-time live streaming image.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/466e49376ca511eea99b5254007bf3f5.png)

#### View stream data

Click on the **stream data** on the right side to view detailed information of the online live stream, such astraffic, bandwidth, frame rate, bitrate, etc.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6543d1626ca511eeb928525400669a4a.png)

#### Optimal Scheduling Management

##### Enable optimal scheduling

Click

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b15787c06ca511ee9a1c52540047987b.png)

，to enable optimal scheduling. When optimal scheduling is enabled, the system will dynamically evaluate the quality of each stream and select the highest-quality stream as the primary stream, The primary and backup streams automatically become invalid after they end.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e92ab1616ca511ee9b5f5254006efdda.png)

##### Disable Optimal Scheduling

Click

![img](https://staticintl.cloudcachetci.com/cms/backend-cms/2985159b6ca611ee9a1c52540047987b.png)

，to disable optimal scheduling.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4f7bc6666ca611ee9a1c52540047987b.png)

#### Primary and Backup Stream Switching

- Click on the left-pointing triangle to expand the manual switch to the standby option.
- Click the **Switch**on the right side to switch between the main and backup streams. By manually switching the main and backup streams, you can flexibly deal with issues that may arise during the live broadcast.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f88b9be66cc211ee8dd5525400bf7398.png)

## Stream History Management

Log in to the CSS console, then navigate to [Stream Management](https://console.intl.cloud.tencent.com/live/streammanage) >**Stream History**, You can query historical live stream data and perform operations according to your actual business needs.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cb64fcacca8e11f0b011525400bf7822.png)

#### Replay Historical Live Stream

In the historical stream list, you can select the domain name to be queried and the corresponding historical live stream. Click **Replay** to view Historical live screen, smart highlight, and intelligent summary information.

> **Note:**Replay requires that the [Time Shifting feature](https://www.tencentcloud.com/document/product/267/53312) be enabled first.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f34dc06dca8f11f0b011525400bf7822.png)

#### Disable Historical Live Stream

In the historical stream list, you can select the domain name to be queried and the corresponding historical live stream. Click **Disable** to disable the historical live stream.

> **Note:**After being disabled, the current live broadcast will stop pushing (streaming cannot be re-pushed until the current StreamName is restored). It can be manually restored or automatically enabled after 7 days by default.You can view stream history in the past 7 days under the **Stream History** tab or query records in the past month in [Stream Interruption Records](https://console.tencentcloud.com/live/event/streamevent).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/08e9a9bfca9111f08942525400e889b2.png)

#### View streaming data

Click on the**Streaming data** on the right side to view detailed information of the online live stream, such as traffic, bandwidth, frame rate, bitrate, etc.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4deff002ca9111f0a7775254005ef0f7.png)

## Disabled Streams Management

Log in to the CSS console, then navigate to [Stream Management](https://console.intl.cloud.tencent.com/live/streammanage) >**Disabled Streams**, and perform operations according to your actual business needs.

#### Enable live streaming

In the Disabled Streams list, select the corresponding disabled live stream and click **Enable** to resume the live stream publishing.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bbc3c374ca9111f09e745254007c27c5.png)

#### View streaming data

Click on the**streaming data** on the right side to view detailed information of the online live stream, such as traffic, bandwidth, frame rate, bitrate, etc.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f4beb1b8ca9111f0aedb525400454e06.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/31068](https://www.tencentcloud.com/document/product/267/31068)*
