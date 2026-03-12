# Configuring DRM Encryption

CSS offers DRM encryption capabilities based on Widevine, FairPlay, and NormalAES to help you protect your content and prevent piracy and hotlinking. This document shows you how to configure DRM encryption in the CSS console.

## Must-Knows

Tencent Cloud only encrypts your content. DRM licenses are offered by third party licensing services SDMC and DRMtoday, which charge a licensing fee. To learn more details, please contact the companies.

## Prerequisites

- You have activated CSS and added a [playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).
- You have created an account at [SDMC DRM](https://india-drm-console.sdmc.tv/setting/drm/index) or [DRMtoday](https://castlabs.com/free-trials/drmtoday/) and configured an access key.

## Console Settings

### Configuring DRM key information

1. Log in to the CSS console and select **Feature Configuration** > [DRM management](https://console.tencentcloud.com/live/config/drm) on the left sidebar.
2. Click  **Edit**  on the right to enter the DRM management configuration page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8ebde0af595111ef9bf1525400a9236a.png)

3. Fill in the  **secret key information**  and select your certificate management provider. You can choose SDMC or DRMtoday. The specific configuration is as follows:
  - If your licensing service provider is **SDMC**:

Enter your SDMC UID, Secret ID, and Secret key (you need to obtain the information from SDMC).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9c9eb1c4595111ef81cf525400d5f8ef.png)

  - If your licensing service provider is **DRMtoday**:

Enter your DRMtoday `Merchantname`, `MerchantUUID`, `MerchantAPIName`, `MerchantAPIPassword`, `KeySeedID`, and IVSeedID (you need to obtain the information from DRMtoday).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a4dfa8b6595111ef8f105254002693fd.png)

### Setting Transcoding Templates

1. Log in to the CSS console and enter the **Feature Configuration**  > [Live Transcoding](https://console.tencentcloud.com/live/config/transcode).
2. Click  **Create Transcoding Template** to enter the transcoding configuration page. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/cb3224e7595011ef9bf1525400a9236a.png) to enable the DRM encryption. Set the DRM encryption information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fc9dbbcd85f611ef852f52540075b605.png)

| Configuration Item | Required | Description |
| --- | --- | --- |
| DRM encryption | No | Whether to enable DRM encryption. It’s disabled by default. Before enabling this feature, you need to configure DRM key information in “DRM management”. |
| Type | Yes | Widevine, FairPlay, or NormalAES. For FairPlay encryption, you need to upload the certificate you obtain from Apple to your player. For details, see [Obtaining a FairPlay certificate](https://www.tencentcloud.com/document/product/267/48069). |

  2.1. You can switch between different tabs to view the DRM encryption configuration requirements for standard transcoding, top speed codec transcoding, and audio-only transcoding.

Standard Transcoding

Top Speed Codec Transcoding

Audio-only Transcoding

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2dff6b6e429611efb438525400f69702.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ed13acd1429511ef98fd52540075b605.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/34414a32429611ef98fd52540075b605.png)

3. After the configuration is completed, click  **Save** .

### Binding Domain Names

1. Log in to the CSS console and enter the **Feature Configuration**  > [Live Transcoding](https://console.tencentcloud.com/live/config/transcode).
2. Enter the domain name binding window in the following ways:
  - **Directly bind the domain name** : Click  **Bind Domain Name**  on the top left.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/41691270c51b11f0a62b5254007c27c5.png)

  - **After successfully creating a new transcoding template, bind the domain name** : [After successfully setting the transcoding template](https://www.tencentcloud.com/document/product/267/48068#creating-a-transcoding-template-and-binding-a-domain), click  **Bind Domain Name** in the prompt dialog box.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fadd9a9dc51a11f085c7525400454e06.png)

3. In the domain name binding window, select the **transcoding template**and **playback domain name**（Multiple playback  domain names can be bound simultaneously） you want to bind, and click  **Confirm** to finish.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1aac61c3c51b11f085c7525400454e06.png)

### Obtaining the DRM-encrypted playback URL

Only HLS playback supports DRM encryption. Use the [Address Generator](https://console.tencentcloud.com/live/addrgenerator/addrgenerator) to generate playback URLs (select the template you created). The HLS URL generated is DRM-encrypted.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/81d9762085f711ef80ff525400d5f8ef.png)

### Configuring Your Player

- It must have been equipped by [SDMC](https://india-drm-sso.sdmc.tv/applyAccount) with the ability to obtain and decrypt license information from video data.
- Use FairPlay encryption for iOS players and Widevine or NormalAES for Android players.
- On iOS, you need to apply for a certificate and upload it to the [SDMC console](https://india-drm-console.sdmc.tv/licenses/drm/index).

> **Note:**You need to create an account first before you can visit the SDMC console. For detailed directions on how to create an SDMC account, see [Obtaining the UID and Key Information](https://www.tencentcloud.com/document/product/267/48070). If you encounter any problems, please [submit a ticket](https://console.tencentcloud.com/workorder/category). We will help you navigate the process.


---
*Source: [https://www.tencentcloud.com/document/product/267/48068](https://www.tencentcloud.com/document/product/267/48068)*
