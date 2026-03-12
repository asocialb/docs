# Screen Sharing

This tutorial mainly introduces how to implement screen sharing in TRTC Web SDK.

## Demo

## Usage

### Start Screen Sharing

Call [trtc.startScreenShare()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startScreenShare) to start screen sharing.

```
const trtcA = TRTC.create();await trtcA.enterRoom({  scene: 'rtc',  sdkAppId: 140000000, // Fill in your sdkAppId  userId: 'userA', // Fill in your userId  userSig: 'userA_sig', // Fill in userSig corresponding to userId  roomId: 6969})await trtcA.startScreenShare();// Setting a view if you need to preview local screen sharing.await trtcA.startScreenShare({ view: 'local-screen-sharing-element-id' });
```

The SDK uses the **1080p** parameter configuration by default to capture screen sharing, you can customize this parameter by referring to [trtc.startScreenShare({ option: { profile: '720p' }})](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startScreenShare)

### Play Remote Screen Sharing

```
const trtcB = TRTC.create();trtcB.on(TRTC.EVENT.REMOTE_VIDEO_AVAILABLE, ({ userId, streamType }) => {  // Main video stream  if (streamType === TRTC.TYPE.STREAM_TYPE_MAIN) {    trtcB.startRemoteVideo({ userId, streamType,  view: `${userId}_main` });  } else {    // Sub video stream, it's remote screen sharing.    // 'view' is the element id of a div for video playback.    trtcB.startRemoteVideo({ userId, streamType, view: `${userId}_screen` });  }});await trtcB.enterRoom({  scene: 'rtc',  sdkAppId: 140000000, // Fill in your sdkAppId  userId: 'userB', // Fill in your userId  userSig: 'userB_sig', // Fill in userSig corresponding to userId  roomId: 6969})
```

> **What is the main/sub video stream?**TRTC has a main video stream (main stream) and an sub video stream (sub stream).The camera is published through the main stream, and the screen sharing is published through the sub stream.The main video stream includes: big stream and small stream. By default, [TRTC.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo) plays the big stream, and the small stream can be played through the small parameter. Refer to: [Optimize Multi-Person Video Calls](https://www.tencentcloud.com/document/product/647/59665).![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ced93f93e5ec11eeb0c55254001a1c03.png)

### Screen Sharing + System Audio

```
await trtcA.startScreenShare({ option: { systemAudio: true }});
```

Capturing system audio is only supported by Chromium based browser M74+, such as Chrome, Edge, Opera.

| OS | System Audio | Tab Audio |
| --- | --- | --- |
| Windows | Yes | Yes |
| MacOS | No | Yes |
| Linux | No | Yes |
| Non-Chromium based browser, such as Safari, Firefox | No | No |

Check Share audio in the pop-up dialog box, and the system audio will be mixed with the local microphone and published. Other users in the room will receive the [TRTC.EVENT.REMOTE_AUDIO_AVALIABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_AUDIO_AVAILABLE) event.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/73d4f70ce50611eeadff525400e97a5f.png)

### Stop Screen Sharing

1. Call [trtc.stopScreenShare()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopScreenShare) to stop screen sharing.
2. Other users in the room will receive the [TRTC.EVENT.REMOTE_VIDEO_UNAVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_VIDEO_UNAVAILABLE) event, and streamType is [TRTC.TYPE.STREAM_TYPE_SUB](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.STREAM_TYPE_MAIN).

```
 // Stop screen sharing await trtcA.stopScreenShare(); trtcB.on(TRTC.EVENT.REMOTE_VIDEO_UNAVAILABLE, ({ userId, streamType }) => {    // Remote user stopped the screen sharing.    if (streamType === TRTC.TYPE.STREAM_TYPE_SUB) {} })
```

In addition, users may also stop screen sharing through the browser's own button, SDK will stop screen sharing when user click the **Stop Button**. You can listen for the [TRTC.EVENT.SCREEN_SHARE_STOPPED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.SCREEN_SHARE_STOPPED) event.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/19723fece50a11eeb1eb525400b5f95f.png)

```
// Listen for local screen sharing stop eventtrtcA.on(TRTC.EVENT.SCREEN_SHARE_STOPPED, () => {  console.log('screen sharing was stopped');});
```

## FAQ

1. Safari screen sharing error **getDisplayMedia must be called from a user gesture handler**

This is because Safari restricts the **getDisplayMedia** screen capture interface, which must be called within 1 second of the callback function of the user click event.

Refer to: [webkit issue](https://bugs.webkit.org/show_bug.cgi?id=198040).

```
// goodasync function onClick() {  // It is recommended to execute the collection logic first when onClick is executed  await trtcA.startScreenShare();  await trtcA.enterRoom({     roomId: 123123,    sdkAppId: 140000000, // Fill in your sdkAppId    userId: 'userA', // Fill in your userId    userSig: 'userA_sig', // Fill in userSig corresponding to userId  });}// badasync function onClick() {  await trtcA.enterRoom({     roomId: 123123,    sdkAppId: 140000000, // Fill in your sdkAppId    userId: 'userA', // Fill in your userId    userSig: 'userA_sig', // Fill in userSig corresponding to userId  });  // Entering the room may take more than 1s, and the collection may fail  await trtcA.startScreenShare();}
```

2. Mac Chrome screen sharing fails with the error message "NotAllowedError: Permission denied by system" or "NotReadableError: Could not start video source" when screen recording is already authorized.

It's a [Chrome bug](https://bugs.chromium.org/p/chromium/issues/detail?id=1306876). Solution:

  2.1. Open **Mac System Settings**
  2.2. Click **Security & Privacy**
  2.3. Click **Privacy**
  2.4. Click **Screen Recording**
  2.5. Turn off Chrome screen recording authorization
  2.6. Reopen Chrome screen recording authorization
  2.7. Close Chrome browser
  2.8. Reopen Chrome browser


---
*Source: [https://trtc.io/document/59651](https://trtc.io/document/59651)*
