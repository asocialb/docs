# 8.Enabling Screen Sharing

This document describes how to share the screen. Currently, a TRTC room can have only one screen sharing stream at a time.

TRTC supports screen sharing in primary stream and substream modes on Electron:

- **Substream sharing**
In TRTC, you can share the screen via a dedicated stream called the **substream**. In substream sharing, an anchor publishes camera video and screen sharing images at the same time. This is the scheme used by VooV Meeting. You can enable substream sharing by setting the `TRTCVideoStreamType` parameter to `TRTCVideoStreamTypeSub` when calling the `startScreenCapture` API.
- **Primary stream sharing**
In TRTC, the channel via which camera images are published is the primary stream (**bigstream**). In primary stream sharing, an anchor publishes screen sharing images via the primary stream. As there is only one stream, an anchor cannot publish both camera video and screen sharing images. You can enable this mode by setting the `TRTCVideoStreamType` parameter to `TRTCVideoStreamTypeBig` when calling the `startScreenCapture` API.

## Step 1. Get sharing sources

> **explain** On Electron, the desktop also counts as a window. When two monitors are used, each monitor corresponds to a desktop window. The list returned via `getScreenCaptureSources` includes desktop windows.

Based on the obtained window information, you can display a list of sharable sources on the UI for users to choose from.

```
import TRTCCloud from 'trtc-electron-sdk';const rtcCloud = new TRTCCloud();// https://web.sdk.qcloud.com/trtc/electron/doc/en-us/trtc_electron_sdk/TRTCCloud.html#getScreenCaptureSourcesconst screenList = rtcCloud.getScreenCaptureSources();
```

## Step 2. Start screen sharing

- After selecting a sharing source, you can call the [startScreenCapture](https://web.sdk.qcloud.com/trtc/electron/doc/en-us/trtc_electron_sdk/TRTCCloud.html#startScreenCapture) API to start screen sharing.
- During screen sharing, you can call [selectScreenCaptureTarget](https://web.sdk.qcloud.com/trtc/electron/doc/en-us/trtc_electron_sdk/TRTCCloud.html#selectScreenCaptureTarget) to change the sharing source.
- The difference between [pauseScreenCapture](https://web.sdk.qcloud.com/trtc/electron/doc/en-us/trtc_electron_sdk/TRTCCloud.html#pauseScreenCapture) and [stopScreenCapture](https://web.sdk.qcloud.com/trtc/electron/doc/en-us/trtc_electron_sdk/TRTCCloud.html#stopScreenCapture) is that `pauseScreenCapture` pauses screen capturing and displays the image at the moment it is paused. Remote users see the paused video image until screen capturing is resumed.

```
import TRTCCloud, {     Rect, TRTCScreenCaptureProperty, TRTCVideoStreamType, TRTCVideoEncParam,    TRTCVideoResolution, TRTCVideoResolutionMode} from 'trtc-electron-sdk';const rtcCloud = new TRTCCloud();// https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCCloud.html#getScreenCaptureSourcesconst screenList = rtcCloud.getScreenCaptureSources();// https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/Rect.htmlconst captureRect = new Rect(0, 0, 0, 0);// https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCScreenCaptureProperty.htmlconst property = new TRTCScreenCaptureProperty(    true, true, true, 0, 0, false);if (screenList.length > 0) {    rtcCloud.selectScreenCaptureTarget(screenList[0], captureRect, property)}const screenshareDom = document.querySelector('screen-dom');// https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCVideoEncParam.htmlconst encParam = new TRTCVideoEncParam(    TRTCVideoResolution.TRTCVideoResolution_1920_1080,    TRTCVideoResolutionMode.TRTCVideoResolutionModeLandscape,    15,    2000,    0,    false); rtcCloud.startScreenCapture(screenshareDom, TRTCVideoStreamType.TRTCVideoStreamTypeSub, encParam);
```

## Step 3. Set the video quality

| Clarity | Resolution | Frame Rate | Bitrate |
| --- | --- | --- | --- |
| HD+ | 1920 x 1080 | 10 | 2000 kbps |
| HD | 1280 x 720 | 10 | 600 Kbps |
| SD | 960 Ã 720 | 10 | 400 Kbps |

## Step 4. Watch the shared screen

```
import TRTCCloud, {     TRTCVideoStreamType} from 'trtc-electron-sdk';const rtcCloud = new TRTCCloud();const remoteDom = document.querySelector('.remote-user');function onUserSubStreamAvailable(userId, available) {    if (available === 1) {        rtcCloud.startRemoteView(userId, remoteDom, TRTCVideoStreamType.TRTCVideoStreamTypeSub);    } else {        rtcCloud.stopRemoteView(userId, TRTCVideoStreamType.TRTCVideoStreamTypeSub);    }}rtcCloud.on('onUserSubStreamAvailable', onUserSubStreamAvailable);
```

## FAQs

#### 1. Can there be multiple channels of screen sharing streams in a room at the same time?

Currently, a TRTC room can have only one screen sharing stream at a time.

#### 2. When a specified window (`SourceTypeWindow`) is shared, if the window size changes, will the resolution of the video stream change accordingly?

By default, the SDK automatically adjusts encoding parameters according to the size of the shared window.
If you want a fixed resolution, call the `setSubStreamEncoderParam` API to set encoding parameters for screen sharing or specify the parameters when calling the `startScreenCapture` API.


---
*Source: [https://trtc.io/document/47619](https://trtc.io/document/47619)*
