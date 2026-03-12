# Run Sample Code

This document will guide you through quickly running the audio and video call Demo. By following this guide, you can run the Demo within 10 minutes and experience an audio and video call feature with a complete UI.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7a194572ba2d11f09a6b525400454e06.png)

## Prerequisites

### Environment Setup

- Xcode 13 or later.
- Two iOS devices running iOS 13.0 or later.
- CocoaPods 1.7.5 and above. If not installed, please refer to [CocoaPods Guides - Getting Started](https://guides.cocoapods.org/using/getting-started.html) for installation.

### Activate the Service

Please refer to [Activate the Service](https://www.tencentcloud.com/document/product/647/59832) to activate the audio/video service for the demo. After activation, take note of the `SDKAppID` and `SDKSecretKey`, which will be used in a later step ([Configure and Run the Demo](#7d63ff25-014c-46fa-8163-2d2ad2d6fe26)).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/703410ecbbc411f09a6b525400454e06.png)

## Download the Demo

1. Download the [TUICallKit Demo](https://github.com/Tencent-RTC/TUIKit_iOS) source code from GitHub, or run the following command directly in your terminal:

```
git clone https://github.com/Tencent-RTC/TUIKit_iOS.git
```

2. In your terminal, navigate to the iOS project directory:

```
cd TUIKit_iOS/application
```

3. Install the dependencies:

```
pod install --repo-update
```

## Run the Demo

Run the application using Xcode, run the Demo on two devices, log in with two user IDsâone as the caller and one as the calleeâto complete an audio and video call experience.

### Step 1: Configure and Run the Demo

1. After the installation is complete, open the project using the `YourProjectName.xcworkspace` file.
2. **Configure SDKAppID and SecretKey:**Open the`/application/Debug/GenerateTestUserSig.swift`file and fill in the `SDKAppID` and `SDKSecretKey` you obtained when [Activate the Service](https://www.tencentcloud.com/document/product/647/59832):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a61b13d4f08811f09965525400370dda.png)

3. **Select Device:**In Xcode, select the device you want to run the demo on, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/adac56c6f08811f0bdf6525400074c32.png)

4. **Compile and Run:**Click the Run button to build and run our TUICallKit iOS Demo on the target device.

### Step 2: Login and Registration

After the Demo starts, please enter an ID in the `User ID` field. If your current UserID has not been registered, you will enter the registration interface, where you can set a nickname for yourself.

| Logged-in User: Charlie |  | Logged-in User: Jane |  |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dc7b5f59f08811f0bdf6525400074c32.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e0e7f94ff08811f0bfd65254001d6acc.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e3f717f9f08811f0a6f452540097cba1.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e9c2a8ecf08811f0a94d52540073fd3b.png) |

> **Tip:**Avoid using simple UserIDs such as "1", "123", or "111". These IDs are commonly used during collaborative development and may already be in use by others, resulting in login failures. We recommend using a unique UserID during testing.

### Step 3: Make a Call

1. On the caller's device, tap 1V1 Call on the interface, enter the callee's UserID in the pop-up window, and select the desired call type.
2. Click **Start Call**.

| Click **Call** | Charlie calls Jane | Jane receives the incoming call | The call starts after Jane clicks **Answer** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0e93c5b4f08911f0bdf6525400074c32.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1144728df08911f0bdf6525400074c32.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/133d5672f08911f09d46525400a31896.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/151e48c5f08911f0bfd65254001d6acc.png) |

> **Tips:**To start a call, you need to confirm that the Callee User ID is a valid and logged-in ID.

## FAQs

### A signature error or login failure occurs when running the demo?

Please check if the `SDKAppID` and `SDKSecretKey` you filled in the`/application/Debug/GenerateTestUserSig.swift` file are correct. Ensure they are the keys you obtained when [Activate the Service](https://www.tencentcloud.com/document/product/647/59832).

### Purchase prompt appears during callï¼

| Error Message | Solution |
| --- | --- |
| You have not purchased an audio and video calling package. Please go to the IM console to activate a free trial or purchase the official version. | You have not purchased an audio and video calling package. Please go to the console to [activate a free trial](https://console.trtc.io/call) or [purchase the official version](https://console.trtc.io/subscription/buy/call). |
| The audio and video calling package you currently purchased does not support this feature. It is recommended that you upgrade your package type. | The audio and video calling package you currently purchased does not support this feature. It is recommended that you go to the console to [upgrade your package type](https://console.trtc.io/subscription/buy/call). |

> **Tips:**If you encounter other error prompts, you can refer to the [TUICallDefine Error Codes](https://www.tencentcloud.com/document/product/647/54901#TUICommonDefine.Error) for a solution.

## Contact Us

If you have any questions or suggestions during integration or usage, feel free to join our [Telegram](https://t.me/+Lmw2MSqW6ethMGM1) group or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/60416](https://trtc.io/document/60416)*
