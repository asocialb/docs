# Run Sample Code

This document mainly introduces how to quickly run through the **Conference (TUIRoomKit) sample project** and experience a high-quality multi-person video conference. By following this document, you can run through the demo within 10 minutes and ultimately experience a multi-person video conference feature with a complete UI interface.

| **Conference creation page** | **Conference main page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc31096124a811efa45a5254008fe934.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2d6409c24a811ef94525254005f7176.png) |

## Prerequisites

- Minimum compatibility with Android 4.4 (SDK API Level 19), with Android 5.0 (SDK API Level 21) or higher recommended.
- Android Studio 3.5 or above.

## Download the Demo

1. Download the [TUIRoomKit Demo](https://github.com/Tencent-RTC/TUIRoomKit/) source code from GitHub, or directly execute the following command in the command line:

```
  git clone https://github.com/Tencent-RTC/TUIRoomKit.git
```

2. Open the TUIRoomKit Android project via Android Studio:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa2ce7dd167c11efb366525400762795.png)

## Configure the Demo

1. [Activate the Conference services](https://www.tencentcloud.com/document/product/647/59973#), to obtain the **SDKAppID** and **SDKSecretKey**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa1e7c81167c11efb6495254005ac0ca.png)

2. Open the project and find the `Android/debug/src/main/java/com/tencent/liteav/debug/GenerateTestUserSig.java` file. Enter the corresponding **SDKAppID** and **SDKSecretKey** obtained from Back:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa181bad167c11efb8ef5254002fd0a8.png)

## Running the Demo

1. In the top right corner of Android Studio, select the device you want to run the Demo on as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa27cc32167c11ef9c015254002977b6.png)

2. After selection, click to run, deploying the TUIRoomKit Android Demo to the target device.

| **APP main page** | **Conference creation page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bbf9b9f4591f11ef8357525400bdab9d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/92cc5fa224aa11efa45a5254008fe934.png) |

## Create your first conference

Click on the **Create Room** button to create your first meeting room. The room types are **On-stage Speaking Room** and **Free Speech Room**.

- **Free Speech Room**: Regular users can freely speak and have the liberty to turn their microphones and cameras on or off.
- **On-stage Speaking Room**: Only users on stage can freely turn their microphones and cameras on or off. Regular audience members can apply to become stage users by raising their hand.

| **Free speech room member management panel** | **On-stage speaking room member list panel** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/92c0eb3924aa11efac39525400560de4.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/92985a7824aa11efac39525400560de4.jpeg) |

## Join conference

After clicking **Join Room,** participants can join the meeting created by the host by filling in the corresponding `RoomId`.

| **Join conference page** | **Conference main page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9328117624aa11ef812f5254002a8f58.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/93044b1424aa11ef9bc3525400456a87.png) |


---
*Source: [https://trtc.io/document/60443](https://trtc.io/document/60443)*
