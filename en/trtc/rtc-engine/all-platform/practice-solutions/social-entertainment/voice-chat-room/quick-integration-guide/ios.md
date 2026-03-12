# iOS

## Business Process

This document summarizes some common business processes in voice chat rooms to help you better understand the entire scenario implementation process.

Room Management Process

Room Owner Seat Management Process

Audience Seat Management Process

The following figure shows the room management process, including the creation, joining, exiting, and dissolvement of rooms.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb2bcd718f0411f0814e525400bf7822.png)

The following figure shows the room owner seat management process, including inviting a listener to speak, removing a speaker, and muting a seat.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb5532488f0411f084bd5254007c27c5.png)

The following figure shows the audience seat management process, including becoming a speaker, become a listener, and moving a seat.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb46a64e8f0411f088af5254005ef0f7.png)

## Integration Preparation

### Step 1. Activating the Services

The voice chat room scenario typically depends on 2 paid PaaS services for construction, [Chat](https://trtc.io/products/chat) and [RTC Engine](https://trtc.io/products/rtc).

1. First, log in to the [Console](https://console.trtc.io/) to create applications, wherein one is an RTC Engine application, and the other one is a Chat application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb32d8bc8f0411f084bd5254007c27c5.png)

> **Note:**It's recommended to create 2 separate applications for testing environment and production environment respectively. Each account (UIN) is given 10,000 free minutes monthly for one year.RTC Engine monthly packages are divided into Trial Edition (default), Lite Edition, Standard Edition, and Professional Edition, unlocking different value-added features and services. For details, see [Version Features and Monthly Package Description](https://trtc.io/document/67650?product=pricing).

2. After creating the application, you can see its basic information in the Application Management - Application Overview section. It is important to keep the **SDKAppID** and **SDKSecretKey** safe for later use and to avoid key leakage that could lead to traffic theft.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb4c73188f0411f0974b52540044a08e.png)

### Step 2: Importing the SDK

The RTC Engine SDK and the Chat SDK have been published to CocoaPods. You can integrate SDKs through CocoaPods.

1. Install CocoaPods.

Enter the following command in a terminal window (you need to install Ruby on your Mac first):

```
sudo gem install cocoapods
```

2. Create a Podfile.

Go to the project directory, and enter the following command. A Podfile file will then be created in the project directory.

```
pod init
```

3. Edit the Podfile.

Choose the appropriate version for your project and edit the Podfile.

```
platform :ios, '8.0'target 'App' do    # TRTC Lite Edition    # Installation package minimum incremental size, only supports RTC Engine and live streaming player (TXLivePlayer) two features.    pod 'TXLiteAVSDK_TRTC', :podspec => 'https://liteav.sdk.qcloud.com/pod/liteavsdkspec/TXLiteAVSDK_TRTC.podspec'        # Add the Chat SDK    pod 'TXIMSDK_Plus_iOS'    # pod 'TXIMSDK_Plus_iOS_XCFramework'    # pod 'TXIMSDK_Plus_Swift_iOS_XCFramework'        # If you need to add the Quic plugin, please uncomment the next line.    # Note: This plugin must be used with the Objective-C edition or XCFramework edition of the Chat SDK, and the plugin version number must match the Chat SDK version number.    # pod 'TXIMSDK_Plus_QuicPlugin'end
```

4. Update and install the SDK.

Enter the following command in a terminal window to update the local repository files and install the SDK.

```
pod install
```

Or use the following command to update the local repository.

```
pod update
```

Upon the completion of pod command execution, an .xcworkspace project file integrated with the SDK will be generated. Double-click to open it.

> **Note:**If the pod search fails, it is recommended to try updating the local repo cache of pod. The update command is as follows.pod setuppod repo updaterm ~/Library/Caches/CocoaPods/search_index.jsonExcept CocoaPods integration, you can also choose to download SDKs and manually import them. For details, see [Manual Integration of the RTC Engine SDK](https://trtc.io/document/62045?product=rtcengine&menulabel=core%20sdk&platform=android#31b6b3f0-5363-44b1-95a0-dbabe648e9df) and [Manual Integration of the Chat SDK](https://trtc.io/document/34306?product=chat&menulabel=core%20sdk&platform=android#96b656a2-61f9-4b6b-9240-38b28a86057a).Quic plugin, offering axp-Quic multiplexing protocol with better resistance to poor networks, can still offer services under 70% packet loss rate. It's only applicable to Professional Edition, Professional Edition plus, and Enterprise Edition users. [Purchase Pro Edition, Pro plus Edition , or Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use. To ensure normal usage of features, update the Chat SDK to version 7.7.5282 or later.

### Step 3: Project Configuration

1. For voice chat scenarios, the RTC Engine SDK and the Chat SDK need App authorization for microphone permissions. Add the following content to the App's Info.plist corresponding to the microphone prompts in the system pop-up authorization dialog box:

```
Privacy - Microphone Usage Description. Also enter a prompt specifying the purpose of microphone use.
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb36ea228f0411f0b321525400e889b2.png)

2. To allow the App to continue running certain features in the backend, select the current project in Xcode, set the setting item Background Modes to ON under Capabilities, and check **Audio, AirPlay and Picture in Picture**, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb390dd58f0411f0974b52540044a08e.png)

## Integration Process

### Step 1: Generate Authentication Credentials

UserSig is a security protection signature designed by Tencent for real-time communication services to prevent attackers from stealing your right of using cloud services. RTC Engine and Chat services adopt this security protection mechanism, with RTC Engine performing authentication during room entry and Chat performing authentication during login.

- Debugging Stage: UserSig can be generated through two methods for debugging and testing purposes only: [client sample code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk&platform=android) and [console access](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk&platform=android#console).
- Formal Operation Stage: It is recommended to use a higher security level server computation for generating UserSig. This is to prevent key leakage due to client reverse engineering.

The specific implementation process is as follows:

1. Before calling the SDK's initialization function, your app must first request UserSig from your server.
2. Your server computes the UserSig based on the SDKAppID and UserID.
3. The server returns the computed UserSig to your app.
4. Your app passes the obtained UserSig into the SDK through a specific API.
5. The SDK submits the SDKAppID + UserID + UserSig to Tencent Cloud CVM for verification.
6. Tencent Cloud verifies the UserSig and confirms its validity.
7. After the verification passes, the Chat SDK will be provided with instant messging services, and the RTC Engine SDK will be provided with TRTC services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb2d166b8f0411f0ae9d5254001c06ec.jpeg)

> **Note:**The local computation method of UserSig during the debugging stage is not recommended for application in an online environment. It is prone to reverse engineering, leading to key leakage.We provide UserSig server-side computation source code in multiple languages (Java/Go/PHP/Nodejs/Python/C#/C++). For details, see [Server-Side Calculation of UserSig](https://trtc.io/document/34580?product=chat&menulabel=uikit&platform=react#.E7.AD.BE.E5.90.8D.EF.BC.88usersig.EF.BC.89.E7.94.9F.E6.88.90.E5.B7.A5.E5.85.B7).

### Step 2: Initialization and Listening

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb3c2e018f0411f0b321525400e889b2.svg)

1. Initialize the Chat SDK and add an event listener.

```
// Obtain the SDKAppID from the Chat console.// Add an event listener for V2TIMSDKListener, where self is the implementation class of id<V2TIMSDKListener>. If you don't need to listen to Chat SDK events, this step can be skipped.[[V2TIMManager sharedInstance] addIMSDKListener:self];// Initialize the Chat SDK. After calling this API, you can immediately call the login API.[[V2TIMManager sharedInstance] initSDK:sdkAppID config:config];// After the SDK is initialized, it will trigger various events, such as connection status and expiration of log-in credentials.- (void)onConnecting {    NSLog(@"Chat SDK is connecting to the Tencent cloud server");}- (void)onConnectSuccess {    NSLog(@"Chat SDK has successfully connected to Tencent CVM");}// Remove event listener.// self is the implementation class of id <V2TIMSDKListener>.[[V2TIMManager sharedInstance] removeIMSDKListener:self];// Deinitialize the SDK.[[V2TIMManager sharedInstance] unInitSDK];
```

> **Note:**If your application's lifecycle is consistent with the SDK's lifecycle, you do not need to deinitialize before exiting the application. If you only initialize the SDK after entering a specific interface and no longer use it after exiting, you may deinitialize the SDK.

2. Create an RTC Engine SDK instance and set an event listener.

```
// Create an RTC Engine SDK instance (singleton mode)_trtcCloud = [TRTCCloud sharedInstance];// Set event listeners._trtcCloud.delegate = self;// Notifications from various SDK events (e.g., error codes, warning codes, audio and video status parameters, etc.).- (void)onError:(TXLiteAVError)errCode errMsg:(nullable NSString *)errMsg extInfo:(nullable NSDictionary *)extInfo {    NSLog(@"%d: %@", errCode, errMsg);}- (void)onWarning:(TXLiteAVWarning)warningCode warningMsg:(nullable NSString *)warningMsg extInfo:(nullable NSDictionary *)extInfo {    NSLog(@"%d: %@", warningCode, warningMsg);}// Remove event listener._trtcCloud.delegate = nil;// Terminate the RTC Engine SDK instance (singleton mode)[TRTCCloud destroySharedIntance];
```

> **Note:**It is recommended to listen to SDK event notifications. Perform log printing and handling for some common errors. For details, see [Error Code Table](https://trtc.io/document/rtc-engine-overview?product=rtcengine&menulabel=core%20sdk&platform=ios).

### Step 3: Log In and Log Out

After initializing the Chat SDK, you need to call the SDK login API to authenticate account identity and obtain permissions to use features of the account. Therefore, before using other features, ensure successful login. Otherwise, feature malfunction or unavailability may occur. If you only need to use the RTC Engine audio and video service, you can skip this step.

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb3c22e28f0411f088af5254005ef0f7.svg)

1. Log in.

```
// Log in: userID can be defined by the user and userSig can be generated as per Step 1.[[V2TIMManager sharedInstance] login:userID userSig:userSig succ:^{    NSLog(@"success");} fail:^(int code, NSString *desc) {    // The following error codes mean an expired UserSig, and you need to generate a new one for log-in again.    // 1. ERR_USER_SIG_EXPIRED(6206).    // 2. ERR_SVR_ACCOUNT_USERSIG_EXPIRED(70001).    // Note: For other error codes, do not call the login API here to avoid the Chat SDK entering an infinite loop.    NSLog(@"failure, code:%d, desc:%@", code, desc);}];
```

2. Log out.

```
// Log out.[[V2TIMManager sharedInstance] logout:^{    NSLog(@"success");} fail:^(int code, NSString *desc) {    NSLog(@"failure, code:%d, desc:%@", code, desc);}];
```

> **Note:**If your application's lifecycle matches the Chat SDK's lifecycle, you do not need to log out before exiting the application. If you only use the Chat SDK after entering a specific interface and no longer use it after exiting the interface, you can log out and deinitialize the Chat SDK.

### Step 4: Room Management

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb3c743d8f0411f0818a52540099c741.svg)

1. Create a room.

The anchor (room owner) needs to create a room when going live. Here, the concept of "room" corresponds to "group" in Chat. This example only shows the way to create a Chat group on the client side. It can also be done via [server-side group creation](https://trtc.io/document/34895?product=chat&menulabel=core%20sdk&platform=android).

```
// Create a group.[[V2TIMManager sharedInstance] createGroup:GroupType_AVChatRoom groupID:groupID groupName:groupName succ:^(NSString *groupID) {    // Group created successfully.} fail:^(int code, NSString *desc) {    // Group creation failed.}];// Listen for group creation notifications.[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onGroupCreated:(NSString *)groupID {    // Group creation callback. groupID is the ID of the newly created group.}
```

> **Note:**To create a Chat group for a voice chat room scenario, select the live streaming group type `GroupType_AVChatRoom`.The RTC Engine does not provide a room-creation API. When a user attempts to join a room that does not exist, the backend automatically creates a room.

2. Enter a room.
- Join a Chat group.

```
// Join a group.[[V2TIMManager sharedInstance] joinGroup:groupID msg:message succ:^{    // Successfully joined the group.} fail:^(int code, NSString *desc) {    // Failed to join the group.}];// Listen for the event of joining a group.[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onMemberEnter:(NSString *)groupID memberList:(NSArray<V2TIMGroupMemberInfo *>*)memberList {    // Someone joined the group.}
```

- Join an RTC Engine room.

```
- (void)enterRoomWithRoomId:(NSString *)roomId userID:(NSString *)userId {    TRTCParams *params = [[TRTCParams alloc] init];    // Using a string as the room ID for example, it is recommended to keep it consistent with the Chat group ID.    params.strRoomId = roomId;    params.userId = userId;    // UserSig obtained from the business backend.    params.userSig = getUserSig(userId);    // Replace with your SDKAppID.    params.sdkAppId = SDKAppID;    // For entering a room in voice chat interaction scenarios, specify the user's role.    params.role = TRTCRoleAudience;    // Use room entry in voice chat interaction scenarios as an example.    [self.trtcCloud enterRoom:params appScene:TRTCAppSceneVoiceChatRoom];}// Event callback for the result of entering the room.- (void)onEnterRoom:(NSInteger)result {    if (result > 0) {        // result indicates the time taken (in milliseconds) to join the room.        [self toastTip:@"Enter room succeed!"];    } else {        // result indicates the error code when you fail to enter the room.        [self toastTip:@"Enter room failed!"];    }}
```

> **Note:**RTC Engine room IDs are divided into integer type `roomId` and string type `strRoomId`. Rooms of different types are not interconnected. It is advisable to unify the room ID type.When entering a room in voice chat interaction scenarios, it is necessary to specify the user's role (anchor/audience). Only anchors have permissions to push streams. If not specified, the default role is anchor.For entering a room in voice chat interaction scenarios, it is recommended to select `TRTCAppSceneVoiceChatRoom`.

3. Exit the room.
- Exit a Chat group.

```
[[V2TIMManager sharedInstance] quitGroup:groupID succ:^{    // Exiting the group successful.} fail:^(int code, NSString *desc) {    // Exiting the group failed.}];[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onMemberLeave:(NSString *)groupID member:(V2TIMGroupMemberInfo *)member {    // Group member leave callback.}
```

> **Note:**In a live streaming group (AVChatRoom), the group owner cannot exit the group. The owner can only dissolve the group by calling `dismissGroup`.

- Exit an RTC Engine room.

```
- (void)exitTrtcRoom {    self.trtcCloud = [TRTCCloud sharedInstance];    [self.trtcCloud stopLocalAudio];    [self.trtcCloud exitRoom];}// Listen for the onExitRoom callback to get the reason for exiting the room.- (void)onExitRoom:(NSInteger)reason {    if (reason == 0) {        // Actively call exitRoom to exit the room.        NSLog(@"Exit current room by calling the 'exitRoom' api of sdk ...");    } else if (reason == 1) {        // Removed from the current room by the server.        NSLog(@"Kicked out of the current room by server through the restful api...");    } else if (reason == 2) {        // The current room is dissolved.        NSLog(@"Current room is dissolved by server through the restful api...");    }}
```

> **Note:**After all resources occupied by the SDK are released, the SDK will throw the `onExitRoom` callback notification to inform you.If you want to call `enterRoom` again or switch to another audio/video SDK, wait for the `onExitRoom` callback before proceeding. Otherwise, you may encounter exceptions such as the camera or microphone being forcefully occupied.

4. Dissolve the room.
- Dissolve a Chat group.

This example only shows the way to dissolve a Chat group on the client side. It can also be done via [server-side group dissolving](https://trtc.io/document/34896?product=chat&menulabel=core%20sdk&platform=ios%20and%20macos).

```
[[V2TIMManager sharedInstance] dismissGroup:groupID succ:^{    // Dissolving group successful.} fail:^(int code, NSString *desc) {    // Dissolving the group failed.}];[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onGroupDismissed:(NSString *)groupID opUser:(V2TIMGroupMemberInfo *)opUser {    // Group dissolved callback.}
```

- Dissolve an RTC Engine room.
  - **Server-side dissolving**: RTC Engine provides the [server-side room dissolving](https://trtc.io/document/34269?product=rtcengine&menulabel=core%20sdk&platform=ios) API `DismissRoom` (distinguish between numeric room ID and string room ID). You can call this API to remove all users from the room and dissolve the room.
  - **Client dissolving**: Complete room exit for all anchors and audiences in the room via the room exit API `exitRoom` of each client. After room exit, the room will be automatically dissolved according to RTC Engine room lifecycle rules. For details, see[Exit the Room](https://trtc.io/document/62044?product=rtcengine&menulabel=core%20sdk&platform=ios#5055ad66-53b1-4539-88ec-6992d45bb0fd).

> **Warning:**It is recommended that after the end of live streaming, you call the room dissolvement API to ensure the room is dissolved. This will prevent audiences from accidentally entering the room and incurring unexpected charges.

### Step 5: Seat Management

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb4924d38f0411f0818a52540099c741.svg)

Firstly, we can create a model to save seat information.

```
#import "JSONModel.h"typedef NS_ENUM(NSUInteger, SeatInfoStatus) {    SeatInfoStatusUnused = 0,    SeatInfoStatusUsed = 1,    SeatInfoStatusLocked = 2,};NS_ASSUME_NONNULL_BEGIN@interface SeatInfoModel : JSONModel/// Seat status, corresponding to three statuses.@property (nonatomic, assign) SeatInfoStatus status;/// Whether the seat is muted.@property (nonatomic, assign) BOOL mute;/// When the seat is occupied, store the user information.@property (nonatomic, copy) NSString *userId;@endNS_ASSUME_NONNULL_END
```

1. Join a voice chat actively.

Becoming a speaker refers to off-mic audience sending a request to speak to the room owner or administrator. The audience can speak once the approval signaling is received. In a free-speaking mode, the signaling request part can be skipped.

  - Audience sends a request to speak.

```
// Audience sends a request to speak. userId is the Anchor ID, and data can pass in a JSON identifying the signaling.- (void)sendInvitationWithUserId:(NSString *)userId data:(NSString *)data {    [[V2TIMManager sharedInstance] invite:userId data:data onlineUserOnly:YES offlinePushInfo:nil timeout:0 succ:^{        NSLog(@"sendInvitation success");    } fail:^(int code, NSString *desc) {        NSLog(@"sendInvitation error %d", code);    }];}// Anchor receives the request to speak. inviteID is the request ID, and inviter is the requester ID.[[V2TIMManager sharedInstance] addSignalingListener:self];- (void)onReceiveNewInvitation:(NSString *)inviteID inviter:(NSString *)inviter groupID:(NSString *)groupID inviteeList:(NSArray<NSString *> *)inviteeList data:(NSString * __nullable)data {    NSLog(@"received invitation: %@ from %@", inviteID, inviter);}
```

  - Anchor processes the request to speak.

```
// Agree to the request to speak.- (void)acceptInvitationWithInviteID:(NSString *)inviteID data:(NSString *)data {    [[V2TIMManager sharedInstance] accept:inviteID data:data succ:^{        NSLog(@"acceptInvitation success");    } fail:^(int code, NSString *desc) {        NSLog(@"acceptInvitation error %d", code);    }];}// Reject the request to speak.- (void)rejectInvitationWithInviteID:(NSString *)inviteID data:(NSString *)data {    [[V2TIMManager sharedInstance] reject:inviteID data:data succ:^{        NSLog(@"rejectInvitation success");    } fail:^(int code, NSString *desc) {        NSLog(@"rejectInvitation error %d", code);    }];}
```

  - Audience to speak.

If the anchor agrees to the audience's request to speak, the audience can add seat information by modifying group attributes. Other users will receive a callback for the change in group attributes. Update the local seat information.

```
// Locally saved full list of seats.@property (nonatomic, copy) NSArray<SeatInfoModel *> *seatInfoArray;// Callback for agreeing to the request to speak.- (void)onInviteeAccepted:(NSString *)inviteID invitee:(NSString *)invitee data:(NSString * __nullable)data {    NSLog(@"received accept invitation: %@ from %@", inviteID, invitee);    NSInteger seatIndex = [self findSeatIndex:inviteID];    [self takeSeatWithIndex:seatIndex];}// Audience begins to speak.- (void)takeSeatWithIndex:(NSInteger)seatIndex {    // Create a seat information instance. Store the modified seat information.    SeatInfoModel *localInfo = self.seatInfoArray[seatIndex];    SeatInfoModel *seatInfo = [[SeatInfoModel alloc] init];    seatInfo.status = SeatInfoStatusUsed;    seatInfo.mute = localInfo.mute;    seatInfo.userId = self.userId;        // Serialize the seat information object into JSON format.    NSString *jsonStr = seatInfo.toJSONString;    NSDictionary *dict = @{ [NSString stringWithFormat:@"seat%ld", seatIndex]: jsonStr };        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the attribute is added.    [[V2TIMManager sharedInstance] setGroupAttributes:self.groupId attributes:dict succ:^{        // Successfully modified group attributes. Switch TRTC role and start streaming.        [self.trtcCloud switchRole:TRTCRoleAnchor];        [self.trtcCloud startLocalAudio:TRTCAudioQualityDefault];    } fail:^(int code, NSString *desc) {        // Failed to modify group attributes. Failed to become a speaker.    }];}
```

2. Bring someone to a voice chat.

Anchor brings someone to a voice chat (with no listener consent required), directly modifies the seat information saved in group attributes. After matching the userId successfully upon receiving the group attribute change callback, the corresponding listener can switch the RTC Engine role and start streaming. In an invite-to-speak mode, refer to the implementation logic of becoming a speaker. Just switch the sender and recipient of the signaling.

```
// Locally saved full list of seats.@property (nonatomic, copy) NSArray<SeatInfoModel *> *seatInfoArray;// Anchor calls this API to modify the seat information saved in group attributes.- (void)pickSeatWithUserId:(NSString *)userId seatIndex:(NSInteger)seatIndex {    // Create a seat information instance. Store the modified seat information.    SeatInfoModel *localInfo = self.seatInfoArray[seatIndex];    SeatInfoModel *seatInfo = [[SeatInfoModel alloc] init];    seatInfo.status = SeatInfoStatusUsed;    seatInfo.mute = localInfo.mute;    seatInfo.userId = self.userId;        // Serialize the seat information object into JSON format.    NSString *jsonStr = seatInfo.toJSONString;    NSDictionary *dict = @{ [NSString stringWithFormat:@"seat%ld", seatIndex]: jsonStr };        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the attribute is added.    [[V2TIMManager sharedInstance] setGroupAttributes:self.groupId attributes:dict succ:^{        // Successfully modified group attributes and it triggers onGroupAttributeChanged callback.    } fail:^(int code, NSString *desc) {        // Failed to modify group attributes. Failed to become a speaker.    }];}// Audience receives group attribute change callback. Audience starts streaming after successfully matching own information.[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onGroupAttributeChanged:(NSString *)groupID attributes:(NSMutableDictionary<NSString *,NSString *> *)attributes {    // Last locally saved full list of seats.    NSArray *oldSeatArray = self.seatInfoArray;    // The most recent full list of seats parsed from groupAttributeMap.    NSArray *newSeatArray = [self getSeatListFromAttr:attributes seatSize:self.seatSize];    // Iterate through the full list of seats. Compare old and new seat information.    for (int i = 0; i < self.seatSize; i++) {        SeatInfoModel *oldInfo = oldSeatArray[i];        SeatInfoModel *newInfo = newSeatArray[i];        if (oldInfo.status != newInfo.status && newInfo.status == SeatInfoStatusUsed) {            if ([newInfo.userId isEqualToString:self.userId]) {                // Match own information successfully. Switch TRTC role and start streaming.                [self.trtcCloud switchRole:TRTCRoleAnchor];                [self.trtcCloud startLocalAudio:TRTCAudioQualityDefault];            } else {                // Update local seat list. Render local seat view.            }        }    }}
```

3. Leave a voice chat actively.

Mic-connecting audiences can reset seat information by modifying group attributes. Other users will receive a group attribute change callback. Update local seat information.

```
// Locally saved full list of seats.@property (nonatomic, copy) NSArray<SeatInfoModel *> *seatInfoArray;- (void)leaveSeatWithIndex:(NSInteger)seatIndex {    // Create a seat information instance. Store the modified seat information.    SeatInfoModel *localInfo = self.seatInfoArray[seatIndex];    SeatInfoModel *seatInfo = [[SeatInfoModel alloc] init];    seatInfo.status = SeatInfoStatusUnused;    seatInfo.mute = localInfo.mute;    seatInfo.userId = @"";        // Serialize the seat information object into JSON format.    NSString *jsonStr = seatInfo.toJSONString;    NSDictionary *dict = @{ [NSString stringWithFormat:@"seat%ld", seatIndex]: jsonStr };        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the attribute is added.    [[V2TIMManager sharedInstance] setGroupAttributes:self.groupId attributes:dict succ:^{        // Successfully modified group attributes. Switch TRTC role and stop streaming.        [self.trtcCloud switchRole:TRTCRoleAudience];        [self.trtcCloud stopLocalAudio];    } fail:^(int code, NSString *desc) {        // Failed to modify group attributes. Failed to become a listener.    }];}
```

4. Remove people from the voice chat.

Anchor removes a speaker. Directly modify the seat information saved in group attributes. After matching the userId successfully upon receiving the group attribute change callback, the corresponding listener can switch the RTC Engine role and stop streaming.

```
// Locally saved full list of seats.@property (nonatomic, copy) NSArray<SeatInfoModel *> *seatInfoArray;// Anchor calls this API to modify the seat information saved in group attributes.- (void)kickSeatWithIndex:(NSInteger)seatIndex {    // Create a seat information instance. Store the modified seat information.    SeatInfoModel *localInfo = self.seatInfoArray[seatIndex];    SeatInfoModel *seatInfo = [[SeatInfoModel alloc] init];    seatInfo.status = SeatInfoStatusUnused;    seatInfo.mute = localInfo.mute;    seatInfo.userId = @"";        // Serialize the seat information object into JSON format.    NSString *jsonStr = seatInfo.toJSONString;    NSDictionary *dict = @{ [NSString stringWithFormat:@"seat%ld", seatIndex]: jsonStr };        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the attribute is added.    [[V2TIMManager sharedInstance] setGroupAttributes:self.groupId attributes:dict succ:^{        // Successfully modified group attributes and it triggers onGroupAttributeChanged callback.    } fail:^(int code, NSString *desc) {        // Failed to modify group attributes. Failed to remove the speaker.    }];}// Mic-connecting audience receives group attribute change callback. It stops streaming after successfully matching own information.[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onGroupAttributeChanged:(NSString *)groupID attributes:(NSMutableDictionary<NSString *,NSString *> *)attributes {    // Last locally saved full list of seats.    NSArray *oldSeatArray = self.seatInfoArray;    // The most recent full list of seats parsed from groupAttributeMap.    NSArray *newSeatArray = [self getSeatListFromAttr:attributes seatSize:self.seatSize];    // Iterate through the full list of seats. Compare old and new seat information.    for (int i = 0; i < self.seatSize; i++) {        SeatInfoModel *oldInfo = oldSeatArray[i];        SeatInfoModel *newInfo = newSeatArray[i];        if (oldInfo.status != newInfo.status && newInfo.status == SeatInfoStatusUnused) {            if ([newInfo.userId isEqualToString:self.userId]) {                // Match own information successfully. Switch TRTC role and stop streaming.                [self.trtcCloud switchRole:TRTCRoleAudience];                [self.trtcCloud stopLocalAudio];            } else {                // Update local seat list. Render local seat view.            }        }    }}
```

5. Mute the mic.

Anchor mutes/unmutes a specific seat. Directly modify the seat information saved in group attributes. Corresponding mic-connecting audience receives group attribute change callback. After successfully matching userId, they pause/resume local streaming.

```
// Locally saved full list of seats.@property (nonatomic, copy) NSArray<SeatInfoModel *> *seatInfoArray;// Anchor calls this API to modify the seat information saved in group attributes.- (void)muteSeatWithIndex:(NSInteger)seatIndex mute:(BOOL)mute {    // Create a seat information instance. Store the modified seat information.    SeatInfoModel *localInfo = self.seatInfoArray[seatIndex];    SeatInfoModel *seatInfo = [[SeatInfoModel alloc] init];    seatInfo.status = localInfo.status;    seatInfo.mute = mute;    seatInfo.userId = localInfo.userId;        // Serialize the seat information object into JSON format.    NSString *jsonStr = seatInfo.toJSONString;    NSDictionary *dict = @{ [NSString stringWithFormat:@"seat%ld", seatIndex]: jsonStr };        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the attribute is added.    [[V2TIMManager sharedInstance] setGroupAttributes:self.groupId attributes:dict succ:^{        // Successfully modified group attributes and it triggers onGroupAttributeChanged callback.    } fail:^(int code, NSString *desc) {        // Failed to modify group attributes. Failed to mute the seat.    }];}// The mic-connecting audience receives the group attribute change callback. The audience pauses/resumes streaming after successfully matching own information.[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onGroupAttributeChanged:(NSString *)groupID attributes:(NSMutableDictionary<NSString *,NSString *> *)attributes {    // Last locally saved full list of seats.    NSArray *oldSeatArray = self.seatInfoArray;    // The most recent full list of seats parsed from groupAttributeMap.    NSArray *newSeatArray = [self getSeatListFromAttr:attributes seatSize:self.seatSize];    // Iterate through the full list of seats. Compare old and new seat information.    for (int i = 0; i < self.seatSize; i++) {        SeatInfoModel *oldInfo = oldSeatArray[i];        SeatInfoModel *newInfo = newSeatArray[i];        if (oldInfo.mute != newInfo.mute) {            if ([newInfo.userId isEqualToString:self.userId]) {                // Match own information successfully. Pause/resume local streaming.                [self.trtcCloud muteLocalAudio:newInfo.mute];            } else {                // Update local seat list. Render local seat view.            }        }    }}
```

6. Lock the mic.

Anchor locks/unlocks a seat by directly modifying the seat information saved in group attributes. Audience updates the corresponding seat view after receiving the group attribute change callback.

```
// Locally saved full list of seats.@property (nonatomic, copy) NSArray<SeatInfoModel *> *seatInfoArray;// Anchor calls this API to modify the seat information saved in group attributes.- (void)lockSeatWithIndex:(NSInteger)seatIndex isLock:(BOOL)isLock {    // Create a seat information instance. Store the modified seat information.    SeatInfoModel *localInfo = self.seatInfoArray[seatIndex];    SeatInfoModel *seatInfo = [[SeatInfoModel alloc] init];    seatInfo.status = isLock? SeatInfoStatusLocked : SeatInfoStatusUnused;    seatInfo.mute = localInfo.mute;    seatInfo.userId = @"";        // Serialize the seat information object into JSON format.    NSString *jsonStr = seatInfo.toJSONString;    NSDictionary *dict = @{ [NSString stringWithFormat:@"seat%ld", seatIndex]: jsonStr };        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the attribute is added.    [[V2TIMManager sharedInstance] setGroupAttributes:self.groupId attributes:dict succ:^{        // Successfully modified group attributes and it triggers onGroupAttributeChanged callback.    } fail:^(int code, NSString *desc) {        // Failed to modify group attributes. Failed to lock the seat.    }];}// The audience receives the group attribute change callback. Update the corresponding seat view.[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onGroupAttributeChanged:(NSString *)groupID attributes:(NSMutableDictionary<NSString *,NSString *> *)attributes {    // Last locally saved full list of seats.    NSArray *oldSeatArray = self.seatInfoArray;    // The most recent full list of seats parsed from groupAttributeMap.    NSArray *newSeatArray = [self getSeatListFromAttr:attributes seatSize:self.seatSize];    // Iterate through the full list of seats. Compare old and new seat information.    for (int i = 0; i < self.seatSize; i++) {        SeatInfoModel *oldInfo = oldSeatArray[i];        SeatInfoModel *newInfo = newSeatArray[i];        if (oldInfo.status == SeatInfoStatusLocked && newInfo.status == SeatInfoStatusUnused) {            // Unlock a seat.        } else if (oldInfo.status != newInfo.status && newInfo.status == SeatInfoStatusLocked) {            // Lock a seat.        }    }}
```

7. Move the microphone position.

On-mic anchor moves a seat by necessarily and separately modifying the source and target seat information saved in group attributes. Audience updates the corresponding seat view after receiving the group attribute change callback.

```
// Locally saved full list of seats.@property (nonatomic, copy) NSArray<SeatInfoModel *> *seatInfoArray;// On-mic anchor calls this API to modify the seat information saved in group attributes.- (void)moveSeatToIndex:(NSInteger)dstIndex {    // Obtain the source seat ID by userId.    __block NSInteger srcIndex = -1;    [self.seatInfoArray enumerateObjectsUsingBlock:^(SeatInfoModel * _Nonnull seatInfo, NSUInteger idx, BOOL * _Nonnull stop) {        if ([seatInfo.userId isEqualToString:self.userId]) {            srcIndex = idx;            *stop = YES;        }    }];    if (srcIndex < 0 || dstIndex < 0 || dstIndex >= self.seatInfoArray.count) {        return;    }        // Obtain the corresponding seat information by its ID.    SeatInfoModel *srcSeatInfo = self.seatInfoArray[srcIndex];    SeatInfoModel *dstSeatInfo = self.seatInfoArray[dstIndex];        // Create a seat information instance to store the modified source seat data.    SeatInfoModel *srcChangeInfo = [[SeatInfoModel alloc] init];    srcChangeInfo.status = SeatInfoStatusUnused;    srcChangeInfo.mute = srcSeatInfo.mute;    srcChangeInfo.userId = @"";        // Create a seat information instance to store the modified target seat data.    SeatInfoModel *dstChangeInfo = [[SeatInfoModel alloc] init];    dstChangeInfo.status = SeatInfoStatusUsed;    dstChangeInfo.mute = dstSeatInfo.mute;    dstChangeInfo.userId = self.userId;        // Serialize the seat information object into JSON format.    NSString *srcJsonStr = srcChangeInfo.toJSONString;    NSString *dstJsonStr = dstChangeInfo.toJSONString;    NSDictionary *dict = @{ [NSString stringWithFormat:@"seat%ld", srcIndex]: srcJsonStr,                            [NSString stringWithFormat:@"seat%ld", dstIndex]: dstJsonStr    };        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the attribute is added.    [[V2TIMManager sharedInstance] setGroupAttributes:self.groupId attributes:dict succ:^{        // Modify group attributes successfully. Move the seat successfully.    } fail:^(int code, NSString *desc) {        // Failed to modify group attributes. Failed to move the seat.    }];}
```

### Step 6: Audio Management

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb4fe6a38f0411f0814e525400bf7822.svg)

1. Subscription mode.

The RTC Engine SDK defaults to automatic subscription of audio streams. Users automatically play remote users' voice when joining a room. For manual subscription to audio streams, calling` muteRemoteAudio(userId, mute) `additionally is required to subscribe and play remote users' audio streams.

```
// Automatic subscription mode (default).[self.trtcCloud setDefaultStreamRecvMode:YES video:YES];// Manual subscription mode (custom).[self.trtcCloud setDefaultStreamRecvMode:NO video:NO];
```

> **Note:**Set the subscription mode `setDefaultStreamRecvMode` before entering the room `enterRoom` to ensure to take effect.

2. Collect and publish.

```
// Enable local audio capture and publishing.[self.trtcCloud startLocalAudio:TRTCAudioQualityDefault];// Stop local audio capture and publishing.[self.trtcCloud stopLocalAudio];
```

> **Note:**`startLocalAudio` requests mic permissions, and `stopLocalAudio` releases them.

3. Mute and unmute.

```
// Pause publishing local audio streams (mute).[self.trtcCloud muteLocalAudio:YES];// Resume publishing local audio streams (unmute).[self.trtcCloud muteLocalAudio:NO];// Pause the subscription and playback of a specific remote user's audio streams.[self.trtcCloud muteRemoteAudio:userId mute:YES];// Resume the subscription and playback of a specific remote user's audio streams.[self.trtcCloud muteRemoteAudio:userId mute:NO];// Pause the subscription and playback of all remote users' audio streams.[self.trtcCloud muteAllRemoteAudio:YES];// Resume the subscription and playback of all remote users' audio streams.[self.trtcCloud muteAllRemoteAudio:NO];
```

> **Note:**In comparison, `muteLocalAudio` only requires a pause or release of the data stream at the software level, thus it is more efficient and smoother. And it is better suited for scenarios that require frequent muting and unmuting.

4. Audio quality and volume type.
  - Audio quality setting

```
// Set audio quality during local audio capture and publishing.[self.trtcCloud startLocalAudio:TRTCAudioQualityDefault];// Dynamically set audio quality during audio streaming.[self.trtcCloud setAudioQuality:TRTCAudioQualityDefault];
```

> **Note:**The RTC Engine offers 3 preset audio quality levels (Speech/Default/Music), corresponding to different audio parameters. For details, see [TRTCAudioQuality](https://trtc.io/document/50760?platform=ios&product=rtcengine&menulabel=core%20sdk#f8aeb89d8ef78db15d893e55f68cdb42).

  - Volume type setting.

Each RTC Engine audio quality level corresponds to a default volume type. If you need to forcibly specify a volume type, you can use the following API.

```
// Set volume type.[self.trtcCloud setSystemVolumeType:TRTCSystemVolumeTypeAuto];
```

> **Note:**The RTC Engine offers 3 volume type levels (VOIP/Auto/Media), corresponding to different volume channels. For details, see [TRTCSystemVolumeType](https://trtc.io/document/50760?platform=ios&product=rtcengine&menulabel=core%20sdk#231e219e2864cf7145620089c6321c8e).

  - Audio routing setting.

Mobile devices such as smartphones usually have two playback locations: the speaker and the earpiece. If you need to forcibly specify the audio routing, you can use the following API.

```
// Set audio routing.[self.trtcCloud setAudioRoute:TRTCAudioModeSpeakerphone];
```

> **Note:**The RTC Engine offers two audio routes (Speaker/Earpiece), corresponding to different sound emission locations. For details, see [TRTCAudioRoute](https://trtc.io/document/50760?product=rtcengine&menulabel=core%20sdk&platform=ios#aaca0d57f6f9d9c6a6425485464b0877).

## Advanced Features

### Bullet Screen Message Interaction

Voice chat live streaming rooms usually provide text-based bullet screen message interactions, which can be achieved by sending and receiving group chat plain text messages through Chat.

```
// Send public screen bullet screen messages.[[V2TIMManager sharedInstance] sendGroupTextMessage:text to:groupID priority:V2TIM_PRIORITY_NORMAL succ:^{    // Successfully sent bullet screen messages.} fail:^(int code, NSString *desc) {    // Failed to send bullet screen messages.}];// Receive public screen bullet screen messages.[[V2TIMManager sharedInstance] addSimpleMsgListener:self];- (void)onRecvGroupTextMessage:(NSString *)msgID groupID:(NSString *)groupID sender:(V2TIMGroupMemberInfo *)info text:(NSString *)text {    NSLog(@"%@: %@", info.nickName, text);}
```

### Volume Level Callback

RTC Engine can callback the volume levels of the on-mic anchor at a fixed frequency. It is usually used to display sound waves and indicate the speaking anchor.

```
// Enable volume level callback. It is recommended to be enabled immediately after successful room entry.// interval: Callback interval (ms). enable_vad: Whether to enable voice detection.[self.trtcCloud enableAudioVolumeEvaluation:interval enable_vad:enable_vad];self.trtcCloud.delegate = self;- (void)onUserVoiceVolume:(NSArray<TRTCVolumeInfo *> *)userVolumes totalVolume:(NSInteger)totalVolume {    // userVolumes is used to hold the volume levels of all speaking users, including both local users and remote streaming users.    // totalVolume is used to report the maximum volume value among remote streaming users.    ...    // Adjust the corresponding visual representation of sound waves on the UI based on volume levels.    ...}
```

> **Note:**Voice detection only provides local voice detection results. The user's role must be an anchor to make it convenient to remind users to turn on their mics.`userVolumes` is an array. For each element in the array, when userId is empty, it means the volume captured by the local mic; when userId is not empty, it means the volume of remote users.

### Music and Sound Effect Playback

Playing background music and sound effects is a high-frequency demand in voice chat room scenarios. Below, we will explain the use of and precautions for commonly used background music APIs.

1. Start/stop/pause/resume playback.

```
// Obtain the management class for configuring background music, short sound effects, and voice special effects.self.audioEffectManager = [self.trtcCloud getAudioEffectManager];TXAudioMusicParam *param = [[TXAudioMusicParam alloc] init];param.ID = musicID;param.path = musicPath;// Whether to publish the music to remote (otherwise play locally only).param.publish = YES;// Whether the playback is from a short sound effect file.param.isShortFile = NO;// Start background music playback.__weak typeof(self) weakSelf = self;[self.audioEffectManager startPlayMusic:param onStart:^(NSInteger errCode) {    __strong typeof(weakSelf) strongSelf = weakSelf;    // Playback start callback.    // -4001: Path opening failed.    // -4002: Decoding failed.    // -4003: Invalid URL address.    // -4004: Playback not stopped.    if (errCode < 0) {        // Before replaying after playback failure, you must first stop the current music.        [strongSelf.audioEffectManager stopPlayMusic:musicID];    }} onProgress:^(NSInteger progressMs, NSInteger durationMs) {    // Playback progress callback.    // progressMs: Current playback duration (milliseconds).    // durationMs: Total duration of the current music (milliseconds).} onComplete:^(NSInteger errCode) {    // Playback end callback.    // Playback failure due to weak network during playback will also throw this callback. In this case, errCode < 0.    // Pausing or stopping playback midway will not trigger the onComplete callback.}];// Stop background music playback.[self.audioEffectManager stopPlayMusic:musicID];// Pause background music playback.[self.audioEffectManager pausePlayMusic:musicID];// Resume background music playback.[self.audioEffectManager resumePlayMusic:musicID];
```

> **Note:**The RTC Engine supports playing multiple music tracks simultaneously, identified uniquely by musicID. To play only one piece of music at a time, stop other music before starting playback. Alternatively, use the same musicID to play different music. In this way, the SDK will stop the previous music first, then play the next music.The RTC Engine supports playing local and network audio files. Use `musicPath` to input a local absolute path or URL address. Supported formats include MP3/AAC/M4A/WAV.

2. Adjust the ratio of music and voice volume.

```
// Set the local playback volume of a piece of background music.[self.audioEffectManager setMusicPlayoutVolume:musicID volume:volume];// Set the remote playback volume of a specific background music.[self.audioEffectManager setMusicPublishVolume:musicID volume:volume];// Set the local and remote volume of all background music.[self.audioEffectManager setAllMusicVolume:volume];// Set the volume of voice capture.[self.audioEffectManager setVoiceVolume:volume];
```

> **Note:**Volume value's normal range is 0-100, with a default of 60 and a maximum setting of 150, but there is a risk of audio clipping.If background music is overwhelming vocals, consider lowering the music playback volume and increasing the voice capture volume.**Mute the mic without muting background music**: Use `setVoiceVolume(0)` to replace `muteLocalAudio(true)`.

3. Repeat background music and sound effects continuously.
  - Solution 1: Use the `AudioMusicParam`'s `loopCount` parameter to set the number of loop playbacks.

The value range is from 0 to any positive integer. The default value is 0. 0 means play the music once; 1 means play the music twice; and so on.

```
- (void)startPlayMusicWithId:(int32_t)musicId path:(NSString *)path loopCount:(NSInteger)loopCount {    TXAudioMusicParam *param = [[TXAudioMusicParam alloc] init];    param.ID = musicId;    param.path = path;    param.publish = YES;    // Whether the playback is from a short sound effect file.    param.isShortFile = YES;    // Set the number of loop playbacks. Negative number means an infinite loop.    param.loopCount = loopCount < 0 ? NSIntegerMax : loopCount;    [self.audioEffectManager startPlayMusic:param onStart:nil onProgress:nil onComplete:nil];}
```

> **Note:**Solution 1 will not trigger the `onComplete` callback after each loop playback. It will only be triggered after all the set loop counts have been played.

- Solution 2: Implement loop playback through the "Background music has finished playing" event callback `onComplete`. It is usually used for list loop or single track loop.

```
- (void)repeatPlayMusicWithParam:(TXAudioMusicParam *)param {    __weak typeof(self) weakSelf = self;    [self.audioEffectManager startPlayMusic:param onStart:nil onProgress:nil onComplete:^(NSInteger errCode) {        __strong typeof(weakSelf) strongSelf = weakSelf;        // Here you can re-call the playback API to achieve loop playback of the music.        if (errCode >= 0) {            [strongSelf repeatPlayMusicWithParam:param];        }    }];}
```

### Mixed Stream Relay and Push Back

1. Send mixed streams to the RTC Engine room.

```
- (void)startPublishMediaToRoom:(NSString *)roomId userID:(NSString *)userId {    // The target URLs for media stream publication.    TRTCPublishTarget *target = [[TRTCPublishTarget alloc] init];    // After mixing, the stream is relayed back to the room.    target.mode = TRTCPublishMixStreamToRoom;    target.mixStreamIdentity.strRoomId = roomId;    // Mixed stream robot's userid, must not duplicate with other users' userid in the room.    target.mixStreamIdentity.userId = [NSString stringWithFormat:@"%@%@", userId, MIX_ROBOT];        TRTCStreamEncoderParam* encoderParam = [[TRTCStreamEncoderParam alloc] init];    // Set the encoding parameters of the transcoded audio stream (can be customized).    encoderParam.audioEncodedSampleRate = 48000;    encoderParam.audioEncodedChannelNum = 2;    encoderParam.audioEncodedKbps = 64;    encoderParam.audioEncodedCodecType = 2;        // Set the encoding parameters of the transcoded video stream (can be ignored for pure audio mix stream).    encoderParam.videoEncodedWidth = 64;    encoderParam.videoEncodedHeight = 64;    encoderParam.videoEncodedFPS = 15;    encoderParam.videoEncodedGOP = 3;    encoderParam.videoEncodedKbps = 30;        // Set audio mixing parameters.    TRTCStreamMixingConfig *config = [[TRTCStreamMixingConfig alloc] init];    // By default, leave this field empty. It indicates that all audio in the room will be mixed.    config.audioMixUserList = nil;        // Configure video mixing template (can be ignored for pure audio mix stream).    TRTCVideoLayout *layout = [[TRTCVideoLayout alloc] init];    config.videoLayoutList = @[layout];        // Start mixing and relaying mixed streams.    [self.trtcCloud startPublishMediaStream:target encoderParam:encoderParam mixingConfig:config];}
```

2. Perform event callback and update, and stop the tasks.
  - Task result event callback.

```
#pragma mark - TRTCCloudDelegate- (void)onStartPublishMediaStream:(NSString *)taskId code:(int)code message:(NSString *)message extraInfo:(NSDictionary *)extraInfo {    // taskId: When the request is successful, TRTC backend will provide the taskId of this task in the callback. You can later use this taskId with updatePublishMediaStream and stopPublishMediaStream to update and stop.    // code: Callback result. 0 means success and other values mean failure.}- (void)onUpdatePublishMediaStream:(NSString *)taskId code:(int)code message:(NSString *)message extraInfo:(NSDictionary *)extraInfo {    // When you call the publish media stream API (updatePublishMediaStream), the taskId you provide will be returned to you through this callback. It is used to identify which update request the callback belongs to.    // code: Callback result. 0 means success and other values mean failure.}- (void)onStopPublishMediaStream:(NSString *)taskId code:(int)code message:(NSString *)message extraInfo:(NSDictionary *)extraInfo {    // When you call the stop publishing media stream API (stopPublishMediaStream), the taskId you provide will be returned to you through this callback. It is used to identify which stop request the callback belongs to.    // code: Callback result. 0 means success and other values mean failure.}
```

  - Update the published media stream.

This API sends a command to the RTC Engine server to update the media stream initiated by startPublishMediaStream.

```
// taskId: Task ID returned by the onStartPublishMediaStream callback.// target: For example, add or remove the published CDN URLs.// params: It is recommended to maintain consistency in the encoding output parameters for the media stream to avoid interruptions during playback.// config: Update the list of users involved in mix stream transcoding, such as cross-room PK.[self.trtcCloud updatePublishMediaStream:taskId publishTarget:target encoderParam:trtcStreamEncoderParam mixingConfig:trtcStreamMixingConfig];
```

> **Note:**Switching between audio only, audio and video, and video only is not supported within the same task.

  - Stop publishing media stream.

This API sends a command to the RTC Engine server to stop the media stream initiated by `startPublishMediaStream`.

```
// taskId: Task ID returned by the onStartPublishMediaStream callback.[self.trtcCloud stopPublishMediaStream:taskId];
```

> **Note:**If taskId is filled with an empty string, it will stop all media streams initiated by the user through `startPublishMediaStream`. If you have only initiated one media stream or want to stop all media streams initiated by you, this method is recommended.

### Real-Time Network Quality Callback

You can listen to `onNetworkQuality` to real-time monitor the network quality of both local and remote users. This callback is thrown every 2 seconds.

```
#pragma mark - TRTCCloudDelegate- (void)onNetworkQuality:(TRTCQualityInfo *)localQuality remoteQuality:(NSArray<TRTCQualityInfo *> *)remoteQuality {    // localQuality userId is empty. It represents the local user's network quality evaluation result.    // remoteQuality represents the remote user's network quality evaluation result. The result is affected by both remote and local factors.    switch(localQuality.quality) {        case TRTCQuality_Unknown:            NSLog(@"Undefined.");            break;        case TRTCQuality_Excellent:            NSLog(@"The current network is excellent.");            break;        case TRTCQuality_Good:            NSLog(@"The current network is good.");            break;        case TRTCQuality_Poor:            NSLog(@"The current network is moderate.");            break;        case TRTCQuality_Bad:            NSLog(@"The current network is poor.");            break;        case TRTCQuality_Vbad:            NSLog(@"The current network is very poor.");            break;        case TRTCQuality_Down:            NSLog(@"The current network does not meet the minimum requirements of TRTC.");            break;        default:            break;    }}
```

### Advanced Permission Control

RTC Engine advanced permission control can be used to set different entry permissions for different rooms, such as advanced VIP rooms. It can also control the permission for audience to speak, such as handling ganchor mics. The detailed operation steps are as follows:

1. Enable the advanced permission control switch on the feature configuration page of the application [RTC Engine Console](https://console.trtc.io/).
2. Generate privateMapKey on the backend. For sample code, see [privateMapKey computation source code](https://trtc.io/document/35157?product=rtcengine&menulabel=core%20sdk&platform=ios).
3. Room entry verification & speaking permission verification with PrivateMapKey.
  - Room entry verification

```
TRTCParams *params = [[TRTCParams alloc] init];params.sdkAppId = SDKAppID;params.roomId = self.roomId;params.userId = self.userId;// UserSig obtained from the business backend.params.userSig = [self getUserSig];// PrivateMapKey obtained from the backend.params.privateMapKey = [self getPrivateMapKey];params.role = TRTCRoleAudience;[self.trtcCloud enterRoom:params appScene:TRTCAppSceneVoiceChatRoom];
```

  - Speaking permission verification

```
// Pass in the latest PrivateMapKey obtained from the backend into the role switching API.[self.trtcCloud switchRole:TRTCRoleAnchor privateMapKey:[self getPrivateMapKey]];
```

## Exception Handling

### Exception Error Handling

When the RTC Engine SDK encounters an unrecoverable error, the error is thrown in the `onError` callback. For details, see [Error Code Table](https://trtc.io/document/35135#e9c6eb6577e24853dd9716de29044384).

- UserSig-related errors.

UserSig verification failure will lead to room-entering failure. You can use the [UserSig tool](https://console.trtc.io/usersig) for verification.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_INVALID_USER_SIG | -3320 | Room entry parameter UserSig is incorrect. Check if `TRTCParams.userSig `is empty. |
| ERR_TRTC_USER_SIG_CHECK_FAILED | -100018 | UserSig verification failed. Check if the parameter `TRTCParams.userSig` is filled in correctly or has expired. |

- Room entry or exit-related errors.

If failed to enter the room, you should first verify the correctness of the room entry parameters. It is essential that the room entry and exit APIs are called in a paired manner. This means that, even in the event of a failed room entry, the room exit API must still be called.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_CONNECT_SERVER_TIMEOUT | -3308 | Room entry request timed out. Check if your internet connection is lost or if a VPN is enabled. You may also attempt to switch to 4G for testing. |
| ERR_TRTC_INVALID_SDK_APPID | -3317 | Room entry parameter SDKAppId is incorrect. Check if `TRTCParams.sdkAppId `is empty. |
| ERR_TRTC_INVALID_ROOM_ID | -3318 | Room entry parameter roomId is incorrect. Check if `TRTCParams.roomId` or `TRTCParams.strRoomId` is empty. Note that roomId and strRoomId cannot be used interchangeably. |
| ERR_TRTC_INVALID_USER_ID | -3319 | Room entry parameter UserID is incorrect. Check if `TRTCParams.userId `is empty. |
| ERR_TRTC_ENTER_ROOM_REFUSED | -3340 | Room entry request denied. Check if `enterRoom` is called consecutively to enter a room with the same ID. |

- Device-related errors.

Errors for relevant monitoring devices. Prompt the user via UI in case of relevant errors.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_MIC_START_FAIL | -1302 | Failed to open the mic. For example, if there is an exception for the mic's configuration program (driver) on a Windows or macOS device, you should try disabling then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_SPEAKER_START_FAIL | -1321 | Failed to open the speaker. For example, if there is an exception for the speaker's configuration program (driver) on a Windows or macOS device, you should try disabling then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_MIC_OCCUPY | -1319 | The mic is occupied. This occurs when, for example, the user is currently having a call on the mobile device. |

### Exception Exit Handling

1. Be aware of network disconnection and exit the room upon timeout.

You can monitor RTC Engine network disconnection and reconnection events through the following callback.

Upon receiving the `onConnectionLost` callback, display a network disconnection icon on the local seat UI to notify the user. Simultaneously, initiate a local timer. If the `onConnectionRecovery` callback is not received after exceeding the set time threshold, it means the network remains disconnected. Then, locally initiate leaving the seat and room exit process. Pop up a window to inform the user that they have exited the room and the page will be closed. If the disconnection exceeds 90 seconds (default), a timeout room-exit will be triggered, and the RTC Engine server side will remove the user from the room. If the user has an anchor role, other users in the room will receive the `onRemoteUserLeaveRoom` callback.

```
#pragma mark - TRTCCloudDelegate- (void)onConnectionLost {    // The connection between the SDK and the cloud has been disconnected.}- (void)onTryToReconnect {    // The SDK is attempting to reconnect to the cloud.}- (void)onConnectionRecovery {    // The connection between the SDK and the cloud has been restored.}
```

2. Automatically leave the voice chat when offline.

Chat user status is divided into online (ONLINE), offline (OFFLINE), and not logged in (UNLOGINED). Among them, the offline status is usually caused by user force-stopping process or abnormal network disruption. You can detect offline mic-connecting audiences through the features of anchors subscribing to the connection status of mic-connecting audiences, thereby removing them.

```
// Anchor subscribes to the connection status of mic-connecting audiences.[[V2TIMManager sharedInstance] subscribeUserStatus:userList succ:^{    // Subscription of user status succeeded.} fail:^(int code, NSString *desc) {    // Subscription of user status failed.}];// Anchor unsubscribes from the connection status of audiences leaving the seat.[[V2TIMManager sharedInstance] unsubscribeUserStatus:userList succ:^{    // Unsubscription of user status succeeded.} fail:^(int code, NSString *desc) {    // Failed to unsubscription of user status.}];// User status change notification and processing.[[V2TIMManager sharedInstance] addIMSDKListener:self];- (void)onUserStatusChanged:(NSArray<V2TIMUserStatus *> *)userStatusList {    for (V2TIMUserStatus *userStatus in userStatusList) {        NSString *userId = userStatus.userID;        V2TIMUserStatusType status = userStatus.statusType;        if (status == V2TIM_USER_STATUS_OFFLINE) {            // Remove an offline-status user.            [self kickSeatWithIndex:[self getSeatIndexWithUserId:userId]];        }    }}
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb51c86c8f0411f0b321525400e889b2.png)

> **Note:**User status subscription needs to be upgraded to the Professional Edition package. For details, see [Basic Service Details](https://trtc.io/document/34349?product=chat&menulabel=core%20sdk&platform=android).User status subscription needs enabling **User Status Query and Status Change Notification Configurations** in the [Chat Console](https://console.trtc.io/chat) in advance. Failure to enable it will result in an error when `subscribeUserStatus` is called.

### Server-Side User Removing and Room Dissolving

1. Remove someone through the server side.

First, call the RTC Engine server-side user removing API [RemoveUser](https://trtc.io/document/34268?product=rtcengine&menulabel=core%20sdk&platform=ios) (for integer room IDs) or [RemoveUserByStrRoomId](https://trtc.io/document/39630?product=rtcengine&menulabel=core%20sdk&platform=ios) (for string room IDs) to remove the target user from the RTC Engine room. The input example is as follows:

```
https://trtc.tencentcloudapi.com/?Action=RemoveUser&SdkAppId=1400000001&RoomId=1234&UserIds.0=test1&UserIds.1=test2&<Common request parameters>
```

After the user is removed successfully, the target user on the client will receive the `onExitRoom() `callback with `reason` set to 1. You can handle leaving the seat and exiting the Chat group in this callback.

```
// Exit TRTC room event callback.- (void)onExitRoom:(NSInteger)reason {    if (reason == 0) {        // Actively call exitRoom to exit the room.        NSLog(@"Exit current room by calling the 'exitRoom' api of sdk ...");    } else {        // reason 1: Removed from the current room by the server.        // reason 2: The current room is dissolved.        NSLog(@"Kicked out of the current room by server or current room is dissolved ...");        // Leave the seat.        [self leaveSeatWithIndex:seatIndex];        // Exit the Chat group        [[V2TIMManager sharedInstance] quitGroup:groupID succ:^{            // Exiting the group successful.        } fail:^(int code, NSString *desc) {            // Exiting the group failed.        }];    }}
```

2. Dissolve the room through the server side.

First call the Chat server-side group dissolving API [destroy_group](https://trtc.io/document/34896?product=chat&menulabel=core%20sdk&platform=ios) to dissolve the target group. The request URL example is as follows:

```
https://xxxxxx/v4/group_open_http_svc/destroy_group?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

After the group is dissolved successfully, all members in the target group will receive the `onGroupDismissed() callback`. You can handle leaving the seat and exiting the RTC Engine room in this callback.

```
// Group dissolved callback.[[V2TIMManager sharedInstance] addGroupListener:self];- (void)onGroupDismissed:(NSString *)groupID opUser:(V2TIMGroupMemberInfo *)opUser {    // Exit TRTC room.    [self.trtcCloud stopLocalAudio];    [self.trtcCloud exitRoom];}
```

> **Note:**When all users in the room call `exitRoom()` to complete room exit, the RTC Engine room will be automatically dissolved. Of course, you can also call the server-side API [DismissRoom](https://trtc.io/document/34269?product=rtcengine&menulabel=core%20sdk&platform=ios) (room ID in integer type) or [DismissRoomByStrRoomId](https://trtc.io/document/39631?product=rtcengine&menulabel=core%20sdk&platform=ios) (string room ID) to mandatorily dissolve the RTC Engine room.

### Viewing Live Streaming Room's Historical Messages upon Room Entry

By default, using AVChatRoom does not store live streaming room's historical messages. Therefore, when new users enter the live streaming room, they can only see messages sent after their entry. To optimize the experience for new users joining the group, you can configure the number of messages new live streaming group users can pull before joining the group in the console, as shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eb590be18f0411f0814e525400bf7822.png)

Pulling historical messages before joining the live streaming group for live group users is the same as pulling historical messages for other groups, as shown in the sample code:

```
V2TIMMessageListGetOption *option = [[V2TIMMessageListGetOption alloc] init];option.getType = V2TIM_GET_CLOUD_OLDER_MSG; // Pull earlier existing messages from the cloud.option.getTimeBegin = 1640966400;        // Starting from midnight January 1, 2022.option.getTimePeriod = 1 * 24 * 60 * 60; // Pull messages from a 24-hour period.option.count = INT_MAX;                  // Return all messages within the time range.option.groupID = #your group id#;        // Pull messages for the group chat.[V2TIMManager.sharedInstance getHistoryMessageList:option succ:^(NSArray<V2TIMMessage *> *msgs) {    NSLog(@"success");} fail:^(int code, NSString *desc) {    NSLog(@"failure, code:%d, desc:%@", code, desc);}];
```

> **Note:**This feature is only available to advanced users. It only supports pulling up to 20 historical messages within 24 hours from the group.

### Sense the Mute Status of Anchors When They Enter the Room

Solution 1: Mute all anchors by default when they enter the room, then unmute the corresponding anchor based on the onUserAudioAvailable(userId, true) callback.

```
- (void)onUserAudioAvailable:(NSString *)userId available:(BOOL)available {    if (available) {        // Unmute the corresponding anchors.    }}
```

Solution 2: Store the anchor's mute status in the Chat group attribute. When the audience enters the room, obtain all group attributes and parse the mute status of on-mic anchors.

```
[[V2TIMManager sharedInstance] getGroupAttributes:groupID keys:nil succ:^(NSMutableDictionary<NSString *,NSString *> *groupAttributeList) {    // Successfully obtained group attributes. Assume the key for storing anchor mute status is muteStatus    NSString *muteStatus = groupAttributeList[@"muteStatus"];    // Parse muteStatus, and obtain the mute status of each on-mic anchor.} fail:^(int code, NSString *desc) {    // Failed to obtain the group attributes.}];
```


---
*Source: [https://trtc.io/document/73429](https://trtc.io/document/73429)*
