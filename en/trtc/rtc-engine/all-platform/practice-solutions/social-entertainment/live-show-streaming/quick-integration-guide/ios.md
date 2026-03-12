# iOS

## Business Process

This section summarizes some common business processes in live showroom, helping you better understand the implementation process of the entire scenario.

Anchor Starting and Ending Live Streaming

Anchor Initiating Cross-Room Mic-Connection PK

RTC Audience Entering the Room for Mic-Connection

The following diagram shows the process of an anchor (room owner) local preview, creating a room, entering a room to start live streaming, and leaving the room to end the live streaming.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0ff8cdf88f0411f0974b52540044a08e.png)

The following diagram shows the process of Anchor A inviting Anchor B for a cross-room mic-connection PK. During the cross-room mic-connection PK, the audience in both rooms can see the mic-connection live streaming of the two room owners.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0ff8e4818f0411f0818a52540099c741.png)

The following diagram shows the process for RTC live interactive streaming audience to enter the room, apply for the mic-connection, end the mic-connection, and exit the room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0fde7de68f0411f0ae9d5254001c06ec.png)

## Integration Preparation

### Step 1. Activating the Services

Live showroom scenarios usually require 2 paid PaaS services for construction, [RTC Engine](https://trtc.io/products/rtc) and [Beauty AR](https://trtc.io/products/beauty), to build. Among them, RTC Engine is responsible for providing real-time audio and video interaction capability, while Beauty AR provides beauty effects capabilities. Beauty AR is responsible for providing beauty effect capabilities. If you use a third-party beauty effect product, you can disregard the Beauty AR integration part.

Activating RTC Engine Service

Activating Beauty AR Service

1. First, log in to the [RTC Engine console](https://console.trtc.io/) to create an application. Based on your needs, you can upgrade the RTC Engine application version, such as the Professional Edition, which unlocks more value-added features and services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0ff4faa38f0411f0818a52540099c741.png)

> **Note:**It is recommended to create two applications for testing and production environments, respectively. Each Tencent Cloud account (UIN) is given 10,000 minutes of free duration every month for one year.RTC Engine monthly packages are divided into Trial Edition (default), Lite Edition, Standard Edition, and Professional Edition, unlocking different value-added features and services. For details, see [Version Features and Monthly Package Description](https://trtc.io/document/67650?product=pricing).

2. After an application is created, you can see the basic information of the application in the Application Management - Application Overview section. It is important to keep the **SDKAppID** and **SDKSecretKey** safe for later use and to avoid key leakage that could lead to traffic theft.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0fd11a718f0411f084bd5254007c27c5.png)

1. Log in to the [Beauty AR Console > Mobile Terminal License](https://console.trtc.io/beauty/license?start=1), and click **Create Trial License** (the trial license has a free trial period of 14 days and can be renewed once, totaling 28 days). Select Mobile, and enter App Name, Package Name, and Bundle ID based on your actual needs. Check the features you want to try: **All Beauty Features**, **Virtual Background**, **Face Recognition**, **Gesture Recognition**, and **Gift AR**, then click **Confirm**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0ffa1de58f0411f0ae9d5254001c06ec.png)

2. After activation, you can view your information on the current page and refer to the [integration guide](https://trtc.io/document/60195) at the top for integration. You can see how to use the License Key and License URL in the Integration Guide.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0ff78e9e8f0411f0814e525400bf7822.png)

### Step 2: Importing the SDK

The RTC Engine SDK and the Beauty AR SDK have been published to the **CocoaPods** repository. You can configure CocoaPods to download updates automatically.

1. Install CocoaPods by entering the following command in the terminal window (ensure that the Ruby environment is pre-installed on your Mac).

```
sudo gem install cocoapods
```

2. Create a Podfile. Navigate to the project directory and enter the following command. A Podfile will then be generated in the project directory.

```
pod init
```

3. Edit Podfile. Choose appropriate version for your project needs and edit Podfile.

```
platform :ios, '8.0'    target 'App' do        # RTC Engine Lite Edition    # The installation package has the minimum incremental size, but only supports 2 features, RTC Engine and live streaming player (TXLivePlayer).    pod 'TXLiteAVSDK_TRTC', :podspec => 'https://liteav.sdk.qcloud.com/pod/liteavsdkspec/TXLiteAVSDK_TRTC.podspec'        # Pro Edition    # Includes features such as RTC Engine, live streaming player (TXLivePlayer), RTMP streaming (TXLivePusher), VOD player (TXVodPlayer), and short video recording and editing (UGSV).    # pod 'TXLiteAVSDK_Professional', :podspec => 'https://liteav.sdk.qcloud.com/pod/liteavsdkspec/TXLiteAVSDK_Professional.podspec'        # Beauty AR SDK, for example: S1-07 package as follows    pod 'TencentEffect_S1-07'end
```

4. Update and install the SDK.

Enter the following command in the terminal window to update the local repository files and install the SDK.

```
pod install
```

Or run this command to update the local repository:

```
pod update
```

Upon the completion of pod command execution, a project file suffixed with .xcworkspace and integrated with the SDK will be generated. Double-click to open it.

> **Note:**If the pod search fails, it is recommended to try updating the pod's local repo cache. Update command is as follows:  pod setup  pod repo update  rm ~/Library/Caches/CocoaPods/search_index.jsonExcept the recommended automatic loading method, you can also choose to download SDK and manually import it. For details, see [Manual Integration of the RTC Engine SDK](https://trtc.io/document/62045?product=rtcengine&menulabel=core%20sdk&platform=ios#31b6b3f0-5363-44b1-95a0-dbabe648e9df) and [Manual Integration of the Beauty AR SDK](https://trtc.io/document/60195?product=beautyar&menulabel=core%20sdk&platform=ios#6d52c803-02a2-475c-9b62-d301b5d0c050).

5. Add beauty resources to actual project engineering.
  5.1. Download and decompress the corresponding package's [SDK and beauty resources](https://trtc.io/document/60206?platform=ios&product=beautyar&menulabel=core%20sdk#dynamically-downloading-.60assets.60-resources), then add the bundle resources under the resources/motionRes folder to the actual project.
  5.2. Add `-ObjC` in Other Linker Flags of Build Settings.
6. Modify the Bundle Identifier to match the applied trial authorization.

### Step 3: Project Configuration

1. Configure the permissions.

For live showroom scenarios, RTC Engine SDK and Beauty AR SDK require the following permissions. Add the following 2 items to the App's Info.plist corresponding to the microphone and camera prompts in the system pop-up authorization dialog box.

  - **Privacy - Microphone Usage Description**. Enter a prompt specifying the purpose of microphone use.
  - **Privacy - Camera Usage Description**. Enter a prompt specifying the purpose of camera use.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0fdebb438f0411f084bd5254007c27c5.png)

2. To allow the App to continue running certain features in the backend, select the current project in Xcode, set the setting item Background Modes to ON under Capabilities, and check **Audio, AirPlay and Picture in Picture**, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0fdc88548f0411f084bd5254007c27c5.png)

### Step 4: Authentication and Authorization

RTC Engine Authentication Credential

Beauty AR Authentication Permission

UserSig is a security signature designed by Tencent Cloud to prevent attackers from stealing your right of using cloud services. RTC Engine validates this authentication credential upon room entry.

- Debugging Stage: UserSig can be generated through two methods for debugging and testing purposes only: [client sample code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk&platform=ios) and [console access](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk&platform=ios#console).
- Formal Operation Stage: It is recommended to use a higher security level server computation for generating UserSig. This is to prevent key leakage due to client reverse engineering.

The specific implementation process is as follows:

1. Before calling the SDK's initialization function, your app must first request UserSig from your server.
2. Your server computes the UserSig based on the SDKAppID and UserID.
3. The server returns the computed UserSig to your app.
4. Your app passes the obtained UserSig into the SDK through a specific API.
5. The SDK submits the SDKAppID + UserID + UserSig to Tencent Cloud CVM for verification.
6. Tencent Cloud verifies the UserSig and confirms its validity.
7. After the verification passes, Tencent Real-Time Communication (TRTC) services will be provided for RTC Engine SDK.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0fe0202a8f0411f084bd5254007c27c5.jpeg)

> **Note:**The method of generating UserSig locally during the debugging and testing stage is not recommended for the online environment because it may be easily decompiled and reversed, causing key leakage.We provide UserSig server side computation source code in multiple languages (Java/Go/PHP/Node.js/Python/C#/C++). For details, see [Server-Side Calculation of UserSig](https://trtc.io/document/34580?product=chat&menulabel=uikit&platform=react#.E7.AD.BE.E5.90.8D.EF.BC.88usersig.EF.BC.89.E7.94.9F.E6.88.90.E5.B7.A5.E5.85.B7).

Before using Beauty AR, you need to verify the license credential with Tencent Cloud. Configuring License requires License Key and License URL. Sample code is as follows.

```
[TELicenseCheck setTELicense:LicenseURL key:LicenseKey completion:^(NSInteger authresult, NSString * _Nonnull errorMsg) { if (authresult == TELicenseCheckOk) {     NSLog(@"Authentication successful."); } else {     NSLog(@"Authentication failed."); }}];
```

> **Note:**It is recommended to trigger the authentication permission in the initialization code of related business modules. Ensure to avoid having to download the License temporarily before use. Additionally, during authentication, network permissions must be ensured.The actual application's Bundle ID must match exactly with the Bundle ID associated with the creation of License. Otherwise, it will lead to License verification failure. For details, see [Authentication Error Code](https://trtc.io/document/60195?product=beautyar&menulabel=core%20sdk&platform=android#.E6.AD.A5.E9.AA.A4.E4.B8.80.EF.BC.9A.E9.89.B4.E6.9D.83).

### Step 5: Initializing the SDK

Initializing RTC Engine SDK

Initializing Beauty AR SDK

```
// Create an RTC Engine SDK instance (singleton mode)self.trtcCloud = [TRTCCloud sharedInstance];// Set event listeners.self.trtcCloud.delegate = self;// Notifications from various SDK events (e.g., error codes, warning codes, audio and video status parameters, etc.).- (void)onError:(TXLiteAVError)errCode errMsg:(nullable NSString *)errMsg extInfo:(nullable NSDictionary *)extInfo {    NSLog(@"%d: %@", errCode, errMsg);}- (void)onWarning:(TXLiteAVWarning)warningCode warningMsg:(nullable NSString *)warningMsg extInfo:(nullable NSDictionary *)extInfo {    NSLog(@"%d: %@", warningCode, warningMsg);}// Remove event listener.self.trtcCloud.delegate = nil;// Terminate the RTC Engine SDK instance (singleton mode)[TRTCCloud destroySharedIntance];
```

> **Note:**It is recommended to listen to SDK event notifications. Perform log printing and handling for some common errors. For details, see [Error Code Table](https://trtc.io/zh/document/35130?platform=ios&product=rtcengine&menulabel=core%20sdk#336ef58d7636c75f9aa0c87753e08e7c).

```
// Load beauty-related resources.NSDictionary *assetsDict = @{@"core_name":@"LightCore.bundle", @"root_path":[[NSBundle mainBundle] bundlePath]};// Initialize the Tencent Effect SDK.self.beautyKit = [[XMagic alloc] initWithRenderSize:previewSize assetsDict:assetsDict];// Release the Tencent Effect SDK.[self.beautyKit deinit]
```

> **Note:**Before initializing the Beauty AR SDK, resource copying and other preparations are required. For detailed steps, see [Beauty AR SDK Integration Step](https://trtc.io/document/60195?product=beautyar&menulabel=core%20sdk&platform=android).

## Integration Process

### API Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0ff7e8da8f0411f0bd05525400454e06.svg)

### Step 1: the Anchor Enters the Room to Push Streams

1. The anchor activates local video preview and audio capture before entering the room.

```
// Obtain the video rendering control for displaying the anchor's local video preview.@property (nonatomic, strong) UIView *anchorPreviewView;@property (nonatomic, strong) TRTCCloud *trtcCloud;- (void)setupTRTC {    self.trtcCloud = [TRTCCloud sharedInstance];    self.trtcCloud.delegate = self;    // Set video encoding parameters to determine the picture quality seen by remote users.    TRTCVideoEncParam *encParam = [[TRTCVideoEncParam alloc] init];    encParam.videoResolution = TRTCVideoResolution_960_540;    encParam.videoFps = 15;    encParam.videoBitrate = 1300;    encParam.resMode = TRTCVideoResolutionModePortrait;    [self.trtcCloud setVideoEncoderParam:encParam];        // isFrontCamera can specify the use of front/rear camera for video capture    [self.trtcCloud startLocalPreview:self.isFrontCamera view:self.anchorPreviewView];    // Here you can specify the audio quality, from low to high as SPEECH/DEFAULT/MUSIC.    [self.trtcCloud startLocalAudio:TRTCAudioQualityDefault];}
```

> **Note:**You can set the video encoding parameters [TRTCVideoEncParam](https://trtc.io/document/35153?product=rtcengine&menulabel=core%20sdk&platform=ios#trtcvideoencparam) according to business needs. For the best combinations of resolutions and bitrates for each tier, see [Resolution and Bitrate Reference Table](https://trtc.io/document/35153?product=rtcengine&menulabel=core%20sdk&platform=ios#.E5.88.86.E8.BE.A8.E7.8E.87.E7.A0.81.E7.8E.87.E5.8F.82.E7.85.A7.E8.A1.A8).Call the above API before `enterRoom`. The SDK will only start the camera preview and audio capture, and wait until you call `enterRoom` to start streaming.Call the above API after `enterRoom`. The SDK will start the camera preview and audio capture and automatically start streaming.

2. The anchor sets rendering parameters for the local video, and the encoder output video mode (optional).

```
- (void)setupRenderParams {    TRTCRenderParams *params = [[TRTCRenderParams alloc] init];    // Video mirror mode    params.mirrorType = TRTCVideoMirrorTypeAuto;    // Video fill mode    params.fillMode = TRTCVideoFillMode_Fill;    // Video rotation angle    params.rotation = TRTCVideoRotation_0;    // Set the rendering parameters for the local video.    [self.trtcCloud setLocalRenderParams:params];    // Set the video mirror mode for the encoder output.    [self.trtcCloud setVideoEncoderMirror:YES];    // Set the rotation of the video encoder output.    [self.trtcCloud setVideoEncoderRotation:TRTCVideoRotation_0];}
```

> **Note:**Setting local video rendering parameters only affects the rendering effect of the local video.Setting encoder output mode affects the viewing effect for other users in the room (and the cloud recording files).

3. The anchor starts the live streaming, entering the room and start streaming.

```
- (void)enterRoomByAnchorWithUserId:(NSString *)userId roomId:(NSString *)roomId {    TRTCParams *params = [[TRTCParams alloc] init];    // Take the room ID string as an example.    params.strRoomId = roomId;    params.userId = userId;    // UserSig obtained from the business backend.    params.userSig = @"userSig";    // Replace with your SDKAppID.    params.sdkAppId = 0;    // Specify the anchor role.    params.role = TRTCRoleAnchor;    // Enter the room in an interactive live streaming scenario.    [self.trtcCloud enterRoom:params appScene:TRTCAppSceneLIVE];}// Event callback for the result of entering the room.- (void)onEnterRoom:(NSInteger)result {    if (result > 0) {        // result indicates the time taken (in milliseconds) to join the room.        NSLog(@"Enter room succeed!");    } else {        // result indicates the error code when you fail to enter the room.        NSLog(@"Enter room failed!");    }}
```

> **Note:**RTC Engine room IDs are divided into integer type `roomId` and string type `strRoomId`. Rooms of different types are not interconnected. It is advisable to unify the room ID type.RTC Engine user roles include anchor and audience. Only hosts have permission to streaming. The user role should be specified upon room entry. If it's not specified, the default role is anchor.In live showroom scenarios, it is recommended to choose `TRTCAppSceneLIVE` as the room entry mode.

### Step 2: the Audience Enters the Room to Pull Streams

1. Audience enters the RTC Engine room.

```
- (void)enterRoomByAudienceWithUserId:(NSString *)userId roomId:(NSString *)roomId {    TRTCParams *params = [[TRTCParams alloc] init];    // Take the room ID string as an example.    params.strRoomId = roomId;    params.userId = userId;    // UserSig obtained from the business backend.    params.userSig = @"userSig";    // Replace with your SDKAppID.    params.sdkAppId = 0;    // Specify the audience role.    params.role = TRTCRoleAudience;    // Enter the room in an interactive live streaming scenario.    [self.trtcCloud enterRoom:params appScene:TRTCAppSceneLIVE];}// Event callback for the result of entering the room.- (void)onEnterRoom:(NSInteger)result {    if (result > 0) {        // result indicates the time taken (in milliseconds) to join the room.        NSLog(@"Enter room succeed!");    } else {        // result indicates the error code when you fail to enter the room.        NSLog(@"Enter room failed!");    }}
```

2. Audience subscribes to the anchor's audio and video streams.

```
- (void)onUserAudioAvailable:(NSString *)userId available:(BOOL)available {    // The remote user publishes/unpublishes their audio.    // Under the automatic subscription mode, you do not need to do anything. The SDK will automatically play the remote user's audio.}- (void)onUserVideoAvailable:(NSString *)userId available:(BOOL)available {    // The remote user publishes/unpublishes the primary video.    if (available) {        // Subscribe to the remote user's video stream and bind the video rendering control.        [self.trtcCloud startRemoteView:userId streamType:TRTCVideoStreamTypeBig view:self.remoteView];    } else {        // Unsubscribe to the remote user's video stream and release the rendering control.        [self.trtcCloud stopRemoteView:userId streamType:TRTCVideoStreamTypeBig];    }}
```

3. Audience sets the rendering mode for the remote video (optional).

```
- (void)setupRemoteRenderParams {    TRTCRenderParams *params = [[TRTCRenderParams alloc] init];    // Video mirror mode    params.mirrorType = TRTCVideoMirrorTypeAuto;    // Video fill mode    params.fillMode = TRTCVideoFillMode_Fill;    // Video rotation angle    params.rotation = TRTCVideoRotation_0;    // Set the rendering mode for the remote video.    [self.trtcCloud setRemoteRenderParams:@"userId" streamType:TRTCVideoStreamTypeBig params:params];}
```

### Step 3: the Audience Interacts via Mic

1. The audience is switched to the anchor role.

```
- (void)switchToAnchor {    // Switched to the anchor role.    [self.trtcCloud switchRole:TRTCRoleAnchor];}// Event callback for switching the role.- (void)onSwitchRole:(TXLiteAVError)errCode errMsg:(NSString *)errMsg {    if (errCode == ERR_NULL) {        // Role switched successfully.    }}
```

2. Audience starts local audio and video capture and streaming.

```
- (void)setupTRTC {    // Set video encoding parameters to determine the picture quality seen by remote users.    TRTCVideoEncParam *encParam = [[TRTCVideoEncParam alloc] init];    encParam.videoResolution = TRTCVideoResolution_480_270;    encParam.videoFps = 15;    encParam.videoBitrate = 550;    encParam.resMode = TRTCVideoResolutionModePortrait;    [self.trtcCloud setVideoEncoderParam:encParam];     // isFrontCamera can specify the use of front/rear camera for video capture    [self.trtcCloud startLocalPreview:self.isFrontCamera view:self.audiencePreviewView];    // Here you can specify the audio quality, from low to high as SPEECH/DEFAULT/MUSIC.    [self.trtcCloud startLocalAudio:TRTCAudioQualityDefault];}
```

> **Note:**You can set the video encoding parameters [TRTCVideoEncParam](https://trtc.io/document/35153?product=rtcengine&menulabel=core%20sdk&platform=ios#trtcvideoencparam) according to business needs. For the best combinations of resolutions and bitrates for each tier, see [Resolution and Bitrate Reference Table](https://trtc.io/document/35153?product=rtcengine&menulabel=core%20sdk&platform=ios#.E5.88.86.E8.BE.A8.E7.8E.87.E7.A0.81.E7.8E.87.E5.8F.82.E7.85.A7.E8.A1.A8).

3. The audience leaves the seat and stops streaming.

```
- (void)switchToAudience {    // Switched to the audience role.    [self.trtcCloud switchRole:TRTCRoleAudience];}// Event callback for switching the role.- (void)onSwitchRole:(TXLiteAVError)errCode errMsg:(NSString *)errMsg {    if (errCode == ERR_NULL) {        // Stop camera capture and streaming.        [self.trtcCloud stopLocalPreview];        // Stop microphone capture and streaming.        [self.trtcCloud stopLocalAudio];    }}
```

### Step 4: Exiting and Dissolving the Room

1. Exit the room.

```
- (void)exitRoom {    [self.trtcCloud stopLocalAudio];    [self.trtcCloud stopLocalPreview];    [self.trtcCloud exitRoom];}// Event callback for exiting the room.- (void)onExitRoom:(NSInteger)reason {    if (reason == 0) {        NSLog(@"Proactively call exitRoom to exit the room");    } else if (reason == 1) {        NSLog(@"Removed from the current room by the server");    } else if (reason == 2) {        NSLog(@"The current room is dissolved");    }}
```

> **Note:**After all resources occupied by the SDK are released, the SDK will throw the `onExitRoom` callback notification to inform you.If you want to call `enterRoom` again or switch to another audio/video SDK, wait for the `onExitRoom` callback before proceeding. Otherwise, you may encounter exceptions such as the camera or microphone being forcefully occupied.

2. Dissolve the room.
  - **Server-side dissolving**: RTC Engine provides [the server side room dissolving](https://trtc.io/zh/document/34269?product=rtcengine&menulabel=core%20sdk&platform=ios) API `DismissRoom` (distinguish between numeric room ID and string room ID). You can call this API to remove all users from the room and dissolve the room.
  - **Client dissolving**: Complete room exit for all anchors and audiences in the room via the room exit API `exitRoom` of each client. After room exit, the room will be automatically dissolved according to RTC Engine room lifecycle rules. For details, see [Exit the Room](https://trtc.io/zh/document/62045?product=rtcengine&menulabel=core%20sdk&platform=ios#5055ad66-53b1-4539-88ec-6992d45bb0fd).

> **Note:**It is recommended that after the end of live streaming, you call the room dissolvement API on the server to ensure the room is dissolved. This will prevent audiences from accidentally entering the room and incurring unexpected charges.

## Advanced Features

### Anchor Initiating Cross-Room Mic-Connection PK

1. Either party initiates the cross-room mic-connection PK.

```
- (void)connectOtherRoom:(NSString *)roomId {    NSMutableDictionary *jsonDict = [[NSMutableDictionary alloc] init];    ? ? // The digit room ID is roomId.    [jsonDict setObject:roomId forKey:@"strRoomId"];    [jsonDict setObject:self.userId forKey:@"userId"];    NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDict options:NSJSONWritingPrettyPrinted error:nil];    NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];    [self.trtcCloud connectOtherRoom:jsonString];}// Result callback for requesting cross-room mic-connection.- (void)onConnectOtherRoom:(NSString *)userId errCode:(TXLiteAVError)errCode errMsg:(NSString *)errMsg {    // The user ID of the anchor in the other room you want to initiate the cross-room link-up.    // Error code. ERR_NULL indicates the request is successful.    // Error message.}
```

> **Note:**Both local and remote users participating in the cross-room mic-connection PK must be in the anchor role and must have audio or video uplink capabilities.

2. All users in both rooms will receive a callback indicating that the audio and video streams from the PK anchor in the other room are available.

```
- (void)onUserAudioAvailable:(NSString *)userId available:(BOOL)available {    // The remote user publishes/unpublishes their audio.    // Under the automatic subscription mode, you do not need to do anything. The SDK will automatically play the remote user's audio.}- (void)onUserVideoAvailable:(NSString *)userId available:(BOOL)available {    // The remote user publishes/unpublishes the primary video.    if (available) {        // Subscribe to the remote user's video stream and bind the video rendering control.        [self.trtcCloud startRemoteView:userId streamType:TRTCVideoStreamTypeBig view:self.remoteView];    } else {        // Unsubscribe to the remote user's video stream and release the rendering control.        [self.trtcCloud stopRemoteView:userId streamType:TRTCVideoStreamTypeBig];    }}
```

3. Either party exits the cross-room mic-connection PK.

```
// Exit the cross-room mic-connection.[self.trtcCloud disconnectOtherRoom];// Result callback for exiting cross-room mic-connection.- (void)onDisconnectOtherRoom:(TXLiteAVError)errCode errMsg:(NSString *)errMsg {}
```

> **Note:**After calling `DisconnectOtherRoom()`, you may exit the cross-room mic-connection PK with all other room anchors.Either the initiator or the receiver can call `DisconnectOtherRoom()` to exit the cross-room mic-connection PK.

### Integrating Third-Party Beauty Features

RTC Engine supports integrating third-party beauty effect products. The example of Beauty AR is used next to demonstrate the process of integrating the third-party beauty effects.

1. Integrate the Beauty AR SDK, and apply for authorization License. For details, see the [Access Preparation](#8b6b50a0-939d-48a1-aac1-58c6009e4b78) step for implementation.
2. Set the SDK material resource path (if any).

```
NSString *beautyConfigPath = [NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES) lastObject];beautyConfigPath = [beautyConfigPath stringByAppendingPathComponent:@"beauty_config.json"];NSFileManager *localFileManager=[[NSFileManager alloc] init];BOOL isDir = YES;NSDictionary * beautyConfigJson = @{};if ([localFileManager fileExistsAtPath:beautyConfigPath isDirectory:&isDir] && !isDir) {    NSString *beautyConfigJsonStr = [NSString stringWithContentsOfFile:beautyConfigPath encoding:NSUTF8StringEncoding error:nil];    NSError *jsonError;    NSData *objectData = [beautyConfigJsonStr dataUsingEncoding:NSUTF8StringEncoding];    beautyConfigJson = [NSJSONSerialization JSONObjectWithData:objectData                                            options:NSJSONReadingMutableContainers                                            error:&jsonError];}NSDictionary *assetsDict = @{@"core_name":@"LightCore.bundle",                            @"root_path":[[NSBundle mainBundle] bundlePath],                            @"tnn_"                            @"beauty_config":beautyConfigJson};// Initialize the SDK: Width and height are the width and height of the texture, respectively.self.xMagicKit = [[XMagic alloc] initWithRenderSize:CGSizeMake(width,height) assetsDict:assetsDict];
```

3. Set video data callback for third-party beauty effects by passing the results of the beauty effect SDK processing each frame of data into the RTC Engine SDK for rendering processing.

```
// RTC Engine SDK sets video data callback for third-party beauty effects[self.trtcCloud setLocalVideoProcessDelegete:self pixelFormat:TRTCVideoPixelFormat_Texture_2D bufferType:TRTCVideoBufferType_Texture];#pragma mark - TRTCVideoFrameDelegate// Construct the YTProcessInput and pass it into the SDK for rendering processing.- (uint32_t)onProcessVideoFrame:(TRTCVideoFrame *_Nonnull)srcFrame dstFrame:(TRTCVideoFrame *_Nonnull)dstFrame {    if (!self.xMagicKit) {        [self buildBeautySDK:srcFrame.width and:srcFrame.height texture:srcFrame.textureId];// Initialize the XMagic SDK.        self.heightF = srcFrame.height;        self.widthF = srcFrame.width;    }    if(self.xMagicKit!=nil && (self.heightF!=srcFrame.height || self.widthF!=srcFrame.width)){       self.heightF = srcFrame.height;       self.widthF = srcFrame.width;       [self.xMagicKit setRenderSize:CGSizeMake(srcFrame.width, srcFrame.height)];    }    YTProcessInput *input = [[YTProcessInput alloc] init];    input.textureData = [[YTTextureData alloc] init];    input.textureData.texture = srcFrame.textureId;    input.textureData.textureWidth = srcFrame.width;    input.textureData.textureHeight = srcFrame.height;    input.dataType = kYTTextureData;    YTProcessOutput *output = [self.xMagicKit process:input withOrigin:YtLightImageOriginTopLeft withOrientation:YtLightCameraRotation0];    dstFrame.textureId = output.textureData.texture;    return 0;}
```

> **Note:**Step 1 and Step 2 vary depending on differing implementation methods of third-party beauty effect products, and **Step 3** is **a universal and important step** for RTC Engine's integration with third-party beauty effects.

### Dual-Stream Encoding Mode

When the dual-stream encoding mode is enabled, the current user's encoder outputs two video streams, a high-definition large screen and a low-definition small screen, at the same time (but only one audio stream). In this way, other users in the room can choose to subscribe to the high-definition large screen or low-definition small screen based on their network conditions or screen sizes.

1. Enable large-and-small-screen dual-stream encoding mode.

```
- (void)enableDualStreamMode:(BOOL)enable {    // Video encoding parameters for the small-screen stream (customizable).    TRTCVideoEncParam *smallVideoEncParam = [[TRTCVideoEncParam alloc] init];    smallVideoEncParam.videoResolution = TRTCVideoResolution_480_270;    smallVideoEncParam.videoFps = 15;    smallVideoEncParam.videoBitrate = 550;    smallVideoEncParam.resMode = TRTCVideoResolutionModePortrait;    [self.trtcCloud enableEncSmallVideoStream:enable withQuality:smallVideoEncParam];}
```

> **Note:**When the dual-stream encoding mode is enabled, it will consume more CPU and network bandwidth. Therefore, it may be considered for use on Mac, Windows, or high-performance Pads. It is not recommended for mobile devices.

2. Choose the type of remote user's video stream to pull.

```
// Optional video stream types when subscribing to a remote user's video stream.[self.trtcCloud startRemoteView:userId streamType:TRTCVideoStreamTypeBig view:view];// You can switch the size of the specified remote user's screen at any time.[self.trtcCloud setRemoteVideoStreamType:userId type:TRTCVideoStreamTypeSmall];
```

> **Note:**When the dual-stream encoding mode is enabled, you can specify the video stream type as `TRTCVideoStreamTypeSmall` with `streamType` to pull a low-quality small video for viewing.

### Viewing Rendering

If your business is involved in interaction scenarios that require switching display areas, you can use the RTC Engine SDK to update the local preview screen and the remote user's video rendering control feature.

```
// Update local preview screen rendering control.[self.trtcCloud updateLocalView:view];// Update the remote user's video rendering control.[self.trtcCloud updateRemoteView:view streamType:TRTCVideoStreamTypeBig forUser:userId];
```

> **Note:**The parameter `view` refers to the target video rendering control. And `streamType` only supports `TRTCVideoStreamTypeBig` and `TRTCVideoStreamTypeSub`.

### Live Streaming Interactive Messages

Live interaction is particularly important in live-streaming scenarios. Users interact with the anchor through [like messages](#11eee571-8277-4639-961d-34eba818a429), [gift messages](#3335554c-4b30-476c-8541-24553b2356bf), [bullet screen messages](#3335554c-4b30-476c-8541-24553b2356bf), and other methods. The precondition for implementing the live interaction feature is activating the [Chat](https://trtc.io/products/chat) service and importing the Chat SDK. For detailed directions, please refer to [Voice Room Integration Guide - Integration Preparation](#8b6b50a0-939d-48a1-aac1-58c6009e4b78).

#### Like Messages

1. The liker sends custom group messages related to likes through the client. After it is sended successfully, the business party renders the likes effect locally.

```
// Construct the likes message body.NSDictionary *msgDict = @{    @"type": @1,        // Like type    @"likeCount": @10   // Number of likes};NSDictionary *dataDict = @{    @"cmd": @"like_msg",    @"msg": msgDict};NSError *error;NSData *data = [NSJSONSerialization dataWithJSONObject:dataDict options:0 error:&error];// Send custom group messages (it is recommended that like messages should be set to low priority).[[V2TIMManager sharedInstance] sendGroupCustomMessage:data to:groupID priority:V2TIM_PRIORITY_LOW succ:^{    // Like messages sent successfully.    // Local rendering of likes effect.} fail:^(int code, NSString *desc) {    // Failed to send like messages.}];
```

2. Other users in the room receive callback for custom group messages. Then proceed with message parsing and likes effect rendering.

```
// Custom group messages received.[[V2TIMManager sharedInstance] addSimpleMsgListener:self];- (void)onRecvGroupCustomMessage:(NSString *)msgID groupID:(NSString *)groupID sender:(V2TIMGroupMemberInfo *)info customData:(NSData *)data {    if (data.length > 0) {        NSError *error;        NSDictionary *dataDict = [NSJSONSerialization JSONObjectWithData:data options:0 error:&error];        if (!error) {            NSString *command = dataDict[@"cmd"];            NSDictionary *msgDict = dataDict[@"msg"];            if ([command isEqualToString:@"like_msg"]) {                NSNumber *type = msgDict[@"type"];            // Likes type.                NSNumber *likeCount = msgDict[@"likeCount"];            // Number of likes.                // Render likes effect based on likes type and count.            }        } else {            NSLog(@"Parsing error: %@", error.localizedDescription);        }    }}
```

#### Gift Messages

1. The sender initiates a request to the business server. Upon completing the billing and settlement, the business server calls the [REST API](https://trtc.io/document/34959?product=chat&menulabel=core%20sdk&platform=ios) to send a custom message to the group.
  1.1. Example request URL.

```
https://xxxxxx/v4/group_open_http_svc/send_group_msg?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

  1.2. Request body example.

```
{    "GroupId": "@TGS#12DEVUDHQ",    "Random": 2784275388,    "MsgPriority": "High",  // The priority of the message. Gift messages should be set to high priority.    "MsgBody": [        {            "MsgType": "TIMCustomElem",             "MsgContent": {                // type: gift type; giftUrl: gift resource URL; giftName: gift name; giftCount: number of gifts.                "Data": "{\\"cmd\\": \\"gift_msg\\", \\"msg\\": {\\"type\\": 1, \\"giftUrl\\": \\"xxx\\", \\"giftName\\": \\"xxx\\", \\"giftCount\\": 1}}"            }        }    ]}
```

2. Other users in the room receive a callback for custom group messages. Then proceed with message parsing and gift effect rendering.

```
// Custom group messages received.[[V2TIMManager sharedInstance] addSimpleMsgListener:self];- (void)onRecvGroupCustomMessage:(NSString *)msgID groupID:(NSString *)groupID sender:(V2TIMGroupMemberInfo *)info customData:(NSData *)data {    if (data.length > 0) {        NSError *error;        NSDictionary *dataDict = [NSJSONSerialization JSONObjectWithData:data options:0 error:&error];        if (!error) {            NSString *command = dataDict[@"cmd"];            NSDictionary *msgDict = dataDict[@"msg"];            if ([command isEqualToString:@"gift_msg"]) {                NSNumber *type = msgDict[@"type"];            // Gift type.                NSNumber *giftCount = msgDict[@"giftCount"];  // Number of gifts.                NSString *giftUrl = msgDict[@"giftUrl"];      // Gift resource URL.                NSString *giftName = msgDict[@"giftName"];    // Gift name.                // Render gift effects based on gift type, count, resource URL, and name.            }        } else {            NSLog(@"Parsing error: %@", error.localizedDescription);        }    }}
```

#### Bullet Screen Messages

Live streaming rooms usually provide text-based bullet screen message interactions, which can be achieved by sending and receiving group chat plain text messages through Chat.

```
// Send public screen bullet screen messages.[[V2TIMManager sharedInstance] sendGroupTextMessage:text to:groupID priority:V2TIM_PRIORITY_NORMAL succ:^{    // Successfully sent bullet screen messages.    // Local display of the message text.} fail:^(int code, NSString *desc) {    // Failed to send bullet screen messages.}];// Receive public screen bullet screen messages.[[V2TIMManager sharedInstance] addSimpleMsgListener:self];- (void)onRecvGroupTextMessage:(NSString *)msgID groupID:(NSString *)groupID sender:(V2TIMGroupMemberInfo *)info text:(NSString *)text {    // Rendering bullet screen messages based on sender info and message text.}
```

> **Note:**The recommended priority setting is as follows. Gift messages should be set to high priority. Bullet screen messages should be set to medium priority. Like messages should be set to low priority.Sending group chat messages from the client will not trigger the message reception callback. Only other users within the group can receive them.

## Exception Handling

### Exception Handling

When the RTC Engine SDK encounters an unrecoverable error, the error is thrown in the `onError` callback. For details, see [Error Code Table](https://trtc.io/document/35130?product=rtcengine&menulabel=core%20sdk&platform=ios#336ef58d7636c75f9aa0c87753e08e7c).

1. UserSig related. UserSig verification failure can cause room entry failure. You can use the [UserSig tool](https://console.trtc.io/usersig)for verification.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_INVALID_USER_SIG | -3320 | Room entry parameter userSig is incorrect. Check if `TRTCParams.userSig` is empty. |
| ERR_TRTC_USER_SIG_CHECK_FAILED | -100018 | UserSig verification failed. Check if the parameter `TRTCParams.userSig` is filled in correctly or has expired. |

2. Check-in/out related. If failed to enter the room, please first check whether the parameters are correct. The room entry and exit API must be called in a paired manner. The room exit API must be called even after failed room entry.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_CONNECT_SERVER_TIMEOUT | -3308 | Room entry request timed out. Check if your internet connection is lost or if a VPN is enabled. You may also attempt to switch to 4G for testing. |
| ERR_TRTC_INVALID_SDK_APPID | -3317 | Room entry parameter sdkAppId is incorrect. Check if `TRTCParams.sdkAppId` is empty. |
| ERR_TRTC_INVALID_ROOM_ID | -3318 | Room entry parameter roomId is incorrect. Check if `TRTCParams.roomId` or `TRTCParams.strRoomId` is empty. Note that roomId and strRoomId cannot be used interchangeably. |
| ERR_TRTC_INVALID_USER_ID | -3319 | Room entry parameter userId is incorrect. Check if `TRTCParams.userId` is empty. |
| ERR_TRTC_ENTER_ROOM_REFUSED | -3340 | Room entry request is denied. Check if `enterRoom` is called consecutively to enter rooms with the same ID. |

3. Device-related. Errors for monitoring devices. In case of relevant errors, prompt the user via UI.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_CAMERA_START_FAIL | -1301 | Failed to open the camera. For example, if there is an exception for the camera's configuration program (driver) on a Windows or macOS device, you should try disabling then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_MIC_START_FAIL | -1302 | Failed to open the mic. For example, if there is an exception for the mic's configuration program (driver) on a Windows or macOS device, you should try disabling then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_CAMERA_NOT_AUTHORIZED | -1314 | The device of camera is unauthorized. This typically occurs on mobile devices and may be due to the user having denied the permission. |
| ERR_MIC_NOT_AUTHORIZED | -1317 | The device of mic is unauthorized. This typically occurs on mobile devices and may be due to the user having denied the permission. |
| ERR_CAMERA_OCCUPY | -1316 | The camera is occupied. Try a different camera. |
| ERR_MIC_OCCUPY | -1319 | The mic is occupied. This occurs when, for example, the user is currently having a call on the mobile device. |

### Remote Mirror Mode Not Functioning Properly

In RTC Engine, video mirrors are set to be divided into local preview mirror `setLocalRenderParams` and video encoding mirror `setVideoEncoderMirror`. These mirrors separately affect the mirror effect of the local preview video and that of the video encoding output video (the mirror mode for remote audiences and on-cloud recordings). If you expect the mirror effect seen in the local preview to also take effect on the remote audiences' end, follow the following encoding procedures.

```
// Set the rendering parameters for the local video.TRTCRenderParams *params = [[TRTCRenderParams alloc] init];params.mirrorType = TRTCVideoMirrorTypeEnable; // Video mirror modeparams.fillMode = TRTCVideoFillMode_Fill; // Video fill modeparams.rotation = TRTCVideoRotation_0; // Video rotation angle[self.trtcCloud setLocalRenderParams:params];// Set the video mirror mode for the encoder output.[self.trtcCloud setVideoEncoderMirror:YES];
```

### Adjustment of Camera Scale, Focus, and Switch

In live showroom scenarios, the anchor may need custom adjustment of the camera. The RTC Engine SDK's device management class provides APIs for such needs.

1. Query and set the zoom factor for the camera.

```
// Get the maximum zoom factor for the camera (only for mobile devices).CGFloat zoomRatio = [[self.trtcCloud getDeviceManager] getCameraZoomMaxRatio];// Set the zoom factor for the camera (only for mobile devices).// Value range is 1 - 5. 1 means the furthest field of view (normal lens), and 5 means the closest field of view (zoom lens). The maximum recommended value is 5, exceeding this may result in blurry video.[[self.trtcCloud getDeviceManager] setCameraZoomRatio:zoomRatio];
```

2. Set the focus feature and position of the camera.

```
// Enable or disable the camera's autofocus feature (only for mobile devices).[[self.trtcCloud getDeviceManager] enableCameraAutoFocus:NO];// Set the focus position of the camera (only for mobile devices).// The precondition for using this API is to first disable the autofocus feature using enableCameraAutoFocus.[[self.trtcCloud getDeviceManager] setCameraFocusPosition:CGPointMake(x, y)];
```

3. Determine and switch to front or rear cameras.

```
// Determine if the current camera is the front camera (only for mobile devices).BOOL isFrontCamera = [[self.trtcCloud getDeviceManager] isFrontCamera];// Switch to front or rear cameras (only for mobile devices).// Passing true means switching to front, and passing false means switching to rear.[[self.trtcCloud getDeviceManager] switchCamera:!isFrontCamera];
```


---
*Source: [https://trtc.io/document/73425](https://trtc.io/document/73425)*
