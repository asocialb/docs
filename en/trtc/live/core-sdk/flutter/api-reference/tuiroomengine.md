# TUIRoomEngine

## TUIRoomEngine APIs

TUIRoomEngine API is a no UI interface for multi-person audio and video rooms, you can use these APIs to perform custom encapsulation based on your business needs.

### sharedInstance

Create TUIRoomEngine Instance.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
static TUIRoomEngine sharedInstance()
```

**return:** TUIRoomEngine instance.

### destroySharedInstance

Destroy TUIRoomEngine instance.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void destroySharedInstance()
```

### login

Log in to roomEngine interface, you need to initialize user information first, then you can enter the room and perform a series of operations.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
static Future<TUIActionCallback> login(int sdkAppId,                                String userId,                               String userSig)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| sdkAppId | int | Get sdkAppId information from Application Information |
| userId | String | User ID |
| userSig | String | userSig signature. For the calculation method of userSig, please refer to[UserSig related](https://www.tencentcloud.com/document/product/647/35166#) |

### logout

Logout Interface, which includes proactively leaving the room and destroying resources.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
static Future<TUIActionCallback> logout()
```

### setSelfInfo

Set Local Username and Avatar.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
static Future<TUIActionCallback> setSelfInfo(String userName, String avatarURL)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userName | String | Username |
| avatarUrl | String | User's profile photo |

### setLoginUserInfo

Set Login User Information.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
static Future<TUIActionCallback> setLoginUserInfo(TUILoginUserInfo userInfo)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userInfo | TUILoginUserInfo | User Information |

### **getSelfInfo**

Obtain Basic Information of Local User Login.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
static TUILoginUserInfo getSelfInfo()
```

**return:** User log in to information.

### addObserver

Add TUIRoomEngine event callback.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void addObserver(TUIRoomObserver observer)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| observer | TUIRoomObserver | TUIRoomEngine event callback |

### removeObserver

Remove TUIRoomEngine event callback.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void removeObserver(TUIRoomObserver observer)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| observer | TUIRoomObserver | TUIRoomEngine event callback |

### createRoom

The host creates a room, and the user who calls createRoom is the owner of the room. When creating a room, you can set the room ID, room name, and whether the room allows users to initiate audio and video, send messages, and other features.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> createRoom(TUIRoomInfo roomInfo)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| roomInfo | [TUIRoomInfo](https://www.tencentcloud.com/document/product/647/67259#RoomInfo) | Room Basic Information |

### destroyRoom

Destroy room interface. The room must be destroyed by the owner. After destroying the room, it cannot be entered.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> destroyRoom()
```

### enterRoom

Enter room interface.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIValueCallBack<TUIRoomInfo>> enterRoom(String roomId,{TUIRoomType roomType = TUIRoomType.conference,TUIEnterRoomOptions? options})
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| roomId | String | Room number, string type |
| roomType | TUIRoomType | Room type |
| options | TUIEnterRoomOptions | Optional parameters for entering the room |

### exitRoom

Leave room interface, users can leave the room via exitRoom after executing enterRoom.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> exitRoom(bool syncWaiting)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| syncWaiting | bool | Whether to exit the room synchronously |

### connectOtherRoom

Connect to Other Rooms.

> **Note:**Used to apply for a cross-room mic connection in live streaming scenarios.

```
TUIRequest connectOtherRoom(String roomId,                             String userId,                             int timeout,                                TUIRequestCallback? requestCallback)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| roomId | String | Room ID |
| userId | String | User ID |
| timeout | int | Time |
| callback | TUIRequestCallback | Callback for connecting to other rooms request |

**Return:**Request Body

### disconnectOtherRoom

Disconnect from Other Rooms.

> **Note:**Used to disconnect cross-room mic connections in live streaming scenarios.

```
Future<TUIActionCallback> disconnectOtherRoom()
```

### fetchRoomInfo

Obtain room information.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIValueCallBack<TUIRoomInfo>> fetchRoomInfo()
```

### updateRoomNameByAdmin

Update Room Name.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> updateRoomNameByAdmin(String roomName)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| roomName | String | Room Name |

### updateRoomSeatModeByAdmin

Set room microphone mode (only administrators or group owners can call this).

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> updateRoomSeatModeByAdmin(TUISeatMode mode)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| mode | [TUISeatMode](https://www.tencentcloud.com/document/product/647/67259#TUISeatMode) | Room mode |

### setLocalVideoView

Set the view controls for local user video rendering.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void setLocalVideoView(int viewId)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| viewId | int | int64 type value of the pending view pointer, this viewId can be converted to the corresponding native platform's view, and the video footage will be rendered on this view |

### openLocalCamera

Turn on the local camera and start video stream acquisition.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> openLocalCamera(bool isFront,                                   TUIVideoQuality quality)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| isFront | bool | Whether to use the front-facing camera |
| quality | [TUIVideoQuality](https://www.tencentcloud.com/document/product/647/67259#74d0aadf-0c54-4a05-9e30-f40b427f1402) | Video Quality |

### closeLocalCamera

Turns the local camera off.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void closeLocalCamera()
```

### updateVideoQuality

Set local video parameters.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void updateVideoQuality(TUIVideoQuality quality)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| quality | [TUIVideoQuality](https://www.tencentcloud.com/document/product/647/67259#74d0aadf-0c54-4a05-9e30-f40b427f1402) | Video Quality |

### updateVideoQualityEx

Set local video encoder parameters.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void updateVideoQualityEx(      TUIVideoStreamType streamType, TUIRoomVideoEncoderParams params);
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| streamType | TUIVideoStreamType | Video stream type |
| params | TUIRoomVideoEncoderParams | Video Encoder Parameters |

### setVideoResolutionMode

Set video encoder resolution mode (landscape resolution or portrait resolution).

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void setVideoResolutionMode(      TUIVideoStreamType streamType, TUIResolutionMode resolutionMode);
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| streamType | TUIVideoStreamType | Video stream type |
| resolutionMode | TUIResolutionMode | Resolution Mode |

### enableGravitySensor

Enable gravity sensing mode.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void enableGravitySensor(bool enable);
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| enable | bool | Whether Enabled |

### startPushLocalVideo

Start pushing the local video stream to the remote.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void startPushLocalVideo()
```

### stopPushLocalVideo

Stop pushing local video streams to the remote.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void stopPushLocalVideo()
```

### startScreenSharing

Starting Screen Sharing

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<void> startScreenSharing({String appGroup = ''})
```

### stopScreenSharing

End Screen Sharing

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<void> stopScreenSharing()
```

### openLocalMicrophone

Enable the local mic.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> openLocalMicrophone(TUIAudioQuality quality)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| quality | [TUIAudioQuality](https://www.tencentcloud.com/document/product/647/67259#c079e8f9-62be-4ea2-b740-20658dcec529) | Audio Quality |

### closeLocalMicrophone

Disable the local mic.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void closeLocalMicrophone()
```

### updateAudioQuality

Update local audio encoding quality settings.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void updateAudioQuality(TUIAudioQuality quality)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| quality | [TUIAudioQuality](https://www.tencentcloud.com/document/product/647/67259#c079e8f9-62be-4ea2-b740-20658dcec529) | Audio Quality |

### muteLocalAudio

Stop pushing local audio streams to the remote.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> muteLocalAudio()
```

### unMuteLocalAudio

Start pushing the local audio stream to the remote.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> unMuteLocalAudio()
```

### setRemoteVideoView

Set the view controls for remote user video rendering.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void setRemoteVideoView(String userId,                        TUIVideoStreamType streamType,                         int viewId)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/67259#VideoStreamType) | User stream type |
| viewId | int | int64 type value of the pending view pointer, this viewId can be converted to the corresponding native platform's view, and the video footage will be rendered on this view |

### startPlayRemoteVideo

Start playing the remote user's video stream.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void startPlayRemoteVideo(String userId,                                                        TUIVideoStreamType streamType,                                                               TUIPlayCallback? callback)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/67259#VideoStreamType) | User stream type |
| callback | TUIPlayCallback? | Playback result callback |

### stopPlayRemoteVideo

Stop playing the remote user's video stream.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void stopPlayRemoteVideo(String userId,                         TUIVideoStreamType streamType)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/67259#VideoStreamType) | User stream type |

### muteRemoteAudioStream

Mute remote user.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void muteRemoteAudioStream(String userId, boolean isMute);
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| isMute | bool | Whether to mute |

### getUserList

Get the current room user list. Note that the maximum number of users that can be pulled at one time is 100.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIValueCallBack<TUIUserListResult>> getUserList(int nextSequence)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| nextSequence | int | Pagination pull flag. Fill in 0 for the first pull. If nextSeq is not zero in the callback, pagination is needed. Pass in nextSeq to pull again until nextSeq is zero in the callback |

### getUserInfo

Get the detailed information of users.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIValueCallBack<TUIUserInfo>> getUserInfo(String userId)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | Get detailed information of this user based on userId |

### changeUserRole

Change the user's role. Only administrators or group owners can call this.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> changeUserRole(String userId,                                  TUIRole role)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| role | [TUIRole](https://www.tencentcloud.com/document/product/647/67259#Role) | User Role |

### changeUserNameCard

Change the nickname of a user in the room.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> changeUserNameCard(String userId, String nameCard);
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| nameCard | String | User Nickname |

### kickRemoteUserOutOfRoom

Remove a user from the room. Only administrators or group owners can call this.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> kickRemoteUserOutOfRoom(String userId)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |

### addCategoryTagForUsers

Add tags for users. Only the room owner can call this.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> addCategoryTagForUsers(int tag, List<String> userList);
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| tag | int | Mark type. Numeric type, greater than or equal to 1000. You can define it yourself. |
| userList | List<String> | User list |

### removeCategoryTagForUsers

Remove tags for users. Only the room owner can call this.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> removeCategoryTagForUsers(int tag, List<String> userList);
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| tag | int | Type. Numeric type, greater than or equal to 1000. You can define it yourself. |
| userList | List<String> | User list |

### getUserListByTag

Get user information in the room based on labels

Remove tags for users. Only the room owner can call this.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIValueCallBack<TUIUserListResult>> getUserListByTag(int tag, int nextSequence);
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| tag | int | Type. Numeric type, greater than or equal to 1000. You can define it yourself. |
| nextSequence | int | Pagination pull flag. Fill in 0 for the first pull. If nextSequence is not zero in the callback, pagination is needed. Pass it in to pull again until it is zero |

### setCustomInfoForUser

Set customized information for members in the room

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> setCustomInfoForUser(String userId,HashMap<String, String> customInfo);
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | userId |
| customInfo | HashMap<String, String> | Customized Information |

### disableDeviceForAllUserByAdmin

All Users Media Device Management, only administrators or group owners can invoke.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> disableDeviceForAllUserByAdmin(TUIMediaDevice device,                                                  bool isDisable)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| device | [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/67259#45f8cc27-8bbe-4ed5-bb40-511a08e27477) | Device |
| isDisable | bool | Whether to disable |

### openRemoteDeviceByAdmin

Request Remote User to Open Media Device, only administrators or group owners can invoke.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
TUIRequest openRemoteDeviceByAdmin(String userId,                                    TUIMediaDevice device,                                       int timeout,                                    TUIRequestCallback? requestCallback)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| device | [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/67259#45f8cc27-8bbe-4ed5-bb40-511a08e27477) | Device |
| timeout | int | Timeout period, unit: seconds. If set to 0, the SDK will not perform timeout detection and will not trigger a timeout callback |
| requestCallback | TUIRequestCallback? | Operation result callback |

### closeRemoteDeviceByAdmin

Close Remote User Media Device, only administrators or group owners can invoke.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> closeRemoteDeviceByAdmin(String userId,                                            TUIMediaDevice device)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| device | [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/67259#45f8cc27-8bbe-4ed5-bb40-511a08e27477) | Device |

### applyToAdminToOpenLocalDevice

All Users Media Device Management lock.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
TUIRequest applyToAdminToOpenLocalDevice(TUIMediaDevice device,                                          int timeout,                                          TUIRequestCallback? requestCallback)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| device | [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/67259#45f8cc27-8bbe-4ed5-bb40-511a08e27477) | Device |
| timeout | int | Timeout period, unit: seconds. If set to 0, the SDK will not perform timeout detection and will not trigger a timeout callback |
| callback | TUIRequestCallback? | Operation result callback |

### setMaxSeatCount

Set the maximum number of microphone slots. It can only be set before entering the room or when creating the room.

```
Future<TUIActionCallback> setMaxSeatCount(int maxSeatCount)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| maxSeatCount | int | Maximum Number of Microphones |

### getSeatApplicationList

Host/Administrator retrieves the list of requests from users applying to speak in the room.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIValueCallBack<List<TUIRequest>>> getSeatApplicationList();
```

### lockSeatByAdmin

Lock microphone position (includes location lock, audio status lock, video status lock).

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> lockSeatByAdmin(int seatIndex,                                   TUISeatLockParams lockParams)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Microphone slot number |
| lockParams | [TUISeatLockParams](https://www.tencentcloud.com/document/product/647/67259#080212f8-d6ce-4430-b745-2fdd5ef8c330) | Mute Microphone parameter |

### getSeatList

Get the microphone position list.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIValueCallBack<List<TUISeatInfo>>> getSeatList()
```

### takeSeat

Local Microphone On.

> **Note:**Meeting scenario:[applyToSpeak](https://www.tencentcloud.com/document/product/647/67259#TUISeatMode) mode requires an application to the host or administrator before taking the mic. Other modes do not support taking the mic.Live streaming scenario:[freeToSpeak](https://www.tencentcloud.com/document/product/647/67259#TUISeatMode) mode allows free mic access. After taking the mic, open the microphone to speak; [applySpeakAfterTakingSeat](https://www.tencentcloud.com/document/product/647/67259#TUISeatMode) mode requires an application to the host or administrator before taking the mic. Other modes do not support taking the mic.This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
TUIRequest takeSeat(int seatIndex,                     int timeout,                     TUIRequestCallback? requestCallback)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Microphone slot number |
| timeout | int | Timeout period, unit: seconds. If set to 0, the SDK will not perform timeout detection and will not trigger a timeout callback |
| requestCallback | TUIRequestCallback? | Invoke interface callback to notify the request status |

**Return**: Request Body

### leaveSeat

Local Microphone Off.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> leaveSeat()
```

### moveToSeat

Move Microphone.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> moveToSeat(int targetSeatIndex);
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Microphone slot number |

### takeUserOnSeatByAdmin

Host/Administrator invites users to go on stage.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
TUIRequest takeUserOnSeatByAdmin(int seatIndex,                                  String userId,                                  int timeout,                                     TUIRequestCallback? requestCallback)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Microphone slot number |
| userId | String | User ID |
| timeout | int | Timeout period, unit: seconds. If set to 0, the SDK will not perform timeout detection and will not trigger a timeout callback |
| requestCallback | TUIRequestCallback? | Invoke interface callback to notify the request status |

**Return**: Request Body

### kickUserOffSeatByAdmin

Host/Administrator removes users from the mic.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> kickUserOffSeatByAdmin(int seatIndex,                                          String userId)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | Microphone slot number |
| userId | String | User ID |

### disableSendingMessageByAdmin

Disable the remote user's ability to send text messages (only administrators or group owners can call this).

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> disableSendingMessageByAdmin(String userId,                                                bool isDisable)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| isDisable | bool | Whether to disable |

### disableSendingMessageForAllUser

Disable all users' ability to send text messages (only administrators or group owners can call this).

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> disableSendingMessageForAllUser(bool isDisable)
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| isDisable | bool | Whether to disable |

### cancelRequest

Cancel the already sent request.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> cancelRequest(String requestId)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| requestId | String | Request ID |

### responseRemoteRequest

Respond to the remote user's request.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
Future<TUIActionCallback> responseRemoteRequest(String requestId,                                         bool agree)
```

**Parameter:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| requestId | String | Request ID |
| agree | bool | Do you agree? |

### callExperimentalAPI

Calls an experimental API.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void callExperimentalAPI(String jsonStr);
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| jsonStr | String | Interface Information |

### setBeautyLevel

Set beauty filter effect level

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void setBeautyLevel(int beautyStyle, int beautyLevel);
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| beautyStyle | int | Beauty filter style |
| beautyLevel | int | Beauty filter effect level |

### setWhitenessLevel

Set brightening filter effect level

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
void setWhitenessLevel(int whitenessLevel);
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| whitenessLevel | int | Brightening filter effect level |

### getExtension

Get plugins

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
dynamic getExtension(TUIExtensionType extensionType);
```

| Parameters | Type | Meaning |
| --- | --- | --- |
| extensionType | TUIExtensionType | Plugin Type |

### getMediaDeviceManager

Get device management class

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
TUIRoomDeviceManager getMediaDeviceManager();
```


---
*Source: [https://trtc.io/document/67263](https://trtc.io/document/67263)*
