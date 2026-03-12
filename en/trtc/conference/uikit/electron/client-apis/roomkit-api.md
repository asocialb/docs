# RoomKit API

## API Introduction

The TUIRoomKit API is a multi-person meeting component with an **Including UI Interface**. By using the TUIRoomKit API, you can quickly implement a meeting-like scenario through a simple interface. For more detailed integration steps, see: [Rapid Integration with TUIRoomKit](https://www.tencentcloud.com/document/product/647/54844#).

## API Overview

- `<ConferenceMainView />:` The component body of TUIRoomkit UI.
- Conference: dependencies `ConferenceMainView ` provided API.

| API | Description |
| --- | --- |
| [getRoomEngine](https://www.tencentcloud.com/document/product/647/54885#b3295cfe-067f-4193-96f6-4a829dcfcc15) | Access the roomEngine instance. If roomEngine does not exist, it will return null. |
| [on](https://www.tencentcloud.com/document/product/647/54885#54e35df8-f2db-4796-81ea-10f775e92e4c) | Listen to specified types of apid Integration with TUIRoomKit .Event. When the event occurs, the callback function will be called. |
| [off](https://www.tencentcloud.com/document/product/647/54885#fd92a726-7469-46ca-af7c-5a36636a2782) | Cancel listening for events of a specified type. |
| [login](https://www.tencentcloud.com/document/product/647/54885#5a429689-e07a-4c01-bfc6-bfb67f7f5b7f) | Log in to the conference system. |
| [logout](https://www.tencentcloud.com/document/product/647/54885#40f8261a-7135-4739-8149-9984c105678b) | Log out of the meeting system. |
| [start](https://www.tencentcloud.com/document/product/647/54885#b0bf2a3b-428c-474f-9a0e-271c7c3b6bfd) | Start a new meeting. |
| [join](https://www.tencentcloud.com/document/product/647/54885#b08d0951-c1f4-4db4-a84d-8414b853d0f1) | Join an existing meeting. |
| [leave](https://www.tencentcloud.com/document/product/647/54885#ffc266fb-4207-4e59-b664-82ce6046758b) | Leave the current meeting. |
| [dismiss](https://www.tencentcloud.com/document/product/647/54885#31e2d7df-1c4d-449f-80fa-e6e50ebe0f6f) | Dismiss the current meeting. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54885#949c2101-7f9f-435a-8a60-294df8545620) | Set your user information. |
| [setLanguage](https://www.tencentcloud.com/document/product/647/54885#51991a76-0777-4773-a2dd-91ce51b92b18) | Set the interface language. |
| [setTheme](https://www.tencentcloud.com/document/product/647/54885#5bb291c2-edb5-48b0-968a-db52ed2252ae) | Set the interface topic. |
| [enableWatermark](https://www.tencentcloud.com/document/product/647/54885#daceee1b-175d-41a1-b495-d158fe01d63c) | Enable the text watermark feature in the application. For details, see: [Text Watermark](https://www.tencentcloud.com/document/product/647/60531#). |
| [disableScreenSharing](https://www.tencentcloud.com/document/product/647/54885#833fce4f-6e77-45bf-bea0-33a618b540fb) | Disable the screen sharing feature in the application. After invoking this function, users will not be able to share their screen with others. |
| [disableTextMessaging](https://www.tencentcloud.com/document/product/647/54885#9ed81bb6-73a0-4b75-878e-22cc641b43bc) | Disable the text messaging feature in the application. After invoking this function, users will not be able to send or receive text messages. |
| [hideFeatureButton](https://www.tencentcloud.com/document/product/647/54885#49c62018-9bc4-4117-bf68-aa985b868890) | Hide specific feature buttons in the application. By invoking this function and passing in the appropriate [FeatureButton](https://www.tencentcloud.com/document/product/647/54885#6f28a0a9-c315-400e-a73f-b1fbd0b039eb) enumerated values, the corresponding buttons will be hidden from the user interface. |

## Introduction to ConferenceMainView attributes

### Attribute Overview

| Attribute | Description | Type | Required | Default Value |
| --- | --- | --- | --- | --- |
| displayMode | Control of component display pattern:permanent: Permanent mode. The component is always displayed; internal control of the component's visibility is not exerted. If not controlled by the business end, the component will always remain visible.wake-up: Wake-up mode. The component is activated only after calling the [conference start/join](https://www.tencentcloud.com/document/product/647/54885#b0bf2a3b-428c-474f-9a0e-271c7c3b6bfd) interface and officially joining the conference; it will not be displayed beforehand. | 'permanent' \| 'wake-up' | No | permanent |

### Sample code

Vue3

Vue2

```
<template>  <ConferenceMainView display-mode="permanent"></ConferenceMainView></template><script setup>import { ConferenceMainView, conference } from '@tencentcloud/roomkit-electron-vue3';const init = async () => {    await conference.login({          sdkAppId: 0,      userId: '',      userSig: '',     });    await conference.start('123456', {      isSeatEnable: false,      isOpenCamera: true,      isOpenMicrophone: true,    });}init();</script>
```

```
<template>  <ConferenceMainView display-mode="permanent"></ConferenceMainView></template><script>import { ConferenceMainView, conference } from '@tencentcloud/roomkit-electron-vue2.7';export default {  components: {    ConferenceMainView,  },  async created() {    await conference.login({      sdkAppId: 0,      userId: '',      userSig: '',    });    await conference.start('123456', {      isSeatEnable: false,      isOpenCamera: true,      isOpenMicrophone: true,    });  },};</script>
```

## Conference API Details

Conference provides a series of methods for managing and controlling online meeting features. By implementing this interface, developers can easily integrate online meeting features into their applications.

### getRoomEngine

Access the roomEngine instance. If roomEngine does not exist, it will return null.

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference, TUIRoomEngine } from '@tencentcloud/roomkit-electron-vue3';TUIRoomEngine.once('ready', () => {    const roomEngine = conference.getRoomEngine();});
```

Returns:*TUIRoomEngine | null*

### on

Listen for a specified type of event. When the event occurs, the callback function will be called.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| eventType | [RoomEvent](https://www.tencentcloud.com/document/product/647/54885#76598037-a787-4283-adc1-34dd4474fe33) | - | Event Type to Listen For |
| callback | () => void | - | Callback Function Called When the Event Occurs |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference, RoomEvent } from '@tencentcloud/roomkit-electron-vue3';conference.on(RoomEvent.RoomStart, () => {  console.log('[conference] The meeting has already started.')});conference.on(RoomEvent.ROOM_DISMISS, () => {  console.log('[conference] The meeting has been dismissed')});
```

Returns:*void*

### off

Cancel listening for events of a specified type.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| eventType | [RoomEvent](https://www.tencentcloud.com/document/product/647/54885#76598037-a787-4283-adc1-34dd4474fe33) | - | The type of event to cancel listening for |
| callback | () => void | - | The callback function added previously |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.off('event', callback);
```

Returns:*void*

### login

Log in to the conference system.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| params | {sdkAppId: number; userId: string; userSig: string; tim?: ChatSDK} | - | Log in to the parameter object |
| sdkAppId | number | - | In the [Real-time Audio and Video Console](https://console.tencentcloud.com/trtc) click **Application Management** > **create an application**. After creating a new application, you can access the sdkAppId information in **Application Information**. |
| userId | string | - | It's advised to limit the User ID length to 32 bytes, allowing only uppercase and lowercase letters (a-zA-Z), digits (0-9), underscores, and hyphens. |
| userSig | string | - | userSig Signature For the method of calculating userSig, please refer to [UserSig Related](https://www.tencentcloud.com/document/product/647/35166). |
| tim | ChatSDK (optional) | - | If you want to leverage more capabilities of the Instant Messaging SDK while integrating roomEngine, you can pass the created tim instance into TUIRoomEngine. For how to create a tim instance, please refer to [TIM.create](https://web.sdk.qcloud.com/im/doc/zh-cn/TIM.html#.create). |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.login({  sdkAppId: 123456,  userId: 'testUser',  userSig: 'testSig'});
```

Returns:*Promise<void>*

### logout

Log out of the meeting system.

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.logout();
```

Returns:*Promise<void>*

### start

Start a new meeting.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| roomId | string | - | Meeting Room ID |
| params | [StartParams](https://www.tencentcloud.com/document/product/647/54885#d48132a7-b92a-4122-a1b0-bc821dcbab11) | - | Parameters for starting a meeting |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.start('123456', {  roomName: 'TestRoom',  isSeatEnabled: false,  isOpenCamera: false,  isOpenMicrophone: false,});
```

Returns:*Promise<void>*

### join

Join an existing meeting.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| roomId | string | - | Meeting Room ID |
| params | [JoinParams](https://www.tencentcloud.com/document/product/647/54885#2497d39a-9a74-4b86-b13f-240ae30217db) | - | Parameters for joining the meeting |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.join('123456', {  isOpenCamera: false,  isOpenMicrophone: false,});
```

Returns:*Promise<void>*

### leave

Leave the current meeting.

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.leave();
```

Returns:*Promise<void>*

### dismiss

Dismiss the current meeting.

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.dismiss();
```

Returns:*Promise<void>*

### setSelfInfo

Set your user information.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| options | {userName: string; avatarUrl: string} | - | User information object |
| userName | string (Optional) | - | User's nickname |
| avatarUrl | string (Optional) | - | User profile photo |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.setSelfInfo({  userName: 'test-name',  avatarUlr: 'https://avatar.png'});
```

Returns:*Promise<void>*

### setLanguage

Set the interface language.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| language | 'zh-CN' \| 'en-US' | - | Language |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.setLanguage('en-US');
```

Returns:*void*

### setTheme

Set the interface topic.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| theme | 'LIGHT' \| 'DARK' | - | Topic Type |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.setTheme('DARK');
```

Returns:*void*

### enableWatermark

Enable the text messaging feature in the application. For details, see: [Text Watermark](https://www.tencentcloud.com/document/product/647/60531#).

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.enableWatermark();
```

Returnsï¼*void*

### disableTextMessaging

Disable the text messaging feature in the application. After invoking this function, users will not be able to send or receive text messages.

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.disableTextMessaging();
```

Returns:*void*

### disableScreenSharing

Disable the screen sharing feature in the application. After invoking this function, users will not be able to share their screen with others.

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.disableScreenSharing();
```

Returns:*void*

### hideFeatureButton

Hide specific feature buttons in the application. By invoking this function and passing in the appropriate [FeatureButton](https://www.tencentcloud.com/document/product/647/54885#6f28a0a9-c315-400e-a73f-b1fbd0b039eb) enumerated values, the corresponding buttons will be hidden from the user interface.

The parameters are described as follows:

| Parameter | Type | Default Value | Meaning |
| --- | --- | --- | --- |
| name | [FeatureButton](https://www.tencentcloud.com/document/product/647/54885#6f28a0a9-c315-400e-a73f-b1fbd0b039eb) | - | Names of Buttons to be Hidden |

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference, FeatureButton } from '@tencentcloud/roomkit-electron-vue3';conference.hideFeatureButton(FeatureButton.SwitchTheme);
```

Returns:*void*

## Type Definition

### RoomEvent (enumeration)

| Parameter | Type | Description |
| --- | --- | --- |
| ROOM_START | string | Creating a Meeting |
| ROOM_JOIN | string | Joining a Meeting |
| ROOM_LEAVE | string | Leave Meeting |
| ROOM_DISMISS | string | Meeting Dismissed |
| KICKED_OFFLINE | string | User kicked offline |
| KICKED_OUT | string | Participant removed from meeting |
| USER_LOGOUT | string | User logged out |
| ROOM_ERROR | string | Meeting error |
| ROOM_NEED_PASSWORD | string | Meeting password |

### FeatureButton (enumerated values)

| Parameter | Type | Description |
| --- | --- | --- |
| SwitchTheme | string | Switch Topic Feature Button |
| SwitchLayout | string | Switch Layout Feature Button |
| SwitchLanguage | string | Switch Language Feature Button |
| FullScreen | string | Fullscreen Feature Button |
| Invitation | string | Invite Feature Button |
| BasicBeauty | string | Basic Beauty Button |

### StartParams

| Parameter | Type | Description | Default Value |
| --- | --- | --- | --- |
| roomName | string (Optional) | Room Name | - |
| isSeatEnabled | boolean (optional) | Enable Seats | false |
| isOpenCamera | boolean (optional) | Whether to enable the camera | false |
| isOpenMicrophone | boolean (optional) | Whether to enable the microphone | false |
| defaultCameraId | string (Optional) | Default Camera ID | - |
| defaultMicrophoneId | string (Optional) | Default Microphone ID | - |
| defaultSpeakerId | string (Optional) | Default Speaker ID | - |
| password | string (Optional) | Meeting password | - |

### JoinParams

| Parameter | Type | Description | Default Value |
| --- | --- | --- | --- |
| isOpenCamera | boolean (optional) | Whether to enable the camera | false |
| isOpenMicrophone | boolean (optional) | Whether to enable the microphone | false |
| defaultCameraId | string (Optional) | Default Camera ID | - |
| defaultMicrophoneId | string (Optional) | Default Microphone ID | - |
| defaultSpeakerId | string (Optional) | Default Speaker ID | - |
| password | string (Optional) | Meeting password | - |


---
*Source: [https://trtc.io/document/54885](https://trtc.io/document/54885)*
