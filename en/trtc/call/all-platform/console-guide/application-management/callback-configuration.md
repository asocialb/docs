# Callback Configuration

The Event callback service notifys your server of real-time audio and video service events in the form of HTTP/HTTPS requests. The Event callback service integrates some events in the Room Event and Media Event groups. You can fill in the callback configuration information on the [Tencent RTC console](https://console.trtc.io)by following the instructions below. After the configuration is complete, you can receive the callback event notification.

## Preconditions

1. Enter [Tencent RTC console > Advanced Features](https://console.trtc.io/features), select the target application in the top-left corner . Meanwhile, you can also click **Create** to quickly create a new application here.
2. Enter the Advanced Features configuration page of the target application, and set the callback configuration in **Callback Configuration**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bcd8ef6bcb6511f087ad52540099c741.png)

## Set the callback key and URL

1. Click in the upper right corner of the callback Configuration TAB to **edit**.
2. Set the callback key (optional) based on service requirements.
3. Enter a callback URL based on service requirements (required):
  - Room event callback: Event notification for creating/dissolving rooms, entering/exiting rooms, etc. [More callback event descriptions.](https://www.tencentcloud.com/document/product/647/39558)
  - Media event callback: Start/stop push video data, start/stop push audio data, start/stop push auxiliary route data and other event notifications. [More callback event descriptions.](https://www.tencentcloud.com/document/product/647/39558)
  - Recording callback: It is used to call back events related to the [on-cloud recording](https://trtc.io/document/45169) function, and supports event notification of the start and exit of the on-cloud recording module, the start of the cloud recording upload module, and the end of the upload. [More callback event descriptions.](https://www.tencentcloud.com/document/product/647/54914)
  - Relay to CDN callback: Event callbacks used to enable the [Relay to CDN](https://trtc.io/document/48245) function. [More callback event descriptions](https://www.tencentcloud.com/document/product/647/54913).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa4bf65ecb6511f08942525400e889b2.png)

> **Noteï¼**Callback URL Protocol header: HTTP, HTTPS, and can contain only the following characters: a-z, A-Z, 0-9, -, _, and? , %, =, #,., /, and + contain a maximum of 2083 characters.

4. Click **Confirm** to successfully set the callback URL.


---
*Source: [https://trtc.io/document/39559](https://trtc.io/document/39559)*
