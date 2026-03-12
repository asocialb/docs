# Integration

## Feature Overview

**TUILiveKit** is a comprehensive live streaming component. Once integrated, it allows you to quickly implement the following functional modules:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1728c8fe978f11f0ad595254007c27c5.png)

## Preparations

### Service Activation

Before using TUILiveKit, you need to [Activate Services](https://trtc.io/document/60033?product=live&menulabel=uikit&platform=web) in the Tencent Cloud console and receive a trial version or activate a paid version.

### Environmental requirements

- **Vue 3 + Composition API:**Leverage the latest Vue 3 features to build high-performance, maintainable applications.
- **TypeScript:**Improve code quality and development efficiency through static type checking.
- **SCSS Module:**Implement modular style management to effectively avoid style conflicts.

### Code Integration

#### Step 1: Install Dependencies

You can install dependencies using any of the following methods:

npm

pnpm

yarn

```
npm install tuikit-atomicx-vue3 @tencentcloud/uikit-base-component-vue3 --save
```

```
pnpm install tuikit-atomicx-vue3 @tencentcloud/uikit-base-component-vue3
```

```
yarn install tuikit-atomicx-vue3 @tencentcloud/uikit-base-component-vue3
```

#### Step 2: Complete login

```
import { useLoginState } from 'tuikit-atomicx-vue3';const { login } = useLoginState();async function initLogin() {  try {    await login({      sdkAppId: 0,        // SDKAppId, refer to step 1 to obtain      userId: '',         // UserID, refer to step 1 to obtain      userSig: '',        // userSig, refer to step 1 to obtain    });  } catch (error) {    console.error('Login Error:', error);  }}
```

**Login API Parameter Description**

| Parameter | Type | Description |
| --- | --- | --- |
| SDKAppID | Int | Get this from [TRTC console > Application management](https://console.trtc.io/app). |
| UserID | String | Unique identifier for the current user. It can only contain letters (a-z, A-Z), numbers (0-9), hyphens (-), and underscores (_). |
| userSig | String | A ticket for TRTC authentication:**Development Environment**: Use `GenerateTestUserSig.genTestSig` locally or the [UserSig Generation Tool](https://console.trtc.io/usersig) to generate temporary credentials.**Production**: Generate UserSig server-side to prevent key exposure. See [Server-Side UserSig Generation](https://www.tencentcloud.com/document/product/647/69883). |

#### Step 3: Functional Experience

Congratulations! You've successfully integrated the live video component and logged in. Next, you can start broadcasting, have viewers watch, or implement other live streaming features. For details, see the table below.

| **Function** | **Description** | **Experience Link** |
| --- | --- | --- |
| **Host Streaming** | The live streamer's entire live streaming process is supported, including pre-streaming preparation and post-streaming interactions. | [Host Streaming](https://www.tencentcloud.com/document/product/647/73741) |
| **Audience Viewing** | Viewers can enter the live streamer's room to watch the live stream, connect to the microphone, view live stream room information, view online viewers, and display comments. | [Audience Viewing](https://www.tencentcloud.com/document/product/647/73747) |
| **Live Streaming Kit** | A comprehensive set of out-of-the-box live streaming interfaces and features are provided, including video source control, microphone connection, audience interaction, live streaming in both landscape and portrait modes, and viewer management. | [Live Streaming Kit](https://www.tencentcloud.com/document/product/647/73792) |
| **Live Streaming List** | The live stream list interface and features include a live stream list and room information display. | [Live Streaming List](https://www.tencentcloud.com/document/product/647/73760) |

### FAQ

If you need to deploy the project's packaged dist file, you must use an HTTPS domain name in the production environment.

> **Note:****Protocol Requirements for Production:**Due to browser security policy restrictions, using WebRTC capabilities has strict requirements for page access protocols. Please refer to the following table for application development and deployment.**Environment****Protocol****Receive Stream****Send Stream****Screen Sharing****Notes****Production**HTTPSâââRecommended**Production**HTTPâââ-**Local Development**http://localhostâââRecommended**Local Development**http://127.0.0.1âââ-**Local Development**http://[Local IP]âââ-**Local Development**file://âââ-


---
*Source: [https://trtc.io/document/66938](https://trtc.io/document/66938)*
