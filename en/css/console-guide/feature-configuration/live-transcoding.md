# Live Transcoding

Live transcoding (including video transcoding and audio transcoding) refers to the process where the original stream pushed from the live streaming site is converted into streams of different codecs, resolutions, and bitrates in the cloud before being pushed to viewers. This meets playback needs in varying network environments on different devices. This document describes how to create, bind, unbind, modify, and delete a transcoding template via the CSS console.

**You can create a transcoding template in two ways:**

- Create a transcoding template in the CSS console. For detailed directions, see [Creating a standard transcoding template](#creating-a-standard-transcoding-template), [Creating a TSC transcoding template](#C_topspeed), and [Creating an audio-only transcoding template](#C_audio).
- Create a transcoding template for live streams using an API. For the API parameters and examples, see [CreateLiveTranscodeTemplate](https://www.tencentcloud.com/document/product/267/30790).

## Must-Knows

- CSS supports standard transcoding, Top Speed Codec (TSC) transcoding, and audio-only transcoding. Please read the billing documents before using the services.
  - Standard transcoding: [Standard Transcoding Packages](https://www.tencentcloud.com/document/product/267/52220#standard_pag), [Standard Transcoding (pay-as-you-go)](https://intl.cloud.tencent.com/document/product/267/39604)
  - TSC transcoding: [TSC Transcoding Packages](https://www.tencentcloud.com/document/product/267/52220#.E6.9E.81.E9.80.9F.E9.AB.98.E6.B8.85.E8.BD.AC.E7.A0.81.E5.8C.85), [TSC Transcoding (pay-as-you-go)](https://intl.cloud.tencent.com/document/product/267/39604)
- Compared with **standard transcoding**, **TSC transcoding** provides higher video quality at lower bitrate. Leveraging technologies including intelligent scene recognition, dynamic encoding, and CTU/line/frame-level bitrate control, TSC transcoding allows you to provide higher-definition streaming services at lower bitrates (50% lower on average). It is widely used for game streaming, showroom streaming, and event streaming.
- After creating a template, you can bind it with a playback domain name. The binding takes effect in 5-10 minutes.
- After binding a template, you can add the template name ( `_template name`) after `StreamName` in the original URL to generate a URL for the transcoding output. Note that the **template name** and **stream name** cannot have the same suffix. For example, if the template name is `hd`, and `StreamName` is `test_a1_hd`, the system will use `test_a1` as the stream name and `hd` as the transcoding template, and playback will fail.
- If you have specified the height and width or short and long sides of the transcoding output, to prevent image distortion, keep the resolution of published streams as close to the values set as possible.
- On the **Live Transcoding** page of the console, you can view the domain a template is bound to, as well as finer-granularity bindings performed via APIs. You can also [unbind](#unbinding-a-domain-name) a template here.
- You can bind one playback domain name with **multiple transcoding templates**, or bind one transcoding template with **multiple playback domain names**.
- You can create up to **50** transcoding templates.
- The transcoding configuration template for live streaming supports the configuration of a  **face blurring**  feature, which can achieve the blurring of faces and specific objects. To utilize this feature, you need to [submit a ticket](https://console.tencentcloud.com/workorder/category) to request support. Enabling this service will incur [live transcoding](https://www.tencentcloud.com/document/product/267/39604) fees and Media Processing Service (MPS) [intelligent recognition](https://www.tencentcloud.com/document/product/1041/49204) fees.

## Creating a Transcoding Template

### Creating a standard transcoding template

1. Log in to the CSS console and select **Feature Configuration** > [**Live Transcoding**](https://console.tencentcloud.com/live/config/transcode).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ff4e06ecc46111f0aa02525400e889b2.png)

2. Click **Create Template**, select **Standard Transcoding** for transcoding type, and complete the following configuration:
  - Basic configuration: Template name, video bitrate, video resolution and more. For details, see [Basic Configuration for Standard Transcoding](https://www.tencentcloud.com/document/product/267/31071#e0336bf4-96b8-4b92-975d-7fbcf342bf67).
  - Advanced configuration (optional): Click **Advanced Configuration** to show advanced settings. For details, see [Advanced Configuration for Standard Transcoding](https://www.tencentcloud.com/document/product/267/31071#910fd1af-3f0b-473b-b737-4376216e2b8f).
3. Click **Save**.

#### Basic Configuration for Standard Transcoding

| Basic Configuration for Standard Transcoding | Required | Description |
| --- | --- | --- |
| Transcoding type | Yes | The optional transcoding types, include standard transcoding, TSC transcoding, or audio-only transcoding. |
| Template name | Yes | Please enter 1 to 10 characters.The live transcoding template name. It only supports letters and alphanumeric combinations and does not support pure digits.The template name must not duplicate existing transcoding template names, adaptive bitrate template names, or sub-stream names. |
| Template description | No | The live transcoding template description. It can only contain Chinese characters, letters, digits, spaces, underscores (_), and hyphens (-). |
| Video quality | No | You can choose Smooth, SD, HD or FHD. After you select a value, the system will automatically enter the recommended video bitrate and height, which can be modified. |
| Video bitrate(in Kbps) | Yes | You can choose to keep the original bitrate, set the video bitrate, or use the default transcoding bitrate.Set the transcoding code rate, value range: 101Kbps - 8000Kbps.If you enter a value not larger than 1,000, it must be a multiple of 100.If you enter a value larger than 1,000, it must be a multiple of 500. |
| Video resolution (px) | Yes | Choose to keep the original resolution, set by width and height, or set by length.The default is set by long and short sides.The input value is the short side value, which can be switched to width and height settings, and the input value is the height value.Value range: 0-3000. The value must be a multiple of 2. The other side will be auto-scaled. |
| DRM encryption | No | It is disabled by default and can be enabled manually.To enable DRM encryption, you need to first obtain the key information in  DRM Management.DRM encryption of Widevine, FairPlay, and NormalAES are supported for HLS. For FairPlay encryption, you need to upload the certificate you obtain from Apple to your player.Encryption types: default Widevine, optional Fairplay, and NormalAES. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b65a741a241811f091625254001c06ec.png)

#### Advanced Configuration for Standard Transcoding

| Advanced Configuration for Standard Transcoding | Required | Description |
| --- | --- | --- |
| Video Encoding | No | The original codec is used by default. You can choose H.264, H.265, H.266, or AV1. |
| Face blurring | No | If necessary, you can [submit a ticket](https://console.tencentcloud.com/workorder/category) to enable this feature and activate [Media Processing Service (MPS)](https://www.tencentcloud.com/document/product/1041/33482).The feature is disabled by default and can be manually enabled.The feature can be used to blur faces and specific objects, with the following effect:![](https://staticintl.cloudcachetci.com/cms/backend-cms/35a98b68b11e11efbfb3525400bdab9d.png)Enabling this service will incur [live transcoding](https://www.tencentcloud.com/document/product/267/39604) fees and MPS [intelligent recognition](https://www.tencentcloud.com/document/product/1041/49204) fees. |
| Video frame rate (fps) | No | You can choose to keep the original frame rate, set the video frame rate, and keep the original frame rate by default.**Set the video frame rate range**: 1fps - 60fps. |
| GOP(seconds) | No | The GOP setting range is between 1 to 6 seconds.The larger the GOP, the higher the latency; a smaller GOP may potentially lead to stuttering.If not configured, the system default value will be adopted. |
| Live subtitles | No | The subtitle feature is deactivated by default, but can be manually activated.To activate this feature, it is necessary to bind a subtitle template. Choose a subtitle template to bind based on your business requirements.Preview and observe the effects of the subtitle template.You can adjust the subtitle template according to business needs at any time. |
| Parameter limit | No | Parameter limits are disabled by default. After a limit is enabled, if you enter a value higher than the original, the original will be used. This can avoid video quality issues caused by using high video quality settings to transcode videos of low quality. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1a59058f241911f0948f52540099c741.png)

### Creating a TSC transcoding template

2. Click **Create Template**, select **Top Speed Codec Transcoding** for transcoding type, and complete the following configuration:
  - Basic configuration: Template name, video bitrate, video resolution, etc. For details, see [Basic Configuration for TSC Transcoding](https://www.tencentcloud.com/document/product/267/31071#490e722e-d572-467a-93a8-35615f810bed).
  - Advanced configuration (optional): Click **Advanced Configuration** to show advanced settings. For details, see [Advanced Configuration for Top Speed Codec Transcoding](https://www.tencentcloud.com/document/product/267/31071#fa43b38d-4392-46c0-8297-47f7441fe167).
3. Click **Save**.

#### Basic Configuration for TSC Transcoding

| Basic Configuration for TSC Transcoding | Required | Description |
| --- | --- | --- |
| Transcoding Type | Yes | The optional transcoding types, include standard transcoding, TSC transcoding, or audio-only transcoding. |
| Template name | Yes | Please enter 2 to 10 characters.The live transcoding template name. It only supports letters and alphanumeric combinations and does not support pure digits.The template name must not duplicate existing transcoding template names, adaptive bitrate template names, or sub-stream names. |
| Template description | No | The live transcoding template description. It can only contain Chinese characters, letters, digits, spaces, underscores (_), and hyphens (-). |
| Video quality | No | You can choose Smooth, SD, HD or FHD. After you select a value, the system will automatically enter the recommended video bitrate and height, which can be modified. |
| Video bitrate(in Kbps) | Yes | You can choose to keep the original bitrate, set the video bitrate, or use the default transcoding bitrate.Set the transcoding code rate, value range: 101Kbps - 8000Kbps.If you enter a value not larger than 1,000, it must be a multiple of 100.If you enter a value larger than 1,000, it must be a multiple of 500. |
| Video resolution (px) | Yes | Choose to keep the original resolution, set by width and height, or set by length.The default is set by long and short sides.The input value is the short side value, which can be switched to width and height settings, and the input value is the height value.Value range: 0-3000. The value must be a multiple of 2. The other side will be auto-scaled. |
| DRM encryption | No | It is disabled by default and can be enabled manually.To enable DRM encryption, you need to first obtain the key information in  DRM Management.DRM encryption of Widevine, FairPlay, and NormalAES are supported for HLS. For FairPlay encryption, you need to upload the certificate you obtain from Apple to your player.Encryption types: default Widevine, optional Fairplay, and NormalAES. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/614a0e1c241a11f0b0b1525400e889b2.png)

#### Advanced Configuration for TSC Transcoding

| Advanced Configuration for TSC Transcoding | Required | Description |
| --- | --- | --- |
| Video Encoding | No | The original codec is used by default. You can choose H.264, H.265, H.266, or AV1. |
| Video frame rate (fps) | No | You can choose to keep the original frame rate, set the video frame rate, and keep the original frame rate by default.**Set the video frame rate range**: 1fps - 60fps. |
| GOP(seconds) | No | Value range: 1-6. The larger the GOP, the higher the delay. If this parameter is left empty, the default value will be used.The GOP setting range is between 1 to 6 seconds.The larger the GOP, the higher the latency; a smaller GOP may potentially lead to stuttering.If not configured, the system default value will be adopted. |
| Live subtitles | No | The subtitle feature is deactivated by default, but can be manually activated.To activate this feature, it is necessary to bind a subtitle template. Choose a subtitle template to bind based on your business requirements.Preview and observe the effects of the subtitle template.You can adjust the subtitle template according to business needs at any time. |
| Parameter limit | No | It is disabled by default and can be enabled manually.After a limit is enabled, the original value of the input stream will be used if you enter a value larger than the original. This can avoid video quality issues caused by using high video quality settings to transcode videos of low quality. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e7e22fed241911f091625254001c06ec.png)

### Creating an Audio-only transcoding template

2. Click **Create Template**, select **Audio-only Transcoding** for transcoding type, complete the configuration, and then click **Save**.

| Basic Configuration for Audio-only Transcoding | Required | Description |
| --- | --- | --- |
| Transcoding type | Yes | The optional transcoding types, include standard transcoding, TSC transcoding, or audio-only transcoding. |
| Template name | Yes | Please enter 1 to 10 characters.The live transcoding template name. It only supports letters and alphanumeric combinations and does not support pure digits.The template name must not duplicate existing transcoding template names, adaptive bitrate template names, or sub-stream names. |
| Template description | No | The live transcoding template description. It can only contain Chinese characters, letters, digits, spaces, underscores (_), and hyphens (-). |
| Audio bitrate (Kbps) | Yes | You can choose to keep the original bitrate or set the audio bitrate, with the default being to keep the original bitrate.To set the audio bitrate, the value range is 101kbps - 500kbps. |
| Live subtitles | No | The subtitle feature is deactivated by default, but can be manually activated.To activate this feature, it is necessary to bind a subtitle template. Choose a subtitle template to bind based on your business requirements.Preview and observe the effects of the subtitle template.You can adjust the subtitle template according to business needs at any time. |
| DRM encryption | No | It is disabled by default and can be enabled manually.To enable DRM encryption, you need to first obtain the key information in [DRM Management](https://console.intl.cloud.tencent.com/live/config/drm).DRM encryption of Widevine, FairPlay, and NormalAES are supported for HLS. For FairPlay encryption, you need to upload the certificate you obtain from Apple to your player.Encryption types: default **Widevine**, optional Fairplay, and NormalAES. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2cf9eac3241a11f0b44b5254007c27c5.png)

## Binding a Domain Name

2. Bind a domain name in either of two ways:
  - **Bind a domain to an existing template**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9f4ae583c46311f0b35752540099c741.png)

  - **Bind a domain name after creating a transcoding template**: After [creating a template](#creating-a-transcoding-template), click **Bind Domain Name** in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/85e026ddc46211f0b4a7525400454e06.png)

3. Select a **transcoding template** and a **playback domain name**（Multiple playback  domain names can be bound simultaneously）  in the domain binding window and then click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a1312a83c46211f0a0935254007c27c5.png)

## Unbinding a Domain Name

2. Select the target template and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/358638ea241c11f09e67525400bf7822.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fe9a8d83b8d011eea201525400170219.png)

## Modifying a Template

2. Select the target transcoding template and click **Edit** on the right to modify it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/57436eee241c11f0b47352540044a08e.png)

3. After modification, click **Save**.

## Deleting a Template

> **Note:**If a template has been bound to domains, you need to [unbind](#unbinding-a-domain-name) them before you can delete the template.You cannot delete a transcoding template that has the Live subtitles feature enabled.

1. Log in to the CSS console and select **Feature Configuration** > [Live Transcoding](https://console.tencentcloud.com/live/config/transcode).
2. Select the target template (make sure it’s not bound to a domain), and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8775ddc9241c11f0948f52540099c741.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a8147c31241c11f09e67525400bf7822.png)

## More

You can also **unbind** and **bind** domains and transcoding templates on the **Domain Management** page. For details, see [Template Configuration](https://intl.cloud.tencent.com/document/product/267/31062).


---
*Source: [https://www.tencentcloud.com/document/product/267/31071](https://www.tencentcloud.com/document/product/267/31071)*
