# Live Push

The nature of CSS is a streaming process, similar to the live broadcast of TV channels sent to audience through cable networks. To complete this process, CSS needs to have a capture and push device (similar to a camera), a cloud live streaming service (similar to a cable network), and a playback device (similar to a TV set). These devices can be smart devices such as mobile phones, PCs, and tablets as well as web browsers. We provide complete software demos for different types of devices.

## Preparations

2. Select [**Domain Management**](https://console.tencentcloud.com/live/domainmanage), click **Add Domain** to add a push domain name with an ICP filing number. For more information, please see [Adding Domain Name](https://intl.cloud.tencent.com/document/product/267/35970).

> **Note:**CSS provides a default push domain name in the format of `xxx.push.tlivecloud.com`. We recommend you not use it as the push domain name for your real business.

## Getting Push Address

1. Log in to the CSS console, select **Toolkit** > [**Address Generator**](https://console.tencentcloud.com/live/addrgenerator/addrgenerator) to generate a push address and configure as follows:
  - Select **Push Address** as the domain type.
  - Select the push domain name you added in domain management.
  - Enter an `AppName` (`live` by default). This is used to differentiate the paths of different applications under the same domain name.
  - Enter a custom `StreamName`, such as `liveteststream`.
  - Select an encryption type based on the security needs and performance considerations. The available encryption types are **MD5** or **SHA256**, with **MD5** being the default option.
  - Select the expiration time of the address, such as `2024-03-21 11:49:04`.
2. Click **Generate Address**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/84b1a2e2e77a11eebbb2525400564496.png)

> **Note:**To ensure the security of your live streams, the system will automatically enable push authentication. You can also select the push domain name to be modified in [**Domain Management**](https://console.tencentcloud.com/live/domainmanage) and click **Manage** on the right to enter the domain name details page and customize the authentication information in **Push Configuration**. The push address is in the following format:
> `rtmp://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)`In addition to the above method, you can also select a push domain name in [**Domain Management**](https://console.tencentcloud.com/live/domainmanage) in the CSS console, click **Manage**, select **Push Configuration**, enter the expiration time of the push address and the custom `StreamName`, and click **Generate Push Address** to generate a push address.
> -If you need a **persistent push address**, you can enter [**Domain Management**](https://console.tencentcloud.com/live/domainmanage), select a push domain name, click **Manage**, and select **Push Configuration** for calculation and generation by referring to the sample code in **Push Address Sample Code**. For more information, please see [How can I view the push sample code?](https://intl.cloud.tencent.com/document/product/267/31059).

## Live Push

You can use the following methods to implement live push based on your business scenario:

### Scenario 1. PC push

For PC (Windows/macOS), you can choose to install [OBS](https://obsproject.com/download) or [XSplit](https://www.xsplit.com) for push. The former is a free open-source video recording and streaming program that supports operating systems such as Windows, macOS, and Linux, while the latter is a paid program that offers a standalone installer for live game streaming. For non-game live streaming, we recommend you use BroadCaster.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a6e96a5f515a11eeabd75254005810a4.png)

This document uses push with OBS as an example to describe the steps. Assume that the prepared push address is:

```
rtmp://xxxx.livepush.myqcloud.com/live/xxxx_test?bizid=xxxx&txSecret=xxx&txTime=58540F7F
```

1. Go to [OBS official website](https://obsproject.com/download) to download and install the push tool.
2. Open OBS and click **Controls** > **Settings** at the bottom to enter the settings page.
3. Click **Stream** to enter the push configuration page and set as follows:
  3.1. Select "Custom" as the service type.
  3.2. Enter the first half of the push address as the server, such as `rtmp://xxxx.livepush.myqcloud.com/live/`.
  3.3. Enter the second half of the push address as the stream key, such as `xxxx?bizid=xxxx&txSecret=xxx&txTime=58540F7F`.
  3.4. Click **OK** in the bottom-right corner.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8c6a912ee77b11ee91ba525400aa857d.png)

4. Click **Controls** > **Start Streaming** to test streaming. For more information on how to use OBS, please see [Push via OBS](https://intl.cloud.tencent.com/document/product/267/31569).

### Scenario 2. Web push

2. Select **Toolkit** > [**Web Push**](https://console.tencentcloud.com/live/tools/webpush).
3. Perform the following settings on the web push page:

You can choose Single stream or Multiple streams. For detailed operational procedures, see [Web Push](https://intl.cloud.tencent.com/document/product/267/35968).

  - After deciding on the collection method, configuration, and push settings.
  - Click **Generate** to proceed to the address generator configuration page.
  - Select a push domain name.
  - Enter an `AppName` (`live` by default). This is used to differentiate the paths of different applications under the same domain name.
  - Enter a custom `StreamName`, such as `liveteststream`.
  - Select an expiration time, such as `2024-03-21 11:55:59`.
4. Click **Start Push** and grant the camera permission to start the push.

> **Note:**The web push feature requires that your device have a camera installed and its browser support the Flash plugin to call the camera permission.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/46f6aeece77d11ee91ba525400aa857d.png)

### Scenario 3. Live SDK push

1. Download the MLVB SDK.
2. Complete the integration as instructed in the iOS or Android integration document.

The live SDK is a collection of mobile live streaming services. It demonstrates in the form of free source code how to use Tencent Cloud CSS, VOD, IM, and COS to build the most appropriate live streaming solution for your business. For more details, see [Mobile Live Video Broadcasting (MLVB) SDK](https://intl.cloud.tencent.com/products/mlvb).

## FAQs

- [How can I implement live playback?](https://intl.cloud.tencent.com/document/product/267/31559)
- [How can I splice a push URL?](https://intl.cloud.tencent.com/document/product/267/38393)
- [How can I calculate a hotlink protection URL?](https://intl.cloud.tencent.com/document/product/267/31560)


---
*Source: [https://www.tencentcloud.com/document/product/267/31558](https://www.tencentcloud.com/document/product/267/31558)*
