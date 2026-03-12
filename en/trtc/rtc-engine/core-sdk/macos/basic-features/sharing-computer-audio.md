# Sharing Computer Audio

## Pain Point and Solution

It is often necessary to share system audio in scenarios such as screen sharing, but the sound cards of Mac computers do not allow the capturing of system audio, making it impossible to share system audio on Mac computers. To solve this problem, TRTC has introduced a feature that records system audio on Mac computers. See below for details on how to enable the feature.

## Directions

### Step 1. Integrate the TRTCPrivilegedTask library

Integration via CocoaPods

Manual integration

1. Open the `Podfile` file in the root directory of your project and add the following content:

```
platform :osx, '10.10'  target 'Your Target' do    pod 'TRTCPrivilegedTask', :podspec => 'https://pod-1252463788.cos.ap-guangzhou.myqcloud.com/liteavsdkspec/TRTCPrivilegedTask.podspec'end
```

2. Run the `pod install` command to install the **TRTCPrivilegedTask** library.

> **explain:**If you cannot find aÂ PodfileÂ file in the directory, run theÂ pod initÂ command to create one and then add the above content.For how to install CocoaPods, see CocoaPods'Â [official installation document](https://guides.cocoapods.org/using/getting-started.html).

1. Download the [TRTCPrivilegedTask](https://liteavsdk-1252463788.cos.ap-guangzhou.myqcloud.com/TRTCPrivilegedTask/TRTCPrivilegedTask.tar.bz2) library.
2. Decompress the downloaded file, open your Xcode project, and import the file to the project.
3. Select the target to run, select **Build Phases**, expand **Link Binary with Libraries**, click **+**, and add the dependent library `libPrivilegedTask.a`.![libPrivilegedTask.a](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b97b6b3e37f311ed8088525400463ef7.png)

### Step 2. Disable App Sandbox

In the entitlements file of the app, delete

**App Sandbox**

.

![Sandbox](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b97f67cc37f311edb1de525400c56988.png)

### Step 3. Package the virtual sound card plugin

After you

integrate the TRTCPrivilegedTask library

and

disable App Sandbox

, when you use the system audio recording feature for the first time, the SDK will download the virtual sound card plugin from the internet and install it. To accelerate this process, you can package the virtual sound card plugin

`TRTCAudioPlugin.driver`

in the

` PlugIns`

directory of

`TXLiteAVSDK_TRTC_Mac.framework`

to the resources directory of the app's bundle, as shown below.

![Packaging plugin](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b989d33c37f311ed8088525400463ef7.png)

Alternatively, copy the file to the

`PlugIns`

directory of the app's bundle.

![Packaging plugin 2](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b98a4b3d37f311ed8088525400463ef7.png)

### Step 4. Start capturing system audio

```
TRTCCloud *trtcCloud = [TRTCCloud sharedInstance];[_trtc startLocalAudio];[trtcCloud startSystemAudioLoopback];
```

> **notice**After the TRTCPrivilegedTask library is integrated and App Sandbox disabled, when you call `startSystemAudioLoopback` for the first time, the SDK will request root access.After being granted root access, the SDK will start installing the virtual sound card plugin to the computer automatically.

### Step 5. Stop capturing system audio

```
TRTCCloud *trtcCloud = [TRTCCloud sharedInstance];[trtcCloud stopSystemAudioLoopback];
```

### Step 6. Set the volume of system audio capturing

```
TRTCCloud *trtcCloud = [TRTCCloud sharedInstance];[trtcCloud setSystemAudioLoopbackVolume:80];
```

## Summary

- TRTC records system audio on Mac computers using the virtual sound card plugin `TRTCAudioPlugin.driver`. For the plugin to work, you need to copy it to the system directory `/Library/Audio/Plug-Ins/HAL` and restart the audio service. You can check whether the plugin is installed successfully using the Audio MIDI Setup app, which can be found in the `Other` folder of Launchpad. The presence of a device named "TRTC Audio Device" in the device list of the app indicates that the plugin is installed successfully.
- The purpose of [integrating the TRTCPrivilegedTask library](#step1) and [disabling App Sandbox](#step2) is for the SDK to get root access so as to install the virtual sound card plugin; otherwise it cannot automatically install the plugin. However, if a virtual sound card is already installed in the system, you can use the system audio recording feature without integrating the TRTCPrivilegedTask library or disabling App Sandbox.

> **explain** You can also manually install a virtual sound card to enable the feature.Copy `TRTCAudioPlugin.driver` in the `PlugIns` directory of `TXLiteAVSDK_TRTC_Mac.framework` to the system directory `/Library/Audio/Plug-Ins/HAL`.Restart the system audio service.

```
 sudo cp -R TXLiteAVSDK_TRTC_Mac.framework/PlugIns/TRTCAudioPlugin.driver /Library/Audio/Plug-Ins/HAL   sudo kill -9 `ps ax|grep 'coreaudio[a-z]' |awk '{print $1}'`
```

## Notes

- You may be unable to release your app to the Mac App Store after integrating the TRTCPrivilegedTask library.App Sandbox must be disabled for the SDK to get root access and automatically install a virtual sound card. This may cause your app to be rejected by the Mac App Store. For details, see [App Store Review Guidelines](https://developer.apple.com/app-store/review/guidelines/#hardware-compatibility).If you need to release your app to the Mac App Store or want to use the Sandbox feature, consider manually installing a virtual sound card.


---
*Source: [https://trtc.io/document/39694](https://trtc.io/document/39694)*
