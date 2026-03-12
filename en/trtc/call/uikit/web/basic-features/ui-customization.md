# UI Customization

This document describes how to customize the UI of `TUICallKit` and provides two schemes for customization: **slight UI adjustment** and **custom UI implementation**.

## Scheme 1: Slight UI Adjustment

### Button Hiding

Invoke the [hideFeatureButton](https://www.tencentcloud.com/document/product/647/51015#bc0bf579-f35b-483b-a1c7-ae098d2e0e48) interface to hide buttons, currently supporting Camera, Microphone, SwitchCamera, InviteUser. For details, see the enumeration type [FeatureButton](https://www.tencentcloud.com/document/product/647/51015#6e728b5d-c006-4ccd-93d2-6542835b6366).

Taking the hiding of the **Camera Button** as an example.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/393375281fdc11efb2cb5254006568c0.png)

Vue3

React

```
import { TUICallKitAPI, FeatureButton } from "@trtc/calls-uikit-vue";TUICallKitAPI.hideFeatureButton(FeatureButton.Camera);
```

```
import { TUICallKitAPI, FeatureButton } from "@trtc/calls-uikit-react";TUICallKitAPI.hideFeatureButton(FeatureButton.Camera);
```

### Custom Call Background Image

The call background image appears when the camera is turned off during a voice or video call. Modify the local user's call interface background image by calling [setLocalViewBackgroundImage](https://www.tencentcloud.com/document/product/647/51015#becf0aa7-fc00-49da-81da-f96782bd8357), and modify the remote user's call interface background image with [setRemoteViewBackgroundImage](https://www.tencentcloud.com/document/product/647/51015#e02ee7dd-5bea-4396-bc86-522e332053b4).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/395800971fdc11ef91395254000a29ac.png)

Vue3

React

```
import { TUICallKitAPI } from "@trtc/calls-uikit-vue";TUICallKitAPI.setLocalViewBackgroundImage('http://xxx.png');TUICallKitAPI.setRemoteViewBackgroundImage('remoteUserId', 'http://xxx.png');
```

```
import { TUICallKitAPI } from "@trtc/calls-uikit-react";TUICallKitAPI.setLocalViewBackgroundImage('http://xxx.png');TUICallKitAPI.setRemoteViewBackgroundImage('remoteUserId', 'http://xxx.png');
```

### Set Layout

> **Noteï¼****Only available for 1V1 video calls.**

Use [setLayoutMode](https://www.tencentcloud.com/document/product/647/51015#a5410b97-d61e-4628-b349-8a0d23dc5ce8) to set the call interface layout, currently only supports LocalInLargeView and RemoteInLargeView, see the [LayoutMode](https://www.tencentcloud.com/document/product/647/51015#5cd991d8-2784-4616-9068-6501e7b8b464) enum for details.

1. LocalInLargeView layout, with the local user in the large window:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/287c075b2e0b11ef9bb3525400ab9413.png)

2. RemoteInLargeView layout, with the remote user in the large window:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/278d8e002e0b11ef9bb3525400ab9413.png)

Vue3

React

```
import { TUICallKitAPI, LayoutMode } from "@trtc/calls-uikit-vue";TUICallKitAPI.setLayoutMode(LayoutMode.LocalInLargeView);
```

```
import { TUICallKitAPI, LayoutMode } from "@trtc/calls-uikit-react";TUICallKitAPI.setLayoutMode(LayoutMode.LocalInLargeView);
```

### Set the initial state of the camera

Use [setCameraDefaultState](https://www.tencentcloud.com/document/product/647/51015#eb19b592-e938-40a9-a03d-4e2c45eb0aa5) to set the initial state of the camera button, currently supports Enabled and Off.

Taking the default Off state of the camera as an example:

Vue3

React

```
import { TUICallKitAPI } from "@trtc/calls-uikit-vue";TUICallKitAPI.setCameraDefaultState(false);
```

```
import { TUICallKitAPI } from "@trtc/calls-uikit-react";TUICallKitAPI.setCameraDefaultState(false);
```

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

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f9383978fd4c11ee8fa7525400ae4d13.png)

| Serial number | Resource Path |
| --- | --- |
| 1 | /TUICallKit/Components/assets/button/camera-close.svg |
| 2 | /TUICallKit/Components/assets/button/microphone-open.svg |
| 3 | /TUICallKit/Components/assets/button/speaker-open.svg |
| 4 | /TUICallKit/Components/assets/button/desktop/inviteUser.svg |
| 5 | /TUICallKit/Components/assets/button/hangup.svg |
| 6 | /TUICallKit/Components/assets/button/desktop/minimize.svg |
| 7 | /TUICallKit/Components/assets/button/desktop/fullScreen.svg |

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a70000fbfca311eea33752540095b445.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0cbeb8aefd4d11ee8fa7525400ae4d13.png)

| Serial number | Resource Path |
| --- | --- |
| 1 | /TUICallKit/Components/assets/button/mobile/minimize.svg |
| 2 | /TUICallKit/Components/assets/button/hangup.svg |
| 3 | /TUICallKit/Components/assets/button/accept.svg |
| 4 | /TUICallKit/Components/assets/button/microphone-open.svg |
| 5 | /TUICallKit/Components/assets/button/speaker-open.svg |
| 6 | /TUICallKit/Components/assets/button/camera-close.svg |
| 7 | /TUICallKit/Components/assets/button/switchCamera.svg |

### Replacing ringtones

You can replace ringtones by replacing the three audio files in the `TUICallKit/src/TUICallService/assets/` folder.

| Filename | Description |
| --- | --- |
| phone_dialing.mp3 | The sound of making a call |
| phone_ringing.mp3 | The ringtone for incoming calls |

## Scheme 2: Custom UI Implementation

The features of `TUICallKit` are implemented based on the `TUICallEngine` SDK, which does not include UI elements. You can use `TUICallEngine` to implement your own UI. For detailed directions, refer to the documents below:

- [TUICallEngine integration guide](https://web.sdk.qcloud.com/component/trtccalling/doc/TUICallEngine/web/en/tutorial-00-%E5%AE%9E%E7%8E%B0%E5%8F%8C%E4%BA%BA%E9%80%9A%E8%AF%9D.html)
- [TUICallEngine APIs](https://trtc.io/document/51016)


---
*Source: [https://trtc.io/document/50997](https://trtc.io/document/50997)*
