# Run Sample Code

This document mainly introduces how to quickly run through the **Conference (TUIRoomKit) sample project** and experience a high-quality multi-person video conference. By following this document, you can run through the demo within 10 minutes and ultimately experience a multi-person video conference feature with a complete UI interface.

| **Conference creation page** | **Conference main page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc31096124a811efa45a5254008fe934.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2d6409c24a811ef94525254005f7176.png) |

## Prerequisites

- iOS 13.0 or later.
- Xcode 15.0 or later.

## Download the Demo

1. Download the [TUIRoomKit Demo](https://github.com/Tencent-RTC/TUIRoomKit/) source code from GitHub, or directly execute the following command in the command line:

```
  git clone https://github.com/Tencent-RTC/TUIRoomKit.git
```

2. Enter the iOS project directory in the command line:

```
  cd TUIRoomKit/iOS/Example
```

3. Load the dependent libraries:

```
  pod install
```

> **Note:**If you haven't installed CocoaPods, you can refer to [this](https://guides.cocoapods.org/using/getting-started.html) for instructions on how to install.If you cannot install the latest version of TUIRoomKit, execute the following command to update the local CocoaPods repository list and then install it again:pod repo update

## Configure the Demo

1. [Activate the Conference services](https://www.tencentcloud.com/document/product/647/59973#), to obtain the **SDKAppID** and **SDKSecretKey**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5607f076167d11efae48525400720cb5.png)

2. Open the project, and within it, find the `iOS/Example/Debug/GenerateTestUserSig.swift` file. Enter the corresponding **SDKAppID** and **SDKSecretKey** obtained from Back:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/55ffd82c167d11efae48525400720cb5.png)

## Running the Demo

1. Generate your own certificate (**optional**, skip this step if you already have one).
  1.1. Click on Xcode and find Edit Behaviors.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0f7ae944770311efa87a525400bdab9d.png)

  1.2. Click the Account tab, then click the **+** sign in the lower left corner, select Add **Apple ID** and click Continue.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/32abe3fb770311ef852f52540075b605.png)

  1.3. Enter your Apple ID and password to sign in.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4a2a5492770311ef8829525400fdb830.png)

2. Click to enter the **Signing & Capabilities** tab under the project **TARGETS** and fill in your own developer certificate in **Team**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6b73a0c6770311efaa4b525400d5f8ef.png)

3. Run the project.
  3.1. Please turn on the developer mode of your iOS device by clicking **Settings** > **Privacy & Security** > **Developer Mode**. Connect your device to your computer and select the device to run the demo in XCode.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9bf209b5770311efb9d8525400f69702.png)

  3.2. Click **Run** to run our TUIRoomKit iOS Demo on the target device.

| **APP main page** | **Conference creation page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a1a344e2591f11efb66652540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ddee106624a811ef94525254005f7176.png) |

> **Noteï¼**This project also supports running on the simulator. Just select the simulator model when selecting the device.

## Create your first conference

Click on the **Create Room** button to create your first meeting room. The room types are **On-stage Speaking Room** and **Free Speech Room**.

- **Free Speech Room**: Regular users can freely speak and have the liberty to turn their microphones and cameras on or off.
- **On-stage Speaking Room**: Only users on stage can freely turn their microphones and cameras on or off. Regular audience members can apply to become stage users by raising their hand.

| **Free speech room member management panel** | **On-stage speaking room member list panel** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/de12e9ca24a811efac39525400560de4.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ddc744d724a811ef9bc3525400456a87.jpeg) |

## Join conference

After clicking **Join Room,** participants can join the meeting created by the host by filling in the corresponding `RoomId`.

| **Join conference page** | **Conference main page** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dee1ef1d24a811ef94525254005f7176.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/de1a232524a811efa45a5254008fe934.png) |

> **Note:**If you want to use different mobile phones to experience audio and video intercommunication scenarios, please make sure that the **SDKAppID** filled in the iOS/Example/Debug/GenerateTestUserSig.swift file is consistent.

## Suggestions and Feedback

If you have any suggestions or feedback, please contact info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/60442](https://trtc.io/document/60442)*
