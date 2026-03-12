# TUIRoomEngine

## TUIRoomEngine Introduction

TUIRoomEngine SDK TUIRoomEngine SDK provides general **audio and video** room management, member management, interactive control, instant messaging, and other features, supporting two typical scenarios: Conference and Live.

**Installation:**

```
// Use npmnpm i @tencentcloud/tuiroom-engine-electron --save// Use pnpmpnpm i @tencentcloud/tuiroom-engine-electron --save// Use yarnyarn add @tencentcloud/tuiroom-engine-electron
```

## TUIRoomEngine API

### **TUIRoomEngine Static Methods**

| API | Validation |
| --- | --- |
| [once](https://www.tencentcloud.com/document/product/647/64342#once) | Listening TUIRoomEngine ready event.**Note:**All methods other than TUIRoomEngine.init must be executed after the TUIRoomEngine ready event is received and the TUIRoomEngine.init method is successfully executed. |
| [login](https://www.tencentcloud.com/document/product/647/64342#login) | Log in to TUIRoomEngine |
| [logout](https://www.tencentcloud.com/document/product/647/64342#logout) | Log out of TUIRoomEngine |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/64342#setSelfInfo) | Set basic information of the current user (user name, user avatar) |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/64342#getSelfInfo) | Get basic information of the current user (user name, user avatar) |
| [getDeviceManager](https://www.tencentcloud.com/document/product/647/64342#getDeviceManager) | Get device manager |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/64342#getAudioEffectManager) | Get audio effect manager |
| [getMediaMixingManager](https://www.tencentcloud.com/document/product/647/64342#getMediaMixingManager) | Get media source mixing manager |
| [getVideoEffectPluginManager](https://www.tencentcloud.com/document/product/647/64342#getVideoEffectPluginManager) | Get video effect plugin manager |

### **roomEngine Room Management API**

| API | Validation |
| --- | --- |
| [createRoom](https://www.tencentcloud.com/document/product/647/64342#createRoom) | Create a room |
| [enterRoom](https://www.tencentcloud.com/document/product/647/64342#enterRoom) | Enter a room |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/64342#destroyRoom) | Destroy a room |
| [exitRoom](https://www.tencentcloud.com/document/product/647/64342#exitRoom) | Exit a room |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/64342#fetchRoomInfo) | Fetch room information |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/64342#updateRoomNameByAdmin) | Update room name (Only available to room owners or administrators) |
| [updateRoomSeatModeByAdmin](https://www.tencentcloud.com/document/product/647/64342#updateRoomSeatModeByAdmin) | Update room seat mode (Only available to room owners or administrators) |
| [getUserList](https://www.tencentcloud.com/document/product/647/64342#getUserList) | Get members list |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/64342#getUserInfo) | Get member detail information |

### **roomEngine Video and Audio API**

| API | Validation |
| --- | --- |
| [setLocalVideoView](https://www.tencentcloud.com/document/product/647/64342#setLocalVideoView) | Set the HTML element where to play local camera video stream |
| [openLocalCamera](https://www.tencentcloud.com/document/product/647/64342#openLocalCamera) | Open local camera |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/64342#closeLocalCamera) | Close local camera |
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/64342#openLocalMicrophone) | Open local microphone |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/64342#closeLocalMicrophone) | Close local microphone |
| [updateVideoQuality](https://www.tencentcloud.com/document/product/647/64342#updateVideoQuality) | Set local video parameters |
| [setVideoResolutionMode](https://www.tencentcloud.com/document/product/647/64342#setVideoResolutionMode) | Set the resolution mode of the local video stream |
| [updateVideoQualityEx](https://www.tencentcloud.com/document/product/647/64342#updateVideoQualityEx) | Set local video encoding parameters |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/64342#updateAudioQuality) | Set local audio parameters |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/64342#startPushLocalVideo) | Start pushing the local video stream to the remote end |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/64342#stopPushLocalVideo) | Stop pushing the local video stream to the remote end |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/64342#muteLocalAudio) | Stop pushing the local audio stream to the remote end |
| [unmuteLocalAudio](https://www.tencentcloud.com/document/product/647/64342#unmuteLocalAudio) | Start pushing the local audio stream to the remote end |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/64342#setRemoteVideoView) | Set the HTML element where to play the remote video stream |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/64342#startPlayRemoteVideo) | Start playing the remote user's video stream |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/64342#stopPlayRemoteVideo) | Stop playing the remote user's video stream |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/64342#muteRemoteAudioStream) | Stop the remote user's audio stream |

### **roomEngine Member Management API**

| API | Validation |
| --- | --- |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/64342#cancelRequest) | Cancel a request already sent |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/64342#responseRemoteRequest) | Response to remote use request |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/64342#changeUserRole) | Change user role |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/64342#kickRemoteUserOutOfRoom) | Kick user out of current room |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/64342#disableSendingMessageByAdmin) | Disable/Enable instant message chat |

### **roomEngine Seat Management API**

| API | Validation |
| --- | --- |
| [getSeatList](https://www.tencentcloud.com/document/product/647/64342#getSeatList) | Get seats information |
| [takeSeat](https://www.tencentcloud.com/document/product/647/64342#takeSeat) | Take a seat |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/64342#leaveSeat) | Release a seat |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/64342#takeUserOnSeatByAdmin) | Invite someone else to speak (only available to room owner and administrators) |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/64342#kickUserOffSeatByAdmin) | Kick someone off the seat (only available to room owner and administrators) |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/64342#lockSeatByAdmin) | Lock a seat (only available to room owner and administrators) |
| [getSeatApplicationList](https://www.tencentcloud.com/document/product/647/64342#getSeatApplicationList) | Get the list of speaking requests |

### **roomEngine Screen/Window Sharing API**

| API | Validation |
| --- | --- |
| [startScreenSharingElectron](https://www.tencentcloud.com/document/product/647/64342#startScreenSharingElectron) | Start screen or window sharing |
| [stopScreenSharingElectron](https://www.tencentcloud.com/document/product/647/64342#stopScreenSharingElectron) | Stop screen or window sharing |
| [getScreenSharingTarget](https://www.tencentcloud.com/document/product/647/64342#getScreenSharingTarget) | Get the screens and windows to be shared |
| [selectScreenSharingTarget](https://www.tencentcloud.com/document/product/647/64342#selectScreenSharingTarget) | Select the screen or window to share |

### **roomEngine Event Listening API**

| API | Validation |
| --- | --- |
| [on](https://www.tencentcloud.com/document/product/647/64342#on) | Add [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/64350#) event listener |
| [off](https://www.tencentcloud.com/document/product/647/64342#off) | Remove [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/64350#) event listener |

### **roomEngine Malicious API**

| API | Validation |
| --- | --- |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/64342#getTRTCCloud) | Get TRTCCloud instance |
| [getTIM](https://www.tencentcloud.com/document/product/647/64342#getTIM) | Get TIM/Chat instance |

## API Description

### once

Listening TUIRoomEngine 'ready' event

```
TUIRoomEngine.once('ready', () => {  const roomEngine = new TUIRoomEngine();    await TUIRoomEngine.init({    sdkAppId: 0,   // Fill your `sdkAppId`    userId: '',    // Fill your `userId`    userSig: '',   // Fill your `userSig`   });    await roomEngine.createRoom({    roomId: '12345',   // Fill room ID of type string    name: 'Test Room',     // Fill room name, default value is `roomId`, maximize length: 30    roomType: TUIRoomType.kLive, // Room type should be `TUIRoomType.kLive`  });});
```

### login

Log in to TUIRoomEngine. Other API can work only after `login` successfully.

```
// Log in to TUIRoomEngineawait TUIRoomEngine.login({ sdkAppId: 0,   // Fill your `sdkAppId` userId: '',    // Fill your `userId` userSig: '',   // Fill the `userSig` responded from server or generated locally.});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| sdkAppId | number | Required | - | sdkAppIdOn [TRTC Cloud Console](https://console.trtc.io/) Click `Application Management` > `Create Application`. After creation, you can get the `sdkappId` from application detail information. |
| userId | string | Required | - | It is recommended that the user ID be limited to 32 bytes and only contain uppercase and lowercase letters (a-zA-Z), digits (0-9), underscores, and hyphens. |
| userSig | string | Required | - | userSigFor detail about what and how to generate `userSig`, please refer to the online documentation:[UserSig](https://www.tencentcloud.com/document/product/647/35166). |
| tim | TIM | Not required | - | If you want to use more capabilities of the Instant Messaging SDK while connecting to roomEngine, you can pass the created tim instance into TUIRoomEngine. For the creation method of the tim instance, please refer to:[TIM.create](https://web.sdk.qcloud.com/im/doc/en/TIM.html#.create). |

**Returns***Promise<void>*

### **logout**

Log out of TUIRoomEngineã

```
// Log out of TUIRoomEngineawait TUIRoomEngine.logout();
```

Returns*Promise<void>*

### setSelfInfo

Set basic information of the current user (user name, user avatar)

```
// Set basic information of the current user (user name, user avatar)await TUIRoomEngine.setSelfInfo({ userName: '',     // Fill your `userName` avatarUrl: '',    // Fill your avatar URL});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userName | string | Required | - | User name |
| avatarUrl | string | Required | - | User avatar |

**Returns***Promise<void>*

### **getSelfInfo**

Get basic information of the current user (user name, user avatar)

```
// Get basic information of the current user (user name, user avatar)const loginUserInfo = await TUIRoomEngine.getSelfInfo();
```

Returns*Promise<*[TUILoginUserInfo](https://www.tencentcloud.com/document/product/647/64351#tuiloginuserinfo)*> loginUserInfo*

**

### getDeviceManager

Get device manager

```
import TUIRoomEngine, {  TUIDeviceManager} from '@tencentcloud/tuiroom-engine-electron';const deviceManager:TUIDeviceManager = TUIRoomEngine.getDeviceManager();
```

Returns [TUIDeviceManager](https://www.tencentcloud.com/document/product/647/64352)

### getAudioEffectManager

Get audio effect manager

```
import TUIRoomEngine, {  TUIAudioEffectManager} from '@tencentcloud/tuiroom-engine-electron';const audioEffectManager: TUIAudioEffectManager = TUIRoomEngine.getAudioEffectManager();
```

Return [TUIAudioEffectManager](https://www.tencentcloud.com/document/product/647/64353)

### getMediaMixingManager

Get media source mixing manager

```
import TUIRoomEngine, { TUIMediaMixingManager } from '@tencentcloud/tuiroom-engine-electron';const mediaMixingManager: TUIMediaMixingManager = TUIRoomEngine.getMediaMixingManager();
```

Return [TUIMediaMixingManager](https://www.tencentcloud.com/document/product/647/64354)

### getVideoEffectPluginManager

Get video effect plugin manager

```
import TUIRoomEngine, {  TUIVideoEffectPluginManager} from '@tencentcloud/tuiroom-engine-electron';const videoEffectPluginManager: TUIVideoEffectPluginManager = TUIRoomEngine.getVideoEffectPluginManager();
```

Return [TUIVideoEffectPluginManager](https://www.tencentcloud.com/document/product/647/64355)

### createRoom

When the host creates a room, the user who calls createRoom becomes the owner of the room. When creating a room, you can set the room ID, room name, room type, whether to enable seat control, whether to allow users to join and enable audio and video, send messages, and other features.

```
const roomEngine = new TUIRoomEngine();await roomEngine.createRoom({    roomId: '12345',   // Fill the `roomId`of string type    roomName: 'Test Room',     // Enter your room name. The room name defaults to roomId and can be up to 30 bytes long.    roomType: TUIRoomType.kLive, // The room type must be `TUIRoomType.kLive` for online living    isSeatEnabled: false, // Whether to enable microphone seat control.    isMicrophoneDisableForAllUser: false,  // Whether to allow joining users to turn on the microphone.    isCameraDisableForAllUser: false,  // Whether to allow joining users to turn on the camera.    isMessageDisableForAllUser: false,  // Whether to allow joining users to send instance message.});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| roomId | string | Required | - | Room ID is limited to 64 bytes in length and only supports the following character sets:Uppercase and lowercase English letters (a-zA-Z), number(0-9), Space ! # $ % & ( ) + - : ; < = . > ? @ [ ] ^ _ { } \| ~ , |
| roomName | string | Optional | roomId | Room name, default to `roomId`, cannot be empty. |
| roomType | [TUIRoomType](https://www.tencentcloud.com/document/product/647/64351#tuiroomtype) | Optional | TUIRoomType.kConference | Room typeFor office collaboration, medical consultation, remote meetings, and educational scenarios, set roomType to TUIRoomType.kConference, for e-commerce live streaming and voice chat room scenarios, set roomType to TUIRoomType.kLive. |
| isSeatEnabled | boolean | Optional | false | Whether to enable microphone seat control. Default is `false` to not enable. |
| seatMode | [TUISeatMode](https://www.tencentcloud.com/document/product/647/64351#tuiseatmode) | Optional | TUISeatMode.kFreeToTake | Seat mode(enable when microphone seat controlling is enabled), default value:`TUISeatMode.kFreeToTake``TUISeatMode.kFreeToTake`: user can open or close microphone and camera freely without requesting for permission. When `seatMode`is `TUISeatMode.kApplyToTake`TUISeatMode.kApplyToTake: Audience members need the approval of the room owner or administrator before they can speak. |
| isMicrophoneDisableForAllUser | boolean | Optional | false | Whether to disable users to control their microphones. Not disabled by default. |
| isCameraDisableForAllUser | boolean | Optional | false | Whether to disable users to control their cameras. Not disabled by default. |
| isMessageDisableForAllUser | boolean | Optional | false | Whether to disable users to send instance messages. Not disabled by default. |
| maxSeatCount | number | Optional | - | Maximum number of seatsWhen `roomType` is `TUIRoomType.kConference`(education and meeting scenarios), there is no limit on the `maxSeatCount` value.When `roomType` is `TUIRoomType.kLivingRoom`(living scenarios), the maximum value for `maxSeatCount` is 16. |
| enableCDNStreaming | boolean | Optional | false | Whether to enable CDN live streaming. |
| cdnStreamDomain | string | Optional | '' | The URL domain to receive living stream. |

Returns*Promise<void>*

### enterRoom

Enter a room.

```
const roomEngine = new TUIRoomEngine();const roomInfo = await roomEngine.enterRoom({    roomId: '12345',    roomType: TUIRoomType.kLive});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| roomId | string | Required | - | Room ID |
| roomType | [TUIRoomType](https://www.tencentcloud.com/document/product/647/64351#tuiroomtype) | Optional | TUIRoomType.kConference | Room type |

**Returns***Promise<*[TUIRoomInfo](https://www.tencentcloud.com/document/product/647/64351#tuiroominfo)*> roomInfo*

Get video effect plugin manager

### destroyRoom

Room destroying API. Only the room owner can initiate the destroying. Once dissolved, the room cannot be entered.

```
const roomEngine = new TUIRoomEngine();await roomEngine.destroyRoom();
```

**Returns***Promise<void>*

### exitRoom

After invoking enterRoom, users can leave the room by calling exitRoom.

```
const roomEngine = new TUIRoomEngine();await roomEngine.exitRoom();
```

**Returns***Promise<void>*

### fetchRoomInfo

Fetch room information

```
const roomEngine = new TUIRoomEngine();const roomInfo = roomEngine.fetchRoomInfo();
```

Returns:*Promise<*[TUIRoomInfo](https://www.tencentcloud.com/document/product/647/64351#tuiroominfo)*> roomInfo*

### updateRoomNameByAdmin

Update room name (Only available to room owners or administrators)

```
const roomEngine = new TUIRoomEngine();await roomEngine.createRoom({ roomId: '12345' });await roomEngine.updateRoomNameByAdmin({ roomName: 'New room name' });
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| roomName | string | Required | - | Room name that can not be empty string. |

**Returns***Promise<void>*

### updateRoomSeatModeByAdmin

Update room seat mode (Only available to room owners or administrators)

```
const roomEngine = new TUIRoomEngine();await roomEngine.createRoom({ roomId: '12345' });await roomEngine.updateRoomSeatModeByAdmin({  seatMode: TUISeatMode.kApplyToTake,  // Update room seat mode});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| seatMode | [TUISeatMode](https://www.tencentcloud.com/document/product/647/64351#tuiseatmode) | Required | - | Room seat mode |

### getUserList

Get the current room user list. Note that the maximum number of users that can be pulled at one time by this API is 50.

```
const roomEngine = new TUIRoomEngine();const userList = [];let result;let nextSequence = 0;do {  result = await roomEngine.getUserList({ nextSequence });  userList.push(...result.userInfoList);  nextSequence = result.nextSequence;} while (result.nextSequence !== 0)
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| nextSequence | number | Optional | 0 | Offset. By default, users are pulled starting from offset 0. |

**Returns**:*Promise<object>  result*

result.nextSequence is the offset for the next group user pull. If result.nextSequence is 0, it means the userList has been completely pulled.

result.userInfoList is the userList pulled this time.

### getUserInfo

Get a user detail information

```
const roomEngine = new TUIRoomEngine();const userList = [];const userInfo = await roomEngine.getUserInfo({    userId: 'user_12345',});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | Get a user detail information by user ID. |

**Returns**:*Promise<*[TUIUserInfo](https://www.tencentcloud.com/document/product/647/64351#tuiuserinfo)*> userInfo*

Reture a user detail information

### setLocalVideoView

Set the HTML element where to play local camera video stream

```
const roomEngine = new TUIRoomEngine();    // HTML div element with id 'preview-camera' to play local camera streamawait roomEngine.setLocalVideoView({  view: 'preview-camera',});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| view | string | Required | - | `id` value of HTML element attribute |

Returns:*Promise<void>*

**

### openLocalCamera

Open local camera

```
const roomEngine = new TUIRoomEngine();await roomEngine.setLocalVideoView({  streamType: TUIVideoStreamType.kCameraStream,  view: 'preview-camera',});await roomEngine.openLocalCamera();
```

Returns:*Promise<void>*

### closeLocalCamera

Close local camera

```
const roomEngine = new TUIRoomEngine();await roomEngine.closeLocalCamera();
```

Returns:*Promise<void>*

### openLocalMicrophone

Open local microphone

```
const roomEngine = new TUIRoomEngine();await roomEngine.openLocalMicrophone();
```

Returns:*Promise<void>*

### closeLocalMicrophone

Close local microphone

```
const roomEngine = new TUIRoomEngine();await roomEngine.closeLocalMicrophone();
```

Returns:*Promise<void>*

### updateVideoQuality

Set the encoding parameters of the local camera video stream. The default is TUIVideoProfile.kVideoQuality_720P.

```
const roomEngine = new TUIRoomEngine();await roomEngine.updateVideoQuality({    quality: TUIVideoQuality.kVideoQuality_540p,});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| quality | [TUIVideoQuality](https://www.tencentcloud.com/document/product/647/64351#tuivideoquality) | Required | - | Clear definition TUIVideoProfile.kVideoQuality_360PStandard definition TUIVideoProfile.kVideoQuality_540PHigh definition TUIVideoProfile.kVideoQuality_720PUltra high definition TUIVideoProfile.kVideoQuality_1080P |

Returns:*Promise<void>*

### setVideoResolutionMode

Set the resolution mode of the local video stream. The default is TUIResolutionMode.kResolutionMode_Landscape.

```
const roomEngine = new TUIRoomEngine();await roomEngine.setVideoResolutionMode({  type: TUIVideoStreamType.kCameraStream,  resolutionMode: TUIResolutionMode.kResolutionMode_Landscape,});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64351#tuivideostreamtype) | Required | - | Video stream type |
| resolutionMode | [TUIResolutionMode](https://www.tencentcloud.com/document/product/647/64351#tuiresolutionmode) | Required | TUIResolutionMode.kResolutionMode_Landscape | Resolution mode |

Returns:*Promise<void>*

### updateVideoQualityEx

Set the encoding parameters of the local video stream. The default is TUIVideoProfile.kVideoQuality_720P.

```
const roomEngine = new TUIRoomEngine();await roomEngine.updateVideoQualityEx({  streamType: TUIVideoStreamType.kCameraStream,  encoderParams: {    videoResolution: TUIVideoQuality.kVideoQuality_720p,    fps: 15,    bitrate: 2000,    resolutionMode: TUIResolutionMode.kResolutionMode_Landscape,  }});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64351#tuivideostreamtype) | Required | - | Video stream type |
| encoderParams | [TUIVideoEncoderParams](https://www.tencentcloud.com/document/product/647/64351#tuivideoencoderparams) | Required | - | Detailed encoding parameters |

### updateAudioQuality

Set local audio parameters.

> **Note:**This method needs to be called before calling openLocalMicrophone, otherwise it will not take effect.

```
const roomEngine = new TUIRoomEngine();await roomEngine.updateAudioQuality({    quality: TUIAudioQuality.kAudioProfileMusic,});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| audioProfile | [TUIAudioQuality](https://www.tencentcloud.com/document/product/647/64351#tuiaudioquality) | Required | - | TUIAudioQuality.kAudioProfileSpeech: Speech Mode; Sample Rate: 16kHzTUIAudioQuality.kAudioProfileDefault: Standard mode(Default mode); Sample Rate: 48kHzTUIAudioQuality.kAudioProfileMusic: Music Mode; Sample Rate: 48kHz |

Returns:*Promise<void>*

### startPushLocalVideo

After entering the room, the local video stream will be pushed to the remote end by default. This API is used to push the local video stream to the remote end again after stopping the streaming.

```
const roomEngine = new TUIRoomEngine();await roomEngine.startPushLocalVideo();
```

Returns:*Promise<void>*

### stopPushLocalVideo

Stop pushing the local video stream to the remote end

```
const roomEngine = new TUIRoomEngine();await roomEngine.stopPushLocalVideo();
```

Returns:*Promise<void>*

### muteLocalAudio

Stop pushing the local audio stream to the remote end

```
const roomEngine = new TUIRoomEngine();await roomEngine.muteLocalAudio();
```

Returns:*Promise<void>*

### unmuteLocalAudio

Start pushing the local audio stream to the remote end

```
const roomEngine = new TUIRoomEngine();await roomEngine.unmuteLocalAudio();
```

Returns:*Promise<void>*

### setRemoteVideoView

Set the HTML element where to play the remote video stream

```
const roomEngine = new TUIRoomEngine();// Play remote video at HTML element with id attribute 'remote_preview_camera'await roomEngine.setRemoteVideoView({   userId: 'user_1234',   streamType: TUIVideoStreamType.kCameraStream,   view: 'remote_preview_camera',});// Play remote user screen sharing at HTML element with id attribute 'remote_preview_screen'await roomEngine.setRemoteVideoView({   userId: 'user_1234',   streamType: TUIVideoStreamType.kScreenStream,   view: 'remote_preview_screen',});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64351#tuivideostreamtype) | Required | - | Video stream type |
| view | string | Required | - | `id` value of HTML element attribute |

Returns:*Promise<void>*

### startPlayRemoteVideo

Start playing the remote user's video stream

```
const roomEngine = new TUIRoomEngine();await roomEngine.startPlayRemoteVideo({   userId: 'user_1234',   streamType: TUIVideoStreamType.kCameraStream,});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64351#tuivideostreamtype) | Required | - | User video stream typeTUIVideoStreamType.kCameraStream Camera video streamTUIVideoStreamType.kScreenStream Screen/window sharing video streamTUIVideoStreamType.kCameraStreamLow Camera video stream of Low definition |

Returns:*Promise<void>*

### stopPlayRemoteVideo

Stop playing the remote user's video stream

```
const roomEngine = new TUIRoomEngine();await roomEngine.stopPlayRemoteVideo({   userId: 'user_1234',   streamType: TUIVideoStreamType.kCameraStream,});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64351#tuivideostreamtype) | Required | - | User video stream typeTUIVideoStreamType.kCameraStream Camera video streamTUIVideoStreamType.kScreenStream Screen/window sharing video streamTUIVideoStreamType.kCameraStreamLow Camera video stream of Low definition |

Returns:*Promise<void>*

### muteRemoteAudioStream

Stop the remote user's audio stream

```
const roomEngine = new TUIRoomEngine();await roomEngine.muteRemoteAudioStream({  userId: 'user_1234',  isMute: true,});
```

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| isMute | boolean | Required | - | Whether to stop subscribing  remote user audio |

### cancelRequest

Cancel a request already sent

```
const roomEngine = new TUIRoomEngine();await roomEngine.cancelRequest({   requestId: '',    // Request unique ID});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| requestId | string | Required | - | Request ID |

**Returns**:*Promise<string>*requestId

This API returns a requestId, which can be used by the user to call the cancelRequest API to cancel the request.

### responseRemoteRequest

Response to remote use request

```
const roomEngine = new TUIRoomEngine();// Agree with remote user requestawait roomEngine.responseRemoteRequest({ requestId: '',    // Request ID agree: true,});// Disagree with remote user requestawait roomEngine.responseRemoteRequest({ requestId: '',    // Request ID agree: false,});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| requestId | string | Required | - | Request ID |
| agree | boolean | Required | - | Whether to agree |

**Returns**:*Promise<void>*

### disableSendingMessageByAdmin

Disable/Enable instant message chat

```
await roomEngine.disableSendingMessageByAdmin({  userId: 'user_1234',  isDisable: true,});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| isDisable | boolean | Required | - | Whether it is disabled |

Returns:*Promise<void>*

### changeUserRole

Change the user's role (only the host can call this API).

```
const roomEngine = new TUIRoomEngine();// Transfer the room to user user_1234await roomEngine.changeUserRole({   userId: 'user_1234',   role: TUIRole.kRoomOwner,});// Set user user_1234 as the room administratorawait roomEngine.changeUserRole({  userId: 'user_1234',  userRole: TUIRole.kAdministrator,});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |
| userRole | [TUIRole](https://www.tencentcloud.com/document/product/647/64351#tuirole) | Required | - | User roleRoom owner  TUIRole.kRoomOwnerRoom administrator  TUIRole.kAdministratorRegular member TUIRole.kGeneralUser |

Returns:*Promise<void>*

### kickRemoteUserOutOfRoom

Kick user out of current room

```
const roomEngine = new TUIRoomEngine();await roomEngine.kickRemoteUserOutOfRoom({   userId: 'user_1234',});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| userId | string | Required | - | User ID |

Returns:*Promise<void>*

### getSeatList

Get seats information

```
const roomEngine = new TUIRoomEngine();const seatList = await roomEngine.getSeatList();
```

**Returns**:*Promise<*[TUISeatInfo](https://www.tencentcloud.com/document/product/647/64351#tuiseatinfo)*[]>*seatList

seatList Current room seat list

### takeSeat

Users off the microphone seat can call takeSeat to become speakers. Only speakers can publish local audio and video streams.

- When roomInfo.roomType is TUIRoomType.kConference and roomInfo.seatMode is TUISeatMode.kApplyToTake, ordinary users calling the takeSeat method need to wait for the host/administrator's approval to become speakers.
- When roomInfo.roomType is TUIRoomType.kLivingRoom and roomInfo.seatMode is TUISeatMode.kFreeToTake, ordinary users become speakers successfully after calling the takeSeat method.
- The room owner & administrator becomes a speaker after successfully calling takeSeat.
- Changes to the user microphone-seat list are notified to all users through TUIRoomEvents.onSeatListChanged.

```
const roomEngine = new TUIRoomEngine();// Case 1: room owner/administrator takes microphone seat// Case 2: When roomInfo.roomType is `TUIRoomType.kConference` //  and roomInfo.seatMode `TUISeatMode.kFreeToTake`, regular user takes microphone seatawait roomEngine.takeSeat({ seatIndex: -1, timeout: 0,});    // Case 3: When roomInfo.seatMode is TUISeatMode.kApplyToTake, regular user takes microphone seatconst requestId = await roomEngine.instance?.takeSeat({   seatIndex: -1,   timeout: 0,   requestCallback: ({ requestCallbackType, requestId, userId, code, message }) => {      switch (requestCallbackType) {       case TUIRequestCallbackType.kRequestAccepted:         // Request is accepted         break;       case TUIRequestCallbackType.kRequestRejected:         // Request is rejected         break;       case TUIRequestCallbackType.kRequestCancelled:         // Request is cancelled         break;       case TUIRequestCallbackType.kRequestTimeout:         // Request is timeout         break;       case TUIRequestCallbackType.kRequestError:         // Incorrect request         break;       default:         break;   } },});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| seatIndex | number | Required | - | Microphone seat index. When seat mode is TUISeatMode.kFreeToTake, the value must be -1. |
| timeout | number | Required | - | Timeout period. If timeout is set to 0, there is no timeout limitation. |
| requestCallback | Function | Optional | Empty function | Request callback, used to notify the initiator that the request has been accepted/rejected/canceled/timed out/errored. |

**Returns**:Promise<string> requestId

When roomInfo.seatMode is in TUISeatMode.kApplyToTake mode, ordinary users will receive a requestId when calling this interface, and they can use this requestId to call the cancelRequest interface to cancel their request to speak.

### leaveSeat

Release a seat

```
const roomEngine = new TUIRoomEngine();await roomEngine.leaveSeat();
```

**Returns**:*Promise<void>*

### takeUserOnSeatByAdmin

Invite someone else to speak (only available to room owner and administrators)

```
const roomEngine = new TUIRoomEngine();const requestId = roomEngine.takeUserOnSeatByAdmin({    seatIndex: 0,    userId: 'user_1234',    timeout: 0,    requestCallback: ({ requestCallbackType, requestId, userId, code, message }) => {     switch (requestCallbackType) {       case TUIRequestCallbackType.kRequestAccepted:         // Request is accepted         break;       case TUIRequestCallbackType.kRequestRejected:         // Request is rejected         break;       case TUIRequestCallbackType.kRequestCancelled:         // Request is cancelled         break;       case TUIRequestCallbackType.kRequestTimeout:         // Request is timeout         break;       case TUIRequestCallbackType.kRequestError:         // Incorrect request         break;       default:         break;     }   },});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| seatIndex | number | Required | - | Microphone seat index |
| userId | string | Required | - | User ID |
| timeout | number | Required | - | Timeout period. If timeout is set to 0, there is no timeout limitation. |
| requestCallback | Function | Optional | Empty function | Request callback, used to notify the initiator that the request has been accepted/rejected/canceled/timed out/errored. |

**Returns**:*Promise<string> requestId*

This API returns a requestId, which users can use to call the cancelRequest API to cancel the request.

### kickUserOffSeatByAdmin

Kick someone off the seat (only available to room owner and administrators)

```
const roomEngine = new TUIRoomEngine();const requestId = await roomEngine.kickUserOffSeatByAdmin({   seatIndex: 0,   userId: 'user_1234',});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| seatIndex | number | Required | - | Microphone seat index |
| userId | string | Required | - | User ID |

**Returns**:*Promise<void>*

### lockSeatByAdmin

Lock a seat (only available to room owner and administrators)

```
const roomEngine = new TUIRoomEngine();await roomEngine.lockSeatByAdmin({   seatIndex: 0,   lockParams: {      lockSeat: true,      lockVideo: true,      lockAudio: true,   },});
```

Parameters:

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| seatIndex | number | Required | - | Microphone seat index |
| lockParams | [TUISeatLockParams](https://www.tencentcloud.com/document/product/647/64351#tuiseatlockparams) | Required | - | Lock microphone seat parameter |

Returns:*Promise<void>*

### getSeatApplicationList

Get the list of speaking requests

```
const roomEngine = new TUIRoomEngine();const applicationList = await roomEngine.getSeatApplicationList();
```

Returns:*Promise<*TUIRequest[]*>*

### startScreenSharingElectron

Start screen or window sharing

```
const roomEngine = new TUIRoomEngine();// Case 1: Start sharing screenawait roomEngine.startScreenSharingElectron({     targetId: 'targetId'});// Case 2: Start sharing screen and preview locallyawait roomEngine.startScreenSharingElectron({     targetId: 'targetId',     view: 'screen-preview'});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| targetId | string | Optional | - | Scree or window ID, which can be obtained from getScreenSharingTarget. |
| view | string | Optional | - | The HTML element ID for local preview of screen sharing |

**Returns**:*Promise<void>*

### stopScreenSharingElectron

Stop screen or window sharing on Electronã

```
const roomEngine = new TUIRoomEngine();await roomEngine.stopScreenSharingElectron();
```

**Returns**:*Promise<void>*

### getScreenSharingTarget

Get the screens and windows to be shared

```
const roomEngine = new TUIRoomEngine();const screenList = await roomEngine.getScreenSharingTarget();
```

**Returns**:*Promise<void>*

### selectScreenSharingTarget

Select the screen or window to share

```
const roomEngine = new TUIRoomEngine();await roomEngine.selectScreenSharingTarget({    targetId: 'targetId'});
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| targetId | string | Required | - | Screen or window ID, which can be obtained from getScreenSharingTarget. |

**Returns**:*Promise<void>*

### on

Add event listener

```
const roomEngine = new TUIRoomEngine();roomEngine.on(event, func);
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| event | [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/64350#) | Required | - | TUIRoomEngine events |
| func | Function | Required | - | Event handler function |

**Returns**:***void***

### off

Remove roomEngine event listener

```
const roomEngine = new TUIRoomEngine();roomEngine.off(event, func);
```

**Parameters:**

| Parameter | Type | Validation | Default value | Description |
| --- | --- | --- | --- | --- |
| event | [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/64350#) | Required | - | TUIRoomEngine events |
| func | Function | Required | - | Event handler function |

**Returns**:***void***

### getTRTCCloud

Get the trtcCloud instance. For detail about trtcCloud, please refer to:[TRTCCloud API documents](https://web.sdk.qcloud.com/trtc/electron/doc/en-us/trtc_electron_sdk/index.html)ã

```
const roomEngine = new TUIRoomEngine();const trtcCloud = roomEngine.getTRTCCloud();
```

**Returns**:[TRTCCloud](https://web.sdk.qcloud.com/trtc/electron/doc/en-us/trtc_electron_sdk/index.html)**

### getTIM

Get the tim instance. For detail about tim instance, please refer to:[IM API documents](https://web.sdk.qcloud.com/im/doc/en/SDK.html)ã

```
const roomEngine = new TUIRoomEngine();const tim = roomEngine.getTIM();
```

**Returns:** [TIM](https://web.sdk.qcloud.com/im/doc/en/SDK.html)


---
*Source: [https://trtc.io/document/64342](https://trtc.io/document/64342)*
