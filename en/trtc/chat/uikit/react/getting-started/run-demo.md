# Run Demo

This document introduces how to quickly run through the Chat Demo to experience sending text, voice, and video messages.

## Quick Experience

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1974df05adb411f0a0a052540099c741.png)

Before local integration, we built a [Demo](https://trtc.io/demo/homepage/#/detail?scene=messenger) you can try online.

## Prerequisites

### Enabling a Service

1. Log in to the [Chat console](https://console.trtc.io/), go to the **application management** page, and click **Create New Application**. If you have an existing application, you can omit the application creation process.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2882e3e3adb411f08bcc5254007c27c5.png)

2. On the **application management** page, obtain the SDKAppID and key information from the SDKAppID column.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/27e7d9bdadb411f09b75525400bf7822.png)

> **Note:**View key info requires identity verification.Key information is sensitive information. To prevent misappropriation, keep it safe and guard against leakage.

3. [Go to the user management page](https://console.trtc.io/chat/account-management), create 2â3 test accounts for experience in C2C chat and group chat capacities.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/27ca22a6adb411f0a68e5254001c06ec.png)

4. userSig info. Click [Chat console > Development tool > userSig tool](https://console.trtc.io/usersig), fill in the created userID to generate userSig.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f29a385c07911f0b4a7525400454e06.png)

### Development Environment Requirement

- React^18.2 || React^19.0.0
- TypeScript
- Node.js >= v18 (recommended: current stable version LTS v22.x)
- npm (version must match Node.js version)
- Git

## Operation Steps

### Get Demo

```
# Run the code in CLI$ git clone https://github.com/Tencent-RTC/TUIKit_React.git# Go to the project$ cd ./TUIKit_React/demos/rtcube-vite-react# Install dependencies of the demo and build chat-uikit-react$ npm install
```

### Run Demo

> **Note:**The correct UserSig issuance method is to integrate the UserSig calculation code into your server and provide an App-oriented API. When UserSig is required, your App can initiate request to the business server to obtain dynamic UserSig. For more details, see [UserSig generation by the server](https://www.tencentcloud.com/document/product/1047/34385).

> **Note:**To respect the copyright of emoji designs, the Chat Demo/TUIKit project does not include cutouts of large emoji elements. Please replace them with your own designs or other emoji packs for which you hold the copyright before officially launching for commercial use. **The default smiley face emoji pack shown below is copyrighted by Tencent RTC**, you can upgrade to [Chat Pro Plus Edition and Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it for free.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fa73da7661f111f091585254001c06ec.png)

```
# Launch the projectnpm run dev
```

After running the program, click the "Experience Chat" card to enter the login page. Enter the obtained SDKAppID, userID, and secretKey to experience the chat function.

## Experience one-on-one chat

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/43baddd5b63711f0a808525400bf7822.png)

## Integrating Chat-Uikit-React

If you want to integrate chat-uikit-react into your project, go to [Integrate chat-uikit-react](https://www.tencentcloud.com/zh/document/product/1047/50055).

## Communication and Feedback

Join the [Telegram Technical Exchange Group](https://t.me/tencent_imsdk) or [WhatsApp communication group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik) to enjoy support from professional engineers and solve your problems.


---
*Source: [https://trtc.io/document/45912](https://trtc.io/document/45912)*
