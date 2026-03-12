# UI Customization

This article will detail how to customize the TUIRoomkit user interface. TUIRoomkit offers two customization methods: one is through the simple use of Custom UI API, and the other is by replacing existing UI components. We will introduce these methods in detail below.

## Scheme 1: Interface Fine-tuning

TUIRoomkit provides a series of [API](https://www.tencentcloud.com/document/product/647/54885#), allowing for easy customization of the UI. The table below lists some of the main APIs and their functions:

| API | Description |
| --- | --- |
| [setLanguage](https://www.tencentcloud.com/document/product/647/54885#51991a76-0777-4773-a2dd-91ce51b92b18) | Set the interface language. |
| [setTheme](https://www.tencentcloud.com/document/product/647/54885#5bb291c2-edb5-48b0-968a-db52ed2252ae) | Set the interface topic. |
| [enableWatermark](https://www.tencentcloud.com/document/product/647/54885#daceee1b-175d-41a1-b495-d158fe01d63c) | Enable the text watermark feature in the application. For details, see: [Text Watermark](https://www.tencentcloud.com/document/product/647/60531#). |
| [disableTextMessaging](https://www.tencentcloud.com/document/product/647/54885#9ed81bb6-73a0-4b75-878e-22cc641b43bc) | Disable the text messaging feature in the application. After invoking this function, users will not be able to send or receive text messages. |
| [disableScreenSharing](https://www.tencentcloud.com/document/product/647/54885#833fce4f-6e77-45bf-bea0-33a618b540fb) | Disable the screen sharing feature in the application. After invoking this function, users will not be able to share their screen with others. |
| [hideFeatureButton](https://www.tencentcloud.com/document/product/647/54885#49c62018-9bc4-4117-bf68-aa985b868890) | Hide specific feature buttons in the application. By invoking this function and passing in the appropriate [FeatureButton](https://www.tencentcloud.com/document/product/647/54885#6f28a0a9-c315-400e-a73f-b1fbd0b039eb) enumerated values, the corresponding buttons will be hidden from the user interface. |

## Scheme 2: UIKit Source Code Export and Modification

You can directly modify the UI source code we provide to adjust the TUIRoomKit user interface according to your needs. Execute the following node script to automatically copy the TUIRoomKit interface source code into your project (default path `./src/components/TUIRoom`).

> **Note:**
> After exporting the source code, you need to manually change the reference of the TUIRoom component from the npm package address to the relative path address of the TUIRoom source code.

Vue3

Vue2

```
node ./node_modules/@tencentcloud/roomkit-electron-vue3/scripts/eject.js
```

```
node ./node_modules/@tencentcloud/roomkit-electron-vue2.7/scripts/eject.js
```

### 1. Replace Icons

You can directly modify the icon components in the `/TUIRoom/assets/icons/svg` folder, to ensure the icon color and style are consistent throughout the app. Please keep the icon file names unchanged while replacing them.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/235499ef1bfc11efac7f5254007bbd8c.png)

### 2. Adjust UI Layout

You can adjust the UI layout of the multi-person video conference interface by modifying different components in the `/TUIRoom/components/` folder

```
- components/        - Chat                Chat    - common              Public Icon Components    - ManageMember        Member Management    - RoomContent         Room Video    - RoomFooter          Room Page Footer    - RoomHeader          Room Page Header    - RoomHome            Home Page    - RoomInvite          Invite Members    - RoomLogin           Login Page    - RoomMore            More    - RoomSetting         Settings    - RoomSidebar        Drawer Components
```

## Solution 3: Implement Your Own UI

The overall feature of TUIRoomKit is based on the TUIRoomEngine, a UI-less SDK. You can fully implement your own UI interface based on TUIRoomEngine. For more details, see:

- [TUIRoomEngine Integration Guide](https://www.tencentcloud.com/document/product/647/54844#)
- [TUIRoomEngine API Address](https://www.tencentcloud.com/document/product/647/54882#)


---
*Source: [https://trtc.io/document/54847](https://trtc.io/document/54847)*
