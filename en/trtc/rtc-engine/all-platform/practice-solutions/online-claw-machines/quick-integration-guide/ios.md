# iOS

## Implementation Workflow

This section summarizes some common business processes in online claw machines to help you better understand the implementation of the entire scenario.

Online Claw Machine TRTC Streaming

Online Claw Machine RTMP Streaming

The diagram below illustrates the sequence of RTC Engine streaming for an online claw machine, including processes such as RTC Engine streaming from a network camera and user-side stream pulling.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4cc86691dbb811f0b31e5254007c27c5.png)

The diagram below illustrates the sequence of RTMP streaming for an online claw machine, including processes such as RTMP streaming from a network camera and user-side stream pulling.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/28011949dc0311f09143525400bf7822.png)

## Integration Preparation

### Step 1: Activate the Service

The online claw machine scenario typically relies on the paid PaaS service of [RTC Engine](https://trtc.io/document/rtc-engine-overview?product=rtcengine&menulabel=core%20) for implementation. RTC Engine provides real-time audio and video interaction capabilities. You can choose to activate the service based on your specific business requirements.

1. Log in to the [RTC Engine console](https://console.trtc.io/app), then click **Create application** on the **Applications** page. You can choose to upgrade the RTC Engine application edition as needed. For example, upgrading to the Pro Edition includes additional value-added feature services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7d111e09dbb711f0b45152540099c741.jpg)

> **Note:**It is recommended to create two separate applications for the test environment and the production environment. The first activation of RTC Engine includes a free 10,000-minute trial package.The RTC Engine monthly packages (Free Trial, Lite, Standard, and Pro packages) offer different value-added feature services. For details, see [RTC Engine Monthly Packages](https://trtc.io/document/56025?product=pricing#f10b65d1-6e8d-41e3-8686-84909b00a1a2).

2. After creating the application, you can view its basic information in [Application Management](https://console.trtc.io/app) > **Application Overview**. Keep your **SDKAppID** and **SDKSecretKey** secure for future use, and take precautions to prevent key leakage that may result in unauthorized traffic usage.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8053d86ddbb711f09dea52540044a08e.png)

### Step 2: Import SDK

The RTC Engine SDK has been released to the **CocoaPods** repository. You can integrate the SDK through CocoaPods.

1. Install CocoaPods.

Run the following command in a terminal window to install CocoaPods. If you have completed the CocoaPods installation, skip this step.

```
sudo gem install cocoapods
```

2. Create a Podfile file.

Navigate to your project directory and run the following command. A Podfile file will then be created in the project directory.

```
pod init
```

3. Edit the Podfile file.

Choose the appropriate version for your project and edit the Podfile file.

```
platform :ios, '8.0'target 'App' do# RTC Engine Lite Edition (Recommended)# Minimum incremental size of the installation package. Only the RTC Engine and TXLivePlayer features are supported.pod 'TXLiteAVSDK_TRTC', :podspec => 'https://liteav.sdk.qcloud.com/pod/liteavsdkspec/TXLiteAVSDK_TRTC.podspec'# LiteAVSDK Professional Edition# A number of features, such as RTC Engine, TXLivePlayer, TXLivePusher, TXVodPlayer, and UGSV, are supported.pod 'TXLiteAVSDK_Professional', :podspec => 'https://liteav.sdk.qcloud.com/pod/liteavsdkspec/TXLiteAVSDK_Professional.podspec'end
```

4. Update and install the SDK.

Enter the following command in the terminal window to update the local repository files and install the SDK.

```
pod install
```

Or run the following command to update the local repository.

```
pod update
```

After the pod command is executed, an .xcworkspace project file integrated with the SDK will be generated. Double-click to open the file.

> **Note:**If the pod search fails, it is recommended to try updating the local repo cache of pod. The update command is as follows:pod setuppod repo updaterm ~/Library/Caches/CocoaPods/search_index.json

### Step 3: Project Configuration

1. In the online claw machine scenario, the RTC Engine SDK requires app authorization for microphone and camera permissions. Add the following content to the Info.plist of the app, and the corresponding microphone and camera prompts will be displayed in the system pop-up authorization dialog box.

```
Privacy - Microphone Usage Description. Enter a prompt specifying the purpose of microphone use.Privacy - Camera Usage Description. Enter a prompt specifying the purpose of camera use.
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8c4daafddc0311f0a6e3525400e889b2.png)

2. To allow the app to continue running certain features in the backend, select the current project in Xcode, set the setting item Background Modes to ON under Capabilities, and select Audio, AirPlay, and Picture in Picture, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/904dbc80dc0311f08a7a52540099c741.png)

### Step 4: Perform Authentication and Authorization

UserSig is a security protection signature designed by TRTC to prevent malicious attackers from misappropriating your cloud service usage rights. RTC Engine validates this authentication credential when entering a room.

- Debugging phase: You can generate the UserSig using either the [Client Sample Code](https://trtc.io/document/35166?product=conference&menulabel=uikit&platform=web) or the [Console Access](https://console.trtc.io/usersig). This method is intended solely for debugging and testing purposes.
- Production stage: It is recommended to use the server-side computation scheme for UserSig with a higher security level to prevent client-side reverse engineering and key leakage.

Implementation process:

1. Before calling the initialization API of the SDK, your application must first request a UserSig from your server.
2. Your server generates the UserSig based on the SDKAppID and UserID.
3. The server returns the generated UserSig to your app.
4. Your app sends the obtained UserSig to the SDK through the designated API.
5. The SDK submits the SDKAppID + UserID + UserSig to the TRTC server for verification.
6. TRTC verifies the validity of the UserSig.
7. After the verification is passed, the RTC Engine SDK will be provided with real-time audio and video services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8a98989cdbb711f0809c525400454e06.jpeg)

> **Note:**The method of generating UserSig locally during the debugging and testing stage is not recommended for the production environment because it may be easily decompiled and reversed, causing key leakage.We provide UserSig server generation source code in multiple languages (Java/Go/PHP/Nodejs/Python/C#/C++). For details, see [UserSig Generation Source Code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk#formal).

### Step 5: Initialize the SDK

```
// Create an RTC Engine SDK instance (singleton mode).self.trtcCloud = [TRTCCloud sharedInstance];// Set an event listener.self.trtcCloud.delegate = self;// Notifications from various SDK events (including error codes, warning codes, and audio and video status parameters).- (void)onError:(TXLiteAVError)errCode errMsg:(nullable NSString *)errMsg extInfo:(nullable NSDictionary *)extInfo {    NSLog(@"%d: %@", errCode, errMsg);}- (void)onWarning:(TXLiteAVWarning)warningCode warningMsg:(nullable NSString *)warningMsg extInfo:(nullable NSDictionary *)extInfo {    NSLog(@"%d: %@", warningCode, warningMsg);}// Remove the event listener.self.trtcCloud.delegate = nil;// Terminate the RTC Engine SDK instance (singleton mode).[TRTCCloud destroySharedIntance];
```

> **Note:**It is recommended to listen to SDK event notifications. Perform log printing and handling for some common errors. For details, see [Error Code Table](https://trtc.io/document/54573?product=rtcengine&menulabel=core%20sdk&platform=ios).

### Step 6: Generate RTMP Streaming Address (RTMP Streaming)

Generate the RTMP streaming address.

```
rtmp://intl-rtmp.rtc.qq.com/push/roomID?sdkappid=application&userid=username&usersig=signature
```

- intl-rtmp.rtc.qq.comï¼The primary domain name.
- rtmp.rtc-web.comï¼The secondary domain name.

If there are issues with the primary domain name parsing, you can use the secondary domain name.

- push: The RTMP appName.
- Replace roomId, appId, username, and signature with your business-specific values.
- To simplify parameters, only string room IDs are supported, up to 64 characters, including numbers, letters, or underscores.

> **Note:**If other RTC Engine endpoints need to watch the RTMP stream, use the **string room ID for room entry**.

- For the UserSig generation rules, see [UserSig](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk) (**The signature is valid)**.

**Example:**

```
rtmp://intl-rtmp.rtc.qq.com/push/hello-string-room?sdkappid=140**66&userid=rtmp2&usersig=eJw1jdERBZ8qKGRj8Yp-wVbvmGMVZqS7w-mMDQL
```

## Integration Process

### API Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/910a9e68dbb711f0809c525400454e06.jpg)

### Step 1: Claw Machine Streaming

#### RTC Engine Streaming

1. Calculate and generate the UserSig using either the [client example code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk) or the [console](https://console.trtc.io/usersig).
2. Configure the SdkAppid, UserID, UserSig, RoomId, and other information on the RTC Engine network camera or streaming box to start streaming.

> **Note:**RTC Engine room IDs are divided into numeric type `roomId` and string type `strRoomId`. The rooms of these two types are not interconnected. It is recommended to unify the room ID type.RTC Engine user roles are divided into anchors and audiences. Only hosts have streaming permissions. The user role should be specified upon room entry. If the user role is not specified, the default role is anchor.For the online claw machine scenario, it is recommended to use the `TRTC_APP_SCENE_VIDEOCALL` mode for entering a room, as it ensures lower latency.

#### **RTMP Streaming**

1. Use the [RTMP Address Generator](https://console.trtc.io/rtmptool) to generate an RTMP streaming address.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ba377bd8b30c11f09e195254007c27c5.png)

2. Configure the RTMP streaming address on the RTMP network camera or streaming box to start streaming.

### Step 2: Enter a Room and Play Streams

1. User enters RTC Engine room.

```
- (void)enterRoomByAudienceWithUserId:(NSString *)userId roomId:(NSString *)roomId {    TRTCParams *params = [[TRTCParams alloc] init];    // Take a string room ID as an example.    params.strRoomId = roomId;    params.userId = userId;    // UserSig obtained from the business backend.    params.userSig = @"userSig";    // Replace with your SDKAppID.    params.sdkAppId = 0;    // Specify the audience role.    params.role = TRTCRoleAudience;    // Enter the room in an interactive live streaming scenario.    [self.trtcCloud enterRoom:params appScene:TRTCAppSceneVideoCall];}// Event callback for the result of entering the room.- (void)onEnterRoom:(NSInteger)result {    if (result > 0) {        // The result indicates the time taken (in milliseconds) to join the room.        NSLog(@"Enter room succeed!");    } else {        // The result indicates the error code for a room entry failure.        NSLog(@"Enter room failed!");    }}
```

2. User subscribes to hostâs audio and video stream.

```
- (void)onUserAudioAvailable:(NSString *)userId available:(BOOL)available {    // The remote user publishes/unpublishes the audio.    // In the automatic subscription mode, you do not need to do anything. The SDK will automatically play the audio of the remote user.}- (void)onUserVideoAvailable:(NSString *)userId available:(BOOL)available {    // The remote user publishes/unpublishes the primary video.    if (available) {        // Subscribe to the video stream of the remote user and bind the video rendering control.        [self.trtcCloud startRemoteView:userId streamType:TRTCVideoStreamTypeBig view:self.remoteView];    } else {        // Unsubscribe to the video stream of the remote user and release the rendering control.        [self.trtcCloud stopRemoteView:userId streamType:TRTCVideoStreamTypeBig];    }}
```

3. Audience sets the rendering mode for the remote video (optional).

```
- (void)setupRemoteRenderParams {    TRTCRenderParams *params = [[TRTCRenderParams alloc] init];    // Video mirror mode.    params.mirrorType = TRTCVideoMirrorTypeAuto;    // Video fill mode.    params.fillMode = TRTCVideoFillMode_Fill;    // Video rotation angle.    params.rotation = TRTCVideoRotation_0;    // Set the rendering mode for the remote video.    [self.trtcCloud setRemoteRenderParams:@"userId" streamType:TRTCVideoStreamTypeBig params:params];}
```

### Step 3: Exit Room

1. User exits the room.

```
- (void)exitRoom {    [self.trtcCloud stopLocalAudio];    [self.trtcCloud stopLocalPreview];    [self.trtcCloud exitRoom];}// Event callback for exiting the room.- (void)onExitRoom:(NSInteger)reason {    if (reason == 0) {        NSLog(@"Actively call exitRoom to exit the room.");    } else if (reason == 1) {        NSLog(@"Removed from the current room by the server.");    } else if (reason == 2) {        NSLog(@"The current room has been dissolved.");    }}
```

> **Note:**After all resources occupied by the SDK are released, the SDK will throw the `onExitRoom` callback notification to inform you.If you want to call `enterRoom` again or switch to another audio and video SDK, wait for the `onExitRoom` callback before proceeding. Otherwise, you may encounter various exceptional issues such as camera, microphone device being forcibly occupied.

2. Dissolve room.
  - **Server-side Dissolve Room.**

RTC Engine provides the server-side API [DismissRoom](https://trtc.io/document/34269?product=rtcengine&menulabel=core%20) for dissolving rooms with numeric types and the API [DismissRoomByStrRoomId](https://trtc.io/zh/document/39631?product=rtcengine&menulabel=core%20sdk) for dissolving rooms with string types. You can use these server-side APIs to remove all users from the room and dissolve the room.

  - **Client-side Dissolve Room.**

The client does not provide an API for directly dissolving a room. Each client should call [exitRoom](https://trtc.io/zh/document/50762?platform=android&product=rtcengine&menulabel=core%20sdk#4651ae2c9ff5aa99442102e0d77a8606) to exit the room. Once all anchors and audiences have exited the room, the room will be automatically dissolved according to the RTC Engine room lifecycle rules. For details, see [RTC Engine Exit the Room](https://trtc.io/zh/document/62045?product=rtcengine&menulabel=core%20sdk&platform=android#5055ad66-53b1-4539-88ec-6992d45bb0fd).

## Exception Handling

### Error Handling

RTC Engine SDK throws unrecoverable errors in the `onError` callback. For details, see [RTC Engine Error Codes](https://trtc.io/zh/document/54573?product=rtcengine&menulabel=core%20sdk&platform=ios).

1. UserSig related.

UserSig verification failure can lead to room entry failure. You can use the [UserSig tool for verification](https://console.trtc.io/usersig).

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_INVALID_USER_SIG | -3320 | Enter Room parameter UserSig is incorrect. Please Check if `TRTCParams.userSig` is empty. |
| ERR_TRTC_USER_SIG_CHECK_FAILED | -100018 | UserSig verification failed. Please check if `TRTCParams.userSig` is correct or expired. |

2. Enter or Exit Room related.

If entering room fails, first check whether the room entry parameters are correct. The room entry and exit APIs should be called in pairs. This

means that even if room entry fails, the room exit API should still be called.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_CONNECT_SERVER_TIMEOUT | -3308 | Enter Room request timed out. Check if your internet connection is lost or if a VPN is enabled. You may also attempt to switch to 4G for testing. |
| ERR_TRTC_INVALID_SDK_APPID | -3317 | Enter Room parameter sdkAppId is incorrect. Check if `TRTCParams.sdkAppId` is empty. |
| ERR_TRTC_INVALID_ROOM_ID | -3318 | Enter Room parameter roomId is incorrect. Check if `TRTCParams.roomId` or `TRTCParams.strRoomId` is empty. Note that roomId and strRoomId cannot be used interchangeably. |
| ERR_TRTC_INVALID_USER_ID | -3319 | Enter Room parameter userId is incorrect. Check if `TRTCParams.userId` is empty. |
| ERR_TRTC_ENTER_ROOM_REFUSED | -3340 | Enter Room request was refused. Check if `enterRoom` is called consecutively to enter a room with the same ID. |

3. Device related.

Device-related errors can be monitored. Users are prompted via UI if related errors occur.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_CAMERA_START_FAIL | -1301 | Failed to turn the camera on. For example, if there is an exception for the camera's configuration program (driver) on a Windows or Mac device, you should try disabling then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_MIC_START_FAIL | -1302 | Failed to turn the mic on. For example, if there is an exception for the microphone's configuration program (driver) on a Windows or Mac device, you should try disabling and then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_CAMERA_NOT_AUTHORIZED | -1314 | The camera is unauthorized. This typically occurs on mobile devices, probably because the user denied the permission. |
| ERR_MIC_NOT_AUTHORIZED | -1317 | The microphone is unauthorized. This typically occurs on mobile devices, probably because the user denied the permission. |
| ERR_CAMERA_OCCUPY | -1316 | The camera is occupied. Try a different camera. |
| ERR_MIC_OCCUPIED | -1319 | The microphone is occupied. For example, when the user is currently having a call on a mobile device, the microphone cannot be turned on. |

### Black Screen During Playback

In RTMP claw machine streaming scenarios, RTMP streaming successfully enters the RTC Engine room, but playback fails. The issue occurs because the streaming configuration includes B-frames, which are not supported by RTC Engine rooms, resulting in failed RTMP stream playback. Example streaming configuration:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a062b70bdbb711f0b45152540099c741.png)

### Audience Playback Stuck

In claw machine scenarios, when an RTC Engine audience enters a room and plays back for a period of time, playback may freeze, especially after multiple peer-join or onUserVideoAvailable callbacks. The audience's playback screen may freeze on the last frame. If this occurs, first check the dashboard for detailed call information. If the dashboard shows that the host has entered and exited the room multiple times, the issue is likely due to mutual kicking. Dashboard example:

****

**Solution**: You can try disabling the streaming on the current machine to resolve the issue. If the issue remains unresolved, then check whether 2 identical streaming addresses are configured on the same machine.


---
*Source: [https://trtc.io/document/77217](https://trtc.io/document/77217)*
