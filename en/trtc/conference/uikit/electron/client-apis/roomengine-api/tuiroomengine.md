# TUIRoomEngine

## TUIRoomEngine Introduction

TUIRoomEngine SDK provides Room Management, Multi-person Tencent Real-Time Communication, Screen Sharing, Member Management, Instant Messaging, and other features.

**Installation Method:**

```
// Use npmnpm i @tencentcloud/tuiroom-engine-electron --save// Use pnpmpnpm i @tencentcloud/tuiroom-engine-electron --save// Use yarnyarn add @tencentcloud/tuiroom-engine-electron
```

## TUIRoomEngine API

### **TUIRoomEngine Static Method**

| API | Description |
| --- | --- |
| [once](https://www.tencentcloud.com/document/product/647/54883#once) | **Listening to the TUIRoomEngine ready Event. Note: All methods other than TUIRoomEngine.login must be executed after listening to the TUIRoomEngine ready event and the successful execution of the TUIRoomEngine.login method.** |
| [login](https://www.tencentcloud.com/document/product/647/54883#login) | Login to TUIRoomEngine |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54883#setSelfInfo) | Setting the current user's Basic information (Username, User Avatar) |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/54883#getSelfInfo) | Get the current user's Basic information (Username, User Avatar) |
| [logout](https://www.tencentcloud.com/document/product/647/54883#logout) | Logout of TUIRoomEngine |

### **roomEngine Room Management API**

| API | Description |
| --- | --- |
| [createRoom](https://www.tencentcloud.com/document/product/647/54883#createRoom) | Create Room |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54883#enterRoom) | Enter Room |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/54883#destroyRoom) | Destroy Room |
| [exitRoom](https://www.tencentcloud.com/document/product/647/54883#exitRoom) | Exit Room |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/54883#fetchRoomInfo) | Get Room data |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/54883#updateRoomNameByAdmin) | Update Name (Call by Group Owner or Administrator only) |
| [updateRoomSpeechModeByAdmin](https://www.tencentcloud.com/document/product/647/54883#updateRoomSpeechModeByAdmin) | Update Speaking Mode (Call by Group Owner or Administrator only) |
| [getUserList](https://www.tencentcloud.com/document/product/647/54883#getUserList) | Get User List |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/54883#getUserInfo) | Learn more about the user |

### **roomEngine Audio Video API**

| API | Description |
| --- | --- |
| [setLocalVideoView](https://www.tencentcloud.com/document/product/647/54883#setLocalVideoView) | Set Local Stream Rendering Position |
| [openLocalCamera](https://www.tencentcloud.com/document/product/647/54883#openLocalCamera) | Capturing Local Camera Video streams |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/54883#closeLocalCamera) | Close Local Camera |
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/54883#openLocalMicrophone) | Open Local mic |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/54883#closeLocalMicrophone) | Close Local mic |
| [updateVideoQuality](https://www.tencentcloud.com/document/product/647/54883#updateVideoQuality) | Set Local Video Parameters |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/54883#updateAudioQuality) | Set Local Audio Parameters |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/54883#startPushLocalVideo) | Start Pushing Local Video streams to Remote |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/54883#stopPushLocalVideo) | Stop Pushing Local Video streams to Remote |
| [startPushLocalAudio](https://www.tencentcloud.com/document/product/647/54883#startPushLocalAudio) | Start Pushing Local Audio Stream to Remote |
| [stopPushLocalAudio](https://www.tencentcloud.com/document/product/647/54883#stopPushLocalAudio) | Stop Pushing Local Audio Stream to Remote |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/54883#setRemoteVideoView) | Set Remote Stream Rendering Area |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54883#startPlayRemoteVideo) | Start Playback Remote User Video streams |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54883#stopPlayRemoteVideo) | Stop Playback Remote User Video streams |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/54883#muteRemoteAudioStream) | Stop Remote User Audio Stream |

### **roomEngine Member Management API**

| API | Description |
| --- | --- |
| [openRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54883#openRemoteDeviceByAdmin) | Request Remote User to Open Media Device |
| [applyToAdminToOpenLocalDevice](https://www.tencentcloud.com/document/product/647/54883#applyToAdminToOpenLocalDevice) | Participant Apply to Host to Open Device |
| [closeRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54883#closeRemoteDeviceByAdmin) | Close Remote User Media Device |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/54883#cancelRequest) | Cancel Sent Request |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/54883#responseRemoteRequest) | Reply to Remote User Request |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/54883#changeUserRole) | Change User Role |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/54883#kickRemoteUserOutOfRoom) | Kick Out User from Room |
| [disableDeviceForAllUserByAdmin](https://www.tencentcloud.com/document/product/647/54883#disableDeviceForAllUserByAdmin) | Disable/Enable All Users' Media Device |
| [disableSendingMessageForAllUser](https://www.tencentcloud.com/document/product/647/54883#disableSendingMessageForAllUser) | Disallow/Allow All Users to Send Message |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/54883#disableSendingMessageByAdmin) | Disallow/Allow Specific User to Send Message |

### **roomEngine**Screen Sharing**API**

| API | Description |
| --- | --- |
| [startScreenSharingElectron](https://www.tencentcloud.com/document/product/647/54883#startScreenSharingElectron) | Start Screen Sharing |
| [stopScreenSharingElectron](https://www.tencentcloud.com/document/product/647/54883#stopScreenSharingElectron) | Stop Screen Sharing |
| [getScreenSharingTarget](https://www.tencentcloud.com/document/product/647/54883#getScreenSharingTarget) | Obtain Screen Sharing List |
| [selectScreenSharingTarget](https://www.tencentcloud.com/document/product/647/54883#selectScreenSharingTarget) | Switch Screen Sharing Window |

### **roomEngine Mic Position Management API**

| API | Description |
| --- | --- |
| [setMaxSeatCount](https://www.tencentcloud.com/document/product/647/54883#setMaxSeatCount) | Set Room Maximum Value |
| [getSeatList](https://www.tencentcloud.com/document/product/647/54883#getSeatList) | Get Mic Position Information |
| [takeSeat](https://www.tencentcloud.com/document/product/647/54883#takeSeat) | Get Mic Position |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/54883#leaveSeat) | Release Mic Position |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/54883#takeUserOnSeatByAdmin) | Invite Others to Go Live (Only Room Host and Administrator can invoke this method) |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/54883#kickUserOffSeatByAdmin) | Kick Others Off the Mic (Only Room Host and Administrator can invoke this method) |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/54883#lockSeatByAdmin) | Lock a Specific Mic Position Status (Only Room Host and Administrator can invoke this method) |

### **roomEngine Message Sending API**

| API | Description |
| --- | --- |
| [sendTextMessage](https://www.tencentcloud.com/document/product/647/54883#sendTextMessage) | Send Text Message |
| [sendCustomMessage](https://www.tencentcloud.com/document/product/647/54883#sendCustomMessage) | Send Custom Message |

### **roomEngine Device Management API**

| API | Description |
| --- | --- |
| [getCameraDevicesList](https://www.tencentcloud.com/document/product/647/54883#getCameraDevicesList) | Get Camera Device List |
| [getMicDevicesList](https://www.tencentcloud.com/document/product/647/54883#getMicDevicesList) | Get Mic Device List |
| [getSpeakerDevicesList](https://www.tencentcloud.com/document/product/647/54883#getSpeakerDevicesList) | Get Speaker Device List |
| [setCurrentCameraDevice](https://www.tencentcloud.com/document/product/647/54883#setCurrentCameraDevice) | Set to Use Camera |
| [setCurrentMicDevice](https://www.tencentcloud.com/document/product/647/54883#setCurrentMicDevice) | Set to Use Mic |
| [setCurrentSpeakerDevice](https://www.tencentcloud.com/document/product/647/54883#setCurrentSpeakerDevice) | Set to Use Speaker |
| [getCurrentCameraDevice](https://www.tencentcloud.com/document/product/647/54883#getCurrentCameraDevice) | Get the Currently Used Camera |
| [getCurrentMicDevice](https://www.tencentcloud.com/document/product/647/54883#getCurrentMicDevice) | Get the Currently Used Mic |
| [getCurrentSpeakerDevice](https://www.tencentcloud.com/document/product/647/54883#getCurrentSpeakerDevice) | Get the Currently Used Speaker |
| [startCameraDeviceTest](https://www.tencentcloud.com/document/product/647/54883#startCameraDeviceTest) | Start Camera Test |
| [stopCameraDeviceTest](https://www.tencentcloud.com/document/product/647/54883#stopCameraDeviceTest) | Stop Camera Test |

### **roomEngine Event Listening API**

| API | Description |
| --- | --- |
| [on](https://www.tencentcloud.com/document/product/647/54883#on) | Listen to [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/54884) |
| [off](https://www.tencentcloud.com/document/product/647/54883#off) | Cancel Listening to [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/54884) |

### **roomEngine Other API**

| API | Description |
| --- | --- |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/54883#getTRTCCloud) | Get trtcCloud Instance |
| [getTIM](https://www.tencentcloud.com/document/product/647/54883#getTIM) | Get tim Instance |

## API Details

### once

Monitor TUIRoomEngine 'ready' Event

```
TUIRoomEngine.once('ready', () => {  const roomEngine = new TUIRoomEngine();    await TUIRoomEngine.init({    sdkAppId: 0,   // Fill in the sdkAppId you applied for    userId: '',    // Fill in the userId corresponding to your business    userSig: '',   // Fill in the userSig calculated by the server or locally  });    await roomEngine.createRoom({    roomId: '12345',   // Enter your Room ID, note that the Room ID is required to be a string type    name: 'Test Room',     // Enter your room name, the default room name is roomId, up to 30 bytes    roomType: TUIRoomType.kGroup, // Set the room type to TUIRoomType.kGroup type  });});
```

### login

> **Description:**In version v1.0.0, this interface is named TUIRoomEngine.init, please use TUIRoomEngine.login to log in TUIRoomEngine in v1.0.1 and above versions.

You must log in to TUIRoomEngine before you can call other methods of TUIRoomEngine and its instances.

```
// Login TUIRoomEngineawait TUIRoomEngine.login({ sdkAppId: 0,   // Fill in the sdkAppId you applied for userId: '',    // Fill in the userId corresponding to your business userSig: '',   // Fill in the userSig calculated by the server or locally});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| sdkAppId | number | Required | - | After clicking Application Management > Create Application in the Tencent Real-Time Communication Console, you can get the sdkAppId information in Application Info. |
| userId | string | Required | - | It is recommended to limit the user ID length to 32 bytes, and only allow uppercase and lowercase English letters (a-zA-Z), numbers (0-9), underscores, and hyphens. |
| userSig | string | Required | - | UserSig signature Please refer to [UserSig related](https://www.tencentcloud.com/document/product/647/35166) for the method of calculating userSig. |
| tim | TIM | Not Required | - | If you want to use more capabilities of the Chat SDK while accessing roomEngine, you can pass the created tim instance into TUIRoomEngine. For the creation method of tim instance, please refer to [TIM.create](https://web.sdk.qcloud.com/im/doc/zh-cn/TIM.html#.create). |

**Returns***Promise<void>*

### setSelfInfo

Set current user Basic information (Username, User avatar).

```
// Set current user Username and User avatarawait TUIRoomEngine.setSelfInfo({ userName: '',     // Enter your New username avatarUrl: '',    // Enter your New avatar URL});
```

**Parameter:**

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userName | string | Required | - | User Name |
| avatarUrl | string | Required | - | User avatar |

**Returns***Promise<void>*

### **getSelfInfo**

Get current user Basic information (Username, User avatar).

```
// Get current user Username and User avatarconst loginUserInfo = await TUIRoomEngine.getSelfInfo();
```

Returns*Promise<*[TUILoginUserInfo](https://www.tencentcloud.com/document/product/647/54886#TUILoginUserInfo)*> loginUserInfo*

### **logout**

> **Description:**Interface since v1.0.1 Version support.

Logout TUIRoomEngine

```
// Logout TUIRoomEngineawait TUIRoomEngine.logout();
```

Returns*Promise<void>*

### createRoom

Host creates room, Call createRoom User is the room owner. When creating a room, you can set Room ID, Room name, Room type, Speaking mode, Whether to allow users to join and enable audio and video, Send message and other functions.

```
const roomEngine = new TUIRoomEngine();await roomEngine.createRoom({    roomId: '12345',   // Enter your Room ID, note that the Room ID must be a string type    roomName: 'Test Room',     // Enter your Room Name, the default Room Name is roomId, with a maximum length of 30 bytes    roomType: TUIRoomType.kConference, // Set the Room Type to TUIRoomType.kConference    speechMode: TUISpeechMode.kFreeToSpeak, // Set the speech mode to free speech mode    isMicrophoneDisableForAllUser: false,  // Allow users to turn on their mic when joining the room    isCameraDisableForAllUser: false,  // Allow users to turn on their Camera when joining the room    isMessageDisableForAllUser: false,  // Allow users to send messages when joining the room});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| roomId | string | Required | - | Room ID, roomId has a length limit of 64 bytes and only supports the following character sets:English letters (a-zA-Z)Numbers (0-9)Space ! # $ % & ( ) + - : ; < = . > ? @ [ ] ^ _ { } \| ~ , |
| roomName | string | Optional | roomId | Room Name, default value is roomId, cannot be an empty string |
| roomType | [TUIRoomType](https://www.tencentcloud.com/document/product/647/54886#TUIRoomType) | Optional | TUIRoomType.kConference | Room TypeOffice collaboration, medical consultation, remote conference, educational scene, roomType is set to TUIRoomType.kConferenceE-commerce live broadcast, audio chat room scene, roomType is set to TUIRoomType.kLivingRoom |
| speechMode | TUISpeechMode | Optional | TUISpeechMode.kFreeToSpeak | Speech mode in the roomFor TUIRoomType.kConference (education and conference scenes): Set speechMode to TUISpeechMode.kFreeToSpeak, users can turn on their Camera and mic by default when entering the room Set speechMode to TUISpeechMode.kApplyToSpeak, users do not turn on their Camera and mic by default when entering the room, and need to apply to the host to turn on their Camera or mic. TUISpeechMode.kFreeToSpeak and TUISpeechMode.kApplyToSpeak modes can be switched Set speechMode to TUISpeechMode.kSpeakAfterTakingSeat, users need to call the takeSeat interface to get permission to turn on their Camera and mic after entering the roomFor TUIRoomType.kLivingRoom (live broadcast scene): Set speechMode to TUISpeechMode.kFreeToSpeak, no need for host approval to Go Live Set speechMode to TUISpeechMode.kSpeakAfterTakingSeat, host approval is required to Go Live TUISpeechMode.kFreeToSpeak and TUISpeechMode.kSpeakAfterTakingSeat modes can be switched |
| isMicrophoneDisableForAllUser | boolean | Optional | false | Enable mute all by default, do not enable mute all by default |
| isCameraDisableForAllUser | boolean | Optional | false | Enable disable all drawings by default, do not enable disable all drawings by default |
| isMessageDisableForAllUser | boolean | Optional | false | Allow members to send messages, do not prohibit by default |
| maxSeatCount | number | Optional | - | Maximum number of microphone seatsFor TUIRoomType.kConference (education and conference scenes), there is no limit on the value of maxSeatCountFor TUIRoomType.kLivingRoom (live broadcast scene), the maximum limit of maxSeatCount is 16 |
| enableCDNStreaming | boolean | Optional | false | Enable CDNs live stream |
| cdnStreamDomain | string | Optional | '' | Push domain |

Returns*Promise<void>*

### enterRoom

Entered room interface.

```
const roomEngine = new TUIRoomEngine();const roomInfo = await roomEngine.enterRoom({    roomId: '12345',});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| roomId | string | Required | - | Room ID |

**Returns***Promise<*[TUIRoomInfo](https://www.tencentcloud.com/document/product/647/54886#TUIRoomInfo)*> roomInfo*

This interface returns the current Room data

### destroyRoom

Close the room interface, the room must be closed by the room owner, and the room cannot be entered after it is closed.

```
const roomEngine = new TUIRoomEngine();await roomEngine.destroyRoom();
```

**Returns***Promise<void>*

### exitRoom

Leave the room interface, users can leave the room through exitRoom after executing enterRoom.

```
const roomEngine = new TUIRoomEngine();await roomEngine.exitRoom();
```

**Returns***Promise<void>*

### fetchRoomInfo

Get Room information.

```
const roomEngine = new TUIRoomEngine();const roomInfo = roomEngine.fetchRoomInfo();
```

Returnsï¼*Promise<*[TUIRoomInfo](https://www.tencentcloud.com/document/product/647/54886#TUIRoomInfo)*> roomInfo*

### updateRoomNameByAdmin

Update the current room's name (only group owner or admin can invoke).

```
const roomEngine = new TUIRoomEngine();await roomEngine.createRoom({ roomId: '12345' });await roomEngine.updateRoomNameByAdmin({ roomName: 'new name' });
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| roomName | string | Required | - | Update the room's name, with the requirement that roomName is not an empty string |

**Returns***Promise<void>*

### updateRoomSpeechModeByAdmin

Update the room's speaking mode (only group owner or admin can invoke).

```
const roomEngine = new TUIRoomEngine();await roomEngine.createRoom({ roomId: '12345' });await roomEngine.updateRoomSpeechModeByAdmin({  speechMode: TUISpeechMode.kSpeakAfterTakingSeat  // Update to Go Live Speaking mode});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| speechMode | TUISpeechMode | Required | - | Update the room's speaking mode |

### getUserList

Get the current room's user list, note that the maximum number of user lists fetched by this interface is 100.

```
const roomEngine = new TUIRoomEngine();const userList = [];let result;do {  result = await globalProperties.roomEngine.getUserList();  userList.push(...result.userInfoList);} while (result.nextSequence !== 0)
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| nextSequence | number | Optional | 0 | Offset, default is to start fetching users from 0 |

**Returns**ï¼*Promise<object>  result*

result.nextSequence is the offset for fetching group users next time, if result.nextSequence is 0, it means that all userList have been fetched

result.userInfoList is the userList fetched this time

### getUserInfo

Get the detailed information of the user.

```
const roomEngine = new TUIRoomEngine();const userList = [];const userInfo = await roomEngine.getUserInfo({    userId: 'user_12345',});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | Get the detailed information of the user according to userId |

**Returns**ï¼*Promise<*[TUIUserInfo](https://www.tencentcloud.com/document/product/647/54886#TUIUserInfo)*> userInfo*

This interface returns the user information of the specified user

### setLocalVideoView

Set the rendering position of the local stream.

```
const roomEngine = new TUIRoomEngine();    // Set the playback area of the local camera stream to the div element with id 'preview-camera'await roomEngine.setLocalVideoView({  streamType: TUIVideoStreamType.kCameraStream,  view: 'preview-camera',});    // Set the playback area of the local screen sharing stream to the div element with id 'preview-screen'await roomEngine.setLocalVideoView({  streamType: TUIVideoStreamType.kScreenStream,  view: 'preview-screen',});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/54886#TUIVideoStreamType) | Required | - | Local stream type |
| view | string | Required | - | The id of the div element corresponding to the streamType |

Returnsï¼*Promise<void>*

### openLocalCamera

Open the local camera and start capturing video streams.

```
const roomEngine = new TUIRoomEngine();await roomEngine.setLocalVideoView({  streamType: TUIVideoStreamType.kCameraStream,  view: 'preview-camera',});await roomEngine.openLocalCamera();
```

Returnsï¼*Promise<void>*

### closeLocalCamera

Close the local camera.

```
const roomEngine = new TUIRoomEngine();await roomEngine.closeLocalCamera();
```

Returnsï¼*Promise<void>*

### openLocalMicrophone

Open the local mic and start capturing audio streams.

```
const roomEngine = new TUIRoomEngine();await roomEngine.openLocalMicrophone();
```

Returnsï¼*Promise<void>*

### closeLocalMicrophone

Close the local mic.

```
const roomEngine = new TUIRoomEngine();await roomEngine.closeLocalMicrophone();
```

Returnsï¼*Promise<void>*

### updateVideoQuality

Set the codec parameters of the local video stream, default is TUIVideoProfile.kVideoQuality_720P.

```
const roomEngine = new TUIRoomEngine();await roomEngine.updateVideoQuality({    quality: TUIVideoQuality.kVideoQuality_540p,});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| quality | [TUIVideoQuality](https://www.tencentcloud.com/document/product/647/54886#TUIVideoQuality) | Required | - | Clear TUIVideoProfile.kVideoQuality_360PSD TUIVideoProfile.kVideoQuality_540PHD TUIVideoProfile.kVideoQuality_720PFull HD TUIVideoProfile.kVideoQuality_1080P |

Returnsï¼*Promise<void>*

### updateAudioQuality

Set Local Audio Parameters.

> Note:This method needs to be set before openLocalMicrophone, otherwise it will not take effect.

```
const roomEngine = new TUIRoomEngine();await roomEngine.setLocalAudioProfile({    audioProfile: TUIAudioProfile.kAudioProfileSpeech,});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| audioProfile | [TUIAudioProfile](https://www.tencentcloud.com/document/product/647/54886#TUIAudioProfile) | Required | - | TUIAudioProfile.kAudioProfileSpeech: Speech Mode; Sample rate: 16kTUIAudioProfile.kAudioProfileDefault: Standard Mode (or Default Mode); Sample rate: 48kTUIAudioProfile.kAudioProfileMusic: Music Mode; Sample rate: 48k |

Returnsï¼*Promise<void>*

### startPushLocalVideo

After entering the room, the local video stream will be pushed to the remote by default. This interface is used to re-push the local video stream to the remote after stopping the push.

```
const roomEngine = new TUIRoomEngine();await roomEngine.startPushLocalVideo();
```

Returnsï¼*Promise<void>*

### stopPushLocalVideo

Stop Pushing Local Video Stream to Remote.

```
const roomEngine = new TUIRoomEngine();await roomEngine.stopPushLocalVideo();
```

Returnsï¼*Promise<void>*

### startPushLocalAudio

After entering the room, the local audio stream will be pushed to the remote by default. This interface is used to re-push the local audio stream to the remote after stopping the push.

```
const roomEngine = new TUIRoomEngine();await roomEngine.startPushLocalAudio();
```

Returnsï¼*Promise<void>*

### stopPushLocalAudio

Stop Pushing Local Audio Stream to Remote.

```
const roomEngine = new TUIRoomEngine();await roomEngine.stopPushLocalAudio();
```

Returnsï¼*Promise<void>*

### setRemoteVideoView

Set Remote Stream Rendering Area.

```
const roomEngine = new TUIRoomEngine();// Set the remote user's video stream to play in the area with id 'remote_preview_camera'await roomEngine.setRemoteVideoView({   userId: 'user_1234',   streamType: TUIVideoStreamType.kCameraStream,   view: 'remote_preview_camera',});// Set the remote user's screen sharing stream to play in the area with id 'remote_preview_screen'await roomEngine.setRemoteVideoView({   userId: 'user_1234',   streamType: TUIVideoStreamType.kScreenStream,   view: 'remote_preview_screen',});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/54886#TUIVideoStreamType) | Required | - | User Stream Type |
| view | string | Required | - | The id of the div element playing the remote user's stream |

Returnsï¼*Promise<void>*

### startPlayRemoteVideo

Start Playback of Remote User Video Stream.

```
const roomEngine = new TUIRoomEngine();await roomEngine.startPlayRemoteVideo({   userId: 'user_1234',   streamType: TUIVideoStreamType.kCameraStream,});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/54886#TUIVideoStreamType) | Required | - | User Stream TypeTUIVideoStreamType.kCameraStream Video StreamTUIVideoStreamType.kScreenStream Screen Sharing StreamTUIVideoStreamType.kCameraStreamLow Low Definition Video Stream |

Returnsï¼*Promise<void>*

### stopPlayRemoteVideo

Stop Playback of Remote User Video Stream.

```
const roomEngine = new TUIRoomEngine();await roomEngine.stopPlayRemoteVideo({   userId: 'user_1234',   streamType: TUIVideoStreamType.kCameraStream,});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/54886#TUIVideoStreamType) | Required | - | User Stream TypeTUIVideoStreamType.kCameraStream Video StreamTUIVideoStreamType.kScreenStream Screen Sharing StreamTUIVideoStreamType.kCameraStreamLow Low Definition Video Stream |

Returnsï¼*Promise<void>*

### muteRemoteAudioStream

Stop Remote User's Audio Stream.

```
const roomEngine = new TUIRoomEngine();await roomEngine.muteRemoteAudioStream({  userId: 'user_1234',  isMute: true,});
```

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| isMute | boolean | Required | - | Whether to Stop Remote User's Audio |

### openRemoteDeviceByAdmin

Request Remote User to Open Media Device.

```
const roomEngine = new TUIRoomEngine();const requestId = roomEngine.openRemoteDeviceByAdmin({    userId: 'user_1234',    device: TUIMediaDevice.kMicrophone  //The requested device is a mic    timeout: 0,    requestCallback: ({ requestCallbackType, requestId, userId, code, message }) => {     switch (requestCallbackType) {       case TUIRequestCallbackType.kRequestAccepted:         // Request Accepted         break;       case TUIRequestCallbackType.kRequestRejected:         // Request Rejected         break;       case TUIRequestCallbackType.kRequestCancelled:         // Request Canceled         break;       case TUIRequestCallbackType.kRequestTimeout:         // Request Timeout         break;       case TUIRequestCallbackType.kRequestError:         // Request Error         break;       default:         break;     }   },});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | UserÂ ID |
| device | [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/54886#TUIMediaDevice) | Required | - | Media Device Type (Camera/Mic/Screen Sharing) |
| timeout | number | Required | - | Timeout Time. If timeout is set to 0, there is no timeout time |
| requestCallback | Function | Optional | Empty Function | Request Callback, used to notify the initiator of the request being accepted/rejected/canceled/timeout/error |

Returnsï¼*Promise<string> requestId*

This interface returns requestId, users can use this requestId to call cancelRequest interface to cancel the request.

> **Description:**In v1.0.2 and above, the requestId returned by this interface is of type string; in v1.0.0 and v1.0.1, the requestId returned by this interface is of type number;

### applyToAdminToOpenLocalDevice

Participant applies to the host to open the device.

```
const roomEngine = new TUIRoomEngine();const requestId = roomEngine.applyToAdminToOpenLocalDevice({    device: TUIMediaDevice.kMicrophone  //The requested device is a mic    timeout: 0,    requestCallback: ({ requestCallbackType, requestId, userId, code, message }) => {     switch (requestCallbackType) {       case TUIRequestCallbackType.kRequestAccepted:         // Request Accepted         break;       case TUIRequestCallbackType.kRequestRejected:         // Request Rejected         break;       case TUIRequestCallbackType.kRequestCancelled:         // Request Canceled         break;       case TUIRequestCallbackType.kRequestTimeout:         // Request Timeout         break;       case TUIRequestCallbackType.kRequestError:         // Request Error         break;       default:         break;     }   },});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| device | [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/54886#TUIMediaDevice) | Required | - | Media Device Type (Camera/Mic/Screen Sharing) |
| timeout | number | Required | - | Timeout Time. If timeout is set to 0, there is no timeout time |
| requestCallback | Function | Optional | Empty Function | Request Callback, used to notify the initiator of the request being accepted/rejected/canceled/timeout/error |

Returnsï¼*Promise<string> requestId*

This interface returns requestId, users can use this requestId to call cancelRequest interface to cancel the request.

### closeRemoteDeviceByAdmin

Close Remote User Media Device.

```
const roomEngine = new TUIRoomEngine();await roomEngine.closeRemoteDeviceByAdmin({   userId: 'user_1234',   device: TUIMediaDevice.kMicrophone, //Close mic });
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| device | [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/54886#TUIMediaDevice) | Required | - | Media Device Type (Camera/Mic/Screen Sharing) |

### cancelRequest

Cancel Already Sent Request.

```
const roomEngine = new TUIRoomEngine();await roomEngine.cancelRequest({   requestId: '',    // Please use Actual requestId});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| requestId | string | Required | - | Request ID |

**Returns**ï¼*Promise<string>*requestId

This interface returns requestId, users can use this requestId to call cancelRequest interface to cancel the request

> **Note:**In v1.0.2 and above, the requestId returned by this interface is of type string; in v1.0.0 and v1.0.1, the requestId returned by this interface is of type number;

### responseRemoteRequest

Reply to Remote User's Request.

```
const roomEngine = new TUIRoomEngine();// Agree to Remote User's Requestawait roomEngine.responseRemoteRequest({ requestId: '',    // Please use Actual requestId agree: true,});// Reject Remote User's Requestawait roomEngine.responseRemoteRequest({ requestId: '',    // Please use Actual requestId agree: false,});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| requestId | string | Required | - | Request ID |
| agree | boolean | Required | - | Whether to Agree |

**Returns**ï¼*Promise<void>*

> **Noteï¼**In v1.0.2 and above, the requestId returned by this interface is of type string; in v1.0.0 and v1.0.1, the requestId returned by this interface is of type number;

### disableDeviceForAllUserByAdmin

Prohibit/Allow All Users to Open Media Device (This Interface is invalid for Room Owner and Administrator).

```
// Example 1: Prohibit All Users to Open Micawait roomEngine.disableDeviceForAllUserByAdmin({  device: TUIMediaDevice.kMicrophone,  isDisable: true,})// Example 2: Allow All Users to Open Micawait roomEngine.disableDeviceForAllUserByAdmin({  device: TUIMediaDevice.kMicrophone,  isDisable: false,})
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| device | [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/54886#TUIMediaDevice) | Required | - | Disabled Media Device Type (Camera/Mic/Screen Sharing) |
| isDisable | boolean | Required | - | Whether it is Prohibited |

Returnsï¼*Promise<void>*

### disableSendingMessageForAllUser

Whether All Users are Allowed to Send Messages (This Interface is invalid for Room Owner and Administrator).

```
await roomEngine.disableSendingMessageForAllUser({  isDisable: true,});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| isDisable | boolean | Required | - | Whether it is Disabled |

Returnsï¼*Promise<void>*

### disableSendingMessageByAdmin

Whether Specific User is Allowed to Send Messages.

```
await roomEngine.disableSendingMessageByAdmin({  userId: 'user_1234',  isDisable: true,});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| isDisable | boolean | Required | - | Whether it is Disabled |

Returnsï¼*Promise<void>*

### changeUserRole

Change User's Role (Only the Host can call this Interface).

```
const roomEngine = new TUIRoomEngine();// Transfer the Room to User user_1234await roomEngine.changeUserRole({   userId: 'user_1234',   role: TUIRole.kRoomOwner,});// Set user_1234 as Room Administratorawait roomEngine.changeUserRole({  userId: 'user_1234',  userRole: TUIRole.kAdministrator,});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| userRole | [TUIRole](https://www.tencentcloud.com/document/product/647/54886#TUIRole) | Required | - | User RoleHost  TUIRole.kRoomOwnerAdministrator  TUIRole.kAdministratorGeneral Member  TUIRole.kGeneralUser |

Returnsï¼*Promise<void>*

### kickRemoteUserOutOfRoom

Kick Out User from Room (Only Host and Administrator can call this Interface).

```
const roomEngine = new TUIRoomEngine();await roomEngine.kickRemoteUserOutOfRoom({   userId: 'user_1234',});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |

Returnsï¼*Promise<void>*

### setMaxSeatCount

Set Room Seat Maximum Value

When roomType is TUIRoomType.kConference (Education and Conference Scene), maxSeatCount value is not limited;

When roomType is TUIRoomType.kLivingRoom (Live Scene), maxSeatCount is limited to 16;

```
const roomEngine = new TUIRoomEngine();await roomEngine.createRoom({ roomId: '12345' });await roomEngine.setMaxSeatCount({ maxSeatCount: 16 })
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| maxSeatCount | number | Required | - | Set Room Seat Maximum Value |

Returnsï¼Promise<void>

### getSeatList

Get Seat List

```
const roomEngine = new TUIRoomEngine();const seatList = await roomEngine.getSeatList();
```

**Returns**ï¼*Promise<*[TUISeatInfo](https://www.tencentcloud.com/document/product/647/54886#TUISeatInfo)*[]>*seatList

seatList for the Current Room's All Seat List

### takeSeat

Mic-off Users can call takeSeat to become Mic-on Users, only Mic-on Users can Publish Local stream.

- When roomInfo.roomType is TUIRoomType.kConference and roomInfo.speechMode is TUISpeechMode.kSpeakAfterTakingSeat, General Users need to Wait for the Host/Administrator's Agreement to become Mic-on Users after calling takeSeat method.
- When roomInfo.roomType is TUIRoomType.kLivingRoom and roomInfo.speechMode is TUISpeechMode.kFreeToSpeak, General Users become Mic-on Users after calling takeSeat method Successfully.
- Host & Administrator become Mic-on Users after calling takeSeat Successfully.
- Changes of Mic-on Users are Notified to All Users through TUIRoomEvents.onSeatListChanged.

```
const roomEngine = new TUIRoomEngine();// Scenario 1: Host/Administrator Go Live// Scenario 2: When roomInfo.roomType is TUIRoomType.kConference // and roomInfo.speechMode is TUISpeechMode.kSpeakAfterTakingSeat, General Users Go Liveawait roomEngine.takeSeat({ seatIndex: -1, timeout: 0,});    // Scenario 3: When roomInfo.enableSeatControl is true, General Users Go Liveconst requestId = await roomEngine.instance?.takeSeat({   seatIndex: -1,   timeout: 0,   requestCallback: ({ requestCallbackType, requestId, userId, code, message }) => {      switch (requestCallbackType) {       case TUIRequestCallbackType.kRequestAccepted:         // Request Accepted         break;       case TUIRequestCallbackType.kRequestRejected:         // Request Rejected         break;       case TUIRequestCallbackType.kRequestCancelled:         // Request Canceled         break;       case TUIRequestCallbackType.kRequestTimeout:         // Request Timeout         break;       case TUIRequestCallbackType.kRequestError:         // Request Error         break;       default:         break;   } },});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| seatIndex | number | Required | - | Seat index, set to -1 when there is No Serial Number |
| timeout | number | Required | - | Timeout. If timeout is set to 0, there is no Timeout |
| requestCallback | Function | Optional | Empty Function | Callback, used to Notify Initiator of Request being Accepted/Rejected/Cancelled/Timeout/Error |

**Returns**ï¼Promise<string> requestId

When roomInfo.enableSeatControl is true, General Users call this Interface to return requestId, General Users can use this requestId to call cancelRequest Interface to cancel Go Live Requestã

> **Note:**In v1.0.2 and above, the requestId returned by this interface is of type string; in v1.0.0 and v1.0.1, the requestId returned by this interface is of type number;

### leaveSeat

Release Seat.

```
const roomEngine = new TUIRoomEngine();await roomEngine.leaveSeat();
```

**Returns**ï¼*Promise<void>*

### takeUserOnSeatByAdmin

Invite Others to Go Live.

```
const roomEngine = new TUIRoomEngine();const requestId = roomEngine.takeUserOnSeatByAdmin({    seatIndex: 0,    userId: 'user_1234',    timeout: 0,    requestCallback: ({ requestCallbackType, requestId, userId, code, message }) => {     switch (requestCallbackType) {       case TUIRequestCallbackType.kRequestAccepted:         // Request Accepted         break;       case TUIRequestCallbackType.kRequestRejected:         // Request Rejected         break;       case TUIRequestCallbackType.kRequestCancelled:         // Request Canceled         break;       case TUIRequestCallbackType.kRequestTimeout:         // Request Timeout         break;       case TUIRequestCallbackType.kRequestError:         // Request Error         break;       default:         break;     }   },});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| seatIndex | number | Required | - | Seat index |
| userId | string | Required | - | UserÂ ID |
| timeout | number | Required | - | Timeout. If timeout is set to 0, there is no Timeout |
| requestCallback | Function | Optional | Empty Function | Callback, used to Notify Initiator of Request being Accepted/Rejected/Cancelled/Timeout/Error |

**Returns**ï¼*Promise<string> requestId*

This Interface returns requestId, Users can use this requestId to call cancelRequest Interface to cancel Request.

> **Note:**In v1.0.2 and above, the requestId returned by this interface is of type string; in v1.0.0 and v1.0.1, the requestId returned by this interface is of type number;

### kickUserOffSeatByAdmin

Ask others to get off the mic

```
const roomEngine = new TUIRoomEngine();const requestId = await roomEngine.kickUserOffSeatByAdmin({   seatIndex: 0,   userId: 'user_1234',});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| seatIndex | number | Required | - | Seat index |
| userId | string | Required | - | User ID |

**Returns**ï¼*Promise<void>*

### lockSeatByAdmin

Lock a certain mic position status (Only the room host and administrator can call this method).

```
const roomEngine = new TUIRoomEngine();await roomEngine.lockSeatByAdmin({   seatIndex: 0,   lockParams: {      lockSeat: true,      lockVideo: true,      lockAudio: true,   },});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| seatIndex | number | Required | - | Mic position index |
| lockParams | [TUISeatLockParams](https://www.tencentcloud.com/document/product/647/54886#TUISeatLockParams) | Required | - | Lock mic parameter |

Returnsï¼*Promise<void>*

### startScreenSharingElectron

Start Screen Sharing Electronã

```
const roomEngine = new TUIRoomEngine();await roomEngine.startScreenSharingElectron('targetId');
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| targetId | string | Optional | - | Sharing Window ID, can be obtained from getScreenSharingTarget |

**Returns**ï¼*Promise<void>*

### stopScreenSharingElectron

Stop Screen Sharing Electronã

```
const roomEngine = new TUIRoomEngine();await roomEngine.stopScreenSharingElectron();
```

**Returns**ï¼*Promise<void>*

### getScreenSharingTarget

Get Screen Sharing list Electronã

```
const roomEngine = new TUIRoomEngine();const screenList = await roomEngine.getScreenSharingTarget();
```

**Returns**ï¼*Promise<void>*

### selectScreenSharingTarget

Switch Screen Sharing Window Electronã

```
const roomEngine = new TUIRoomEngine();await roomEngine.selectScreenSharingTarget('targetId');
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| targetId | string | Required | - | Sharing Window ID, can be obtained from getScreenSharingTarget |

**Returns**ï¼*Promise<void>*

### sendTextMessage

Send text message.

```
const roomEngine = new TUIRoomEngine();await roomEngine.sendTextMessage({ messageText: 'hello, everyone',});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| messageText | string | Required | - | Text message content |

**Returns**ï¼*Promise<void>*

### sendCustomMessage

Send custom message.

```
const roomEngine = new TUIRoomEngine();await roomEngine.sendCustomMessage({ messageText: '{ data:'', description: ''}',});
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| messageText | string | Required | - | Custom message content |

**Returns**ï¼*Promise<void>*

### getCameraDevicesList

Get camera device list.

```
 const roomEngine = new TUIRoomEngine(); const cameraList = await roomEngine.getCameraDevicesList(); for (i = 0; i < cameraList.length; i++) {    var camera = cameraList[i];    console.info("camera deviceName: " + camera.deviceName + " deviceId:" + camera.deviceId); }
```

**Returns:** *Promise<*[TRTCDeviceInfo](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCDeviceInfo.html)*[]>*cameraList

### getMicDevicesList

Get mic device list.

```
 const roomEngine = new TUIRoomEngine(); const micList = await roomEngine.getMicDevicesList(); for (i = 0; i < micList.length; i++) {    var mic = micList[i];    console.info("mic deviceName: " + mic.deviceName + " deviceId:" + mic.deviceId); }
```

**Returns:** *Promise<*[TRTCDeviceInfo](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCDeviceInfo.html)*[]>*micList

### getSpeakerDevicesList

Get speaker device list.

```
 const roomEngine = new TUIRoomEngine(); const speakerList = await roomEngine.getSpeakerDevicesList(); for (i = 0; i < speakerList.length; i++) {    var speaker = speakerList[i];    console.info("speaker deviceName: " + speaker.deviceName + " deviceId:" + speaker.deviceId); }
```

**Returns:** *Promise<*[TRTCDeviceInfo](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCDeviceInfo.html)*[]>* speakerList

### setCurrentCameraDevice

Set the camera device to be used.

```
const roomEngine = new TUIRoomEngine();await roomEngine.setCurrentCameraDevice({ deviceId: '' });
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| deviceId | string | Required | - | Device ID obtained from getCameraDevicesList |

**Returns**ï¼***void***

### setCurrentMicDevice

Set the mic device to be used.

```
const roomEngine = new TUIRoomEngine();await roomEngine.setCurrentMicDevice({ deviceId: '' });
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| deviceId | string | Required | - | Device ID obtained from getSpeakerDevicesList |

**Returns**ï¼***void***

### setCurrentSpeakerDevice

Get the currently used camera device.

```
const roomEngine = new TUIRoomEngine();await roomEngine.setCurrentSpeakerDevice({ deviceId: '' });
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| deviceId | string | Required | - | Device ID obtained from getSpeakerDevicesList |

**Returns**ï¼*void*

### getCurrentCameraDevice

Get the currently used camera device.

```
const roomEngine = new TUIRoomEngine();const currentCameraDevice = roomEngine.getCurrentCameraDevice();
```

**Returns**ï¼[TRTCDeviceInfo](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCDeviceInfo.html)

Device information, can get device ID and device name

### getCurrentMicDevice

Get the currently used mic device.

```
const roomEngine = new TUIRoomEngine();const currentMicDevice = roomEngine.getCurrentMicDevice();
```

**Returns**ï¼[TRTCDeviceInfo](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCDeviceInfo.html)

Device information, can get device ID and device name

### getCurrentSpeakerDevice

Get the currently used speaker device.

```
const roomEngine = new TUIRoomEngine();const currentSpeakerDevice = roomEngine.getCurrentSpeakerDevice();
```

**Returns**ï¼[TRTCDeviceInfo](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCDeviceInfo.html)

Device information, can get device ID and device name

### startCameraDeviceTest

Start camera test.

```
const roomEngine = new TUIRoomEngine();await roomEngine.startCameraDeviceTest({ view: 'test-preview' });
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| view | string | Required | - | Display the video area of the camera test, the input view is the Id of the div element carrying the preview screen |

**Returns**ï¼*Promise<void>*

### stopCameraDeviceTest

Stop camera test.

```
const roomEngine = new TUIRoomEngine();await roomEngine.stopCameraDeviceTest();
```

**Returns**ï¼*Promise<void>*

### on

Listen to roomEngine events.

```
const roomEngine = new TUIRoomEngine();roomEngine.on(event, func);
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| event | [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/54884) | Required | - | TUIRoomEngine event list |
| func | Function | Required | - | Event callback function |

**Returns**ï¼***void***

### off

Cancel listening to roomEngine events

```
const roomEngine = new TUIRoomEngine();roomEngine.off(event, func);
```

Parameter:

| Parameter | Type | Description | Default Value | Meaning |
| --- | --- | --- | --- | --- |
| event | [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/54884) | Required | - | TUIRoomEngine event list |
| func | Function | Required | - | Event callback function |

**Returns**ï¼***void***

### getTRTCCloud

Get trtcCloud instance, for web-side trtcCloud capabilities, please check: [TRTCCloud API documentation](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/index.html).

```
const roomEngine = new TUIRoomEngine();const trtcCloud = roomEngine.getTRTCCloud();
```

**Returns**ï¼[TRTCCloud](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/index.html)**

### getTIM

Get tim instance, for web-side tim capabilities, please check: [IM API documentation](https://web.sdk.qcloud.com/im/doc/zh-cn/SDK.html)

```
const roomEngine = new TUIRoomEngine();const trtcCloud = roomEngine.getTIM();
```

**Returns**ï¼*TIM*


---
*Source: [https://trtc.io/document/54883](https://trtc.io/document/54883)*
