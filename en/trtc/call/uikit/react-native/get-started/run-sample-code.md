# Run Sample Code

This document will guide you through quickly running the audio and video call Demo. By following this guide, you can run the Demo within 10 minutes and experience an audio and video call feature with a complete UI.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1b059654bbad11f0a5e052540099c741.png)

## Prerequisites

### Environment Setup

- [Node.js](https://nodejs.org/en/) 16 and above.
- Two mobile phones.

### Activate the Service

Please refer to [Activate the Service](https://www.tencentcloud.com/document/product/647/59832) to obtain your `SDKAppID` and `SDKSecretKey`. These will be used in a later step ([Configure and Run the Demo](#ac9d69e3-f8f6-4eaf-bd28-6ab847a6669a)).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7e45366bbc411f0b9945254005ef0f7.png)

## Downloading the Demo

1. Download the source code from [GitHub](https://github.com/Tencent-RTC/TUICallKit), or run the following command in the command line:

```
git clone https://github.com/Tencent-RTC/TUICallKit.git
```

2. Enter the `./TUICallKit/ReactNative` directory and depend on the TUICallKit component.

```
cd ./TUICallKit/ReactNativeyarn install
```

## Running the Demo

We recommend that you run the Demo on two devices, **Log in with two different user accounts on two devices,** **one as the caller and one as the callee**, to complete an audio/video call experience.

### Step 1: Configure and Run the Demo

1. **Configure SDKAppID and SecretKey:**Open the `TUICallKit/ReactNative/src/debug/GenerateTestUserSig-es.js` file, and fill in the `SDKAppID` and `SDKSecretKey` obtained during [Activate the Service](https://www.tencentcloud.com/document/product/647/59832):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1806fd5fb6db11ef9448525400fdb830.png)

2. **Compile and Run:** Run the Demo using the following command.

```
# TUICallKit/ReactNativeyarn start
```

### Step 2: Login

After the Demo starts, please enter an ID at the `Login` field to complete the login.

| Login User: Charlie | Login User: Jane |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/26845f82ba2411f0b4c35254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5c1fed88ba2411f0b0cf525400e889b2.png) |

> **Tip:**Avoid using simple UserIDs such as "1", "123", or "111". These IDs are commonly used during collaborative development and may already be in use by others, resulting in login failures. We recommend using a unique UserID during testing.

### Step 3: Make a Call

1. On the caller's device, tap 1V1 Call on the interface, enter the callee's UserID in the pop-up window, and select the desired call type.
2. Click **Start Call**.

| Charlie calls Jane | Jane receives the call | Both parties start talking after Jane clicks "Answer" |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/16139640ba2511f0a5e052540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e86660e9bbc411f085a55254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f86eb8dfbbc411f0b4c35254001c06ec.png) |

> **Tip:**To start a call, you need to confirm that the Callee User ID is a valid and logged-in ID.

## FAQs

### A signature error or login failure occurs when running the demo?

Please check if the `SDKAppID` and `SDKSecretKey` you filled in the `TUIKit_Android/application/debug/src/main/java/com/tencent/qcloud/tuikit/debug/GenerateTestUserSig.java` file are correct. Ensure they are the keys you obtained when [Activate the Service](https://www.tencentcloud.com/document/product/647/59832).

### Purchase prompt appears during callï¼

| Error Prompt | Solution |
| --- | --- |
| You have not purchased an audio and video calling package. Please go to the IM console to activate a free trial or purchase the official version. | You have not purchased an audio and video calling package. Please go to the console to [activate a free trial](https://console.trtc.io/call) or [purchase the official version](https://console.trtc.io/subscription/buy/call). |
| The audio and video calling package you currently purchased does not support this feature. It is recommended that you upgrade your package type. | The audio and video calling package you currently purchased does not support this feature. It is recommended that you go to the console to [upgrade your package type](https://console.trtc.io/subscription/buy/call). |

### How to check for React Native environment issues?

If you need to know if there are any issues with your React Native environment, run `npx react-native doctor` to check if the React Native environment is properly installed.

```
npx react-native doctor
```

## Contact Us

If you have any needs or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/66931](https://trtc.io/document/66931)*
