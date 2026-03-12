# 9.Sharing Computer Audio

## Pain Points and Solutions

It is often necessary to share system audio in scenarios such as screen sharing, but the sound cards of Mac computers do not allow the capturing of system audio when the application is packaged by Electron, making it impossible to share system audio on Mac computers. To solve this problem, TRTC has introduced a feature that records system audio on Mac computers. See below for details on how to enable the feature.

### Step 1. Start capturing system audio

```
import TRTCCloud, { TRTCAudioQuality } from 'trtc-electron-sdk';const rtcCloud = new TRTCCloud();function onSystemAudioLoopbackError(errCode) {  if (errCode === 0) {    console.log('Started successfully');  }  if (errCode === -1330) {    console.log('Failed to enable system sound recording; for example, the audio driver plugin was unavailable');  }  if (errCode === -1331) {    console.log('No permission to install the audio driver plugin');  }  if (errCode === -1332) {    console.log('Failed to install the audio driver plugin');  }}trtcCloud.on('onSystemAudioLoopbackError', onSystemAudioLoopbackError);trtcCloud.startLocalAudio(TRTCAudioQuality.TRTCAudioQualityDefault);trtcCloud.startSystemAudioLoopback();
```

> **notice** When you call `startSystemAudioLoopback` for the first time, the SDK will request root access. After being granted root access, the SDK will start installing the virtual sound card plugin to the computer automatically.

### Step 2. Stop capturing system audio

```
trtcCloud.stopSystemAudioLoopback();
```

### Step 3. Set the volume of system audio capturing

```
trtcCloud.setSystemAudioLoopbackVolume(60);
```

## Summary

TRTC records system audio on Mac computers using the virtual sound card plugin `TRTCAudioPlugin.driver`. For the plugin to work, you need to copy it to the system directory `/Library/Audio/Plug-Ins/HAL` and restart the audio service. You can check whether the plug is installed successfully using the Audio MIDI Setup app, which can be found in the `Other` folder of Launchpad. The presence of a device named "TRTC Audio Device" in the device list of the app indicates that the plugin is installed successfully.


---
*Source: [https://trtc.io/document/47641](https://trtc.io/document/47641)*
