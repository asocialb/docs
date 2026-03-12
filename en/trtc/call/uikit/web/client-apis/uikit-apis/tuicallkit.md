# TUICallKit

The TUICallKit API is the **audio and video call component that includes a UI interface**. With the TUICallKit API, you can swiftly develop audio and video call scenarios reminiscent of WeChat through simple interfaces. For further comprehensive steps to access this, please refer to: [Integrating TUICallKit](https://trtc.io/document/50993).

## API Overview

| API | Description |
| --- | --- |
| [<TUICallKit/>](https://www.tencentcloud.com/document/product/647/51015#TUICallKit) | The core UI call component. |
| [init](https://www.tencentcloud.com/document/product/647/51015#init) | Initialize TUICallKit. |
| [calls](https://www.tencentcloud.com/document/product/647/51015#calls) | Initiate a one-to-one or multi-person call. |
| [join](https://www.tencentcloud.com/document/product/647/51015#join) | Proactively join a call. |
| [setCallingBell](https://www.tencentcloud.com/document/product/647/51015#setCallingBell) | Customize user's ringtone. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/51015#setSelfInfo) | Set your own nickname and avatar. |
| [enableMuteMode](https://www.tencentcloud.com/document/product/647/51015#enableMuteMode) | Turn on/off ringtone. |
| [enableFloatWindow](https://www.tencentcloud.com/document/product/647/51015#enableFloatWindow) | Turn on/off the floating window function. |
| [enableVirtualBackground](https://www.tencentcloud.com/document/product/647/51015#enableVirtualBackground) | Turn on/off the blurred background function button. |
| [setLanguage](https://www.tencentcloud.com/document/product/647/51015#setLanguage) | Set the call language for the TUICallKit component. |
| [hideFeatureButton](https://www.tencentcloud.com/document/product/647/51015#hideFeatureButton) | Hidden Button. |
| [setLocalViewBackgroundImage](https://www.tencentcloud.com/document/product/647/51015#setLocalViewBackgroundImage) | Set the background image for the local user's call interface. |
| [setRemoteViewBackgroundImage](https://www.tencentcloud.com/document/product/647/51015#setRemoteViewBackgroundImage) | Set the background image for the remote user's call interface. |
| [setLayoutMode](https://www.tencentcloud.com/document/product/647/51015#setLayoutMode) | Set the call interface layout mode. |
| [setCameraDefaultState](https://www.tencentcloud.com/document/product/647/51015#setCameraDefaultState) | et whether the camera is opened by default. |
| [destroyed](https://www.tencentcloud.com/document/product/647/51015#destroyed) | Destroy TUICallKit. |
| [getTUICallEngineInstance](https://www.tencentcloud.com/document/product/647/51015#getTUICallEngineInstance) | Get TUICallEngine instance. |

## `<TUICallKit/>` attributes

### Attribute Overview

| Attribute | Description | Type | Required | Default Value | Vue | React |
| --- | --- | --- | --- | --- | --- | --- |
| allowedMinimized | Is the floating window permitted? | boolean | No | false |  â | â |
| allowedFullScreen | Whether to permit full screen mode for the call interface | boolean | No | true | â | â |
| [videoDisplayMode](https://www.tencentcloud.com/document/product/647/51015#videoDisplayMode) | Display mode for the call interface | VideoDisplayMode | No | VideoDisplayMode.COVER | â | â |
| [videoResolution](https://www.tencentcloud.com/document/product/647/51015#videoResolution) | Call Resolution | VideoResolution | No | VideoResolution.RESOLUTION_480P | â | â |
| beforeCalling | This function will be executed prior to making a call and before receiving an invitation to talk | function(type, error) | No | - | â | â |
| afterCalling | This function will be executed after the termination of the call | function() | No | - | â | â |
| onMinimized | This function will be executed when the component switches to a minimized state. The explanation for the [STATUS value is](https://www.tencentcloud.com/document/product/647/51015#STATUS) | function(oldStatus, newStatus) | No | - | â | â |
| kickedOut | The events thrown by the component occur when the current logged-in user is ejected. The call will also automatically terminate | function() | No | - | â | Ã |
| statusChanged | Event thrown by the component; this event is triggered when the call status changes. For detailed types of call status, refer to [STATUS value description](https://www.tencentcloud.com/document/product/647/51015#STATUS) | function({oldStatus, newStatus}) | No | - | â | Ã |

### Sample code

React

Vue3

```
import { TUICallKit, VideoDisplayMode, VideoResolution } from "@trtc/calls-uikit-react";<TUICallKit    videoDisplayMode={VideoDisplayMode.CONTAIN}    videoResolution={VideoResolution.RESOLUTION_1080P}    beforeCalling={handleBeforeCalling}     afterCalling={handleAfterCalling} />function handleBeforeCalling(type: string, error: any) {  console.log("[TUICallkit Demo] handleBeforeCalling:", type, error);}function handleAfterCalling() {  console.log("[TUICallkit Demo] handleAfterCalling");}
```

```
<template>   <TUICallKit    :allowedMinimized="true"    :allowedFullScreen="true"    :videoDisplayMode="VideoDisplayMode.CONTAIN"    :videoResolution="VideoResolution.RESOLUTION_1080P"    :beforeCalling="beforeCalling"    :afterCalling="afterCalling"    :onMinimized="onMinimized"    :kickedOut="handleKickedOut"    :statusChanged="handleStatusChanged"  /></template><script lang="ts" setup>import { TUICallKit, TUICallKitAPI, VideoDisplayMode, VideoResolution, STATUS } from "@trtc/calls-uikit-vue";function beforeCalling(type: string, error: any) {  console.log("[TUICallkit Demo] beforeCalling:", type, error);}function afterCalling() {  console.log("[TUICallkit Demo] afterCalling");}function onMinimized(oldStatus: string, newStatus: string) {  console.log("[TUICallkit Demo] onMinimized: " + oldStatus + " -> " + newStatus);}function kickedOut() {  console.log("[TUICallkit Demo] kickedOut");}function statusChanged(args: { oldStatus: string; newStatus: string; }) {  const { oldStatus, newStatus } = args;  if (newStatus === STATUS.CALLING_C2C_VIDEO) {    console.log(`[TUICallkit Demo] statusChanged: ${oldStatus} -> ${newStatus}`);  }}</script>
```

## Detailed information on TUICallKitAPI API

React

Vue3

```
import { TUICallKitAPI } from "@trtc/calls-uikit-react";
```

```
import { TUICallKitAPI } from "@trtc/calls-uikit-vue";
```

### init

Initialize TUICallKit.

```
try {  await TUICallKitAPI.init({ SDKAppID, userID, userSig });  // If you already have a tim instance in your project, you need to pass it in here  // await TUICallKitAPI.init({ tim, SDKAppID, userID, userSig});   console.log("[TUICallKit] Initialization succeeds.");} catch (error: any) {  console.error(`[TUICallKit] Initialization failed. Reason: ${error}`);}
```

The parameters are described below:

| Parameter | Type | Required | Meaning |
| --- | --- | --- | --- |
| SDKAppID | Number | Yes | The SDKAppID of your app, you can find your SDKAppID in the Live Audio and Video console. For details, see [Activating Services](https://www.tencentcloud.com/document/product/647/59832) |
| userID | String | Yes | The current user's ID is of string type, only allowing for the inclusion of English letters (a-z and A-Z), digits (0-9), hyphens (-) and underscores (_) |
| userSig | String | Yes | Use SDKSecretKey to encrypt SDKAppID, UserID and other information to obtain userSig.It is an authentication ticket used by Tencent Cloud to identify whether the current user can use TRTC services. For how to obtain it, please refer to How to Calculate [UserSig](https://www.tencentcloud.com/document/product/647/51024#calc_UserSig) |
| tim | TencentCloudChat | No | tim is an instance of [TencentCloudChat](https://www.npmjs.com/package/@tencentcloud/chat) SDK. |

### calls

Initiate a one-to-one or multi-person call.

```
try {  await TUICallKitAPI.calls({     userIDList: ['jack', 'tom'],     type: CallMediaType.VIDEO   });} catch (error: any) {  console.error(`[TUICallKit] Failed to call the groupCall API. Reason:${error}`);}
```

The parameters are described below:

| **Parameter** | **Type** | **Required** | **Meaning** |
| --- | --- | --- | --- |
| userIDList | Array<String> | Yes | List of called users |
| type | [CallMediaType](https://www.tencentcloud.com/document/product/647/51015#Type) | Yes | The type of media for the call, you can refer to [CallMediaType for the explanation of parameter values](https://www.tencentcloud.com/document/product/647/51015#TUICallType) |
| chatGroupID | String | Yes | chat group Id. |
| roomID | Number | No | Numerical Room ID, range [1, 2147483647] |
| strRoomID | String | No | String room ID. **v3.3.1+ supported****rangeï¼**Limited to 64 bytes in length. The supported character set range is as follows (a total of 89 characters):Lowercase and uppercase English letters.ï¼a-zA-Zï¼ï¼Numberï¼0-9ï¼ï¼ `Spaces`ã`!`ã`#`ã`$`ã`%`ã`&`ã`(`ã`)`ã`+`ã`-`ã`:`ã`;`ã`<`ã`=`ã`.`ã`>`ã`?`ã`@`ã`[`ã`]`ã`^`ã`_`ã`{`ã`}`ã`\|`ã`~`ã`,`ãroomID and strRoomID are mutually exclusive, if you use strRoomID, then roomID should be 0. If you use both, the SDK will prioritize the roomID. 2.don't mix roomID and strRoomID, because they are not interchangeable, for example, the number 123 and the string "123" are two completely different rooms. |
| timeout | Number | No | Call timeout, default: 30s, unit: seconds. timeout = 0, set to no timeout |
| userData | String | No | Customize the extended fields when initiating a call. The called user has this parameter in the [ON_CALL_RECEIVED](https://www.tencentcloud.com/document/product/647/51017#on_call_received) event. |
| [offlinePushInfo](https://www.tencentcloud.com/document/product/647/51015#offlinePushInfo) | Object | No | Customize offline message push parameters |

### join

Proactively join a call.

```
try {  await TUICallKitAPI.join({     callId: 'xx'  });} catch (error: any) {  console.error(`[TUICallKit] Failed to call the join API. Reason:${error}`);}
```

The parameters are described below:

| **Parameter** | **Type** | **Required** | **Meaning** |
| --- | --- | --- | --- |
| callId | String | Yes | Unique ID for this call |

### setLanguage

Set language, currently supports: Chinese, English, Japanese.

```
TUICallKitAPI.setLanguage("zh-cn"); // "en" | "zh-cn" | "ja_JP"
```

The parameters are described below:

| Parameter | Type | Required | Meaning |
| --- | --- | --- | --- |
| lang | String | Yes | Language type `en`,`zh-cn` and `ja_JP`. |

### setSelfInfo

Set your own nickname and avatar.

> **Note:****If you use this interface to modify user information during a call, the UI will not be updated immediately, and you will need to wait until the next call to see the changes.**

```
try {  await TUICallKitAPI.setSelfInfo({ nickName: "xxx", avatar: "http://xxx" });} catch (error: any) {  console.error(`[TUICallKit] Failed to call the setSelfInfo API. Reason: ${error}`;}
```

The parameters are described below:

| Parameter | Type | Required | Meaning |
| --- | --- | --- | --- |
| nickName | String | Yes | own nickname |
| avatar | String | Yes | own avatar address |

### setCallingBell

- Customize the user's incoming call ringtone.
- The input is restricted to the local MP3 format file address. It is imperative to ensure that the application has access to this file directory.
- Use the import method to import the ringtone file.
- If you need to restore the default ringtone, just pass empty filePath.

```
import filePath from '../assets/phone_ringing.mp3';try {  await TUICallKitAPI.setCallingBell(filePath);} catch (error: any) {  console.error(`[TUICallKit] Failed to call the setCallingBell API. Reason: ${error}`);}
```

The parameters are described below:

| Parameter | Type | Required | Meaning |
| --- | --- | --- | --- |
| filePath | String | Yes | Ringtone file path |

### enableFloatWindow

Turn on/off the floating window function. The default is false. The floating window button in the upper left corner of the call interface is hidden. It will be displayed after setting it to true.

```
try {  const enable = true;  await TUICallKitAPI.enableFloatWindow(enable);} catch (error: any) {  console.error(`[TUICallKit] Failed to call the enableFloatWindow API. Reason: ${error}`);}
```

The parameters are described below:

| Parameter | Type | Required | Meaning |
| --- | --- | --- | --- |
| enable | Boolean | Yes | Turn on/off the floating window function. default false. |

### enableMuteMode

Turn on/off the ringtone for incoming calls. When turned on, the incoming call ringtone will not be played when a call request is received.

```
try {  const enable = true;  await TUICallKitAPI.enableMuteMode(enable);} catch (error: any) {  console.error(`[TUICallKit] Failed to call the enableMuteMode API. Reason: ${error}`);}
```

### enableVirtualBackground

Turn on/off the blurred background function. If you want to set the picture background to be blurry see [Web](https://www.tencentcloud.com/document/product/647/60487). By calling the interface, you can display the blurred background function button on the UI, and click the button to directly enable the blurred background function.

```
import { TUICallKitAPI } from "@trtc/calls-uikit-react";const enable = true;TUICallKitAPI.enableVirtualBackground(enable);
```

The parameters are described below:

| Parameter | Type | Required | Meaning |
| --- | --- | --- | --- |
| enable | boolean | Yes | enable = true, show blur background buttonenable = false, don't show blur background button |

### destroyed

- Terminate the TUICallKit instance.
- This method won't automatically log out of `tim`, manual logging out is required: `tim.logout();`.

```
try {  await TUICallKitAPI.destroyed();} catch (error: any) {  console.error(`[TUICallKit] Failed to call the destroyed API. Reason: ${error}`);}
```

### hideFeatureButton

Hidden feature buttons, currently only support Camera, Microphone, and Switch Camera Button.

```
TUICallKitAPI.hideFeatureButton(buttonName: FeatureButton);
```

The parameters are described below:

| **Parameter** | **Type** | **Required** | **Meaning** |
| --- | --- | --- | --- |
| buttonName | [FeatureButton](https://www.tencentcloud.com/document/product/647/51015#FeatureButton) | Yes | Button Name |

### setLocalViewBackgroundImage

Set the background image for the local user's call interface.

```
TUICallKitAPI.setLocalViewBackgroundImage(url: string);
```

The parameters are described below:

| **Parameter** | **Type** | **Required** | **Meaning** |
| --- | --- | --- | --- |
| url | string | Yes | Image Address (supports Local Path and Network Address) |

### setRemoteViewBackgroundImage

Set the background image for the remote user's call interface.

```
TUICallKitAPI.setRemoteViewBackgroundImage(userId: string, url: string);
```

The parameters are described below:

| **Parameter** | **Type** | **Required** | **Meaning** |
| --- | --- | --- | --- |
| userId | string | Yes | Remote User userId, setting to '*' means it applies to all Remote Users |
| url | string | Yes | Image Address (supports Local Path and Network Address) |

### setLayoutMode

Set the call interface layout mode.

Vue

React

```
import { TUICallKitAPI, LayoutMode } from "@trtc/calls-uikit-vue";TUICallKitAPI.setLayoutMode(LayoutMode.LocalInLargeView);
```

```
import { TUICallKitAPI, LayoutMode } from "@trtc/calls-uikit-react";TUICallKitAPI.setLayoutMode(LayoutMode.LocalInLargeView);
```

Parameter list:

| **Parameter** | **Type** | **Required** | **Meaning** |
| --- | --- | --- | --- |
| layoutMode | [LayoutMode](https://www.tencentcloud.com/document/product/647/51015#LayoutMode) | Yes | User flow layout mode |

### setCameraDefaultState

Set whether the camera is on by default.

```
TUICallKitAPI.setCameraDefaultState(true);
```

Parameter list:

| Parameter | Type | Required | Meaning |
| --- | --- | --- | --- |
| isOpen | boolean | Yes | Whether to enable the camera |

### getTUICallEngineInstance

Get TUICallEngine instance.

```
TUICallKitAPI.getTUICallEngineInstance();
```

## TUICallKit Type Definition

### videoDisplayMode

There are three values for the `videoDisplayMode` display mode:

- `VideoDisplayMode.CONTAIN`
- `VideoDisplayMode.COVER`
- `VideoDisplayMode.FILL`, the default value is `VideoDisplayMode.COVER`.

| Attribute | Value | Description |
| --- | --- | --- |
| videoDisplayMode | VideoDisplayMode.CONTAIN | Ensuring the full display of video content is our top priority.The dimensions of the video are scaled proportionally until one side aligns with the frame of the viewing window.In case of discrepancy in sizes between the video and the display window, the video is scaled - on the premise of maintaining the aspect ratio - to fill the window, resulting in a black border around the scaled video. |
|  | VideoDisplayMode.COVER | Priority is given to ensure that the viewing window is filled.The video size is scaled proportionally until the entire window is filled.If the video's dimensions are different from those of the display window, the video stream will be cropped or stretched to match the window's ratio. |
|  | VideoDisplayMode.FILL | Ensuring that the entire video content is displayed while filling the window does not guarantee preservation of the original video's proportion.The dimensions of the video will be stretched to match those of the window. |

### videoResolution

The resolution `videoResolution` has three possible values:

- `VideoResolution.RESOLUTION_480P`
- `VideoResolution.RESOLUTION_720P`
- `VideoResolution.RESOLUTION_1080P`, the default value is `VideoResolution.RESOLUTION_480P`.

**Resolution Explanation:**

| Video Profile | Resolution (W x H) | Frame Rate (fps) | Bitrate (Kbps) |
| --- | --- | --- | --- |
| 480p | 640 Ã 480 | 15 | 900 |
| 720p | 1280 Ã 720 | 15 | 1500 |
| 1080p | 1920 Ã 1080 | 15 | 2000 |

**Frequently Asked Questions:**

- iOS 13&14 does not support encoding videos higher than 720P. It is suggested to limit the highest collection to 720P on these two system versions. Refer to [iOS Safari known issue case 12](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-02-info-webrtc-issues.html#h2-4).
- Firefox does not permit the customization of video frame rates (default is set to 30fps).
- Due to the influence of system performance usage, camera collection capabilities, browser restrictions, and other factors, the actual values of video resolution, frame rate, and bit rate may not necessarily match the set values exactly. In such scenarios, the browser will automatically adjust the Profile to get as close to the set values as feasible.

### STATUS

| STATUS attribute value | Description |
| --- | --- |
| STATUS.IDLE | Idle status |
| STATUS.BE_INVITED | Received an Audio/Video Call Invite |
| STATUS.DIALING_C2C | Initiating a one-to-one call |
| STATUS.DIALING_GROUP | Initiating a group call |
| STATUS.CALLING_C2C_AUDIO | Engaged in a 1v1 Audio Call |
| STATUS.CALLING_C2C_VIDEO | In the midst of a one-to-one video call |
| STATUS.CALLING_GROUP_AUDIO | Engaged in Group Audio Communication |
| STATUS.CALLING_GROUP_VIDEO | Engaged in group video call |

### **CallMediaType**

| CallMediaType Type | Description |
| --- | --- |
| CallMediaType.AUDIO_CALL | Audio Call |
| CallMediaType.VIDEO | Video Call |

### **offlinePushInfo**

| Parameter | Type | Required | Meaning |
| --- | --- | --- | --- |
| offlinePushInfo.title | String | No | Offline Push Title (Optional) |
| offlinePushInfo.description | String | No | Offline Push Content (Optional) |
| offlinePushInfo.androidOPPOChannelID | String | No | Setting the channel ID for OPPO phones with 8.0 system and above for offline pushes (Optional) |
| offlinePushInfo.extension | String | No | Offline push through content. Can be used to set Android [Notification mode](https://www.tencentcloud.com/document/product/647/51015#Notification mode) and [VoIP mode](https://www.tencentcloud.com/document/product/647/51015#VoIP mode).**Default**: Notification mode, it will be a notification from the system; VoIP mode is required to pass the field. |
| offlinePushInfo.ignoreIOSBadge | Boolean | No | Ignore badge count for offline push (only for iOS), if set to true, the message will not increase the unread count of the app icon on the iOS receiver's side. |
| offlinePushInfo.iOSSound | String | No | Offline push sound setting (only for iOS). |
| offlinePushInfo.androidSound | String | No | Offline push sound setting. |
| offlinePushInfo.androidVIVOClassification | Number | No | Classification of VIVO push messages (deprecated interface, VIVO push service will optimize message classification rules on April 3, 2023. It is recommended to use setAndroidVIVOCategory to set the message category). 0: Operational messages, 1: System messages. The default value is 1. |
| offlinePushInfo.androidXiaoMiChannelID | String | No | Set the channel ID for Xiaomi phones with Android 8.0 and above systems. |
| offlinePushInfo.androidFCMChannelID | String | No | Set the channel ID for google phones with Android 8.0 and above systems. |
| offlinePushInfo.androidHuaWeiCategory | String | No | Classification of Huawei push messages. |
| offlinePushInfo.isDisablePush | Boolean | No | Whether to turn off push notifications (default is on). |
| offlinePushInfo.iOSPushType | Number | No | iOS offline push typeï¼default is 0ã0-APNsï¼1-VoIP. |

#### Android Notification Mode

```
const extension = {  timPushFeatures: {            fcmPushType: 0, // 0, VoIP; 1, notification  }};offlinePushInfo.extension = JSON.stringify(extension);
```

#### Android VoIP Mode

```
const extension = {  timPushFeatures: {            fcmPushType: 0, // 0, data; 1, notification    fcmNotificationType: 1, // 0, TIMPush implementationï¼ 1, business implementation after transparent transmission   }};offlinePushInfo.extension = JSON.stringify(extension);
```

### FeatureButton

| FeatureButton Type | Description |
| --- | --- |
| FeatureButton.Camera | Camera Button |
| FeatureButton.Microphone | Microphone Button |
| FeatureButton.SwitchCamera | Switches between the front and rear cameras. |
| FeatureButton.InviteUser | Invite users button |

### LayoutMode

| LayoutMode type | Description |
| --- | --- |
| LayoutMode.LocalInLargeView | Local user in large window display |
| LayoutMode.RemoteInLargeView | Remote user in large window display |


---
*Source: [https://trtc.io/document/51015](https://trtc.io/document/51015)*
