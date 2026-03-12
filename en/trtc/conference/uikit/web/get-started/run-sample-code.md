# Run Sample Code

This article describes how to quickly run through the TUIRoomKit sample project and experience high-quality multiplayer video conferencing. You can run through the demo in less than 10 minutes and experience a multiplayer videoconferencing with a complete UI.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fc2ad018bde711efb6f3525400dd4ba9.png)

## Prerequisites

- Node.js version: Node.js â¥ 16.19.1 (we recommend using the official LTS version, please match the npm version with the node version).
- Modern browser, [supporting WebRTC APIs](https://caniuse.com/?search=webrtc).

## Step.1 Download Demo

1. Open the Terminal, copy and paste the sample command to clone the repository.

```
git clone https://github.com/Tencent-RTC/TUIRoomKit.git
```

2. Install dependencies.

Vue3

Vue2

```
cd ./TUIRoomKit/Web/example/vite-vue3-ts
```

```
cd ./TUIRoomKit/Web/example/webpack-vue2.7-ts
```

```
npm install
```

## Step.2 Configure Demo

[Go to the Activate Service page](https://trtc.io/document/59832?platform=web&product=call&menulabel=web) and get the `SDKAppID and SDKSecretKey`**, then fill them in the TUIRoomKit/Web/example/vite-vue3-ts/src/config/basic-info-config.js** file.

> **Noteï¼**For Vue2 projects, open the **TUIRoomKit/Web/example/webpack-vue2.7-ts/src/config/basic-info-config.js** file and enter the `SDKAppID and SDKSecretKey` you got when you activated the service.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/35094959bdec11efb51a525400bdab9d.png)

## Step.3 Run Demo

Run Demo by typing the command in the terminal.

Vue3

Vue2

```
npm run dev
```

```
npm run serve
```

> **Noteï¼**For local environment, please access under localhost protocol, please refer to [the description of network access protocol](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-05-info-browser.html#h2-3).

## Step.4 Make your first Conference

1. Open a browser page and enter the corresponding URL.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/31f031d4bdee11efb9d2525400329841.png)

2. Click on the **New Room** to create your first conference room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b6f298dabdee11efba8d525400f69702.png)


---
*Source: [https://trtc.io/document/60441](https://trtc.io/document/60441)*
