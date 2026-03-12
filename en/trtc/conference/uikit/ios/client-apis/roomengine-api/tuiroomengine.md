# TUIRoomEngine

Copyright (c) 2024 Tencent. All rights reserved.

Module:   TUIRoomEngine @ TUIKitEngine.

Function: TUIRoomEngine Main function APIs.

Version: 3.2

**TUIRoomEngine**

## TUIRoomEngine

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
| [openLocalMicrophone:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#0d61ecfc837ff6d44e5a5c3d0faee8b3) | Open local microphone. |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/54855#6a5f4544cf81d483a4dba368545f94b9) | Close the local microphone. |
| [updateAudioQuality:](https://www.tencentcloud.com/document/product/647/54855#8b1839388fa8e799f0ae35c49a3f2911) | Update audio encoding quality. |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/54855#c64198c0a04341cac736e4104ebdf0bd) | Pause publishing the local audio stream. |
| [unmuteLocalAudio:onError:](https://www.tencentcloud.com/document/product/647/54855#14f97e6ab0e879b699ab0e37b485eba4) | Resume publishing the local audio stream. |
| [enableSystemAudioSharing:](https://www.tencentcloud.com/document/product/647/54855#25c0877abd6134e2522eafe7c4de65f9) | Enable system audio sharing |
| [setRemoteVideoView:streamType:view:](https://www.tencentcloud.com/document/product/647/54855#e3a3d88e04a1f569e6dcb68d91cce59a) | Set the render view for remote user. |
| [startPlayRemoteVideo:streamType:onPlaying:onLoading:onError:](https://www.tencentcloud.com/document/product/647/54855#989232414785216d37587684becbb483) | Start playing the remote user's video stream. |
| [stopPlayRemoteVideo:streamType:](https://www.tencentcloud.com/document/product/647/54855#5500e4b4d12b3d56faee3eb725b00f1a) | Stop playing the remote user's video stream. |
| [muteRemoteAudioStream:isMute:](https://www.tencentcloud.com/document/product/647/54855#b78726b72ddf579f240da34884b2c609) | Mute the remote user's audio stream. |
| [getUserList:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#1e4f7da192b0128754ba6e9f385bed8d) | Get the list of user in the room. |
| [getUserInfo:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#ec236cd0d12ab2fce2ca5621f668ab5d) | Get user information. |
| [changeUserRole:role:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#17f8c2dc10f266cbc78d3b1812f95240) | Change user role (only support for administrators or room owner). |
| [changeUserNameCard:nameCard:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#b1ea3d2360a2c0889ffc5cf382fb9da2) | Change user nickname in the room (only support to change all user for administrators or room owner, user can only change by self). |
| [kickRemoteUserOutOfRoom:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#fa4bd9852c77cf5f5b7be203fe6dbb22) | Kick the remote user out of the room (only support for administrators or room owner). |
| [addCategoryTagForUsers:userList:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#619bec5e8dcb6619488732a8a9effaae) | Add a tag for the user (only support for administrators or room owner). |
| [removeCategoryTagForUsers:userList:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#6e3ba5a485a91fc43757891c4dc99d27) | Remove tag for user (only support for room owner). |
| [getUserListByTag:nextSequence:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#333966765d152e41f549157cc2ab7071) | Get user information in the room based on the tag. |
| [setCustomInfoForUser:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#56222c867961904dc8769ad714bba5fe) | Set custom information for room users. |
| [disableDeviceForAllUserByAdmin:isDisable:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#8f96b729c8a9948c9cf7d2ebfd6ff48f) | The owner or administrator control that all users whether can open device. For example: all users are prohibited from opening the microphone(only available in the conference scenario). |
| [openRemoteDeviceByAdmin:device:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:](https://www.tencentcloud.com/document/product/647/54855#5efa632932881735e551ff016402160b) | Request the remote user to open the media device (only support for administrators or room owner). |
| [closeRemoteDeviceByAdmin:device:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#780489248cb022a5495812a6eb072317) | Close remote user media devices (only support for administrators or room owner). |
| [applyToAdminToOpenLocalDevice:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:](https://www.tencentcloud.com/document/product/647/54855#4993a64e14a999449612351df8a574c6) | Apply to open the local media device (available to general users). |
| [getSeatList:onError:](https://www.tencentcloud.com/document/product/647/54855#9a8217b0951913d5c24a3418cd5f452d) | Get seat list. |
| [lockSeatByAdmin:lockMode:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#df1f081b00d3640cd6173899e788d9bf) | Lock the seat (only support for administrators or room owner). |
| [takeSeat:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:](https://www.tencentcloud.com/document/product/647/54855#b7dec60a76be6d9a9b63093319301943) | Take the seat. |
| [leaveSeat:onError:](https://www.tencentcloud.com/document/product/647/54855#f301d65082c9fe6e54df6f74522df36d) | Leave the seat. |
| [moveToSeat:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#17c6072ee712ee80751eb30a5815ff1b) | Move to seat. |
| [takeUserOnSeatByAdmin:userId:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:](https://www.tencentcloud.com/document/product/647/54855#060623f0395a1416baf48ebd80c598f1) | Invite user to take the seat (only support for administrators or room owner). |
| [kickUserOffSeatByAdmin:userId:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#4fc6a6c9e386a7a0d9dda3a6a0aade6f) | Kick off the user from seat (only support for administrators or room owner). |
| [getSeatApplicationList:onError:](https://www.tencentcloud.com/document/product/647/54855#318ba4689ead5ec4214664f23c92a6e3) | Get the request list of users who want to take the seat in the room (only support for administrators or room owner). |
| [disableSendingMessageByAdmin:isDisable:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#99f76e01022ed98bcb8759320810d85b) | Disable the ability of remote users to send messages (only support for administrators or room owner). |
| [disableSendingMessageForAllUser:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#88f96a71fd0ee8c59ab3cdecd0930551) | Disable the ability of all users to send messages (only support for administrators or room owner). |
| [sendTextMessage:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#2211c4227dfecaf8a1a0448d943599d2) | Send text message |
| [sendCustomMessage:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#a6092b6681c81429033efd93161b415e) | Send custom message |
| [cancelRequest:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#17ba27cad02e54757cdd41e442ddfbbc) | Cancel request. |
| [responseRemoteRequest:agree:onSuccess:onError:](https://www.tencentcloud.com/document/product/647/54855#10789c19d23dec9a25d6c8bfab407f23) | Response request. |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/54855#d3c48e3c9d0f371386ca7b0589ef4c88) | Get the TRTC instance object. |
| [setBeautyLevel:beautyLevel:](https://www.tencentcloud.com/document/product/647/54855#4c6d4893dba79b7e4a41a001eaea1534) | Set the beauty level. |
| [setWhitenessLevel:](https://www.tencentcloud.com/document/product/647/54855#ba29ed099d81a69fc300a82caebb8fde) | Set whitening level. |
| [getExtension:](https://www.tencentcloud.com/document/product/647/54855#b99da8d3a9d62547dd23c56e0b4436c0) | Get the extension. |
| [getMediaDeviceManager](https://www.tencentcloud.com/document/product/647/54855#c6483c3f80f639d0eb3fd076f02872d6) | Get device management class. |
| [getLiveConnectionManager](https://www.tencentcloud.com/document/product/647/54855#fdb1665975863e593233d97715af0dc5) | Get live-connection management class. |
| [getLiveBattleManager](https://www.tencentcloud.com/document/product/647/54855#0a32a3590a6ae1e2776d80e5eb3040e1) | Get live-battle management class. |
| [callExperimentalAPI:callback:](https://www.tencentcloud.com/document/product/647/54855#91021955c4aadb7dfcbff8f0376f0106) | Call experimental APIs. |

## sharedInstance

**sharedInstance**

#### Create a TUIRoomEngine instance (singleton pattern).

Description:

- Creates and returns the global shared instance of TUIRoomEngine (singleton pattern).
- Supports both conference and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- Using singleton pattern avoids duplicate engine instance creation and saves resources.

Return value:

- Returns the singleton instance pointer of TUIRoomEngine.

```
// Objective-C Usage example:TUIRoomEngine *engine = [TUIRoomEngine sharedInstance];// Swift Usage example:let engine = TUIRoomEngine.sharedInstance()
```

> **Note** Multiple calls will return the same instance.

## destroySharedInstance

**destroySharedInstance**

#### Destroy the TUIRoomEngine instance (singleton pattern).

Description:

- To avoid unknown exceptions after destroying the singleton instance, this interface is not recommended to be called during program runtime.
- Destroys the global shared instance of TUIRoomEngine.
- Releases all resources occupied by the engine.
- Need to reacquire sharedInstance if used again after calling this.

```
// Objective-C Usage example:[TUIRoomEngine destroySharedInstance];// Swift Usage example:TUIRoomEngine.destroySharedInstance()
```

> **Note** Make sure all rooms have been exited before calling this method. All engine functionalities will become unavailable after calling this. Applies to both conference and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)) .

## loginWithSDKAppId:userId:userSig:onSuccess:onError:

**loginWithSDKAppId:userId:userSig:onSuccess:onError:**

| + (void)loginWithSDKAppId: | (NSInteger)sdkAppId |
| --- | --- |
| userId: | (NSString *)userId |
| userSig: | (NSString *)userSig |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### After creating a TUIRoomEngine instance, you should login with sdkAppId, userId and userSig then you can call TUIRoomEngine instance and other function.

Description:

- The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.
- If a user is kicked off while online, the SDK will notify you through the [onKickedOffLine](https://www.tencentcloud.com/document/product/647/54854#b0238d7b1fa86af2c540ec313dba8e6b) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

```
// Objective-C Usage example:[TUIRoomEngine loginWithSDKAppId:1400000001                           userId:@"user123"                          userSig:@"xxxxxx"                        onSuccess:^{                           // Login success handling                        }                          onError:^(int code, NSString *message) {                           // Login failure handling                       }];// Swift Usage example:TUIRoomEngine.login(sdkAppId: 1400000001,                      userId: "user123",                     userSig: "xxxxxx",                   onSuccess: {                          // Login success handling                    },                     onError: { code, message in                          // Login failure handling                  })
```

Parameters:

| Param | DESC |
| --- | --- |
| sdkAppId | It is Application ID. You can see the SDKAppId by creating an application in the TRTC [Console](https://console.trtc.io/). |
| userId | User ID, it is the unique identifier used by Tencent Cloud to distinguish users. |
| userSig | The user signature designed by Tencent Cloud based on the UserId, which is used to access Tencent Cloud services. More details, see [UserSig](https://trtc.io/document/35166). |

> **Note** You must call this interface to log in successfully before performing other operations. The userId under the same SDKAppId must be unique. userSig needs to be generated by your business server.

## logout:onError:

**logout:onError:**

| + (void)logout: | (TUISuccessBlock)onSuccess |
| --- | --- |
| onError: | (TUIErrorBlock)onError |

#### Log out of your account. If you are in the room, there will be active leaving room and destroying resource operations.

Description:

- Actively logs out of current login status.
- Releases all resources occupied by the engine.
- Automatically executes room leaving operation if currently in a room.
- Requires calling login interface again for subsequent usage.

```
// Objective-C Usage example:[TUIRoomEngine logout:^{ // Handle logout success} onError:^(int code, NSString *message) { // Handle logout failure}];// Swift Usage example:TUIRoomEngine.logout { // Handle logout success} onError: { code, message in // Handle logout failure}
```

Parameters:

| Param | DESC |
| --- | --- |
| onError | Callback for failed logout, including error code and message. |
| onSuccess | Callback for successful logout. |

> **Note** Ensure all necessary cleanup is completed before calling this method. All engine functionalities will become unavailable after calling this method. Applies to both meeting and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)). If logout fails due to network issues, recommend retrying or prompting user to check network.

## setSelfInfoWithUserName:avatarUrl:onSuccess:onError:

**setSelfInfoWithUserName:avatarUrl:onSuccess:onError:**

| + (void)setSelfInfoWithUserName: | (NSString *)userName |
| --- | --- |
| avatarUrl: | (NSString *)avatarURL |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Update user name and avatar for logged-in user.

Description:

- Sets local user's nickname and avatar URL.
- Modified information will be synchronized to other users in the room.
- Applies to both meeting and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

```
// Objective-C Usage example:[TUIRoomEngine setSelfInfoWithUserName:@"John"  avatarUrl:@"https://avatar.url"  onSuccess:^{ // Handle success }  onError:^(int code, NSString *message) { // Handle failure }];// Swift Usage example:TUIRoomEngine.setSelfInfo(userName: "John",  avatarUrl: "https://avatar.url", onSuccess: { // Handle success }, onError: { code, message in // Handle failure })
```

Parameters:

| Param | DESC |
| --- | --- |
| avatarURL | User avatar URL address. |
| onError | Callback for failed operation, including error code and message. |
| onSuccess | Callback for successful operation. |
| userName | User nickname. |

> **Note** Avatar URL must be a valid and accessible address. Nickname and avatar changes may take at least 10 minutes to sync to other users in the room.

## getSelfInfo

**getSelfInfo**

#### Return the basic information of the logged-in user, including nickname and avatar.

Description:

- Retrieves detailed information of currently logged-in user.
- Includes basic information like user ID, nickname, avatar URL.
- Applies to both meeting and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUILoginUserInfo](https://www.tencentcloud.com/document/product/647/64477#cd70be62de13ce83edd3fa01a1f67e89)).

Return Value:

- Returns TUILoginUserInfo object ([TUILoginUserInfo](https://www.tencentcloud.com/document/product/647/64477#cd70be62de13ce83edd3fa01a1f67e89)).

Usage Example:

```
// Objective-C Usage example:TUILoginUserInfo *userInfo = [TUIRoomEngine getSelfInfo];// Swift Usage example:let userInfo = TUIRoomEngine.getSelfInfo()
```

> **Note** Must be called after successful login, returns locally cached user information.

## setSelfInfo:onSuccess:onError:

**setSelfInfo:onSuccess:onError:**

| + (void)setSelfInfo: | ([TUILoginUserInfo](https://www.tencentcloud.com/document/product/647/64477#cd70be62de13ce83edd3fa01a1f67e89) *)userInfo |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Update user basic information for logged-in user.

Description:

- Sets basic information of currently logged-in user, including user ID, nickname, avatar URL etc.
- Modified information will be synchronized to other users in the room.
- Supports both meeting room type and live room type ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

```
// Objective-C Usage example:TUILoginUserInfo *userInfo = [[TUILoginUserInfo alloc] init];userInfo.userId = @"user123";userInfo.userName = @"John";userInfo.avatarUrl = @"https://avatar.url";[TUIRoomEngine setSelfInfo:userInfo  onSuccess:^{ // Handle success }  onError:^(int code, NSString *message) { // Handle failure }];// Swift Usage example:let userInfo = TUILoginUserInfo()userInfo.userId = "user123"userInfo.userName = "John"userInfo.avatarUrl = "https://avatar.url"TUIRoomEngine.setSelfInfo(userInfo: userInfo, onSuccess: { // Handle success }, onError: { code, message in // Handle failure })
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | Interface callback to notify success or failure of the operation. |
| userInfo | User information object ([TUILoginUserInfo](https://www.tencentcloud.com/document/product/647/64477#cd70be62de13ce83edd3fa01a1f67e89)). |

> **Note** Must be called after successful login. Avatar URL must be a valid and accessible address. Nickname and avatar changes may take at least 10 minutes to sync to other users in the room.

## addObserver:

**addObserver:**

| - (void)addObserver: | (id<[TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa)>)observer |
| --- | --- |

#### Set event observer.

Description:

- Registers an observer object to receive various event notifications in the room.
- Supports both meeting room type and live room type ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- Receives various event notifications through TUIRoomObserver (e.g., error codes, remote user joining, audio/video status parameters, etc.).

```
// Objective-C Usage example:TUIRoomEngine *engine = [TUIRoomEngine sharedInstance];[engine addObserver:self];// Swift Usage example:let engine = TUIRoomEngine.sharedInstance()engine.addObserver(self)
```

Parameters:

| Param | DESC |
| --- | --- |
| observer | Object instance conforming to TUIRoomObserver protocol. |

> **Note** Must be called before entering the room. The added observer object's lifecycle needs to be managed manually. Avoid adding the same observer repeatedly. Observer won't be automatically removed after leaving the room, must call removeObserver manually.

## removeObserver:

**removeObserver:**

| - (void)removeObserver: | (id<[TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa)>)observer |
| --- | --- |

#### Remove event observer.

Description:

- Unregisters a previously registered observer object to stop receiving various event notifications in the room.
- Supports both meeting room type and live room type ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

```
// Objective-C Usage example:TUIRoomEngine *engine = [TUIRoomEngine sharedInstance];[engine removeObserver:self];// Swift Usage example:let engine = TUIRoomEngine.sharedInstance()engine.removeObserver(self)
```

Parameters:

| Param | DESC |
| --- | --- |
| observer | The observer callback instance to be removed. |

> **Note** Removing non-existent observer may cause errors. Recommended to call this method before the observer object is destroyed.

## createRoom:onSuccess:onError:

**createRoom:onSuccess:onError:**

| - (void)createRoom: | ([TUIRoomInfo](https://www.tencentcloud.com/document/product/647/64477#db993979ddd9ad0c0ea59633fb49a507) *)roomInfo |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Create a room.

Description:

- Creates a new room supporting both conference and live streaming room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- Room creator automatically becomes the room owner.
- Requires room info parameters to initialize room settings.

```
// Objective-C Usage example:TUIRoomInfo *roomInfo = [[TUIRoomInfo alloc] init];roomInfo.roomId = @"room123";roomInfo.roomType = TUIRoomTypeConference;roomInfo.name = @"Conference Room";[[TUIRoomEngine sharedInstance] createRoom:roomInfo                                    onSuccess:^{    NSLog(@"Room created");}                                    onError:^(TUIError code, NSString * _Nonnull message) {    NSLog(@"Create failed: %@", message);}];// Swift Usage example:let roomInfo = TUIRoomInfo()roomInfo.roomId = "room123"roomInfo.roomType = .conferenceroomInfo.name = "Conference Room"TUIRoomEngine.sharedInstance().createRoom(roomInfo, onSuccess: {    print("Room created")}, onError: { code, message in    print("Create failed: \\(message)")})
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| roomInfo | Room information object used to initialize room settings. |

> **Note** Must call login method first before creating room. Different room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)/ [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)) affect feature availability. Creator automatically becomes room owner. Single user can only create one room at a time.

## destroyRoom:onError:

**destroyRoom:onError:**

| - (void)destroyRoom: | (TUISuccessBlock)onSuccess |
| --- | --- |
| onError: | (TUIErrorBlock)onError |

#### Dismiss the room.

Description:

- Dismisses the current room where the user is located.
- All members will be forcibly removed after room dismissal.
- Supports both conference and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] destroyRoom:^{    NSLog(@"Room dismissed successfully");} onError:^(TUIError code, NSString * _Nonnull message) {    NSLog(@"Failed to dismiss room: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().destroyRoom {    print("Room dismissed successfully")} onError: { code, message in    print("Failed to dismiss room: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |

> **Note** Only room owner can call this interface. After room dismissal, SDK will notify users in the room via [onRoomDismissed](https://www.tencentcloud.com/document/product/647/54854#e3741060867444c54121e60eb54f989c) callback in  [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa) . Ensure all room transactions are completed before calling this interface. Dismissed room cannot be recovered, a new room needs to be created for continued use.

## enterRoom:onSuccess:onError:

**enterRoom:onSuccess:onError:**

| - (void)enterRoom: | (NSString *)roomId |
| --- | --- |
| onSuccess: | (TUIRoomInfoBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Enter a room.

Description:

- This interface will be deprecated in future versions and is not recommended for use.
- For entering rooms, it is recommended to use either:

` 2.4 enterRoom(String roomId, TUIRoomDefine.RoomType roomType ` or ` 2.5 enterRoom(String roomId, TUIRoomDefine.RoomType roomType, TUIRoomDefine.EnterRoomOptions ` interface.

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] enterRoom:@"roomId123" onSuccess:^(TUIRoomInfo * _Nullable roomInfo) {    NSLog(@"Enter room successfully");} onError:^(TUIError code, NSString * _Nonnull message) {    NSLog(@"Failed to enter room: %@", message);}];// Swift ExampleTUIRoomEngine.sharedInstance().enterRoom("roomId123") { roomInfo in  print("Enter room successfully")} onError: { code, message in  print("Failed to enter room: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| roomId | Room ID. |

> **Note** Single device is limited to joining 1 room at the same time. If exceeded, the earliest joined room will be exited automatically. For same account logged in on multiple devices, only 1 device is allowed to join a conference room with the same ID. Other devices attempting to join will kick out the earlier joined device. After entering room, SDK will notify users in the room via [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54854#64bc4ce1b62e5a15de963ecfb9225e98) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## enterRoom:roomType:onSuccess:onError:

**enterRoom:roomType:onSuccess:onError:**

| - (void)enterRoom: | (NSString *)roomId |
| --- | --- |
| roomType: | ([TUIRoomType](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248))roomType |
| onSuccess: | (TUIRoomInfoBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Enter a room.

Description:

- Enter the specified room, supporting two room types: conference and live streaming ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] enterRoom:@"roomId123"                                 roomType:TUIRoomTypeConference                                onSuccess:^(TUIRoomInfo * _Nullable roomInfo) {    NSLog(@"Enter room successfully");} onError:^(TUIError code, NSString * _Nonnull message) {    NSLog(@"Failed to enter room: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().enterRoom("roomId123", roomType: .conference) { roomInfo in    print("Enter room successfully")} onError: { code, message in    print("Failed to enter room: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| roomId | Room ID, must be unique. |
| roomType | Room type (conference/live). |

> **Note** Single device is limited to joining 1 conference room or 3 live rooms simultaneously. If exceeded, the earliest joined room will be exited automatically. For same account logged in on multiple devices, only 1 device is allowed to join a conference room with the same ID. Other devices attempting to join will kick out the earlier joined device. After entering room, SDK will notify users in the room via [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54854#64bc4ce1b62e5a15de963ecfb9225e98) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## enterRoom:roomType:options:onSuccess:onError:

**enterRoom:roomType:options:onSuccess:onError:**

| - (void)enterRoom: | (NSString *)roomId |
| --- | --- |
| roomType: | ([TUIRoomType](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248))roomType |
| options: | ([TUIEnterRoomOptions](https://www.tencentcloud.com/document/product/647/64477#16f3cb3850bd70aecb0bd6f007955a13) *)options |
| onSuccess: | (TUIRoomInfoBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Enter a room.

Description:

- Enter the specified room, supporting two room types: conference and live streaming ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- Supports passing additional room entry parameters through options, such as room password etc.

```
// Objective-C Usage example:TUIEnterRoomOptions *options = [[TUIEnterRoomOptions alloc] init];options.password = @"***";[[TUIRoomEngine sharedInstance] enterRoom:@"roomId123"                                 roomType:TUIRoomTypeConference                                  options:options                                onSuccess:^(TUIRoomInfo * _Nullable roomInfo) {    NSLog(@"Enter room successfully");} onError:^(TUIError code, NSString * _Nonnull message) {    NSLog(@"Failed to enter room: %@", message);}];// Swift Usage example:let options = TUIEnterRoomOptions()options.password = "***"TUIRoomEngine.sharedInstance().enterRoom("roomId123",                                         roomType: .conference,                                          options: options) { roomInfo in    print("Enter room successfully")} onError: { code, message in    print("Failed to enter room: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| options | Room entry parameters, type is ([TUIEnterRoomOptions](https://www.tencentcloud.com/document/product/647/64477#16f3cb3850bd70aecb0bd6f007955a13)). |
| roomId | Room ID. |
| roomType | Room type. |

> **Note** Single device is limited to joining 1 conference room or 3 live rooms simultaneously. If exceeded, the earliest joined room will be exited automatically. For same account logged in on multiple devices, only 1 device is allowed to join a conference room with the same ID. Other devices attempting to join will kick out the earlier joined device. After entering room, SDK will notify users in the room via [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54854#64bc4ce1b62e5a15de963ecfb9225e98) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## exitRoom:onSuccess:onError:

**exitRoom:onSuccess:onError:**

| - (void)exitRoom: | (BOOL)syncWaiting |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Exit the room.

Description:

- Exit the current room.
- This function supports both conference and live streaming room types([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- All audio/video streams will automatically stop pushing after exiting.

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] exitRoom:YES onSuccess:^{    NSLog(@"Exit room successfully");} onError:^(TUIError code, NSString * _Nonnull message) {    NSLog(@"Failed to exit room: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().exitRoom(syncWaiting: true) {  print("Exit room successfully")} onError: { code, message in  print("Failed to exit room: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| syncWaiting | Whether to wait synchronously for the interface to return. |

> **Note** After leaving the room, the SDK will notify users in the room via [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/54854#16b0d80475c0d1f945024d5116074c66) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## fetchRoomInfo:onError:

**fetchRoomInfo:onError:**

| - (void)fetchRoomInfo: | (TUIRoomInfoBlock)onSuccess |
| --- | --- |
| onError: | (TUIErrorBlock)onError |

#### Fetch room information.

Description:

- Get detailed information of the current room, including room ID, room name, room type, etc.
- Supports both conference and live streaming room types([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] fetchRoomInfo:^(TUIRoomInfo * _Nullable roomInfo) {    NSLog(@"Get room info successfully: %@", roomInfo);} onError:^(TUIError code, NSString * _Nonnull message) {    NSLog(@"Failed to get room info: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().fetchRoomInfo { roomInfo in    print("Get room info successfully: \\(roomInfo)")} onError: { code, message in    print("Failed to get room info: \\(message)")}
```

Parameters:

- @param onSuccess(iOS) Callback when room info is successfully obtained, contains $TUIRoomInfo room information.
- @param onError(iOS) Failure callback (contains error code and message).
- @param callback(Android/Win) Interface callback to notify success or failure of the call, success returns $TUIRoomInfo room info, failure returns error code and message.

> **Note** Must be called after entering a room. Returned room info includes basic configuration and current status. Returns error if not currently in any room.

## fetchRoomInfo:roomType:onSuccess:onError:

**fetchRoomInfo:roomType:onSuccess:onError:**

| - (void)fetchRoomInfo: | (NSString*)roomId |
| --- | --- |
| roomType: | ([TUIRoomType](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248))roomType |
| onSuccess: | (TUIRoomInfoBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Fetch Specified Room Information.

Description:

- Retrieves detailed information of a specified room, including room ID, room name, room type, etc.
- Applicable to both conference and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] fetchRoomInfo:@"room123"                                      roomType:TUIRoomTypeConference                                    onSuccess:^(TUIRoomInfo *roomInfo) {    NSLog(@"Room info fetched successfully: %@", roomInfo);} onError:^(TUIError code, NSString *message) {    NSLog(@"Failed to fetch room info: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().fetchRoomInfo(roomId: "room123", roomType: .conference) { roomInfo in    print("Room info fetched successfully: \\(roomInfo)")} onError: { code, message in    print("Failed to fetch room info: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android) Interface callback to notify success or failure of the call, success returns $TUIRoomInfo room info, failure returns error code and message. |
| onError | (iOS) Failure callback, includes error code and message. |
| onSuccess | (iOS) Success callback, returns room information object. |
| roomId | Room ID to query. |
| roomType | Room type (conference/live). |

> **Note** Can be called before entering a room to query basic room information. Returned room info includes basic configuration and current status. Returns ROOM_ERROR_NOT_FOUND(1001) error if room doesn't exist.

## updateRoomNameByAdmin:onSuccess:onError:

**updateRoomNameByAdmin:onSuccess:onError:**

| - (void)updateRoomNameByAdmin: | (NSString *)roomName |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Update room name (only support for administrators or room owner).

Description:

- Modifies the name of the current room, applicable to both conference and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- After the room name is updated, the SDK notifies all users in the room via the [onRoomNameChanged](https://www.tencentcloud.com/document/product/647/54854#14f6f031aedb2aef37640bd8d52b512d) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] updateRoomNameByAdmin:@"New Room" onSuccess:^{  NSLog(@"Room name updated successfully");} onError:^(TUIError code, NSString *message) {  NSLog(@"Failed to update room name: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().updateRoomNameByAdmin("New Room") {    print("Room name updated successfully")} onError: { code, message in    print("Failed to update room name: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure returns error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| roomName | New room name. |

> **Note** Only administrators or room owners can call this interface. After successful modification, all users in the room will receive the [onRoomNameChanged](https://www.tencentcloud.com/document/product/647/54854#14f6f031aedb2aef37640bd8d52b512d) callback. Returns error code if room name contains illegal characters or exceeds length limit.

## updateRoomSeatModeByAdmin:onSuccess:onError:

**updateRoomSeatModeByAdmin:onSuccess:onError:**

| - (void)updateRoomSeatModeByAdmin: | ([TUISeatMode](https://www.tencentcloud.com/document/product/647/64477#6e6fdc219cc838c9e3c5d622ab32c8f1))seatMode |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Update room seat mode (only support for administrators or room owner).

Description:

- Modifies the seat management mode of the room, supporting both free-to-take and apply-to-take modes.
- Applicable to both conference and live room types ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) & [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- After seat mode is updated, the SDK notifies all users in the room via [onRoomSeatModeChanged](https://www.tencentcloud.com/document/product/647/54854#43c39ab0e5611de1f28bfe62e4e0077b) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] updateRoomSeatModeByAdmin:TUISeatModeApplyToTake onSuccess:^{  NSLog(@"Room seat mode updated successfully");} onError:^(TUIError code, NSString *message) {  NSLog(@"Failed to update room seat mode: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().updateRoomSeatModeByAdmin(.applyToTake) {    print("Room seat mode updated successfully")} onError: { code, message in    print("Failed to update room seat mode: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure returns error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| seatMode | Seat mode [TUISeatModeFreeToTake](https://www.tencentcloud.com/document/product/647/64477#6e6fdc219cc838c9e3c5d622ab32c8f1): Free-to-take mode, audience can take seat without application.[TUISeatModeApplyToTake](https://www.tencentcloud.com/document/product/647/64477#6e6fdc219cc838c9e3c5d622ab32c8f1): Apply-to-take mode, audience needs admin/owner approval to take seat. |

> **Note** Only administrators or room owners can call this interface. After mode change, all users in room will receive [onRoomSeatModeChanged](https://www.tencentcloud.com/document/product/647/54854#43c39ab0e5611de1f28bfe62e4e0077b) callback. Free-to-take mode suits interactive scenarios, apply-to-take mode suits scenarios requiring speaking control.

## updateRoomPasswordByAdmin:onSuccess:onError:

**updateRoomPasswordByAdmin:onSuccess:onError:**

| - (void)updateRoomPasswordByAdmin: | (NSString *)password |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Update room password (only support for administrators or room owner).

Description:

- Modifies the access password of the current room, applicable only to conference room type ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- After password update, new users joining the room will need to provide the new password.

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] updateRoomPasswordByAdmin:@"NewPassword" onSuccess:^{  NSLog(@"Room password updated successfully");} onError:^(TUIError code, NSString *message) {  NSLog(@"Failed to update room password: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().updateRoomPasswordByAdmin("NewPassword") {  print("Room password updated successfully")} onError: { code, message in  print("Failed to update room password: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android) Interface callback to notify success or failure of the call, failure returns error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| password | New room password, recommended length 8-16 characters, can include letters, numbers and special characters. |

> **Note** Only administrators or room owners can call this interface. Password change does not affect users already in the room. Conference room type ([TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)) only, not supported for live room type ([TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

## getRoomMetadata:onSuccess:onError:

**getRoomMetadata:onSuccess:onError:**

| - (void)getRoomMetadata: | (NSArray<NSString *> *)keys |
| --- | --- |
| onSuccess: | (TUIRoomMetadataResponseBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Get room metadata.

Description:

- Retrieves custom metadata key-value pairs of the room, which are set during room creation or by administrators.
- Only applicable to live room type ([TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).

```
// Objective-C Usage example:[[TUIRoomEngine sharedInstance] getRoomMetadata:@[@"key1", @"key2"] onSuccess:^(NSDictionary<NSString *,NSString *> *metadata) {  NSLog(@"Room metadata fetched successfully: %@", metadata);} onError:^(TUIError code, NSString *message) {  NSLog(@"Failed to fetch room metadata: %@", message);}];// Swift Usage example:TUIRoomEngine.sharedInstance().getRoomMetadata(["key1", "key2"]) { metadata in    print("Room metadata fetched successfully: \\(metadata)")} onError: { code, message in    print("Failed to fetch room metadata: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android)Interface callback to notify success or failure of the call, failure returns error code and message.Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| keys | List of metadata keys to query. Pass empty list to retrieve all metadata. |
| onError | (iOS) Failure callback, includes error code and message. |
| onSuccess | (iOS) Success callback, returns metadata dictionary. |

> **Note** Only live room type ([TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)) supports this feature. Returned metadata is in key-value pair format, with string values. User must be in the room to call this interface.

## setRoomMetadataByAdmin

**setRoomMetadataByAdmin**

#### Set room metadata, if the key already exists, update its value, if not, add the key.

Description:

- Sets or updates custom metadata key-value pairs for the room, applicable only to live room type ([TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)).
- If the specified key exists, its value will be updated; if not, a new key-value pair will be added.
- After metadata is updated, the SDK notifies all users in the room via [onRoomMetadataChanged](https://www.tencentcloud.com/document/product/647/54854#f3151fab3ff4a34eed91d740e05c9d5f) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

```
// Objective-C Usage example:NSDictionary *metadata = @{@"key1": @"value1", @"key2": @"value2"};[[TUIRoomEngine sharedInstance] setRoomMetadataByAdmin:metadata onSuccess:^{  NSLog(@"Room metadata updated successfully");} onError:^(TUIError code, NSString *message) {  NSLog(@"Failed to update room metadata: %@", message);}];// Swift Usage example:let metadata = ["key1": "value1", "key2": "value2"]TUIRoomEngine.sharedInstance().setRoomMetadataByAdmin(metadata) {    print("Room metadata updated successfully")} onError: { code, message in    print("Failed to update room metadata: \\(message)")}
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| metadata | Custom metadata key-value pairs to set, both keys and values must be strings |
| onError | (iOS) Failure callback (contains error code and message) |
| onSuccess | (iOS) Success callback |

> **Note** Only administrators or room owners can call this interface. After metadata update, all users in room will receive [onRoomMetadataChanged](https://www.tencentcloud.com/document/product/647/54854#f3151fab3ff4a34eed91d740e05c9d5f) callback. Key length cannot exceed 50 bytes, value length cannot exceed 200 bytes. Live room type ([TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248)) only.

## setLocalVideoView:

**setLocalVideoView:**

| - (void)setLocalVideoView: | (TUIVideoView *__nullable)view |
| --- | --- |

#### Set the local camera to preview the render view.

| Param | DESC |
| --- | --- |
| view | Render view. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## openLocalCamera:quality:onSuccess:onError:

**openLocalCamera:quality:onSuccess:onError:**

| - (void)openLocalCamera: | (BOOL)isFront |
| --- | --- |
| quality: | ([TUIVideoQuality](https://www.tencentcloud.com/document/product/647/64477#07c18674118c66b4e162b6000b4bafbf))quality |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Open the local camera.

| Param | DESC |
| --- | --- |
| isFront | YES: front NO: rear (only available on mobile OS). |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After opened the local camera in the room, the local video stream is published by default, and the SDK notifies the users in the room through the $onUserVideoStateChanged$ callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## closeLocalCamera

**closeLocalCamera**

#### Close the local camera.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After closed the local camera in the room, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54854#00c4eb2525cf2b404bb784d7731d95a8) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## startPushLocalVideo

**startPushLocalVideo**

#### Start publishing local video stream, default enabled.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After published the local video, if your local camera is opening, the SDK will notify users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54854#00c4eb2525cf2b404bb784d7731d95a8) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## stopPushLocalVideo

**stopPushLocalVideo**

#### Stop publishing local video stream.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After stopped published local video, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54854#00c4eb2525cf2b404bb784d7731d95a8) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## updateVideoQuality:

**updateVideoQuality:**

| - (void)updateVideoQuality: | ([TUIVideoQuality](https://www.tencentcloud.com/document/product/647/64477#07c18674118c66b4e162b6000b4bafbf))quality |
| --- | --- |

#### Update video encoding quality.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## updateVideoQualityEx:params:

**updateVideoQualityEx:params:**

| - (void)updateVideoQualityEx: | ([TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15))streamType |
| --- | --- |
| params: | ([TUIRoomVideoEncoderParams](https://www.tencentcloud.com/document/product/647/64477#5bcaee9b75f4315f349c03a8bc1eae3d) *)params |

#### Set the video encoding parameters.

| Param | DESC |
| --- | --- |
| params | Encoding parameters of the video. More details, see [TUIRoomVideoEncoderParams](https://www.tencentcloud.com/document/product/647/64477#5bcaee9b75f4315f349c03a8bc1eae3d). |
| streamType | The type of video stream. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15). |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## setVideoResolutionMode:resolutionMode:

**setVideoResolutionMode:resolutionMode:**

| - (void)setVideoResolutionMode: | ([TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15))streamType |
| --- | --- |
| resolutionMode: | ([TUIResolutionMode](https://www.tencentcloud.com/document/product/647/64477#281ffe18a1c82b67e026189153cadcd3))resolutionMode |

#### Set the video resolution mode (horizontal resolution or vertical resolution).

| Param | DESC |
| --- | --- |
| resolutionMode | Resolution mode. More details, see [TUIResolutionMode](https://www.tencentcloud.com/document/product/647/64477#281ffe18a1c82b67e026189153cadcd3). |
| streamType | The type of video stream. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15). |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## setLocalVideoMuteImage:

**setLocalVideoMuteImage:**

| - (void)setLocalVideoMuteImage: | (nullable TUIImage *)image |
| --- | --- |

#### Set the substitute image for local video during pause.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.Setting the placeholder image is only supported for streaming after calling stopPushLocalVideo; it is not supported after calling closeLocalCamera.@param image Substitute image.

## enableGravitySensor:

**enableGravitySensor:**

| - (void)enableGravitySensor: | (BOOL)enable |
| --- | --- |

#### Turn on gravity sensing mode. (only availble on mobile OS and the camera capture scene inside the SDK).

| Param | DESC |
| --- | --- |
| enable | YES: Open NO: Close. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After turning on gravity sensing, if the device on the collection end rotates, the images on the collection end and the audience will be rendered accordingly to ensure that the image in the field of view is always facing up.

## startScreenCaptureByReplaykit:

**startScreenCaptureByReplaykit:**

| - (void)startScreenCaptureByReplaykit: | (NSString *)appGroup |
| --- | --- |

#### Start screen sharing (only available on mobile OS).

After screen sharing started, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54854#00c4eb2525cf2b404bb784d7731d95a8) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## startScreenCapture:onSuccess:onError:

**startScreenCapture:onSuccess:onError:**

| - (void)startScreenCapture: | (TUIVideoView *)view |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Start screen sharing (only available on Mac OS).

| Param | DESC |
| --- | --- |
| view | The render view can be set a null value, it means not displaying the preview screen locally. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After screen sharing started, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54854#00c4eb2525cf2b404bb784d7731d95a8) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).The API can capture the screen content of the entire Mac OS, or capture and share the window content you select.

## stopScreenCapture

**stopScreenCapture**

#### Stop screen sharing.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After screen sharing ended, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54854#00c4eb2525cf2b404bb784d7731d95a8) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa) and also notifies you through the [onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/54854#f6bae569cb7519e87904a735c61605da) callback.

## getScreenCaptureSources

**getScreenCaptureSources**

#### Get the sharable screen and windows (only available on Mac OS)

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.The user can use the API to select the screen and window that can be shared. Through the API, you can query the ID, name, and thumbnail of the window that can be shared in the current system.

#### Return Desc:

The list of windows, including screens.

## selectScreenCaptureTarget:

**selectScreenCaptureTarget:**

| - (void)selectScreenCaptureTarget: | (NSString *)targetId |
| --- | --- |

#### Select the screen or windows to share (only available on Mac OS)

| Param | DESC |
| --- | --- |
| targetId | Selected sharing source. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After you obtain the screen and window that can be shared through getScreenCaptureSources, you can call the API to select the target screen or window.During the screen sharing, you can also call the API to change the sharing target.

## openLocalMicrophone:onSuccess:onError:

**openLocalMicrophone:onSuccess:onError:**

| - (void)openLocalMicrophone: | ([TUIAudioQuality](https://www.tencentcloud.com/document/product/647/64477#8a3a133f95f1c0d4e341943ffb7765b4))quality |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Open local microphone.

| Param | DESC |
| --- | --- |
| quality | Audio quality. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After opened the local microphone in a room, the SDK notifies users in the room through the [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54854#57eafbcdec43b9cacef68034b3087e45) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## closeLocalMicrophone

**closeLocalMicrophone**

#### Close the local microphone.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After closed the local microphone in the room, the SDK notifies the users in the room through the [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54854#57eafbcdec43b9cacef68034b3087e45) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## updateAudioQuality:

**updateAudioQuality:**

| - (void)updateAudioQuality: | ([TUIAudioQuality](https://www.tencentcloud.com/document/product/647/64477#8a3a133f95f1c0d4e341943ffb7765b4))quality |
| --- | --- |

#### Update audio encoding quality.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## muteLocalAudio

**muteLocalAudio**

#### Pause publishing the local audio stream.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.If you have opened your microphone and call the API to pause publishing the local audio stream, the SDK will notify the users in the room through the [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54854#57eafbcdec43b9cacef68034b3087e45) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## unmuteLocalAudio:onError:

**unmuteLocalAudio:onError:**

| - (void)unmuteLocalAudio: | (TUISuccessBlock)onSuccess |
| --- | --- |
| onError: | (TUIErrorBlock)onError |

#### Resume publishing the local audio stream.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.If you have opened your microphone and call the API to resume publishing the local audio stream, the SDK will notify the users in the room through the [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54854#57eafbcdec43b9cacef68034b3087e45) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## enableSystemAudioSharing:

**enableSystemAudioSharing:**

| - (void)enableSystemAudioSharing: | (BOOL)enable |
| --- | --- |

#### Enable system audio sharing

This API captures system audio data from your device and mixes it into the current audio stream of the SDK. This ensures that other users in the room hear the audio played back by the another app.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.Android: You need to use this interface to enable system sound capture first, and it will take effect only when you call startScreenCapture to enable screen sharing.

## setRemoteVideoView:streamType:view:

**setRemoteVideoView:streamType:view:**

| - (void)setRemoteVideoView: | (NSString *)userId |
| --- | --- |
| streamType: | ([TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15))streamType |
| view: | (TUIVideoView *__nullable)view |

#### Set the render view for remote user.

| Param | DESC |
| --- | --- |
| streamType | The type of video stream. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15). |
| userId | Remote user ID. |
| view | Render view. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## startPlayRemoteVideo:streamType:onPlaying:onLoading:onError:

**startPlayRemoteVideo:streamType:onPlaying:onLoading:onError:**

| - (void)startPlayRemoteVideo: | (NSString *)userId |
| --- | --- |
| streamType: | ([TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15))streamType |
| onPlaying: | (TUIPlayOnPlayingBlock)onPlaying |
| onLoading: | (TUIPlayOnLoadingBlock)onLoading |
| onError: | (TUIPlayOnErrorBlock)onError |

#### Start playing the remote user's video stream.

| Param | DESC |
| --- | --- |
| streamType | The type of video stream. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15). |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## stopPlayRemoteVideo:streamType:

**stopPlayRemoteVideo:streamType:**

| - (void)stopPlayRemoteVideo: | (NSString *)userId |
| --- | --- |
| streamType: | ([TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15))streamType |

#### Stop playing the remote user's video stream.

| Param | DESC |
| --- | --- |
| streamType | The type of video stream. More details, see [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64477#ca0c0e583eff1fbc8e326f6802b59f15). |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## muteRemoteAudioStream:isMute:

**muteRemoteAudioStream:isMute:**

| - (void)muteRemoteAudioStream: | (NSString *)userId |
| --- | --- |
| isMute: | (BOOL)isMute |

#### Mute the remote user's audio stream.

| Param | DESC |
| --- | --- |
| isMute | true: pause pulling remote user's audio stream, false: resume pulling remote user's audio stream. |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## getUserList:onSuccess:onError:

**getUserList:onSuccess:onError:**

| - (void)getUserList: | (NSInteger)nextSequence |
| --- | --- |
| onSuccess: | (TUIUserListResponseBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Get the list of user in the room.

| Param | DESC |
| --- | --- |
| nextSequence | Filling in 0 for the first request, if the returned data of the callback is not zero, paging is required, continue the operation until it is 0. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## getUserInfo:onSuccess:onError:

**getUserInfo:onSuccess:onError:**

| - (void)getUserInfo: | (NSString *)userId |
| --- | --- |
| onSuccess: | (TUIUserInfoBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Get user information.

| Param | DESC |
| --- | --- |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## changeUserRole:role:onSuccess:onError:

**changeUserRole:role:onSuccess:onError:**

| - (void)changeUserRole: | (NSString *)userId |
| --- | --- |
| role: | ([TUIRole](https://www.tencentcloud.com/document/product/647/64477#246382de7328bdcc5fe6680365be6234))role |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Change user role (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| role | User role. More details, see [TUIRole](https://www.tencentcloud.com/document/product/647/64477#246382de7328bdcc5fe6680365be6234). |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After the user role changed, the SDK will notify the users in the room through the [onUserInfoChanged](https://www.tencentcloud.com/document/product/647/54854#b5637d7d08d9811983db56c8dd28f051) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## changeUserNameCard:nameCard:onSuccess:onError:

**changeUserNameCard:nameCard:onSuccess:onError:**

| - (void)changeUserNameCard: | (NSString *)userId |
| --- | --- |
| nameCard: | (NSString *)nameCard |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Change user nickname in the room (only support to change all user for administrators or room owner, user can only change by self).

| Param | DESC |
| --- | --- |
| nameCard | User nickname to set, maximum support is 32 bytes |
| userId | User ID to change. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.After the user nickname changed, the SDK will notify the users in the room through the [onUserInfoChanged](https://www.tencentcloud.com/document/product/647/54854#b5637d7d08d9811983db56c8dd28f051) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## kickRemoteUserOutOfRoom:onSuccess:onError:

**kickRemoteUserOutOfRoom:onSuccess:onError:**

| - (void)kickRemoteUserOutOfRoom: | (NSString *)userId |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Kick the remote user out of the room (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After the remote user is kicked off from the room, the SDK notifies the kicked user through the [onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/54854#bbebfbd4e8b6c95b7852d1493f60bd4e) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa) and notifies users in the room through [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/54854#16b0d80475c0d1f945024d5116074c66).

## addCategoryTagForUsers:userList:onSuccess:onError:

**addCategoryTagForUsers:userList:onSuccess:onError:**

| - (void)addCategoryTagForUsers: | (NSInteger)tag |
| --- | --- |
| userList: | (NSArray<NSString *> *)userList |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Add a tag for the user (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| tag | Integer type, it is recommended that this value must be greater than or equal to 1000, you can customize it. |
| userList | User list. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.

## removeCategoryTagForUsers:userList:onSuccess:onError:

**removeCategoryTagForUsers:userList:onSuccess:onError:**

| - (void)removeCategoryTagForUsers: | (NSInteger)tag |
| --- | --- |
| userList: | (NSArray<NSString *> *)userList |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Remove tag for user (only support for room owner).

| Param | DESC |
| --- | --- |
| tag | Integer type, it is recommended that this value must be greater than or equal to 1000, you can customize it. |
| userList | User list. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.

## getUserListByTag:nextSequence:onSuccess:onError:

**getUserListByTag:nextSequence:onSuccess:onError:**

| - (void)getUserListByTag: | (NSInteger)tag |
| --- | --- |
| nextSequence: | (NSInteger)nextSequence |
| onSuccess: | (TUIUserListResponseBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Get user information in the room based on the tag.

| Param | DESC |
| --- | --- |
| nextSequence | Filling in 0 for the first request, if the returned data of the callback is not zero, paging is required, continue the operation until it is 0. |
| tag | Integer type, it is recommended that this value must be greater than or equal to 1000, you can customize it. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.

## setCustomInfoForUser:onSuccess:onError:

**setCustomInfoForUser:onSuccess:onError:**

| - (void)setCustomInfoForUser: | (NSString *)userId |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Set custom information for room users.

| Param | DESC |
| --- | --- |
| customInfo | Custom information. |
| userId | User userId. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.

## disableDeviceForAllUserByAdmin:isDisable:onSuccess:onError:

**disableDeviceForAllUserByAdmin:isDisable:onSuccess:onError:**

| - (void)disableDeviceForAllUserByAdmin: | ([TUIMediaDevice](https://www.tencentcloud.com/document/product/647/64477#c9316e85248cf88019d82c742fed3214))device |
| --- | --- |
| isDisable: | (BOOL)isDisable |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### The owner or administrator control that all users whether can open device. For example: all users are prohibited from opening the microphone(only available in the conference scenario).

| Param | DESC |
| --- | --- |
| device | Device. More details, see: [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/64477#c9316e85248cf88019d82c742fed3214). |
| isDisable | true: disable user to open device, false: enable user to open device. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.After the API call is successful:If the device type is MICROPHONE , the SDK will notify the users in the room through [onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/54854#3ec4485cdec9612c161c8a3211b2fb28) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).If the device type is CAMERA , the SDK will notify the users in the room through [onAllUserCameraDisableChanged](https://www.tencentcloud.com/document/product/647/54854#55a547bc323badf7599db85f13c6b286) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).If the device type is SCREEN_SHARING , the SDK will notify the users in the room through [onScreenShareForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54854#fe6861c09539278fb9440da696c4d028) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## openRemoteDeviceByAdmin:device:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:

**openRemoteDeviceByAdmin:device:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:**

| - (TUIRequest *)openRemoteDeviceByAdmin: | (NSString *)userId |
| --- | --- |
| device: | ([TUIMediaDevice](https://www.tencentcloud.com/document/product/647/64477#c9316e85248cf88019d82c742fed3214))device |
| timeout: | (NSTimeInterval)timeout |
| onAccepted: | (nullable TUIRequestAcceptedBlock)onAccepted |
| onRejected: | (nullable TUIRequestRejectedBlock)onRejected |
| onCancelled: | (nullable TUIRequestCancelledBlock)onCancelled |
| onTimeout: | (nullable TUIRequestTimeoutBlock)onTimeout |
| onError: | (nullable TUIRequestErrorBlock)onError |

#### Request the remote user to open the media device (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| device | Media device. More details, see: [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/64477#c9316e85248cf88019d82c742fed3214). |
| timeout | Timeout time, in seconds. If it is set to 0, the SDK will not execute timeout detection and will not trigger a timeout callback. |
| userId | User ID. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.After calling the API, the SDK will notify the requested user through [onRequestReceived](https://www.tencentcloud.com/document/product/647/54854#3697d1d038fd6f3ebe54ea33cd32e3df) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

#### Return Desc:

TUIRequest Request body.

## closeRemoteDeviceByAdmin:device:onSuccess:onError:

**closeRemoteDeviceByAdmin:device:onSuccess:onError:**

| - (void)closeRemoteDeviceByAdmin: | (NSString *)userId |
| --- | --- |
| device: | ([TUIMediaDevice](https://www.tencentcloud.com/document/product/647/64477#c9316e85248cf88019d82c742fed3214))device |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Close remote user media devices (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| device | Media device. More details, see: [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/64477#c9316e85248cf88019d82c742fed3214). |
| userId | User ID. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.After the API call is successful:If the device type is MICROPHONE, the SDK will notify the users in the room through [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54854#57eafbcdec43b9cacef68034b3087e45) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).If the device type is CAMERA or SCREEN_SHARING, the SDK will notify the users in the room through [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54854#00c4eb2525cf2b404bb784d7731d95a8) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## applyToAdminToOpenLocalDevice:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:

**applyToAdminToOpenLocalDevice:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:**

| - (TUIRequest *)applyToAdminToOpenLocalDevice: | ([TUIMediaDevice](https://www.tencentcloud.com/document/product/647/64477#c9316e85248cf88019d82c742fed3214))device |
| --- | --- |
| timeout: | (NSTimeInterval)timeout |
| onAccepted: | (nullable TUIRequestAcceptedBlock)onAccepted |
| onRejected: | (nullable TUIRequestRejectedBlock)onRejected |
| onCancelled: | (nullable TUIRequestCancelledBlock)onCancelled |
| onTimeout: | (nullable TUIRequestTimeoutBlock)onTimeout |
| onError: | (nullable TUIRequestErrorBlock)onError |

#### Apply to open the local media device (available to general users).

| Param | DESC |
| --- | --- |
| device | Media device. More details, see:[TUIMediaDevice](https://www.tencentcloud.com/document/product/647/64477#c9316e85248cf88019d82c742fed3214). |
| timeout | Timeout time, in seconds. If it is set to 0, the SDK will not execute timeout detection and will not trigger a timeout callback. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.After the API call is successful, the SDK will notify the requested user through [onRequestReceived](https://www.tencentcloud.com/document/product/647/54854#3697d1d038fd6f3ebe54ea33cd32e3df) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

#### Return Desc:

TUIRequest: Request body.

## getSeatList:onError:

**getSeatList:onError:**

| - (void)getSeatList: | (TUISeatListResponseBlock)onSuccess |
| --- | --- |
| onError: | (TUIErrorBlock)onError |

#### Get seat list.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## lockSeatByAdmin:lockMode:onSuccess:onError:

**lockSeatByAdmin:lockMode:onSuccess:onError:**

| - (void)lockSeatByAdmin: | (NSInteger)seatIndex |
| --- | --- |
| lockMode: | ([TUISeatLockParams](https://www.tencentcloud.com/document/product/647/64477#a2f6855e485bea12c8ab481e0522e3f4) *)lockParams |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Lock the seat (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| lockParams | Seat lock parameter. More details, see: $TUISeatLockParam$. |
| seatIndex | Seat index. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.If the lockParams is lockSeat, it means that the current seat can not be taken by all users and the user will be kicked off if the seat was taken.If the lockParams is lockVideo/lockAudio, it means that the current seat can not publish video/audio stream.

## takeSeat:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:

**takeSeat:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:**

| - (TUIRequest *)takeSeat: | (NSInteger)seatIndex |
| --- | --- |
| timeout: | (NSTimeInterval)timeout |
| onAccepted: | (TUIRequestAcceptedBlock)onAccepted |
| onRejected: | (TUIRequestRejectedBlock)onRejected |
| onCancelled: | (TUIRequestCancelledBlock)onCancelled |
| onTimeout: | (TUIRequestTimeoutBlock)onTimeout |
| onError: | (TUIRequestErrorBlock)onError |

#### Take the seat.

| Param | DESC |
| --- | --- |
| seatIndex | Seat index. If the seat is not enabled or the sequence of seats is not concerned, just fill in -1. |
| timeout | Timeout time, in seconds. If it is set to 0, the SDK will not execute timeout detection and will not trigger a timeout callback. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.The user can publish audio/video stream after taking the seat when isSeatEnable is true.After taking the seat successfully, the SDK will notify the users in the room through $onSeatListChanged$ in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).When the [TUISeatMode](https://www.tencentcloud.com/document/product/647/64477#6e6fdc219cc838c9e3c5d622ab32c8f1) is ApplyToTake, the operation to take seat need approval from the owner or administrator.When the [TUISeatMode](https://www.tencentcloud.com/document/product/647/64477#6e6fdc219cc838c9e3c5d622ab32c8f1) is FreeToTake, you can take seat freely.

#### Return Desc:

TUIRequest Request body.

## leaveSeat:onError:

**leaveSeat:onError:**

| - (void)leaveSeat: | (TUISuccessBlock)onSuccess |
| --- | --- |
| onError: | (TUIErrorBlock)onError |

#### Leave the seat.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.The user can not publish audio/video stream after leaving the seat when isSeatEnable is true.After leaving seat successfully, the SDK will notify the users in the room through [onSeatListChanged](https://www.tencentcloud.com/document/product/647/54854#31a13be6f374e28422eb363a518b235f) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## moveToSeat:onSuccess:onError:

**moveToSeat:onSuccess:onError:**

| - (void)moveToSeat: | (NSInteger)targetSeatIndex |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Move to seat.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After moving seat successfully, the SDK will notify the users in the room through [onSeatListChanged](https://www.tencentcloud.com/document/product/647/54854#31a13be6f374e28422eb363a518b235f) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## takeUserOnSeatByAdmin:userId:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:

**takeUserOnSeatByAdmin:userId:timeout:onAccepted:onRejected:onCancelled:onTimeout:onError:**

| - (TUIRequest *)takeUserOnSeatByAdmin: | (NSInteger)seatIndex |
| --- | --- |
| userId: | (NSString *)userId |
| timeout: | (NSTimeInterval)timeout |
| onAccepted: | (TUIRequestAcceptedBlock)onAccepted |
| onRejected: | (TUIRequestRejectedBlock)onRejected |
| onCancelled: | (TUIRequestCancelledBlock)onCancelled |
| onTimeout: | (TUIRequestTimeoutBlock)onTimeout |
| onError: | (TUIRequestErrorBlock)onError |

#### Invite user to take the seat (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| seatIndex | Seat index. |
| timeout | Timeout time, in seconds. If it is set to 0, the SDK will not execute timeout detection and will not trigger a timeout callback. |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After the API call is successful, the SDK will notify the invited user through [onRequestReceived](https://www.tencentcloud.com/document/product/647/54854#3697d1d038fd6f3ebe54ea33cd32e3df) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

#### Return Desc:

TUIRequest: Request body.

## kickUserOffSeatByAdmin:userId:onSuccess:onError:

**kickUserOffSeatByAdmin:userId:onSuccess:onError:**

| - (void)kickUserOffSeatByAdmin: | (NSInteger)seatIndex |
| --- | --- |
| userId: | (NSString *)userId |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Kick off the user from seat (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| seatIndex | Seat index. If the seat is not enabled and the sequence of seats is not concerned, just fill in -1. |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After the API call is successful, the SDK will notify the users in the room through [onSeatListChanged](https://www.tencentcloud.com/document/product/647/54854#31a13be6f374e28422eb363a518b235f) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## getSeatApplicationList:onError:

**getSeatApplicationList:onError:**

| - (void)getSeatApplicationList: | (TUIRequestListResponseBlock)onSuccess |
| --- | --- |
| onError: | (TUIErrorBlock)onError |

#### Get the request list of users who want to take the seat in the room (only support for administrators or room owner).

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## disableSendingMessageByAdmin:isDisable:onSuccess:onError:

**disableSendingMessageByAdmin:isDisable:onSuccess:onError:**

| - (void)disableSendingMessageByAdmin: | (NSString *)userId |
| --- | --- |
| isDisable: | (BOOL)isDisable |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Disable the ability of remote users to send messages (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to send message, false: enable user to send message. |
| userId | User ID. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After disabling the ability of remote users to send messages, the SDK notifies the disabled user through [onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/54854#d1f497f96f9523b0d284992b90b22d26) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## disableSendingMessageForAllUser:onSuccess:onError:

**disableSendingMessageForAllUser:onSuccess:onError:**

| - (void)disableSendingMessageForAllUser: | (BOOL)isDisable |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Disable the ability of all users to send messages (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| isDisable | true: disable all users to send message, false: enable all users to send message. |

> **Note**The function only supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.After disabling the ability of all users to send messages, the SDK notifies users in the room through [onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54854#b64a6a83036eb91c14d381c1feca555b) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).

## sendTextMessage:onSuccess:onError:

**sendTextMessage:onSuccess:onError:**

| - (void)sendTextMessage: | ([TUIRoomTextMessage](https://www.tencentcloud.com/document/product/647/64477#7e0dfeb925fa7e89ac4d1073c6e2a046) *)textMessage |
| --- | --- |
| onSuccess: | (TUISendTextMessageBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Send text message

| Param | DESC |
| --- | --- |
| onError | Error callback. |
| onSuccess | Success callback. |
| textMessage | Message object. |

## sendCustomMessage:onSuccess:onError:

**sendCustomMessage:onSuccess:onError:**

| - (void)sendCustomMessage: | ([TUIRoomCustomMessage](https://www.tencentcloud.com/document/product/647/64477#2dbc71d1c436a27bf13d15a5d22e01d1) *)customMessage |
| --- | --- |
| onSuccess: | (TUISendCustomMessageBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Send custom message

| Param | DESC |
| --- | --- |
| customMessage | Message object. |
| onError | Error callback. |
| onSuccess | Success callback. |

## cancelRequest:onSuccess:onError:

**cancelRequest:onSuccess:onError:**

| - (void)cancelRequest: | (NSString *)requestId |
| --- | --- |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Cancel request.

| Param | DESC |
| --- | --- |
| requestId | Request ID (get from the sent request). |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.After cancelling a request, the SDK will notify the requested user through [onRequestCancelled](https://www.tencentcloud.com/document/product/647/54854#92b334084d0e34a0a3d4507e02acb850) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54854#6768cb2b92f818315a7d2ac8774f72fa).The API can be used to cancel a request that has been sent.

## responseRemoteRequest:agree:onSuccess:onError:

**responseRemoteRequest:agree:onSuccess:onError:**

| - (void)responseRemoteRequest: | (NSString *)requestId |
| --- | --- |
| agree: | (BOOL)agree |
| onSuccess: | (TUISuccessBlock)onSuccess |
| onError: | (TUIErrorBlock)onError |

#### Response request.

| Param | DESC |
| --- | --- |
| agree | YES: Agree the request, NO: Reject the request. |
| requestId | Request ID (get from the sent request or notification of the OnRequestReceived event). |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.When received a request, you can use this API to reply the received request.

## getTRTCCloud

**getTRTCCloud**

#### Get the TRTC instance object.

## setBeautyLevel:beautyLevel:

**setBeautyLevel:beautyLevel:**

| - (void)setBeautyLevel: | (NSInteger)beautyStyle |
| --- | --- |
| beautyLevel: | (float)beautyLevel |

#### Set the beauty level.

| Param | DESC |
| --- | --- |
| beautyLevel | Beauty level, the value range is 0 - 9; 0 indicates to disable the filter, and 9 indicates the most obvious effect. |
| beautyStyle | Beauty style, the values ââare as follows:0: Smooth, the skin smoothing effect is more obvious;1: Natural, the skin smoothing effect is more natural, and more facial details are retained;2: Excellent, the skin smoothing effect is between smooth and natural, retaining more skin details than smooth, and the skin smoothing degree is higher than natural. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## setWhitenessLevel:

**setWhitenessLevel:**

| - (void)setWhitenessLevel: | (float)whitenessLevel |
| --- | --- |

#### Set whitening level.

| Param | DESC |
| --- | --- |
| whitenessLevel | Whitening level, ranging from 0 - 9; 0 indicates to disable the filter, and 9 indicates the most obvious effect. |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## getExtension:

**getExtension:**

| - (id) getExtension: | ([TUIExtensionType](https://www.tencentcloud.com/document/product/647/64475#9d4c7f4d7226087edd7da128249f1de7))extensionType |
| --- | --- |

#### Get the extension.

| Param | DESC |
| --- | --- |
| extensionType | Extension type. More deatils, see [TUIExtensionType](https://www.tencentcloud.com/document/product/647/64475#9d4c7f4d7226087edd7da128249f1de7). |

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## getMediaDeviceManager

**getMediaDeviceManager**

#### Get device management class.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.

## getLiveConnectionManager

**getLiveConnectionManager**

#### Get live-connection management class.

> **Note**The function supports the [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.

## getLiveBattleManager

**getLiveBattleManager**

#### Get live-battle management class.

> **Note**The function supports the [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room type.

## callExperimentalAPI:callback:

**callExperimentalAPI:callback:**

| - (id)callExperimentalAPI: | (NSString *)jsonStr |
| --- | --- |
| callback: | (TUIExperimentalAPIResponseBlock)callback |

#### Call experimental APIs.

> **Note**The function supports the [TUIRoomTypeConference](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) and [TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/64477#7f245d24537c126ff60fed533d974248) room types.


---
*Source: [https://trtc.io/document/54855](https://trtc.io/document/54855)*
