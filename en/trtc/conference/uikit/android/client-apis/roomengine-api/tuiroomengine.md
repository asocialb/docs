# TUIRoomEngine

Copyright (c) 2024 Tencent. All rights reserved.

Module:   TUIRoomEngine @ TUIKitEngine.

Function: TUIRoomEngine Main function APIs.

Version: 3.2

**TUIRoomEngine**

## TUIRoomEngine

| FuncList | DESC |
| --- | --- |
| [sharedInstance](https://www.tencentcloud.com/document/product/647/54864#16cf67c8716b1c79b762d19e4ab99008) | Create a TUIRoomEngine instance (singleton pattern). |
| [destroySharedInstance](https://www.tencentcloud.com/document/product/647/54864#56ce73cf1f0b6bf6492c81d308ec029d) | Destroy the TUIRoomEngine instance (singleton pattern). |
| [login](https://www.tencentcloud.com/document/product/647/54864#e91313128572e17f2397f7be8edd93cf) | After creating a TUIRoomEngine instance, you should login with sdkAppId, userId and userSig then you can call TUIRoomEngine instance and other function. |
| [logout](https://www.tencentcloud.com/document/product/647/54864#45756ace1ef6c82297eee3fac5cd8667) | Log out of your account. If you are in the room, there will be active leaving room and destroying resource operations. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54864#bc3705389df676bb8e8cb68942dd820f) | Update user name and avatar for logged-in user. |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/54864#946bae7d91f5073f8044633a79a3c227) | Return the basic information of the logged-in user, including nickname and avatar. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54864#effe69c548ae164bc3c1771de6706844) | Update user basic information for logged-in user. |
| [addObserver](https://www.tencentcloud.com/document/product/647/54864#aa9e2a751854badf8d300deef59680b9) | Set event observer. |
| [removeObserver](https://www.tencentcloud.com/document/product/647/54864#a66b02c83a4371533c8076e9715d13b8) | Remove event observer. |
| [createRoom](https://www.tencentcloud.com/document/product/647/54864#911bbef4c82371be741fa4c6c0693907) | Create a room. |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/54864#9141c0291abba473fe8daeb75e3e052c) | Dismiss the room. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54864#35fdf16804f2627fec75cdce28ffc6cc) | Enter a room. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54864#0b76c433d07df7aa3dfc9248c79d391e) | Enter a room. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54864#7d887cfe0029482a872a8bef2c90b29a) | Enter a room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/54864#380786b98d56b95daf683fa4d68af388) | Exit the room. |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/54864#592e4c141886cc8b8666cf8dfefc3a8f) | Fetch room information. |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/54864#3921f8c55dda7ecb9ae16ec0dcc7ac32) | Fetch Specified Room Information. |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/54864#d970bfb9100d587e0d008db312b5bc5b) | Update room name (only support for administrators or room owner). |
| [updateRoomSeatModeByAdmin](https://www.tencentcloud.com/document/product/647/54864#07121319d8ae42ebccb1761dcbe508a4) | Update room seat mode (only support for administrators or room owner). |
| [updateRoomPasswordByAdmin](https://www.tencentcloud.com/document/product/647/54864#cac0a265de041de6d6e57aa57d705ad6) | Update room password (only support for administrators or room owner). |
| [getRoomMetadata](https://www.tencentcloud.com/document/product/647/54864#4bf28fcd8a1146b0662779f3094a509e) | Get room metadata. |
| [setRoomMetadataByAdmin](https://www.tencentcloud.com/document/product/647/54864#e774ac4968fa3eef64f36571ae2afe42) | Set room metadata, if the key already exists, update its value, if not, add the key. |
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
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/54864#0e9b0f5598d305831ddb19ece07f1b91) | Open local microphone. |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/54864#f677ac0fc0aa1efcd27121054699bfdc) | Close the local microphone. |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/54864#778e31acbb656244cffdb4450ba0c156) | Update audio encoding quality. |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/54864#80693da4a3b18e07d92a802485f6334e) | Pause publishing the local audio stream. |
| [unmuteLocalAudio](https://www.tencentcloud.com/document/product/647/54864#2a622d95aa2f7305de666cbec7109d77) | Resume publishing the local audio stream. |
| [enableSystemAudioSharing](https://www.tencentcloud.com/document/product/647/54864#da0b9688d75cd77f51984e71566fab47) | Enable system audio sharing |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/54864#0e6f5fe07c0f268923e502a3a2be76c1) | Set the render view for remote user. |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54864#72d1726923e949d2c443dd96aa4deeca) | Start playing the remote user's video stream. |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54864#4d251840dd060f6ee45f3d41ad7a6c84) | Stop playing the remote user's video stream. |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/54864#2184de7077cf5dc9f3165329efbf43b5) | Mute the remote user's audio stream. |
| [getUserList](https://www.tencentcloud.com/document/product/647/54864#699fe77c2784c5d75f05078d5add27fb) | Get the list of user in the room. |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/54864#6cd5c36b39754b71ad5cce7bfd2ff4b4) | Get user information. |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/54864#f0cf468f4a2fa73a73f82e60329ae649) | Change user role (only support for administrators or room owner). |
| [changeUserNameCard](https://www.tencentcloud.com/document/product/647/54864#33b8996e2230421dfb1a9c3bc00ecdf7) | Change user nickname in the room (only support to change all user for administrators or room owner, user can only change by self). |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/54864#258101fd02fe373bb682f479d15fc059) | Kick the remote user out of the room (only support for administrators or room owner). |
| [addCategoryTagForUsers](https://www.tencentcloud.com/document/product/647/54864#a1345a3a776cab7c63c0e073b4885481) | Add a tag for the user (only support for administrators or room owner). |
| [removeCategoryTagForUsers](https://www.tencentcloud.com/document/product/647/54864#045a6dc44d38e0d1ac8e282cd1d1676e) | Remove tag for user (only support for room owner). |
| [getUserListByTag](https://www.tencentcloud.com/document/product/647/54864#c27be9df993987f57823fb7d0946722f) | Get user information in the room based on the tag. |
| [setCustomInfoForUser](https://www.tencentcloud.com/document/product/647/54864#f8c95b9ae30880404583b6786a3e4789) | Set custom information for room users. |
| [disableDeviceForAllUserByAdmin](https://www.tencentcloud.com/document/product/647/54864#1ecce7f3cdb7dbb6f35fbaa3cc741122) | The owner or administrator control that all users whether can open device. For example: all users are prohibited from opening the microphone(only available in the conference scenario). |
| [openRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54864#590f32d6fe85c2fc80c339937aac9cdc) | Request the remote user to open the media device (only support for administrators or room owner). |
| [closeRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54864#510e6569a496ebad2e04bde91326eb60) | Close remote user media devices (only support for administrators or room owner). |
| [applyToAdminToOpenLocalDevice](https://www.tencentcloud.com/document/product/647/54864#4d4e5f3bc13e611768a401b4c3db962f) | Apply to open the local media device (available to general users). |
| [getSeatList](https://www.tencentcloud.com/document/product/647/54864#7820648092d091e37560ce0593879fc7) | Get seat list. |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/54864#81044cd0b188305f7227e3863c0e482f) | Lock the seat (only support for administrators or room owner). |
| [takeSeat](https://www.tencentcloud.com/document/product/647/54864#6eee934af96d5538e066a543c637e0cd) | Take the seat. |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/54864#84e97d04aa3dc31eda5d6b1bdeb4c34d) | Leave the seat. |
| [moveToSeat](https://www.tencentcloud.com/document/product/647/54864#60d07dda176d554ffd84e0cf3e373262) | Move to seat. |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/54864#85fcac236a372109a330eb0c5e3f0a0b) | Invite user to take the seat (only support for administrators or room owner). |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/54864#f878dca93c7266e7a132485ba1a00c4d) | Kick off the user from seat (only support for administrators or room owner). |
| [getSeatApplicationList](https://www.tencentcloud.com/document/product/647/54864#54d31a649216d220311f8fcf8f905404) | Get the request list of users who want to take the seat in the room (only support for administrators or room owner). |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/54864#1a14651e5e06305956f7e8dd8c29b821) | Disable the ability of remote users to send messages (only support for administrators or room owner). |
| [disableSendingMessageForAllUser](https://www.tencentcloud.com/document/product/647/54864#5f4a70034d79062967c860559af11b21) | Disable the ability of all users to send messages (only support for administrators or room owner). |
| [sendTextMessage](https://www.tencentcloud.com/document/product/647/54864#b642e3d2cee3cacc9e7c6f47af571314) | Send text message |
| [sendCustomMessage](https://www.tencentcloud.com/document/product/647/54864#7d14723294200fd5aa0c3853884fc97f) | Send custom message |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/54864#3271224bcd640ef9a347492b18bed14b) | Cancel request. |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/54864#ca9c83c643f5bd6c26dd23ec34639660) | Response request. |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/54864#393689f458433968d8dcc9d91635d71b) | Get the TRTC instance object. |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/54864#356c9ac2d40d703ae8075ec6d99719b3) | Set the beauty level. |
| [setWhitenessLevel](https://www.tencentcloud.com/document/product/647/54864#7df1e01587684fba1d0a5766334703b3) | Set whitening level. |
| [getExtension](https://www.tencentcloud.com/document/product/647/54864#5ad5ce957d19bef36541d4eb11a1051e) | Get the extension. |
| [getMediaDeviceManager](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21) | Get device management class. |
| [getLiveConnectionManager](https://www.tencentcloud.com/document/product/647/54864#fe288b50da697505b5ab87a35bed950e) | Get live-connection management class. |
| [getLiveBattleManager](https://www.tencentcloud.com/document/product/647/54864#5d671512de7e22b0507211255a9c123f) | Get live-battle management class. |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/54864#781a86cef929d0e20b8721a3e17b3726) | Call experimental APIs. |

## sharedInstance

**sharedInstance**

#### Create a TUIRoomEngine instance (singleton pattern).

Description:

- Creates and returns the global shared instance of TUIRoomEngine (singleton pattern).
- Supports both conference and live room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- Using singleton pattern avoids duplicate engine instance creation and saves resources.

Return value:

- Returns the singleton instance pointer of TUIRoomEngine.

```
// Java Usage example:TUIRoomEngine engine = TUIRoomEngine.sharedInstance();
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
// Java Usage example:TUIRoomEngine.destroySharedInstance();
```

> **Note** Make sure all rooms have been exited before calling this method. All engine functionalities will become unavailable after calling this. Applies to both conference and live room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)) .

## login

**login**

| void login | (Context context |
| --- | --- |
|  | int sdkAppId |
|  | String userId |
|  | String userSig |
|  | TUIRoomDefine.ActionCallback callback) |

#### After creating a TUIRoomEngine instance, you should login with sdkAppId, userId and userSig then you can call TUIRoomEngine instance and other function.

Description:

- The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.
- If a user is kicked off while online, the SDK will notify you through the [onKickedOffLine](https://www.tencentcloud.com/document/product/647/54863#5dfa1251a6787bde3f2f1d1a4b1bab88) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

```
// Java Usage example:TUIRoomEngine.login(context, 1400000001, "user123", "xxxxxx",     new TUIRoomDefine.ActionCallback() {        @Override        public void onSuccess() {            // Login success handling         }        @Override        public void onError(int errorCode, String errorMessage) {            // Login failure handling         }    });
```

Parameters:

| Param | DESC |
| --- | --- |
| sdkAppId | It is Application ID. You can see the SDKAppId by creating an application in the TRTC [Console](https://console.trtc.io/). |
| userId | User ID, it is the unique identifier used by Tencent Cloud to distinguish users. |
| userSig | The user signature designed by Tencent Cloud based on the UserId, which is used to access Tencent Cloud services. More details, see [UserSig](https://trtc.io/document/35166). |

> **Note** You must call this interface to log in successfully before performing other operations. The userId under the same SDKAppId must be unique. userSig needs to be generated by your business server.

## logout

**logout**

| void logout | (TUIRoomDefine.ActionCallback callback) |
| --- | --- |

#### Log out of your account. If you are in the room, there will be active leaving room and destroying resource operations.

Description:

- Actively logs out of current login status.
- Releases all resources occupied by the engine.
- Automatically executes room leaving operation if currently in a room.
- Requires calling login interface again for subsequent usage.

```
// Java Usage example:TUIRoomEngine.logout(new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Handle logout success    }    @Override    public void onError(int errorCode, String errorMessage) {        // Handle logout failure    }});
```

Parameters:

| Param | DESC |
| --- | --- |
| onError | Callback for failed logout, including error code and message. |
| onSuccess | Callback for successful logout. |

> **Note** Ensure all necessary cleanup is completed before calling this method. All engine functionalities will become unavailable after calling this method. Applies to both meeting and live room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)). If logout fails due to network issues, recommend retrying or prompting user to check network.

## setSelfInfo

**setSelfInfo**

| void setSelfInfo | (String userName |
| --- | --- |
|  | String avatarURL |
|  | TUIRoomDefine.ActionCallback callback) |

#### Update user name and avatar for logged-in user.

Description:

- Sets local user's nickname and avatar URL.
- Modified information will be synchronized to other users in the room.
- Applies to both meeting and live room types (TUIRoomTypeConference & TUIRoomTypeLive).

```
// Java Usage example:TUIRoomEngine.setSelfInfo("John", "https://avatar.url",      new TUIRoomDefine.ActionCallback() {         @Override         public void onSuccess() {             // Handle success         }         @Override         public void onError(int errorCode, String errorMessage) {            // Handle failure         }     });
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
- Applies to both meeting and live room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LoginUserInfo](https://www.tencentcloud.com/document/product/647/64481#333b5318c06cefebacfabb6f0b753b76)).

Return Value:

- Returns TUILoginUserInfo object ([LoginUserInfo](https://www.tencentcloud.com/document/product/647/64481#333b5318c06cefebacfabb6f0b753b76)).

Usage Example:

```
// Java Usage example:TUIRoomDefine.LoginUserInfo userInfo = TUIRoomEngine.getSelfInfo();
```

> **Note** Must be called after successful login, returns locally cached user information.

## setSelfInfo

**setSelfInfo**

| void setSelfInfo | (TUIRoomDefine.[LoginUserInfo](https://www.tencentcloud.com/document/product/647/64481#333b5318c06cefebacfabb6f0b753b76) userInfo |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Update user basic information for logged-in user.

Description:

- Sets basic information of currently logged-in user, including user ID, nickname, avatar URL etc.
- Modified information will be synchronized to other users in the room.
- Supports both meeting room type and live room type ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).

```
// Java Usage example:TUIRoomDefine.LoginUserInfo userInfo = new TUIRoomDefine.LoginUserInfo();userInfo.userId = "user123";userInfo.userName = "John";userInfo.avatarUrl = "https://avatar.url";TUIRoomEngine.setSelfInfo(userInfo, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Handle success    }    @Override    public void onError(int errorCode, String errorMessage) {        // Handle logout failure    }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | Interface callback to notify success or failure of the operation. |
| userInfo | User information object ([LoginUserInfo](https://www.tencentcloud.com/document/product/647/64481#333b5318c06cefebacfabb6f0b753b76)). |

> **Note** Must be called after successful login. Avatar URL must be a valid and accessible address. Nickname and avatar changes may take at least 10 minutes to sync to other users in the room.

## addObserver

**addObserver**

| void addObserver | ([TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a) observer) |
| --- | --- |

#### Set event observer.

Description:

- Registers an observer object to receive various event notifications in the room.
- Supports both meeting room type and live room type ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- Receives various event notifications through TUIRoomObserver (e.g., error codes, remote user joining, audio/video status parameters, etc.).

```
// Java Usage example:TUIRoomEngine engine = TUIRoomEngine.sharedInstance();engine.addObserver(new TUIRoomObserver() {    @Override    public void onRemoteUserEnterRoom(String userId) {        // Handle user enter room events     }    @Override    public void onRemoteUserLeaveRoom(String userId) {        // Handle user exit room events    }    // Implement other callback methods...});
```

Parameters:

| Param | DESC |
| --- | --- |
| observer | Object instance conforming to TUIRoomObserver protocol. |

> **Note** Must be called before entering the room. The added observer object's lifecycle needs to be managed manually. Avoid adding the same observer repeatedly. Observer won't be automatically removed after leaving the room, must call removeObserver manually.

## removeObserver

**removeObserver**

| void removeObserver | ([TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a) observer) |
| --- | --- |

#### Remove event observer.

Description:

- Unregisters a previously registered observer object to stop receiving various event notifications in the room.
- Supports both meeting room type and live room type ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).

```
// Java Usage example:class MyRoomObserver implements TUIRoomObserver {    @Override    public void onRemoteUserEnterRoom(String userId) {        // Handle user enter room events     }    @Override    public void onRemoteUserLeaveRoom(String userId) {        // Handle user exit room events    }    // Implement other callback methods...}MyRoomObserver observer = new MyRoomObserver();TUIRoomEngine engine = TUIRoomEngine.sharedInstance();engine.addObserver(observer);// When observation is no longer neededengine.removeObserver(observer);
```

Parameters:

| Param | DESC |
| --- | --- |
| observer | The observer callback instance to be removed. |

> **Note** Removing non-existent observer may cause errors. Recommended to call this method before the observer object is destroyed.

## createRoom

**createRoom**

| void createRoom | (TUIRoomDefine.[RoomInfo](https://www.tencentcloud.com/document/product/647/54864#592e4c141886cc8b8666cf8dfefc3a8f) roomInfo |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Create a room.

Description:

- Creates a new room supporting both conference and live streaming room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- Room creator automatically becomes the room owner.
- Requires room info parameters to initialize room settings.

```
// Java Usage example:TUIRoomDefine.RoomInfo roomInfo = new TUIRoomDefine.RoomInfo();roomInfo.roomId = "room123";roomInfo.roomType = TUIRoomDefine.RoomType.CONFERENCE;roomInfo.name = "Conference Room";TUIRoomEngine.sharedInstance().createRoom(roomInfo, new TUIRoomDefine.ActionCallback() {  @Override  public void onSuccess() {    Log.d("TAG", "Room created");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Create failed: " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| roomInfo | Room information object used to initialize room settings. |

> **Note** Must call login method first before creating room. Different room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)/ [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)) affect feature availability. Creator automatically becomes room owner. Single user can only create one room at a time.

## destroyRoom

**destroyRoom**

| void destroyRoom | (TUIRoomDefine.ActionCallback callback) |
| --- | --- |

#### Dismiss the room.

Description:

- Dismisses the current room where the user is located.
- All members will be forcibly removed after room dismissal.
- Supports both conference and live room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).

```
// Java Usage example:TUIRoomEngine.sharedInstance().destroyRoom(new TUIRoomDefine.ActionCallback() {  @Override  public void onSuccess() {    Log.d("TAG", "Room dismissed successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to dismiss room: " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |

> **Note** Only room owner can call this interface. After room dismissal, SDK will notify users in the room via [onRoomDismissed](https://www.tencentcloud.com/document/product/647/54863#087189eff55afc545eaa7fc58eaa2622) callback in  [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a) . Ensure all room transactions are completed before calling this interface. Dismissed room cannot be recovered, a new room needs to be created for continued use.

## enterRoom

**enterRoom**

| void enterRoom | (String roomId |
| --- | --- |
|  | TUIRoomDefine.GetRoomInfoCallback callback) |

#### Enter a room.

Description:

- This interface will be deprecated in future versions and is not recommended for use.
- For entering rooms, it is recommended to use either:

` 2.4 enterRoom(String roomId, TUIRoomDefine.RoomType roomType ` or ` 2.5 enterRoom(String roomId, TUIRoomDefine.RoomType roomType, TUIRoomDefine.EnterRoomOptions ` interface.

```
// Java Usage example:TUIRoomEngine.sharedInstance().enterRoom("room123", new TUIRoomDefine.GetRoomInfoCallback() {  @Override  public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {    Log.d("TAG", "Enter room successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to enter room: " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| roomId | Room ID. |

> **Note** Single device is limited to joining 1 room at the same time. If exceeded, the earliest joined room will be exited automatically. For same account logged in on multiple devices, only 1 device is allowed to join a conference room with the same ID. Other devices attempting to join will kick out the earlier joined device. After entering room, SDK will notify users in the room via [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54863#823d44ecd328c1436a8d7e324c5654b1) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## enterRoom

**enterRoom**

| void enterRoom | (String roomId |
| --- | --- |
|  | TUIRoomDefine.[RoomType](https://www.tencentcloud.com/document/product/647/64481#2c5219ee9c5bec4ecd3d78c97c6a3dfc) roomType |
|  | TUIRoomDefine.GetRoomInfoCallback callback) |

#### Enter a room.

Description:

- Enter the specified room, supporting two room types: conference and live streaming ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).

```
TUIRoomEngine.sharedInstance().enterRoom("room123",        TUIRoomDefine.RoomType.CONFERENCE,        new TUIRoomDefine.GetRoomInfoCallback() {    @Override    public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {        Log.d("TAG", "Enter room successfully");    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        Log.e("TAG", "Failed to enter room: " + message);    }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| roomId | Room ID, must be unique. |
| roomType | Room type (conference/live). |

> **Note** Single device is limited to joining 1 conference room or 3 live rooms simultaneously. If exceeded, the earliest joined room will be exited automatically. For same account logged in on multiple devices, only 1 device is allowed to join a conference room with the same ID. Other devices attempting to join will kick out the earlier joined device. After entering room, SDK will notify users in the room via [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54863#823d44ecd328c1436a8d7e324c5654b1) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## enterRoom

**enterRoom**

| void enterRoom | (String roomId |
| --- | --- |
|  | TUIRoomDefine.[RoomType](https://www.tencentcloud.com/document/product/647/64481#2c5219ee9c5bec4ecd3d78c97c6a3dfc) roomType |
|  | TUIRoomDefine.[EnterRoomOptions](https://www.tencentcloud.com/document/product/647/64481#cfb4029060d688617dbafedfa6cee5f6) options |
|  | TUIRoomDefine.GetRoomInfoCallback callback) |

#### Enter a room.

Description:

- Enter the specified room, supporting two room types: conference and live streaming ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- Supports passing additional room entry parameters through options, such as room password etc.

```
// Java Usage example:TUIRoomDefine.EnterRoomOptions options = new TUIRoomDefine.EnterRoomOptions();options.password = "***";TUIRoomEngine.sharedInstance().enterRoom("room123",     TUIRoomDefine.RoomType.CONFERENCE,     options,    new TUIRoomDefine.GetRoomInfoCallback() {        @Override        public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {            Log.d("TAG", "Enter room successfully");        }        @Override        public void onError(TUICommonDefine.Error error, String message) {            Log.e("TAG", "Failed to enter room: " + message);        }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| options | Room entry parameters, type is ([TUIEnterRoomOptions](https://www.tencentcloud.com/document/product/647/64481#cfb4029060d688617dbafedfa6cee5f6)). |
| roomId | Room ID. |
| roomType | Room type. |

> **Note** Single device is limited to joining 1 conference room or 3 live rooms simultaneously. If exceeded, the earliest joined room will be exited automatically. For same account logged in on multiple devices, only 1 device is allowed to join a conference room with the same ID. Other devices attempting to join will kick out the earlier joined device. After entering room, SDK will notify users in the room via [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54863#823d44ecd328c1436a8d7e324c5654b1) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## exitRoom

**exitRoom**

| void exitRoom | (boolean syncWaiting |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Exit the room.

Description:

- Exit the current room.
- This function supports both conference and live streaming room types([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- All audio/video streams will automatically stop pushing after exiting.

```
// Java Usage example:TUIRoomEngine.sharedInstance().exitRoom(true, new TUIRoomDefine.ActionCallback() {  @Override  public void onSuccess() {    Log.d("TAG", "Exit room successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to exit room: " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| syncWaiting | Whether to wait synchronously for the interface to return. |

> **Note** After leaving the room, the SDK will notify users in the room via [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/54863#464debb75790e0f51f4d1690fa4e4450) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## fetchRoomInfo

**fetchRoomInfo**

| void fetchRoomInfo | (TUIRoomDefine.GetRoomInfoCallback callback) |
| --- | --- |

#### Fetch room information.

Description:

- Get detailed information of the current room, including room ID, room name, room type, etc.
- Supports both conference and live streaming room types([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).

```
// Java Usage example:TUIRoomEngine.sharedInstance().fetchRoomInfo(new TUIRoomDefine.GetRoomInfoCallback() {  @Override  public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {    Log.d("TAG", "Get room info successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to get room info: " + message);  }});
```

Parameters:

- @param onSuccess(iOS) Callback when room info is successfully obtained, contains $TUIRoomInfo room information.
- @param onError(iOS) Failure callback (contains error code and message).
- @param callback(Android/Win) Interface callback to notify success or failure of the call, success returns $TUIRoomInfo room info, failure returns error code and message.

> **Note** Must be called after entering a room. Returned room info includes basic configuration and current status. Returns error if not currently in any room.

## fetchRoomInfo

**fetchRoomInfo**

| void fetchRoomInfo | (String roomId |
| --- | --- |
|  | TUIRoomDefine.[RoomType](https://www.tencentcloud.com/document/product/647/64481#2c5219ee9c5bec4ecd3d78c97c6a3dfc) roomType |
|  | TUIRoomDefine.GetRoomInfoCallback callback) |

#### Fetch Specified Room Information.

Description:

- Retrieves detailed information of a specified room, including room ID, room name, room type, etc.
- Applicable to both conference and live room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).

```
// Java Usage example:TUIRoomEngine.sharedInstance().fetchRoomInfo("room123", TUIRoomDefine.RoomType.CONFERENCE, new TUIRoomDefine.GetRoomInfoCallback() {  @Override  public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {    Log.d("TAG", "Room info fetched successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to fetch room info: " + message);  }});
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

## updateRoomNameByAdmin

**updateRoomNameByAdmin**

| void updateRoomNameByAdmin | (String roomName |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Update room name (only support for administrators or room owner).

Description:

- Modifies the name of the current room, applicable to both conference and live room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- After the room name is updated, the SDK notifies all users in the room via the [onRoomNameChanged](https://www.tencentcloud.com/document/product/647/54863#97fc563cec36fcde1bb0bc1b212b5c4e) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

```
// Java Usage example:TUIRoomEngine.sharedInstance().updateRoomNameByAdmin("New Room", new TUIRoomDefine.ActionCallback() {  @Override  public void onSuccess() {    Log.d("TAG", "Room name updated successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to update room name: " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure returns error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| roomName | New room name. |

> **Note** Only administrators or room owners can call this interface. After successful modification, all users in the room will receive the [onRoomNameChanged](https://www.tencentcloud.com/document/product/647/54863#97fc563cec36fcde1bb0bc1b212b5c4e) callback. Returns error code if room name contains illegal characters or exceeds length limit.

## updateRoomSeatModeByAdmin

**updateRoomSeatModeByAdmin**

| void updateRoomSeatModeByAdmin | (TUIRoomDefine.[SeatMode](https://www.tencentcloud.com/document/product/647/54864#07121319d8ae42ebccb1761dcbe508a4) seatMode |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Update room seat mode (only support for administrators or room owner).

Description:

- Modifies the seat management mode of the room, supporting both free-to-take and apply-to-take modes.
- Applicable to both conference and live room types ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) & [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- After seat mode is updated, the SDK notifies all users in the room via [onRoomSeatModeChanged](https://www.tencentcloud.com/document/product/647/54863#dd614e13a79128f06065469914b9a797) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

```
// Java Usage example:TUIRoomEngine.sharedInstance().updateRoomSeatModeByAdmin(TUIRoomDefine.SeatMode.APPLY_TO_TAKE, new TUIRoomDefine.ActionCallback() {  @Override  public void onSuccess() {    Log.d("TAG", "Room seat mode updated successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to update room seat mode: " + error + ", " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android/Win) Interface callback to notify success or failure of the call, failure returns error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| seatMode | Seat mode [FREE_TO_TAKE](https://www.tencentcloud.com/document/product/647/64481#908781531506c53abbfa1db07153d7c1): Free-to-take mode, audience can take seat without application.[APPLY_TO_TAKE](https://www.tencentcloud.com/document/product/647/64481#908781531506c53abbfa1db07153d7c1): Apply-to-take mode, audience needs admin/owner approval to take seat. |

> **Note** Only administrators or room owners can call this interface. After mode change, all users in room will receive [onRoomSeatModeChanged](https://www.tencentcloud.com/document/product/647/54863#dd614e13a79128f06065469914b9a797) callback. Free-to-take mode suits interactive scenarios, apply-to-take mode suits scenarios requiring speaking control.

## updateRoomPasswordByAdmin

**updateRoomPasswordByAdmin**

| void updateRoomPasswordByAdmin | (String password |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Update room password (only support for administrators or room owner).

Description:

- Modifies the access password of the current room, applicable only to conference room type ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- After password update, new users joining the room will need to provide the new password.

```
// Java Usage example:TUIRoomEngine.sharedInstance().updateRoomPasswordByAdmin("NewPassword", new TUIRoomDefine.ActionCallback() {  @Override  public void onSuccess() {    Log.d("TAG", "Room password updated successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to update room password: " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android) Interface callback to notify success or failure of the call, failure returns error code and message. |
| onError | (iOS) Failure callback (contains error code and message). |
| onSuccess | (iOS) Success callback. |
| password | New room password, recommended length 8-16 characters, can include letters, numbers and special characters. |

> **Note** Only administrators or room owners can call this interface. Password change does not affect users already in the room. Conference room type ([CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)) only, not supported for live room type ([LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).

## getRoomMetadata

**getRoomMetadata**

| void getRoomMetadata | (List<String> keys |
| --- | --- |
|  | TUIRoomDefine.GetRoomMetadataCallback callback) |

#### Get room metadata.

Description:

- Retrieves custom metadata key-value pairs of the room, which are set during room creation or by administrators.
- Only applicable to live room type ([LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).

```
// Java Usage example:List<String> keys = Arrays.asList("key1", "key2");TUIRoomEngine.sharedInstance().getRoomMetadata(keys, new TUIRoomDefine.GetRoomMetadataCallback() {  @Override  public void onSuccess(HashMap<String, String> metadata) {    Log.d("TAG", "Room metadata fetched successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to fetch room metadata: " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android)Interface callback to notify success or failure of the call, failure returns error code and message.Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| keys | List of metadata keys to query. Pass empty list to retrieve all metadata. |
| onError | (iOS) Failure callback, includes error code and message. |
| onSuccess | (iOS) Success callback, returns metadata dictionary. |

> **Note** Only live room type ([LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)) supports this feature. Returned metadata is in key-value pair format, with string values. User must be in the room to call this interface.

## setRoomMetadataByAdmin

**setRoomMetadataByAdmin**

| void setRoomMetadataByAdmin | (HashMap<String, String> metadata |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Set room metadata, if the key already exists, update its value, if not, add the key.

Description:

- Sets or updates custom metadata key-value pairs for the room, applicable only to live room type ([LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)).
- If the specified key exists, its value will be updated; if not, a new key-value pair will be added.
- After metadata is updated, the SDK notifies all users in the room via [onRoomMetadataChanged](https://www.tencentcloud.com/document/product/647/54863#bcc8d33dab3ea6791703f3755bd5986b) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

```
// Java Usage example:HashMap<String, String> metadata = new HashMap<>();metadata.put("key1", "value1");metadata.put("key2", "value2");TUIRoomEngine.sharedInstance().setRoomMetadataByAdmin(metadata, new TUIRoomDefine.ActionCallback() {  @Override  public void onSuccess() {    Log.d("TAG", "Room metadata updated successfully");  }  @Override  public void onError(TUICommonDefine.Error error, String message) {    Log.e("TAG", "Failed to update room metadata: " + message);  }});
```

Parameters:

| Param | DESC |
| --- | --- |
| callback | (Android) Interface callback to notify success or failure of the call, failure callback contains error code and message. |
| metadata | Custom metadata key-value pairs to set, both keys and values must be strings |
| onError | (iOS) Failure callback (contains error code and message) |
| onSuccess | (iOS) Success callback |

> **Note** Only administrators or room owners can call this interface. After metadata update, all users in room will receive [onRoomMetadataChanged](https://www.tencentcloud.com/document/product/647/54863#bcc8d33dab3ea6791703f3755bd5986b) callback. Key length cannot exceed 50 bytes, value length cannot exceed 200 bytes. Live room type ([LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db)) only.

## setLocalVideoView

**setLocalVideoView**

| void setLocalVideoView | (TUIVideoView view) |
| --- | --- |

#### Set the local camera to preview the render view.

| Param | DESC |
| --- | --- |
| view | Render view. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## openLocalCamera

**openLocalCamera**

| void openLocalCamera | (boolean isFront |
| --- | --- |
|  | TUIRoomDefine.[VideoQuality](https://www.tencentcloud.com/document/product/647/54864#ea061bff081ab6fb25c9d23efbb659b3) quality |
|  | TUIRoomDefine.ActionCallback callback) |

#### Open the local camera.

| Param | DESC |
| --- | --- |
| isFront | true: front false: rear (only available on mobile OS). |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After opened the local camera in the room, the local video stream is published by default, and the SDK notifies the users in the room through the $onUserVideoStateChanged$ callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## closeLocalCamera

**closeLocalCamera**

#### Close the local camera.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After closed the local camera in the room, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54863#1b5f1be3b9eacef43456b28a335bde63) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## startPushLocalVideo

**startPushLocalVideo**

#### Start publishing local video stream, default enabled.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After published the local video, if your local camera is opening, the SDK will notify users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54863#1b5f1be3b9eacef43456b28a335bde63) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## stopPushLocalVideo

**stopPushLocalVideo**

#### Stop publishing local video stream.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After stopped published local video, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54863#1b5f1be3b9eacef43456b28a335bde63) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## updateVideoQuality

**updateVideoQuality**

| void updateVideoQuality | (TUIRoomDefine.[VideoQuality](https://www.tencentcloud.com/document/product/647/54864#ea061bff081ab6fb25c9d23efbb659b3) quality) |
| --- | --- |

#### Update video encoding quality.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## updateVideoQualityEx

**updateVideoQualityEx**

| void updateVideoQualityEx | (TUIRoomDefine.[VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0) streamType |
| --- | --- |
|  | TUIRoomDefine.[RoomVideoEncoderParams](https://www.tencentcloud.com/document/product/647/64481#36880da6ee46fd2fa7b3239d5cb8d097) params) |

#### Set the video encoding parameters.

| Param | DESC |
| --- | --- |
| params | Encoding parameters of the video. More details, see [RoomVideoEncoderParams](https://www.tencentcloud.com/document/product/647/64481#36880da6ee46fd2fa7b3239d5cb8d097). |
| streamType | The type of video stream. More details, see [VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0). |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## setVideoResolutionMode

**setVideoResolutionMode**

| void setVideoResolutionMode | (TUIRoomDefine.[VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0) streamType |
| --- | --- |
|  | TUIRoomDefine.[ResolutionMode](https://www.tencentcloud.com/document/product/647/54864#a995efd41a996d7c0b09a3efb5ff5df1) resolutionMode) |

#### Set the video resolution mode (horizontal resolution or vertical resolution).

| Param | DESC |
| --- | --- |
| resolutionMode | Resolution mode. More details, see [ResolutionMode](https://www.tencentcloud.com/document/product/647/54864#a995efd41a996d7c0b09a3efb5ff5df1). |
| streamType | The type of video stream. More details, see [VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0). |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## setLocalVideoMuteImage

**setLocalVideoMuteImage**

| void setLocalVideoMuteImage | (Bitmap image) |
| --- | --- |

#### Set the substitute image for local video during pause.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.Setting the placeholder image is only supported for streaming after calling stopPushLocalVideo; it is not supported after calling closeLocalCamera.@param image Substitute image.

## enableGravitySensor

**enableGravitySensor**

| void enableGravitySensor | (boolean enable) |
| --- | --- |

#### Turn on gravity sensing mode. (only availble on mobile OS and the camera capture scene inside the SDK).

| Param | DESC |
| --- | --- |
| enable | true: Open false: Close. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After turning on gravity sensing, if the device on the collection end rotates, the images on the collection end and the audience will be rendered accordingly to ensure that the image in the field of view is always facing up.

## startScreenSharing

**startScreenSharing**

#### Start screen sharing (only available on mobile OS).

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After screen sharing started, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54863#1b5f1be3b9eacef43456b28a335bde63) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## stopScreenSharing

**stopScreenSharing**

#### Stop screen sharing.

After screen sharing ended, the SDK notifies users in the room through the [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54863#1b5f1be3b9eacef43456b28a335bde63) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a) and also notifies you through the [onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/54863#bdd10647f4a557c8225bc897047ad3db) callback.

## openLocalMicrophone

**openLocalMicrophone**

| void openLocalMicrophone | (TUIRoomDefine.[AudioQuality](https://www.tencentcloud.com/document/product/647/54864#778e31acbb656244cffdb4450ba0c156) quality |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Open local microphone.

| Param | DESC |
| --- | --- |
| quality | Audio quality. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After opened the local microphone in a room, the SDK notifies users in the room through the [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54863#0d385087f48c9f2d85d650f492bacb9d) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## closeLocalMicrophone

**closeLocalMicrophone**

#### Close the local microphone.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After closed the local microphone in the room, the SDK notifies the users in the room through the [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54863#0d385087f48c9f2d85d650f492bacb9d) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## updateAudioQuality

**updateAudioQuality**

| void updateAudioQuality | (TUIRoomDefine.[AudioQuality](https://www.tencentcloud.com/document/product/647/54864#778e31acbb656244cffdb4450ba0c156) quality) |
| --- | --- |

#### Update audio encoding quality.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## muteLocalAudio

**muteLocalAudio**

#### Pause publishing the local audio stream.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.If you have opened your microphone and call the API to pause publishing the local audio stream, the SDK will notify the users in the room through the [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54863#0d385087f48c9f2d85d650f492bacb9d) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## unmuteLocalAudio

**unmuteLocalAudio**

| void unmuteLocalAudio | (TUIRoomDefine.ActionCallback callback) |
| --- | --- |

#### Resume publishing the local audio stream.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.If you have opened your microphone and call the API to resume publishing the local audio stream, the SDK will notify the users in the room through the [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54863#0d385087f48c9f2d85d650f492bacb9d) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## enableSystemAudioSharing

**enableSystemAudioSharing**

| void enableSystemAudioSharing | (boolean enable) |
| --- | --- |

#### Enable system audio sharing

This API captures system audio data from your device and mixes it into the current audio stream of the SDK. This ensures that other users in the room hear the audio played back by the another app.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.Android: You need to use this interface to enable system sound capture first, and it will take effect only when you call startScreenCapture to enable screen sharing.

## setRemoteVideoView

**setRemoteVideoView**

| void setRemoteVideoView | (String userId |
| --- | --- |
|  | TUIRoomDefine.[VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0) streamType |
|  | TUIVideoView view) |

#### Set the render view for remote user.

| Param | DESC |
| --- | --- |
| streamType | The type of video stream. More details, see [VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0). |
| userId | Remote user ID. |
| view | Render view. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## startPlayRemoteVideo

**startPlayRemoteVideo**

| void startPlayRemoteVideo | (String userId |
| --- | --- |
|  | TUIRoomDefine.[VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0) streamType |
|  | TUIRoomDefine.PlayCallback callback) |

#### Start playing the remote user's video stream.

| Param | DESC |
| --- | --- |
| streamType | The type of video stream. More details, see [VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0). |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## stopPlayRemoteVideo

**stopPlayRemoteVideo**

| void stopPlayRemoteVideo | (String userId |
| --- | --- |
|  | TUIRoomDefine.[VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0) streamType) |

#### Stop playing the remote user's video stream.

| Param | DESC |
| --- | --- |
| streamType | The type of video stream. More details, see [VideoStreamType](https://www.tencentcloud.com/document/product/647/64481#ea56a503f0706f2dc1d93ea018bddbe0). |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## muteRemoteAudioStream

**muteRemoteAudioStream**

| void muteRemoteAudioStream | (String userId |
| --- | --- |
|  | boolean isMute) |

#### Mute the remote user's audio stream.

| Param | DESC |
| --- | --- |
| isMute | true: pause pulling remote user's audio stream, false: resume pulling remote user's audio stream. |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## getUserList

**getUserList**

| void getUserList | (long nextSequence |
| --- | --- |
|  | TUIRoomDefine.GetUserListCallback callback) |

#### Get the list of user in the room.

| Param | DESC |
| --- | --- |
| nextSequence | Filling in 0 for the first request, if the returned data of the callback is not zero, paging is required, continue the operation until it is 0. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## getUserInfo

**getUserInfo**

| void getUserInfo | (String userId |
| --- | --- |
|  | TUIRoomDefine.GetUserInfoCallback callback) |

#### Get user information.

| Param | DESC |
| --- | --- |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## changeUserRole

**changeUserRole**

| void changeUserRole | (String userId |
| --- | --- |
|  | TUIRoomDefine.[Role](https://www.tencentcloud.com/document/product/647/54864#f0cf468f4a2fa73a73f82e60329ae649) role |
|  | TUIRoomDefine.ActionCallback callback) |

#### Change user role (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| role | User role. More details, see [Role](https://www.tencentcloud.com/document/product/647/54864#f0cf468f4a2fa73a73f82e60329ae649). |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After the user role changed, the SDK will notify the users in the room through the [onUserInfoChanged](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## changeUserNameCard

**changeUserNameCard**

| void changeUserNameCard | (String userId |
| --- | --- |
|  | String nameCard |
|  | TUIRoomDefine.ActionCallback callback) |

#### Change user nickname in the room (only support to change all user for administrators or room owner, user can only change by self).

| Param | DESC |
| --- | --- |
| nameCard | User nickname to set, maximum support is 32 bytes |
| userId | User ID to change. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.After the user nickname changed, the SDK will notify the users in the room through the [onUserInfoChanged](https://www.tencentcloud.com/document/product/647/54863#9df3bd61a4a7bfb3a508d114cbc99e7d) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## kickRemoteUserOutOfRoom

**kickRemoteUserOutOfRoom**

| void kickRemoteUserOutOfRoom | (String userId |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Kick the remote user out of the room (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After the remote user is kicked off from the room, the SDK notifies the kicked user through the [onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/54863#216fe07cfda9d5b3736e368c0eef69c2) callback in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a) and notifies users in the room through [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/54863#464debb75790e0f51f4d1690fa4e4450).

## addCategoryTagForUsers

**addCategoryTagForUsers**

| void addCategoryTagForUsers | (int tag |
| --- | --- |
|  | List<String> userList |
|  | TUIRoomDefine.ActionCallback callback) |

#### Add a tag for the user (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| tag | Integer type, it is recommended that this value must be greater than or equal to 1000, you can customize it. |
| userList | User list. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.

## removeCategoryTagForUsers

**removeCategoryTagForUsers**

| void removeCategoryTagForUsers | (int tag |
| --- | --- |
|  | List<String> userList |
|  | TUIRoomDefine.ActionCallback callback) |

#### Remove tag for user (only support for room owner).

| Param | DESC |
| --- | --- |
| tag | Integer type, it is recommended that this value must be greater than or equal to 1000, you can customize it. |
| userList | User list. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.

## getUserListByTag

**getUserListByTag**

| void getUserListByTag | (int tag |
| --- | --- |
|  | long nextSequence |
|  | TUIRoomDefine.GetUserListCallback callback) |

#### Get user information in the room based on the tag.

| Param | DESC |
| --- | --- |
| nextSequence | Filling in 0 for the first request, if the returned data of the callback is not zero, paging is required, continue the operation until it is 0. |
| tag | Integer type, it is recommended that this value must be greater than or equal to 1000, you can customize it. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.

## setCustomInfoForUser

**setCustomInfoForUser**

| void setCustomInfoForUser | (String userId |
| --- | --- |
|  | HashMap<String |
|  | byte[]> customInfo |
|  | TUIRoomDefine.ActionCallback callback) |

#### Set custom information for room users.

| Param | DESC |
| --- | --- |
| customInfo | Custom information. |
| userId | User userId. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.

## disableDeviceForAllUserByAdmin

**disableDeviceForAllUserByAdmin**

| void disableDeviceForAllUserByAdmin | (TUIRoomDefine.[MediaDevice](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21) device |
| --- | --- |
|  | boolean isDisable |
|  | TUIRoomDefine.ActionCallback callback) |

#### The owner or administrator control that all users whether can open device. For example: all users are prohibited from opening the microphone(only available in the conference scenario).

| Param | DESC |
| --- | --- |
| device | Device. More details, see: [MediaDevice](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21). |
| isDisable | true: disable user to open device, false: enable user to open device. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.After the API call is successful:If the device type is [MICROPHONE](https://www.tencentcloud.com/document/product/647/64480#726ca9fc63ac2f58472dd54daa6b022f) , the SDK will notify the users in the room through [onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/54863#15f469022d454f95f53372a83157fbbc) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).If the device type is [CAMERA](https://www.tencentcloud.com/document/product/647/64480#726ca9fc63ac2f58472dd54daa6b022f) , the SDK will notify the users in the room through [onAllUserCameraDisableChanged](https://www.tencentcloud.com/document/product/647/54863#6bc81e3152578d22f10f45780fa7cb77) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).If the device type is [SCREEN_SHARING](https://www.tencentcloud.com/document/product/647/64480#726ca9fc63ac2f58472dd54daa6b022f) , the SDK will notify the users in the room through [onScreenShareForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54863#d6f2fb6b5936b7313bf9e36aa75aef9d) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## openRemoteDeviceByAdmin

**openRemoteDeviceByAdmin**

| Request openRemoteDeviceByAdmin | (String userId |
| --- | --- |
|  | TUIRoomDefine.[MediaDevice](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21) device |
|  | int timeout |
|  | TUIRoomDefine.RequestCallback callback) |

#### Request the remote user to open the media device (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| device | Media device. More details, see: [MediaDevice](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21). |
| timeout | Timeout time, in seconds. If it is set to 0, the SDK will not execute timeout detection and will not trigger a timeout callback. |
| userId | User ID. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.After calling the API, the SDK will notify the requested user through [onRequestReceived](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

#### Return Desc:

TUIRequest Request body.

## closeRemoteDeviceByAdmin

**closeRemoteDeviceByAdmin**

| void closeRemoteDeviceByAdmin | (String userId |
| --- | --- |
|  | TUIRoomDefine.[MediaDevice](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21) device |
|  | TUIRoomDefine.ActionCallback callback) |

#### Close remote user media devices (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| device | Media device. More details, see: [MediaDevice](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21). |
| userId | User ID. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.After the API call is successful:If the device type is [MICROPHONE](https://www.tencentcloud.com/document/product/647/64480#726ca9fc63ac2f58472dd54daa6b022f), the SDK will notify the users in the room through [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54863#0d385087f48c9f2d85d650f492bacb9d) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).If the device type is [CAMERA](https://www.tencentcloud.com/document/product/647/64480#726ca9fc63ac2f58472dd54daa6b022f) or [SCREEN_SHARING](https://www.tencentcloud.com/document/product/647/64480#726ca9fc63ac2f58472dd54daa6b022f), the SDK will notify the users in the room through [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54863#1b5f1be3b9eacef43456b28a335bde63) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## applyToAdminToOpenLocalDevice

**applyToAdminToOpenLocalDevice**

| Request applyToAdminToOpenLocalDevice | (TUIRoomDefine.[MediaDevice](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21) device |
| --- | --- |
|  | int timeout |
|  | TUIRoomDefine.RequestCallback callback) |

#### Apply to open the local media device (available to general users).

| Param | DESC |
| --- | --- |
| device | Media device. More details, see:[MediaDevice](https://www.tencentcloud.com/document/product/647/54864#63940a3d4b6af78eee8e77087330ff21). |
| timeout | Timeout time, in seconds. If it is set to 0, the SDK will not execute timeout detection and will not trigger a timeout callback. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.After the API call is successful, the SDK will notify the requested user through [onRequestReceived](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

#### Return Desc:

TUIRequest: Request body.

## getSeatList

**getSeatList**

| void getSeatList | (TUIRoomDefine.GetSeatListCallback callback) |
| --- | --- |

#### Get seat list.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## lockSeatByAdmin

**lockSeatByAdmin**

| void lockSeatByAdmin | (int seatIndex |
| --- | --- |
|  | TUIRoomDefine.[SeatLockParams](https://www.tencentcloud.com/document/product/647/64481#80795bda03a58adbe30293d3de33b99c) lockParams |
|  | TUIRoomDefine.ActionCallback callback) |

#### Lock the seat (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| lockParams | Seat lock parameter. More details, see: $TUISeatLockParam$. |
| seatIndex | Seat index. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.If the lockParams is lockSeat, it means that the current seat can not be taken by all users and the user will be kicked off if the seat was taken.If the lockParams is lockVideo/lockAudio, it means that the current seat can not publish video/audio stream.

## takeSeat

**takeSeat**

| Request takeSeat | (int seatIndex |
| --- | --- |
|  | int timeout |
|  | TUIRoomDefine.RequestCallback callback) |

#### Take the seat.

| Param | DESC |
| --- | --- |
| seatIndex | Seat index. If the seat is not enabled or the sequence of seats is not concerned, just fill in -1. |
| timeout | Timeout time, in seconds. If it is set to 0, the SDK will not execute timeout detection and will not trigger a timeout callback. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.The user can publish audio/video stream after taking the seat when isSeatEnable is true.After taking the seat successfully, the SDK will notify the users in the room through $onSeatListChanged$ in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).When the [TUISeatMode](https://www.tencentcloud.com/document/product/647/64481#908781531506c53abbfa1db07153d7c1) is ApplyToTake, the operation to take seat need approval from the owner or administrator.When the [TUISeatMode](https://www.tencentcloud.com/document/product/647/64481#908781531506c53abbfa1db07153d7c1) is FreeToTake, you can take seat freely.

#### Return Desc:

TUIRequest Request body.

## leaveSeat

**leaveSeat**

| void leaveSeat | (TUIRoomDefine.ActionCallback callback) |
| --- | --- |

#### Leave the seat.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.The user can not publish audio/video stream after leaving the seat when isSeatEnable is true.After leaving seat successfully, the SDK will notify the users in the room through [onSeatListChanged](https://www.tencentcloud.com/document/product/647/54863#d544966ec2d49b6f777c2474c0ad0d91) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## moveToSeat

**moveToSeat**

| void moveToSeat | (int targetSeatIndex |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Move to seat.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After moving seat successfully, the SDK will notify the users in the room through [onSeatListChanged](https://www.tencentcloud.com/document/product/647/54863#d544966ec2d49b6f777c2474c0ad0d91) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## takeUserOnSeatByAdmin

**takeUserOnSeatByAdmin**

| Request takeUserOnSeatByAdmin | (int seatIndex |
| --- | --- |
|  | String userId |
|  | int timeout |
|  | TUIRoomDefine.RequestCallback callback) |

#### Invite user to take the seat (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| seatIndex | Seat index. |
| timeout | Timeout time, in seconds. If it is set to 0, the SDK will not execute timeout detection and will not trigger a timeout callback. |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After the API call is successful, the SDK will notify the invited user through [onRequestReceived](https://www.tencentcloud.com/document/product/647/54863#51c9deaee5b33b0ef9f6d5223880c667) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

#### Return Desc:

TUIRequest: Request body.

## kickUserOffSeatByAdmin

**kickUserOffSeatByAdmin**

| void kickUserOffSeatByAdmin | (int seatIndex |
| --- | --- |
|  | String userId |
|  | TUIRoomDefine.ActionCallback callback) |

#### Kick off the user from seat (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| seatIndex | Seat index. If the seat is not enabled and the sequence of seats is not concerned, just fill in -1. |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After the API call is successful, the SDK will notify the users in the room through [onSeatListChanged](https://www.tencentcloud.com/document/product/647/54863#d544966ec2d49b6f777c2474c0ad0d91) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## getSeatApplicationList

**getSeatApplicationList**

| void getSeatApplicationList | (TUIRoomDefine.RequestListCallback callback) |
| --- | --- |

#### Get the request list of users who want to take the seat in the room (only support for administrators or room owner).

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## disableSendingMessageByAdmin

**disableSendingMessageByAdmin**

| void disableSendingMessageByAdmin | (String userId |
| --- | --- |
|  | boolean isDisable |
|  | TUIRoomDefine.ActionCallback callback) |

#### Disable the ability of remote users to send messages (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| isDisable | true: disable user to send message, false: enable user to send message. |
| userId | User ID. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After disabling the ability of remote users to send messages, the SDK notifies the disabled user through [onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/54863#493bc419ce28818107f146e7f1563893) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## disableSendingMessageForAllUser

**disableSendingMessageForAllUser**

| void disableSendingMessageForAllUser | (boolean isDisable |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Disable the ability of all users to send messages (only support for administrators or room owner).

| Param | DESC |
| --- | --- |
| isDisable | true: disable all users to send message, false: enable all users to send message. |

> **Note**The function only supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.After disabling the ability of all users to send messages, the SDK notifies users in the room through [onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54863#8d2f050ec369f72915aa26991c04399b) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).

## sendTextMessage

**sendTextMessage**

| void sendTextMessage | (TUIRoomDefine.[RoomTextMessage](https://www.tencentcloud.com/document/product/647/64481#689abfd294b9f06b1438a1b3f71b0bbf) textMessage |
| --- | --- |
|  | TUIRoomDefine.SendTextMessageCallback callback) |

#### Send text message

| Param | DESC |
| --- | --- |
| callback | Callback. |
| textMessage | Message object. |

## sendCustomMessage

**sendCustomMessage**

| void sendCustomMessage | (TUIRoomDefine.[RoomCustomMessage](https://www.tencentcloud.com/document/product/647/64481#144f8c845a241d5f390c8ff49ea33ee1) customMessage |
| --- | --- |
|  | TUIRoomDefine.SendCustomMessageCallback callback) |

#### Send custom message

| Param | DESC |
| --- | --- |
| callback | Callback. |
| customMessage | Message object. |

## cancelRequest

**cancelRequest**

| void cancelRequest | (String requestId |
| --- | --- |
|  | TUIRoomDefine.ActionCallback callback) |

#### Cancel request.

| Param | DESC |
| --- | --- |
| requestId | Request ID (get from the sent request). |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.After cancelling a request, the SDK will notify the requested user through [onRequestCancelled](https://www.tencentcloud.com/document/product/647/54863#635b121d6722a2a7c7a69bcf1bc4981a) in [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#813244772a459c655a423eec84ae8f9a).The API can be used to cancel a request that has been sent.

## responseRemoteRequest

**responseRemoteRequest**

| void responseRemoteRequest | (String requestId |
| --- | --- |
|  | boolean agree |
|  | TUIRoomDefine.ActionCallback callback) |

#### Response request.

| Param | DESC |
| --- | --- |
| agree | YES: Agree the request, NO: Reject the request. |
| requestId | Request ID (get from the sent request or notification of the OnRequestReceived event). |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.When received a request, you can use this API to reply the received request.

## getTRTCCloud

**getTRTCCloud**

#### Get the TRTC instance object.

## setBeautyLevel

**setBeautyLevel**

| void setBeautyLevel | (int beautyStyle |
| --- | --- |
|  | float beautyLevel) |

#### Set the beauty level.

| Param | DESC |
| --- | --- |
| beautyLevel | Beauty level, the value range is 0 - 9; 0 indicates to disable the filter, and 9 indicates the most obvious effect. |
| beautyStyle | Beauty style, the values ââare as follows:0: Smooth, the skin smoothing effect is more obvious;1: Natural, the skin smoothing effect is more natural, and more facial details are retained;2: Excellent, the skin smoothing effect is between smooth and natural, retaining more skin details than smooth, and the skin smoothing degree is higher than natural. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## setWhitenessLevel

**setWhitenessLevel**

| void setWhitenessLevel | (float whitenessLevel) |
| --- | --- |

#### Set whitening level.

| Param | DESC |
| --- | --- |
| whitenessLevel | Whitening level, ranging from 0 - 9; 0 indicates to disable the filter, and 9 indicates the most obvious effect. |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## getExtension

**getExtension**

| Object getExtension | (TUICommonDefine.[ExtensionType](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) extensionType) |
| --- | --- |

#### Get the extension.

| Param | DESC |
| --- | --- |
| extensionType | Extension type. More deatils, see [TUIExtensionType](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db). |

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## getMediaDeviceManager

**getMediaDeviceManager**

#### Get device management class.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.

## getLiveConnectionManager

**getLiveConnectionManager**

#### Get live-connection management class.

> **Note**The function supports the [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.

## getLiveBattleManager

**getLiveBattleManager**

#### Get live-battle management class.

> **Note**The function supports the [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room type.

## callExperimentalAPI

**callExperimentalAPI**

| Object callExperimentalAPI | (String jsonStr |
| --- | --- |
|  | TUIRoomDefine.ExperimentalAPIResponseCallback callback) |

#### Call experimental APIs.

> **Note**The function supports the [CONFERENCE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) and [LIVE](https://www.tencentcloud.com/document/product/647/64480#16f14b26fa9a9f11bc07ef5be5db48db) room types.


---
*Source: [https://trtc.io/document/54864](https://trtc.io/document/54864)*
