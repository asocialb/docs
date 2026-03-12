# Latency Control

Set a latency that fits your needs. Note that setting the latency too low may cause playback to stutter.

## Note

Latency configuration will take effect approximately 10 minutes after configuration.

## Prerequisites

- You have activated CSS and logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- You have added a [playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Latency control

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar and click the **playback domain** for which you want to configure RTMP and FLV latency, or click **Manage** on the right to enter the details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7e68436f142611ef83585254007bbd8c.png)

2. In  **Advanced Configuration**  >  **Playback latency configuration** , you can configure the latency for RTMP and FLV.
3. When live streaming latency parameters are configured, it is recommended to select appropriate latency parameters based on your actual business needs. It is advisable to set the GOP for publishing to 1-2s because the larger the GOP value, the greater the live streaming latency. Note that setting the latency too low may cause playback to stutter.
4. When GOP is set to two seconds, the latency is as follows:

| Setting | High | Medium | Low |
| --- | --- | --- | --- |
| Estimated Latency | 7-9s | 5-7s | 4-5s |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f74f1c14cc0911f091ab5254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/15ef8e02cc0a11f093295254001c06ec.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/48377](https://www.tencentcloud.com/document/product/267/48377)*
