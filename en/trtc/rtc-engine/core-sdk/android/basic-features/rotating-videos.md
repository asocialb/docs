# Rotating Videos

## Overview

Mobile live streaming uses mainly the portrait mode, but TRTC supports both the landscape and portrait modes, making it necessary to implement different page orientation logics. This document introduces you to the following:

- How to implement the portrait mode, for example, for video calls like those on WeChat
- How to implement the landscape mode, for example, for group communication applications such as Zoom
- How to customize settings for the rotation and rendering mode of the local image and remote images.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6f20876d3a7b11ed8e47525400463ef7.jpeg)

## Supported Platforms

| iOS | Android | macOS | Windows | Electron | Web |
| --- | --- | --- | --- | --- | --- |
| â | â | â | â | â | Ã |

## Portrait Mode

To deliver an experience similar to that of WeChat video calls, you need to do two things.

### 1. Set the orientation of your app to portrait.

iOS

Android

Set the page orientation in Xcode >

**General**

>

**Deployment Info**

>

**Device Orientation**

.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6ef3d0163a7b11ed90fd525400c56988.png)

Alternatively, use the `supportedInterfaceOrientationsForWindow` method in `Appdelegate`.

```
- (UIInterfaceOrientationMask)application:(UIApplication *)application     supportedInterfaceOrientationsForWindow:(UIWindow *)window {    return  UIInterfaceOrientationMaskPortrait ;}
```

> **explain** This [CSDN article](https://blog.csdn.net/DreamcoffeeZS/article/details/79037207) offers a detailed guide on page orientation and adaptation on iOS for developers.

Set the `screenOrientation` attribute of the activity element to `portrait`:

```
<activity android:name=".trtc.TRTCMainActivity"  android:launchMode="singleTask" android:windowSoftInputMode="adjustPan"          android:screenOrientation="portrait" />
```

### 2. Set the orientation of the SDK to portrait.

iOS

Android

```
TRTCVideoEncParam* encParam = [TRTCVideoEncParam new];encParam.videoResolution = TRTCVideoResolution_640_360;encParam.videoBitrate = 600;encParam.videoFps = 15;encParam.resMode = TRTCVideoResolutionModePortrait; // Set the resolution mode to portrait.[trtc setVideoEncoderParam: encParam];
```

```
TRTCCloudDef.TRTCVideoEncParam encParam = new TRTCCloudDef.TRTCVideoEncParam();encParam.videoResolution = TRTCCloudDef.TRTC_VIDEO_RESOLUTION_640_360;encParam.videoBitrate = 600;encParam.videoFps = 15;encParam.videoResolutionMode = TRTCCloudDef.TRTC_VIDEO_RESOLUTION_MODE_PORTRAIT; //Set the resolution mode to portrait.trtc.setVideoEncoderParam(encParam);
```

## Landscape Mode

The steps to implement the landscape mode for your app are similar to the steps of implementing the portrait mode, except that different values are used for the parameters in step 1 and step 2.
In particular, regarding the value of `resMode` in `TRTCVideoEncParam` in [step 2](#step2),

- on iOS, set it to `TRTCVideoResolutionModeLandscape`.
- on Android, set it to `TRTC_VIDEO_RESOLUTION_MODE_LANDSCAPE`.

## Custom Settings

The TRTC SDK provides different APIs for the setting of the rotation and rendering mode of the local image and remote images.

| API | Description | Remarks |
| --- | --- | --- |
| setLocalViewRotation | Set the clockwise rotation of the local image preview | Rotate 90, 180, or 270 degrees clockwise |
| setLocalViewFillMode | Set the rendering mode of the local image preview | Crop the image or fill the blank space with black bars |
| setRemoteViewRotation | Set the clockwise rotation of remote video images | Rotate 90, 180, or 270 degrees clockwise |
| setRemoteViewFillMode | Set the rendering mode of remote video images | Crop the image or fill the blank space with black bars |
| setVideoEncoderRotation | Set the clockwise rotation of encoded images | Rotate 90, 180, or 270 degrees clockwise |

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6f0f10383a7b11ed90fd525400c56988.jpeg)

## GSensorMode

For adaptation during video recording and CDN live streaming, the TRTC SDK provides a simple gravity-sensing adaptation feature, which you can enable using the `setGSensorMode` API of `TRTCCloud`.

The feature supports 90-degrees, 180-degrees and 270-degrees adaptive rotation. This means that when a user's phone is turned, the orientation of the user's image seen by remote users remains the same. Since the feature is achieved through encoder-based rotation adjustment, adaptive rotation is also possible for recorded videos and videos played via HTML5 players.

> **notice** Another way to achieve adaptive rotation is by embedding the gravity direction of a video in the information of each video frame, and adjusting the rotation degree of the video at the viewer end. This scheme requires the introduction of additional transcoding resources to adjust the orientation of recorded videos as expected and is therefore not recommended.


---
*Source: [https://trtc.io/document/35154](https://trtc.io/document/35154)*
