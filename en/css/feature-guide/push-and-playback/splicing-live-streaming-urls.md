# Splicing Live Streaming URLs

## Notes

- This article mainly explains the rules for assembling live streaming URLs. If you want to quickly generate push and playback addresses, you can go to the console to generate them. For more information, please refer to the documentation on [the Address Generator](https://www.tencentcloud.com/document/product/267/31084).
- After you create a [transcoding template](https://www.tencentcloud.com/document/product/267/31071#creating-a-transcoding-template) and [bind](https://www.tencentcloud.com/document/product/267/31071#unbinding-a-domain-name) it with a playback domain name, you need to add the transcoding template name after the `StreamName` of the live stream with the transcoding configuration in the format of `StreamName_transcoding template name`. For details, see [Playback Configuration](https://intl.cloud.tencent.com/document/product/267/31058).

## Prerequisites

- You have signed up for a Tencent Cloud account and activated the [CSS service](https://console.intl.cloud.tencent.com/live/livestat).
- You have applied for a domain name through [Tencent Cloud Domain Service](https://buy.intl.cloud.tencent.com/domain/buy).
- You have added push/playback domain names in [**Domain Management**](https://console.tencentcloud.com/live/domainmanage) of the **CSS console** and successfully configured the CNAME record. For detailed directions, please see [Adding Domain Names](https://intl.cloud.tencent.com/document/product/267/35970).

## Splicing Push URLs

If you run a large number of live streaming rooms, it is impossible to manually generate a push and playback URL for each host. In such cases, you can use the server to automatically **splice** the addresses. Any URL that meets Tencent Cloud standards can be used for push. A standard push URL consists of four parts, as shown below:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/55d4a3bdd77611eea2b0525400bb593a.png)

- **domain**

Push Domain: You can use the default push domain provided by Tencent Cloud Live Streaming, or you can use your own push domain that has been filed and successfully configured with CNAME.

- **AppName**

The name of the live streaming application, which is "live" by default and can be customized.

- **StreamName（Stream ID）**

Custom Stream Name: A unique identifier for each live stream, recommended to use random numbers or a combination of numbers and letters.

- **Authentication Key (optional)**

The URL includes two parts: txSecret and txTime, where `txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)`.

After enabling push authentication, you need to use a URL containing the authentication key for pushing. If push authentication is not enabled, there is no need for "?" and its subsequent content in the push address.

  - **txTime**（URL Expiration）

Indicates when the URL will expire, and the format supports hexadecimal UNIX timestamps (Time Unit: Seconds++)++.

> **Note:**For example, `5867D600` represents the expiration at 0:00:00 on January 1, 2017. Our customers usually set txTime to expire 24 hours after the current time. The expiration time should not be too short or too long. When the broadcaster encounters a network interruption during the live streaming process, they will resume pushing the stream. If the expiration time is too short, the broadcaster will not be able to resume pushing the stream due to the expiration of the push URL.

  - **txSecret (Anti-leakage Signature)**

Used to prevent attackers from forging your backend-generated push URL. The calculation method can be found in [the Best Practices - Anti-leakage Calculation](https://intl.cloud.tencent.com/document/product/267/31560).

## Splicing Playback URLs

A playback URL consists of a playback protocol prefix, domain name ( `domain`), application name ( `AppName`), stream name ( `StreamName`), playback protocol suffix, authentication key, and other custom parameters. Below are a few examples.

The examples of the addresses are as follows:

```
webrtc://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)http://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)rtmp://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)http://domain/AppName/StreamName.m3u8?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)
```

- Playback prefix

| Playback Protocol | Playback Prefix | Notes |
| --- | --- | --- |
| WebRTC | webrtc:// | We recommend WebRTC most as it has the best instant streaming performance and supports ultra-high concurrency. |
| HTTP-FLV | http:// or https:// | We recommend HTTP-FLV as it has good instant streaming performance and supports high concurrency. |
| RTMP | rtmp:// | We do not recommend RTMP as it has poor instant streaming performance and does not support high concurrency. |
| HLS (M3U8) | http:// or https:// | We recommend HLS for mobile clients and for the Safari browser on macOS. |

- **domain**

Push Domain: You can use the default push domain provided by Tencent Cloud Live Streaming, or you can use your own push domain that has been filed and successfully configured with CNAME.

- **AppName**

The name of the live streaming application, utilized for differentiating the storage path of live streaming media files, which is "live" by default and can be customized.

- **StreamName（Stream ID）**

Custom Stream Name: A unique identifier for each live stream. It is recommended to use random numbers or a combination of numbers and letters. It is not recommended to include "_". If the string after "_" is the same as the transcoding template name, the string will be recognized as the transcoding template name, and the string before "_" will be recognized as StreamName, which may cause playback anomalies. For example: `test_a1_hd1`, `test_a1` will be recognized as StreamName, and "hd1" will be recognized as the transcoding template name.

- **Transcoding Template Name**

By appending a "_" suffix to the StreamName, the program will pull the transcoding stream according to this transcoding template. If you only need to pull the source stream, appending the transcoding template name is unnecessary.

- **Authentication Key (optional)**

The URL includes two parts: txSecret and txTime, where

`txSecret=Md5(key+StreamName_Transcoding Template Name+hex(time))&txTime=hex(time)`.

After enabling push authentication, you need to use a URL containing the authentication key for pushing. If push authentication is not enabled, there is no need for "?" and its subsequent content in the push address.

  - **txTime（URL Expiration）**

Indicates when the URL will expire, and the format supports hexadecimal UNIX timestamps (Time Unit: Seconds).

  - **txSecret (Anti-leakage Signature)**

Used to prevent attackers from forging your backend-generated push URL. The calculation method can be found in [the Best Practices - Anti-leakage Calculation](https://intl.cloud.tencent.com/document/product/267/31560).

## Viewing Sample Push Codes

Go to [**Domain Management**](https://console.tencentcloud.com/live/domainmanage) of the CSS console, select a pre-configured push domain name, and click **Manage** > **Push Configuration** to display the **Push Address Sample Code** (for both PHP 、Java) that demonstrates how to generate a hotlink protection address. For detailed directions, please see [Push Configuration](https://intl.cloud.tencent.com/document/product/267/31059).


---
*Source: [https://www.tencentcloud.com/document/product/267/38393](https://www.tencentcloud.com/document/product/267/38393)*
