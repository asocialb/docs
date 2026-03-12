# IP Blocklist/Allowlist Configuration

This document shows you how to configure an IP allowlist/blocklist to filter requests and control access to streaming content.

## How It Works

- IP **allowlist**: Only IP addresses on the list can access your streaming content.
- IP **blocklist**: IP addresses on the list cannot access your streaming content.

## Must-Knows

An IP allowlist/blocklist takes effect about ten minutes after configuration.

## Prerequisites

- You have activated CSS and logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- When both IP Blocklist/Allowlist and [Playback Region Management](https://www.tencentcloud.com/document/product/267/56788) (Regional Block/Allowlist) are enabled at the same time, the system's judgment logic is as follows:
  1.1. **First, check the IP Blocklist/Allowlist**:
  - If the IP is in the allowlist, it is directly allowed.
  - If the IP is in the blocklist, access is directly denied.
  - If the IP is not in the blocklist/allowlist, go to the next step.
  1.2. **Then, check the Regional Block/Allowlist**(only when the IP is not in the IP Block/Allowlist):
  - If the region is in the allowlist, then allow access; otherwise, deny access.
  - If the region is in the blocklist, then deny access; otherwise, allow access.

## Configuring an IP Allowlist/Blocklist

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar, and click the target **playback domain** or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ede7fcc7013311efb881525400a7e516.png)

2. Within the **Access Control**> **IP allowlist/blocklist**, click on ![](https://staticintl.cloudcachetci.com/cms/backend-cms/264adb0e013411efbba352540095b445.png)to enable the IP Allowlist/Blocklist.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/52650437cc0811f091ab5254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6742d4d5cc0811f091ab5254007c27c5.png)

3. After enabling the **IP Allowlist/Blocklist** , enter the **IP Allowlist/Blocklist** configuration page and perform the following configuration:

Blocklist

Allowlist

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bf3fa5e5d3e111f08f8f525400454e06.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cb104ab4d3e111f08206525400e889b2.png)

| Configuration Item | Description |
| --- | --- |
| Authenticate By | Allowlist or blocklist:You cannot select both.If you configure an allowlist, only IP addresses on the list will be able to access your streaming content.If you configure a blocklist, IP addresses on the list cannot access your streaming content. |
| IP List | The IP blocklist supports a maximum configuration of 200 rules, and the IP allowlist supports up to 500 rules. Please separate entries with a newline character.Allowlist/Blocklist supports IPv4, IPv6, and network segment formats. |

4. Click **Save** to save the configuration (it takes a while for the configuration to take effect).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dfe67ca5d3e111f09f555254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4f71c64a013411efbf03525400ae4d13.png)

## Modifying an IP Allowlist/Blocklist

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar, and click the target **playback domain** or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/56cd152e013411ef9125525400275b90.png)

2. Click **Access Control** and, in the **IP Allowlist/Blocklist** area, click **Edit**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5d389a19013411efbba352540095b445.png)

3. Modify the configuration and click **Save**.

## Disabling IP Allowlist/Blocklist

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar, and click the target **playback domain** or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/671ed55c013411efbba352540095b445.png)

2. Select the **Access Control** tab. In the **IP allowlist/blocklist** area, click ![img](https://staticintl.cloudcachetci.com/cms/backend-cms/94e49a114ee911ee84f2525400494e51.png) to disable IP allowlist/blocklist.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6c54345e013411efbf03525400ae4d13.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/46767](https://www.tencentcloud.com/document/product/267/46767)*
