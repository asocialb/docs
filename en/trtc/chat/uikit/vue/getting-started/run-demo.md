# Run Demo

TUIKit is a UI component library based on Tencent Cloud Chat SDK. It provides some universal UI components, including conversations, chats, relationship chains, groups, audio/video calls, and other features. With these UI components, you can quickly build your own in-app chat.

While implementing UI features, the components in TUIKit will call the corresponding interfaces of the Chat SDK to implement Chat-related logic and data processing. Therefore, developers only need to focus on their own business or personalized expansion when using TUIKit.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/71eafaeab5f611eeb395525400461a83.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/78f28c36b5f611ee9d74525400c26da5.png)

## Prerequisites

### Activate the Service

1. Log in to [Chat](https://console.trtc.io/) and create an application. Click `Create Application`, input your Application name in the dialog box, select Product and Region, then click `Create` to create the application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed981df2c06c11f09c26525400bf7822.png)

2. After creation, you can view the `SDKAppID` and `SecretKey` of the newly created app on the console overview page. These two pieces of info are required to run the Demo subsequently.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/edeb6a3cc06c11f0b4a7525400454e06.png)

3. Create 2 to 3 accounts for experience in C2C chat and group chat.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed59ce71c06c11f09c26525400bf7822.png)

4. Get userSig info via [UserSign Tools](https://console.trtc.io/usersig) for login account.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed228f5ec06c11f09c26525400bf7822.png)

### Environment Requirements

- Vue (Fully compatible with both Vue2 & Vue3. While incorporating below, please select the Vue version guide that matches your needs)
- TypeScript (Should your project be based on JavaScript, please proceed to [JS project integrate](https://www.tencentcloud.com/document/product/1047/58645#84b6b984-9573-4dd4-a2f8-bcdcd2cabce2) to set up a progressive support for TypeScript)
- Sass (sass-loader â¤ 10.1.1)
- node(node.js â¥ 16.0.0)
- npm (use a version that matches the Node version in use)

## Integrate TUIKit

### Step 1: Create a Project

TUIKit supports the use of vite or vue-cli for project creation, configuring Vue3/Vue2 + TypeScript + sass. The following is several project setup examples:

vite

vue-cli

> **Note:**Vite requires [**Node.js**](https://nodejs.org/en/)**version 18+ or 20+.** When your package manager issues a warning, please note to upgrade your Node Version. For details, refer to [vite official website](https://cn.vitejs.dev/guide/).

Create a project using vite, configure Vue + TypeScript as shown in the figure below.

```
npm create vite@5
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/715800d6c06d11f0b4a7525400454e06.png)

Then switch to the project directory and install the project dependencies:

```
cd chat-examplenpm install
```

Install the Sass environment dependency required for TUIKit:

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

> **Note:**If `tsconfig.json` uses `references`, the rule must be written in the referenced file (such as `./tsconfig.app.json`), otherwise writing it in `tsconfig.json` does not take effect. The rule addition must be made to the actual `references` corresponding file. The following is a specific example:Incorrect Writing FormatCorrect Writing FormatWhen the tsconfig.json file contains existing references configuration, declaring the following rules directly in tsconfig.json is invalid.When the tsconfig.json file contains existing references configuration, the following rules must be declared in the corresponding references internal file. Below is the configuration of the following rules in the root directory `tsconfig.app.json` file within references.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/714fcd63c06d11f0a6dd5254005ef0f7.png)
> ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/715bbce1c06d11f0b35752540099c741.png)

> **Note:**Note: Be sure to ensure your **@vue/cli version is 5.0.0** or higher. You can use the following example code to upgrade your @vue/cli version to v5.0.8.

Create a project using vue-cli, configure Vue2/Vue3 + TypeScript + sass.

If you have not installed vue-cli or your vue-cli version is lower than 5.0.0, you can install it in terminal or cmd in the following ways:

```
npm install -g @vue/cli@5.0.8 sass@1.77.0 sass-loader@10.1.1
```

Create a project using vue-cli and choose the selected configuration in the figure below.

```
vue create chat-example
```

Ensure the following configuration selection:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/716192e6c06d11f0aa02525400e889b2.png)

After creation, switch to the project directory:

```
cd chat-example
```

If you are using Vue 2, configure the environment according to your vue version. Ignore it for vue 3 projects.

vue2.7

Vue 2.6 and Below

```
npm i vue@2.7.9 vue-template-compiler@2.7.9
```

```
npm i @vue/composition-api unplugin-vue2-script-setup vue@2.6.14 vue-template-compiler@2.6.14Step 2: Download the TUIKit component
```

Download the TUIKit component via [npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-vue). Copy the TUIKit component to your project's src directory:

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

### Step 2: Import the TUIKit Component

On the page to be displayed, import the TUIKit component and it can be used.

> **Note:**To respect emoji design copyright, the Chat Demo/TUIKit project does not include large emoji element slicing. Before official commercial launch, please replace with other emoji packs designed or owned by oneself. The default **little yellow face emoji pack is owned by Tencent Cloud**, as shown below. You can upgrade to [Chat Pro Edition Plus and Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to try it for free.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a45748f8c06d11f083155254001c06ec.png)

For example: Implement the following code in the App.vue page to quickly build a chat interface (the example code below supports both Web and H5):

> **Note:**Note: The following example code uses the setup syntax. If your project no longer uses the setup syntax, register the component according to the standard method for Vue3/Vue2.

vue3

vue2.7

Vue 2.6 and Below

```
<template>  <div id="app">    <TUIKit :SDKAppID="0" userID="xxx" userSig="xxx" />    <TUICallKit class="callkit-container" :allowedMinimized="true" :allowedFullScreen="false" />  </div></template><script lang="ts" setup>import { TUIKit } from './TUIKit';import { TUICallKit } from '@trtc/calls-uikit-vue';</script><style lang="scss"></style>
```

If it is a project created with Vite, you can comment out the default invalid style in the project. You can delete useless content depending on the situation.

src/style.css

```
#app {  /* max-width: 1280px; */  margin: 0 auto;  /* padding: 2rem; */  text-align: center;}
```

```
<template>  <div id="app">    <TUIKit :SDKAppID="0" userID="xxx" userSig="xxx" />    <TUICallKit class="callkit-container" :allowedMinimized="true" :allowedFullScreen="false" />  </div></template><script lang="ts" setup>import { TUIKit } from './TUIKit';import { TUICallKit } from '@trtc/calls-uikit-vue2';</script><style lang="scss"></style>
```

If it is a project created by vite, you can comment out the invalid style in the default project. You can delete useless content depending on the situation.

src/style.css

```
#app {  /* max-width: 1280px; */  margin: 0 auto;  /* padding: 2rem; */  text-align: center;}
```

```
<template>  <div id="app">    <TUIKit :SDKAppID="0" userID="xxx" userSig="xxx" />    <TUICallKit class="callkit-container" :allowedMinimized="true" :allowedFullScreen="false" />  </div></template><script lang="ts" setup>import { TUIKit } from './TUIKit';import { TUICallKit } from '@trtc/calls-uikit-vue2.6';</script><style lang="scss"></style>
```

1. Install dependencies related to composition-api and script setup, as well as dependencies for vue2.6.

```
npm i @vue/composition-api unplugin-vue2-script-setup vue@2.6.14 vue-template-compiler@2.6.14
```

2. Introduce VueCompositionAPI in `main.ts/main.js`.

```
import VueCompositionAPI from "@vue/composition-api";Vue.use(VueCompositionAPI);
```

3. Add the following to `vue.config.js`. If the file does not exist, please create it.

```
const ScriptSetup = require("unplugin-vue2-script-setup/webpack").default;module.exports = {  parallel: false, // disable thread-loader, which is not compactible with this plugin  configureWebpack: {    plugins: [      ScriptSetup({        /* options */      }),    ],  },  chainWebpack(config) {    // disable type check and let `vue-tsc` handles it    config.plugins.delete("fork-ts-checker");  },};
```

4. At the end of the `src/TUIKit/adapter-vue.ts` file, replace the export source:

```
// initial writingexport * from "vue";// replace withexport * from "@vue/composition-api";
```

If it is a project created by Vite, you can comment out the invalid style in the default project. You can delete useless content depending on the situation.

src/style.css

```
#app {  /* max-width: 1280px; */  margin: 0 auto;  /* padding: 2rem; */  text-align: center;}
```

### Step 3: Configure Authentication Information

Set the props `App.vue` in the TUIKit component: SDKAppID, userID, userSig.

> **Note:**UserSig is the password for user login to Chat, which is essentially the encrypted ciphertext of UserID and other information.UserSig issuance method integrates the UserSig calculation code into your server and provides a project-oriented API. When UserSig is required, your project initiates request to the business server to obtain dynamic UserSig.The example code in this document uses the method of obtaining UserSig by configuring SECRETKEY in client-side code. In this method, SECRETKEY can be easily decompiled and reverse-engineered. Once your key is leaked, attackers can misappropriate your Tencent Cloud traffic. **Therefore, this method is only suitable for locally debugging features.** For more details, see [server-side generation of UserSig](https://www.tencentcloud.com/document/product/1047/34385).

```
<TUIKit  :SDKAppID="0" // number  userID="xxx"  // string  userSig="xxx" // string/>
```

### Step 4: Build and Run the Demo

Execute the following command to start the project:

vite

vue-cli

```
npm run dev
```

> **Note:**Since vue-cli enables the global overlay error message prompt by default, for a better experience, **it is recommended to disable the global overlay error prompt in vue.config.js or other webpack configuration files in your project**.Webpack4 and Abovewebpack3module.exports = defineConfig({  ...  // Add new configuration code to disable overlay  devServer: {    client: {      overlay: false,    },  },});module.exports = {  ...  // Add new configuration code to disable overlay  devServer: {    overlay: false,  },};

```
npm run serve
```

## Experience Basic Feature

### Send Your First Message

1. After the project starts, click **Initiate a Private Chat** in the upper left corner.
2. Enter the **Initiate a Private Chat** popup. In the search box, input the userID created in "**Enabling a Service"**, then click **Complete** once selected.
3. Enter the message in the input box and click **Send**.

Step example for sending your first message on the Web:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/33e21aaac06e11f0a0935254007c27c5.png)

H5 steps to "send your first message":

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/33eddfd4c06e11f09c26525400bf7822.png)

### Make Your First Phone Call

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/33d9a963c06e11f0b4a7525400454e06.png)

### Add-Ons: Switch Language

Web & H5 `Vue TUIKit` comes with built-in **Simplified Chinese, English** language packs as interface display languages.

You can switch language in the following ways. For more switch methods, check [internationalized interface language](https://www.tencentcloud.com/document/product/1047/58652).

```
import { TUITranslateService } from "@tencentcloud/chat-uikit-engine";// change language to chineseTUITranslateService.changeLanguage("zh");// change language to englishTUITranslateService.changeLanguage("en");
```

## FAQs

### Product Service FAQs

#### 1. The Audio/Video Call Capability package is not activated? Failure to initiate the Audio/Video Call?

Please click [Audio/Video Call > Frequently Asked Questions](https://www.tencentcloud.com/document/product/647/53565) to view the solutions.

#### 2. What is UserSig? How is UserSig generated?

A UserSig is a password with which you can log in to use IM service. It is the ciphertext generated by encrypting information such as userID.

The issuance of UserSig is achieved by integrating the calculation code for UserSig into your server-side, whilst providing an interface designed for your project. Whenever UserSig is required, your project could request the operational server for a dynamic UserSig. For further information, please refer to [Generating UserSig on the server-side](https://www.tencentcloud.com/en/document/product/1047/34385).

> **Caution**The method to obtain UserSig demonstrated in this document utilizes the configuration of a SECRETKEY within the client-side code. Within this procedure, the SECRETKEY is notably vulnerable to decompilation and reverse-engineering. Should your SECRETKEY be leaked, malefactors could potentially exploit your Tencent Cloud traffic. Therefore, **this technique is only appropriate for local operation and functional debugging**. For the correct method of issuing UserSig, please refer to the earlier text.

### Connection Errors FAQs

#### Runtime error: "TypeError: Cannot read properties of undefined (reading "getFriendList")"

If the following errors occur during runtime after connecting as per the steps outlined above, it is imperative that you **delete the node_modules directory under the TUIKit folder** to ensure the uniqueness of TUIKit's dependencies, preventing issues caused by multiple copies of dependencies.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ade11ffbb46211ee9939525400461a83.png)

#### How does a JS project integrate the TUIKit component?

TUIKit exclusively supports the TS environment for operation. You can enable the coexistence of existing JS code in your project with the TS code in TUIKit through progressive configuration of TypeScript.

vue-cli

vite

Please execute the following in the root directory of your engineering project created by the Vue CLI scaffold:

```
vue add typescript
```

Subsequently, please make selections in accordance with the following configuration options. To assure that we can support both the existing js code and the ts code within TUIKit, it is imperative that you strictly adhere to the five options presented below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/adcb2b1bb46211eeb2a1525400170219.png)

**Once these steps are completed, please rerun the project!**

Please execute the following command in your project's root directory created with vite:

```
npm install -D typescript
```

#### Runtime error reported: /chat-example/src/TUIKit/components/TUIChat/message-input/message-input-editor.vue .ts(8,23)TS1005: expected.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ade25c17b46211ee9fd6525400bb593a.png)

The above error message appears because your installed @vue/cli version is too low. **You must ensure that your @vue/cli version is 5.0.0 or higher**. The upgrade method is as follows:

```
npm install -g @vue/cli@5.0.8
```

#### Runtime error: Failed to resolve loader: sass-loader

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/adc33382b46211eeae9a525400c26da5.png)

The above error message appears because the `sass` environment is not installed on your machine, please run the following command to install the `sass` environment:

```
npm i -D sass sass-loader@10.1.1
```

#### Other ESLint errors?

If copying chat-uikit-vue to the src directory results in error due to inconsistency with your local project code style, you may ignore this component directory. This can be achieved by adding .eslintignore file to the project root directory:

```
# .eslintignoresrc/TUIKit
```

#### How to disable the full screen overlay error message prompt of webpack in dev mode in vue/cli?

You can disable it in the vue.config.js file at the root directory of your project:

webpack4

webpack3

```
module.exports = defineConfig({  ...  devServer: {    client: {      overlay: false,    },  },});
```

```
module.exports = {  ...  devServer: {    overlay: false,  },};
```

#### What to do when encountering 'Component name "XXXX" should always be multi-word'?

- The version of ESLint utilized in IM TUIKit web is v6.7.2, which does not rigidly verify the camelCase format for module names.
- Should you encounter this dilemma, you may configure as follows in the .eslintrc.js file:

```
  module.exports = {    ...    rules: {        ...        'vue/multi-word-component-names': 'warn',    },  };
```

#### What should I do if I encounter ERESOLVE unable to resolve dependency tree?

If ERESOLVE unable to resolve dependency tree appears when npm install is run, it indicates a conflict in dependency installation. The following method can be adopted for installation:

```
npm install --legacy-peer-deps
```

#### How might one address the error message, 'vue packages version mismatch' occurring during execution?

```
// If you are using a vue2.7 project, please execute in your project root directorynpm i vue@2.7.9 vue-template-compiler@2.7.9// If you have a Vue2.6 project, please execute in your project's root directorynpm i vue@2.6.14 vue-template-compiler@2.6.14
```

#### Why does TypeScript report an error after npm run build in a Vite project?

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ae16b784b46211ee9939525400461a83.png)

**Reason**: It's led by the vue-tsc command in "build": "vue-tsc && vite build" under package.json script.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/adabee49b46211eeb2a1525400170219.png)

**Solution**: Simply remove vue-tsc. "build": "vite build"

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/add243e1b46211ee9939525400461a83.png)

## Contact Us

Join the [Telegram technical discussion group](https://t.me/tencent_imsdk) or [WhatsApp discussion group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik), enjoy the support of professional engineers, and solve your difficulties.

## Documentation

#### Related to Vue2 & Vue3 UIKit:

- [chat-uikit-vue npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-vue)
- [Vue2 Demo Source Code and Running Example](https://github.com/TencentCloud/chat-uikit-vue/tree/main/Vue2/Demo)
- [Vue3 Demo Source Code and Running Example](https://github.com/TencentCloud/chat-uikit-vue/tree/main/Vue3/Demo)

#### Vue2 & Vue3 UIKit engine:

- [chat-uikit-engine npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-engine)
- [chat-uikit-engine interface](https://web.sdk.qcloud.com/im/doc/chat-engine/index.html)


---
*Source: [https://trtc.io/document/58645](https://trtc.io/document/58645)*
