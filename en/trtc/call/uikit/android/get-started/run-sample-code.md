# Run Sample Code

This document will guide you through quickly running the audio and video call Demo. By following this guide, you can run the Demo within 10 minutes and experience an audio and video call feature with a complete UI.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/431eed47bba411f0b4c35254001c06ec.png)

## Prerequisites

### Environment Setup

- Install [Android Studio](https://developer.android.com/studio?hl=zh-cn).
- Two devices running Android 5.0 or above.

### Activate the Service

Please refer to [Activate the Service](https://www.tencentcloud.com/document/product/647/59832) to obtain your `SDKAppID` and `SDKSecretKey`. These will be used in a later step ([Configure and Run the Demo](#7d63ff25-014c-46fa-8163-2d2ad2d6fe26)).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c61e2f70bbc311f0b4c35254001c06ec.png)

## Downloading the Demo

1. Download the [TUICallKit Demo](https://github.com/Tencent-RTC/TUIKit_Android) source code from GitHub, or run the following command in the command line:

```
git clone https://github.com/Tencent-RTC/TUIKit_Android.git
```

2. Open the `TUIKit_Android/application` directory through Android Studio:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aacfbeebf07a11f09d62525400ecee81.png)

> **Tip:**Currently, TUICallKit is compatible with Gradle 7.x and 8.x. If you encounter an issue like: Your build is currently configured to use incompatible Java 21.0.5 and Gradle 8.0. Cannot sync the project.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f6e8ea15b93011f0b0cf525400e889b2.png)**Recommended Solution:** Change the Java version in Android Studio to 17.Open Android Studio Settings.**Windows**ï¼File > Settings**Mac**ï¼Android Studio > PreferencesModify the Java compiler settings.Path: Build, Execution, Deployment > Build Tools > GradleChange the Gradle JDK to 17 (if installed) or Use project JDK

## Running the Demo

Run the program through Android Studio. **Log in with two different user accounts on two devices,** **one as the caller and one as the callee**, to complete an audio/video call experience.

### Step 1: Configure and Run the Demo

1. **Configure SDKAppID and SecretKey:**Open the`application/debug/src/main/java/com/tencent/qcloud/tuikit/debug/GenerateTestUserSig.java`file, and fill in the `SDKAppID` and `SDKSecretKey` obtained during [Activate the Service](https://www.tencentcloud.com/document/product/647/59832):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3a4be2eff07b11f09965525400370dda.png)

2. **Compile and Run:** Please select a device and run the Demo.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e3742dc1bbb611f0a6c652540044a08e.png)

### Step 2: Login and Registration

After the Demo starts, please enter an ID in the `User ID` field. If your current UserID has not been registered, you will enter the registration interface, where you can set a nickname for yourself.

| Logged-in User: Charlie |  | Logged-in User: Jane |  |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9e8d7b04f07c11f0b306525400380f7d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b02576f6f07c11f0bfd65254001d6acc.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d0916882f07c11f09965525400370dda.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc8aac07f07c11f0a94d52540073fd3b.png) |

> **Tip**:Avoid using simple UserIDs such as "1", "123", or "111". These IDs are commonly used during collaborative development and may already be in use by others, resulting in login failures. We recommend using a unique UserID during testing.

### Step 3: Make a Call

1. Click **Call** on the interface. On the next screen, enter the recipient's ID in the User ID List and select the Media Type.
2. Click **Initiate a Call**.

| Click **Call** | Charlie calls Jane | Jane receives the incoming call | The call starts after Jane clicks **Answer** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/edec88d6f07d11f09965525400370dda.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f58d95f7f07d11f09d62525400ecee81.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/faa4a6dcf07d11f09d62525400ecee81.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/07f2022bf07e11f0a6f452540097cba1.png) |

> **Tip:**To start a call, you need to confirm that the Callee User ID is a valid and logged-in ID.

## FAQs

### A signature error or login failure occurs when running the demo?

Please check if the `SDKAppID` and `SDKSecretKey` you filled in the`TUIKit_Android/application/debug/src/main/java/com/tencent/qcloud/tuikit/debug/GenerateTestUserSig.java` file are correct. Ensure they are the keys you obtained when [Activate the Service](https://www.tencentcloud.com/document/product/647/59832).

### Purchase prompt appears during callï¼

| Error Prompt | Solution |
| --- | --- |
| You have not purchased an audio and video calling package. Please go to the IM console to activate a free trial or purchase the official version. | You have not purchased an audio and video calling package. Please go to the console to [activate a free trial](https://console.trtc.io/call) or [purchase the official version](https://console.trtc.io/subscription/buy/call). |
| The audio and video calling package you currently purchased does not support this feature. It is recommended that you upgrade your package type. | The audio and video calling package you currently purchased does not support this feature. It is recommended that you go to the console to [upgrade your package type](https://console.trtc.io/subscription/buy/call). |

> **Tip:**If you encounter other error prompts, you can refer to the [TUICallDefine Error Codes](https://www.tencentcloud.com/document/product/647/54901#TUICommonDefine.Error) for a solution.

## Contact Us

If you have any questions or suggestions during integration or usage, feel free to join our [Telegram](https://t.me/+Lmw2MSqW6ethMGM1) group or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/60417](https://trtc.io/document/60417)*
