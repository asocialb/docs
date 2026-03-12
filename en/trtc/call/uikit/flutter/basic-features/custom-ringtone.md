# Custom Ringtone

This article explains how to replace the incoming call ringtone of TUICallKit, which is divided into **application ringtone** and **offline push ringtone**.

## Setting application ringtone

There are two ways to set an application ringtone:

### 1. Replace Audio File

If you integrate the TUICallKit component via source code dependency, you can replace the audio files in the **assets\\audios** folder to achieve the purpose of ringtone replacement:

| File Name | Use |
| --- | --- |
| phone_dialing.mp3 | Ringtone when initiating a call |
| phone_ringing.mp3 | Ringtone when receiving a call |

### 2. Call Ringtone Interface

You can also set the incoming call ringtone through the [setCallingBell](https://www.tencentcloud.com/document/product/647/54906#setCallingBell) interface.

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';void setCallingBell() {    TUICallKit.instance.setCallingBell('flie path');}
```

## Set Mute Mode

If you do not need ringing, you can enable the silent mode through [enableMuteMode](https://www.tencentcloud.com/document/product/647/54906#enableMuteMode) interface.

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';void enableMuteMode() {    TUICallKit.instance.enableMuteMode(true);}
```

## Set Offline Push Ringtone

### 1. iOS

VoIP push does not support custom Definition push ringtones. APNs push allows modifying the parameters `call` and `groupcall` in the interface `params` including `TUIOfflinePushInfo.iOSSound` Setting on the `iOS` platform for offline message ringtones.

### 2. Android

> **Note:**The interface supports Huawei, Xiaomi, FCM.

FCM's push ringtone is set as the application ringtone.

For Huawei, Xiaomi, and APNs push ringtone settings, please set the `TUIOfflinePushInfo.iOSSound`'s `iOSSound` and `androidSound` fields when calling Call and GroupCall.


---
*Source: [https://trtc.io/document/59849](https://trtc.io/document/59849)*
