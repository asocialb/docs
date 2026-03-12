# Adaptive Bitrate

With the adaptive bitrate feature, the playback bitrate of a live stream can change smoothly based on network conditions. This ensures a smooth playback experience under changing network conditions.

## Notes

- After creating a template, you can bind it with a playback domain name. The binding takes effect in 5-10 minutes.
- A playback domain can be bound with **multiple adaptive bitrate templates**, and an adaptive bitrate template can be bound to **multiple playback domains**.
- Each adaptive bitrate template can have up to 15 streams.
- For the adaptive bitrate feature to work, the player needs to support adaptive bitrate.
- The GOP for the streams of an adaptive bitrate template must be identical.
- The codec for the streams of an adaptive bitrate template must be the same.
- Adaptive bitrate playback addresses only support HLS and WebRTC playback protocols. For the address concatenation rules, please refer to the [Address Generator](https://www.tencentcloud.com/document/product/267/31084?lang=en&pg=).
- The transcoding configuration template for adaptive bitrate streaming supports the configuration of a face blurring feature, which can achieve the blurring of faces and specific objects. To utilize this feature, you need to [submit a ticket](https://console.tencentcloud.com/workorder/category) to request support. In the adaptive bitrate template, even if multiple sub-stream templates have the face blurring feature enabled, the fee will be charged only once. Enabling this service will incur [live transcoding](https://www.tencentcloud.com/document/product/267/39604) fees and Media Processing Service (MPS) [intelligent recognition](https://www.tencentcloud.com/document/product/1041/49204) fees.

## Creating an Adaptive Bitrate Template

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and select **Feature Configuration > Adaptive Bitrate** on the left sidebar.
2. Click **Create template** and complete the following settings:
  - Basic information: The template name and description. For details, see [Basic Information](#259b6eab-5b7d-44ca-95c5-9483cddea573).
  - Stream information: See [Stream Information](#e5c271c5-129d-4271-a204-903606dccbe7).
3. Click **Add stream** to add a new stream to the template. You can add up to 15 streams for a template.
4. Click **Save**.

### Basic Information

| Basic Information | Required | Description |
| --- | --- | --- |
| Template name | Yes | Please enter 1 to 10 characters.The adaptive bitrate template name. It only supports letters and alphanumeric combinations and does not support pure digits.The template name must not duplicate existing transcoding template names, adaptive bitrate template names, or sub-stream names. |
| Template description | No | The adaptive bitrate template description. It can only contain Chinese characters, letters, digits, spaces, underscores (_), and hyphens (-). |
| Live subtitles | No | The subtitle feature is deactivated by default, but can be manually activated.To activate this feature, it is necessary to bind a subtitle template. Choose a subtitle template to bind based on your business requirements.Preview and observe the effects of the subtitle template.You can adjust the subtitle template according to business needs at any time. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/721b5ac1c46411f08c0e52540044a08e.png)

### Stream Information

| Stream Information | Required | Description |
| --- | --- | --- |
| Transcoding type | Yes | The optional transcoding types, include standard transcoding and TSC transcoding. |
| Stream name | Yes | Please enter 1 to 10 characters.Substream Template Name supports 1-10 characters, only allowing letters and alphanumeric combinations, and does not support pure digits.The substream name cannot be duplicated with existing transcoding template names, adaptive bitrate template names, and substream names. |
| Video quality | No | You can choose **Smooth**, **SD**, **HD** or **FHD**. After you select a value, the system will automatically enter the recommended video bitrate and height, which can be modified. |
| Video bitrate (Kbps) | Yes | The output video bitrate. Value range: 101-8000.If you enter a value not larger than 1,000, it must be a multiple of 100.If you enter a value larger than 1,000, it must be a multiple of 500. |
| Video resolution (px) | Yes | By default, you set the**height** of the output video.You can also **set the short side length**.The value must be in the range of 2-3000 and must be multiple of two. The other side will be scaled proportionally. |
| DRM encryption | Yes | Disabled by default and can be enabled manually.To enable DRM encryption,  you need to first obtain the key information in [DRM Management](https://console.intl.cloud.tencent.com/live/config/drm).DRM schemes including Widevine, FairPlay, and NormalAES are supported for HLS playback. For FairPlay encryption, you need to upload the certificate you obtain from Apple to your player.Encryption Types: Default **Widevine**, Optional Fairplay and NormalAES. |
| Video Encoding | No | The original codec is selected by default. You can change it to H.264, H.265, H.266, or AV1.The codec for all the streams in the same adaptive bitrate template must be the same. |
| Face Blurring | No | If necessary, you can [submit a ticket](https://console.tencentcloud.com/workorder/category) to enable this feature and activate [Media Processing Service (MPS)](https://www.tencentcloud.com/document/product/1041/33482).The feature is disabled by default and can be manually enabled.The feature can be used to blur faces and specific objects, with the following effect:![](https://staticintl.cloudcachetci.com/cms/backend-cms/35a98b68b11e11efbfb3525400bdab9d.png)Enabling the service will incur [live transcoding](https://www.tencentcloud.com/document/product/267/39604) fees and MPS [intelligent recognition](https://www.tencentcloud.com/document/product/1041/49204) fees. |
| Video frame rate (fps) | No | You can choose to keep the original frame rate or set a video frame rate. By default, the original frame rate is maintained.The video frame rate setting value range: 1 fps - 60 fps. |
| GOP(seconds) | No | The GOP is not specified by default. Value range: 1-6.The higher the GOP, the higher the latency. A smaller GOP may potentially lead to stuttering. The GOP for all the streams in the same adaptive bitrate template must be the same. |
| Parameter limit | No | Parameter limits are disabled by default.After a limit is enabled, if you enter a value higher than the original, the original will be used. This can avoid video quality issues caused by using high video quality settings to transcode videos of low quality. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dae4b6fe24a911f09e67525400bf7822.png)

## Binding a Domain Name

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Select **Feature Configuration > Adaptive Bitrate** on the left sidebar.
2. Bind a domain name in either of two ways:
  - **Bind a domain to an existing template**: Click **Bind Domain Name** in the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/81c7b596c46511f0a6dd5254005ef0f7.png)

  - **Bind a domain after creating a template**: After [creating an adaptive bitrate template](https://www.tencentcloud.com/document/product/267/50271#creating-an-adaptive-bitrate-template), click **Bind Domain Name** in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fd009ed0c46411f0b4a7525400454e06.png)

3. Select an **adaptive bitrate template** and a **playback domain** **name**（Multiple playback  domain names can be bound simultaneously） and then click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1698f442c46511f0b4a7525400454e06.png)

## Unbinding a Domain Name

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Select **Feature Configuration > Adaptive Bitrate** on the left sidebar.
2. Select the target template and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bc1d0de124aa11f0b0b1525400e889b2.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ed46f369b8f311eeb395525400461a83.png)

## Modifying a Template

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Select **Feature Configuration > Adaptive Bitrate** on the left sidebar.
2. Select the target template and click **Edit** on the right to modify it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dbc1e8c424aa11f0b44b5254007c27c5.png)

3. After modification, click **Save**.

## Deleting a Template

> **Note:** If a template has been bound to domains, you need to [unbind](#unbinding-a-domain-name) them before you can delete the template.You cannot delete a transcoding template that has the Live subtitles feature enabled.Once the template is deleted, it cannot be recovered. Please proceed with caution.

1. Log in to the[CSS console](https://console.tencentcloud.com/live/livestat). Select **Feature Configuration > Adaptive Bitrate** on the left sidebar.
2. Select the target template (make sure it’s not bound to a domain), and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb8e48f424aa11f0a62e525400454e06.png)

3. In the pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1741fa1624ab11f0b44b5254007c27c5.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/50271](https://www.tencentcloud.com/document/product/267/50271)*
