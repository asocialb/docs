# Web&H5 (Vue3)

This document describes how to rapidly integrate the TUICallKit component. You can complete the following key steps within 10 minutes and obtain a complete audio and video call interface.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b85ededb32c11f099275254005ef0f7.png)

## Preparations

### **Environmental Requirements**

- [Node.js](https://nodejs.org/en/) version 16+.
- Modern browser, supporting WebRTC APIs.

## Activate the service

Before using the audio and video service provided by Tencent Cloud, go to the console to activate the service for your application. For specific steps, see [activating the service](https://www.tencentcloud.com/document/product/647/59832). After enabling the service, record the `SDKAppID` and `SDKSecretKey`, which will be used in subsequent stepsï¼loginï¼.

## Implementation

### Download the TUICallKit

1. Download the [@trtc/calls-uikit-vue](https://www.npmjs.com/package/@trtc/calls-uikit-vue) component. In existing projects or empty projects created using scaffolding tools like @vue/cli or Vite, the following demonstrates an empty project created with @vue/cli.

```
npm install @trtc/calls-uikit-vue
```

2. Copy the `debug` directory to your project directory `src/debug`, it is necessary when generating userSig locally.

MacOS

Windows

```
cp -r node_modules/@trtc/calls-uikit-vue/debug ./src
```

```
xcopy node_modules\\@trtc\\calls-uikit-vue\\debug .\\src\\debug /i /e
```

### Add the TUICallKit component

You can choose to import the sample code in the `src/App.vue` file.The example code uses the `Composition API` approach.

1. Using [<TUICallKit />](https://trtc.io/document/51015#init#tuicallkit), which contains the complete UI interaction during a call.

```
<template>  <span> caller's ID: </span>  <input type="text" v-model="callerUserID">   <button @click="init"> step1. init </button> <br>  <span> callee's ID: </span>  <input type="text" v-model="calleeUserID">  <button @click="call"> step2. call </button>    <!--ã1ãImport the TUICallKit component: Call interface UI -->  <TUICallKit style="width: 650px; height: 500px " /></template>
```

2. Using the [TUICallKitAPI.init](https://trtc.io/document/51015#init) API to log in to the component, you need to `fill in``SDKAppID, SDKSecretKey`**as two parameters in the code.**

```
<script setup> // lang='ts'import { ref } from 'vue';import { TUICallKit, TUICallKitAPI } from "@trtc/calls-uikit-vue";import * as GenerateTestUserSig from "./debug/GenerateTestUserSig-es"; // Refer to Step 2.3const SDKAppID = 0;       // TODO: Replace with your SDKAppID (Notice: SDKAppID is of type numberï¼const SDKSecretKey = '';  // TODO: Replace with your SDKSecretKeyconst callerUserID = ref('');const calleeUserID = ref('');//ã2ãInitialize the TUICallKit componentconst init = async () => {  const { userSig } = GenerateTestUserSig.genTestUserSig({    userID: callerUserID.value,     SDKAppID,    SecretKey: SDKSecretKey   });  await TUICallKitAPI.init({    userID: callerUserID.value,     userSig,     SDKAppID,  });  alert('TUICallKit init succeed');}</script>
```

| **Parameter** | **Type** | **Note** |
| --- | --- | --- |
| userID | String | **Unique identifier of the user,**`defined by you`**,**it is allowed to contain only upper and lower case letters (a-z, A-Z), numbers (0-9), underscores, and hyphens. |
| SDKAppID | Number | The unique identifier for the audio and video application created in the [Tencent RTC Console](https://console.trtc.io/). |
| SDKSecretKey | String | The SDKSecretKey of the audio and video application created in the [Tencent RTC Console](https://console.trtc.io/). |
| userSig | String | A security protection signature used for user log in authentication to confirm the user's identity and prevent malicious attackers from stealing your cloud service usage rights. |

> **Explanation of userSig:****Development environment:** If you are running a demo locally and developing debugging, you can use the `genTestUserSig` (Refer to Step 3.2) function in the debug file to generate a `userSig`. In this method, SDKSecretKey is vulnerable to decompilation and reverse engineering. Once your key is leaked, attackers can steal your Tencent Cloud traffic.**Production environment:**If your project is going live, please use the [Server-side Generation of UserSig](https://trtc.io/document/35166) method.

### Set Nickname and Avatar ï¼Optionalï¼

The user logging in for the first time has no avatar and nickname information. You can set the avatar and nickname through the [setSelfInfo](https://www.tencentcloud.com/document/product/647/51015#setSelfInfo) API.

```
try {  await TUICallKitAPI.setSelfInfo({    nickName: "jack",    avatar: "http://xxx",  });} catch (error: any) {  alert(`[TUICallKit] Failed to call the setSelfInfo API. Reason: ${error}`);}
```

> **Noteï¼**Due to user privacy restrictions, for calls between non-friends, there might be a delay in updating the callee's nickname and avatar. This will be updated smoothly after the first successful call.

### Start a Call

The caller can initiate a voice or video call by calling the [calls](https://www.tencentcloud.com/document/product/647/51015#calls) function and specifying the call type and the callee's userID. The [calls](https://www.tencentcloud.com/document/product/647/51015#calls) API simultaneously supports one-to-one calls and group calls. When the userIDList contains a single userID, it is a one-to-one call; when the userIDList contains multiple userIDs, it is a group call.

1. Using the [TUICallKitAPI.calls API](https://trtc.io/document/51015#calls) to make a call.

```
import { TUICallKitAPI, CallMediaType } from "@trtc/calls-uikit-vue";//ã3ãMake a 1v1 video callconst call = async () => {  await TUICallKitAPI.calls({    userIDList: [calleeUserID.value],    type: CallMediaType.VIDEO,  }); };
```

2. Run the project.

> **Warning:****For local environment, please access under**`localhost protocol`**. For public network experience, please access under HTTPS protocol. For details, see**[Description of Network Access Protocol](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-05-info-browser.html#h2-3)**.**

3. Open two browser pages,**enter different userID(defined by you)**click `step1. init` to login (caller and callee).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/601ba223668811efbd54525400f69702.png)

4. **After both userID init to successfully**, click on` step2. call`to make a call. If you have a call problem, refer to [FAQs](https://trtc.io/document/51024?platform=android&product=call#create_userID).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5dbee027668811efbd54525400f69702.png)

### Answering a Call

After the recipient completes login, the caller can initiate a call, and the recipient will receive the call invitation with ringtone and vibration.

## More Features

### Enabling Floating Window

You can enable/disable the floating window feature by calling [enableFloatWindow](https://www.tencentcloud.com/document/product/647/51015#enableFloatWindow). Enable this feature when initializing the TUICallKit component, with the default status being Off (false). Click the floating window button in the top-left corner of the call interface to minimize the call interface into a floating window format.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/99450b5ab32b11f099275254005ef0f7.png)

Use `enableFloatWindow(enable: boolean)` to enable/disable the floating window.

```
TUICallKitAPI.enableFloatWindow(true)
```

### Setting incoming call ringtone

You can configure the default ringtone and mute mode for incoming calls using the following methods:

- **Set the default ringtone:**Use the setCallingBell interface to set the ringtone that the callee receives.
  - Only local MP3 format file addresses can be used, ensuring that the file is accessible.
  - To reset the ringtone, pass in an empty string for filePath.
  - Use the ES6 import method to import the ringtone file.

```
import
```

- **Mute mode for incoming calls:** Use the enableMuteMode interface to configure it.

```
try {  await TUICallKitAPI.enableMuteMode(enable: boolean);} catch (error: any) {  alert(`[TUICallKit] enableMuteMode API failed. Reason: ${error}`);}
```

## Customizing Your UI

### Replacing icons

To replace an icon, source code import is required first. Copy the component to your project (the source code is in TypeScript version).

> **Noteï¼**The Interface Replacing icons Plan is suitable for `Vue3 + TypeScript` and `@trtc/calls-uikit-vue` version number is 3.2.2 or later projects. If you are using other languages or technology stacks, please use the Custom UI Implementation.

1. **Download Source Code**

Vue3

```
npm install @trtc/calls-uikit-vue
```

2. **Copy the source code into your own project, taking copying into the**`src/components/`**directory as an example:**

macOS + Vue3

Windows + Vue3

```
mkdir -p ./src/components/TUICallKit && cp -r ./node_modules/@trtc/calls-uikit-vue/* ./src/components/TUICallKit
```

```
xcopy .\\node_modules\\@trtc\\calls-uikit-vue  .\\src\\components\\TUICallKit /i /e
```

3. **Modify Import Path**

It's necessary to change CallKit to be imported from a local file, as shown below. For other usage details, refer to [TUICallKit Quick Integration](https://trtc.io/document/58484?platform=web&product=call).

```
import { TUICallKit, TUICallKitAPI } from "./components/TUICallKit/src/index";
```

4. **Solve Errors That May Be Caused by Copying Source Code**

If you encounter an error while using the TUICallKit component, please don't worry. In most cases, this is due to inconsistencies between ESLint and TSConfig configurations. You can consult the documentation and configure correctly as required. If you need help, please feel free to contact us, and we will ensure that you can successfully use this component. Here are some common issues:

ESLint Error

TypeScript Error

If the TUICallKit causes an error due to inconsistency with your project's code style, you can block this component directory by adding a `.eslintignore` file in the root directory of your project, for example:

```
# .eslintignoresrc/components/TUICallKit
```

1. If you encounter the 'Cannot find module '../package.json'' error, it's because TUICallKit references a JSON file. You can add the related configuration in tsconfig.json, example:

```
{  "compilerOptions": {    "resolveJsonModule": true  }}
```

For other TSConfig issues, please refer to [TSConfig Reference](https://www.typescriptlang.org/tsconfig).

2. If you encounter the 'Uncaught SyntaxError: Invalid or unexpected token' error, it's because TUICallKit uses decorators. You can add the related configuration in tsconfig.json, example:

```
{  "compilerOptions": {    "experimentalDecorators": true  }}
```

5. **Modify the icon components in the TUICallKit/Components/assets folder**

> **Note:**To ensure the icon color and style remain consistent throughout the application, please keep the icon file name unchanged when replacing.

Desktop

Mobile

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98a7f482b32b11f0bb7b525400bf7822.png)

| Serial number | Resource Path | Description |
| --- | --- | --- |
| 1 | /TUICallKit/Components/assets/button/camera-close.svg | Camera Off icon |
| 2 | /TUICallKit/Components/assets/button/microphone-open.svg | Turn on the mic icon |
| 3 | /TUICallKit/Components/assets/button/speaker-open.svg | Turn on the speaker icon |
| 4 | /TUICallKit/Components/assets/button/desktop/inviteUser.svg | Invite user icon during call |
| 5 | /TUICallKit/Components/assets/button/hangup.svg | Hang Up Call icon |
| 6 | /TUICallKit/Components/assets/button/desktop/minimize.svg | Miniaturize Icon |
| 7 | /TUICallKit/Components/assets/button/desktop/fullScreen.svg | Full Screen Icon |

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98926282b32b11f0995e525400454e06.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98a6be1db32b11f0bd1d5254001c06ec.png)

| Serial number | Resource Path | Description |
| --- | --- | --- |
| 1 | /TUICallKit/Components/assets/button/mobile/minimize.svg | Miniaturize Icon |
| 2 | /TUICallKit/Components/assets/button/hangup.svg | Hang Up Call icon |
| 3 | /TUICallKit/Components/assets/button/accept.svg | Accept icon |
| 4 | /TUICallKit/Components/assets/button/microphone-open.svg | Turn on the mic icon |
| 5 | /TUICallKit/Components/assets/button/speaker-open.svg | Turn on the speaker icon |
| 6 | /TUICallKit/Components/assets/button/camera-close.svg | Camera Off icon |
| 7 | /TUICallKit/Components/assets/button/switchCamera.svg | Switch Camera Icon |

### Button Hiding

Invoke the [hideFeatureButton](https://www.tencentcloud.com/document/product/647/51015#hideFeatureButton) interface to hide buttons, currently supporting Camera, Microphone, SwitchCamera, InviteUser. For details, see the enumeration type [FeatureButton](https://www.tencentcloud.com/document/product/647/51015#FeatureButton).

Taking the hiding of the **Camera Button** as an example.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98a530ffb32b11f099275254005ef0f7.png)

Vue3

```
import { TUICallKitAPI, FeatureButton } from "@trtc/calls-uikit-vue";TUICallKitAPI.hideFeatureButton(FeatureButton.Camera);
```

### Custom Call Background Image

The call background image appears when the camera is turned off during a voice or video call. Modify the local user's call interface background image by calling [setLocalViewBackgroundImage](https://www.tencentcloud.com/document/product/647/51015#setLocalViewBackgroundImage), and modify the remote user's call interface background image with [setRemoteViewBackgroundImage](https://www.tencentcloud.com/document/product/647/51015#setRemoteViewBackgroundImage).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9900bc1eb32b11f097b152540099c741.png)

Vue3

```
import { TUICallKitAPI } from "@trtc/calls-uikit-vue";TUICallKitAPI.setLocalViewBackgroundImage('http://xxx.png');TUICallKitAPI.setRemoteViewBackgroundImage('remoteUserId', 'http://xxx.png');
```

### Set Layout

> **Noteï¼****Only available for 1V1 video calls.**

Use [setLayoutMode](https://www.tencentcloud.com/document/product/647/51015#setLayoutMode) to set the call interface layout, currently only supports LocalInLargeView and RemoteInLargeView, see the [LayoutMode](https://www.tencentcloud.com/document/product/647/51015#LayoutMode) enum for details.

1. LocalInLargeView layout, with the local user in the large window:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9902171fb32b11f097b152540099c741.png)

2. RemoteInLargeView layout, with the remote user in the large window:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98b65d68b32b11f0a6a2525400e889b2.png)

Vue3

```
import { TUICallKitAPI, LayoutMode } from "@trtc/calls-uikit-vue";TUICallKitAPI.setLayoutMode(LayoutMode.LocalInLargeView);
```

### Set the initial state of the camera

Use [setCameraDefaultState](https://www.tencentcloud.com/document/product/647/51015#setCameraDefaultState) to set the initial state of the camera button, currently supports Enabled and Off.

Taking the default Off state of the camera as an example:

Vue3

```
import { TUICallKitAPI } from "@trtc/calls-uikit-vue";TUICallKitAPI.setCameraDefaultState(false);
```

## FAQs

If you encounter any issues during integration and use, please refer to [Frequently Asked Questions](https://www.tencentcloud.com/document/product/647/51022).

## Contact Us

If you have any suggestions or feedback, please contact `info_rtc@tencent.com`.


---
*Source: [https://trtc.io/document/50993](https://trtc.io/document/50993)*
