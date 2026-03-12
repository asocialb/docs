# Detect Capabilities

To ensure that users can have a good experience with the TRTC SDK, we recommend you test the user's media device and network quality the user enters a TRTC room.

## Supported Platforms

Refer to [Supported Platforms](https://www.tencentcloud.com/document/product/647/59733).

## Detect Browser Capabilities

Before entering room, we recommend you use the [TRTC.isSupported](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.isSupported) API to check whether the SDK supports the current browser first, and if not, please guide the user to use a supported browser(**Chrome 56+, Edge 80+, Firefox 56+, Safari 11+**).

```
TRTC.isSupported().then(checkResult => {  // Not supported, guide the user to use a supported browser(Chrome 56+, Edge 80+, Firefox 56+, Safari 11+).  if (!checkResult.result) {}  // Not support to publish video  if (!checkResult.detail.isH264EncodeSupported) {}  // Not support to subscribe video  if (!checkResult.detail.isH264DecodeSupported) {}});
```

If the check result returned from **TRTC.isSupported** is **false**, the reason may be:

1. The web page uses the http protocol. Browsers do not allow http protocol sites to capture cameras and microphones, you need to deploy your page using the https protocol.
2. Firefox browser needs to load H264 codec dynamically after installation, so the detection result will be false for a short period of time, please wait and try again or guide to use other browsers.

## Test Media Device By Plugin

The device detector plugin is used to test the user's media device(camera, microphone, speaker) and network which is recommended to be used before the user enters the room.

> **Note:**Support TRTC Web SDK version â¥ v5.8.0The z-index of this device detection plugin is set to 9999, and you need to ensure your z-index level is lower than 9999.

### Usage

```
import { DeviceDetector } from 'trtc-sdk-v5/plugins/device-detector';
const trtc = TRTC.create({ plugins: [DeviceDetector] });

// 1. Test Media Device Only
const result = await trtc.startPlugin('DeviceDetector');

// 2. Test Media Device & Network Quality
const options = { 
    networkDetect: { sdkAppId, userId, userSig }
}
const resultWithNetwork = await trtc.startPlugin('DeviceDetector', options);
```

### API Description

#### trtc.startPlugin('DeviceDetector', options)

##### options.networkDetect(optional)

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| sdkAppId | `number` | required | Your sdkAppId |
| userId | `string` | required | The userId for testing uplink network quality. It should be different from downlinkUserId. |
| userSig | `string` | required | The [UserSig](https://trtc.io/document/35166) of the userId. |
| downlinkUserId | `string` | optional | The userId for testing downlink network quality. It should be different from userId.Fill in downlinkUserId and downlinkUserSig will perform a downlink network test. |
| downlinkUserSig | `string` | optional | The [UserSig](https://trtc.io/document/35166) of the downlinkUserId. |
| roomId | `number` | optional | Optional. The default value is 8080. The value must be an integer of [1, 4294967294]. |

##### Result of the startPlugin

> **Note:**If the user clicks skip detection button on the test page, return `undefined`.

| Name | Type | Result |
| --- | --- | --- |
| **camera** | `object` | { isSuccess: boolean, device: MediaDeviceInfo} |
| **microphone** | `object` | { isSuccess: boolean, device: MediaDeviceInfo} |
| **speaker** | `object` | { isSuccess: boolean, device: MediaDeviceInfo} |
| **network** | `object` | { isSuccess: boolean, result: { quality: number , rtt: number }}The quality is uplink network quality. When the downlinkUserId and downlinkUserSig passed, the quality is the worse one of the uplink and uplink network quality**Network Quality Values**0: The network quality is unknown, indicating that the current TRTC instance has not established a media connection1:  The network quality is excellent2:  The network quality is good3:  The network quality is average4:  The network quality is poor5:  The network quality is extremely poor6:  The network connection has been disconnected. |

### Plugin Demo

## Test Media Device Manually

### Test Camera

1. Get camera list

Generally, you need to check the camera list first to confirm whether the user has a camera. Then, you can show a camera list to let user to select the camera they want.

```
const cameraList = await TRTC.getCameraList();const hasCameraDevice = cameraList.length > 0;if (!hasCameraDevice) {    // User has not any camera.}
```

2. Capture and play camera

In this step, you need to capture and play camera, and does not need to publish stream.

  - If capturing camera successfully, you need guide user confirm whether user can see the camera view normally.
  - If capturing camera failed, it is usually caused by NotAllowedError or NotReadableError, refer to [DEVICE_ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.DEVICE_ERROR).

```
try {    // Capture and play camera, not need to publish stream    await trtc.startLocalVideo({ view: 'camera-video-view-id', publish: false });} catch(error) {    // Common reasons: NotAllowedError or NotReadableError}
```

3. Switch camera

The SDK will capture the first camera of camera list by default if you did not specify the cameraId when calling trtc.startLocalVideo.

The user may want to switch another camera before entering room if the user has a lot of cameras.

```
// You can get the cameraId from the camera list you got in fisrt step.if (cameraList[1]) {    try {        await trtc.updateLocalVideo({ option: { cameraId: cameraList[1].deviceId } });    } catch(error) {      // Common reasons: NotAllowedError or NotReadableError, same with step 2.    }}
```

4. Stop camera

You need to stop camera when the testing finished.

```
await trtc.stopLocalVideo();
```

### Test Microphone

1. Get mircrophone list

Generally, you need to check the mircrophone list first to confirm whether the user has a mircrophone. Then, you can show a mircrophone list to let user select the mircrophone they want.

```
const microphoneList = await TRTC.getMicrophoneList();const hasMicrophoneDevice = micList.length > 0;if (!hasMicrophoneDevice) {    // User has not any microphone.}
```

2. Capture microphone and get the volume

In this step, you need to capture the microphone, get the audio volume of microphone to show a volume bar,  and do not need to publish stream.

  - If capturing successfully, you need to guide the user to confirm whether the volume bar has changed.
  - If capturing failed, it is usually caused by NotAllowedError or NotReadableError, refer to [DEVICE_ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.DEVICE_ERROR).

```
try {    // Capture microphone    await trtc.startLocalAudio({ publish: false });    trtc.on(TRTC.EVENT.AUDIO_VOLUME, event => {        event.result.forEach(({ userId, volume }) => {            // When userId is an empty string, it represents the volume of the local microphone.            const isMe = userId === '';             if (isMe) {               // show a volume bar based on the value of volume.            }        })    });    trtc.enableAudioVolumeEvaluation(500);} catch(error) {    // Common reasons: NotAllowedError or NotReadableError}
```

3. Switch microphone

The SDK will capture the first microphone of microphone list by default if you did not specify the microphoneId when calling trtc.startLocalAudio.

The user may want to switch to another microphone before entering room if the user has a lot of microphones.

```
// You can get the microphoneId from the microphone list you got in fisrt step.if (microphoneList[1]) {    try {        await trtc.updateLocalAudio({ option: { microphoneId: microphoneList[1].deviceId } });    } catch(error) {      // Common reasons: NotAllowedError or NotReadableError, same with step 2.    }}
```

4. Stop microphone

```
// You need to stop microphone when the testing finished.await trtc.stopLocalAudio();// disable audio-volume eventtrtc.enableAudioVolumeEvaluation(-1);
```

### Test Speaker

1. Get speaker list

```
const speakerList = await TRTC.getSpeakerList();if (speakerList.length === 0) {    // User has not speaker.}
```

2. Play a mp3 media file through the audio element.

You need to guide user to play the mp3 file and confirm whether they can hear the sound from the speaker.

```
<audio id="audio-player" src="xxxxx" controls></audio>
```

3. Switch speaker

You cannot use the [TRTC.setCurrentSpeaker](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.setCurrentSpeaker) to switch speaker, because you play a mp3 by audio element but not TRTC SDK. There is a [HTMLMediaElement.sinkId](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/sinkId) property which can be used to set speaker.

```
const audioElement = document.getElementById('audio-player');if (speakerList[1]) {    audioElement.sinkId = speakerList[1].deviceId;}
```

## Detect Network Quality

Refer to [Detect Network Quality](https://www.tencentcloud.com/document/product/647/59655).

## Online TRTC Capability Detection

You can use the [Online TRTC Capability Detection](https://web.sdk.qcloud.com/trtc/webrtc/demo/detect/index.html) where you are currently using the TRTC SDK to detect the current environment. You can also click the "Generate Report" button to get a report of the current environment for environment detection or troubleshooting.


---
*Source: [https://trtc.io/document/59656](https://trtc.io/document/59656)*
