# Run Sample Demo

- This document guides you through the whole process with the `TUILiveKit` Demo. By following these steps, you can set up and run the Demo in under 10 minutes and experience a fully featured online live streaming application with a complete UI.
- You can also customize the page style, layout, and features to fit your requirements by following the customization instructions in each section.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1a1ed63db3d411f0b96752540044a08e.png)

## Quick Experience

You can directly experience all **Live** features using the following methods.

## Prerequisites

### Enable the Service

Refer to [Enable the Service](https://www.tencentcloud.com/document/product/647/60033) to obtain a TUILiveKit trial license. Then, retrieve the following information from the [Console](https://console.trtc.io/app) for application management:

- `SDKAppID`: Application identifier (required). Tencent Cloud uses `SDKAppId` for billing and details.
- `SDKSecretKey`: Application secret key, used to initialize configuration file credentials.

### Environment Preparation

- **Node.js**: â¥ 18.19.1 (official LTS version recommended)
- **Vue**: â¥ 3.4.21
- **Modern Browser**: A browser that supports [WebRTC APIs](https://web.sdk.qcloud.com/trtc/webrtc/demo/detect/index.html)
- **Devices**: Camera, microphone, and speakers

## Instructions

### Get the Demo

1. Download the [TUILiveKit Demo](https://github.com/Tencent-RTC/TUILiveKit) from GitHub, or run the following command directly from the command line:

```
git clone https://github.com/Tencent-RTC/TUILiveKit.git
```

2. Install dependencies

```
cd TUILiveKit/Web/web-vite-vue3npm install
```

### Setup

Open the `TUILiveKit/Web/web-vite-vue3/src/config/basic-info-config.js` in the Demo and enter the `SDKAppID` and `SDKSecretKey` you obtained when enabling the service:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fa056245b3d011f0995e525400454e06.png)

### Build and Run the Demo

```
npm run dev
```

### Experience the Basic Features

#### Host Streaming

- To start streaming as a host, navigate to the streaming page by setting the URL to `http://localhost:5173/#/live-pusher`. This page supports both **landscape** and **portrait** streaming modes.
- Use the material addition area on the left to add media sources, and click the **Connect with Audience** button to accept or reject audience connection requests.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f9efe903b3d011f0bd1d5254001c06ec.png)

#### Audience Viewing

When you run the project for the first time, enter a `UserId` to register your identity. On subsequent runs, the live streaming list page displays directly, as shown below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/65ca0d17b3d211f0bb7b525400bf7822.png)

Click a live cover to enter a live room. In the live room, you can **watch the stream, follow the host, send bullet comments, view the audience list**, and more.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/850e9549b3d211f09e195254007c27c5.png)

> **Noteï¼**Do not use simple UserIDs such as "1", "123", or "111". TRTC does not support multi-end login for the same UserID, and these simple UserIDs are likely to be used by others during collaborative development, which can cause login failures. Use distinctive UserIDs during debugging.Multiple audience members can simultaneously **send bullet comments, follow the host, request to connect,** and more, to simulate real multi-user interaction scenarios.

### Customization Guide

You can modify the provided UI source code to customize the `TUILiveKit` Demo interface as needed. Run the following commands in the `TUILiveKit/Web/web-vite-vue3` directory:

macOS

Windows

```
mkdir -p ./src/TUILiveKit && rsync -av --exclude={'node_modules','package.json','excluded-list.txt'} ./node_modules/@tencentcloud/livekit-web-vue3/src/* ./src/TUILiveKit
```

```
xcopy .\\node_modules\\@tencentcloud\\livekit-web-vue3\\src\\* .\\src\\TUILiveKit /i /e /exclude:.\\node_modules\\@tencentcloud\\livekit-web-vue3\\excluded-list.txt
```

> **Noteï¼**After running the export script:The `livekit-web-vue3` source code will be generated in the specified src directory.You must then manually update the `Web/web-vite-vue3 project`. Change all component references for `livekit-web-vue3` from the npm package path to the relative path of the local source code.To reference the `tuikit-atomicx-vue3` source code, please visit its [GitHub repository](https://github.com/Tencent-RTC/TUIKit_Vue3/tree/main/packages/tuikit-atomicx-vue3) .

If you want to integrate specific pages into your existing project or customize the UI for individual pages, refer to the following documentation links for detailed guidance:

| **Page** | **Documentation Link** |
| --- | --- |
| **Host Streaming** | [Host Streaming](https://www.tencentcloud.com/document/product/647/73741) |
| **Audience Viewing** | [Audience Viewing](https://www.tencentcloud.com/document/product/647/73747) |
| **Live Streaming List** | [Live Streaming List](https://www.tencentcloud.com/document/product/647/73760) |

## FAQs

### After entering the room, you may encounter error code "-3301" with the message "Services are not available in your region."

If you receive this error code, [contact us](https://trtc.io/contact) for support.

## Contact Us

If you have any questions or suggestions during integration or usage, join our [Telegram technical group](https://t.me/+EPk6TMZEZMM5OGY1?s_url=https%3A%2F%2Ftrtc.io) or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/66940](https://trtc.io/document/66940)*
