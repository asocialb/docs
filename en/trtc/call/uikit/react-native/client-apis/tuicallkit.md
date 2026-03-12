# TUICallKit

## TUICallKit API

The TUICallKit API is a **UI-inclusive interface** for the audio and video call component. By using the TUICallKit API, you can quickly implement a WeChat-like audio and video call scenario through simple interfaces. For more detailed integration steps, please refer to Quick Access to TUICallKit.

## TUICallKit APIs

| API | Description |
| --- | --- |
| [login](https://www.tencentcloud.com/document/product/647/66842#93b6b48b-6ced-41f6-9efe-3c99ac82a7cc) | Login. |
| [logout](https://www.tencentcloud.com/document/product/647/66842#34205667-e433-4e42-80fb-ca9d0fc256c7) | Logout. |
| [calls](https://www.tencentcloud.com/document/product/647/66842#184a66f0-1280-4575-89a1-409f4f64aa3b) | Initiate a one-to-one or multi-person call. |
| [call](https://www.tencentcloud.com/document/product/647/66842#call_param) | To make a one-on-one call, supports custom room ID, call timeout, offline push content, and more. |
| [groupCall](https://www.tencentcloud.com/document/product/647/66842#groupcall) | To make a group call, supports custom room ID, call timeout, offline push content, and more. |
| [joinInGroupCall](https://www.tencentcloud.com/document/product/647/66842#joiningroupcall) | Join a group call. |
| [setCallingBell](https://www.tencentcloud.com/document/product/647/66842#93d9981e-20e0-4619-b01b-ae0b9edc85a5) | Customize user's ringtone. |
| [setSelfInfo](#1e1b351d-802a-45ec-ae9f-0a06bc1a1187) | Set user's avatar and nickname. |
| [enableMuteMode](https://www.tencentcloud.com/document/product/647/66842#f437b400-a478-4446-a060-ae2283af3a38) | Set whether to turn on the mute mode. |
| [enableVirtualBackground](https://www.tencentcloud.com/document/product/647/66842#48143cfb-18bc-4b06-b4bc-6fd8214f15d4) | Turn On/Off Ringtone. |
| [setScreenOrientation](https://www.tencentcloud.com/document/product/647/66842#1f6205a6-9ef8-42aa-9143-697476ad4478) | Set Screen Orientation. |
| [on](https://www.tencentcloud.com/document/product/647/66842#41ad2909-fce1-4b6e-8a0c-2a4a982bc6ae) | Listen to TUICallKit events |
| [off](https://www.tencentcloud.com/document/product/647/66842#ce43fcef-252e-4ab2-bd0e-175fc4847b54) | Cancel listening to TUICallKit events |

## API Details

### login

Login. This step is crucial. Only after successful login can you use the various features provided by TUICallKit normally.

```
TUICallKit.login(  {    sdkAppId: 0,    userId: '',    userSig: '',  },  (res) => {    console.log('login success');  },   (errCode, errMsg) => {     console.log('login error');   });
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| sdkAppId | Number | The unique identifier SDKAppID for the audio and video application created in [Tencent RTC Console](https://console.trtc.io/). |
| userId | String | Customers define their own User ID based on their business. You can only include letters (a-z, A-Z), digits (0-9), underscores, and hyphens. |
| userSig | String | SDKSecretKey for the audio and video application created in [Tencent RTC Console](https://console.trtc.io/). |

### logout

Logout. After logging out, no TUICallKit events will be listened to.

```
TUICallKit.login(  (res) => {    console.log('login success', res);  },   (errCode, errMsg) => {     console.log('login error', errCode, errMsg);   });
```

### calls

Initiate a one-to-one or multi-person call.

```
TUICallKit.calls(  {    userIdList: userIDList,    mediaType: MediaType.Audio,    callParams: {      offlinePushInfo: {        title: '',        desc: '',      },    },  },  () => {    console.log('calls success');  },  () => {    console.log('calls error');  });
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| userIdList | Array<String> | The target user IDs. |
| mediaType | [MediaType](https://www.tencentcloud.com/document/product/647/66840#fb7a5c31-59f7-421a-a743-a08ac55305d8) | The media type of the call, such as video call, voice call.MediaType.Audio: Voice Call.MediaType.Video: Video Call. |
| callParams | [callParams](https://www.tencentcloud.com/document/product/647/66840#7c505b92-4c45-43cd-a254-cbce7809a746) | call extension parameters include room number, call invitation timeout, offline push custom content, etc. |

### call

Make a phone call (1v1 call), supports custom room number, call invitation timeout, offline push content, and more.

```
TUICallKit.call(  {    userId: calleeID,    mediaType: MediaType.Audio,    callParams: {      offlinePushInfo: {        title: '',        desc: '',      },    },  },  () => {    console.log('call success');  },  () => {    console.log('call error');  });
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | target user's userId |
| mediaType | [MediaType](https://www.tencentcloud.com/document/product/647/66840#fb7a5c31-59f7-421a-a743-a08ac55305d8) | The media type of the call, such as video call, voice call.MediaType.Audio: Voice Call.MediaType.Video: Video Call. |
| callParams | [callParams](https://www.tencentcloud.com/document/product/647/66840#7c505b92-4c45-43cd-a254-cbce7809a746) | call extension parameters include room number, call invitation timeout, offline push custom content, etc. |

### groupCall

Initiate group communication.

```
TUICallKit.groupCall(  {    userIdList: userIDList,    mediaType: MediaType.Audio,    groupId: '',  },  (res) => {    console.log('groupCall success', res);  },  (errCode, errMsg) => {    console.log('groupCall error', errCode, errMsg);  });
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| groupId | String | The group ID. |
| userIdList | Array<String> | The target user IDs. |
| mediaType | [MediaType](https://www.tencentcloud.com/document/product/647/66840#fb7a5c31-59f7-421a-a743-a08ac55305d8) | The media type of the call, such as video call, voice callMediaType.Audio: Voice Call.MediaType.Video: Video Call. |
| callParams | [callParams](https://www.tencentcloud.com/document/product/647/66840#7c505b92-4c45-43cd-a254-cbce7809a746) | call extension parameters, for example: room number, call invitation timeout, custom content for offline push, etc. |

### joinInGroupCall

Join an existing audio-video call in a group.

```
TUICallKit.joinInGroupCall(  {    roomId: '',    groupId: '',    mediaType: '',  });
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | [RoomId](https://www.tencentcloud.com/document/product/647/66840#280a991e-d6a9-4194-9c98-ab703173227f) | Audio-Video Room ID for this call |
| groupId | String | Group ID associated with this group call |
| mediaType | [MediaType](https://www.tencentcloud.com/document/product/647/66840#fb7a5c31-59f7-421a-a743-a08ac55305d8) | The media type of the call, such as video call, voice call |

### setCallingBell

Set a custom incoming call ringtone.

- The input is restricted to the local MP3 format file address. It is imperative to ensure that the application has access to this file directory.
- Use the import method to introduce the ringtone file.
- To reset the ringtone, pass in an empty string for `filePath`.

```
var filePath: string = '';TUICallKit.setCallingBell(filePath);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| filePath | String | Ringtone file address |

### setSelfInfo

This API is used to set the alias and profile photo. The alias cannot exceed 500 bytes, and the profile photo is specified by a URL.

```
 var nickname: string = 'user'; var avatar: string = ''; TUICallKit.setSelfInfo(nickname, userAvatar,  (res) => {    console.log('groupCall success', res);  },  (errCode, errMsg) => {    console.log('groupCall error', errCode, errMsg);  } );
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| nickname | string | The target user names. |
| avatar | string | The target user avatar. |

### enableMuteMode

Enable/Disable Ringtone. After enabling, the ringtone will not play when receiving a call request.

```
Boolean enable = trueTUICallKit.enableMuteMode(enable);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| enable | Boolean | Enable/Disable Ringtone. Default is false. |

### enableVirtualBackground

Enable/disable blurry background feature. By calling the interface, you can display the blurry background feature button on the UI, and click the button to directly enable the blurry background feature.

```
Boolean enable = trueTUICallKit.enableVirtualBackground(enable);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| enable | Boolean | enable = true Show blurry background buttonenable = false Do not show blurry background button |

### setScreenOrientation

Set screen display mode.

```
Number orientation = 0TUICallKit.setScreenOrientation(orientation);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| orientation | Number | orientation = 0 : Portrait display.orientation = 1 : Landscape display.orientation = 2 : Automatically select the best display mode based on the current state of the device. |

### on

You can listen to TUICallKit events using the example code below. For event details, please refer to [TUICallEvent](https://www.tencentcloud.com/document/product/647/66841#tuicallevent-api-.E7.AE.80.E4.BB.8B) .

```
TUICallKit.on(TUICallEvent.onCallReceived, (res: any) => {  console.log('onUserReject userId=' + res.userId);});
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| type | String | For the events you are listening to with TUICallKit, please refer to the event list in [TUICallEvent](https://www.tencentcloud.com/document/product/647/66841#tuicallevent-api-.E7.AE.80.E4.BB.8B) . |
| params | Any | Information carried by the event, please refer to [TUICallEvent](https://www.tencentcloud.com/document/product/647/66841#tuicallevent-api-.E7.AE.80.E4.BB.8B) for details. |

### off

You can use the following sample code to cancel listening to TUICallKit events.

```
TUICallKit.off(TUICallEvent.onCallReceived);
```


---
*Source: [https://trtc.io/document/66842](https://trtc.io/document/66842)*
