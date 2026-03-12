# Run Sample Demo

This guide provides step-by-step instructions to help you quickly set up and run the Live Streaming Demo. Youâll be able to launch the demo in about 10 minutes and explore a complete live streaming user interface.

| **Host Live Stream Page** | **Co-host Management Page** | **Audience Viewing Page** |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/955c635feaef11f0bfd65254001d6acc.PNG) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8e26b1e5eaef11f0b306525400380f7d.PNG) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/854bea24eaef11f0a6f452540097cba1.PNG) |

## Prerequisites

**Activate the Service**

Go to [Activate the Service](https://www.tencentcloud.com/document/product/647/60033) to obtain a TUILiveKit Trial Edition. Then, on the [Application Management](https://trtc.io/login?fro=gt&s_url=https%3A%2F%2Fconsole.trtc.io%2Fapp) page, collect the following details:

- **SDKAppID**: Your application identifier (required). TRTC uses SDKAppId for billing and statistics.
- **SDKSecretKey**: Your application SecretKey, required for initializing configuration files.

**Environment Setup**

- **Node.js**: Version 20.0.0 or higher (LTS recommended)
- **Yarn**: Version 4.11.0 or higher
- **Android Studio (Android only)**: Required for Android development
- **Xcode 14+**: Required for iOS development (macOS only)
- **CocoaPods (iOS only)**: CocoaPods installed. If not, see the [CocoaPods Installation Guide](https://guides.cocoapods.org/using/getting-started.html) or run:

`sudo gem install cocoapods` in your terminal.

> **Tipsï¼**When running `sudo gem install cocoapods`, you may be prompted for your computer password. Enter your administrator password to continue.

- **Devices**: Two smartphones with working cameras and microphones

## Instructions

### Download the Demo

1. Clone the TUILiveKit Demo source code from GitHub, or run:

```
git clone https://github.com/Tencent-RTC/TUIKit_ReactNative.git
```

2. Install project dependencies:

```
cd TUIKit_ReactNativeyarn install
```

3. Install iOS Pod dependencies (skip this step if you are only running on Android):

```
cd TUIKit_ReactNative/application/iospod install
```

### Configure the Demo

1. Set **SDKAppID** and **SDKSecretKey**: Open `TUIKit_ReactNative/application/src/debug/UserSigGenerator.ts` and enter the **SDKAppID** and **SDKSecretKey** you obtained when activating the service:

```
// Your SDKAppIDexport const sdkAppID = 0;// Your SDKSECRETKEYconst SDKSECRETKEY = "";
```

2. Set up Apple Developer signing (skip this step if you are only running on Android): In your project, go to **TARGETS** > **Signing & Capabilities**, enable **Automatically** **manage** signing, and select your Apple Developer account and Bundle Identifier:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/591263f2ea2b11f0a75a525400370dda.png)

### Build and Run

Run on Android

Run on iOS

To run the demo on Android:

```
cd TUIKit_ReactNative/applicationyarn android
```

To run the demo on iOS:

```
cd TUIKit_ReactNative/applicationyarn ios
```

### Try Live Streaming and Viewing

1. **Log in or sign up with a custom user ID.**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d998d214ea2b11f0ae695254001d6acc.png)

> **Note:**TUILiveKit does not support logging in on multiple devices with the same UserID. During team development, simple UserIDs like â1â, â123â, or â111â may be occupied, causing login failures. Use unique UserIDs for testing. To fully experience the live streaming workflow, log in on two devices with different usersâone as the host, one as the audience.

2. **Start a live stream as a host:**

Tap the center button at the bottom of the homepage to open the live preview page. Then tap **Start Live** to begin streaming.

| **Live Stream List Page** | **Host Preview Page** | **Host Live Page** |
| --- | --- | --- |
|  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/56b9a622ea2c11f0a616525400380f7d.png) |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b2b827bfeaef11f0b306525400380f7d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc994ff5eaef11f09d62525400ecee81.PNG) |

3. **Join as an audience member:**

On a second device, log in with a different userID as an audience. Tap any room in the Live Stream List or enter a specific liveID to join a stream. You can interact with the host by co-hosting, sending gifts, or participating in chat.

| **Live Stream List Page** | **Gift Selection Page** | **Audience Viewing Page** |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c72685b7eaef11f09d46525400a31896.PNG) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cd8343c9eaef11f0bfd65254001d6acc.PNG) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/022f112feaf011f0a94d52540073fd3b.png) |

## Next Steps

After youâve successfully run the demo, you can integrate its features into your own project as needed. For detailed integration instructions, refer to the following guides:

| **Page** | **Documentation link** |
| --- | --- |
| **Live Stream Publishing** | [Live streaming page](https://www.tencentcloud.com/document/product/647/77116) |
| **Audience Viewing** | [Audience viewing page](https://www.tencentcloud.com/document/product/647/77117) |
| **Live Stream List** | [Live stream list page](https://www.tencentcloud.com/document/product/647/77118) |

## Contact Us

If you have any questions or suggestions during running the demo or usage, join our [Telegram technical group](https://t.me/+EPk6TMZEZMM5OGY1?s_url=https%3A%2F%2Ftrtc.io) or [contact us](https://trtc.io/contact) for support.

## FAQs

### Signature error or login failure in the demo?

Verify that the SDKAppID and SDKSecretKey entered in `TUIKit_ReactNative/application/src/debug/UserSigGenerator.ts` match the credentials from the [TRTC Console Application Management](https://trtc.io/login?fro=gt&s_url=https%3A%2F%2Fconsole.trtc.io%2Fapp) page.

### How to check React Native environment issues?

To check your React Native environment, run the following command:

```
npx react-native doctor
```


---
*Source: [https://trtc.io/document/77111](https://trtc.io/document/77111)*
