# TUIRoomObserver

**TUIRoomObserver**

## TUIRoomObserver

| FuncList | DESC |
| --- | --- |
| [onError:message:](https://www.tencentcloud.com/document/product/647/54854#e2d2a8b13e80bbe60e2467739f0a0316) | Error event callback. |
| [onKickedOffLine:](https://www.tencentcloud.com/document/product/647/54854#b0238d7b1fa86af2c540ec313dba8e6b) | The current user was kicked offline. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/54854#7b8df3f701ffd641b11047e27094d8db) | The current user signature is expired. |
| [onRoomNameChanged:roomName:](https://www.tencentcloud.com/document/product/647/54854#14f6f031aedb2aef37640bd8d52b512d) | The name of the room has changed. |
| [onAllUserMicrophoneDisableChanged:isDisable:](https://www.tencentcloud.com/document/product/647/54854#3ec4485cdec9612c161c8a3211b2fb28) | The status of disabling to open microphone has changed for all users. |
| [onAllUserCameraDisableChanged:isDisable:](https://www.tencentcloud.com/document/product/647/54854#55a547bc323badf7599db85f13c6b286) | The status of disabling to open camera has changed for all users. |
| [onScreenShareForAllUserDisableChanged:isDisable:](https://www.tencentcloud.com/document/product/647/54854#fe6861c09539278fb9440da696c4d028) | The status of disabling to open screen sharing has changed for all users. |
| [onSendMessageForAllUserDisableChanged:isDisable:](https://www.tencentcloud.com/document/product/647/54854#b64a6a83036eb91c14d381c1feca555b) | The status of disabling to send message has changed for all users. |
| [onRoomDismissed:reason:](https://www.tencentcloud.com/document/product/647/54854#e3741060867444c54121e60eb54f989c) | Room was dismissed. |
| [onKickedOutOfRoom:reason:message:](https://www.tencentcloud.com/document/product/647/54854#bbebfbd4e8b6c95b7852d1493f60bd4e) | The current user has been kicked off from the room. |
| [onRoomSeatModeChanged:seatMode:](https://www.tencentcloud.com/document/product/647/54854#43c39ab0e5611de1f28bfe62e4e0077b) | The room seat mode has changed. |
| [onRoomUserCountChanged:userCount:](https://www.tencentcloud.com/document/product/647/54854#4c5cdb0b2676614586770fe9085576fe) | The count of user in the room has changed. |
| [onRoomMetadataChanged:value:](https://www.tencentcloud.com/document/product/647/54854#f3151fab3ff4a34eed91d740e05c9d5f) | The key-value of room metadata has changed. |
| [onRemoteUserEnterRoom:userInfo:](https://www.tencentcloud.com/document/product/647/54854#64bc4ce1b62e5a15de963ecfb9225e98) | Remote user entered room. |
| [onRemoteUserLeaveRoom:userInfo:](https://www.tencentcloud.com/document/product/647/54854#16b0d80475c0d1f945024d5116074c66) | Remote user left room. |
| [onUserInfoChanged:modifyFlag:](https://www.tencentcloud.com/document/product/647/54854#b5637d7d08d9811983db56c8dd28f051) | User information has changed in the room. |
| [onUserVideoStateChanged:streamType:hasVideo:reason:](https://www.tencentcloud.com/document/product/647/54854#00c4eb2525cf2b404bb784d7731d95a8) | The status of the user has video stream changed. |
| [onUserAudioStateChanged:hasAudio:reason:](https://www.tencentcloud.com/document/product/647/54854#57eafbcdec43b9cacef68034b3087e45) | The status of the user has audio stream changed. |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/54854#65abb01367f2509a0457ba351efb1fe1) | User volume changed. |
| [onSendMessageForUserDisableChanged:userId:isDisable:](https://www.tencentcloud.com/document/product/647/54854#d1f497f96f9523b0d284992b90b22d26) | The status of disabling to send message has changed for user. |
| [onUserNetworkQualityChanged:](https://www.tencentcloud.com/document/product/647/54854#1147aa1bf7e279740ad961bdbbd626bb) | The user network status changed. |
| [onUserScreenCapturePaused:](https://www.tencentcloud.com/document/product/647/54854#73cb544fa8fd92b8a607a9298ce686ae) | Screen sharing paused. |
| [onUserScreenCaptureResumed:](https://www.tencentcloud.com/document/product/647/54854#48f8345803b57e6ec01593732ec756e7) | Screen sharing resumed. |
| [onUserScreenCaptureStopped:](https://www.tencentcloud.com/document/product/647/54854#f6bae569cb7519e87904a735c61605da) | Screen sharing stopped. |
| [onUserVideoSizeChanged:userId:streamType:width:height:](https://www.tencentcloud.com/document/product/647/54854#850d2069ee734aa8537e9fe830f3591d) | The User video size changed. |
| [onSeatListChanged:seated:left:](https://www.tencentcloud.com/document/product/647/54854#31a13be6f374e28422eb363a518b235f) | Seat list changed. |
| [onKickedOffSeat:operateUser:](https://www.tencentcloud.com/document/product/647/54854#bd26ee6b56090e87eb9409c47df09435) | The user was kicked off the seat. |
| [onRequestReceived:](https://www.tencentcloud.com/document/product/647/54854#3697d1d038fd6f3ebe54ea33cd32e3df) | Receive a request message. |
| [onRequestCancelled:operateUser:](https://www.tencentcloud.com/document/product/647/54854#92b334084d0e34a0a3d4507e02acb850) | Received a cancelled request. |
| [onRequestProcessed:operateUser:](https://www.tencentcloud.com/document/product/647/54854#ca708aa561838272c90fa5e3e4eb41e7) | Receive a request to be processed by other administrator/owner. |
| [onReceiveTextMessage:](https://www.tencentcloud.com/document/product/647/54854#ac7c0d898f526f0f902a83c49afffd64) | Text message received |
| [onReceiveCustomMessage:](https://www.tencentcloud.com/document/product/647/54854#a8574308a070707a877d1c699a9c3aba) | Custom message received |
| [onDeviceChanged:type:state:](https://www.tencentcloud.com/document/product/647/54854#8bb5da23b114eee5d7422671ada72503) | Local device added. |

## onError:message:

**onError:message:**

| - (void)onError: | ([TUIError](https://www.tencentcloud.com/document/product/647/64475#d41b099f14c721618a59bac76f0f456b))errorCode |
| --- | --- |
| message: | (NSString *)message |

#### Error event callback.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Callback error events when entering a room or opening a device.

| Param | DESC |
| --- | --- |
| errorCode | Error code. More details, see: [TUIError](https://www.tencentcloud.com/document/product/647/64475#d41b099f14c721618a59bac76f0f456b). |
| message | Error message. |

## onKickedOffLine:

**onKickedOffLine:**

| - (void)onKickedOffLine: | (NSString *)message |
| --- | --- |

#### The current user was kicked offline.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user is kicked offline.

| Param | DESC |
| --- | --- |
| message | Description of being kicked off. |

## onUserSigExpired

**onUserSigExpired**

#### The current user signature is expired.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's signature expires.

## onRoomNameChanged:roomName:

**onRoomNameChanged:roomName:**

| - (void)onRoomNameChanged: | (NSString *)roomId |
| --- | --- |
| roomName: | (NSString *)roomName |

#### The name of the room has changed.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when the room name changes.

| Param | DESC |
| --- | --- |
| roomId | Room ID. |
| roomName | Room name. |

## onAllUserMicrophoneDisableChanged:isDisable:

**onAllUserMicrophoneDisableChanged:isDisable:**

| - (void)onAllUserMicrophoneDisableChanged: | (NSString *)roomId |
| --- | --- |
| isDisable: | (BOOL)isDisable |

#### The status of disabling to open microphone has changed for all users.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to open microphone false: enable user to open microphone. |
| roomId | Room ID. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type..Called when the microphone disable status changes for all users.

## onAllUserCameraDisableChanged:isDisable:

**onAllUserCameraDisableChanged:isDisable:**

| - (void)onAllUserCameraDisableChanged: | (NSString *)roomId |
| --- | --- |
| isDisable: | (BOOL)isDisable |

#### The status of disabling to open camera has changed for all users.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to open camera false: enable user to open camera. |
| roomId | Room ID. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type..Called when the camera disable status changes for all users.

## onScreenShareForAllUserDisableChanged:isDisable:

**onScreenShareForAllUserDisableChanged:isDisable:**

| - (void)onScreenShareForAllUserDisableChanged: | (NSString *)roomId |
| --- | --- |
| isDisable: | (BOOL)isDisable |

#### The status of disabling to open screen sharing has changed for all users.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to open screen sharing false: enable user to open screen sharing. |
| roomId | Room ID. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type..Called when the screen sharing permissions change for all users.

## onSendMessageForAllUserDisableChanged:isDisable:

**onSendMessageForAllUserDisableChanged:isDisable:**

| - (void)onSendMessageForAllUserDisableChanged: | (NSString *)roomId |
| --- | --- |
| isDisable: | (BOOL)isDisable |

#### The status of disabling to send message has changed for all users.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to send message false: enable user to send message. |
| roomId | Room ID. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type..Called when the message sending permissions change for all users.

## onRoomDismissed:reason:

**onRoomDismissed:reason:**

| - (void)onRoomDismissed: | (NSString *)roomId |
| --- | --- |
| reason: | ([TUIRoomDismissedReason](https://www.tencentcloud.com/document/product/647/64477#9e97a16d20d331906cc0990099121355))reason |

#### Room was dismissed.

| Param | DESC |
| --- | --- |
| reason | The reason why the room was dismissed. More details, see: [TUIRoomDismissedReason](https://www.tencentcloud.com/document/product/647/64477#9e97a16d20d331906cc0990099121355). |
| roomId | Room ID. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type..Called when the room is dismissed.

## onKickedOutOfRoom:reason:message:

**onKickedOutOfRoom:reason:message:**

| - (void)onKickedOutOfRoom: | (NSString *)roomId |
| --- | --- |
| reason: | ([TUIKickedOutOfRoomReason](https://www.tencentcloud.com/document/product/647/64477#c6b3c5e07b71d50181b15edf97f384c8))reason |
| message: | (NSString *)message |

#### The current user has been kicked off from the room.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user is kicked out of the room.

| Param | DESC |
| --- | --- |
| message | Description of being kicked off. |
| reason | Reason for being kicked off. |
| roomId | Room ID. |

## onRoomSeatModeChanged:seatMode:

**onRoomSeatModeChanged:seatMode:**

| - (void)onRoomSeatModeChanged: | (NSString *)roomId |
| --- | --- |
| seatMode: | ([TUISeatMode](https://www.tencentcloud.com/document/product/647/64477#6e6fdc219cc838c9e3c5d622ab32c8f1))seatMode |

#### The room seat mode has changed.

| Param | DESC |
| --- | --- |
| roomId | : Room ID. |
| seatMode | : Seat mode. More details, see [TUISeatMode](https://www.tencentcloud.com/document/product/647/64477#6e6fdc219cc838c9e3c5d622ab32c8f1).#### [REMARK]The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.Called when the seat mode of the room changes. |

## onRoomUserCountChanged:userCount:

**onRoomUserCountChanged:userCount:**

| - (void)onRoomUserCountChanged: | (NSString *)roomId |
| --- | --- |
| userCount: | (NSInteger)userCount |

#### The count of user in the room has changed.

| Param | DESC |
| --- | --- |
| roomId | Room ID. |
| userCount | Count of user.#### [REMARK]The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.Called when the user count of the room changes. |

## onRoomMetadataChanged:value:

**onRoomMetadataChanged:value:**

| - (void)onRoomMetadataChanged: | (NSString *)key |
| --- | --- |
| value: | (NSString *)value |

#### The key-value of room metadata has changed.

| Param | DESC |
| --- | --- |
| key | The key of room metadata. |
| value | The value of room metadata.#### [REMARK]The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.Called when the custom information of the room changes. |

## onRemoteUserEnterRoom:userInfo:

**onRemoteUserEnterRoom:userInfo:**

| - (void)onRemoteUserEnterRoom: | (NSString *)roomId |
| --- | --- |
| userInfo: | ([TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619) *)userInfo |

#### Remote user entered room.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a remote user enters the room.

| Param | DESC |
| --- | --- |
| roomId | Room ID. |
| userInfo | User information. More details, see [TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619). |

## onRemoteUserLeaveRoom:userInfo:

**onRemoteUserLeaveRoom:userInfo:**

| - (void)onRemoteUserLeaveRoom: | (NSString *)roomId |
| --- | --- |
| userInfo: | ([TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619) *)userInfo |

#### Remote user left room.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a remote user leaves the room.

| Param | DESC |
| --- | --- |
| roomId | Room ID. |
| userInfo | User information. More details, see [TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619). |

## onUserInfoChanged:modifyFlag:

**onUserInfoChanged:modifyFlag:**

| - (void)onUserInfoChanged: | ([TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619) *)userInfo |
| --- | --- |
| modifyFlag: | (TUIUserInfoModifyFlag)modifyFlag |

#### User information has changed in the room.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's information changes.

| Param | DESC |
| --- | --- |
| modifyFlag | Modifiable parameter. More details, see TUIUserInfoModifyFlag. |
| userInfo | User information. More details, see [TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619). |

## onUserVideoStateChanged:streamType:hasVideo:reason:

**onUserVideoStateChanged:streamType:hasVideo:reason:**

| - (void)onUserVideoStateChanged: | (NSString *)userId |
| --- | --- |
| streamType: | ([TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15))streamType |
| hasVideo: | (BOOL)hasVideo |
| reason: | ([TUIChangeReason](https://www.tencentcloud.com/document/product/647/64477#e076e8a54a50ddfea400e7eeeb5b3132))reason |

#### The status of the user has video stream changed.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's video state changes.

| Param | DESC |
| --- | --- |
| hasVideo | The current user whether has video stream. |
| reason | The reason why the video stream changed: [TUIChangeReasonBySelf](https://www.tencentcloud.com/document/product/647/64477#e076e8a54a50ddfea400e7eeeb5b3132): Changed by self [TUIChangeReasonByAdmin](https://www.tencentcloud.com/document/product/647/64477#e076e8a54a50ddfea400e7eeeb5b3132): Changed by administrator. |
| streamType | Video stream type. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15). |
| userId | User ID. |

## onUserAudioStateChanged:hasAudio:reason:

**onUserAudioStateChanged:hasAudio:reason:**

| - (void)onUserAudioStateChanged: | (NSString *)userId |
| --- | --- |
| hasAudio: | (BOOL)hasAudio |
| reason: | ([TUIChangeReason](https://www.tencentcloud.com/document/product/647/64477#e076e8a54a50ddfea400e7eeeb5b3132))reason |

#### The status of the user has audio stream changed.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's audio state changes.

| Param | DESC |
| --- | --- |
| hasAudio | The current user whether has audio stream. |
| reason | The reason why the video stream changed: [TUIChangeReasonBySelf](https://www.tencentcloud.com/document/product/647/64477#e076e8a54a50ddfea400e7eeeb5b3132): Changed by self [TUIChangeReasonByAdmin](https://www.tencentcloud.com/document/product/647/64477#e076e8a54a50ddfea400e7eeeb5b3132): Changed by administrator. |
| userId | User ID. |

## onUserVoiceVolumeChanged

**onUserVoiceVolumeChanged**

#### User volume changed.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's voice volume changes.

| Param | DESC |
| --- | --- |
| volumeMap | : User volume dictionary key: userId, value: the volume of all speaking users, with a value range of 0 - 100. |

## onSendMessageForUserDisableChanged:userId:isDisable:

**onSendMessageForUserDisableChanged:userId:isDisable:**

| - (void)onSendMessageForUserDisableChanged: | (NSString *)roomId |
| --- | --- |
| userId: | (NSString *)userId |
| isDisable: | (BOOL)muted |

#### The status of disabling to send message has changed for user.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's message sending permissions change.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to send message false: enable user to send message. |
| userId | User ID. |

## onUserNetworkQualityChanged:

**onUserNetworkQualityChanged:**

| - (void)onUserNetworkQualityChanged: | (NSArray<[TUINetworkInfo](https://www.tencentcloud.com/document/product/647/64475#4ef6f8348df6b2fa6ebd5318a3e88c67) *> *)networkList |
| --- | --- |

#### The user network status changed.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's network quality changes.

| Param | DESC |
| --- | --- |
| networkList | User network status list. More details, see [TUINetworkInfo](https://www.tencentcloud.com/document/product/647/64475#4ef6f8348df6b2fa6ebd5318a3e88c67). |

## onUserScreenCapturePaused:

**onUserScreenCapturePaused:**

| - (void)onUserScreenCapturePaused: | (NSInteger)reason |
| --- | --- |

#### Screen sharing paused.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's screen capture pauses.

| Param | DESC |
| --- | --- |
| reason | pause reason, 0: User manually paused; 1: The screen sharing window became invisible (Mac) or due to screen sharing parameter settings (Windows). 2: The screen sharing window was minimized (Windows only). 3: The screen sharing window was hidden (Windows only). 4: The system stopped screen recording (iOS only). |

## onUserScreenCaptureResumed:

**onUserScreenCaptureResumed:**

| - (void)onUserScreenCaptureResumed: | (NSInteger)reason |
| --- | --- |

#### Screen sharing resumed.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's screen capture resumes.

| Param | DESC |
| --- | --- |
| reason | resume reasonï¼0: User manually resumed. 1: The screen sharing window became visible again (Mac) or screen sharing parameters were set (Windows). 2: The screen sharing window was restored from minimization (Windows only). 3: The screen sharing window was restored from being hidden (Windows only). 4: The system resumed screen recording (iOS only). |

## onUserScreenCaptureStopped:

**onUserScreenCaptureStopped:**

| - (void)onUserScreenCaptureStopped: | (NSInteger)reason |
| --- | --- |

#### Screen sharing stopped.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user's screen capture stops.

| Param | DESC |
| --- | --- |
| reason | Stop reason, 0: user actively stops; 1: the screen or the window is closed ; 2: the status of the screen or the window has changed (such as device disconnect). |

## onUserVideoSizeChanged:userId:streamType:width:height:

**onUserVideoSizeChanged:userId:streamType:width:height:**

| - (void)onUserVideoSizeChanged: | (NSString *)roomId |
| --- | --- |
| userId: | (NSString *)userId |
| streamType: | ([TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15))streamType |
| width: | (int)width |
| height: | (int)height |

#### The User video size changed.

The function supports the ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)) room types.

Called when a user's video size changes.

| Param | DESC |
| --- | --- |
| height | Video height. |
| roomId | Room ID. |
| streamType | Video stream type. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15). |
| userId | User ID or mixed stream ID. When the local user is an audience and successfully connected to the host, this parameter represents the host's user ID; otherwise, it represents the mixed stream ID. |
| width | Video width. |

## onSeatListChanged:seated:left:

**onSeatListChanged:seated:left:**

| - (void)onSeatListChanged: | (NSArray<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/64477#6c78abecee8a3d1925fbecbb0949611c) *> *)seatList |
| --- | --- |
| seated: | (NSArray<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/64477#6c78abecee8a3d1925fbecbb0949611c) *> *)seatedList |
| left: | (NSArray<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/64477#6c78abecee8a3d1925fbecbb0949611c) *> *)leftList |

#### Seat list changed.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when the seat list changes.

| Param | DESC |
| --- | --- |
| leftList | List of newly leave-seat users. |
| seatList | The latest user list on seat, including new users. |
| seatedList | List of newly take-seat users. |

## onKickedOffSeat:operateUser:

**onKickedOffSeat:operateUser:**

| - (void)onKickedOffSeat: | (NSInteger)seatIndex |
| --- | --- |
| operateUser: | ([TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619) *)operateUser |

#### The user was kicked off the seat.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a user is kicked off a seat.

| Param | DESC |
| --- | --- |
| operateUser | User information of the owner/administrator who kicked the user. |
| seatIndex | Seat index. |

## onRequestReceived:

**onRequestReceived:**

| - (void)onRequestReceived: | ([TUIRequest](https://www.tencentcloud.com/document/product/647/64477#befd0ee2a4b89417962680c9e81581c8) *)request |
| --- | --- |

#### Receive a request message.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a request is received.

| Param | DESC |
| --- | --- |
| request | Request content. More details, see [TUIRequest](https://www.tencentcloud.com/document/product/647/64477#befd0ee2a4b89417962680c9e81581c8). |

## onRequestCancelled:operateUser:

**onRequestCancelled:operateUser:**

| - (void)onRequestCancelled: | ([TUIRequest](https://www.tencentcloud.com/document/product/647/64477#befd0ee2a4b89417962680c9e81581c8) *)request |
| --- | --- |
| operateUser: | ([TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619) *)operateUser |

#### Received a cancelled request.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a request is cancelled.

| Param | DESC |
| --- | --- |
| operateUser | Operator information. |
| request | Request content. More details, see [TUIRequest](https://www.tencentcloud.com/document/product/647/64477#befd0ee2a4b89417962680c9e81581c8). |

## onRequestProcessed:operateUser:

**onRequestProcessed:operateUser:**

| - (void)onRequestProcessed: | ([TUIRequest](https://www.tencentcloud.com/document/product/647/64477#befd0ee2a4b89417962680c9e81581c8) *)request |
| --- | --- |
| operateUser: | ([TUIUserInfo](https://www.tencentcloud.com/document/product/647/64477#f619c1d19040e033e9fa88e0946cc619) *)operateUser |

#### Receive a request to be processed by other administrator/owner.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a request is processed.

| Param | DESC |
| --- | --- |
| operateUser | Operator information. |
| request | Request content. More details, see [TUIRequest](https://www.tencentcloud.com/document/product/647/64477#befd0ee2a4b89417962680c9e81581c8). |

## onReceiveTextMessage:

**onReceiveTextMessage:**

| - (void)onReceiveTextMessage: | ([TUIRoomTextMessage](https://www.tencentcloud.com/document/product/647/64477#7e0dfeb925fa7e89ac4d1073c6e2a046) *)textMessage |
| --- | --- |

#### Text message received

| Param | DESC |
| --- | --- |
| textMessage | The message object, see the $TUIRoomTextMessage$ object for details. |

## onReceiveCustomMessage:

**onReceiveCustomMessage:**

| - (void)onReceiveCustomMessage: | ([TUIRoomCustomMessage](https://www.tencentcloud.com/document/product/647/64477#2dbc71d1c436a27bf13d15a5d22e01d1) *)customMessage |
| --- | --- |

#### Custom message received

| Param | DESC |
| --- | --- |
| customMessage | The message object, see the $TUIRoomCustomMessage$ object for details. |

## onDeviceChanged:type:state:

**onDeviceChanged:type:state:**

| - (void)onDeviceChanged: | (NSString *)deviceId |
| --- | --- |
| type: | (TUIMediaDeviceType)type |
| state: | (TUIMediaDeviceState)state |

#### Local device added.

The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

Called when a device changes.

@deprecated It is not recommended to use it since version v2.0. It is recommended to use onDeviceChanged in {$TUIRoomDeviceManager$} instead.

| Param | DESC |
| --- | --- |
| deviceId | Device ID. |
| state | 0: the device has been added; 1: the device has been removed; 2: the device has been enabled. |
| type | Device type. More details, see TUIMediaDeviceType. |

> **Note**When a local device (including camera, microphone, and speaker) is added, the SDK will throw this event callback.


---
*Source: [https://trtc.io/document/54854](https://trtc.io/document/54854)*
