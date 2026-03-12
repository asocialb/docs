# Android

## Implementation Workflow

This section summarizes some common business processes in online claw machines to help you better understand the implementation of the entire scenario.

Online Claw Machine TRTC Streaming

Online Claw Machine RTMP Streaming

The diagram below illustrates the sequence of RTC Engine streaming for an online claw machine, including processes such as RTC Engine streaming from a network camera and user-side stream pulling.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/55b3a3dc412a11f0b95f5254005ef0f7.png)

The diagram below illustrates the sequence of RTMP streaming for an online claw machine, including processes such as RTMP streaming from a network camera and user streaming pull.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ab6ec8be412b11f0912c52540044a08e.png)

## Integration Preparation

### Step 1: Activate the Service

The online claw machine scenario typically relies on the paid PaaS service of [RTC Engine](https://trtc.io/document/rtc-engine-overview?product=rtcengine&menulabel=core%20) for implementation. RTC Engine provides real-time audio and video interaction capabilities. You can choose to activate the service based on your specific business requirements.

1. Log in to the [RTC Engine console](https://console.trtc.io/app), then click **Create application** on the **Applications** page. You can choose to upgrade the RTC Engine application edition as needed. For example, upgrading to the Pro Edition includes additional value-added feature services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/35d91cd4412c11f0aa86525400e889b2.jpg)

> **Note:**It is recommended to create two separate applications for the test environment and the production environment. The first activation of RTC Engine includes a free 10,000-minute trial package.The RTC Engine monthly packages (Free Trial, Lite, Standard, and Pro packages) offer different value-added feature services. For details, see [RTC Engine Monthly Packages](https://trtc.io/document/56025?product=pricing#f10b65d1-6e8d-41e3-8686-84909b00a1a2).

2. After creating the application, you can view its basic information in [Application Management](https://console.trtc.io/app) > **Application Overview**. Keep your **SDKAppID** and **SDKSecretKey** secure for future use, and take precautions to prevent key leakage that may result in unauthorized traffic usage.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9f4af2e3412a11f0912c52540044a08e.png)

### Step 2: Import the SDK

The RTC Engine SDK has been released to the **mavenCentral** repository. You can configure Gradle for automatic download and update the SDK.

1. Add the dependency for the appropriate version of the SDK in dependencies.

```
// RTC Engine SDK for the Lite Edition, including two features, that is, RTC and live streaming playback.dependencies {    implementation 'com.tencent.liteav:LiteAVSDK_TRTC:latest.release'}
```

> **Note:**For the automatic loading (aar) scheme, ensure that you have added the mavenCentral repository in your `repositories`.

2. Specify the CPU architecture used by the app in defaultConfig.

```
defaultConfig {     ndk {             abiFilters "armeabi-v7a", "arm64-v8a"     }}
```

### Step 3: Project Configuration

1. Permission configuration.

Set the required app permissions in AndroidManifest.xml, LiteAVSDK requires the following permissions for the online claw machine scenario:

```
<uses-permission android:name="android.permission.INTERNET" /><uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /><uses-permission android:name="android.permission.ACCESS_WIFI_STATE" /><uses-permission android:name="android.permission.RECORD_AUDIO" /><uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" /><uses-permission android:name="android.permission.BLUETOOTH" /><uses-permission android:name="android.permission.CAMERA" /><uses-feature android:name="android.hardware.camera.autofocus" />
```

> **Note:**Do not set `android:hardwareAccelerated="false"`. Disabling hardware acceleration will result in failure to render remote video streams.LiteAVSDK does not have built-in permission request logic, so you need to declare the corresponding permissions yourself. Some permissions (such as storage, recording and camera) also require runtime dynamic requests.If the Android projectâs `targetSdkVersion` is 31 or the target device runs Android 12 or higher, it is mandatory to dynamically request the `android.permission.BLUETOOTH_CONNECT` permission in the code to ensure proper Bluetooth feature. For more details, see [Android Official Documentation](https://developer.android.google.cn/develop/connectivity/bluetooth/bt-permissions).

2. Obfuscate configuration.

Java's reflection is used inside the SDK, so you need to add the relevant SDK classes to the non-obfuscation list in the proguard-rules.pro file:

```
-keep class com.tencent.** { *; }
```

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

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e1e8a51e412a11f0be2052540099c741.jpeg)

> **Note:**The method of generating UserSig locally during the debugging and testing stage is not recommended for the production environment because it may be easily decompiled and reversed, causing key leakage.We provide UserSig server generation source code in multiple languages (Java/GO/PHP/Nodejs/Python/C#/C++). For details, see [UserSig Generation Source Code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk#formal).

### Step 5: Initialize the SDK

```
// Create an RTC Engine SDK instance (singleton mode).TRTCCloud mTRTCCloud = TRTCCloud.sharedInstance(context);// Set an event listener.mTRTCCloud.setListener(trtcSdkListener);// Notifications from various SDK events (e.g., error codes, warning codes, audio and video status parameters, etc.).private TRTCCloudListener trtcSdkListener = new TRTCCloudListener() {    @Override    public void onError(int errCode, String errMsg, Bundle extraInfo) {        Log.d(TAG, errCode + errMsg);    }        @Override    public void onWarning(int warningCode, String warningMsg, Bundle extraInfo) {        Log.d(TAG, warningCode + warningMsg);    }};// Remove the event listenermTRTCCloud.setListener(null);// Terminate the TRTC SDK instance (singleton mode).TRTCCloud.destroySharedInstance();
```

> **Note:**It is recommended to listen to SDK events notifications. Perform log printing and handling for some common errors. For details, see [Error Code Table](https://trtc.io/document/35130?product=rtcengine&menulabel=core%20sdk&platform=android).

### Step 6: Generate RTMP Streaming Address (RTMP Streaming)

Generate the RTMP streaming address.

```
rtmp://intl-rtmp.rtc.qq.com/push/roomID?sdkappid=application&userid=username&usersig=signature
```

- intl-rtmp.rtc.qq.com: The primary domain name.
- rtmp.rtc-web.com: The secondary domain name.

If there are issues with the primary domain name parsing, you can use the secondary domain name.

- push: The RTMP appName.
- Replace roomId, appId, username, and signature with your business-specific values.
- To simplify parameters, only string room IDs are supported,up to 64 characters, including numbers, letters, or underscores.

> **Note:**If other RTC Engine endpoints need to watch the RTMP stream, use the **string room ID for room entry**.

- For UserSig generation rules, see [UserSig](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk) (**The signature is valid)**.

**Example:**

```
rtmp://intl-rtmp.rtc.qq.com/push/hello-string-room?sdkappid=140**66&userid=rtmp2&usersig=eJw1jdERBZ8qKGRj8Yp-wVbvmGMVZqS7w-mMDQL
```

## Integration Process

### API Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/52a36460412b11f0912c52540044a08e.jpg)

### Step 1: Claw Machine Streaming

#### RTC Engine Streaming

1. Calculate and generate UserSig using either the [client sample code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk) or the [console](https://console.trtc.io/usersig).
2. Configure the SdkAppID, UserID, UserSig, RoomID, and other information on the RTC Engine network camera or streaming box to start streaming.

> **Note:**RTC Engine room IDs are divided into numeric type `roomID` and string type `strRoomID`. The rooms of these two types are not interconnected. It is recommended to unify the room ID type.RTC Engine user roles are divided into hosts and audiences. Only hosts have streaming permissions. The user role should be specified when entering the room. If the user role is not specified, the default role is host.For the online claw machine scenario, it is recommended to use the `TRTC_APP_SCENE_VIDEOCALL` mode for entering a room, as it ensures lower latency.

#### **RTMP Streaming**

1. Use the [RTMP Address Generator](https://console.trtc.io/rtmptool) to generate the RTMP streaming address.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/03ec4abec2b111efb6165254001c06ec.png)

2. Configure the RTMP streaming address to the RTMP network camera or streaming box to start streaming.

### Step 2: Enter a Room and Play Streams

1. User enters RTC Engine room.

```
public void enterRoomByAudience(String roomId, String userId) {    TRTCCloudDef.TRTCParams params = new TRTCCloudDef.TRTCParams();    // Take the room ID string as an example.    params.strRoomId = roomId;    params.userId = userId;    // UserSig obtained from the business backend.    params.userSig = getUserSig(userId);    // Replace with your SDKAppID.    params.sdkAppId = SDKAppID;    mTRTCCloud.enterRoom(params, TRTCCloudDef.TRTC_APP_SCENE_VIDEOCALL);}// Event callback for the result of entering the room.@Overridepublic void onEnterRoom(long result) {    if (result > 0) {        // The result represents the time taken to join the room (in milliseconds).        Log.d(TAG, "Enter room succeed");    } else {        // The result represents the error code when you fail to enter the room.        Log.d(TAG, "Enter room failed");    }}
```

2. User subscribes to hostâs audio and video stream.

```
@Overridepublic void onUserAudioAvailable(String userId, boolean available) {    // The remote user publishes/unpublishes the audio.    // Under the automatic subscription mode, you do not need to do anything. The SDK will automatically play the remote user's audio.}@Overridepublic void onUserVideoAvailable(String userId, boolean available) {    // The remote user publishes/unpublishes the primary video.    if (available) {        // Subscribe to the remote user's video stream and bind the video rendering control.        mTRTCCloud.startRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, TXCloudVideoView view);    } else {        // Unsubscribe to the remote user's video stream and release the rendering control.        mTRTCCloud.stopRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);    }}
```

3. Audience sets the rendering mode for the remote video (optional).

```
TRTCCloudDef.TRTCRenderParams params = new TRTCCloudDef.TRTCRenderParams();params.mirrorType = TRTCCloudDef.TRTC_VIDEO_MIRROR_TYPE_AUTO;   // Video mirror mode.params.fillMode = TRTCCloudDef.TRTC_VIDEO_RENDER_MODE_FILL; // Video fill mode.params.rotation = TRTCCloudDef.TRTC_VIDEO_ROTATION_0;           // Video rotation angle.// Set the rendering mode for the remote video.mTRTCCloud.setRemoteRenderParams(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, params)
```

### Step 3: Exit Room

1. User exits the room.

```
public void exitRoom() {    mTRTCCloud.stopLocalAudio();    mTRTCCloud.stopLocalPreview();    mTRTCCloud.exitRoom();}// Event callback for exiting the room.@Overridepublic void onExitRoom(int reason) {    if (reason == 0) {        Log.d(TAG, "Actively call exitRoom to exit the room.");    } else if (reason == 1) {        Log.d(TAG, "Removed from the current room by the server.");    } else if (reason == 2) {        Log.d(TAG, "The current room has been dissolved.");    }}
```

> **Note:**After all resources occupied by the SDK are released, the SDK will throw the `onExitRoom` callback notification to inform you.If you need to call `enterRoom` again or switch to another audio and video SDK, wait for the `onExitRoom` callback before proceeding. Otherwise, you may encounter various exceptional issues such as camera, microphone device being forcibly occupied.

2. Dissolve room.
  - **Server-side Dissolve Room.**

RTC Engine provides the server-side API [`DismissRoom`](https://trtc.io/document/34269?product=rtcengine&menulabel=core%20) for dissolving rooms with numeric types and the API [`DismissRoomByStrRoomId`](https://trtc.io/document/39631?product=rtcengine&menulabel=core%20sdk) for dissolving rooms with string types. You can use these server-side APIs to remove all users from the room and dissolve the room.

  - **Client-side Dissolve Room.**

The client does not provide an API for directly dissolving a room. Each client should call [`exitRoom`](https://trtc.io/document/50762?platform=android&product=rtcengine&menulabel=core%20sdk#4651ae2c9ff5aa99442102e0d77a8606) to exit the room. Once all anchors and audiences have exited the room, the room will be automatically dissolved according to the RTC Engine room lifecycle rules. For details, see [RTC Engine Exit the Room](https://trtc.io/document/62045?product=rtcengine&menulabel=core%20sdk&platform=android#5055ad66-53b1-4539-88ec-6992d45bb0fd).

## Exception Handling

### Error Handling

RTC Engine SDK throws unrecoverable errors in the `onError` callback. For details, see [RTC Engine Error Codes](https://trtc.io/document/35130?product=rtcengine&menulabel=core%20sdk&platform=android).

1. UserSig related.

UserSig verification failure will result in enter Room to failure.You can see [UserSig tool](https://console.trtc.io/usersig) for verification.

| Error Example | Value | Description |
| --- | --- | --- |
| ERR_TRTC_INVALID_USER_SIG | -3320 | Enter Room parameter UserSig is incorrect. Please check if `TRTCParams.userSig` is empty. |
| ERR_TRTC_USER_SIG_CHECK_FAILED | -100018 | UserSig verification failed. Please check if`TRTCParams.userSig` is correct or expired. |

2. Enter or Exit Room related.

If entering room fails, you should first verify the correctness of the room entry parameters. It is essential that the room entry and exit APIs are called in a paired manner. This means that, even in the event of a failed room entry, the room exit API must still be called.

| Error Example | Value | Description |
| --- | --- | --- |
| ERR_TRTC_CONNECT_SERVER_TIMEOUT | -3308 | Enter Room request timed out. Check for network disconnection or VPN. You can also try switching to 4G for testing. |
| ERR_TRTC_INVALID_SDK_APPID | -3317 | Enter Room parameter sdkAppId is incorrect. Check if `TRTCParams.sdkAppId` is empty |
| ERR_TRTC_INVALID_ROOM_ID | -3318 | Enter Room parameter roomId is incorrect. Check if `TRTCParams.roomId` or `TRTCParams.strRoomId` is empty. Note that roomId and strRoomId cannot be used interchangeably. |
| ERR_TRTC_INVALID_USER_ID | -3319 | Enter Room parameter userId is incorrect. Check if `TRTCParams.userId` is empty. |
| ERR_TRTC_ENTER_ROOM_REFUSED | -3340 | Enter Room request was refused. Check if`enterRoom` is called consecutively to enter rooms with the same ID. |

3. Device related.

Listen for device-related errors and notify users via the UI when they occur.

| Error Example | Value | Description |
| --- | --- | --- |
| ERR_CAMERA_START_FAIL | -1301 | Failed to turn the camera on. For example, if there is an exception for the camera's configuration program (driver) on a Windows or Mac device, you should try disabling then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_MIC_START_FAIL | -1302 | Failed to turn the microphone on. For example, if there is an exception for the microphone's configuration program (driver) on a Windows or Mac device, you should try disabling and then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_CAMERA_NOT_AUTHORIZED | -1314 | Camera device not authorized. This typically occurs on mobile devices, probably because the user denied the permission. |
| ERR_MIC_NOT_AUTHORIZED | -1317 | Microphone device not authorized. This typically occurs on mobile devices, probably because the user denied the permission. |
| ERR_CAMERA_OCCUPY | -1316 | Camera is currently occupied. Try opening another camera. |
| ERR_MIC_OCCUPY | -1319 | Microphone is currently occupied. For example, when the user is currently having a call on a mobile device, the microphone cannot be turned on. |

### Black Screen During Playback

In RTMP claw machine streaming scenarios, RTMP streaming successfully enters the RTC Engine room, but playback fails. The issue occurs because the streaming configuration includes B-frames, which are not supported by RTC Engine rooms, resulting in failed RTMP stream playback. Example streaming configuration:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/79b8053c412b11f0912c52540044a08e.png)

### Audience Playback Stuck

In claw machine scenarios, when an RTC Engine audience enters a room and plays back for a period of time, playback may freeze, especially after multiple peer-join or onUserVideoAvailable callbacks. The audience's playback screen may freeze on the last frame. If this occurs, first check the dashboard for detailed call information. If the dashboard shows that the host has entered and exited the room multiple times, the issue is likely due to mutual kicking. Dashboard example:

****

**Solution**: Try stopping the current deviceâs stream to resolve the issue. If the problem remains unresolved, then check whether 2 identical streaming addresses are configured on the same machine.


---
*Source: [https://trtc.io/document/77216](https://trtc.io/document/77216)*
