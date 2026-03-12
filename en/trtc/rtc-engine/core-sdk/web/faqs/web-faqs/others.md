# Others

## 1. Basics

### What browsers does the TRTC Web SDK support?

Refer to [Supported Platforms](https://www.tencentcloud.com/document/product/647/59733).

### How do I test my audio/video devices before making a call?

Please see [Detect Capabilities](https://www.tencentcloud.com/document/product/647/59656).

### How do I test my current network quality?

Please see [Detect Network Quality](https://www.tencentcloud.com/document/product/647/59655).

### I can use the TRTC web SDK in a local development environment but not after it is deployed online. What should I do?

If you can use the SDK in a local development environment but cannot capture data from the camera or mic after deploying it to the web, check whether your webpage is deployed using HTTP. If so, use HTTPS instead and make sure you have a valid HTTPS certificate.

For more information, see [Domain Name and Protocol Support](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-05-info-browser.html#h2-2).

### Does the web SDK support the dual-stream mode, watermarking?

You can refer to  [Enable Dual-Channel Mode](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-27-advanced-small-stream.html), and [Enable Watermarking](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-29-advance-water-mark.html) to enable the advanced features.

### What are the known issues of WebRTC?

Refer to [WebRTC Known Issues and Solutions](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-02-info-webrtc-issues.html).

### **What is the main/sub video stream?**

1. TRTC has a main video stream (main stream) and an sub video stream (sub stream).
2. The camera is published through the main stream, and the screen sharing is published through the sub stream.
3. The main video stream includes: big stream and small stream. By default, [TRTC.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo) plays the big stream, and the small stream can be played through the small parameter. Refer to: [Optimize Multi-Person Video Calls](https://www.tencentcloud.com/document/product/647/59665).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/937c27f7eff611eea8b9525400257aad.png)

## 2. Capturing and Publishing

### Why can I turn on the camera or microphone?

Refer to [DEVICE_ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.DEVICE_ERROR).

### Why am I unable to publish or play streams on some mobile browsers?

Refer to [Supported Platforms](https://www.tencentcloud.com/document/product/647/59733).

If your browser is not listed in the above document, you can open the [TRTC compatibility check](https://web.sdk.qcloud.com/trtc/webrtc/demo/detect/index.html) page with the browser to test whether it fully supports WebRTC.

### Can I change the video profile(resolution, frameRate, bitrate)?

Refer to [Set Encoding Profile](https://www.tencentcloud.com/document/product/647/59654).

### Why does the camera support capturing 1080p, but the captured resolution is less than 1080p?

This situation is generally due to the fact that the camera is occupied by low-resolution ahead of time, resulting in the SDK not being able to capture the target resolution.

Solution: Check the business side logic, if the camera is captured in advance, please release the camera in time when it is no longer in use.

### Can I modify the style of screen sharing pop-up window in the TRTC Web SDK?

No. The style of screen sharing is controlled by browsers and cannot be modified.

### How do I capture system audio during screen sharing in the TRTC Web SDK?

Refer to [Screen Sharing](https://www.tencentcloud.com/document/product/647/59651).

### How do I switch the camera/mic?

Refer to [Media Device](https://www.tencentcloud.com/document/product/647/59652).

### How to detect camera added and removed?

Refer to [Media Device](https://www.tencentcloud.com/document/product/647/59652).

### What should I do if the error "Permission denied" occurs when I use the TRTC web SDK in iframes?

To use WebRTC in iframes, you need to add the following attribute to the iframe tag to obtain the permissions needed.
Mic, camera, and screen sharing permissions:

```
<iframe allow="microphone; camera; display-capture;">
```

## 3. Playing

### Why is there video but no audio during a call?

It may be because of the browserâs autoplay policy, which causes the âPLAY_NOT_ALLOWEDâ error. To solve the problem, please see [Handle Autoplay Restriction](https://www.tencentcloud.com/document/product/647/59666).

### Why does the sound output change from speaker to handset after microphone being captured?

On Android, there are usually multiple microphones, and the label list is: ['default', 'Speakerphone', 'Headset earpiece'].

If you do not specify the microphone in trtc.startLocalAudio, the browser default microphone may be the Headset earpiece and the sound will come out of the handset.

If you need to play out through the speaker, you need to specify the microphone with the label 'Speakerphone'.

## 4. Others

### How to get current volume of microphone?

Refer to [Audio Volume](https://www.tencentcloud.com/document/product/647/59653).

### What triggers the trtc.on(TRTC.EVENT.KICKED_OUT) event?

The event is triggered when a user is removed from a room, for example, when the same user ID is used to log in from different devices or when the RESTful API [RemoveUser](https://intl.cloud.tencent.com/document/product/647/34268) is called to remove a user. For more information, see  [KICKED_OUT](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/module-EVENT.html#.KICKED_OUT)ã

> **Note:**Repeated login is not allowed by the SDK (it may cause call exceptions) and should be avoided at the business layer.

### Causion for Using Vue 3

When the Vue3 framework is used, it is necessary to use the markRaw interface to mark the trtc instance to avoid the conversion of trtc into the Proxy object by Vue, which may cause some unexpected problems.

```
import { markRaw } from 'vue';const trtc = markRaw(TRTC.create());
```

### Why mobile phone get hot when make a multi-person video call

Refer to [Optimize Multi-Person Video Calls](https://www.tencentcloud.com/document/product/647/59665).


---
*Source: [https://trtc.io/document/37340](https://trtc.io/document/37340)*
