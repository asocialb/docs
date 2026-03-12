# Delayed Playback

Delayed playback is a feature that allows you to delay the playing of streams. It is mainly used in important live streaming events to allow organizers time to handle emergencies. You can enable this feature through parameter setting.

## Notes

- You can enable the delayed playback via three methods:
  - Directly configure via CSS console. For details, see [Delayed Playback Configuration](https://www.tencentcloud.com/document/product/267/55264).
  - Call the [playback delaying API](https://intl.cloud.tencent.com/document/product/267/30850).
  - Add a `txDelayTime` parameter to the end of a **push URL**. For details, please see [Push Configuration](https://www.tencentcloud.com/document/product/267/41660#push-configuration).
- Delayed playback is a billing value-added service. To activate the delayed playback feature, use the console settings, call the delayed live streaming interface or carry the delayed playback parameter configuration with the push domain name. After successful push, the [Value-added feature billing](https://www.tencentcloud.com/document/product/267/54973) will be generated.

> **Note:**The API method is not recommended because calling an API involves configuration caching, which makes it difficult to estimate when the feature takes effect. You are advised to enable the feature using the second method.

## Preparations

1. Activate [CSS](https://console.tencentcloud.com/live).
2. Log in to the CSS console, select [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click **Add Domain Name** to add a push domain name. For more information, please see [Adding Domain Name](https://intl.cloud.tencent.com/document/product/267/35970).

## Push Configuration

1. Log in to the CSS console, go to **Tools** > [Address Generator](https://console.tencentcloud.com/live/addrgenerator/addrgenerator), select **Push Domain** for **Domain Type**, and click **Generate Address**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d5e4db2485f311ef8829525400fdb830.png)

2. Add `txDelayTime` to the end of the push address, and push streams via OBS. For detailed directions, please see [Push via OBS](https://intl.cloud.tencent.com/document/product/267/31569).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/60f7384685f211efaee3525400bdab9d.png)

> **Note:**Set `txDelayTime` to the number of seconds for which you want to delay playback. The value must be an integer and cannot exceed 600.

## Delayed Playback

1. Log in to the CSS console, go to **Tools** > [Address Generator](https://console.tencentcloud.com/live/addrgenerator/addrgenerator), select **Playback Domain** for **Domain Type**, and click **Generate Address**.
2. Use [VLC](https://intl.cloud.tencent.com/document/product/267/32483), FFmpeg, or other tools for playback. For details, please see [CSS Playback](https://intl.cloud.tencent.com/document/product/267/31559).

In the figure above, the delay time set for playback via the `txDelayTime` parameter in the push address is 30s, and the actual playback latency is 34s, which indicates that the delayed playback feature has taken effect.


---
*Source: [https://www.tencentcloud.com/document/product/267/41660](https://www.tencentcloud.com/document/product/267/41660)*
