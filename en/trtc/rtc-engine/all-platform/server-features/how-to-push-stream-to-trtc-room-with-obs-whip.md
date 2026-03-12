# How to push stream to TRTC room with OBS WHIP

## Overview

OBS includes WHIP support, which allows you to do many interesting things by combining the powers of both OBS and WHIP.

WHIP is a standard protocol that lets you use HTML5 and different clients to publish and play live streams. Plus, you can use open-source tools to build your own live streaming platform.

You can also use TRTC (Tencent Real-Time Communication) cloud services with OBS WHIP support for a streaming platform. This is a great option if you don't want to build your own platform or need a more reliable and stable platform with dedicated support.

Additionally, TRTC (Tencent Real-Time Communication) provides a free trial that includes a specific amount of streaming time, making it super easy for you to try out.

If you need help or run into any problems, don't hesitate to contact us on [Discord](https://discord.gg/vDHty6ddrZ).

## Prerequisites

Before you move forward, double-check that you've got these necessary items ready:

- OBS with WHIP support, please download from [OBS](https://obsproject.com/)
- TRTC (Tencent Real-Time Communication) account, please register [here](https://www.tencentcloud.com/account/login?s_url=https%253A%252F%252Fconsole.tencentcloud.com%252Ftrtc&utm_source=community&utm_medium=github&utm_campaign=OBS-WHIP-TRTC&_channel_track_key=6vGiu0P3)

Next, you need to create a TRTC application and generate a Bearer Token for WHIP.

## Step 1: Create a TRTC application

Please follow the steps below to create a TRTC application:

1. Log in to the [Tencent RTC Console](https://console.trtc.io/app) and click **Create Application**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/37f69b16508011ef9bf1525400a9236a.png)

2. In the creation pop-up, based on the actual business needs, select a product and enter the application name, select the Data Storage **Region**, and click **Create**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fddbe3a7508011efb66652540055f650.png)

3. After completing the application creation, you will automatically enter the application details page of the selected product. You can view the `SDKAppID` and `SDKSecretKey` in the **Application Overview**, which will be used in subsequent steps.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f64f834c508011efbaba525400d5f8ef.png)

## Step 2: Create a Bearer Token for WHIP

Following that, you must generate a Bearer Token for WHIP, which will be utilized in OBS.

You can directly visit [https://tencent-rtc.github.io/obs-trtc/bearer.html](https://tencent-rtc.github.io/obs-trtc/bearer.html) to create a WHIP Bearer Token. Ensure that use the AppID with your own `SDKAppID` and secret with your own `SDKSecretKey`, then click the `Generate Bearer Token` button.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/677cd8520b2b11eea359525400088f3a.png)

> **Noteï¼**You can also access the url `https://tencent-rtc.github.io/obs-trtc/bearer.html?appid=2000xxx&secret=yyyyyy` to setup the parameters.

Next, use the generated WHIP Bearer Token to configure OBS.

## Step 3: Configure OBS

In the `OBS WHIP` section, you will find the generated WHIP `Server` and `Bearer Token` for configuring OBS.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7f8ca6760b2b11eead3b5254007e6a5b.png)

Please follow the steps below to configure OBS:

1. Open OBS and click **Settings**.
2. Click **Stream** on the left sidebar.
3. Select `WHIP` for **Service**.
4. Make sure to input the `Server` and `Bearer Token` accurately.
5. Click **OK** to save the settings.
6. Click **Start Streaming** to start.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8c4822660b2b11eead3b5254007e6a5b.png)

At this point, the stream is streaming to the TRTC service.

## Step 4: Play the stream

Open the previous webpage, go to the `WHEP Player` section, and click **Play Stream** to play the stream via WHEP.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9f50b1f80b2b11ee95bc5254002af9e0.png)

Another option is to go to the `TRTC Room` section, and click **Join Room** to access the TRTC room and watch the stream via TRTC, or you can utilize the TRTC mobile SDK to join the room and view the stream.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa304be50b2b11eea359525400088f3a.png)

Since both WHIP and WHEP are standard protocols, you can utilize any client that supports them to play the stream.

## Conclusion

We looked into using TRTC (Tencent Real-Time Communication) cloud services to make a stronger streaming platform and the steps needed to create a TRTC app with OBS WHIP help. These tools make it easier to organize and provide real-time live streaming experiences for different situations, with the power of OBS.

If you require assistance or encounter any difficulties, please feel free to reach out to us via [Discord](https://discord.gg/vDHty6ddrZ).


---
*Source: [https://trtc.io/document/55633](https://trtc.io/document/55633)*
