# Integration

This tutorial mainly introduces how to implement a basic audio and video call.

## Install

npm

yarn

```
npm install trtc-sdk-v5 --save
```

```
yarn add trtc-sdk-v5
```

Or download manually:

1. Download [trtc-sdk-v5](https://www.unpkg.com/trtc-sdk-v5@latest/trtc.js?response-content-type=application/octet-stream).
2. Unzip and copy `trtc-sdk-v5` to your project.

## Usage

### Import TRTC SDK

```
import TRTC from 'trtc-sdk-v5';
```

If you download trtc.js manully, you should use the script tag to import TRTC SDK.

```
<script src="/your_path/trtc.js"></script>
```

### Create TRTC Instance

Call [TRTC.create()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.create) to create a [trtc](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html) instance.

```
const trtc = TRTC.create();
```

### Enter the Room

Call [trtc.enterRoom()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom) to enter the room. This method is usually called within the Start Call button's click callback function.

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| sdkAppId | `number` | The sdkAppId of the audio and video application you created in [TRTC Console](https://console.trtc.io/). |
| userId | `string` | User ID specified by you. |
| userSig | `string` | User signature, refer to [UserSig](https://www.tencentcloud.com/document/product/647/35166). |
| roomId | `number` | Room ID specified by you, usually a unique room ID. |

For more detailed parameter descriptions,  please refer to the interface document [trtc.enterRoom()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom).

```
try {  await trtc.enterRoom({ sdkAppId, userId, userSig, roomId: 8888 });  console.log('enter room successfully');} catch (error) {  console.error('failed to enter room ' + error);}
```

### Turn on/off Microphone

Call [trtc.startLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalAudio) to turn on the microphone and publish it to the room.

```
await trtc.startLocalAudio();
```

Call [trtc.stopLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalAudio) to turn off the microphone and unpublish it.

```
await trtc.stopLocalAudio();
```

### Turn on/off Camera

Call [trtc.startLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) to turn on the camera and publish it to the room.

```
// To preview the camera image, you need to place an HTMLElement in the DOM, // which can be a div tag, assuming its id is local-video.const view = 'local-video';await trtc.startLocalVideo({ view });
```

Call [trtc.stopLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalVideo)to turn off the camera and unpublish it.

```
await trtc.stopLocalVideo();
```

### Play Remote Audio

By default, the SDK will automatically play remote audio, so you do not need to call any API to play it manually.

> **Autoplay Policy Restriction**If the user has not interacted with the page before entering the room, the automatic audio playback may fail due to [Autoplay Policy Restriction](https://developer.chrome.com/blog/autoplay). Refer to [Handle Autoplay Restriction](https://www.tencentcloud.com/document/product/647/59666).

The following code snippet shows how to call API to play remote audio when you do not prefer an automatic audio play.

```
autoReceiveAudio = false
```

### Play Remote Video

1. Listen for the [TRTC.EVENT.REMOTE_VIDEO_AVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_VIDEO_AVAILABLE) event before entering the room to receive all remote user video publishing events.
2. Call [trtc.startRemoteVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo) to play the remote video stream when you receive the event.

```
trtc.on(TRTC.EVENT.REMOTE_VIDEO_AVAILABLE, ({ userId, streamType }) => {  // To play the video image, you need to place an HTMLElement in the DOM,   // which can be a div tag, assuming its id is `${userId}_${streamType}`  const view = `${userId}_${streamType}`;  trtc.startRemoteVideo({ userId, streamType, view });});
```

### Exit the Room

Call [trtc.exitRoom()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#exitRoom) to exit the room and end the audio and video call.

```
await trtc.exitRoom(); // After the exit is successful, you can call the trtc.destroy method to // destroy the instance and release related resources in a timely manner // if you do not need to use the trtc instance later. // The destroyed trtc instance cannot be used again and a new instance needs to be created.trtc.destroy();
```

**Handling being kicked out**

In addition to actively exiting the room, users may also be kicked out of the room for the following reasons.

1. **kick**: When two users with the same userId enter the same room, the user who entered first will be kicked out. This is not allowed because it may cause abnormal audio and video calls between the two parties, so you should avoid this happening.
2. **banned**: A user is kicked out of a TRTC room through the server's [RemoveUser](https://trtc.io/document/34268) | [RemoveUserByStrRoomId](https://trtc.io/document/39630) interface. The user will receive a kicked event, and the reason is **banned**.
3. **room-disband**: A TRTC room is dissolved through the server's [DismissRoom](https://trtc.io/document/34269) | [DismissRoomByStrRoomId](https://trtc.io/document/39631) interface. After the room is dissolved, all users in the room will receive a kicked event, and the reason is **room-disband**.

When a user is kicked, the SDK will throw the [KICKED_OUT](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.KICKED_OUT) event.

```
trtc.on(TRTC.EVENT.KICKED_OUT, error => {  console.error(`kicked out, reason:${error.reason}, message:${error.message}`);});
```

## API Overview

- [TRTC](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html) is the main entry for TRTC SDK, providing APIs such as create trtc instance([TRTC.create](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.create)), [TRTC.getCameraList](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.getCameraList), [TRTC.getMicrophoneList](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.getMicrophoneList), [TRTC.isSupported](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.isSupported).
- [trtc](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html) instance, provides the core capability for real-time audio and video calls.
  - Enter room [trtc.enterRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom)
  - Exit room [trtc.exitRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#exitRoom)
  - Turn on/off microphone [trtc.startLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalAudio)/[trtc.stopLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalAudio)
  - Turn on/off camera [trtc.startLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo)/[trtc.stopLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalVideo)
  - Play/stop remote audio [trtc.muteRemoteAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#muteRemoteAudio)
  - Play/stop remote video [trtc.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo)/[trtc.stopRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopRemoteVideo)

## API Lifecycle

## ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3be6fd3e0df811ef849e5254005ac0ca.png)

## Contact Us

If you encounter any problems during the implementation process, please feel free to open an issue on [GitHub issue](https://github.com/LiteAVSDK/TRTC_Web/issues), and we will work on it as soon as possible.


---
*Source: [https://trtc.io/document/59649](https://trtc.io/document/59649)*
