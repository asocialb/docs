# Blocking Playback by Protocol

You can block playback for a domain by blocking specific protocols. Playback requests that use the blocked protocols will be rejected.

## Prerequisites

- You have activated CSS and logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- You have added a [playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Blocking Protocols

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the name of the target playback domain or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/847684513f2d11efa56d525400d5f8ef.png)

2. Select the **Access Control** tab. In the **Block playback by protocol** area, you can block playback that uses the RTMP, FLV, HLS, DASH, and WebRTC protocols.
3. Click **Edit** and toggle on the protocols you want to block.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/14797758cc0911f08e74525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2c084906cc0911f08658525400454e06.png)

4. Click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/426b340fcc0911f0ae4f52540099c741.png)

> **Note:**It takes a while for the blocking configuration to take effect. After configuring blocked protocols, please wait for the configuration to take effect before you block other protocols.Except for HLS, protocol blocking only takes effect for new live streams. It does not affect ongoing streams.

## Unblocking Protocols

To unblock a blocked protocol, follow the steps below:

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the name of the target playback domain or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/07550d3d3f2e11efa56d525400d5f8ef.png)

2. Select the **Access Control** tab. In the **Block playback by protocol** area, toggle off the protocol you want to unblock.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/502f09dfcc0911f096d1525400e889b2.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9ff3409fcc0c11f08e74525400bf7822.png)

3. Click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b1580272cc0c11f091ab5254007c27c5.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/48703](https://www.tencentcloud.com/document/product/267/48703)*
