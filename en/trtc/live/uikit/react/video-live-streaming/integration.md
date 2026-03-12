# Integration

## Feature Preview

TUILiveKit React is a feature-rich web live streaming component that provides comprehensive live streaming capabilities out of the box:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/100c509f116f11f18b07525400ecee81.png)

## **Preparation**

### Activate the Service

Before using TUILiveKit, you'll need to activate the service first. See [Activate Services](https://trtc.io/document/60033?product=live&menulabel=uikit&platform=web) to get a trial version or activate the paid version.

### Environment Requirements

- **Devices**: Camera, microphone, and speakers

### Configuration Requirements

- **Node.js**: â¥ 18.19.1 (Official LTS version recommended, check your current version with `node -v` command)
- **react**: â¥ 18.2.0 and < 19.0.0
- **vite**: â¥ 5.4.0
- **typescript**: â¥ 5.8.3
- **sass**: â¥ 1.77.0

## Code Integration

### **Step 1: Install Dependencies**

Choose your preferred package manager:

npm

pnpm

yarn

```
npm install tuikit-atomicx-react @tencentcloud/uikit-base-component-react --save
```

```
pnpm install tuikit-atomicx-react @tencentcloud/uikit-base-component-react
```

```
yarn install tuikit-atomicx-react @tencentcloud/uikit-base-component-react
```

### Step 2: Complete Login

Completing login is the foundation for using **TUILiveKit**. TUILiveKit features can only be used normally after successful login. Make sure all parameters are configured correctly before proceeding.

> **Note:**While the sample code shows direct login calls, **we strongly recommend calling TUILiveKit's login service only after completing your own user authentication flow**. This prevents business logic conflicts or data inconsistency issues and integrates better with your existing user management and permission systems.

```
// Best practice: Call this login logic immediately after your authentication flow completesimport { useLoginState } from 'tuikit-atomicx-react';const { login, logout } = useLoginState();async function initLogin() {  try {    await login({      SDKAppID: 0,        // SDKAppID - SDKAppID obtained when activating service      userID: '',         // UserID   - User ID      userSig: '',        // userSig  - User signature, see parameter description below for detailed instructions    });  } catch (error) {    console.error('Login failed:', error);  }}
```

**Login API Parameter Description**

| Parameter | Type | Description |
| --- | --- | --- |
| SDKAppID | Int | Get this from [TRTC console > Application management](https://console.trtc.io/app). |
| UserID | String | Unique identifier for the current user. It can only contain letters (a-z, A-Z), numbers (0-9), hyphens (-), and underscores (_). |
| userSig | String | A ticket for TRTC authentication:**Development Environment**: Use `GenerateTestUserSig.genTestSig` locally or the [UserSig Generation Tool](https://console.trtc.io/usersig) to generate temporary credentials.**Production**: Generate UserSig server-side to prevent key exposure. See [Server-Side UserSig Generation](https://www.tencentcloud.com/document/product/647/69883). |

## Next Steps

After completing authentication, you can integrate TUILiveKit's live streaming features. Follow the guides below to implement audience viewing, live lists, and more:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Audience Viewing** | Allow viewers to watch live streams, request co-hosting, view room information, see online audience, and interact via chat. | [Audience Viewing (React)](https://www.tencentcloud.com/document/product/647/77815) |
| **Live Room List** | Display available live rooms with room information and status. | [Live List (React)](https://www.tencentcloud.com/document/product/647/77816) |
| **Host Streaming** | Enable hosts to start broadcasts with pre-stream setup and in-stream interactions | [Host Streaming (Vue3)](https://www.tencentcloud.com/document/product/647/73741)(React support coming soon) |

## FAQ

### Do I need to call login every time I enter a room?

No. You typically only need to call `login()` once. We strongly recommend integrating the `login()` and `logout()` functions returned by `useLoginState()` with your application's authentication system.

### Why is HTTPS required for production deployments?

When deploying your application to production, you must use an **HTTPS domain**. TUILiveKit relies on WebRTC technology and requires access to users' cameras, microphones, and speakers. Browsers enforce HTTPS to protect user privacy and security when accessing these sensitive devices.

> **Note:****Protocol Requirements for Production:**Due to browser security policy restrictions, using WebRTC capabilities has strict requirements for page access protocols. Please refer to the following table for application development and deployment.**Environment****Protocol****Receive Stream****Send Stream****Screen Sharing****Notes****Production**HTTPSâââRecommended**Production**HTTPâââ-**Local Development**http://localhostâââRecommended**Local Development**http://127.0.0.1âââ-**Local Development**http://[Local IP]âââ-**Local Development**file://âââ-


---
*Source: [https://trtc.io/document/77813](https://trtc.io/document/77813)*
