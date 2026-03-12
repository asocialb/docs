# Run Sample Code

This document will guide you through quickly running the audio and video call Demo. By following this guide, you can run the Demo within 10 minutes and experience an audio and video call feature with a complete UI.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fd1f6c1ec47711f0b285525400bf7822.png)

## Prerequisites

### Environment Setup

- **Flutter requirements:**Flutter 3.0 and above.
- **Android requirements:** Android Studio 3.5 and above, and an Android device running Android 4.1 and above.
- **iOS requirements:**Xcode 13.0 and above, and ensure your project has a valid developer signature set.

### Activate the Service

Please refer to [Activate the Service](https://www.tencentcloud.com/document/product/647/59832) to obtain your `SDKAppID` and `SDKSecretKey`. These will be used in a later step ([Configure and Run the Demo](#7d63ff25-014c-46fa-8163-2d2ad2d6fe26)).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a33ffa18bbc411f09a6b525400454e06.png)

## Downloading the Demo

1. Download the [TUICallKit Demo](https://github.com/Tencent-RTC/TUICallKit/tree/main) source code from GitHub, or run the following command in the command line:

```
git clone https://github.com/Tencent-RTC/TUICallKit.git
```

2. Open the TUICallKit Flutter example using Android Studio or VSCode. The following process will use Android Studio as an example:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8464b112bbb711f0a6c652540044a08e.png)

> **Note:**If Flutter and Dart plugins are not installed in Android Studio, please refer to: [Installing Flutter and Dart Plugins](#73b83d22-0013-4951-a7cc-22fccfbfba41).

## Running the Demo

We recommend that you run the Demo on two devices, **log in with two different user accounts on two devices,** **one as the caller and one as the callee**, to complete an audio/video call experience.

### Step 1: Configure and Run the Demo

1. **Configure SDKAppID and SecretKey:**Open the `Flutter/example/lib/debug/generate_test_user_sig.dart`file, and fill in the `SDKAppID` and `SDKSecretKey` obtained during [Activate the Service](https://www.tencentcloud.com/document/product/647/59832):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7b8599c02d3d11efb8c45254005a8b94.png)

2. **Run the Demo:**You can run the Demo using the following command.

```
flutter run
```

### Step 2: Login and Registration

After the Demo starts, please enter an ID in the `User ID` field. If your current UserID has not been registered, you will enter the registration interface, where you can set a nickname for yourself.

| Logged-in User: Charlie |  | Logged-in User: Jane |  |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a2239205bbc011f0b0cf525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/01b81a1dbbc111f0a6c652540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2814cf9cbbc111f0a6c652540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/54a78139bbc111f0a808525400bf7822.png) |

> **Tip**:Avoid using simple UserIDs such as "1", "123", or "111". These IDs are commonly used during collaborative development and may already be in use by others, resulting in login failures. We recommend using a unique UserID during testing.

### Step 3: Make a Call

1. On the caller's device, tap 1V1 Call on the interface, enter the callee's UserID in the pop-up window, and select the desired call type.
2. Click **Initiate a Call**.

| Charlie calls Jane | Jane receives the incoming call | The call starts after Jane clicks "Answer" |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e75eb0a6bbc111f0b4c35254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ac2e4b24bbc111f0b0cf525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4a4b2e7bbc111f0a808525400bf7822.png) |

> **Tip:**To start a call, you need to confirm that the Callee User ID is a valid and logged-in ID.

## FAQs

### A signature error or login failure occurs when running the demo?

Please check if the `SDKAppID` and `SDKSecretKey` you filled in the `Flutter/example/lib/debug/generate_test_user_sig.dart` file are correct. Ensure they are the keys you obtained when [Activate the Service](https://www.tencentcloud.com/document/product/647/59832).

### Purchase prompt appears during callï¼

| Error Prompt | Solution |
| --- | --- |
| You have not purchased an audio and video calling package. Please go to the IM console to activate a free trial or purchase the official version. | You have not purchased an audio and video calling package. Please go to the console to [activate a free trial](https://console.trtc.io/call) or [purchase the official version](https://console.trtc.io/subscription/buy/call). |
| The audio and video calling package you currently purchased does not support this feature. It is recommended that you upgrade your package type. | The audio and video calling package you currently purchased does not support this feature. It is recommended that you go to the console to [upgrade your package type](https://console.trtc.io/subscription/buy/call). |

> **Tip:**If you encounter other error prompts, you can refer to the [TUICallDefine Error Codes](https://www.tencentcloud.com/document/product/647/54901#TUICommonDefine.Error) for a solution.

### How to install Flutter and Dart plugins in Android Studio?

Click on **Android Studio** > **Settings**> **Plugins**in the upper left corner to download them.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/664de2feba2011f0a808525400bf7822.png)

### How to check for Flutter environment issues?

If you need to know if there are any issues with your Flutter environment, run `flutter doctor` to check if the Flutter environment is properly installed.

```
flutter doctor
```

## Contact Us

If you have any needs or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/60414](https://trtc.io/document/60414)*
