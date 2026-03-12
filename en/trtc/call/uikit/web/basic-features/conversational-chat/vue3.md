# Vue3

By integrating Chat and CallKit, you can achieve the following effects. Click [Try It Online](https://trtc.io/document/50061?platform=web&product=chat&menulabel=uikit).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c08c4920d32611efa2ff52540044a08e.png)

## Environment Requirements

- TypeScript
- Sass (The version of sass-loader should be â¤ 10.1.1)
- nodeï¼node.js â¥ 16.0.0ï¼
- npm (use a version that matches the Node version in use)

## Step 1: Integrating Chat

For detailed steps, please refer to: [Quick Integration of Chat](https://trtc.io/document/58644?platform=web&product=chat&menulabel=uikit).

## Step 2: Activating the Audio and Video Call Capability

Before using the audio and video services provided by Tencent Cloud, you need to go to the console to activate the service for the application. Refer to the specific steps in [Activate the Service](https://trtc.io/document/59832).

## Step 3: Download the TUICallKit Component

Download the TUICallKit component via [npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-vue), version 3.3.6 and above:

```
npm i @tencentcloud/call-uikit-react
```

## Step 4: Introducing and Invoking the TUICallKit Component

As follows: Import `<TUICallKit />` where `<TUIKit />` is imported.

```
<template>  <div id="app">    <TUIKit :SDKAppID="YOUR_SDKAPPID" userID="YOUR_USERID" userSig="YOUR_USERSIG" />    <TUICallKit class="callkit-container" :allowedMinimized="true" :allowedFullScreen="false" />  </div></template><script lang="ts" setup>import { TUIKit } from './TUIKit';import { TUICallKit } from '@tencentcloud/call-uikit-vue';</script><style lang="scss"></style>
```

## Step 5: Launching the Project

vite

webpack

```
npm run dev
```

```
npm run serve
```

## Step 6: Sending Your First Message

As shown in the figure, you can send messages to and from your friends.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9e3613c9d32511ef81865254005ef0f7.png)

## Step 7. Make your first call

As shown in the figure, click the video/audio Icon in the toolbar to realize the call effect.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b20eb825d32511efa4a3525400bf7822.png)

## FAQs

- If you encounter any problems with access and use, please refer to [FAQs](https://trtc.io/document/53565?platform=web&product=call).
- If you have any requirements or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/67769](https://trtc.io/document/67769)*
