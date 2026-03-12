# Media Device

This tutorial mainly introduces how to

1. [Turn on/off the microphone and camera.](#386adc66-2b5b-4b62-bbd5-d0fc623ce2f7)
2. [Switch microphone, camera and speaker.](#deffd1c4-a821-490a-9465-52300e98a687)
3. [Detect the state of media devices.](#6afad2e3-c584-4105-828b-2c2fe8ab8e08)
4. [Detect whether the user is speaking after muting microphone.](#2acba636-5dc9-4bb4-a8b5-6cb708b33491)
5. [Detect the microphone and camera on/off state of remote user.](#ae9f971c-bca4-4e7c-a227-22027cdd1893)

## Demo

## Turn on/off the Microphone and Camera

There are 3 options to implement this feature. We recommend the [first option](#436632d8-e65d-4ef4-b3cf-63bb807e1a15).

| Options | Software or Hardware | Will capturing lights on | Continue to send mute packets | Able to preview local camera |
| --- | --- | --- | --- | --- |
| Use the Mute Parameter | Software | Yes | Yes | No |
| Use stopLocalVideo() & stopLocalAudio() | Hardware | No | No | No |
| Use the Publish Parameter | Software | Yes | No | Yes |

For remote users, the three plans behave the same:

- After turning off the camera, other users in the room will receive the [TRTC.EVENT.REMOTE_VIDEO_UNAVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_VIDEO_UNAVAILABLE) event.
- After turning on the camera, other users in the room will receive the [TRTC.EVENT.REMOTE_VIDEO_AVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_VIDEO_AVAILABLE) event.
- After turning off the microphone, other users in the room will receive the [TRTC.EVENT.REMOTE_AUDIO_UNAVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_AUDIO_UNAVAILABLE) event.
- After turning on the microphone, other users in the room will receive the [TRTC.EVENT.REMOTE_AUDIO_AVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_AUDIO_AVAILABLE) event.

### Use the Mute Parameter

You can use the **mute** parameter of [trtc.updateLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalVideo) and [trtc.updateLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalAudio) to control the on/off state of camera and microphone after turning on the camera and microphone. In this option, the camera and microphone are muted at the software level. In fact, the device is still in active state, and the physical capturing light of the device is still on.

Physically, since it takes some time for the microphone to start, the user's voice may be missed during this period. Therefore, we **recommend** that you use this option. The advantage of this option is that it will be faster to turn the camera or microphone back on:

```
await trtc.startLocalVideo();// mute the camera// After turning off the camera, the camera preview screen will become black, // and you can display the business side's own UI mask at this time.await trtc.updateLocalVideo({ mute: true });// unmute the cameraawait trtc.updateLocalVideo({ mute: false });
```

```
await trtc.startLocalAudio();// mute the microphoneawait trtc.updateLocalAudio({ mute: true });// unmute the microphoneawait trtc.updateLocalAudio({ mute: false });
```

> **Note:**In addition,  a very low bit rate(about 1kbps) muted packet will be sent after muting microphone or camera.

### Use [stopLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalVideo) & [stopLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalAudio)

You can call [trtc.stopLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalVideo) & [trtc.stopLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalAudio) to turn of camera and microphone.

In this option, the camera and microphone are closed physically, and the physical capturing light of the device will be turned off.

```
// Turn off the cameraawait trtc.stopLocalVideo();// Turn on the camera// 'local-video' is the element id in the DOM used to play the local camera video container.await trtc.startLocalVideo({ view: 'local-video' });
```

```
// Turn off the microphoneawait trtc.stopLocalAudio();// Turn on the microphoneawait trtc.startLocalAudio();
```

### Use the Publish Parameter

You can use the publish parameter of [updateLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalVideo) and [updateLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalAudio) to control whether to publish video and audio stream.

In this option, you control the publish state of audio and video stream at the software level. In fact, the device is still in active state, and the physical capturing light of the device is still on.

```
await trtc.startLocalVideo();// unpublish the stream of camera. await trtc.updateLocalVideo({ publish: false });// publish the stream of camera.await trtc.updateLocalVideo({ publish: true });
```

```
await trtc.startLocalAudio();
// unpublish the stream of microphone
await trtc.updateLocalAudio({ publish: false });
// publish the stream of microphone
await trtc.updateLocalAudio({ publish: true });
```

## Switch the Microphone, Camera and Speaker

### Switch Camera

```
// Open the camera, the default is the first camera in the camera list.await trtc.startLocalVideo();const cameraList = await TRTC.getCameraList();// Switch to the second cameraif (cameraList[1]) {  await trtc.updateLocalVideo({ option: { cameraId: cameraList[1].deviceId }});}// On mobile device.// switch to front camera.await trtc.updateLocalVideo({ option: { useFrontCamera: true }});// switch to rear camera.await trtc.updateLocalVideo({ option: { useFrontCamera: false }});
```

### Switch Microphone

```
// Open the microphone, the default is the first microphone in the microphone list.await trtc.startLocalAudio();const microphoneList = await TRTC.getMicrophoneList();// Switch to the second microphoneif (microphoneList[1]) {  await trtc.updateLocalAudio({ option: { microphoneId: microphoneList[1].deviceId }});}
```

### Switch Speaker

```
// The default speaker is the first speaker in the speaker list.const speakerList = await TRTC.getSpeakerList();if (speakerList[1]) {    await TRTC.setCurrentSpeaker(speakerList[1].deviceId);}
```

## Detect the State of Media Device

### DEVICE_CHANGED Event

You can listen for [DEVICE_CHANGED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.DEVICE_CHANGED) event to detect the behavior of device insertion, device unplugged and device startup.

```
trtc.on(TRTC.EVENT.DEVICE_CHANGED, (event) => {  // Device insertion  if (event.action === 'add') {    // Camera insertion    if (event.type === 'camera') {}  } else if (event.action === 'remove') {    // Device unplugged  } else if (event.action === 'active') {    // Device startup  }  console.log(`${event.type}(${event.device.label}) ${event.action}`);});
```

#### Check If the Device in Used is Unplugged

```
trtc.on(TRTC.EVENT.DEVICE_CHANGED, (event) => {  if (event.action === 'remove') {    if (event.type === 'camera') {      const currentCameraId = trtc.getVideoTrack()?.getSettings()?.deviceId;      if (event.device.deviceId === currentCameraId) {        // The camera in used is unplugged.      }    } else if (event.type === 'microphone') {      const currentMicId = trtc.getAudioTrack()?.getSettings()?.deviceId;      if (event.device.deviceId === currentMicId) {        // The microphone in used is unplugged.      }    }  }});
```

#### Switch to New Device When User Inserts a New device.

```
trtc.on(TRTC.EVENT.DEVICE_CHANGED, (event) => {  if (event.action === 'add') {    if (event.type === 'camera') {      // After inserting the camera, switch to the new camera      trtc.updateLocalVideo({ option: { cameraId: event.device.deviceId }});    }  }});
```

### Recapture Automatically

The SDK will detect the insertion and unplugged behavior of the camera and microphone, and automatically recapture media device at the appropriate time. The specific logic is as follows:

1. If the current streaming camera/microphone is unplugged, the SDK will try to recapture the available media device.
2. If the camera/microphone is unplugged and there is no available media device, the SDK will detect the device insertion behavior. If a new available media device is inserted, the SDK will try to recapture the new inserted media device.
3. If the recapturing fails, an error [TRTC.ERROR_CODE.DEVICE_ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.DEVICE_ERROR) will be thrown, and the extraCode will be 5308 and 5309.

Listen for device capture exception events:

```
trtc.on(TRTC.EVENT.VIDEO_PLAY_STATE_CHANGED, event => {  // Local camera collection exception, at this time the SDK will try to automatically recover the collection, you can guide the user to check whether the camera is normal.  if (event.userId === '' && event.streamType === TRTC.TYPE.STREAM_TYPE_MAIN && (event.reason === 'mute' || event.reason === 'ended')) {}});trtc.on(TRTC.EVENT.AUDIO_PLAY_STATE_CHANGED, event => {  // Local microphone collection exception, at this time the SDK will try to automatically recover the collection, you can guide the user to check whether the microphone is normal.  if (event.userId === '' && (event.reason === 'mute' || event.reason === 'ended')) {}});
```

Listen for SDK recapture failed events:

```
trtc.on(TRTC.EVENT.ERROR, error => {  if (error.code === TRTC.ERROR_CODE.DEVICE_ERROR) {    // Camera recapture failed    if (error.extraCode === 5308) {      // After guiding the user to check the device, call updateLocalVideo and pass in cameraId to recapture.      trtc.updateLocalVideo({ option: { cameraId: '' }});    }    // Microphone recapture failed    if (error.extraCode === 5309) {      // After guiding the user to check the device, call updateLocalAudio and pass in microphoneId to recapture.      trtc.updateLocalAudio({ option: { microphoneId: '' }});    }  }})
```

## Detect Whether the User is Speaking after Muting Microphone

```
const trtc = TRTC.create();await trtc.startLocalAudio();let isAudioMuted = false;await trtc.updateLocalAudio({ mute: true });isAudioMuted = true;// create a new trtc instance for detecting the volume of microphone.const trtcA = TRTC.create();trtcA.enableAudioVolumeEvaluation();trtcA.on(TRTC.EVENT.AUDIO_VOLUME, event => {  event.result.forEach(item => {      // 1. userId === '' is local volume.      // 2. It is generally believed that when the volume is greater than 10, the user is talking, and you can also customize this threshold.      if (item.userId === '' && item.volume > 10 && isAudioMuted) {        // The user is speaking after microphone muted.      }    })})await trtcA.startLocalAudio();
```

## Detect the Microphone and Camera on/off State of Remote User

This is often used to confirm how to display the microphone on/off stat of a remote user.

Suppose there are two users A and B.

1. After A enters the room successfully, if there is another anchor B in the room, A will receive [REMOTE_USER_ENTER](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_USER_ENTER) event.
2. At this point, A can assume that B has not turned on the microphone or camera by default.
3. If A receives a [REMOTE_AUDIO_AVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_AUDIO_AVAILABLE) or [REMOTE_VIDEO_AVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_VIDEO_AVAILABLE) event from B, it means B has turned on the microphone or camera.
4. If A receives a [REMOTE_AUDIO_UNAVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.REMOTE_AUDIO_UNAVAILABLE) or [REMOTE_VIDEO_UNAVAILABLE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#. REMOTE_VIDEO_UNAVAILABLE) event from B, it means B has turned off the microphone or camera.


---
*Source: [https://trtc.io/document/59652](https://trtc.io/document/59652)*
