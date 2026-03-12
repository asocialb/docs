# Getting Started

This document describes how to get started with CSS. Before trying out CSS, you're advised to read the [Pricing Overview](https://intl.cloud.tencent.com/document/product/267/2819) of CSS to get familiar with its **billable items** and **prices**.

## Preparations

2. Go to the [CSS service activation page](https://console.tencentcloud.com/live?from=product-banner-use-lvb), indicate your consent to the "Tencent Cloud Service Terms", and click **Apply for Activation** to activate the CSS service.

## Step 1. Add domain names

To use CSS, you should have at least one **push domain name** and one **playback domain name**. You cannot use one domain name for both push and playback.

1. Prepare your own domain names. For domain names in Chinese mainland regions, ICP filing is required.
2. Log in to the CSS console, enter [**Domain Management**](https://console.tencentcloud.com/live/domainmanage), and click **Add Domain**.![](https://staticintl.cloudcachetci.com/cms/backend-cms/884df034537c11ee974d5254005f490f.png)
  2.1. Tags are used to categorize and manage resources from different dimensions. If the existing tags do not meet your requirements, you can also go to the [Tag Console](https://console.intl.cloud.tencent.com/tag/taglist)to manage tags uniformly.
  2.2. Click  **Add domain**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/650cac86144911f09b3252540044a08e.png)

> **Note:**CSS provides a test domain name `xxxx.livepush.myqcloud.com`. You can use it to test live push, but you’re not advised to use it as the push domain name for business purposes.After the domain name is added successfully, you can view its information in the domain name list in **Domain Management**. For how to manage it, see [Domain Management](https://www.tencentcloud.com/document/product/267/64153).For more information on live streaming domain names, please see [Basic CSS Features](https://intl.cloud.tencent.com/document/product/267/7968).

3. Once your domain name is added, the system will assign it a CNAME domain name (suffixed with `.txlivecdn.com` or `.tlivepush.com`), which cannot be accessed before you complete the CNAME configuration at your DNS service provider. After the CNAME configuration takes effect, you can use CSS. The following example shows you how to add a CNAME record by assuming Tencent Cloud is your DNS service provider:
  3.1. Log in to the [Tencent Cloud Domain Name Service console](https://console.tencentcloud.com/domain).
  3.2. Find the target domain name and click **Resolve**.
  3.3. On the domain name resolution page, click **Add Record**.
  3.4. In the new line, enter the domain name prefix as the host record, select CNAME as the record type, and enter the CNAME domain name as the record value.
  3.5. Click **Save**.

> **Note:**After a CNAME record is successfully added, it takes some time for the CNAME configuration to take effect. If the configuration fails, you cannot use CSS.After the CNAME configuration succeeds, you can see that the status symbol of the CNAME address in [**Domain Management**](https://console.tencentcloud.com/live/domainmanage) in the CSS console has changed to ![](https://staticintl.cloudcachetci.com/cms/backend-cms/bff81031537811ee94c3525400d793d0.png).If the CNAME configuration failure persists, consult your DNS service provider.For more information on how to configure with other DNS service providers, please see [Configuring CNAME for Domain Name](https://intl.cloud.tencent.com/document/product/267/31057).

## Step 2. Get push URL

2. On the **Address Generator** page, configure as follows:
  2.1. Select **Push Domain** for **Domain Type**.
  2.2. Select a push domain name you added in **Domain Management**.
  2.3. Enter an **AppName**. It is `live` by default.
  2.4. Enter a custom `StreamName`, such as `liveteststream`.
  2.5. You need to choose an encryption type based on your security requirements and performance considerations. The encryption type can be either **MD5** or **SHA256**, with **MD5** being the default option.
  2.6. Select the URL expiration time, such as `2024-07-30 16:59:07`.
3. Click **Generate Address** to generate a push address.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6872cd0f4d8b11efbaba525400d5f8ef.png)

> **Note:**In the push URL, `live` is the default `AppName`, `txSecret` is the signature for playing back the stream, and `txTime` is the URL expiration time.Here is another way to generate a push URL: In [**Domain Management**](https://console.tencentcloud.com/live/domainmanage), find the push domain name you want use to generate a push URL, click **Manage**, select **Push Configuration**, enter an expiration time for the URL and a custom `StreamName`, and click **Generate Push Address**.Before generating a push URL, you can create [templates](https://intl.cloud.tencent.com/document/product/267/31069) and bind them to your push domain. For the prices of CSS value-added services, see [Pricing Overview](https://intl.cloud.tencent.com/document/product/267/2819).

## Step 3. Push live stream

- For push on PCs, you're advised to use OBS. For detailed directions, see [Push via OBS](https://intl.cloud.tencent.com/document/product/267/31569).
- For push on web, you're advised to use [**Web Push**](https://console.tencentcloud.com/live/tools/webpush): select a push domain name, enter a custom `StreamName`, select a URL expiration time, turn the camera on, and click **Start Push**.
- For push on mobile devices, download and install Tencent Video Cloud Demo, open it, select **Mobile Live Video Broadcasting** > **Push (Camera)** , enter the push URL into the address box manually or by scanning the QR code, and then tap the start icon in the bottom-left corner to push the stream.

> **Note:**You can integrate Tencent Cloud [MLVB SDK](https://www.tencentcloud.com/document/product/1071?lang=en&pg=) into customized apps for live push.

## Step 4. Get playback URL

2. Select **CSS Toolkit** > [**Address Generator**](https://console.tencentcloud.com/live/addrgenerator/addrgenerator) to get a playback address and configure as follows:
  2.1. Select **Playback Domain** for **Domain Type**.
  2.2. Select a playback domain name you added in **Domain Management**.
  2.3. Enter an **AppName**. It is `live` by default.
  2.4. Enter the `StreamName` in the push URL to play back the corresponding stream.
  2.5. Select the URL expiration time, such as `2024-07-30 16:59:07`.
  2.6. You need to choose an encryption type based on your security requirements and performance considerations. The encryption type can be either**MD5**or **SHA256**, with**MD5** being the default option.
  2.7. To generate a playback URL for a transcoded stream, please select a transcoding template which must be bound to the domain name in the playback URL. For directions on how to bind a transcoding template, please see [Live Transcoding > Binding Domain Name](https://intl.cloud.tencent.com/document/product/267/31071).
  2.8. Click **Generate Address** to generate a playback address.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d2c175154d8b11ef8f105254002693fd.png)

  - For playback test on PCs, you're advised to use tools such as [VLC](https://intl.cloud.tencent.com/document/product/267/32483). For more information, please see [Live Playback](https://intl.cloud.tencent.com/document/product/267/31559).
  - For playback test on mobile devices, you're advised to download and install Tencent Video Cloud Toolkit App, select **Mobile Live Video Broadcasting** > **LVB Playback**, enter the playback URL into the address box manually or by scanning the QR code, and tap the play icon in the bottom-left corner.

> **Note:**To push/play back a stream on an app, you can integrate the[MLVB SDK](https://www.tencentcloud.com/products/mlvb) into the app to supplement the CSS service. If you encounter any problem during the trial period, please see [FAQs](https://intl.cloud.tencent.com/document/product/267/7968).

## Step 5.Generate Push and Playback Address Group

1. Go to **CSS Toolkit** > [Address Generator](https://console.intl.cloud.tencent.com/live/addrgenerator/addrgenerator).
2. Select the address type as **Push and playback URLs**.
3. Select the**Push Domain Name** and **Playback Domain Name** that you have added to Domain Management.
4. Enter an**AppName**. It is` live` by default.
5. Enter a StreamName, such as` liveteststream`.
6. You need to choose an encryption type based on your security requirements and performance considerations. The encryption type can be either **MD5** or **SHA256**, with **MD5** being the default option.
7. Select the URL expiration time, such as `2024-07-30 16:59:07`.
8. Select an existing transcoding template (optional).
9. Click**Generate Address.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/19b1d6f54d8c11ef8357525400bdab9d.png)

## Operations

- To enable **live recording**, please create a recording template and bind it to a domain name first. For more information, please see [Creating Recording Template](https://intl.cloud.tencent.com/document/product/267/34223).
- To enable **live transcoding**, please create a transcoding template and bind it to a domain name first. For more information, please see [Creating Transcoding Template](https://intl.cloud.tencent.com/document/product/267/31071).
- To enable **live watermarking**, please create a watermark template and bind it to a domain name first. For more information, please see [Creating Recording Template](https://intl.cloud.tencent.com/document/product/267/31073).
- To enable **live screencapture and porn detection**, please create a screencapture and porn detection template and bind it to a domain name first. For more information, please see [Creating Screencapture and Porn Detection Template](https://intl.cloud.tencent.com/document/product/267/31072).
- To enable  **Live Time Shift** , you can create a time shift template and bind it to a domain name. For more information, please see [Creating Time Shift Template](https://www.tencentcloud.com/document/product/267/53312).
- To enable**live streaming callbacks**, you can create a callback template and associate it with the domain for configuration. For related documentation, please refer to [Creating a Callback Template](https://www.tencentcloud.com/document/product/267/31074).
- To enable **Live Audit** , you can create an audit template and bind it to a domain name. For more information, please see [Creating Audit Template](https://www.tencentcloud.com/document/product/267/58265).
- To enable **Live Subtitle** , you can create a subtitle template and bind it to a domain name. For more information, please see [Creating Subtitle Template](https://www.tencentcloud.com/document/product/267/58144).
- To enable**live streaming standby content**, you can create a standby content template and associate it with the domain for configuration. For related documentation, please refer to [Creating a Standby Content Template](https://www.tencentcloud.com/document/product/267/53400?lang=en&pg=).
- To enable **live stream mixing**, please call the stream mixing API [CreateCommonMixStream](https://intl.cloud.tencent.com/document/product/267/35997).
- To enable **Live Adaptive Bitrate** , you can create an adaptive bitrate template and bind it to a domain name. For more information, please see [Creating Adaptive Bitrate Template](https://www.tencentcloud.com/document/product/267/50271).

## FAQs

- [What are the differences between push, live streaming, and video on demand?](https://intl.cloud.tencent.com/document/product/267/7968#.E6.8E.A8.E6.B5.81.E3.80.81.E7.9B.B4.E6.92.AD.E5.92.8C.E7.82.B9.E6.92.AD.E5.88.86.E5.88.AB.E6.98.AF.E4.BB.80.E4.B9.88.EF.BC.9F)
- [What push protocols are supported?](https://intl.cloud.tencent.com/document/product/267/7968#.E6.94.AF.E6.8C.81.E5.93.AA.E4.BA.9B.E6.8E.A8.E6.B5.81.E5.8D.8F.E8.AE.AE.EF.BC.9F)
- [What playback protocols are supported?](https://intl.cloud.tencent.com/document/product/267/7968#.E6.94.AF.E6.8C.81.E5.93.AA.E4.BA.9B.E6.92.AD.E6.94.BE.E5.8D.8F.E8.AE.AE.EF.BC.9F)
- [What does a playback URL consist of?](https://intl.cloud.tencent.com/document/product/267/7968#.E6.92.AD.E6.94.BE.E5.9C.B0.E5.9D.80.E7.94.B1.E4.BB.80.E4.B9.88.E7.BB.84.E6.88.90.EF.BC.9F)
- [How do I splice multiple live stream URLs?](https://intl.cloud.tencent.com/document/product/267/38393)


---
*Source: [https://www.tencentcloud.com/document/product/267/13551](https://www.tencentcloud.com/document/product/267/13551)*
