# TUIRoomObserver

**TUIRoomObserver**

## TUIRoomObserver

| FuncList | DESC |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/54863#2db3f881372c598e3e647f3b17915369) | Error event callback. |
| [onKickedOffLine](https://www.tencentcloud.com/document/product/647/54863#5dfa1251a6787bde3f2f1d1a4b1bab88) | The current user was kicked offline. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/54863#4309a1386c7b4635777bb8520b0c44fc) | The current user signature is expired. |
| [onRoomNameChanged](https://www.tencentcloud.com/document/product/647/54863#97fc563cec36fcde1bb0bc1b212b5c4e) | The name of the room has changed. |
| [onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/54863#15f469022d454f95f53372a83157fbbc) | The status of disabling to open microphone has changed for all users. |
| [onAllUserCameraDisableChanged](https://www.tencentcloud.com/document/product/647/54863#6bc81e3152578d22f10f45780fa7cb77) | The status of disabling to open camera has changed for all users. |
| [onScreenShareForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54863#d6f2fb6b5936b7313bf9e36aa75aef9d) | The status of disabling to open screen sharing has changed for all users. |
| [onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54863#8d2f050ec369f72915aa26991c04399b) | The status of disabling to send message has changed for all users. |
| [onRoomDismissed](https://www.tencentcloud.com/document/product/647/54863#087189eff55afc545eaa7fc58eaa2622) | Room was dismissed. |
| [onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/54863#216fe07cfda9d5b3736e368c0eef69c2) | The current user has been kicked off from the room. |
| [onRoomSeatModeChanged](https://www.tencentcloud.com/document/product/647/54863#dd614e13a79128f06065469914b9a797) | The room seat mode has changed. |
| [onRoomUserCountChanged](https://www.tencentcloud.com/document/product/647/54863#b1ce0f40db4b25f53d14ca03d2902846) | The count of user in the room has changed. |
| [onRoomMetadataChanged](https://www.tencentcloud.com/document/product/647/54863#bcc8d33dab3ea6791703f3755bd5986b) | The key-value of room metadata has changed. |
| [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54863#823d44ecd328c1436a8d7e324c5654b1) | Remote user entered room. |
| [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/54863#464debb75790e0f51f4d1690fa4e4450) | Remote user left room. |
| [onUserInfoChanged](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) | User information has changed in the room. |
| [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54863#1b5f1be3b9eacef43456b28a335bde63) | The status of the user has video stream changed. |
| [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54863#0d385087f48c9f2d85d650f492bacb9d) | The status of the user has audio stream changed. |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/54863#b0dfa9b3b96e9704c57c81f4f4e3c35a) | User volume changed. |
| [onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/54863#493bc419ce28818107f146e7f1563893) | The status of disabling to send message has changed for user. |
| [onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/54863#13f898da65ec4ad64994746ac417fbc1) | The User network status changed. |
| [onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/54863#bdd10647f4a557c8225bc897047ad3db) | Screen sharing stopped. |
| [onUserVideoSizeChanged](https://www.tencentcloud.com/document/product/647/54863#a8f343f64a1c508ccfc9fe547e22e687) | The User video size changed. |
| [onSeatListChanged](https://www.tencentcloud.com/document/product/647/54863#d544966ec2d49b6f777c2474c0ad0d91) | Seat list changed. |
| [onKickedOffSeat](https://www.tencentcloud.com/document/product/647/54863#4e11a93aedd2ef4b75a7bc5f9a925032) | The user was kicked off the seat. |
| [onRequestReceived](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) | Receive a request message. |
| [onRequestCancelled](https://www.tencentcloud.com/document/product/647/54863#635b121d6722a2a7c7a69bcf1bc4981a) | Received a cancelled request. |
| [onRequestProcessed](https://www.tencentcloud.com/document/product/647/54863#bee4b3bdf3bee6c00ec58801b882ceca) | Receive a request to be processed by other administrator/owner. |
| [onReceiveTextMessage](https://www.tencentcloud.com/document/product/647/54863#386f4c4ff37a699303b09b64bd051b99) | Text message received |
| [onReceiveCustomMessage](https://www.tencentcloud.com/document/product/647/54863#5abdba4e2d80e39bbc9a268e4fd07791) | Custom message received |

## onError

**onError**

| void onError | (TUICommonDefine.[Error](https://www.tencentcloud.com/document/product/647/54863#2db3f881372c598e3e647f3b17915369) errorCode |
| --- | --- |
|  | String message) |

#### Error event callback.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Callback error events when entering a room or opening a device.

| Param | DESC |
| --- | --- |
| errorCode | Error code. More details, see: [Error](https://www.tencentcloud.com/document/product/647/54863#2db3f881372c598e3e647f3b17915369). |
| message | Error message. |

## onKickedOffLine

**onKickedOffLine**

| void onKickedOffLine | (String message) |
| --- | --- |

#### The current user was kicked offline.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user is kicked offline.

| Param | DESC |
| --- | --- |
| message | Description of being kicked off. |

## onUserSigExpired

**onUserSigExpired**

#### The current user signature is expired.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user's signature expires.

## onRoomNameChanged

**onRoomNameChanged**

| void onRoomNameChanged | (String roomId |
| --- | --- |
|  | String roomName) |

#### The name of the room has changed.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when the room name changes.

| Param | DESC |
| --- | --- |
| roomId | Room ID. |
| roomName | Room name. |

## onAllUserMicrophoneDisableChanged

**onAllUserMicrophoneDisableChanged**

| void onAllUserMicrophoneDisableChanged | (String roomId |
| --- | --- |
|  | boolean isDisable) |

#### The status of disabling to open microphone has changed for all users.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to open microphone false: enable user to open microphone. |
| roomId | Room ID. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type..Called when the microphone disable status changes for all users.

## onAllUserCameraDisableChanged

**onAllUserCameraDisableChanged**

| void onAllUserCameraDisableChanged | (String roomId |
| --- | --- |
|  | boolean isDisable) |

#### The status of disabling to open camera has changed for all users.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to open camera false: enable user to open camera. |
| roomId | Room ID. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type..Called when the camera disable status changes for all users.

## onScreenShareForAllUserDisableChanged

**onScreenShareForAllUserDisableChanged**

| void onScreenShareForAllUserDisableChanged | (String roomId |
| --- | --- |
|  | boolean isDisable) |

#### The status of disabling to open screen sharing has changed for all users.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to open screen sharing false: enable user to open screen sharing. |
| roomId | Room ID. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type..Called when the screen sharing permissions change for all users.

## onSendMessageForAllUserDisableChanged

**onSendMessageForAllUserDisableChanged**

| void onSendMessageForAllUserDisableChanged | (String roomId |
| --- | --- |
|  | boolean isDisable) |

#### The status of disabling to send message has changed for all users.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to send message false: enable user to send message. |
| roomId | Room ID. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type..Called when the message sending permissions change for all users.

## onRoomDismissed

**onRoomDismissed**

| void onRoomDismissed | (String roomId |
| --- | --- |
|  | TUIRoomDefine.[RoomDismissedReason](https://www.tencentcloud.com/document/product/647/64481#5f24e5d31bd068c0cfb09a71f1a3dd1b) reason) |

#### Room was dismissed.

| Param | DESC |
| --- | --- |
| reason | The reason why the room was dismissed. More details, see: [RoomDismissedReason](https://www.tencentcloud.com/document/product/647/64481#5f24e5d31bd068c0cfb09a71f1a3dd1b). |
| roomId | Room ID. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type..Called when the room is dismissed.

## onKickedOutOfRoom

**onKickedOutOfRoom**

| void onKickedOutOfRoom | (String roomId |
| --- | --- |
|  | TUIRoomDefine.[KickedOutOfRoomReason](https://www.tencentcloud.com/document/product/647/64481#0146a10db3e3c88e5e3a3649ef4b8269) reason |
|  | String message) |

#### The current user has been kicked off from the room.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user is kicked out of the room.

| Param | DESC |
| --- | --- |
| message | Description of being kicked off. |
| reason | Reason for being kicked off. |
| roomId | Room ID. |

## onRoomSeatModeChanged

**onRoomSeatModeChanged**

| void onRoomSeatModeChanged | (String roomId |
| --- | --- |
|  | TUIRoomDefine.[SeatMode](https://www.tencentcloud.com/document/product/647/54863#dd614e13a79128f06065469914b9a797) seatMode) |

#### The room seat mode has changed.

| Param | DESC |
| --- | --- |
| roomId | : Room ID. |
| seatMode | : Seat mode. More details, see [TUISeatMode](https://www.tencentcloud.com/document/product/647/64481#908781531506c53abbfa1db07153d7c1).#### [REMARK]The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.Called when the seat mode of the room changes. |

## onRoomUserCountChanged

**onRoomUserCountChanged**

| void onRoomUserCountChanged | (String roomId |
| --- | --- |
|  | int userCount) |

#### The count of user in the room has changed.

| Param | DESC |
| --- | --- |
| roomId | Room ID. |
| userCount | Count of user.#### [REMARK]The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.Called when the user count of the room changes. |

## onRoomMetadataChanged

**onRoomMetadataChanged**

| void onRoomMetadataChanged | (String key |
| --- | --- |
|  | String value) |

#### The key-value of room metadata has changed.

| Param | DESC |
| --- | --- |
| key | The key of room metadata. |
| value | The value of room metadata.#### [REMARK]The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.Called when the custom information of the room changes. |

## onRemoteUserEnterRoom

**onRemoteUserEnterRoom**

| void onRemoteUserEnterRoom | (String roomId |
| --- | --- |
|  | TUIRoomDefine.[UserInfo](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) userInfo) |

#### Remote user entered room.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a remote user enters the room.

| Param | DESC |
| --- | --- |
| roomId | Room ID. |
| userInfo | User information. More details, see [TUIUserInfo](https://www.tencentcloud.com/document/product/647/64481#bc8ea9058aacb64d01afa686523dbdaa). |

## onRemoteUserLeaveRoom

**onRemoteUserLeaveRoom**

| void onRemoteUserLeaveRoom | (String roomId |
| --- | --- |
|  | TUIRoomDefine.[UserInfo](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) userInfo) |

#### Remote user left room.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a remote user leaves the room.

| Param | DESC |
| --- | --- |
| roomId | Room ID. |
| userInfo | User information. More details, see [TUIUserInfo](https://www.tencentcloud.com/document/product/647/64481#bc8ea9058aacb64d01afa686523dbdaa). |

## onUserInfoChanged

**onUserInfoChanged**

| void onUserInfoChanged | (TUIRoomDefine.[UserInfo](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) userInfo |
| --- | --- |
|  | List<TUIRoomDefine.[UserInfoModifyFlag](https://www.tencentcloud.com/document/product/647/64481#25ce7d8fe7ae9d0fb7baecd643a3da03)> modifyFlag) |

#### User information has changed in the room.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user's information changes.

| Param | DESC |
| --- | --- |
| modifyFlag | Modifiable parameter. More details, see [UserInfoModifyFlag](https://www.tencentcloud.com/document/product/647/64481#25ce7d8fe7ae9d0fb7baecd643a3da03). |
| userInfo | User information. More details, see [TUIUserInfo](https://www.tencentcloud.com/document/product/647/64481#bc8ea9058aacb64d01afa686523dbdaa). |

## onUserVideoStateChanged

**onUserVideoStateChanged**

| void onUserVideoStateChanged | (String userId |
| --- | --- |
|  | TUIRoomDefine.[VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0) streamType |
|  | boolean hasVideo |
|  | TUIRoomDefine.[ChangeReason](https://www.tencentcloud.com/document/product/647/64481#4cc7da84ae9c0e2e9a207631c66d29c2) reason) |

#### The status of the user has video stream changed.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user's video state changes.

| Param | DESC |
| --- | --- |
| hasVideo | The current user whether has video stream. |
| reason | The reason why the video stream changed: [BY_SELF](https://www.tencentcloud.com/document/product/647/64481#4cc7da84ae9c0e2e9a207631c66d29c2): Changed by self [BY_ADMIN](https://www.tencentcloud.com/document/product/647/64481#4cc7da84ae9c0e2e9a207631c66d29c2): Changed by administrator. |
| streamType | Video stream type. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0). |
| userId | User ID. |

## onUserAudioStateChanged

**onUserAudioStateChanged**

| void onUserAudioStateChanged | (String userId |
| --- | --- |
|  | boolean hasAudio |
|  | TUIRoomDefine.[ChangeReason](https://www.tencentcloud.com/document/product/647/64481#4cc7da84ae9c0e2e9a207631c66d29c2) reason) |

#### The status of the user has audio stream changed.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user's audio state changes.

| Param | DESC |
| --- | --- |
| hasAudio | The current user whether has audio stream. |
| reason | The reason why the video stream changed: [BY_SELF](https://www.tencentcloud.com/document/product/647/64481#4cc7da84ae9c0e2e9a207631c66d29c2): Changed by self [BY_ADMIN](https://www.tencentcloud.com/document/product/647/64481#4cc7da84ae9c0e2e9a207631c66d29c2): Changed by administrator. |
| userId | User ID. |

## onUserVoiceVolumeChanged

**onUserVoiceVolumeChanged**

| void onUserVoiceVolumeChanged | (Map<String, Integer> volumeMap) |
| --- | --- |

#### User volume changed.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user's voice volume changes.

| Param | DESC |
| --- | --- |
| volumeMap | : User volume dictionary key: userId, value: the volume of all speaking users, with a value range of 0 - 100. |

## onSendMessageForUserDisableChanged

**onSendMessageForUserDisableChanged**

| void onSendMessageForUserDisableChanged | (String roomId |
| --- | --- |
|  | String userId |
|  | boolean isDisable) |

#### The status of disabling to send message has changed for user.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user's message sending permissions change.

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to send message false: enable user to send message. |
| userId | User ID. |

## onUserNetworkQualityChanged

**onUserNetworkQualityChanged**

| void onUserNetworkQualityChanged | (Map<String, TUICommonDefine.[NetworkInfo](https://www.tencentcloud.com/document/product/647/64480#f05ccf0cb4317161e0b13fc79fcf0ceb)> networkMap) |
| --- | --- |

#### The User network status changed.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user's network quality changes.

| Param | DESC |
| --- | --- |
| networkMap | User network status Map. More details, see [NetworkInfo](https://www.tencentcloud.com/document/product/647/64480#f05ccf0cb4317161e0b13fc79fcf0ceb). |

## onUserScreenCaptureStopped

**onUserScreenCaptureStopped**

| void onUserScreenCaptureStopped | (int reason) |
| --- | --- |

#### Screen sharing stopped.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user's screen capture stops.

| Param | DESC |
| --- | --- |
| reason | Stop reason, 0: user actively stops; 1: the screen or the window is closed ; 2: the status of the screen or the window has changed (such as device disconnect). |

## onUserVideoSizeChanged

**onUserVideoSizeChanged**

| void onUserVideoSizeChanged | (String roomId |
| --- | --- |
|  | String userId |
|  | TUIRoomDefine.[VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0) streamType |
|  | int width |
|  | int height) |

#### The User video size changed.

The function supports the ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)) room types.

Called when a user's video size changes.

| Param | DESC |
| --- | --- |
| height | Video height. |
| roomId | Room ID. |
| streamType | Video stream type. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0). |
| userId | User ID or mixed stream ID. When the local user is an audience and successfully connected to the host, this parameter represents the host's user ID; otherwise, it represents the mixed stream ID. |
| width | Video width. |

## onSeatListChanged

**onSeatListChanged**

| void onSeatListChanged | (List<TUIRoomDefine.[SeatInfo](https://www.tencentcloud.com/document/product/647/64481#4ecfc5204fdb0d82f7204f69541f4aba)> seatList |
| --- | --- |
|  | List<TUIRoomDefine.[SeatInfo](https://www.tencentcloud.com/document/product/647/64481#4ecfc5204fdb0d82f7204f69541f4aba)> seatedList |
|  | List<TUIRoomDefine.[SeatInfo](https://www.tencentcloud.com/document/product/647/64481#4ecfc5204fdb0d82f7204f69541f4aba)> leftList) |

#### Seat list changed.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when the seat list changes.

| Param | DESC |
| --- | --- |
| leftList | List of newly leave-seat users. |
| seatList | The latest user list on seat, including new users. |
| seatedList | List of newly take-seat users. |

## onKickedOffSeat

**onKickedOffSeat**

| void onKickedOffSeat | (int seatIndex |
| --- | --- |
|  | TUIRoomDefine.[UserInfo](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) operateUser) |

#### The user was kicked off the seat.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a user is kicked off a seat.

| Param | DESC |
| --- | --- |
| operateUser | User information of the owner/administrator who kicked the user. |
| seatIndex | Seat index. |

## onRequestReceived

**onRequestReceived**

| void onRequestReceived | (TUIRoomDefine.[Request](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) request) |
| --- | --- |

#### Receive a request message.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a request is received.

| Param | DESC |
| --- | --- |
| request | Request content. More details, see [Request](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667). |

## onRequestCancelled

**onRequestCancelled**

| void onRequestCancelled | (TUIRoomDefine.[Request](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) request |
| --- | --- |
|  | TUIRoomDefine.[UserInfo](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) operateUser) |

#### Received a cancelled request.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a request is cancelled.

| Param | DESC |
| --- | --- |
| operateUser | Operator information. |
| request | Request content. More details, see [Request](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667). |

## onRequestProcessed

**onRequestProcessed**

| void onRequestProcessed | (TUIRoomDefine.[Request](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) request |
| --- | --- |
|  | TUIRoomDefine.[UserInfo](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) operateUser) |

#### Receive a request to be processed by other administrator/owner.

The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

Called when a request is processed.

| Param | DESC |
| --- | --- |
| operateUser | Operator information. |
| request | Request content. More details, see [Request](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667). |

## onReceiveTextMessage

**onReceiveTextMessage**

| void onReceiveTextMessage | (TUIRoomDefine.[RoomTextMessage](https://www.tencentcloud.com/document/product/647/64481#689abfd294b9f06b1438a1b3f71b0bbf) textMessage) |
| --- | --- |

#### Text message received

| Param | DESC |
| --- | --- |
| textMessage | The message object, see the $TUIRoomTextMessage$ object for details. |

## onReceiveCustomMessage

**onReceiveCustomMessage**

| void onReceiveCustomMessage | (TUIRoomDefine.[RoomCustomMessage](https://www.tencentcloud.com/document/product/647/64481#144f8c845a241d5f390c8ff49ea33ee1) customMessage) |
| --- | --- |

#### Custom message received

| Param | DESC |
| --- | --- |
| customMessage | The message object, see the $TUIRoomCustomMessage$ object for details. |


---
*Source: [https://trtc.io/document/54863](https://trtc.io/document/54863)*
