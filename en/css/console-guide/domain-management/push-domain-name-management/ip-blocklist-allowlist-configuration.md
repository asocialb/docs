# IP Blocklist/Allowlist Configuration

This document shows you how to configure an IP allowlist/blocklist to filter requests and control access to streaming content.

## How It Works

- IP **allowlist**: Only the configured IP addresses are allowed to push streams to Cloud Streaming Services.
- IP **blocklist**: Only the configured IP addresses are restricted from pushing streams to Cloud Streaming Services.

## Reminders

- An IP allowlist/blocklist takes effect about ten minutes after configuration.
- For an IP allowlist/blocklist configuration to apply to ongoing streams, you need to restart the streams.

## Prerequisites

- You have activated CSS and logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- You have added a [push domain](https://intl.cloud.tencent.com/document/product/267/35970).

## Configuring an IP Allowlist/Blocklist

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the name of the target playback domain or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/31ce70fc013211efbba352540095b445.png)

2. Within the **Advanced Configuration**> **IP allowlist/blocklist**, click on ![](https://staticintl.cloudcachetci.com/cms/backend-cms/75e67e17013211efbf03525400ae4d13.png)to enable the IP Allowlist/Blocklist.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/eedcf94cd3dd11f09f555254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/705b12f7d3e111f0a78a52540044a08e.png)

3. After enabling the **IP Allowlist/Blocklist** , enter the **IP Allowlist/Blocklist** configuration page and perform the following configuration:

Blocklist

Allowlist

![](https://staticintl.cloudcachetci.com/cms/backend-cms/86aae7cdd3e111f09975525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8f7a4006d3e111f09f555254007c27c5.png)

| Configuration Item | Description |
| --- | --- |
| Authenticate By | Allowlist or blocklist:You cannot select both.If you configure an allowlist, only IP addresses on the list will be able to access your streaming content.If you configure a blocklist, IP addresses on the list cannot access your streaming content. |
| IP List | The IP blocklist supports a maximum configuration of 200 rules, and the IP allowlist supports up to 500 rules. Please separate entries with a newline character.Allowlist/Blocklist supports IPv4, IPv6, and network segment formats. |

4. Click **Save** to save the configuration (it takes a while for the configuration to take effect).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a5af2f1cd3e111f0a73852540099c741.png)

## Modifying an IP Allowlist/Blocklist

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the name of the target playback domain or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7177425d013311efbf03525400ae4d13.png)

2. Select the **Access Control** tab. In the **IP allowlist/blocklist** area, click **Edit**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/00b9079cd3de11f0a73852540099c741.png)

3. Modify the configuration and click **Save**.

## Disabling IP Allowlist/Blocklist

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the name of the target playback domain or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8680ac48013311efb881525400a7e516.png)

2. Select the **Access Control** tab. In the **IP allowlist/blocklist** area, click ![img](https://staticintl.cloudcachetci.com/cms/backend-cms/0d0592e04eec11ee84f2525400494e51.png) to disable IP allowlist/blocklist.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/15c87680d3de11f09975525400bf7822.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/48812](https://www.tencentcloud.com/document/product/267/48812)*
