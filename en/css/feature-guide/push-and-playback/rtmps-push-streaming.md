# RTMPS Push Streaming

Tencent Video Cloud continuously improves its streaming media transmission to cater to various requirements. Apart from the common RTMP streaming protocol, it also now supports the RTMPS streaming protocol, which specifically caters to users with encryption needs, particularly those with overseas operations. This article primarily focuses on the implementation of RTMPS streaming.

## Comparison of Advantages

Standard RTMP streaming protocol relies entirely on adding relevant parameters to the URL for authentication, with the RTMP server carrying out verification based on these parameters. However, this does not encrypt transmitted audio and video data packets, hence, captured and decoded RTMP packets can be played.

The RTMPS protocol effectively resolves these RTMP security issues. It is the SSL-encrypted version of the RTMP protocol, which enhances the security of data communication, allowing safe stream transmission between the encrypted encoder and CDN.

**Comparison chart of various streaming protocols:**

| Protocol | Protocol Type | Transmission Method | Delay | Protocol Characteristic | Application Scenario | Tencent's Optimization Scheme |
| --- | --- | --- | --- | --- | --- | --- |
| RTMPS | Streaming Protocol | TCP | - | Encryption | Encryption scenarios | Supporting multiple domains and certificates |
| SRT | Streaming Protocol | UDP | 500 ms-1s | Low latency, packet loss resistance | OTT, cross-regional transmission | - |
| WebRTC | Streaming Protocol | RTP | 200 ms-1s | Low latency | Audio and video calls | Optimizing instant loading and stuttering in Live Event Broadcasting |
| QUIC | Streaming Protocol | UDP | - | Packet loss resistance, 0rtt | Browser access | Optimizing the first frame transmission |

## Notes

The RTMPS streaming protocol, which employs SSL encryption, demands the configuration of a push domain name certificate; at present, the default push domain name 'push.tlivecloud.com' of Cloud Streaming Services has been equipped with a common certificate. For other domain names, you need to [Submit a Ticket](https://console.tencentcloud.com/workorder/category) to provide the domain name and corresponding certificate for configuration.

> **Note:**If you wish to test the RTMPS streaming, you can connect the default push domain name by Cloud Streaming Services.If you need to use the RTMPS streaming through your own domain, you need to [Submit a Ticket](https://console.tencentcloud.com/workorder/category) providing the domain name and corresponding certificate.

## RTMPS Streaming

1. The generation of live streaming URLs can be carried out in the following two methods:
  - Assemble independently through splicing rules. For detailed operations, please refer to [Splicing Live Streaming URLs](https://www.tencentcloud.com/document/product/267/38393).
  1.1. Go to  **Tools >** [Address Generator](https://console.tencentcloud.com/live/addrgenerator/addrgenerator) in the CSS console, select the URL type as Push Address, and select a domain name as needed. For detailed operations, refer to the Address Generator documentation > [Address Generator](https://www.tencentcloud.com/document/product/267/31084).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e57752629ee011eebd87525400c40977.png)

2. Modify the generated RTMP live streaming URL into RTMPS, input it into OBS to start RTMPS streaming. For detailed operations, please refer to [Push via OBS](https://www.tencentcloud.com/document/product/267/31569).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e56cda079ee011eea869525400c26cb9.png)

## Live Playback

Operate according to the normal live playback process. For more details, please refer to [Live Playback](https://www.tencentcloud.com/document/product/267/31559).


---
*Source: [https://www.tencentcloud.com/document/product/267/58607](https://www.tencentcloud.com/document/product/267/58607)*
