# SRT Push

TS over SRT directly transmits TS streams containing audio/video data using **SRT protocol**. The existing live streaming system is used for playback. TS over SRT is used as the standard push format for Haivision hardware and OBS.
In this mode, the SRT server parses TS streams, remuxes to RTMP streams, and forwards to the backend RTMP server.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5e9694da520f11ee974d5254005f490f.png)

> **Note:**Using SRT for push will not increase the cost.

## Upstream Lag Rate Comparison

Using SRT to push streams reduces lag, as shown in the following figure:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5e8b61b8520f11ee84f2525400494e51.png)

## Packet Loss Rate Comparison

Using SRT to push streams optimizes upstream performance, resulting in better playback smoothness. The following shows the performance comparison of the Douyu app.

- Android: performance test data of push over SRT (test device — Mi 9):

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5e9dbb67520f11ee974d5254005f490f.png)

- iOS: performance test data of push over SRT (test device — iPhone XR):

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5ec0f774520f11ee84f2525400494e51.png)

## Packet Loss Prevention Comparison

Compared with QUIC, SRT reduces packet loss at the application layer under the same packet loss rate, thanks to its faster, more precise retransmission control and pacing mechanism for live streaming scenarios. When the packet loss rate is 50%, SRT can still guarantee stable transmission.

With the same linkage and the same live stream file on the push end, the packet loss rate reduces by 5% every five minutes when SRT is used. The following figure shows that the push frame rate of SRT is more stable.

## Live Push

### Access Method

Live push supports using **port 9000** to push streams over SRT. You can [generate a push address](https://intl.cloud.tencent.com/document/product/267/31084) via the [Address Generator](https://console.tencentcloud.com/live/addrgenerator/addrgenerator) in the CSS console and splice the address by following the rules below.

Tencent Cloud SRT push address:

```
srt://${rtmp-push-domain}:9000?streamid=#!::h=${rtmp-push-domain},r=${app}/${stream},txSecret=${txSecret},txTime=${txTime}
```

> **Note:**`$ {app}` is a variable and should be replaced with the actual value. Note that `$`, `{`, and `}` are not required.

### Implementation Method

The SRT server will remux TS streams to RTMP streams and relay them to the  `${rtmp-push-domain} domain name` .

Example of OBS streaming content via the SRT protocol:

Enter the following in Server:  `srt://${rtmp-push-domain}:9000?streamid=#!::h=${rtmp-push-domain},r=${app}/${stream},txSecret=${txSecret},txTime=${txTime}`

Enter the following in Stream Key:  `r=${app}/${stream},txSecret=${txSecret},txTime=${txTime}`

![](https://staticintl.cloudcachetci.com/cms/backend-cms/612ebd9c638e11ef8357525400bdab9d.png)

> **Note:**If you want to push streams over SRT, the OBS version cannot be lower than v25.0.

## Live Pull

Follow the general pull and playback process. For details, see [CSS Playback](https://intl.cloud.tencent.com/document/product/267/31559).


---
*Source: [https://www.tencentcloud.com/document/product/267/40102](https://www.tencentcloud.com/document/product/267/40102)*
