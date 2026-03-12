# TUIRoomEngine

## TUIRoomEngine API Introduction

TUIRoomEngine API is a No UI Interface for Conference Component, you can use this API to custom encapsulate according to your business needs.

### createInstance

Create TUIRoomEngine Instance.

```
static TUIRoomEngine createInstance()
```

**return:**TUIRoomEngine Instance

### destroyInstance

Destroy TUIRoomEngine Instance.

```
void destroyInstance()
```

### login

Login interface, you need to initialize user information before entering the room and perform a series of operations.

```
static Future<TUIActionCallback> login(int sdkAppId,                                String userId,                               String userSig)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| sdkAppId | int | Get sdkAppId information from Application Info |
| userId | String | User ID |
| userSig | String | UserSig |

### logout

Logout interface, there will be actively leave the room operation, destroy resources.

```
static Future<TUIActionCallback> logout()
```

### setSelfInfo

Set local user name and avatar.

```
static Future<TUIActionCallback> setSelfInfo(String userName, String avatarURL)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userName | String | User Name |
| avatarUrl | String | User avatar URL address |

### setLoginUserInfo

Set login user information.

```
static Future<TUIActionCallback> setLoginUserInfo(TUILoginUserInfo userInfo)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userInfo | TUILoginUserInfo | User information |

### **getSelfInfo**

Get the basic information of the local user login.

```
static TUILoginUserInfo getSelfInfo()
```

**return:**the basic information of the local user login

### addObserver

Add TUIRoomEngine Event Callback.

```
void addObserver(TUIRoomObserver observer)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| observer | TUIRoomObserver | TUIRoomEngine Event Callback |

### removeObserver

Remove TUIRoomEngine Event Callback.

```
void removeObserver(TUIRoomObserver observer)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| observer | TUIRoomObserver | TUIRoomEngine Event Callback |

### createRoom

The host creates a room, and the user who calls createRoom is the owner of the room. When creating a room, you can set the Room ID, room name, and whether the room allows users to join, enable video and audio, send messages, and other functions.

```
Future<TUIActionCallback> createRoom(TUIRoomInfo roomInfo)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomInfo | [TUIRoomInfo](/document/product/647/57515#RoomInfo) | Room data |

### destroyRoom

Destroy Room Interface, the room owner must initiate the destruction of the room. After the room is destroyed, it is unavailable for entry.

```
Future<TUIActionCallback> destroyRoom()
```

### enterRoom

Entered room.

```
Future<TUIValueCallBack<TUIRoomInfo>> enterRoom(String roomId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | Room ID |

### exitRoom

Exit Room Interface, after the user executes Enter Room, they can leave the room through Leave Room.

```
Future<TUIActionCallback> exitRoom(bool syncWaiting)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| syncWaiting | bool | Whether to synchronize leaving the room |

### connectOtherRoom

Connect to other rooms.

> **Description:**Used for live streaming scenario to apply for cross-room streaming

```
TUIRequest connectOtherRoom(String roomId,                             String userId,                             int timeout,                                TUIRequestCallback? requestCallback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | Room ID |
| userId | String | User ID |
| timeout | int | Time |
| callback | TUIRequestCallback | Connect to other rooms Callback |

**Returnï¼**Request body

### disconnectOtherRoom

Disconnect from other rooms

> **Description:**Used for live streaming scenario to disconnect cross-room streaming

```
Future<TUIActionCallback> disconnectOtherRoom()
```

### fetchRoomInfo

Get Room data.

```
Future<TUIValueCallBack<TUIRoomInfo>> fetchRoomInfo()
```

### updateRoomNameByAdmin

Update Room ID.

```
Future<TUIActionCallback> updateRoomNameByAdmin(String roomName)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomName | String | Room ID |

### updateRoomSpeechModeByAdmin

Set Management mode (only Administrator or Group owner can call).

```
Future<TUIActionCallback> updateRoomSpeechModeByAdmin(TUISpeechMode mode)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| mode | [TUISpeechMode](/document/product/647/57515#SpeechMode) | Management mode |

### setLocalVideoView

Set Local user Video Rendering View control.

```
void setLocalVideoView(TUIVideoStreamType streamType,                        int viewId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| streamType | [TUIVideoStreamType](/document/product/647/57515#VideoStreamType) | Local streams type |
| viewId | int | The int64 type value of the pointer to the view to be rendered, through this viewId, can be converted to the corresponding native platform view, and the video screen will be rendered on this view. |

### openLocalCamera

Open Local Camera, Start Video Capturing.

```
Future<TUIActionCallback> openLocalCamera(bool isFront,                                   TUIVideoQuality quality)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| isFront | bool | Whether to use Front Camera |
| quality | [TUIVideoQuality](/document/product/647/57515#VideoQuality) | Video Quality |

### closeLocalCamera

Close Local Camera.

```
void closeLocalCamera()
```

### updateVideoQuality

Set Local Video Parameter.

```
void updateVideoQuality(TUIVideoQuality quality)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| quality | [TUIVideoQuality](/document/product/647/57515#VideoQuality) | Video Quality |

### updateVideoQualityEx

Set the encoding parameters of video encoderã

```
void updateVideoQualityEx(      TUIVideoStreamType streamType, TUIRoomVideoEncoderParams params);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| streamType | TUIVideoStreamType | Video Stream type |
| params | TUIRoomVideoEncoderParams | Encoding parameters of video encoder |

### setVideoResolutionMode

Set the  resolution mode of video encoder

```
void setVideoResolutionMode(      TUIVideoStreamType streamType, TUIResolutionMode resolutionMode);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| streamType | TUIVideoStreamType | Video Stream type |
| resolutionMode | TUIResolutionMode | Video resolution mode |

### enableGravitySensor

Enable the gravity sensor

```
void enableGravitySensor(bool enable);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| enable | bool | Whether to enable |

### startPushLocalVideo

Start pushing Local Video streams to Remote.

```
void startPushLocalVideo()
```

### stopPushLocalVideo

Stop pushing Local Video streams to Remote.

```
void stopPushLocalVideo()
```

### startScreenSharing

Start screen sharing

```
Future<void> startScreenSharing({String appGroup = ''})
```

### stopScreenSharing

Stop screen sharing

```
Future<void> stopScreenSharing()
```

### openLocalMicrophone

Open Local mic.

```
Future<TUIActionCallback> openLocalMicrophone(TUIAudioQuality quality)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| quality | [TUIAudioQuality](/document/product/647/57515#AudioQuality) | Audio Quality |

### closeLocalMicrophone

Close Local mic.

```
void closeLocalMicrophone()
```

### updateAudioQuality

Update Local Audio Codec Quality setting.

```
void updateAudioQuality(TUIAudioQuality quality)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| quality | [TUIAudioQuality](/document/product/647/57515#AudioQuality) | Audio Quality |

### muteLocalAudio

Mute local audio

```
Future<TUIActionCallback> muteLocalAudio()
```

### unMuteLocalAudio

UnMute local audio

```
Future<TUIActionCallback> unMuteLocalAudio()
```

### setRemoteVideoView

Set Remote user Video Rendering View control.

```
void setRemoteVideoView(String userId,                        TUIVideoStreamType streamType,                         int viewId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| streamType | [TUIVideoStreamType](/document/product/647/57515#VideoStreamType) | User streams type |
| viewId | int | The int64 type value of the pointer to the view to be rendered, through this viewId, can be converted to the corresponding native platform view, and the video screen will be rendered on this view. |

### startPlayRemoteVideo

Start Playback Remote user Video streams.

```
void startPlayRemoteVideo(String userId,                                                        TUIVideoStreamType streamType,                                                               TUIPlayCallback? callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| streamType | [TUIVideoStreamType](/document/product/647/57515#VideoStreamType) | User streams type |
| callback | TUIPlayCallback? | Playback Operation result Callback |

### stopPlayRemoteVideo

Stop Playback Remote user Video streams.

```
void stopPlayRemoteVideo(String userId,                         TUIVideoStreamType streamType)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| streamType | [TUIVideoStreamType](/document/product/647/57515#VideoStreamType) | User streams type |

### muteRemoteAudioStream

Mute Remote user.

```
void muteRemoteAudioStream(String userId, boolean isMute);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| isMute | bool | Whether to mute |

### getUserList

Get current User list in the room, Note that the maximum number of User list fetched by this Interface is 100.

```
Future<TUIValueCallBack<TUIUserListResult>> getUserList(int nextSequence)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| nextSequence | int | Pagination Fetch Flag, fill in 0 for the first Fetch, if the nextSeq in the Callback is not 0, you need to do Pagination, pass in the nextSeq to Fetch again until the nextSeq in the Callback is 0 |

### getUserInfo

Get User Learn more.

```
Future<TUIValueCallBack<TUIUserInfo>> getUserInfo(String userId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | Get Learn more of the user by userId |

### changeUserRole

Change user Role, only Administrator or Group owner can call.

```
Future<TUIActionCallback> changeUserRole(String userId,                                  TUIRole role)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| role | [TUIRole](/document/product/647/57515#Role) | User Role |

### kickRemoteUserOutOfRoom

Kick user out of the room, only Administrator or Group owner can call.

```
Future<TUIActionCallback> kickRemoteUserOutOfRoom(String userId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |

### addCategoryTagForUsers

Add category tags to users (Only Administrator or Group Owner can call)

```
Future<TUIActionCallback> addCategoryTagForUsers(int tag, List<String> userList);
```

**Parametersï¼**

| Parameter | Type | Meaning |
| --- | --- | --- |
| tag | int | Tag type. Number type, greater than or equal to 1000, you can customize |
| userList | List<String> | User list |

### removeCategoryTagForUsers

Remove category tags to users (Only Administrator or Group Owner can call)

```
Future<TUIActionCallback> removeCategoryTagForUsers(int tag, List<String> userList);
```

**Parametersï¼**

| Parameter | Type | Meaning |
| --- | --- | --- |
| tag | int | Tag type. Number type, greater than or equal to 1000, you can customize |
| userList | List<String> | User list |

### getUserListByTag

Get user information in the room based on tags

```
Future<TUIValueCallBack<TUIUserListResult>> getUserListByTag(int tag, int nextSequence);
```

**Parametersï¼**

| Parameter | Type | Meaning |
| --- | --- | --- |
| tag | int | Tag type. Number type, greater than or equal to 1000, you can customize |
| nextSequence | int | Pagination Fetch Flag, fill in 0 for the first Fetch, if the nextSeq in the Callback is not 0, you need to do Pagination, pass in the nextSeq to Fetch again until the nextSeq in the Callback is 0 |

### disableDeviceForAllUserByAdmin

Manage Media device for all users, only Administrator or Group owner can call.

```
Future<TUIActionCallback> disableDeviceForAllUserByAdmin(TUIMediaDevice device,                                                  bool isDisable)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| device | [TUIMediaDevice](/document/product/647/57515#MediaDevice) | Device |
| isDisable | bool | Whether to Disable |

### openRemoteDeviceByAdmin

Request Remote user to open Media device, only Administrator or Group owner can call.

```
TUIRequest openRemoteDeviceByAdmin(String userId,                                    TUIMediaDevice device,                                       int timeout,                                    TUIRequestCallback? requestCallback)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| device | [TUIMediaDevice](/document/product/647/57515#MediaDevice) | Device |
| timeout | int | Timeout in seconds, if set to 0, SDK will not do timeout detection and will not trigger timeout Callback |
| requestCallback | TUIRequestCallback? | Operation result Callback |

### closeRemoteDeviceByAdmin

Close Remote user Media device, only Administrator or Group owner can call.

```
Future<TUIActionCallback> closeRemoteDeviceByAdmin(String userId,                                            TUIMediaDevice device)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| device | [TUIMediaDevice](/document/product/647/57515#MediaDevice) | Device |

### applyToAdminToOpenLocalDevice

Lock all users' Media device management.

```
TUIRequest applyToAdminToOpenLocalDevice(TUIMediaDevice device,                                          int timeout,                                          TUIRequestCallback? requestCallback)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| device | [TUIMediaDevice](/document/product/647/57515#MediaDevice) | Device |
| timeout | int | Timeout Duration, Unit in Seconds. If Set to 0, SDK Will Not Perform Timeout Detection, Nor Will It Trigger Timeout Callback |
| callback | TUIRequestCallback | Operation Result Callback |

### setMaxSeatCount

Set Maximum number of seats, only supported when entering the room and creating the room

When roomType is RoomType.CONFERENCE (Education and Conference scene), maxSeatCount value is not limited;

When roomType is RoomType.LIVE_ROOM (Live broadcast scene), maxSeatCount is limited to 16;

```
Future<TUIActionCallback> setMaxSeatCount(int maxSeatCount)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| maxSeatCount | int | Maximum number of seats |

### lockSeatByAdmin

Lock seat (including position lock, audio status lock, video status lock).

```
Future<TUIActionCallback> lockSeatByAdmin(int seatIndex,                                   TUISeatLockParams lockParams)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Seat number |
| lockParams | [TUISeatLockParams](/document/product/647/57515#SeatLockParams) | Lock microphone parameter |

### getSeatList

Get seat list.

```
Future<TUIValueCallBack<List<TUISeatInfo>>> getSeatList()
```

### takeSeat

Local on microphone.

> **Explanation:**Conference Scene: [applyToSpeak](/document/product/647/57515#SpeechMode) Mode needs to apply to the host or administrator to allow Go Live, other modes do not support Go Live.Live Broadcast Scene: [freeToSpeak](/document/product/647/57515#SpeechMode) Mode can freely Go Live, and speak after Go Live; [applySpeakAfterTakingSeat](/document/product/647/57515#SpeechMode) Mode needs to apply to the host or administrator to allow Go Live; other modes do not support Go Live.

```
TUIRequest takeSeat(int seatIndex,                     int timeout,                     TUIRequestCallback? requestCallback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Seat number |
| timeout | int | Timeout in seconds, if set to 0, SDK will not do timeout detection and will not trigger timeout Callback |
| requestCallback | TUIRequestCallback? | Call interface Callback, used to notify the request Callback status |

**Return**: Request body

### leaveSeat

Local off microphone.

```
Future<TUIActionCallback> leaveSeat()
```

### takeUserOnSeatByAdmin

Host/Administrator Invite User on microphone.

```
TUIRequest takeUserOnSeatByAdmin(int seatIndex,                                  String userId,                                  int timeout,                                     TUIRequestCallback? requestCallback)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Seat number |
| userId | String | User ID |
| timeout | int | Timeout in seconds, if set to 0, SDK will not do timeout detection and will not trigger timeout Callback |
| requestCallback | TUIRequestCallback? | Call interface Callback, used to notify the request Callback status |

**Return**: Request body

### kickUserOffSeatByAdmin

Host/Administrator Take User off microphone.

```
Future<TUIActionCallback> kickUserOffSeatByAdmin(int seatIndex,                                          String userId)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Seat number |
| userId | String | User ID |

### sendTextMessage

Send Text message.

```
Future<TUIActionCallback> sendTextMessage(String message)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| message | String | Text message Content |

### sendCustomMessage

Send Custom message

```
Future<TUIActionCallback> sendCustomMessage(String message)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| message | String | Custom message Content |

### disableSendingMessageByAdmin

Disable Remote user's Text message sending Ability (only Administrator or Group owner can call).

```
Future<TUIActionCallback> disableSendingMessageByAdmin(String userId,                                                bool isDisable)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| isDisable | bool | Whether to Disable |

### disableSendingMessageForAllUser

Disable all users' Text message sending Ability (only Administrator or Group owner can call).

```
Future<TUIActionCallback> disableSendingMessageForAllUser(bool isDisable)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| isDisable | bool | Whether to Disable |

### cancelRequest

Cancel sent Request.

```
Future<TUIActionCallback> cancelRequest(String requestId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| requestId | String | Request ID |

### responseRemoteRequest

Reply to Remote user's Request.

```
Future<TUIActionCallback> responseRemoteRequest(String requestId,                                         bool agree)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| requestId | String | Request ID |
| agree | bool | Whether to agree |

### switchCamera

Switch front/rear camera

```
Future<int?> switchCamera(bool isFrontCamera);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| isFrontCamera | bool | Is front camera |

### setBeautyLevel

Set beauty level

```
void setBeautyLevel(int beautyStyle, int beautyLevel);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| beautyStyle | int | beauty style |
| beautyLevel | int | beauty level |

### setWhitenessLevel

Set whiteness level

```
void setWhitenessLevel(int whitenessLevel);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| whitenessLevel | int | whiteness level |

### callExperimentalAPI

Call experimental api

```
void callExperimentalAPI(String jsonStr);
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| jsonStr | String | Api infomation |


---
*Source: [https://trtc.io/document/57514](https://trtc.io/document/57514)*
