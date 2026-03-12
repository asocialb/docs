# Upgrade Guide

This documentation is intended to guide participants to upgrade `tencent_trtc_cloud` to the new version `tencent_rtc_sdk`. During the upgrade process, we will detail the necessary procedures, precautions, and potential issues and solutions to ensure a smooth transition to the new version.

## Upgrade Guide

> **Note:**Before performing the upgrade, make sure to back up your current project.`tencent_rtc_sdk` currently does not support `tencent_trtc_cloud`'s `tx_beauty_manager`.`tencent_rtc_sdk` temporarily has no plans to support the web end. If your project involves the web end of `tencent_trtc_cloud`, we do not recommend upgrading.

### 1. Introduce new SDK

Enter the project directory in the console:

```
cd <path to your flutter project>
```

Remove old version `tencent_trtc_cloud`

```
flutter pub remove tencent_trtc_cloud
```

Introduce new version `tencent_rtc_sdk`

```
flutter pub add tencent_rtc_sdk
```

### 2. Replace import package

You can use the replace/batch replace feature provided by the IDE to replace `tencent_trtc_cloud` imports in your current project with `tencent_rtc_sdk`.

> **Note:**If you use the GenerateTestUserSig from our `tencent_trtc_cloud` example to generate your project's userSig, please remove the JsGenerateTestUserSig related logic.

### 3. Replace TRTCCloudDef enumerated values

`tencent_rtc_sdk` removed the TRTCCloudDef class provided in `tencent_trtc_cloud`. Various static variables in the class have been split into numerous Dart enums for your convenience in using some parameters.

For the TRTCCloudDef class used in your existing project, you can refer to the comparison table below to replace static variables with corresponding enums:

| tencent_trtc_cloud | tencent_rtc_sdk |
| --- | --- |
| TRTCCloudDef.TRTC_VIDEO_RESOLUTION_* | TRTCVideoResolution |
| TRTCCloudDef.TRTC_VIDEO_RESOLUTION_MODE_* | TRTCVideoResolutionMode |
| TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_* | TRTCVideoStreamType |
| TRTCCloudDef.TRTC_QUALITY_* | TRTCQuality |
| TRTCCloudDef.TRTC_VIDEO_RENDER_MODE_* | TRTCVideoFillMode |
| TRTCCloudDef.TRTC_VIDEO_ROTATION_* | TRTCVideoRotation |
| TRTCCloudDef.TRTC_BEAUTY_STYLE_* | TRTCBeautyStyle |
| TRTCCloudDef.TRTC_VIDEO_PIXEL_FORMAT_* | TRTCVideoPixelFormat |
| TRTCCloudDef.TRTC_VIDEO_MIRROR_TYPE_* | TRTCVideoMirrorType |
| TRTCCloudDef.TRTC_APP_SCENE_* | TRTCAppScene |
| TRTCCloudDef.TRTCRole* | TRTCRoleType |
| TRTCCloudDef.VIDEO_QOS_CONTROL_* | TRTCQosControlMode |
| TRTCCloudDef.TRTC_VIDEO_QOS_PREFERENCE_* | TRTCVideoQosPreference |
| TRTCCloudDef.TRTC_AUDIO_QUALITY_* | TRTCAudioQuality |
| TRTCCloudDef.TRTC_AUDIO_ROUTE_* | TXAudioRoute(speakerPhone & earpiece) |
| TRTCCloudDef.TRTC_REVERB_TYPE_ | TXVoiceReverbType |
| TRTCCloudDef.TRTC_VOICE_CHANGER_TYPE_* | TXVoiceChangerType |
| TRTCCloudDef.TRTC_AUDIO_FRAME_FORMAT_* | TRTCAudioFrameFormat |
| TRTCCloudDef.TRTCSystemVolumeType* | **(Not supported)** |
| TRTCCloudDef.TRTC_DEBUG_VIEW_LEVEL_* | **(Not supported)** |
| TRTCCloudDef.TRTC_LOG_LEVEL_* | TRTCLogLevel |
| TRTCCloudDef.TRTC_GSENSOR_MODE_* | TRTCGSensorMode |
| TRTCCloudDef.TRTC_TranscodingConfigMode_* | **(Deprecated)** |
| TRTCCloudDef.TRTC_VideoView_* | **(Not supported)** |
| TRTCCloudDef.TXMediaDeviceType* | TXMediaDeviceType |
| TRTCCloudDef.TRTCRecordType* | TRTCLocalRecordType |

### 4. Modify Callback Usage

In `tencent_trtc_cloud`, callbacks need to be captured by users using switch or if statements, and the JSON strings need to be manually parsed to obtain the relevant data. This usage method may cause inconvenience to users. Therefore, we optimized the callback mechanism in `tencent_rtc_sdk` to improve the user access experience, making it more convenient and efficient.

#### Example (TRTCCloudListener):

In the new callback mechanism, `registerListener` no longer requires a function as a parameter, but a TRTCCloudListener object. You can selectively assign values to the required callback functions when initializing this object:

```
 TRTCCloudListener speedTestListener = TRTCCloudListener(  onSpeedTestResult: (result) {    // TODO  });
```

### 5. Invoke new method

In this upgrade, we have removed some interfaces marked as deprecated by native TRTC and optimized the calling methods of some interfaces.

You can find all the interfaces we currently support in the [API overview](https://www.tencentcloud.com/document/product/647/39169#).

> **Note:**Except for the TRTCCloud.sharedInstance() interface, all interfaces in `tencent_rtc_sdk` are synchronous calls.

### 6. Platform Configuration

Please configure as follows in your project's `android/app/build.gradle`:

```
android {  ...  packagingOptions {    pickFirst 'lib/**/libliteavsdk.so'  }  ...}
```

> **Note:**`tencent_rtc_sdk` uses FFI to call most of the TRTC interfaces, so it has certain requirements for your Android environment. Please ensure your Android environment supports CMake 3.13 or higher.


---
*Source: [https://trtc.io/document/66724](https://trtc.io/document/66724)*
