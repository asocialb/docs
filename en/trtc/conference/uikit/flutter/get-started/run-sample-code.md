# Run Sample Code

This document mainly introduces how to quickly run through the **Conference (TUIRoomKit) sample project** and experience a high-quality multi-person video conference. By following this document, you can run through the demo within 10 minutes and ultimately experience a multi-person video conference feature with a complete UI interface.

| **Conference creation page** | **Conference main page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc31096124a811efa45a5254008fe934.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2d6409c24a811ef94525254005f7176.png) |

## Prerequisites

| Platform | Version |
| --- | --- |
| Flutter | 3.22.0 or later. |
| Android | Android 4.1 (SDK API level 16) or later (Android 5.0 (SDK API level 21) or later is recommended). Android Studio 3.5 or later (Gradle 3.5.4 or later). Android 4.1 or later mobile devices. |
| iOS | iOS 12.0 or later. |

## Download the Demo

1. Download the [TUIRoomKit Demo](https://github.com/Tencent-RTC/TUIRoomKit/) source code from GitHub, or directly execute the following command in the command line:

```
  git clone https://github.com/Tencent-RTC/TUIRoomKit.git
```

2. Open the TUIRoomKit Flutter's example project with Android Studio or VSCode. The following process will take VSCode as an example:![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2514a7153d0211efb958525400f69702.png)

## Configure the Demo

1. [Activate the Conference services](https://www.tencentcloud.com/document/product/647/59973#), to obtain the **SDKAppID** and **SDKSecretKey**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7c2ebd1167411efb366525400762795.png)

2. Open the project and find the `example/lib/debug/generate_test_user_sig.dart` file within the project. Enter the **SDKAppID** and **SDKSecretKey** obtained from Back into it:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7cd6bb2167411efb366525400762795.png)

## Running the Demo

1. Open `example/lib/main.dart` with VSCode, and click the device connection button at the bottom right. Choose the device you wish to run from the pop-up box at the top. After selecting, click the run button at the top right to run the TUIRoomKit Flutter Demo on the device.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7bff987167411ef9c015254002977b6.png)

2. You can also run the following command in the example directory to run it on your device.

```
flutter run
```

| **APP main page** | **Conference creation page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e175e90c591f11efb927525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b9b26e6124aa11ef812f5254002a8f58.png) |

## Create your first conference

Click on the **Create Room** button to create your first meeting room. The room types are **On-stage Speaking Room** and **Free Speech Room**.

- **Free Speech Room**: Regular users can freely speak and have the liberty to turn their microphones and cameras on or off.
- **On-stage Speaking Room**: Only users on stage can freely turn their microphones and cameras on or off. Regular audience members can apply to become stage users by raising their hand.

| **Free speech room member management panel** | **On-stage speaking room member list panel** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b9d1089924aa11ef9dd5525400441de3.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b97b203b24aa11ef8b7b52540096e81f.jpeg) |

## Join conference

After clicking **Join Room,** participants can join the meeting created by the host by filling in the corresponding `RoomId`.

| **Join conference page** | **Conference main page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b9a348ec24aa11ef8b7b52540096e81f.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b9b1732024aa11ef9aab5254004556a0.png) |


---
*Source: [https://trtc.io/document/60445](https://trtc.io/document/60445)*
