# Live Streaming

This tutorial mainly introduces how to implement the Live Streaming by using scene [**live**](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.SCENE_LIVE).

## Demo

## TRTC Scene and Roles

In general business scenarios, not all users need to publish streams, and some users only need to subscribe streams.

There are two types of scene in TRTC

- Scene [rtc](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.SCENE_RTC): Default scene. All users in rtc scene are anchors, and there are no audience role in this scene.
- Scene [live](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.SCENE_LIVE): Users in this scene can be divided into two roles, the [anchor](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.ROLE_ANCHOR) and the [audience](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.ROLE_AUDIENCE). The difference between the two roles is:
  - The [anchor](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.ROLE_ANCHOR) can publish the stream. A room supports up to 50 anchors to publish streams at the same time.
  - The [audience](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.ROLE_AUDIENCE) can not publish the stream. There is no limit on the number of audiences.

## Anchor Side

The process of implementing audio and video calls on the anchor side is basically the same as the implementation process of the [rtc](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.SCENE_RTC) scene. Refer to: [Basic Audio/Video Call](https://www.tencentcloud.com/document/product/647/59649).

The main difference is the parameters **scene** and **role** set when calling [trtc.enterRoom()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom). Refer to the following sample code:

```
await trtc.enterRoom({     scene: TRTC.TYPE.SCENE_LIVE,    role: TRTC.TYPE.ROLE_ANCHOR,    sdkAppId,     userId,     userSig,    roomId});
```

## Audience Side

### Enter the Room as an Audience

Set the role parameter to TRTC.TYPE.ROLE_AUDIENCE.

```
await trtc.enterRoom({     scene: TRTC.TYPE.SCENE_LIVE,    role: TRTC.TYPE.ROLE_AUDIENCE,    sdkAppId,     userId,     userSig,    roomId});
```

### Play Remote Audio

By default, the SDK will automatically play remote audio, and you do not need to call any API to play remote audio.

> **Autoplay Policy Restriction**If the user has not interacted with the page before entering the room, automatic audio playback may fail due to [Autoplay Policy Restriction](https://developer.chrome.com/blog/autoplay). You need to refer to the [Handle Autoplay Restriction](https://www.tencentcloud.com/document/product/647/59666) for processing.

If you do not want the SDK to automatically play audio, you can try this:

```
autoReceiveAudio = false
```

### Play Remote Video

1. Listen for the [TRTC.EVENT.REMOTE_VIDEO_AVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_VIDEO_AVAILABLE) event before entering the room to receive all remote user video publishing events.
2. Call [trtc.startRemoteVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo) to play the remote video stream when you receive the event.

```
trtc.on(TRTC.EVENT.REMOTE_VIDEO_AVAILABLE, ({ userId, streamType }) => {  // To play the video image, you need to place an HTMLElement in the DOM,   // which can be a div tag, assuming its id is `${userId}_${streamType}`  const view = `${userId}_${streamType}`;  trtc.startRemoteVideo({ userId, streamType, view });});
```

## How to Switch Role

The audience role does not have the permission to publish stream, so if the audience wants to make a call with the anchor, they need to switch to the anchor role by using [trtc.switchRole](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#switchRole) and then publish streams.

```
// Switch to the anchorawait trtc.switchRole(TRTC.TYPE.ROLE_ANCHOR);// Turn on mic and camera, then the other anchor in the room will able to receive your audio and video.await trtc.startLocalAudio();await trtc.startLocalVideo();// Switch back to the audience when the calling is endedawait trtc.switchRole(TRTC.TYPE.ROLE_AUDIENCE);
```


---
*Source: [https://trtc.io/document/59650](https://trtc.io/document/59650)*
