# API Overview

**API OVERVIEW**

## Creating instances and event callback.

| FuncList | DESC |
| --- | --- |
| [sharedInstance](https://www.tencentcloud.com/document/product/647/54855#7591fdc3a0ca12c99ae6e02bd406ed17) | Create a TUIRoomEngine instance (singleton pattern). |
| [destroySharedInstance](https://www.tencentcloud.com/document/product/647/54855#665e37566fe89fb0abeb66ef2fc3d5db) | Destroy the TUIRoomEngine instance (singleton pattern). |
| [loginWithSDKAppId:userId:userSig:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#fb5d593fb688c5e26a700db98250e6dd) | After creating a TUIRoomEngine instance, you should login with sdkAppId, userId and userSig then you can call TUIRoomEngine instance and other function. |
| [logout:onError:](https://www.tencentcloud.com/document/product/647/54855#509b68f796961e5de754932fb21aa50a) | Log out of your account. If you are in the room, there will be active leaving room and destroying resource operations. |
| [setSelfInfoWithUserName:avatarUrl:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#0cf77ae0514c515dc5be4203a6d44f34) | Update user name and avatar for logged-in user. |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/54855#55196a0862d9231f772d05263e703cb2) | Return the basic information of the logged-in user, including nickname and avatar. |
| [setSelfInfo:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#b3121cde5287dbe110376617320fad58) | Update user basic information for logged-in user. |
| [addObserver:](https://www.tencentcloud.com/document/product/647/54855#b272afc5ebfd02ef90e7e8dc599a4b82) | Set event observer. |
| [removeObserver:](https://www.tencentcloud.com/document/product/647/54855#34e77ed104d979192e355dbb31e84fbf) | Remove event observer. |

## Room APIs.

| FuncList | DESC |
| --- | --- |
| [createRoom:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#4d0e7ddf563f6245a1d812b0690a5eea) | Create a room. |
| [destroyRoom:onError:](https://www.tencentcloud.com/document/product/647/54855#31650ce63622900078ee2f81c23e4454) | Dismiss the room. |
| [enterRoom:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#e76b632b17a47f9254f32d2f5ed96222) | Enter a room. |
| [enterRoom:roomType:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#c14956bfcb56cb3759b498050631331a) | Enter a room. |
| [enterRoom:roomType:options:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#3e5f7fdc1c30135d17bd4464609d99e4) | Enter a room. |
| [exitRoom:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#cb2aa94c3b2e1d926793eb7aaab410e8) | Exit the room. |
| [fetchRoomInfo:onError:](https://www.tencentcloud.com/document/product/647/54855#f6d4167648189c5290b711062c74e8fd) | Fetch room information. |
| [fetchRoomInfo:roomType:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#26f5a1529c27553cce6c56d942c80ad0) | Fetch Specified Room Information. |
| [updateRoomNameByAdmin:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#bc6afcb38590615a5df7600df29367ba) | Update room name (only support for administrators or room owner). |
| [updateRoomSeatModeByAdmin:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#d06444a359611753052ac864c5b611e9) | Update room seat mode (only support for administrators or room owner). |
| [updateRoomPasswordByAdmin:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#8a55267d6730bb708d531581746fa966) | Update room password (only support for administrators or room owner). |
| [getRoomMetadata:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#f7eb8d8350b755920accc62b1b7e4397) | Get room metadata. |
| [setRoomMetadataByAdmin](https://www.tencentcloud.com/document/product/647/54855#fba0ca6c5bae1858bcf81734036248cc) | Set room metadata, if the key already exists, update its value, if not, add the key. |

## Local user view rendering, video management.

| FuncList | DESC |
| --- | --- |
| [setLocalVideoView:](https://www.tencentcloud.com/document/product/647/54855#55a67c65f1344a3339ee151b807d24ab) | Set the local camera to preview the render view. |
| [openLocalCamera:quality:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#f72c16229f46ba7b28b0d9849ac98826) | Open the local camera. |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/54855#ff4537fd911678280a013b61005345ed) | Close the local camera. |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/54855#b178202f1acaedf7f1088ce109d3f963) | Start publishing local video stream, default enabled. |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/54855#4500cae058442aa6cf0660899c590b9d) | Stop publishing local video stream. |
| [updateVideoQuality:](https://www.tencentcloud.com/document/product/647/54855#486a72e802a93ad219ac70b2f987ff2d) | Update video encoding quality. |
| [updateVideoQualityEx:params:](https://www.tencentcloud.com/document/product/647/54855#bf634578e3304a18894e04560468c20f) | Set the video encoding parameters. |
| [setVideoResolutionMode:resolutionMode:](https://www.tencentcloud.com/document/product/647/54855#60c1bc35ad2ebbe4b19198bc16ea2865) | Set the video resolution mode (horizontal resolution or vertical resolution). |
| [setLocalVideoMuteImage:](https://www.tencentcloud.com/document/product/647/54855#0fdb2eda054cdf1d2b7c74268d16c62a) | Set the substitute image for local video during pause. |
| [enableGravitySensor:](https://www.tencentcloud.com/document/product/647/54855#e43024d3910ad9ec7001aa44bc8275af) | Turn on gravity sensing mode. (only availble on mobile OS and the camera capture scene inside the SDK). |
| [startScreenCaptureByReplaykit:](https://www.tencentcloud.com/document/product/647/54855#fe00b96dd343d6975b4350efc157d5c8) | Start screen sharing (only available on mobile OS). |
| [startScreenCapture:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#f0c5bef34ea01c7a57f75905a116b310) | Start screen sharing (only available on Mac OS). |
| [stopScreenCapture](https://www.tencentcloud.com/document/product/647/54855#0fa4aee168037d922e21047913bb8382) | Stop screen sharing. |
| [getScreenCaptureSources](https://www.tencentcloud.com/document/product/647/54855#45bab04fe4f34e65db53282904eab4db) | Get the sharable screen and windows (only available on Mac OS) |
| [selectScreenCaptureTarget:](https://www.tencentcloud.com/document/product/647/54855#fe760c4f87bf7d13e878f0085bdb06e9) | Select the screen or windows to share (only available on Mac OS) |

## Local User Audio Management.

| FuncList | DESC |
| --- | --- |
| [openLocalMicrophone:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#0d61ecfc837ff6d44e5a5c3d0faee8b3) | Open local microphone. |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/54855#6a5f4544cf81d483a4dba368545f94b9) | Close the local microphone. |
| [updateAudioQuality:](https://www.tencentcloud.com/document/product/647/54855#8b1839388fa8e799f0ae35c49a3f2911) | Update audio encoding quality. |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/54855#c64198c0a04341cac736e4104ebdf0bd) | Pause publishing the local audio stream. |
| [unmuteLocalAudio:onError:](https://www.tencentcloud.com/document/product/647/54855#14f97e6ab0e879b699ab0e37b485eba4) | Resume publishing the local audio stream. |
| [enableSystemAudioSharing:](https://www.tencentcloud.com/document/product/647/54855#25c0877abd6134e2522eafe7c4de65f9) | Enable system audio sharing |

## Remote user view rendering and video management.

| FuncList | DESC |
| --- | --- |
| [setRemoteVideoView:streamType:view:](https://www.tencentcloud.com/document/product/647/54855#e3a3d88e04a1f569e6dcb68d91cce59a) | Set the render view for remote user. |
| [startPlayRemoteVideo:streamType:onPlaying:onLoading:onError:](https://www.tencentcloud.com/document/product/647/54855#989232414785216d37587684becbb483) | Start playing the remote user's video stream. |
| [stopPlayRemoteVideo:streamType:](https://www.tencentcloud.com/document/product/647/54855#5500e4b4d12b3d56faee3eb725b00f1a) | Stop playing the remote user's video stream. |
| [muteRemoteAudioStream:isMute:](https://www.tencentcloud.com/document/product/647/54855#b78726b72ddf579f240da34884b2c609) | Mute the remote user's audio stream. |

## User information in the room.

| FuncList | DESC |
| --- | --- |
| [getUserList:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#1e4f7da192b0128754ba6e9f385bed8d) | Get the list of user in the room. |
| [getUserInfo:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#ec236cd0d12ab2fce2ca5621f668ab5d) | Get user information. |

## User management in the room.

| FuncList | DESC |
| --- | --- |
| [changeUserRole:role:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#17f8c2dc10f266cbc78d3b1812f95240) | Change user role (only support for administrators or room owner). |
| [changeUserNameCard:nameCard:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#b1ea3d2360a2c0889ffc5cf382fb9da2) | Change user nickname in the room (only support to change all user for administrators or room owner, user can only change by self). |
| [kickRemoteUserOutOfRoom:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#fa4bd9852c77cf5f5b7be203fe6dbb22) | Kick the remote user out of the room (only support for administrators or room owner). |
| [addCategoryTagForUsers:userList:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#619bec5e8dcb6619488732a8a9effaae) | Add a tag for the user (only support for administrators or room owner). |
| [removeCategoryTagForUsers:userList:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#6e3ba5a485a91fc43757891c4dc99d27) | Remove tag for user (only support for room owner). |
| [getUserListByTag:nextSequence:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#333966765d152e41f549157cc2ab7071) | Get user information in the room based on the tag. |
| [setCustomInfoForUser:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#56222c867961904dc8769ad714bba5fe) | Set custom information for room users. |

## User speech management in the room.

| FuncList | DESC |
| --- | --- |
| [disableDeviceForAllUserByAdmin:isDisable:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#8f96b729c8a9948c9cf7d2ebfd6ff48f) | The owner or administrator control that all users whether can open device. For example: all users are prohibited from opening the microphone(only available in the conference scenario). |
| [openRemoteDeviceByAdmin:device:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:](https://www.tencentcloud.com/document/product/647/54855#5efa632932881735e551ff016402160b) | Request the remote user to open the media device (only support for administrators or room owner). |
| [closeRemoteDeviceByAdmin:device:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#780489248cb022a5495812a6eb072317) | Close remote user media devices (only support for administrators or room owner). |
| [applyToAdminToOpenLocalDevice:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:](https://www.tencentcloud.com/document/product/647/54855#4993a64e14a999449612351df8a574c6) | Apply to open the local media device (available to general users). |

## Seat management in the room.

| FuncList | DESC |
| --- | --- |
| [getSeatList:onError:](https://www.tencentcloud.com/document/product/647/54855#9a8217b0951913d5c24a3418cd5f452d) | Get seat list. |
| [lockSeatByAdmin:lockMode:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#df1f081b00d3640cd6173899e788d9bf) | Lock the seat (only support for administrators or room owner). |
| [takeSeat:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:](https://www.tencentcloud.com/document/product/647/54855#b7dec60a76be6d9a9b63093319301943) | Take the seat. |
| [leaveSeat:onError:](https://www.tencentcloud.com/document/product/647/54855#f301d65082c9fe6e54df6f74522df36d) | Leave the seat. |
| [moveToSeat:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#17c6072ee712ee80751eb30a5815ff1b) | Move to seat. |
| [takeUserOnSeatByAdmin:userId:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:](https://www.tencentcloud.com/document/product/647/54855#060623f0395a1416baf48ebd80c598f1) | Invite user to take the seat (only support for administrators or room owner). |
| [kickUserOffSeatByAdmin:userId:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#4fc6a6c9e386a7a0d9dda3a6a0aade6f) | Kick off the user from seat (only support for administrators or room owner). |
| [getSeatApplicationList:onError:](https://www.tencentcloud.com/document/product/647/54855#318ba4689ead5ec4214664f23c92a6e3) | Get the request list of users who want to take the seat in the room (only support for administrators or room owner). |

## Message.

| FuncList | DESC |
| --- | --- |
| [disableSendingMessageByAdmin:isDisable:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#99f76e01022ed98bcb8759320810d85b) | Disable the ability of remote users to send messages (only support for administrators or room owner). |
| [disableSendingMessageForAllUser:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#88f96a71fd0ee8c59ab3cdecd0930551) | Disable the ability of all users to send messages (only support for administrators or room owner). |
| [sendTextMessage:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#2211c4227dfecaf8a1a0448d943599d2) | Send text message |
| [sendCustomMessage:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#a6092b6681c81429033efd93161b415e) | Send custom message |

## Request Management.

| FuncList | DESC |
| --- | --- |
| [cancelRequest:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#17ba27cad02e54757cdd41e442ddfbbc) | Cancel request. |
| [responseRemoteRequest:agree:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#10789c19d23dec9a25d6c8bfab407f23) | Response request. |

## Advanced Features.

| FuncList | DESC |
| --- | --- |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/54855#d3c48e3c9d0f371386ca7b0589ef4c88) | Get the TRTC instance object. |
| [setBeautyLevel:beautyLevel:](https://www.tencentcloud.com/document/product/647/54855#4c6d4893dba79b7e4a41a001eaea1534) | Set the beauty level. |
| [setWhitenessLevel:](https://www.tencentcloud.com/document/product/647/54855#ba29ed099d81a69fc300a82caebb8fde) | Set whitening level. |
| [getExtension:](https://www.tencentcloud.com/document/product/647/54855#b99da8d3a9d62547dd23c56e0b4436c0) | Get the extension. |
| [getMediaDeviceManager](https://www.tencentcloud.com/document/product/647/54855#c6483c3f80f639d0eb3fd076f02872d6) | Get device management class. |
| [getLiveConnectionManager](https://www.tencentcloud.com/document/product/647/54855#fdb1665975863e593233d97715af0dc5) | Get live-connection management class. |
| [getLiveBattleManager](https://www.tencentcloud.com/document/product/647/54855#0a32a3590a6ae1e2776d80e5eb3040e1) | Get live-battle management class. |

## Debug related.

| FuncList | DESC |
| --- | --- |
| [callExperimentalAPI:callback:](https://www.tencentcloud.com/document/product/647/54855#91021955c4aadb7dfcbff8f0376f0106) | Call experimental APIs. |

## Error event callback.

| FuncList | DESC |
| --- | --- |
| [onError:message:](https://www.tencentcloud.com/document/product/647/54854#e2d2a8b13e80bbe60e2467739f0a0316) | Error event callback. |

## Login status event callback.

| FuncList | DESC |
| --- | --- |
| [onKickedOffLine:](https://www.tencentcloud.com/document/product/647/54854#b0238d7b1fa86af2c540ec313dba8e6b) | The current user was kicked offline. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/54854#7b8df3f701ffd641b11047e27094d8db) | The current user signature is expired. |

## Event callback in the room.

| FuncList | DESC |
| --- | --- |
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

## User event callback in the room.

| FuncList | DESC |
| --- | --- |
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

## Seat event callback in the room.

| FuncList | DESC |
| --- | --- |
| [onSeatListChanged:seated:left:](https://www.tencentcloud.com/document/product/647/54854#31a13be6f374e28422eb363a518b235f) | Seat list changed. |
| [onKickedOffSeat:operateUser:](https://www.tencentcloud.com/document/product/647/54854#bd26ee6b56090e87eb9409c47df09435) | The user was kicked off the seat. |

## Request event callback.

| FuncList | DESC |
| --- | --- |
| [onRequestReceived:](https://www.tencentcloud.com/document/product/647/54854#3697d1d038fd6f3ebe54ea33cd32e3df) | Receive a request message. |
| [onRequestCancelled:operateUser:](https://www.tencentcloud.com/document/product/647/54854#92b334084d0e34a0a3d4507e02acb850) | Received a cancelled request. |
| [onRequestProcessed:operateUser:](https://www.tencentcloud.com/document/product/647/54854#ca708aa561838272c90fa5e3e4eb41e7) | Receive a request to be processed by other administrator/owner. |
| [onReceiveTextMessage:](https://www.tencentcloud.com/document/product/647/54854#ac7c0d898f526f0f902a83c49afffd64) | Text message received |

## Message event in the room

| FuncList | DESC |
| --- | --- |
| [onRequestReceived:](https://www.tencentcloud.com/document/product/647/54854#3697d1d038fd6f3ebe54ea33cd32e3df) | Receive a request message. |
| [onReceiveTextMessage:](https://www.tencentcloud.com/document/product/647/54854#ac7c0d898f526f0f902a83c49afffd64) | Text message received |
| [onReceiveCustomMessage:](https://www.tencentcloud.com/document/product/647/54854#a8574308a070707a877d1c699a9c3aba) | Custom message received |

## Deprecated callbacks.

| FuncList | DESC |
| --- | --- |
| [onDeviceChanged:type:state:](https://www.tencentcloud.com/document/product/647/54854#8bb5da23b114eee5d7422671ada72503) | Local device added. |


---
*Source: [https://trtc.io/document/54856](https://trtc.io/document/54856)*
