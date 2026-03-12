# UI Customization

This article will provide a detailed introduction on how to customize the user interface of TUIRoomkit. TUIRoomkit offers two customization methods: one is through a simple custom UI API, and the other is by replacing existing UI components. We will introduce each method in detail below.

## Method 1: Fine-tuning the interface

TUIRoomkit provides a series of [APIs](https://www.tencentcloud.com/document/product/647/54880#) that make it easy to customize the UI. The table below lists some of the main APIs and their functions:

| API | Description |
| --- | --- |
| [setLanguage](https://www.tencentcloud.com/document/product/647/54880#51991a76-0777-4773-a2dd-91ce51b92b18) | Set the interface language. |
| [setTheme](https://www.tencentcloud.com/document/product/647/54880#5bb291c2-edb5-48b0-968a-db52ed2252ae) | Set the interface theme. |
| [enableWatermark](https://www.tencentcloud.com/document/product/647/54880#daceee1b-175d-41a1-b495-d158fe01d63c) | Enable the text watermark feature in the application.For details, see: [Text Watermark](https://www.tencentcloud.com/document/product/647/60531#). |
| [enableVirtualBackground](https://www.tencentcloud.com/document/product/647/54880#ac620717-1b58-42ed-b8a3-589bf0ad545e) | Enable the virtual background feature in the application. After calling this function, a virtual background feature button will be displayed on the UI. For details, see: [Virtual Background](https://www.tencentcloud.com/document/product/647/60533#). |
| [disableTextMessaging](https://www.tencentcloud.com/document/product/647/54880#9ed81bb6-73a0-4b75-878e-22cc641b43bc) | Disable the text messaging feature in the application. After invoking this function, users will not be able to send or receive text messages. |
| [disableScreenSharing](https://www.tencentcloud.com/document/product/647/54880#833fce4f-6e77-45bf-bea0-33a618b540fb) | Disable the screen sharing feature in the application. After calling this function, users will not be able to share their screen with others. |
| [hideFeatureButton](https://www.tencentcloud.com/document/product/647/54880#49c62018-9bc4-4117-bf68-aa985b868890) | Hide specific feature buttons in the application. After calling this function and passing in the appropriate [FeatureButton](https://www.tencentcloud.com/document/product/647/54880#6f28a0a9-c315-400e-a73f-b1fbd0b039eb) enumeration value, the corresponding button will be hidden from the user interface. |

## Method 2: Modify the UIKit source code

You can directly modify the provided UI source code to adjust the user interface of TUIRoomKit according to your requirements.

### Step 1: Exporting UIKit Source Code

Vue3

Vue2

1. Execute the source code export script, the default copy path is `./src/components/TUIRoom`

```
  node ./node_modules/@tencentcloud/roomkit-web-vue3/scripts/eject.js
```

2. Follow the script prompts to confirm that you want to copy the TUIRoomKit source code to the `./src/components/TUIRoom` directory. Enter 'y' if you want to customize the copy directory, otherwise enter 'n'.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9c0479792c9e11ef918f52540005b090.png)

3. After exporting the source code, the TUIRoomKit source code will be added to the project path you specified. At this point, you need to manually change the reference to the ConferenceMainView component, conference object from the npm package address to the relative path address of the TUIRoom source code.

```
- import { ConferenceMainView, conference } from '@tencentcloud/roomkit-web-vue3';//  Replace the reference path with the real path of the TUIRoomKit source code.+ import { ConferenceMainView, conference } from './src/components/TUIRoom/index.ts';
```

1. Execute the source code export script, the default copy path is `./src/components/TUIRoom`

```
  node ./node_modules/@tencentcloud/roomkit-web-vue2.7/scripts/eject.js
```

2. Follow the script prompts to confirm that you want to copy the TUIRoomKit source code to the ./src/components/TUIRoom directory. Enter 'y' if you want to customize the copy directory, otherwise enter 'n'.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9c0697892c9e11efb8c45254005a8b94.png)

3. After exporting the source code, the TUIRoomKit source code will be added to the project path you specified. At this point, you need to manually change the reference to the ConferenceMainView component, conference object from the npm package address to the relative path address of the TUIRoom source code.

```
- import { ConferenceMainView, conference } from '@tencentcloud/roomkit-web-vue2.7';// Replace the reference path with the real path of the TUIRoomKit source code.+ import { ConferenceMainView, conference } from './src/components/TUIRoom/index.ts';
```

### Step 2ï¼Configuring the UIKIT source code development environment

Config for Vue3 + Vite + TS

Config for Vue3 + Webpack + TS

Config for Vue2 + Webpack + TS

1. **Install development environment dependencies**

```
npm install typescript -S -D
```

2. **Register for Pinia**

TUIRoom uses Pinia for room data management, you need to register Pinia in the project entry file, which is the src/main.ts file.

```
// src/main.tsimport { createPinia } from 'pinia';const app = createApp(App);// register for Piniaapp.use(createPinia()); app.mount('#app');
```

3. **Configuring esLint Checksums**

If you don't want the TUIRoomKit component's esLint rules to conflict with your local rules and cause runtime errors, you can add the Ignore TUIRoom folder to `.eslintignore`.

```
// Please add the real path to the TUIRoom source codesrc/components/TUIRoom
```

Should you encounter TypeScript errors during the project build process, it is advisable to inspect the project's `package.json` file. Remove the `vue-tsc` segment within the corresponding build command as illustrated below:

```
// package.json{    "scripts": {        // "build": "vue-tsc --noEmit --skipLibCheck && vite build",        "build": "vite build"    }}
```

4. At this point you can run the project to see the effect of source code importation.

```
npm run dev
```

1. **Install development environment dependencies**

```
npm install typescript -S -D
```

2. **Register for Pinia**
TUIRoom uses Pinia for room data management, you need to register Pinia in the project entry file, which is the src/main.ts file.

```
// src/main.tsimport { createPinia } from 'pinia';const app = createApp(App);// register for Piniaapp.use(createPinia()); app.mount('#app');
```

3. **Configuring esLint Checksums**

If you don't want the TUIRoomKit component's esLint rules to conflict with your local rules and cause runtime errors, you can add the Ignore TUIRoom folder to `.eslintignore`.

```
// Please add the real path to the TUIRoom source codesrc/components/TUIRoom
```

4. At this point you can run the project to see the effect of source code importation.

```
npm run serve
```

> **Noteï¼**TUIRoomKit component requires vue2 project to have vue2.7 installed and supports typescript environment. If your current project is in vue2.6 + js environment, follow the steps below to upgrade to vue2.7 + ts environment.Upgrading from vue2.6 to vue2.7 is a smooth upgrade and has no effect on existing code. After configuring the ts environment, there is no impact on the existing js code. Please feel free to upgrade.

1. **Upgrade vue2 to v2.7+, if your project's vue version is already v2.7+, ignore this step.**

```
npm install vue@2 -S
```

2. **Configure typescript to support TUIRoom component loading.**

```
vue add typescript
```

The options for configuring the TS development environment can be found in the imageï¼

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3d612fe52c9f11efa01d5254005235d8.png)

****

3. **Register for Pinia**

TUIRoom uses Pinia for room data management, you need to register Pinia in the project entry file, which is the src/main.ts file.

```
import { createPinia, PiniaVuePlugin } from 'pinia';Vue.use(PiniaVuePlugin);const pinia = createPinia();new Vue({  pinia,  render: h => h(App),}).$mount('#app');
```

4. **Configuring esLint Checksums**

If you don't want the TUIRoomKit component's esLint rules to conflict with your local rules and cause runtime errors, you can add the Ignore TUIRoom folder to `.eslintignore`.

```
// Please add the real path to the TUIRoom source codesrc/components/TUIRoom
```

5. At this point you can run the project to see the effect of source code importation.

```
npm run serve
```

### Step 3ï¼Modify the source code according to the requirements

#### 1. Replace icons

You can directly modify the icon components in the `/TUIRoom/components/common/icons` folder to ensure that the icon color and style are consistent throughout the app. Please keep the icon file names unchanged when replacing.

#### 2. Adjust UI layout

You can adjust the multi-person video conference interface UI layout by modifying different components in the `/TUIRoom/components/` folder:

```
- components/        - Chat                Chat    - common              Common icon components    - ManageMember        Member management    - RoomContent         Room video    - RoomFooter          Room page Footer section    - RoomHeader          Room page Header section    - RoomHome            Home page    - RoomInvite          Invite members    - RoomLogin           Login page    - RoomMore            More    - RoomSetting         Settings    - RoomSidebar         Drawer component
```

## Method 3: Implement your own UI

The overall functionality of TUIRoomKit is based on the TUIRoomEngine, a UI-less SDK. You can fully implement your own UI interface based on TUIRoomEngine. For more information, please see:

- [TUIRoomEngine Integration Guide](https://www.tencentcloud.com/document/product/647/54845#)
- [TUIRoomEngine API Interface Address](https://www.tencentcloud.com/document/product/647/54878#)


---
*Source: [https://trtc.io/document/54851](https://trtc.io/document/54851)*
