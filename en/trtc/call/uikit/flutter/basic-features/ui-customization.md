# UI Customization

This article will introduce how to customize the user interface of TUICallKit. We provide two solutions for you to choose: **interface fine-tuning solution** and**self-implementation UI**solution.

Note: The page customization solution needs to use the [tencent_calls_uikit](https://pub.dev/packages/tencent_calls_uikit) plugin version 1.8.0 or later.

## Scheme 1. Slight UI Adjustment

You can download the latest version of the [tencent_calls_uikit](https://pub.dev/packages/tencent_calls_uikit/versions) plugin locally, and then use the local dependency method to access the plugin in your project. The local dependency method is as follows:

Under the **dependencies** node in the project **pubspec.yaml**file, add the **tencent_calls_uikit** plugin dependency, as shown below:

```
dependencies:    tencent_calls_uikit:        path: your file path
```

### replace icon

You can directly replace the icons under the **assets\\images**folder to ensure that the color tone of the icons in the entire app is consistent. Please keep the name of the icon file unchanged when replacing.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/95eccefd372811eeb231525400c56988.png)

### replace ringtone

You can replace the three audio files in the **assets\\audios**folder to achieve the purpose of replacing the ringtone:

| Name | Purpose |
| --- | --- |
| phone_dialing.mp3 | The sound of making a call |
| phone_hangup.mp3 | The sound of being hung up |
| phone_ringing.mp3 | The ringtone for incoming calls |

### Replacing text

You can modify the string content in the video call interface by modifying the strings in the **strings.g.dart** file in the **lib\\src\\i18n** directory.

## Scheme 2. Custom UI Implementation

The entire call feature of TUICallKit is implemented based on the UI-less component TUICallEngine. You can directly use the TUICallEngine API provided by [tencent_calls_uikit](https://pub.dev/packages/tencent_calls_uikit/versions) to implement your own UI interface fully based on TUICallEngine.

### TUICallEngine

[TUICallEngine](https://www.tencentcloud.com/document/product/647/54907) is the underlying API of the entire call component, mainly providing key APIs for one-to-one audio and video calls and group calls, including initiation, answer, reject, end, as well as device operation.

### TUICallObserver

[TUICallObserver](https://www.tencentcloud.com/document/product/647/54908) is the callback event class for TUICallEngine. You can receive callback events of interest through this observer.


---
*Source: [https://trtc.io/document/56562](https://trtc.io/document/56562)*
