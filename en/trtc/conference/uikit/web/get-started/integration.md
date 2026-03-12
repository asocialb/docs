# Integration

This article will guide you through a quick integration of TUIRoomKit components. You will go through several key steps in less than 10 minutes and end up with a full user interface for multiplayer conferencing.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bf302197021d11efaa01525400ae4d13.png)

## TUIRoomKit Demo Experience

You can visit our online [TUIRoomKit demo](https://trtc.io/demo/homepage/#/detail?scene=roomkit) to experience more features of TUIRoomKit.

You can also visit [Github](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/Web) to download the TUIRoomKit code and refer to the README.md file to run the TUIRoomKit Web sample project.

## Environment Preparation

- Node.js version: Node.js â¥ 16.19.1 (It is recommended to use the official LTS version, and the npm version should match the node version).
- Modern browser, [supporting WebRTC APIs](https://caniuse.com/?search=webrtc).

## Integrating TUIRoomKit Component

> **Noteï¼**If you **don't have a vue project**, you can directly refer to the [Run Sample Demo](https://trtc.io/document/60441?platform=web&product=conference) run through [Github](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/Web) sample project.

If you need to integrate it into an existing project, please follow the steps below for integration.

### **Step 1: Install Dependencies**

Vue3

Vue2

```
npm install @tencentcloud/roomkit-web-vue3 pinia --save
```

```
# Please note that the required Vue version is >= 2.7.16. If the installation fails, # please check if your Vue version is supported.npm install @tencentcloud/roomkit-web-vue2.7 pinia
```

> **Noteï¼**TUIRoomKit package provides a pre-meeting preview component, an in-meeting component, and methods for starting meetings, joining meetings, and fine-tuning the interface. For more, see [RoomKit API](https://trtc.io/document/54880?platform=web&product=conference). If these APIs don't meet your business needs, you can refer to [UIKit source code export](https://trtc.io/document/54851?platform=web&product=conference#method-2.3A-modify-the-uikit-source-code) for accessing the TUIRoomKit source code.

### Step 2: Project Engineering Configuration

**Register Pinia**: TUIRoom uses Pinia for room data management, and you need to register Pinia in the project entry file. The project entry file is `src/main.ts`.

Vue3

Vue2

```
// src/main.tsimport { createPinia } from 'pinia';const app = createApp(App);// register piniaapp.use(createPinia()); app.mount('#app')
```

```
// src/main.tsimport { createPinia, PiniaVuePlugin } from 'pinia';Vue.use(PiniaVuePlugin);const pinia = createPinia();new Vue({  pinia,  render: h => h(App),}).$mount('#app');
```

### Step 3: Import the TUIRoom component

> **Note:**Import the ConferenceMainView component, which is by default in the [permanent mode](https://www.tencentcloud.com/document/product/647/54880#1489e306-bc17-4bd2-b0bb-f4b8e3efad51) (the component is always displayed, and its display and hiding are not controlled internally. If the business end does not control it, the component will always remain displayed).

Vue3

Vue2

```
<template>  <ConferenceMainView></ConferenceMainView></template><script setup>import { ConferenceMainView } from '@tencentcloud/roomkit-web-vue3';</script>
```

```
<template>  <ConferenceMainView></ConferenceMainView></template><script>import { ConferenceMainView } from '@tencentcloud/roomkit-web-vue2.7';export default {  components: {    ConferenceMainView,  },};</script>
```

### Step 4: Logging into the TUIRoomKit Component

Before initiating a meeting, it is necessary to invoke the [login](https://www.tencentcloud.com/document/product/647/54880#5a429689-e07a-4c01-bfc6-bfb67f7f5b7f) interface for authentication. To obtain the `SDKAppID, userIdï¼userSig`, refer to the [service activation](https://www.tencentcloud.com/document/product/647/59973#).

```
import { conference } from '@tencentcloud/roomkit-web-vue3';await conference.login({      sdkAppId: 0,  // Replace with your sdkAppId  userId: '',  // Replace with your userId  userSig: '',  // Replace with your userSig});
```

| **Parameter** | **Type** | **Note** |
| --- | --- | --- |
| userID | String | **Unique identifier of the user,**`defined by you`**,**it is allowed to contain only upper and lower case letters (a-z, A-Z), numbers (0-9), underscores, and hyphens. |
| SDKAppID | Number | The unique identifier for the audio and video application created in the [Tencent RTC Console](https://console.trtc.io/). |
| SDKSecretKey | String | The SDKSecretKey of the audio and video application created in the [Tencent RTC Console](https://console.trtc.io/). |
| userSig | String | A security protection signature used for user log in authentication to confirm the user's identity and prevent malicious attackers from stealing your cloud service usage rights. |

> **Explanation of userSig:****Development environment:** If you are running a demo locally and developing debugging, you can use the `genTestUserSig` (Refer to Step 3.2) function in the debug file to generate a `userSig`. In this method, SDKSecretKey is vulnerable to decompilation and reverse engineering. Once your key is leaked, attackers can steal your Tencent Cloud traffic.**Production environment:**If your project is going live, please use the [Server-side Generation of UserSig](https://trtc.io/document/35166) method.

### Step 5: Initiate a new meeting

The conference host can initiate a new conference by calling the [start](https://www.tencentcloud.com/document/product/647/54880#b0bf2a3b-428c-474f-9a0e-271c7c3b6bfd) interface. Other participants can refer to the description in [step 6](https://www.tencentcloud.com/document/product/647/54845#061c9593-1112-4763-aff2-7289b3af0c41) and call the join interface to [join](https://www.tencentcloud.com/document/product/647/54880#b08d0951-c1f4-4db4-a84d-8414b853d0f1) the conference.

```
// Note the package name, if you are using the vue2 version change the package name to @tencentcloud/roomkit-web-vue2.7import { conference } from '@tencentcloud/roomkit-web-vue3';const startConference = async () => {    await conference.login({          sdkAppId: 0,  // Replace with your sdkAppId      userId: '',  // Replace with your userId      userSig: '',  // Replace with your userSig    });    await conference.start('123456', {      roomName: 'TestRoom',      isSeatEnabled: false,      isOpenCamera: false,      isOpenMicrophone: false,    });}startConference()
```

### Step 6: Enter an existing meeting

Participants can [join](https://www.tencentcloud.com/document/product/647/54880#b08d0951-c1f4-4db4-a84d-8414b853d0f1)the conference initiated by the conference host in [step 5](https://www.tencentcloud.com/document/product/647/54845#7e2fb3c2-2b17-4445-985d-4af641ff66be) by calling the join interface and filling in the corresponding roomId parameter.

```
// Note the package name, if you are using the vue2 version change the package name to @tencentcloud/roomkit-web-vue2.7import { conference } from '@tencentcloud/roomkit-web-vue3';const joinConference = async () => {    await conference.login({          sdkAppId: 0,  // Replace with your sdkAppId      userId: '',  // Replace with your userId      userSig: '',  // Replace with your userSig    });    await conference.join('123456', {      isOpenCamera: false,      isOpenMicrophone: false,    });}joinConference()
```

## Development environment running

1. Execute the development environment command. (Here we take the vue3 + vite default project as an example. The dev instructions of different projects may be different. Please adjust according to your own project)

```
npm run dev
```

2. According to the console prompts, open the page in the browser, such as: http://localhost:3000/.
3. Experience the TUIRoomKit component functions.

## Production environment deployment

1. Package the dist file.

```
npm run build
```

2. Deploy the dist file to the server.

> **Note:**The production environment requires the use of an HTTPS domain name.

## Other documents

- [TUIRoomKit](https://www.tencentcloud.com/document/product/647/54880#)
- [TUIRoom Demo Quick Start](https://github.com/tencentyun/TUIRoom/tree/main/Web)
- [interface customization (TUIRoomKit)](https://www.tencentcloud.com/document/product/647/54851#)
- [common problem](https://www.tencentcloud.com/document/product/647/37340#)

## Communication and feedback

If you have any needs or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/54845](https://trtc.io/document/54845)*
