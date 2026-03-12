# Run Sample Demo

This guide walks you through setting up the **TUILiveKit** Android Demo in just 10 minutes. Youâll experience a fully featured video live streaming and voice chat room with a complete UI interface.

## Quick Experience

You can directly experience all **Live** features using the following methods.

## Prerequisites

### Enable the Service

Refer to [Enable the Service](https://www.tencentcloud.com/document/product/647/60033) to obtain a TUILiveKit trial version. Then, go to [the Console](https://console.trtc.io/app) for application management, and get the following:

- `SDKAppID`: Application identifier (required). Tencent Cloud uses `SDKAppId` for billing and details.
- `SDKSecretKey`: Application secret key, used to initialize the configuration file with secret information.

### Environment Preparation

- Android 5.0 (API level 21) or above
- Gradle 8.0 or above
- Two Android devices running 5.0 or above

## Instructions

### Get the Demo

1. **Download the source code**: Download the [TUIKit_Android](https://github.com/Tencent-RTC/TUIKit_Android) source code from GitHub, or run the following command in your terminal:

```
  git clone https://github.com/Tencent-RTC/TUIKit_Android.git
```

2. **Open the project**: Open the TUILiveKit Android project in `Android Studio`:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/02f11d34bef911f0a808525400bf7822.png)

### Setup

1. **Configure**`SDKAppID`**and**`SDKSecretKey`: Open the `TUIKit_Android/application/debug/src/main/java/com/tencent/qcloud/tuikit/debug/GenerateTestUserSig.java` file and enter your `SDKAppID`and`SDKSecretKey`:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/03127a95bef911f08863525400e889b2.png)

### **Build and Run the Demo**

1. In the upper right corner of `Android Studio,` select the device where you want to run the Demo:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/02f82e15bef911f0a808525400bf7822.png)

2. Click Run to `deploy` `TUIKit_Android` to the selected device.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/02f6f350bef911f0a6c652540044a08e.png)

> **Note:**For a complete live streaming experience, log in to the Demo on two devices with different usersâone as the host, the other as the audience.

### Experience the Basic Features

#### 1. Login & Registration

Enter your `ID` in the `UserID` field. If the `UserID` has not been used before, youâll be redirected to the registration page to set your avatar and nickname.

| **Anchorï¼mikeï¼** |  | **Audieceï¼vinceï¼** |  |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8522a98fbf7611f09a6b525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8518b0acbf7611f0a6c652540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/852bf3b2bf7611f0b4c35254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/852fb8fdbf7611f09a6b525400454e06.png) |

> **Note:**Do not use simple UserIDs such as "1", "123", or "111". TRTC does not support multi-end login for the same UserID, and these simple UserIDs are likely to be used by others during collaborative development, which can cause login failures. Use distinctive UserIDs during debugging.

#### 2. Video Live Streaming

Click `Live > Video Live` to start a video live streaming session.

| **Live Streaming List** | **Host Preview Before Going Live** | **Host Starts Video Live Streaming** | **Audience Watches Live Stream** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8f909f5bf7611f0b4c35254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e5298586bf7611f0a6c652540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fc7ac332bf7611f09a6b525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/02c2ffc9bf7711f08863525400e889b2.png) |

#### 3. Voice Chat Room

Click `Live > Voice Room` to start a voice chat session.

| **Live Streaming List** | **Host Preview Before Going Live** | **Host Starts Voice Chat Live** | **Audience Joins Voice Chat Room** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0334f99abef911f085a55254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/033eba1fbef911f0a6c652540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/034bdf67bef911f08863525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/035934d9bef911f0b4c35254001c06ec.png) |

## Next Steps

After running the Demo, refer to the following integration guides to add these features to your own project:

| **Name** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Video Live Streaming** | Supports ultra-low latency HD streaming, multi-user co-hosting/PK, real-time beauty filters, bullet comments, and gift interactionsâenabling you to build interactive video live streaming scenarios. | [Integration Guide](https://www.tencentcloud.com/document/product/647/72218) |
| **Voice Chat Room** | Delivers ultra-clear audio quality, supports multi-user co-hosting, seat management, and real-time text chatâideal for KTV, social, or gaming-themed rooms. | [Integration Guide](https://www.tencentcloud.com/document/product/647/60335) |

## FAQs

### Demo reports signature error or login failure?

Verify that the **SDKAppID** and **SDKSecretKey** in `TUIKit_Android/application/debug/src/main/java/com/tencent/qcloud/tuikit/debug/GenerateTestUserSig.java` are correct. Ensure they match the values from the [Tencent Cloud Console Application Management](https://console.trtc.io/app) page.

### Will running the Demo be affected if Gradle version is below 8.0?

Yes. If your `Gradle` version is below 8.0, you may encounter dependency download failures or build errors. Upgrade your `Gradle` version in Android Studio to meet the requirements.

### After entering the room, you may encounter error code "-3301" with the message "Services are not available in your region."

If you receive this error code, [contact us](https://trtc.io/contact) for support.

## Contact Us

If you have any questions or suggestions during running the demo or usage, join our [Telegram technical group](https://t.me/+EPk6TMZEZMM5OGY1?s_url=https%3A%2F%2Ftrtc.io) or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/60454](https://trtc.io/document/60454)*
