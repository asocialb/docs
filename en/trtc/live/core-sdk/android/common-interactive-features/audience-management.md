# Audience Management

This document mainly introduces how to use the `RTC Room Engine` SDK to implement audio settings features.

## Prerequisites

Before using the audio settings features provided by the `RTC Room Engine` SDK, you need to complete the [SDK login](https://www.tencentcloud.com/document/product/647/66960#) and ensure that you are in a live room.

## User Guide

### Turning On/Off the Local Microphone

iOS

Android

You can turn on or off your local microphone by calling the `openLocalMicrophone` and `closeLocalMicrophone` APIs respectively.

When calling `openLocalMicrophone` to turn on the microphone, you need to pass a parameter of type `TUIAudioQuality` named `quality` to set the audio encoding quality. `TUIAudioQuality` includes the following types, which you can choose according to your business needs:

| Enumeration value types | Meaning |
| --- | --- |
| speech | Voice mode. Mono; audio bitrate: 18kbps; suitable for voice call scenarios. |
| default | Default mode. Mono; audio bitrate: 50kbps; the default audio quality of the SDK, recommended if there are no special requirements. |
| music | Music mode. Stereo + full band; audio bitrate: 128kbps; suitable for scenarios requiring high-fidelity music transmission, such as online karaoke and music live streaming. |

You can turn on or off your local microphone by calling the `openLocalMicrophone` and `closeLocalMicrophone` APIs respectively.

When calling `openLocalMicrophone` to turn on the microphone, you need to pass a parameter of type `AudioQuality` named `quality` to set the audio encoding quality. `AudioQuality` includes the following types, which you can choose according to your business needs:

| Enumeration value types | Meaning |
| --- | --- |
| SPEECH | Voice mode. Mono; audio bitrate: 18kbps; suitable for voice call scenarios. |
| DEFAULT | Default mode. Mono; audio bitrate: 50kbps; the default audio quality of the SDK, recommended if there are no special requirements. |
| MUSIC | Music mode. Stereo + full band; audio bitrate: 128kbps; suitable for scenarios requiring high-fidelity music transmission, such as online karaoke and music live streaming. |

Below is an example of turning on and off the local microphone in default mode.

iOS

Android

```
import RTCRoomEnginelet roomEngine = TUIRoomEngine.sharedInstance()// Turn on the local microphoneroomEngine.openLocalMicrophone(.default) {    // Successfully turned on the mic} onError: { code, message in    // Failed to turn on the mic}// Turn off the local microphoneroomEngine.closeLocalMicrophone()
```

```
TUIRoomEngine roomEngine = TUIRoomEngine.sharedInstance();// Turn on the local microphoneroomEngine.openLocalMicrophone(TUIRoomDefine.AudioQuality.DEFAULT, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Successfully turned on the mic    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed to turn on the mic    }});// Turn off the local microphoneroomEngine.closeLocalMicrophone();
```

### Updating Local Audio Encoding Quality

iOS

Android

When updating local audio encoding quality, the parameter type `TUIAudioQuality` is the same as mentioned above. Below is an example of using the default mode to call the `updateAudioQuality` API to update the local audio encoding quality:

```
import RTCRoomEnginelet audioQuality: TUIAudioQuality = .defaultTUIRoomEngine.sharedInstance().updateAudioQuality(audioQuality)
```

When updating local audio encoding quality, the parameter type `AudioQuality` is the same as mentioned above. Below is an example of using the default mode to call the `updateAudioQuality` API to update the local audio encoding quality:

```
TUIRoomDefine.AudioQuality audioQuality = TUIRoomDefine.AudioQuality.DEFAULT;TUIRoomEngine.sharedInstance().updateAudioQuality(audioQuality);
```

### Pausing/Resuming Local Audio Stream Publishing

When you are in a live room, you may need to pause/resume publishing your local audio stream. You can achieve this by calling the following API:

iOS

Android

```
import RTCRoomEnginelet roomEngine = TUIRoomEngine.sharedInstance()// Pause publishing local audio streamsroomEngine.muteLocalAudio()// Resume publishing local audio streamsroomEngine.unmuteLocalAudio() {    // Resume publishing successful} onError: { code, message in    // Resume publishing failed}
```

```
TUIRoomEngine roomEngine = TUIRoomEngine.sharedInstance();// Pause publishing local audio streamsroomEngine.muteLocalAudio();// Resume publishing local audio streamsroomEngine.unmuteLocalAudio(new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Resume publishing successful    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Resume publishing failed    }});
```

> **Note:**In the room, if you have turned on your microphone, after calling the above API to pause/resume publishing the local audio stream, the SDK will notify the users in the room through the `TUIRoomObserver` callback [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/64184#57eafbcdec43b9cacef68034b3087e45).


---
*Source: [https://trtc.io/document/67665](https://trtc.io/document/67665)*
