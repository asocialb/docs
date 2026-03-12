# API Overview

**API OVERVIEW**

## Error event callback.

| FuncList | DESC |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/54863#2db3f881372c598e3e647f3b17915369) | Error event callback. |

## Login status event callback.

| FuncList | DESC |
| --- | --- |
| [onKickedOffLine](https://www.tencentcloud.com/document/product/647/54863#5dfa1251a6787bde3f2f1d1a4b1bab88) | The current user was kicked offline. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/54863#4309a1386c7b4635777bb8520b0c44fc) | The current user signature is expired. |

## Event callback in the room.

| FuncList | DESC |
| --- | --- |
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

## User event callback in the room.

| FuncList | DESC |
| --- | --- |
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

## Seat event callback in the room.

| FuncList | DESC |
| --- | --- |
| [onSeatListChanged](https://www.tencentcloud.com/document/product/647/54863#d544966ec2d49b6f777c2474c0ad0d91) | Seat list changed. |
| [onKickedOffSeat](https://www.tencentcloud.com/document/product/647/54863#4e11a93aedd2ef4b75a7bc5f9a925032) | The user was kicked off the seat. |

## Request event callback.

| FuncList | DESC |
| --- | --- |
| [onRequestReceived](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) | Receive a request message. |
| [onRequestCancelled](https://www.tencentcloud.com/document/product/647/54863#635b121d6722a2a7c7a69bcf1bc4981a) | Received a cancelled request. |
| [onRequestProcessed](https://www.tencentcloud.com/document/product/647/54863#bee4b3bdf3bee6c00ec58801b882ceca) | Receive a request to be processed by other administrator/owner. |
| [onReceiveTextMessage](https://www.tencentcloud.com/document/product/647/54863#386f4c4ff37a699303b09b64bd051b99) | Text message received |

## Message event in the room

| FuncList | DESC |
| --- | --- |
| [onRequestReceived](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) | Receive a request message. |
| [onReceiveTextMessage](https://www.tencentcloud.com/document/product/647/54863#386f4c4ff37a699303b09b64bd051b99) | Text message received |
| [onReceiveCustomMessage](https://www.tencentcloud.com/document/product/647/54863#5abdba4e2d80e39bbc9a268e4fd07791) | Custom message received |

## Creating instances and event callback.

| FuncList | DESC |
| --- | --- |
| [sharedInstance](https://www.tencentcloud.com/document/product/647/54864#16cf67c8716b1c79b762d19e4ab99008) | Create a TUIRoomEngine instance (singleton pattern). |
| [destroySharedInstance](https://www.tencentcloud.com/document/product/647/54864#56ce73cf1f0b6bf6492c81d308ec029d) | Destroy the TUIRoomEngine instance (singleton pattern). |
| [login](https://www.tencentcloud.com/document/product/647/54864#e91313128572e17f2397f7be8edd93cf) | After creating a TUIRoomEngine instance, you should login with sdkAppId, userId and userSig then you can call TUIRoomEngine instance and other function. |
| [logout](https://www.tencentcloud.com/document/product/647/54864#45756ace1ef6c82297eee3fac5cd8667) | Log out of your account. If you are in the room, there will be active leaving room and destroying resource operations. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54864#bc3705389df676bb8e8cb68942dd820f) | Update user name and avatar for logged-in user. |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/54864#946bae7d91f5073f8044633a79a3c227) | Return the basic information of the logged-in user, including nickname and avatar. |
| [addObserver](https://www.tencentcloud.com/document/product/647/54864#aa9e2a751854badf8d300deef59680b9) | Set event observer. |
| [removeObserver](https://www.tencentcloud.com/document/product/647/54864#a66b02c83a4371533c8076e9715d13b8) | Remove event observer. |

## Room APIs.

| FuncList | DESC |
| --- | --- |
| [createRoom](https://www.tencentcloud.com/document/product/647/54864#911bbef4c82371be741fa4c6c0693907) | Create a room. |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/54864#9141c0291abba473fe8daeb75e3e052c) | Dismiss the room. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54864#35fdf16804f2627fec75cdce28ffc6cc) | Enter a room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/54864#380786b98d56b95daf683fa4d68af388) | Exit the room. |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/54864#592e4c141886cc8b8666cf8dfefc3a8f) | Fetch room information. |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/54864#d970bfb9100d587e0d008db312b5bc5b) | Update room name (only support for administrators or room owner). |
| [updateRoomSeatModeByAdmin](https://www.tencentcloud.com/document/product/647/54864#07121319d8ae42ebccb1761dcbe508a4) | Update room seat mode (only support for administrators or room owner). |
| [updateRoomPasswordByAdmin](https://www.tencentcloud.com/document/product/647/54864#cac0a265de041de6d6e57aa57d705ad6) | Update room password (only support for administrators or room owner). |
| [getRoomMetadata](https://www.tencentcloud.com/document/product/647/54864#4bf28fcd8a1146b0662779f3094a509e) | Get room metadata. |
| [setRoomMetadataByAdmin](https://www.tencentcloud.com/document/product/647/54864#e774ac4968fa3eef64f36571ae2afe42) | Set room metadata, if the key already exists, update its value, if not, add the key. |

## Local user view rendering, video management.

| FuncList | DESC |
| --- | --- |
| [setLocalVideoView](https://www.tencentcloud.com/document/product/647/54864#98362c835e4499225b7f36ad9336d924) | Set the local camera to preview the render view. |
| [openLocalCamera](https://www.tencentcloud.com/document/product/647/54864#67c926e68b2bc30b9e20e0a0c4745bdf) | Open the local camera. |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/54864#ef8016748e2d62b77b933cbbc0bc70d7) | Close the local camera. |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/54864#899becc4c8470f2036a8e53131814471) | Start publishing local video stream, default enabled. |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/54864#672b82fcec8a33f5f4c2009321012adc) | Stop publishing local video stream. |
| [updateVideoQuality](https://www.tencentcloud.com/document/product/647/54864#ea061bff081ab6fb25c9d23efbb659b3) | Update video encoding quality. |
| [updateVideoQualityEx](https://www.tencentcloud.com/document/product/647/54864#79bd53687be4c329a1674d28be1ce907) | Set the video encoding parameters. |
| [setVideoResolutionMode](https://www.tencentcloud.com/document/product/647/54864#a995efd41a996d7c0b09a3efb5ff5df1) | Set the video resolution mode (horizontal resolution or vertical resolution). |
| [setLocalVideoMuteImage](https://www.tencentcloud.com/document/product/647/54864#b8375cb87e8315e878fcaf6b12c12c5b) | Set the substitute image for local video during pause. |
| [enableGravitySensor](https://www.tencentcloud.com/document/product/647/54864#69775a6d4050ab5f60bdccedf14e9182) | Turn on gravity sensing mode. (only availble on mobile OS and the camera capture scene inside the SDK). |
| [startScreenSharing](https://www.tencentcloud.com/document/product/647/54864#cc949f99d6a39e2bcf4723b664fe2d74) | Start screen sharing (only available on mobile OS). |
| [stopScreenSharing](https://www.tencentcloud.com/document/product/647/54864#9c5fa0c202a0f5b24fed30ddf9e62939) | Stop screen sharing. |

## Local User Audio Management.

| FuncList | DESC |
| --- | --- |
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/54864#0e9b0f5598d305831ddb19ece07f1b91) | Open local microphone. |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/54864#f677ac0fc0aa1efcd27121054699bfdc) | Close the local microphone. |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/54864#778e31acbb656244cffdb4450ba0c156) | Update audio encoding quality. |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/54864#80693da4a3b18e07d92a802485f6334e) | Pause publishing the local audio stream. |
| [unmuteLocalAudio](https://www.tencentcloud.com/document/product/647/54864#2a622d95aa2f7305de666cbec7109d77) | Resume publishing the local audio stream. |
| [enableSystemAudioSharing](https://www.tencentcloud.com/document/product/647/54864#da0b9688d75cd77f51984e71566fab47) | Enable system audio sharing |

## Remote user view rendering and video management.

| FuncList | DESC |
| --- | --- |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/54864#0e6f5fe07c0f268923e502a3a2be76c1) | Set the render view for remote user. |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54864#72d1726923e949d2c443dd96aa4deeca) | Start playing the remote user's video stream. |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54864#4d251840dd060f6ee45f3d41ad7a6c84) | Stop playing the remote user's video stream. |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/54864#2184de7077cf5dc9f3165329efbf43b5) | Mute the remote user's audio stream. |

## User information in the room.

| FuncList | DESC |
| --- | --- |
| [getUserList](https://www.tencentcloud.com/document/product/647/54864#699fe77c2784c5d75f05078d5add27fb) | Get the list of user in the room. |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/54864#6cd5c36b39754b71ad5cce7bfd2ff4b4) | Get user information. |

## User management in the room.

| FuncList | DESC |
| --- | --- |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/54864#f0cf468f4a2fa73a73f82e60329ae649) | Change user role (only support for administrators or room owner). |
| [changeUserNameCard](https://www.tencentcloud.com/document/product/647/54864#33b8996e2230421dfb1a9c3bc00ecdf7) | Change user nickname in the room (only support to change all user for administrators or room owner, user can only change by self). |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/54864#258101fd02fe373bb682f479d15fc059) | Kick the remote user out of the room (only support for administrators or room owner). |
| [addCategoryTagForUsers](https://www.tencentcloud.com/document/product/647/54864#a1345a3a776cab7c63c0e073b4885481) | Add a tag for the user (only support for administrators or room owner). |
| [removeCategoryTagForUsers](https://www.tencentcloud.com/document/product/647/54864#045a6dc44d38e0d1ac8e282cd1d1676e) | Remove tag for user (only support for room owner). |
| [getUserListByTag](https://www.tencentcloud.com/document/product/647/54864#c27be9df993987f57823fb7d0946722f) | Get user information in the room based on the tag. |
| [setCustomInfoForUser](https://www.tencentcloud.com/document/product/647/54864#f8c95b9ae30880404583b6786a3e4789) | Set custom information for room users. |

## User speech management in the room.

| FuncList | DESC |
| --- | --- |
| [disableDeviceForAllUserByAdmin](https://www.tencentcloud.com/document/product/647/54864#1ecce7f3cdb7dbb6f35fbaa3cc741122) | The owner or administrator control that all users whether can open device. For example: all users are prohibited from opening the microphone(only available in the conference scenario). |
| [openRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54864#590f32d6fe85c2fc80c339937aac9cdc) | Request the remote user to open the media device (only support for administrators or room owner). |
| [closeRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54864#510e6569a496ebad2e04bde91326eb60) | Close remote user media devices (only support for administrators or room owner). |
| [applyToAdminToOpenLocalDevice](https://www.tencentcloud.com/document/product/647/54864#4d4e5f3bc13e611768a401b4c3db962f) | Apply to open the local media device (available to general users). |

## Seat management in the room.

| FuncList | DESC |
| --- | --- |
| [getSeatList](https://www.tencentcloud.com/document/product/647/54864#7820648092d091e37560ce0593879fc7) | Get seat list. |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/54864#81044cd0b188305f7227e3863c0e482f) | Lock the seat (only support for administrators or room owner). |
| [takeSeat](https://www.tencentcloud.com/document/product/647/54864#6eee934af96d5538e066a543c637e0cd) | Take the seat. |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/54864#84e97d04aa3dc31eda5d6b1bdeb4c34d) | Leave the seat. |
| [moveToSeat](https://www.tencentcloud.com/document/product/647/54864#60d07dda176d554ffd84e0cf3e373262) | Move to seat. |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/54864#85fcac236a372109a330eb0c5e3f0a0b) | Invite user to take the seat (only support for administrators or room owner). |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/54864#f878dca93c7266e7a132485ba1a00c4d) | Kick off the user from seat (only support for administrators or room owner). |
| [getSeatApplicationList](https://www.tencentcloud.com/document/product/647/54864#54d31a649216d220311f8fcf8f905404) | Get the request list of users who want to take the seat in the room (only support for administrators or room owner). |

## Message.

| FuncList | DESC |
| --- | --- |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/54864#1a14651e5e06305956f7e8dd8c29b821) | Disable the ability of remote users to send messages (only support for administrators or room owner). |
| [disableSendingMessageForAllUser](https://www.tencentcloud.com/document/product/647/54864#5f4a70034d79062967c860559af11b21) | Disable the ability of all users to send messages (only support for administrators or room owner). |
| [sendTextMessage](https://www.tencentcloud.com/document/product/647/54864#b642e3d2cee3cacc9e7c6f47af571314) | Send text message |
| [sendCustomMessage](https://www.tencentcloud.com/document/product/647/54864#7d14723294200fd5aa0c3853884fc97f) | Send custom message |

## Request Management.

| FuncList | DESC |
| --- | --- |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/54864#3271224bcd640ef9a347492b18bed14b) | Cancel request. |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/54864#ca9c83c643f5bd6c26dd23ec34639660) | Response request. |

## Advanced Features.

| FuncList | DESC |
| --- | --- |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/54864#393689f458433968d8dcc9d91635d71b) | Get the TRTC instance object. |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/54864#356c9ac2d40d703ae8075ec6d99719b3) | Set the beauty level. |
| [setWhitenessLevel](https://www.tencentcloud.com/document/product/647/54864#7df1e01587684fba1d0a5766334703b3) | Set whitening level. |
| [getExtension](https://www.tencentcloud.com/document/product/647/54864#5ad5ce957d19bef36541d4eb11a1051e) | Get the extension. |
| [getMediaDeviceManager](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21) | Get device management class. |
| [getLiveConnectionManager](https://www.tencentcloud.com/document/product/647/54864#fe288b50da697505b5ab87a35bed950e) | Get live-connection management class. |
| [getLiveBattleManager](https://www.tencentcloud.com/document/product/647/54864#5d671512de7e22b0507211255a9c123f) | Get live-battle management class. |

## Debug related.

| FuncList | DESC |
| --- | --- |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/54864#781a86cef929d0e20b8721a3e17b3726) | Call experimental APIs. |


---
*Source: [https://trtc.io/document/54861](https://trtc.io/document/54861)*
