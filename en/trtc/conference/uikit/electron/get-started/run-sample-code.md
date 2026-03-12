# Run Sample Code

This article describes how to quickly run through the TUIRoomKit sample project and experience high-quality multiplayer video conferencing. You can run through the demo in less than 10 minutes and experience a multiplayer videoconferencing with a complete UI.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/25f46b18c0ce11efa28d525400329841.png)

## Prerequisites

- Node.js version: Node.js â¥ 16.19.1 (we recommend using the official LTS version, please match the npm version with the node version).
- Modern browser, [supporting WebRTC APIs](https://caniuse.com/?search=webrtc).

## Step.1 Download Demo

1. Open the Terminal, copy and paste the sample command to clone the repository.

```
git clone https://github.com/Tencent-RTC/TUIRoomKit.git
```

2. Install dependencies.

```
cd ./TUIRoomKit/Electron/example/vue3
```

```
npm install
```

## Step.2 Configure Demo

[Go to the Activate Service page](https://trtc.io/document/59832?platform=web&product=call&menulabel=web) and get the `SDKAppID and SDKSecretKey`**, then fill them in the TUIRoomKit/Electron/example/vue3/packages/renderer/src/config/basic-info-config.js** file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a2184e12c0ce11efad135254002693fd.png)

## Step.3 Run Demo

Run Demo by typing the command in the terminal.

```
npm run dev
```

> **Noteï¼**For local environment, please access under localhost protocol, please refer to [the description of network access protocol](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-05-info-browser.html#h2-3).

## Step.4 Make your first Conference

1. Open a browser page and enter the corresponding URL.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0fcd1953bdfa11ef96d352540075b605.png)

2. Click on the **New Room** to create your first conference room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/11a416efbdfa11efb9d2525400329841.png)


---
*Source: [https://trtc.io/document/60444](https://trtc.io/document/60444)*
