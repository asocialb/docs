# Troubleshooting Push Failure

If you follow the steps in [Best Practice - Live Push](https://intl.cloud.tencent.com/document/product/267/31558) but still find that the push is not successful, please troubleshoot common push issues as instructed in this document.

### 1. Check whether a CNAME record that points to a Tencent Cloud address has been configured for your domain name.

Your push can succeed only if your domain name has a CNAME record that points to a Tencent Cloud address. You can check whether an added push domain name has a CNAME record in the **CNAME** column of [**Domain Management**](https://console.tencentcloud.com/live/domainmanage). You will see a green check if the CNAME record is configured, as shown below:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f298895b911611efa50f52540075b605.png)

If your domain name does not have a CNAME record, you can [configure one](https://intl.cloud.tencent.com/zh/document/product/267/31057).

### 2. Check whether the network is normal.

RTMP push uses the **1935** port by default. If the port is not enabled on the firewall of the network for testing, you will be unable to connect to the server. You can check whether this issue caused the push failure by switching to another network (a 4G network for example).

### 3. Check whether the validity period of the push URL is too short.

To prevent the traffic from being stolen, some clients may set `txTime` (the validity period of the push URL) to a very short period, such as 5 minutes from the current time. This is unnecessary as the `txSercet` signature guarantees security. If the validity period is too short, the push URL may expire after a live stream is interrupted due to network disconnection, and consequently the push cannot be resumed.
You are advised to set `txTime` to 12 or 24 hours from the current time, longer than a common live streaming session.

### 4. Check whether `txSecret` is correct.

To ensure security, Tencent Cloud requires configuring hotlink protection for all push URLs and **rejects** all hotlink protection URLs that have expired or are miscalculated. If a push is rejected, the CSS SDK will throw a **PUSH_WARNING_SERVER_DISCONNECT** event.The performance of [Mobile Live Video Broadcasting DEMO](https://www.tencentcloud.com/document/product/1071/38147) at this time is as follows:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/161ce3b7e10f11eeb419525400ea3514.jpeg)

See

Best Practice > Live Push

for how to get reliable push URLs.

### 5. Using V2TXLivePusher to call startPush returns a -2 error?

Currently, error -2 will be reported in the following scenarios:

- Use LiteAVSDK_Smart version V2TXLivePusher to push the TRTC protocol which starts with` trtc://`, because the smart version does not support the TRTC protocol, and requires the professional and enterprise versions to support it.
- The push address lacks necessary parameters. When calling startPush to push a stream, please refer to the [Publishing/Playback URL](https://www.tencentcloud.com/document/product/1071/39359?lang=en&pg=) to splice the correct stream address.
- The player initialization mode is V2TXLiveMode_RTC, is a RTMP protocol address, which starts with` rtmp://`.


---
*Source: [https://www.tencentcloud.com/document/product/267/33383](https://www.tencentcloud.com/document/product/267/33383)*
