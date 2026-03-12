# Integration

This article will guide you through a quick integration of TUIRoomKit components. You will go through several key steps in less than 10 minutes and end up with a full user interface for multiplayer conferencing.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/70d5301470aa11ef92db52540055f650.png)

## TUIRoomKit Demo Experience

You can click [Mac OS Version](https://web.sdk.qcloud.com/trtc/electron/download/solution/TUIRoomKit/TUIRoomKit-Electron-mac-latest.zip) and [Windows Version](https://web.sdk.qcloud.com/trtc/electron/download/solution/TUIRoomKit/TUIRoomKit-Electron-windows-latest.zip) to download and experience more features of TUIRoomKit Electron.
You can click [GitHub](https://github.com/tencentyun/TUIRoomKit) to download the TUIRoomKit code, and refer to the README.md document in the code repository to run through the TUIRoomKit Electron sample project.

## Environment preparations

- Node.js version: Node.js â¥ 16.19.1 (Using the official LTS version is recommended; please ensure the npm version matches the node version).
- **NPM Package Integration**
  - Vue3 development environment, integrate [@tencentcloud/room-electron-vue3](https://www.npmjs.com/package/@tencentcloud/roomkit-electron-vue3) NPM package.
  - Vue2.7 development environment: Integrate [@tencentcloud/roomkit-electron-vue2.7](https://www.npmjs.com/package/@tencentcloud/roomkit-electron-vue2.7) NPM package.
- **Source Code Integration**
  - Vue3 + TypeScript development environment: Copy source code from [@tencentcloud/room-electron-vue3](https://www.npmjs.com/package/@tencentcloud/roomkit-electron-vue3) NPM package.
  - Vue2.7 + TypeScript development environment: Copy source code from [@tencentcloud/roomkit-electron-vue2.7](https://www.npmjs.com/package/@tencentcloud/roomkit-electron-vue2.7) NPM package.
- **Template Project**
  - Electron + vite + vue3 [electron-vite-vue](https://github.com/electron-vite/electron-vite-vue)

## Integrating TUIRoomKit Component

If **you don't have a Vue project**, you can go to [GitHub](https://github.com/Tencent-RTC/TUIRoomKit/tree/main) to download the TUIRoomKit code, and refer to the code repository's README.md to run the TUIRoomKit Electron sample project.

If you need to integrate it into an existing project, please follow the steps below.

### **Step 1: Install dependencies**

Vue3

Vue2

```
npm install @tencentcloud/roomkit-electron-vue3 pinia@2.0.24 --save
```

```
# Note that Vue version >= 2.7.16 is required here. If installation fails, please check if your Vue version is supportednpm install @tencentcloud/roomkit-electron-vue2.7 pinia
```

> **Noteï¼**If you are integrating by downloading the template project [electron-vite-vue](https://github.com/electron-vite/electron-vite-vue), you need to switch the template project to v1.0.0, you can refer to the following instruction:git clone https://github.com/electron-vite/electron-vite-vue.git cd electron-vite-vuegit checkout v1.0.0

### **Step 2: Configure the project**

#### **1. Adjusting content security policies**

In Mac system, the default content security policy settings will cause an error when loading TUIRoomKit components. In order to prevent TUIRoom pages from not loading or interface calls from reporting errors, you can adjust the content security policy. The adjustment file is `packages/renderer/index.html` .

```
<head>  <meta charset="UTF-8" />  <link rel="icon" href="/favicon.ico" />  <meta name="viewport" content="width=device-width, initial-scale=1.0" />  <!-- Modify this setting for Mac -->  <meta http-equiv="Content-Security-Policy" content="script-src 'self' 'unsafe-inline' 'unsafe-eval'; worker-src 'self' blob:;"/>  <title>Vite App</title></head>
```

#### **2. Register Pinia**

TUIRoom uses Pinia for room data management, so you need to register Pinia in the entry file of the project. The entry file is the `src/main.ts` file.

Vue3

Vue2

```
// src/main.ts fileimport { createPinia } from 'pinia';const app = createApp(App);// Register piniaapp.use(createPinia()); app.mount('#app')
```

```
// src/main.ts fileimport { createPinia, PiniaVuePlugin } from 'pinia';Vue.use(PiniaVuePlugin);const pinia = createPinia();new Vue({  pinia,  render: h => h(App),}).$mount('#app');
```

#### **3. Configure vite.config.ts**

To unify code style and import trtc-electron-sdk through import in the UI layer (otherwise, it must be imported via require), you need to configure in `packages/renderer/vite.config.ts`. Please replace the content in resolve with the following configuration items, refer to the file [packages/renderer/vite.config.ts](https://github.com/Tencent-RTC/TUIRoomKit/blob/main/Electron/example/vue3/packages/renderer/vite.config.ts) for details.

> **Noteï¼**If your project is packaged with vite, please follow the steps below to configure it. The reason is that vite only supports ES6 modules by default, and trtc-electron-sdk needs to interface with the Node.js API, which is a Common JS module, so this step is for module type compatibility. If your project is packaged with webpack, you can skip the vite.config.ts step.

```
// vite.config.tsexport default defineConfig({ // ... plugins: [   resolve({      'trtc-electron-sdk': `          const TRTCCloud = require("trtc-electron-sdk");          const TRTCParams = TRTCCloud.TRTCParams;          const TRTCAppScene = TRTCCloud.TRTCAppScene;          const TRTCVideoStreamType = TRTCCloud.TRTCVideoStreamType;          const TRTCScreenCaptureSourceType = TRTCCloud.TRTCScreenCaptureSourceType;          const TRTCVideoEncParam = TRTCCloud.TRTCVideoEncParam;          const Rect = TRTCCloud.Rect;          const TRTCAudioQuality = TRTCCloud.TRTCAudioQuality;          const TRTCScreenCaptureSourceInfo = TRTCCloud.TRTCScreenCaptureSourceInfo;          const TRTCDeviceInfo = TRTCCloud.TRTCDeviceInfo;          const TRTCVideoQosPreference = TRTCCloud.TRTCVideoQosPreference;          const TRTCQualityInfo = TRTCCloud.TRTCQualityInfo;          const TRTCQuality = TRTCCloud.TRTCQuality;          const TRTCStatistics = TRTCCloud.TRTCStatistics;          const TRTCVolumeInfo = TRTCCloud.TRTCVolumeInfo;          const TRTCDeviceType = TRTCCloud.TRTCDeviceType;          const TRTCDeviceState = TRTCCloud.TRTCDeviceState;          const TRTCBeautyStyle = TRTCCloud.TRTCBeautyStyle;          const TRTCVideoResolution = TRTCCloud.TRTCVideoResolution;          const TRTCVideoResolutionMode = TRTCCloud.TRTCVideoResolutionMode;          const TRTCVideoMirrorType = TRTCCloud.TRTCVideoMirrorType;          const TRTCVideoRotation = TRTCCloud.TRTCVideoRotation;          const TRTCVideoFillMode = TRTCCloud.TRTCVideoFillMode;          const TRTCRoleType = TRTCCloud.TRTCRoleType;          const TRTCScreenCaptureProperty = TRTCCloud.TRTCScreenCaptureProperty;          export {             TRTCParams,            TRTCAppScene,            TRTCVideoStreamType,            TRTCScreenCaptureSourceType,            TRTCVideoEncParam,            Rect,            TRTCAudioQuality,            TRTCScreenCaptureSourceInfo,            TRTCDeviceInfo,            TRTCVideoQosPreference,            TRTCQualityInfo,            TRTCStatistics,            TRTCVolumeInfo,            TRTCDeviceType,            TRTCDeviceState,            TRTCBeautyStyle,            TRTCVideoResolution,            TRTCVideoResolutionMode,            TRTCVideoMirrorType,            TRTCVideoRotation,            TRTCVideoFillMode,            TRTCRoleType,            TRTCQuality,            TRTCScreenCaptureProperty,          };          export default TRTCCloud.default;        `,    }), ]});
```

### Step 3: **Reference**TUIRoomKit**Component**

> **Note:**Introduce the ConferenceMainView component, which is defaulted to [Permanent Mode](https://www.tencentcloud.com/document/product/647/54885#1489e306-bc17-4bd2-b0bb-f4b8e3efad51) (the component is always displayed, its visibility is not controlled internally. Without business side control, the component will remain visible).

Vue3

Vue2

```
<template>  <ConferenceMainView></ConferenceMainView></template><script setup>import { ConferenceMainView } from '@tencentcloud/roomkit-electron-vue3';</script>
```

```
<template>  <ConferenceMainView></ConferenceMainView></template><script>import { ConferenceMainView } from '@tencentcloud/roomkit-electron-vue2.7';export default {  components: {    ConferenceMainView,  },};</script>
```

### Step 4: Log in to TUIRoomKit Component

Before starting a meeting, you need to call the [login](https://www.tencentcloud.com/document/product/647/54885#5a429689-e07a-4c01-bfc6-bfb67f7f5b7f) interface to log in and get sdkAppId, userId, userSig as described in [Activate Service](https://www.tencentcloud.com/document/product/647/59973#).

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.login({        sdkAppId: 0,  // Replace with your sdkAppId    userId: '',  // Replace with your userId    userSig: '',  // Replace with your userSig});
```

| Parameter | Type | Description |
| --- | --- | --- |
| userID | String | Customers can customise the user ID according to their business, only case-sensitive English letters (a-z A-Z), numbers (0-9) and underscores and hyphens are allowed. |
| sdkAppID | int | Unique identification SDKAppID of the [Activate the Service](https://www.tencentcloud.com/document/product/647/59973#) created in the real-time audio/video TRTC console. |
| secretKey | String | SDKSecretKey of the [Activate the Service](https://www.tencentcloud.com/document/product/647/59973#) created in the real-time audio/video TRTC console. |
| userSig | String | A security protection signature used to authenticate a user's login credentials, confirm that the user is genuine, and stop malicious attackers from stealing your access to cloud services. |

> **Noteï¼**Development environment: If you are in the local development and debugging stage, you can use the local **GenerateTestUserSig.genTestSig** function to generate a userSig. The SDKSecretKey in this method can be easily decompiled and cracked in reverse, and once your key is leaked, attackers can steal your Tencent Cloud traffic.Production environment: If your project is to be released online, please use the [server-side UserSig](https://www.tencentcloud.com/document/product/647/41664) generation method.

### Step Five: Launch a New Meeting

The meeting host can initiate a new meeting by invoking the [start](https://www.tencentcloud.com/document/product/647/54885#b0bf2a3b-428c-474f-9a0e-271c7c3b6bfd) interface. Other participants can refer to the description in [Step Six](https://www.tencentcloud.com/document/product/647/54844#061c9593-1112-4763-aff2-7289b3af0c41) and join the meeting by calling the [join](https://www.tencentcloud.com/document/product/647/54885#b08d0951-c1f4-4db4-a84d-8414b853d0f1) interface.

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';const startConference = async () => {    await conference.login({          sdkAppId: 0,  // Replace with your sdkAppId      userId: '',  // Replace with your userId      userSig: '',  // Replace with your userSig    });    await conference.start('123456', {      roomName: 'TestRoom',      isSeatEnabled: false,      isOpenCamera: false,      isOpenMicrophone: false,    });}startConference()
```

### Step Six: Enter an Existing Meeting

Participants can join a meeting initiated by the host in [Step Five](https://www.tencentcloud.com/document/product/647/54844#7e2fb3c2-2b17-4445-985d-4af641ff66be) by invoking the [join](https://www.tencentcloud.com/document/product/647/54885#b08d0951-c1f4-4db4-a84d-8414b853d0f1) interface and filling in the corresponding roomId parameter.

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';const joinConference = async () => {    await conference.login({          sdkAppId: 0,  // Replace with your sdkAppId      userId: '',  // Replace with your userId      userSig: '',  // Replace with your userSig    });    await conference.join('123456', {      isOpenCamera: false,      isOpenMicrophone: false,    });}joinConference()
```

## Development Environment Operation

1. Execute the development environment command. (As an example, this uses a vue3 + vite default project, however, the dev command may differ for different projects. Please adjust according to your own project)

```
npm run dev
```

> **Note:**If there are eslint errors in the src/TUIRoom directory during execution, you can add the /src/TUIRoom/ path to the .eslintignore file to ignore the eslint checks.

2. Experience the TUIRoomKit component features.

## Production environment deployment

Packaging of projects

```
npm run build
```

## Common Problems

### **If you have problems with vue version mismatch when installing dependencies in step 1, how to solve it?**

ou need to fix the **vue** version to **3.3.13** in the **package.json** file

### **If you get an app crash during the runtime phase, how to solve it?**

**The issue may be caused by the inability to obtain camera and microphone permissions.**
Solution:

1. Please check whether your camera or microphone device is working properly, and whether it is occupied by other apps.
2. In **/packages/main/index.ts**, comment out the call of `checkAndApplyDevicePrivilege `method, so that you can skip the device privilege check.

### **If you encounter the following error in the runtime or packaging phase, how to solve it?**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0ac2519e726611ef82535254002693fd.png)

**y**You need to enable the **allowJs** option in the **tsconfig.json** file:

```
// tsconfig.json{    "compilerOptions": {      "allowJs": true    // ...Other options  }    // ...Other options}
```

### **If you encounter the following error during the runtime or packaging stage, how to solve it?**

****

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0755158970ad11efbd54525400f69702.png)

You need to add the following content to the **index.html** file:

```
// index.html<head>  ....  <script>const exports = module.exports;</script><head>
```

- [TUIRoomKit](https://www.tencentcloud.com/document/product/647/54885#)
- [TUIRoom Demo Quick Run](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/Electron)
- [UI Customization (TUIRoomKit)](https://www.tencentcloud.com/document/product/647/54847#)
- [Frequently Asked Questions](https://www.tencentcloud.com/document/product/647/57419#)

## Communication and feedback

If you have any needs or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/54844](https://trtc.io/document/54844)*
