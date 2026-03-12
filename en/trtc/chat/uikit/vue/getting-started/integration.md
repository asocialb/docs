# Integration

TUIKit is a UI component library based on the Chat SDK. It enables quick implementation of chat, session, search, Relationship Chain, group, and other features through UI components. This article introduces how to rapidly integrate TUIKit and implement core features.

Or, if you prefer a faster and more automated approach, you can refer to [Get started with AI integration](https://www.tencentcloud.com/document/product/1047/72277) to streamline the process.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/71eafaeab5f611eeb395525400461a83.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/78f28c36b5f611ee9d74525400c26da5.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8380eff8b5f611eea201525400170219.png)

## Key Concepts

TUIKit is mainly divided into several UI subcomponents: TUIChat, TUIConversation, TUIGroup, TUIContact, and TUISearch. Each UI component is responsible for showing different content.

1. TUIChat provides a session page, including a message list, header, and input box.
2. TUIConversation provides a session list page, including a conversation list, group creation, and C2C Chat.
3. TUIGroup provides a group chat management page, including group chat management and group member management.
4. TUIContact provides a contact page, including a contact list and friend requests.
5. TUISearch provides a cloud search page.

## Prerequisites

- Vue (fully supports Vue2 & Vue3, please choose when accessing below the matched Vue version access guide for accessing)
- TypeScript  (Should your project be based on JavaScript, please proceed to [JS project integrate](https://www.tencentcloud.com/document/product/1047/58644#84b6b984-9573-4dd4-a2f8-bcdcd2cabce2) to set up a progressive support for TypeScript)
- sass (sass version â¤ 1.77.4, sass-loader version â¤ 10.1.1)
- node(node.js â¥ 18.0.0)
- npm (version should match node version)

## Integration Steps

### Step 1. Create a project

TUIKit supports the use of vite or vue-cli to create project engineering, configuring Vue3/Vue2 with TypeScript and sass. The following is several project setup examples:

vite

vue-cli

> **Note:**Vite requires [**Node.js**](https://nodejs.org/en/)**version 18+ or 20+.** When your package manager issues a warning, please note to upgrade your Node Version. For details, refer to [vite official website](https://cn.vitejs.dev/guide/).

Create a project using vite, configure Vue + TypeScript as shown in the figure below.

```
npm create vite@5
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/769c3cdeb57411f09a6b525400454e06.png)

Switch to the project directory, then install the project dependencies:

```
cd chat-examplenpm install
```

Install the required sass environment dependency for TUIKit:

```
npm i -D sass@1.77.0 sass-loader@10.1.1
```

Add the following compilation rule to the root directory file `tsconfig.app.json`:

typescript â¥ 5.0.0

typescript < 5.0.0

```
{  ...  "compilerOptions": {    ...    "verbatimModuleSyntax": false,  }}
```

```
{  ...  "compilerOptions": {    ...    "importsNotUsedAsValues": "preserve",  }}
```

> **Note:**If your `tsconfig.json` already has `references` configuration, such as the official vite auto-configured `"./tsconfig.app.json"` and `"./tsconfig.node.json"`, due to the characteristics of `references`, the `tsconfig.json` itself merely serves as a reference file for rules. At this point, directly configuring the following rules in `tsconfig.json` is invalid. You need to add the rules to the actual `references` corresponding file. The following is a specific example:Error Writing FormatCorrect Writing StyleWhen the tsconfig.json file has existing references configuration, declaring the following rules directly in tsconfig.json is invalid.When the tsconfig.json file has existing references configuration, the following rules must be declared in the corresponding references internal file. Below is the configuration of the following rules in the root directory `tsconfig.app.json` file within references![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/82641b72b57411f0a6c652540044a08e.png).

> **Note:**Note: Be sure to ensure your **@vue/cli version is 5.0.0** or higher. You can use the following example code to upgrade your @vue/cli version to v5.0.8.

Create a project using vue-cli, configure Vue2 / Vue3 + TypeScript + sass.

If you have not installed vue-cli or the version is lower than 5.0.0, you can install it in terminal or cmd in the following ways:

```
npm install -g @vue/cli@5.0.8 sass@1.77.0 sass-loader@10.1.1
```

Create a project using vue-cli and choose the selected configuration in the figure below.

```
vue create chat-example
```

Ensure the configuration selection as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/76affbd2b57411f0a6c652540044a08e.png)

After creation, switch to the project directory:

```
cd chat-example
```

If you are using vue 2, configure the environment based on your vue version. Ignore it for vue 3 projects.

vue2.7

Vue 2.6 and Below

```
npm i vue@2.7.9 vue-template-compiler@2.7.9
```

```
npm i @vue/composition-api unplugin-vue2-script-setup vue@2.6.14 vue-template-compiler@2.6.14
```

### Step 2. Download the TUIKit component

Download the TUIKit component through [npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-vue). To facilitate your subsequent expansion, it is recommended that you copy the TUIKit component to the src directory of your project:

macOS

Windows

```
npm i @tencentcloud/chat-uikit-vuemkdir -p ./src/TUIKit && rsync -av --exclude={'node_modules','package.json','excluded-list.txt'} ./node_modules/@tencentcloud/chat-uikit-vue/ ./src/TUIKit
```

```
npm i @tencentcloud/chat-uikit-vue
```

```
xcopy .\\node_modules\\@tencentcloud\\chat-uikit-vue .\\src\\TUIKit /i /e /exclude:.\\node_modules\\@tencentcloud\\chat-uikit-vue\\excluded-list.txt
```

### Step 3. Import TUIKit component

##### On the page where you want to display it, simply import the TUIKit component to use it.

> **Noteï¼**To respect the copyright of emoji designs, the Chat Demo/TUIKit project does not include cutouts of large emoji elements. Please replace them with your own designs or other emoji packs for which you hold the copyright before officially launching for commercial use. **The default smiley face emoji pack shown below is copyrighted by Tencent RTC**, you can upgrade to [Chat Pro Plus Edition and Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it for free.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6a1e26fb97f711ef967c525400a9236a.png)

##### For example, implementing the following code on the App.vue page allows for a quick setup of the chat interface (the following example code supports both Web and H5):

> **Note:**The example code below uses the setup syntax. If your project does not use the setup syntax, please register components according to the standard methods of Vue3/Vue2.

vue3

vue2.7

vue2.6 and below

```
<template>  <div id="app">    <TUIKit :SDKAppID="YOUR_SDKAPPID" userID="YOUR_USERID" userSig="YOUR_USERSIG" />    <TUICallKit class="callkit-container" :allowedMinimized="true" :allowedFullScreen="false" />  </div></template><script lang="ts" setup>import { TUIKit } from './TUIKit';import { TUICallKit } from '@trtc/calls-uikit-vue';</script><style lang="scss"></style>
```

If it is a project built with vite, you can comment out the default invalid style in the project. You can delete useless content as needed.

src/style.css

```
#app {  /* max-width: 1280px; */  margin: 0 auto;  /* padding: 2rem; */  text-align: center;}
```

```
<template>  <div id="app">    <TUIKit :SDKAppID="YOUR_SDKAPPID" userID="YOUR_USERID" userSig="YOUR_USERSIG" />    <TUICallKit class="callkit-container" :allowedMinimized="true" :allowedFullScreen="false" />  </div></template><script lang="ts" setup>import { TUIKit } from './TUIKit';import { TUICallKit } from '@trtc/calls-uikit-vue2';</script><style lang="scss"></style>
```

If it is a project built with vite, you can comment out the default invalid style in the project. You can delete useless content as needed.

src/style.css

```
#app {  /* max-width: 1280px; */  margin: 0 auto;  /* padding: 2rem; */  text-align: center;}
```

```
<template>  <div id="app">   <TUIKit :SDKAppID="YOUR_SDKAPPID" userID="YOUR_USERID" userSig="YOUR_USERSIG" />    <TUICallKit class="callkit-container" :allowedMinimized="true" :allowedFullScreen="false" />  </div></template><script lang="ts" setup>import { TUIKit } from './TUIKit';import { TUICallKit } from '@trtc/calls-uikit-vue2.6';</script><style lang="scss"></style>
```

1. Install dependencies supporting composition-api and script setup, as well as dependencies related to vue2.6.

```
npm i @vue/composition-api unplugin-vue2-script-setup vue@2.6.14 vue-template-compiler@2.6.14
```

2. Import VueCompositionAPI in  `main.ts/main.js`.

```
import VueCompositionAPI from "@vue/composition-api";Vue.use(VueCompositionAPI);
```

3. Add the following in  `vue.config.js` . If the file does not exist, please create it.

```
const ScriptSetup = require("unplugin-vue2-script-setup/webpack").default;module.exports = {  parallel: false, // disable thread-loader, which is not compactible with this plugin  configureWebpack: {    plugins: [      ScriptSetup({        /* options */      }),    ],  },  chainWebpack(config) {    // disable type check and let `vue-tsc` handles it    config.plugins.delete("fork-ts-checker");  },};
```

4. At the end of the  `src/TUIKit/adapter-vue.ts`  file, replace the export source:

```
// Initial notationexport * from "vue";// Replace withexport * from "@vue/composition-api";
```

If it is a project built with vite, you can comment out the default invalid style in the project. You can delete useless content as needed.

src/style.css

```
#app {  /* max-width: 1280px; */  margin: 0 auto;  /* padding: 2rem; */  text-align: center;}
```

### Step 4: Obtain SDKAppID, userID, and userSig

Set the relevant parameters SDKAppID, userID, and corresponding userSig in `<TUIKit>`:

- `SDKAppID` can be obtained through the [Chat Console](https://console.trtc.io/app) in `Applications`:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2cdb24b2353011ef94925254002693fd.png)

- `userID`
  - Click to enter the [Application](https://console.trtc.io/app) you created above. You will see the `Chat` product entrance in the left sidebar. Click to enter.
  - After entering the Chat Product subpage, click on `Users` to go to the User Management Page.
  - Click `Create account`, a form for creating account information will pop up. If you are just a regular member, we recommend you choose the `General` type.
  - To enhance your experience with message sending and receiving features, we recommend creating two userIDs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2dc4eb43353011ef9c9c525400d5f8ef.png)

- `userSig` can be generated in real-time using the development tools provided by the console. To access the development tools, click [Chat Console > Development Tools > UserSig Tools > Signature (UserSig) Generator](https://console.trtc.io/usersig).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2c01dfce353011ef94925254002693fd.png)

### Step 5. Launch the project

Execute the following command to start the project:

vite

vue-cli

```
npm run dev
```

> **Note:**Since vue-cli enables Webpack Global Overlay Error Message Prompt by default, for a better experience, **it is recommended to disable the global overlay error prompt**.Webpack4 and Abovewebpack3module.exports = defineConfig({  ...  // Add new overlay configuration code to close  devServer: {    client: {      overlay: false,    },  },});module.exports = {  ...  // Add new overlay configuration code  devServer: {    overlay: false,  },};

```
npm run serve
```

### Additional item: Switching languages

The `Vue TUIKit` comes with default **Simplified Chinese, English** language packages that serve as the interface display language.

You may switch languages through the following methods, for more methods please see [Internationalization](https://trtc.io/document/58652?platform=web&product=chat).

```
import { TUITranslateService } from "@tencentcloud/chat-uikit-engine";// change language to chineseTUITranslateService.changeLanguage("zh");// change language to englishTUITranslateService.changeLanguage("en");
```

### Step 6. Send your first message

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5b634712b4ec11ee9939525400461a83.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/27fca10ab4ec11eeb2a1525400170219.png)

### Step 7: Make your first phone call

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2518893ab50211ee9939525400461a83.png)

## FAQs

### Product Service FAQs

#### 1. The Audio/Video Call Capability package is not activated? Failure to initiate the Audio/Video Call?

Please click [Audio/Video Call > Frequently Asked Questions](https://trtc.io/document/51024?platform=web&product=call) to view the solutions.

#### 2. What is UserSig? How is UserSig generated?

A UserSig is a password with which you can log in to use Chat service. It is the ciphertext generated by encrypting information such as userID.

The issuance of UserSig is achieved by integrating the calculation code for UserSig into your server-side, whilst providing an interface designed for your project. Whenever UserSig is required, your project could request the operational server for a dynamic UserSig. For further information, please refer to [Generating UserSig on the server-side](https://trtc.io/document/39074?product=consoleguide).

> **Caution**The method to obtain UserSig demonstrated in this document utilizes the configuration of a SECRETKEY within the client-side code. Within this procedure, the SECRETKEY is notably vulnerable to decompilation and reverse-engineering. Should your SECRETKEY be leaked, malefactors could potentially exploit your Tencent Cloud traffic. Therefore, **this technique is only appropriate for local operation and functional debugging**. For the correct method of issuing UserSig, please refer to the earlier text.

### Connection Errors FAQs

#### 1. Runtime error: "TypeError: Cannot read properties of undefined (reading "getFriendList")"

If the following errors occur during runtime after connecting as per the steps outlined above, it is imperative that you **delete the node_modules directory under the TUIKit folder** to ensure the uniqueness of TUIKit's dependencies, preventing issues caused by multiple copies of dependencies.

![259937368-f7c85dfe-b4bd-4c73-88d9-3a9f0d7797f2.png (1186Ã550)](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ade11ffbb46211ee9939525400461a83.png)

#### 2. How does a JS project integrate the TUIKit component?

TUIKit exclusively supports the TS environment for operation. You can enable the coexistence of existing JS code in your project with the TS code in TUIKit through progressive configuration of TypeScript.

vue-cli

vite

Please execute the following in the root directory of your engineering project created by the Vue CLI scaffold:

```
vue add typescript
```

Subsequently, please make selections in accordance with the following configuration options. To assure that we can support both the existing js code and the ts code within TUIKit, it is imperative that you strictly adhere to the five options presented below.

![260706614-5e2fc00b-ace5-4843-bef6-c0e234225b5d.png (1514Ã360)](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/adcb2b1bb46211eeb2a1525400170219.png)

**Once these steps are completed, please rerun the project!**

Please execute the following command in your project's root directory created with vite:

```
npm install -D typescript
```

#### 3. Runtime error reported: /chat-example/src/TUIKit/components/TUIChat/message-input/message-input-editor.vue .ts(8,23)TS1005: expected.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ade25c17b46211ee9fd6525400bb593a.png)

The above error message appears because your installed @vue/cli version is too low. **You must ensure that your @vue/cli version is 5.0.0 or higher**. The upgrade method is as follows:

```
npm install -g @vue/cli@5.0.8
```

#### 4. Runtime error: Failed to resolve loader: sass-loader

![260897345-1ba994d8-da51-4820-94e7-a7145b34750b.png (690Ã160)](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/adc33382b46211eeae9a525400c26da5.png)

The above error message appears because the `sass` environment is not installed on your machine, please run the following command to install the `sass` environment:

```
npm i -D sass sass-loader@10.1.1
```

#### 5. Other ESLint errors?

If copying chat-uikit-vue to the src directory results in error due to inconsistency with your local project code style, you may ignore this component directory. This can be achieved by adding .eslintignore file to the project root directory:

```
# .eslintignoresrc/TUIKit
```

#### 6. How to disable the full screen overlay error message prompt of webpack in dev mode in vue/cli?

You can disable it in the vue.config.js file at the root directory of your project:

webpack4

webpack3

```
module.exports = defineConfig({  ...  devServer: {    client: {      overlay: false,    },  },});
```

```
module.exports = {  ...  devServer: {    overlay: false,  },};
```

#### 7. What to do when encountering 'Component name "XXXX" should always be multi-word'?

- The version of ESLint utilized in Chat TUIKit web is v6.7.2, which does not rigidly verify the camelCase format for module names.
- Should you encounter this dilemma, you may configure as follows in the .eslintrc.js file:

```
  module.exports = {    ...    rules: {        ...        'vue/multi-word-component-names': 'warn',    },  };
```

#### 8. What should I do if I encounter ERESOLVE unable to resolve dependency tree?

If ERESOLVE unable to resolve dependency tree appears when npm install is run, it indicates a conflict in dependency installation. The following method can be adopted for installation:

```
npm install --legacy-peer-deps
```

#### 9. How might one address the error message, 'vue packages version mismatch' occurring during execution?

```
// If you are using a vue2.7 project, please execute in your project root directorynpm i vue@2.7.9 vue-template-compiler@2.7.9// If you have a Vue2.6 project, please execute in your project's root directorynpm i vue@2.6.14 vue-template-compiler@2.6.14
```

#### 10. Why does TypeScript report an error after npm run build in a Vite project?

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ae16b784b46211ee9939525400461a83.png)

**Reason**: It's led by the vue-tsc command in "build": "vue-tsc && vite build" under package.json script.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/adabee49b46211eeb2a1525400170219.png)

**Solution**: Simply remove vue-tsc. "build": "vite build"

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/add243e1b46211ee9939525400461a83.png)

## Communication and Feedback

Join the [Telegram Technical Exchange Group](https://t.me/tencent_imsdk) or [WhatsApp communication group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik) to enjoy support from professional engineers and solve your problems.

## References

#### Vue2 & Vue3 UIKit Related

- [chat-uikit-vue npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-vue)
- [Vue2 Demo source code and runnable example](https://github.com/TencentCloud/chat-uikit-vue/tree/main/Vue2/Demo)
- [Vue3 Demo source code and runnable example](https://github.com/TencentCloud/chat-uikit-vue/tree/main/Vue3/Demo)

#### Vue2 & Vue3 UIKit Logic Layer: Engine Related

- [chat-uikit-engine npm repository](https://www.npmjs.com/package/@tencentcloud/chat-uikit-engine)
- [chat-uikit-engine API Documentation](https://web.sdk.qcloud.com/im/doc/chat-engine/index.html)


---
*Source: [https://trtc.io/document/58644](https://trtc.io/document/58644)*
