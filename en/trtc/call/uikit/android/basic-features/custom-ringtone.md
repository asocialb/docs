# Custom Ringtone

This article introduces how to replace the incoming call ringtone in TUICallKit. The incoming call ringtone includes **application ringtone** and **offline push ringtone**.

## Setting the application ringtone

There are two methods to set the application ringtone:

#### 1. Replace Audio File

If you integrate the TUICallKit component via source code dependency, you can replace the audio files in the [tuicallkit-kt/src/main/res/raw](https://github.com/Tencent-RTC/TUICallKit/tree/main/Android) folder to customize the ringtone.

| File Name | Use |
| --- | --- |
| phone_dialing.mp3 | Ringtone when initiating a call |
| phone_ringing.mp3 | Ringtone when receiving a call |

#### 2. Call setCallingBell Interface

You can also customize the incoming call ringtone through the [setCallingBell](https://www.tencentcloud.com/document/product/647/51005#setcallingbell) interface.

Kotlin

Java

```
TUICallKit.createInstance(context).setCallingBell(filePath)
```

```
TUICallKit.createInstance(context).setCallingBell(filePath);
```

## Set Mute Mode

If you do not need the phone to ring, you can enable the mute mode using the [enableMuteMode](https://www.tencentcloud.com/document/product/647/51005#enablemutemode) interface.

Kotlin

Java

```
TUICallKit.createInstance(context).enableMuteMode(true)
```

```
TUICallKit.createInstance(context).enableMuteMode(true);
```

## Set Offline Push Ringtone

For Offline Push Ringtone Settings, please refer to: [FCM Offline Push customizes incoming call ringtone](https://www.tencentcloud.com/document/product/647/50999#909f9f70-6480-405b-86b9-6c18c0c695e6).


---
*Source: [https://trtc.io/document/59845](https://trtc.io/document/59845)*
