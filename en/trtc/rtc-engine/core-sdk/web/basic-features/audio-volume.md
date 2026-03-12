# Audio Volume

This tutorial mainly introduces how to detect the volume.

- Detect the volume of the local microphone and remote users.
- Detect whether the user is speaking after muting microphone.
- Adjust local microphone and remote audio volume.

## Demo

## Dectect Audio Volume

Listen for the [TRTC.EVENT.AUDIO_VOLUME](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.AUDIO_VOLUME) event, and then call [trtc.enableAudioVolumeEvaluation()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enableAudioVolumeEvaluation) to enable the volume event.

```
trtc.on(TRTC.EVENT.AUDIO_VOLUME, event => {    event.result.forEach(({ userId, volume }) => {        // When userId is an empty string, it represents the volume of the local microphone.        const isMe = userId === '';         if (isMe) {            console.log(`my volume: ${volume}`);        } else {            console.log(`user: ${userId} volume: ${volume}`);        }    })});// Enable volume event and trigger the event every 500mstrtc.enableAudioVolumeEvaluation(500);// For performance reasons, when the page switches to the background, // the SDK will not throw volume callback events. If you need to receive volume event// when the page is switched to the background, you can set the second parameter to true.trtc.enableAudioVolumeEvaluation(500, true);// To turn off the volume event, pass in an value less than or equal to 0trtc.enableAudioVolumeEvaluation(-1);
```

## Detect Whether the User is Speaking after Muting Microphone

```
const trtc = TRTC.create();await trtc.startLocalAudio();let isAudioMuted = false;await trtc.updateLocalAudio({ mute: true });isAudioMuted = true;// create a new trtc instance for detecting the volume of microphone.const trtcA = TRTC.create();trtcA.enableAudioVolumeEvaluation();trtcA.on(TRTC.EVENT.AUDIO_VOLUME, event => {  event.result.forEach(item => {      // 1. userId === '' is local volume.      // 2. It is generally believed that when the volume is greater than 10, the user is talking, and you can also customize this threshold.      if (item.userId === '' && item.volume > 10 && isAudioMuted) {        // The user is speaking after microphone muted.      }    })})await trtcA.startLocalAudio();
```

## Adjust Audio Volume

The default local microphone capture volume is 100. You can set the **captureVolume** parameter of [trtc.updateLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalAudio) to adjust it.

```
// Increase the capture volume by setting captureVolume upper than 100.await trtc.updateLocalAudio({ option: { captureVolume: 200 }});// Decrease the capture volume by setting captureVolume below 100.await trtc.updateLocalAudio({ option: { captureVolume: 50 }});await trtc.updateLocalAudio({ option: { captureVolume: 0 }});
```

The default remote audio volume is 100. You can call [trtc.setRemoteAudioVolume()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#setRemoteAudioVolume) to adjust it.

```
// Increase remote audio volumeawait trtc.setRemoteAudioVolume('remote_user_id', 200);// Decrease remote audio volumeawait trtc.setRemoteAudioVolume('remote_user_id', 50);
```


---
*Source: [https://trtc.io/document/59653](https://trtc.io/document/59653)*
