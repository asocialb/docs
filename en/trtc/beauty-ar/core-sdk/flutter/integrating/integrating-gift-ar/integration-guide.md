# Integration Guide

## Preparing the Environment

- Supports Flutter 3.16.0 or later.
- Android development:
  - Android Studio 3.5 or later.
  - Android SDK API Level 19 or higher.
  - Android 4.4 or higher, supports mobile devices with armeabi-v7a and arm-v8a architecture.
- iOS development:
  - Xcode 11.0 or later.
  - iPhone or iPad with iOS 9.0 or later.
  - The project has a configured valid developer signature.

## SDK Download

The address of the Tencent Gift AR Flutter project is [EffectPlayer Flutter](https://github.com/Tencent-RTC/EffectPlayer_Flutter).

## Quick Integration

### Adding Dependencies in pubspec.yaml

1. Integrate the latest version of EffectPlayer_Player, which is also integrated by default. Add the following configuration in `pubspec.yaml`:

```
  flutter_effect_player:    git:      url: https://github.com/Tencent-RTC/EffectPlayer_Flutter.git
```

If necessary, you can specify the tag of the ref dependency to use the specified version, as shown below:

```
flutter_effect_player:  git:    url: https://github.com/Tencent-RTC/EffectPlayer_Flutter    ref: release_example_tag
```

For more archived tags, see [release list](https://github.com/Tencent-RTC/EffectPlayer_Flutter/releases).

2. After integration, you can get the Flutter dependency through the built-in UI of the code editor or directly use the following commands:

```
flutter pub get
```

3. During use, the following command can be used to update the existing Flutter dependency:

```
flutter pub upgrade
```

## Adding Native End Configuration

### Android End Configuration

#### Encrypting Video Playback Configuration

If you check the **Anim Encrypt** option when converting animations using TepTools, the output animation will be encrypted. At this point, during playback with the effect player, if your application's targetSDKVersion is at least 28, configure as follows separately:

1. Create an xml file at res/xml/network_security_config.xml and set the network security configuration:

```
  <?xml version="1.0" encoding="utf-8"?> <network-security-config>    <domain-config cleartextTrafficPermitted="true">        <domain includeSubdomains="true">localhost</domain>        <domain includeSubdomains="true">127.0.0.1</domain>    </domain-config> </network-security-config>
```

2. Add the following properties to the application tag in the AndroidManifest.xml file:

```
  <?xml version="1.0" encoding="utf-8"?> <manifest ... >    <application android:networkSecurityConfig="@xml/network_security_config"                   ... >     ...    </application></manifest>
```

### iOS End Configuration

> **Note:****Note: iOS currently does not support simulator operation and debugging. It is advisable to perform development and debugging on a real device.**

#### Encrypting Video Playback Configuration

If you check the **Anim Encrypt** option when converting animations using TepTools, the output animation will be encrypted. At this point, during playback with the effect player, configure as follows separately by adding the following configuration to iOS's `Info.plist`:

```
<key>NSAppTransportSecurity</key><dict>    <key>NSAllowsArbitraryLoads</key>    <true/></dict>
```


---
*Source: [https://trtc.io/document/73975](https://trtc.io/document/73975)*
