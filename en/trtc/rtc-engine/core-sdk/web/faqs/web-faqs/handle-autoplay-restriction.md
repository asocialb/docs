# Handle Autoplay Restriction

## Introduction

In order to prevent web pages from automatically playing audio and video and causing interference to users, browsers have restricted the automatic playback function of audio and video: **before the user interacts with the web page (such as clicking, touching the page, etc.), the web page will be prohibited from playing media with sound.** **In iOS 10+, if low power mode is enabled, media without sound will also be prohibited from playing.**

Affected by the above browser autoplay policy, users may not be able to hear the sound when playing audio. The most common business scenario for this issue is that the users are able to enter the room and start remote audio automatically without user interaction(e.g. click) after refreshing the page.

This tutorial mainly introduces **how to solve the issue of playback failure caused by the restriction of autoplay policy**.

## Solutions

### 1. Use the SDK's autoplay popup window

By default, when autoplay fails, the SDK will pop up to guide the user to interact with the page. After the interaction occurs, the SDK will actively call the interface to resume playback.

- **Advantage**: The business side does not need to do anything, simple and efficient.
- **Disadvantage**: The popup window provided by the SDK may not meet the design requirements of the business product. At this time, you can consider using Solution 2.

The popup window provided by the SDK is adapted to desktop and mobile browser, and the style is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f2b91ca2e51611eeadff525400e97a5f.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f60fa586e51611ee9f745254008eb8a8.png)

- The SDK will switch the English and Chinese popup prompts according to the value of [navigator.language](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/language).
- When the user clicks "OK", the SDK automatically calls the relevant interface to resume playback.
- In order to ensure that the popup window is displayed on the top layer as much as possible, its z-index value is 1500.

### 2. Business side provides popup window processing

If Solution 1 does not meet your product design requirements, you can also solve the autoplay problem in the following ways.

2.1 Setting the `enableAutoPlayDialog` parameter in the [trtc.enterRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom) interface to `false` to turn off the SDK's popup window.

2.2 Listening to the [AUTOPLAY_FAILED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.AUTOPLAY_FAILED) event, and guiding the user to click the page when the event triggered. The SDK will automatically resume the audio playback after the user clicks the page.

2.3 In product design, it is recommended to guide users to interact with the page before entering the room (such as clicking the enter room button), which can avoid autoplay failure.

```
trtc.on(TRTC.EVENT.AUTOPLAY_FAILED, event => {  // Guide the user to click the page, you can pop up a prompt.});await trtc.enterRoom({ enableAutoPlayDialog: false });
```

Most browsers release the autoplay restriction after user interaction, and this step can effectively avoid the error of autoplay failure. However, due to the differences in the implementation of autoplay policies by various browser manufacturers, even if users are guided to interact with the page in advance, autoplay failure errors may still occur. Therefore, you still need to listen to the [AUTOPLAY_FAILED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.AUTOPLAY_FAILED) event, and guiding the user to click the page.

For example: In the iOS WeChat browser and its mini-program webview, when playing a remote stream for the first time on the page, **you must call the playback interface in the callback function of the user click event**, otherwise playback will fail. If you use setTimeout and other interfaces to asynchronously call the playback interface in the callback of the user click event, you will also encounter autoplay failure errors.

## Disable Autoplay Policy in Webview

The default autoplay policy in Android and iOS Webview may be different to the browser. You can refer to the following document to turn off autoplay restrictions in your App.

- Android Webview: Call [setMediaPlaybackRequiresUserGesture(false)](https://developer.android.com/reference/android/webkit/WebSettings#setMediaPlaybackRequiresUserGesture(boolean)).
- iOS Webview: Set [mediaTypesRequiringUserActionForPlayback](https://developer.apple.com/documentation/webkit/wkwebviewconfiguration/1851524-mediatypesrequiringuseractionfor) to WKAudiovisualMediaTypeNone.

## Reference

- [Chrome autoplay restriction policy](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes)
- [Safari autoplay restriction policy](https://webkit.org/blog/7734/auto-play-policy-changes-for-macos/)


---
*Source: [https://trtc.io/document/59666](https://trtc.io/document/59666)*
