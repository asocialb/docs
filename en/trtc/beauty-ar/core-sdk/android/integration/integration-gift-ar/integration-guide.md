# Integration Guide

This document mainly introduces how to quickly integrate the Tencent Gift AR SDK into your project. Configure according to the following steps, and you can complete the integration work of the SDK.

## Development Environment Requirement

- Android Studio 2.0+.
- Android 4.4 (SDK API 19) or higher system.

## Integrate the SDK

### Manual Integration

1. Download [MediaX_Android_SDK_Latest.zip](https://mediacloud-76607.gzc.vod.tencent-cloud.com/MediaX/download/latest/MediaX_Android_SDK_Latest.zip). After download completion, decompress to obtain the SDK aar file.
2. Decompress the downloaded file. Then, copy the aar file under the SDK directory to the app/libs directory of the project:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9f400390095911f0b3015254001c06ec.png)

3. In the build.gradle in the root directory of the project, add flatDir and specify the local repository path.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9f5d1827095911f0b3015254001c06ec.png)

4. Add dependency on Gift AR SDK. In app/build.gradle, add code to reference the aar package.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9f5e7f0a095911f0a6d15254007c27c5.png)

```
implementation(name: "TCEffectPlayer_x.x.x", ext: "aar")implementation(name: "TCMediaX_x.x.x", ext: "aar")implementation(name: "xmagic-auth_x.x.x", ext: "aar")
```

> **Note:**As shown in the above example, x.x.x is the version number, which must be consistent with the latest SDK version number of the actual download; Moreover, pay attention to that the version numbers of the three aar files must be consistent.

5. In the defaultConfig of app/build.gradle, specify the CPU architecture used by the app (currently supports armeabi-v7a and arm64-v8a).

```
defaultConfig { ndk {     abiFilters "armeabi-v7a", "arm64-v8a" }}
```

### Integration Via Gradle

1. Open the corresponding build.gradle file and add the Gift AR SDK dependency in the dependencies tag:

Retrieve the version of Gift AR SDK released. Please click [MavenCentral](https://central.sonatype.com/artifact/com.tencent.mediacloud/TCEffectPlayer).

```
 dependencies {    // Not recommended to integrate the latest version. Recommend integrating a specified version number.    //implementation "com.tencent.mediacloud:TCEffectPlayer:latest.release"    implementation "com.tencent.mediacloud:TCEffectPlayer:version number"}
```

2. In the defaultConfig of app/build.gradle, specify the CPU architecture used by the app (currently supports armeabi-v7a and arm64-v8a).

```
defaultConfig { ndk {     abiFilters "armeabi-v7a", "arm64-v8a" }}
```

Finally, click **Sync Now** to synchronize the SDK and complete the integration work of the Gift AR SDK.

### Configuring Obfuscation Rules

In the proguard-rules.pro file, add the related classes to the non-obfuscation list:

```
-keep class com.tcmediax.** { *; }
```

### Soft Decoding Capacity Integration Guide

#### Advantage

Due to the severe fragmentation of the Android system, unavoidable hard decoding failure issues may occur on very few mobile phones. Therefore, it is necessary to use the soft decoding capacity to enhance the playback success rate (the success rate can be increased to 99.99%). Therefore, it is highly recommended that you integrate the soft decoding library at the same time to achieve a better special effect playback experience.

#### Integration Steps

##### **Integrated LiteAVSDK_TRTC SDK**

If you have previously integrated Tencent Cloud RT Cube SDK, such as LiteAVSDK_TRTC and LiteAVSDK_Live, in your project, you need to integrate the simplified SDK of Tencent Cloud Player (LiteAVSDK_Player_Mini). Place the corresponding LiteAVSDK_Player_Mini.aar in the libs directory of the project, and then add the corresponding dependency in dependencies.

```
dependencies {   implementation (name:'LiteAVSDK_Player_Mini', ext:'aar')}
```

##### Integrated LiteAVSDK_Professional Related SDKs

If you have previously integrated Tencent Cloud RT Cube SDK, such as LiteAVSDK_Player, LiteAVSDK_Player_Premium, LiteAVSDK_Professional, and LiteAVSDK_UGC, in your project, the software decoding capacity will be automatically supported without additional configuration.

> **Note:**If Tencent Cloud RT-Cube SDK has been integrated in your project, please check whether it contains player SDK and check whether the player License has been applied for and configured.

##### Not Integrated with Tencent Cloud Video View Related SDKs

If Tencent Cloud RT Cube SDK were not integrated in your previous project, it is recommended to integrate the simplified Tencent Cloud Player SDK (LiteAVSDK_Player_Mini). Place the corresponding LiteAVSDK_Player_Mini.aar file under the libs directory of the project, and then add the corresponding dependency in dependencies:

```
dependencies {   implementation (name:'LiteAVSDK_Player_Mini', ext:'aar')}
```

Last step, need to configure so file: Download the so file in the [jniLibs_txffmpeg_so.zip](https://mediacloud-76607.gzc.vod.tencent-cloud.com/MediaX/Res/jniLibs_txffmpeg_so.zip) link to local, then decompress it. Copy the so file in the decompressed jniLibs directory to the app's src/main directory, and configure the corresponding path in app/build.gradle:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9f4fc8ef095911f0b3015254001c06ec.png)

```
sourceSets {    main {        jniLibs.srcDirs = ['src/main/jniLibs']    }}
```

## Applying for License

Using the Gift AR SDK requires applying for the corresponding License. Please see [Console License Application Guide](https://trtc.io/document/60219?platform=android&product=beautyar) for detailed application process.

## Common Issues

### How to Resolve Xmagic Conflicts?

If you have seamlessly integrated the Beauty AR SDK into your project, and since both the Beauty AR SDK and the Gift AR SDK use the License authorization library xmagic-auth, there will be class conflicts (such as: Duplicate class com.tencent.xmagic.auth.Auth) and so file conflicts (such as: libYTCommonXMagic.so conflict) during integration. The processing methods are as follows:

1. **AAR local integration**

If you have integrated it locally via AAR, when integrating the Gift AR SDK at this time, it is not necessary to additionally integrate xmagic-auth.aar into the project. Remove the introduction of the dependency: xmagic-auth-x.x.x.aar, and share one copy of the License authorization library of the Beauty AR SDK in the project.

2. **Gradle integration**

If you are integrated via Gradle, refer to the following code to remove the License authorization library:

```
implementation("com.tencent.mediacloud:TCEffectPlayer:version number") {	exclude group: "com.tencent.mediacloud", module: "TCXMagicAuth"}
```

### How to Handle Encrypted Video Configuration?

If you check the **Anim Encrypt** switch while using the TepTools tool to convert animation, the converted animation will be encrypted. At this point, when playing with the effect player, if your application's targetSDKVersion is greater than or equal to 28, then you need to configure separately as follows:

1. Create a res/xml/network_security_config.xml file in the project and set network security configuration:

```
  <?xml version="1.0" encoding="utf-8"?> <network-security-config>    <domain-config cleartextTrafficPermitted="true">        <domain includeSubdomains="true">localhost</domain>        <domain includeSubdomains="true">127.0.0.1</domain>    </domain-config> </network-security-config>
```

2. Add the following properties to the application tag under the AndroidManifest.xml file:

```
  <?xml version="1.0" encoding="utf-8"?> <manifest ... >    <application android:networkSecurityConfig="@xml/network_security_config"                   ... >     ...    </application></manifest>
```

### Missing Class Error When Packaging

If SDK is introduced, the following error occurs when packaging:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6f7f79aca5c811f0b1565254001c06ec.png)

Add the following configuration in the proguard-rules.pro file of the project

```
-dontwarn com.tencent.rtmp.ITXVodPlayListener$ITXVodAudioFrameDataListener-dontwarn com.tencent.rtmp.TXVodDef$TXVodAudioFrameData-dontwarn com.tencent.xmagic.XmagicApi$XmagicLightGameListener-dontwarn com.tencent.xmagic.XmagicApi
```


---
*Source: [https://trtc.io/document/70531](https://trtc.io/document/70531)*
