# Integration Guide

This document mainly introduces how to quickly integrate Tencent Gift AR SDK into your project. Configure according to the following steps to complete the SDK integration work.

## Development Environment Requirement

- Xcode 9.0+.
- iPhone or iPad running iOS 9.0 or later.
- The project has been configured with an effective developer signature.

## Integration Guide

### Manual Integration

1. Download [MediaX_Android_iOS_Latest.zip](https://mediacloud-76607.gzc.vod.tencent-cloud.com/MediaX/download/latest/MediaX_iOS_SDK_Latest.zip). After download completion, decompress it to obtain the SDK library file.
2. Use Gift AR Player. The following frameworks need to be integrated:

**SDK Library**

  - TCMediaX.xcframework
  - TCEffectPlayer.xcframework
  - libtcpag.xcframework
  - YTCommonXMagic.framework

**System Database**

  - libz.tab
  - libc++.tbd
  - AVFoundation.framework

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dce8bb4904a211f08c4452540044a08e.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dce67b3a04a211f09c4a5254001c06ec.png)

3. Set Other linker Flags

Set "-ObjC" in "Other linker Flags" under "Build Settings".

## Integration Via Pods

Currently, the Gift AR SDK supports integration via the Pods channel. Follow these steps to integrate Pods:

```
# Introduce TCMediaXpod 'TCMediaX', :podspec => 'https://mediacloud-76607.gzc.vod.tencent-cloud.com/MediaX/iOS/podspec/release/3.3/3.3.256/TCMediaX.podspec'# Introduce TCEffectPlayerpod 'TCEffectPlayer', :podspec => 'https://mediacloud-76607.gzc.vod.tencent-cloud.com/MediaX/iOS/podspec/release/3.3/3.3.256/TCEffectPlayer.podspec'# Introduce YTCommonXMagic.frameworkpod 'YTCommonXMagic', :podspec => 'https://mediacloud-76607.gzc.vod.tencent-cloud.com/MediaX/iOS/podspec/release/YTCommonXMagic_1.3.1/YTCommonXMagic.podspec'
```

TCEffectPlayer supports being integrated separately or dependently via the integration of Tencent Cloud Player SDK. The difference between them lies in whether to leverage the powerful decoding capability of Tencent Cloud Player.

- If you use the way of independent integration, the decoder type (`TCEffectConfig#vapEngineType`) of the video needs to be set as TCEPCodecTypeAVPlayer integrating with Tencent Cloud Player SDK.
- If you integrate the simplified SDK of Tencent Cloud Player (LiteAVSDK_Player_Mini), the decoder type of the video (TCEffectConfig - vapEngineType) needs to be set as TCEPCodecTypeVODPlayer. The simplified Player SDK does not require an additional Player License application.
- If TCEffect SDK has been integrated into your project, please check whether the Player SDK is included. Meanwhile, check whether you have applied for and configured the Player License, [Application Guide for Player License](https://www.tencentcloud.com/document/product/266/51098?lang=en&pg=).
- See [Tencent Cloud Player Integration Documentation](https://www.tencentcloud.com/document/product/266/49669?lang=en&pg=) for Tencent Cloud Player access documentation.

## Apply for Gift AR SDK License

Using Gift AR SDK requires application for Gift AR Playback License. For detailed application process, please refer to [Console License Application Guide](https://trtc.io/document/60219?platform=android&product=beautyar).

## Common Issues

### How to Resolve YTCommonXMagic Conflict?

If the Beauty Special Effects SDK is integrated into your project, a symbol conflict will occur during integration because both the Beauty Special Effects SDK and the Gift AR SDK use the License authorization library YTCommonXMagic.framework. At this point, when integrating the Effect Player SDK, it is not necessary to integrate the YTCommonXMagic.framework additionally. Sharing one copy of the YTCommonXMagic.framework from the Beauty Special Effects SDK is sufficient.


---
*Source: [https://trtc.io/document/70537](https://trtc.io/document/70537)*
