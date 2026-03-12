# Android

## Business Process

This section summarizes some common business processes in the e-commerce live streaming scenario, helping you better understand the implementation process of the entire scenario.

Anchor Starting and Ending Live Streaming

Anchor Initiating Cross-Room Mic-Connection PK

RTC Audience Entering the Room for Mic-Connection

Product Management for Merchandising

The following diagram shows the process of an anchor (room owner) local preview, creating a room, entering a room to start live streaming, and leaving the room to end the live streaming.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77e284e18f0511f0818a52540099c741.png)

The following diagram shows the process of Anchor A inviting Anchor B for a cross-room mic-connection PK. During the cross-room PK, the audiences in both rooms can see the mic-connection live streaming of the two room owners.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77f6ab4e8f0511f0ae9d5254001c06ec.png)

The following diagram shows the process for RTC live interactive streaming audience to enter the room, apply for the mic-connection, end the mic-connection, and exit the room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77e4173c8f0511f0bd05525400454e06.png)

The diagram below shows the process in live streaming merchandising scenarios, where the anchor edits and lists products, while audience browses and purchases products.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77d53ed68f0511f0814e525400bf7822.png)

## Integration Preparation

### Step 1. Activating the Services

E-commerce live streaming scenarios usually require paid PaaS services for construction, including [RTC Engine](https://trtc.io/products/rtc), [Beauty AR](https://trtc.io/products/beauty), and [Player SDK](https://www.tencentcloud.com/document/product/266/7836). RTC Engine is responsible for providing real-time audio and video interaction capability. Beauty AR is responsible for providing beauty effect capabilities. The player is responsible for providing live and on-demand playback. You can freely choose to activate the above services based on actual business needs.

Activating RTC Engine Service

Activating Beauty AR Service

Activating Player Service

1. First, log in to the [RTC Engine console](https://console.trtc.io/) to create an application. Based on your needs, you can upgrade the RTC Engine application version, such as the Professional Edition, which unlocks more value-added features and services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77e304148f0511f088af5254005ef0f7.png)

> **Note:**It is recommended to create two applications for testing and production environments, respectively. Each Tencent Cloud account (UIN) is given 10,000 minutes of free duration every month for one year.RTC Engine monthly packages are divided into Trial Edition (default), Lite Edition, Standard Edition, and Professional Edition, unlocking different value-added features and services. For details, see [Version Features and Monthly Package Description](https://trtc.io/document/67650?product=pricing).

2. After an application is created, you can see the basic information of the application in the Application Management - Application Overview section. It is important to keep the **SDKAppID** and **SDKSecretKey** safe for later use and to avoid key leakage that could lead to traffic theft.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77d791ed8f0511f0b321525400e889b2.png)

1. Log in to the [Beauty AR console > Mobile Terminal License](https://console.trtc.io/beauty/license?start=1), and click **Create Trial License** (the trial license has a free trial period of 14 days and can be renewed once, totaling 28 days). Select Mobile, and enter App Name, Package Name, and Bundle ID based on your actual needs. Check the features you want to try: **All Beauty Features**, **Virtual Background**, **Face Recognition**, **Gesture Recognition**, and **Gift AR**, then click **Confirm**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77f9aede8f0511f084bd5254007c27c5.png)

2. After activation, you can view your information on the current page and refer to the integration guide at the top for integration. You can see how to use the License Key and License URL in the [Integration Guide](https://trtc.io/document/60195).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77e6c0f18f0511f0ae9d5254001c06ec.png)

1. Log in to [VOD console](https://console.tencentcloud.com/vod/license) or [CSS console](https://console.tencentcloud.com/live/license) > **License Management** > **Mobile**, and click **Create trial license**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77e65b4a8f0511f088af5254005ef0f7.png)

2. Enter `App Name`, `Package Name` and `Bundle ID` according to actual needs, select **Player Premium**, and click **Create**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77e772ea8f0511f0818a52540099c741.png)

3. After the Trial License is successfully created, the page will display the generated License information. **When initializing the SDK configuration, you need to enter two parameters: License Key and License URL, so carefully save the following information.**

****

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77f6edb38f0511f0ae9d5254001c06ec.png)

> **Note:**The License URL and Key for the same application are unique; after the Trial License is upgraded to the official version, the License URL and Key remain unchanged.

### Step 2: Importing SDK

RTC Engine SDK, Beauty AR SDK, and Player SDK have been published to the mavenCentral repository. You can configure Gradle to download updates automatically.

1. Add the dependency for the appropriate version of the SDK in dependencies.

```
dependencies {    // LiteAVSDK_Professional SDK, with additional features such as RTC Engine, live stream, short video, and player    implementation 'com.tencent.liteav:LiteAVSDK_Professional:latest.release'        // Beauty AR SDK, for example: S1-07 package as follows    implementation 'com.tencent.mediacloud:TencentEffect_S1-07:latest.release'}
```

> **Note:**Except the recommended automatic loading method, you can also choose to download SDK and manually import it. For details, see[Manual Integration of the RTC Engine SDK](https://trtc.io/document/62045?product=rtcengine&menulabel=core%20sdk&platform=android#31b6b3f0-5363-44b1-95a0-dbabe648e9df) and [Manual Integration of the Beauty AR SDK](https://trtc.io/document/60195?product=beautyar&menulabel=core%20sdk&platform=android#6d52c803-02a2-475c-9b62-d301b5d0c050).Implementation of e-commerce live streaming scenarios typically needs the combination of multiple capacities such as RTC Engine and player. **To avoid the symbol conflict issues arising from single integration, integrating the LiteAVSDK_Professional SDK is recommended**.

2. Specify the CPU architecture used by the app in defaultConfig.

```
defaultConfig {     ndk {             abiFilters "armeabi-v7a", "arm64-v8a"     }}
```

> **Note:**LiteAVSDK_Professional supports armeabi-v7a/arm64-v8a/x86/x86_64 architecture. The Beauty AR SDK only supports armeabi-v7a/arm64-v8a architecture.

3. Click **Sync Now** to automatically download SDK and integrate it into the project. If your beauty effect AR package includes dynamic effect and filter features, you need to download corresponding package on [SDK Download Page](https://trtc.io/document/60206?platform=android&product=beautyar&menulabel=core%20sdk#dynamically-downloading-.60assets.60-resources), decompress the free filter materials (./assets/lut) and sticker animation dynamic effects (./MotionRes) in the package, and place them in your project under the following directory:
  - Dynamic Effect: `../assets/MotionRes`.
  - Filter: `../assets/lut`.

### Step 3: Project Configuration

1. Permission configurations. Configure App permissions in AndroidManifest.xml. In e-commerce livestreaming scenarios, the RTC Engine and Beauty AR SDK require the following permissions:

```
<uses-permission android:name="android.permission.INTERNET" /><uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /><uses-permission android:name="android.permission.ACCESS_WIFI_STATE" /><uses-permission android:name="android.permission.RECORD_AUDIO" /><uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" /><uses-permission android:name="android.permission.BLUETOOTH" /><uses-permission android:name="android.permission.CAMERA" /><uses-feature android:name="android.hardware.camera.autofocus" />
```

> **Note:**Do not set `android:hardwareAccelerated="false"`. Disabling hardware acceleration will result in failure to render the other party's video stream.The RTC Engine SDK has no built-in permission request logic. You need to declare corresponding permissions. Some permissions (such as storage, recording, and camera) require dynamic requests during running.If the Android project's `targetSdkVersion` is 31 or higher, or if the target device runs Android 12 or a newer version, the official requirement is to dynamically request `android.permission.BLUETOOTH_CONNECT` permission in the code to use the Bluetooth feature properly. For more information, see [Bluetooth Permissions](https://developer.android.google.cn/develop/connectivity/bluetooth/bt-permissions).

2. Obfuscation configuration. Since we use Java's reflection feature inside the SDK, you must add relevant SDK classes to the non-obfuscation list in file proguard-rules.pro.

```
-keep class com.tencent.** { *; }-keep class org.light.** { *;}-keep class org.libpag.** { *;}-keep class org.extra.** { *;}-keep class com.gyailib.**{ *;}-keep class androidx.exifinterface.** { *;}
```

### Step 4: Authentication and Authorization

RTC Engine Authentication Credential

Beauty AR Authentication Permission

Player Authentication License

UserSig is a security signature designed by Tencent Cloud to prevent attackers from stealing your right of using cloud services. RTC Engine validates this authentication upon room entry.

- Debugging Stage: UserSig can be generated through two methods for debugging and testing purposes only: [client sample code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk&platform=android) and [console access](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk&platform=android#console).
- Formal Operation Stage: It is recommended to use a higher security level server computation for generating UserSig. This is to prevent key leakage due to client reverse engineering.

The specific implementation process is as follows:

1. Before calling the SDK's initialization function, your app must first request UserSig from your server.
2. Your server computes the UserSig based on the SDKAppID and UserID.
3. The server returns the computed UserSig to your app.
4. Your app passes the obtained UserSig into the SDK through a specific API.
5. The SDK submits the SDKAppID + UserID + UserSig to Tencent Cloud CVM for verification.
6. Tencent Cloud verifies the UserSig and confirms its validity.
7. After the verification passes, Tencent Real-Time Communication (TRTC) services will be provided for RTC Engine SDK.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77fa585a8f0511f0818a52540099c741.jpeg)

> **Note:**The method of generating UserSig locally during the debugging and testing stage is not recommended for the online environment because it may be easily decompiled and reversed, causing key leakage.We provide UserSig server-side computation source code in multiple languages (Java/GO/PHP/Node.js/Python/C#/C++). For details, see [Server-Side Calculation of UserSig](https://trtc.io/document/34580?product=chat&menulabel=uikit&platform=react#.E7.AD.BE.E5.90.8D.EF.BC.88usersig.EF.BC.89.E7.94.9F.E6.88.90.E5.B7.A5.E5.85.B7).

Before using Beauty AR, you need to verify the license credential with Tencent Cloud. Configuring License requires License Key and License URL. The example code is as follows.

```
import com.tencent.xmagic.telicense.TELicenseCheck;// If the purpose is just to trigger the download or update of the License, and not to care about the authentication result, then null is passed in for the fourth parameter.TELicenseCheck.getInstance().setTELicense(context, URL, KEY, new TELicenseCheck.TELicenseCheckListener() {    @Override    public void onLicenseCheckFinish(int errorCode, String msg) {        // Note: This callback does not necessarily be called on the calling thread.        if (errorCode == TELicenseCheck.ERROR_OK) {            // Authentication successful.        } else {            // Authentication failed.        }    }});
```

> **Note:**It is recommended to trigger the authentication permission in the initialization code of related business modules. Ensure to avoid having to download the License temporarily before use. Additionally, during authentication, network permissions must be ensured.The actual application's Package Name must match exactly with the Package Name associated with the creation of License. Otherwise, it will lead to License verification failure. For details, see [Authentication Error Code](https://trtc.io/document/60195?product=beautyar&menulabel=core%20sdk&platform=android#.E6.AD.A5.E9.AA.A4.E4.B8.80.EF.BC.9A.E9.89.B4.E6.9D.83).

Live streaming and on-demand playback features require player license authorization to achieve playback success, otherwise playback failure (screen going black) will occur. It needs to be set globally only once. If you haven't obtained a license, you can [apply for a free trial license](https://console.tencentcloud.com/vod/license) for normal playing. An official license should be [purchased](https://buy.tencentcloud.com/license). After successfully applying for a license, you will obtain 2 strings, **License URL** and **License Key**.

Before your App calls the SDK-related features, you need to configure as follows (recommended to configure in the Application class):

```
public class MApplication extends Application {    public void onCreate() {        super.onCreate();        String licenceURL = ""; // The obtained licence URL        String licenceKey = ""; // The obtained licence key        TXLiveBase.getInstance().setLicence(appContext, licenceURL, licenceKey);        TXLiveBase.setListener(new TXLiveBaseListener() {            @Override            public void onLicenceLoaded(int result, String reason) {                Log.i(TAG, "onLicenceLoaded: result:" + result + ", reason:" + reason);                if (result != 0) {                    // If the result is not 0, it means the setting has failed, and you need to retry                    TXLiveBase.getInstance().setLicence(appContext, licenceURL, licenceKey);                }            }        });    }}
```

After the License is successfully set (you need to wait for a while, the specific time depends on the network conditions), you can use the following method to view the License information:

```
TXLiveBase.getInstance().getLicenceInfo();
```

> **Note:**The actual application's Package Name must exactly match the Package Name associated with the License creation. Otherwise, it will lead to License verification failure.The License is a strong online verification logic. When the TXLiveBase#setLicence is called after the application is started for the first time, the network must be available. At the first launch of the App, if the network permission is not yet authorized, you need to wait until the permission is granted before calling TXLiveBase#setLicence again.Listen to the loading result of TXLiveBase#setLicence: For onLicenceLoaded API, if it fails, you should retry and guide according to the actual situation. If it fails multiple times, you can limit the frequency and supplement with product pop-ups and other guides to allow users to check the network conditions.TXLiveBase#setLicence can be called multiple times. It is advisable to call TXLiveBase#setLicence when entering the main interface of the App to ensure successful loading.For multi-process Apps, ensure that every process using the player calls TXLiveBase#setLicence when it starts. For example, for Apps on the Android side that use a separate process for video playback, when the process is killed and restarted by the system during background playback, TXLiveBase#setLicence should also be called.

### Step 5: Initializing the SDK

Initializing RTC Engine SDK

Initializing Beauty AR SDK

Initializing Player SDK

```
// Create an RTC Engine SDK instance (singleton mode)TRTCCloud mTRTCCloud = TRTCCloud.sharedInstance(context);// Set event listeners.mTRTCCloud.addListener(trtcSdkListener);// Notifications from various SDK events (e.g., error codes, warning codes, audio and video status parameters, etc.).private TRTCCloudListener trtcSdkListener = new TRTCCloudListener() {    @Override    public void onError(int errCode, String errMsg, Bundle extraInfo) {        Log.d(TAG, errCode + errMsg);    }        @Override    public void onWarning(int warningCode, String warningMsg, Bundle extraInfo) {        Log.d(TAG, warningCode + warningMsg);    }};// Remove event listener.mTRTCCloud.removeListener(trtcSdkListener);// Terminate the RTC Engine SDK instance (singleton mode)TRTCCloud.destroySharedInstance();
```

> **Note:**It is recommended to listen to SDK event notifications. Perform log printing and handling for some common errors. For details, see [Error Code Table](https://trtc.io/document/35130?platform=android&product=rtcengine&menulabel=core%20sdk#336ef58d7636c75f9aa0c87753e08e7c).

```
import com.tencent.xmagic.XmagicApi;// Initialize Beauty AR SDKXmagicApi mXmagicApi = new XmagicApi(context, XmagicResParser.getResPath(), new XmagicApi.OnXmagicPropertyErrorListener());// During development and debugging, you can set the log level to DEBUG. For release packages, set it to WARN to avoid impacting performance.mXmagicApi.setXmagicLogLevel(Log.WARN);// Release the Beauty Effect AR SDK. This method needs to be called in the GL thread.mXmagicApi.onDestroy();
```

> **Note:**Before initializing the Beauty AR SDK, resource copying and other preparations are required. For detailed steps, see [Process of Using the Beauty AR SDK](https://trtc.io/document/60195?product=beautyar&menulabel=core%20sdk&platform=android).

- On-demand Playback Scenario SDK Initialization.

```
// Set the SDK connection environment (if you serve global users, configure the SDK connection environment for global connection)TXLiveBase.setGlobalEnv("GDPR");// Create a Player objectTXVodPlayer mVodPlayer = new TXVodPlayer(mContext);// Add a View control for video renderingTXCloudVideoView mPlayerView = findViewById(R.id.video_view);// Associate the Player object with the View controlmVodPlayer.setPlayerView(mPlayerView);// Player parameter configurationTXVodPlayConfig config = new TXVodPlayConfig();config.setEnableAccurateSeek(true);  // Set whether to seek accurately. The default value is trueconfig.setMaxCacheItems(5);          // Set the number of cache files to 5config.setProgressInterval(200); // Set the interval for progress callbacks, in millisecondsconfig.setMaxBufferSize(50); // The maximum pre-load size, in MBmVodPlayer.setConfig(config);// Pass config to mVodPlayer// Player event listenermVodPlayer.setVodListener(new ITXVodPlayListener() {    @Override    public void onPlayEvent(TXVodPlayer player, int event, Bundle param) {        // Event notification    }    @Override    public void onNetStatus(TXVodPlayer player, Bundle bundle) {        // Status feedback    }});
```

- Live Streaming Scenarios SDK initialization.

```
// The TXCloudVideoView for video rendering needs to be added in advanceTXCloudVideoView mRenderView = findViewById(R.id.video_view);// Create a Player objectV2TXLivePlayer mLivePlayer = new V2TXLivePlayerImpl(mContext);// Associate the Player object with the video rendering viewmLivePlayer.setRenderView(mRenderView);// Player event listenermLivePlayer.setObserver(new V2TXLivePlayerObserver() {    @Override    public void onVideoLoading(V2TXLivePlayer player, Bundle extraInfo) {        // Video loading event.    }        @Override    public void onVideoPlaying(V2TXLivePlayer player, boolean firstPlay, Bundle extraInfo) {        // Video playback event.    }});
```

## Integration Process

### API Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77f6f0878f0511f088af5254005ef0f7.svg)

### Step 1: the Anchor Enters the Room to Push Streams

The control used by the RTC Engine SDK to handle video streams only supports passing in a `TXCloudVideoView` type. Therefore, you need to first define the view rendering control in the layout file.

```
<com.tencent.rtmp.ui.TXCloudVideoView    android:id="@+id/live_cloud_view_main"    android:layout_width="match_parent"    android:layout_height="match_parent" />
```

> **Note:**If you need to specifically use `TextureView` or `SurfaceView` as the view rendering control, see [Advanced Features - View Rendering Control](#adc81f8c-0dbf-4889-828c-1ea2859bc49b).

1. The anchor activates local video preview and audio capture before entering the room.

```
// Obtain the video rendering control for displaying the anchor's local video preview.TXCloudVideoView mTxcvvAnchorPreviewView = findViewById(R.id.live_cloud_view_main);// Set video encoding parameters to determine the picture quality seen by remote users.TRTCCloudDef.TRTCVideoEncParam encParam = new TRTCCloudDef.TRTCVideoEncParam();encParam.videoResolution = TRTCCloudDef.TRTC_VIDEO_RESOLUTION_960_540;encParam.videoFps = 15;encParam.videoBitrate = 1300;encParam.videoResolutionMode = TRTCCloudDef.TRTC_VIDEO_RESOLUTION_MODE_PORTRAIT;mTRTCCloud.setVideoEncoderParam(encParam);// boolean mIsFrontCamera can specify using the front/rear camera for video capture.mTRTCCloud.startLocalPreview(mIsFrontCamera, mTxcvvAnchorPreviewView);// Here you can specify the audio quality, from low to high as SPEECH/DEFAULT/MUSIC.mTRTCCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_DEFAULT);
```

> **Note:**You can set the video encoding parameters [TRTCVideoEncParam](https://trtc.io/document/35153?product=rtcengine&menulabel=core%20sdk&platform=android#trtcvideoencparam) according to business needs. For the best combinations of resolutions and bitrates for each tier, see [Resolution and Bitrate Reference Table](https://trtc.io/document/35153?product=rtcengine&menulabel=core%20sdk&platform=android#.E5.88.86.E8.BE.A8.E7.8E.87.E7.A0.81.E7.8E.87.E5.8F.82.E7.85.A7.E8.A1.A8).Call the above API before `enterRoom`. The SDK will only start the camera preview and audio capture, and wait until you call `enterRoom` to start streaming.Call the above API after `enterRoom`. The SDK will start the camera preview and audio capture and automatically start streaming.

2. The anchor sets rendering parameters for the local video, and the encoder output video mode (optional).

```
TRTCCloudDef.TRTCRenderParams params = new TRTCCloudDef.TRTCRenderParams();params.mirrorType = TRTCCloudDef.TRTC_VIDEO_MIRROR_TYPE_AUTO;   // Video mirror modeparams.fillMode = TRTCCloudDef.TRTC_VIDEO_RENDER_MODE_FILL;     // Video fill modeparams.rotation = TRTCCloudDef.TRTC_VIDEO_ROTATION_0;           // Video rotation angle// Set the rendering parameters for the local video.mTRTCCloud.setLocalRenderParams(params);// Set the video mirror mode for the encoder output.mTRTCCloud.setVideoEncoderMirror(boolean mirror);// Set the rotation of the video encoder output.mTRTCCloud.setVideoEncoderRotation(int rotation);
```

> **Note:**Setting local video rendering parameters only affects the rendering effect of the local video.Setting encoder output mode affects the viewing effect for other users in the room (and the cloud recording files).

3. The anchor starts the live streaming, entering the room and start streaming.

```
public void enterRoomByAnchor(String roomId, String userId) {    TRTCCloudDef.TRTCParams params = new TRTCCloudDef.TRTCParams();    // Take the room ID string as an example.    params.strRoomId = roomId;    params.userId = userId;    // UserSig obtained from the business backend.    params.userSig = getUserSig(userId);    // Replace with your SDKAppID.    params.sdkAppId = SDKAppID;    // Specify the anchor role.    params.role = TRTCCloudDef.TRTCRoleAnchor;    // Enter the room in an interactive live streaming scenario.    mTRTCCloud.enterRoom(params, TRTCCloudDef.TRTC_APP_SCENE_LIVE);}// Event callback for the result of entering the room.@Overridepublic void onEnterRoom(long result) {    if (result > 0) {        // result indicates the time taken (in milliseconds) to join the room.        Log.d(TAG, "Enter room succeed");    } else {        // result indicates the error code when you fail to enter the room.        Log.d(TAG, "Enter room failed");    }}
```

> **Note:**RTC Engine room IDs are divided into numeric type `roomId` and string type `strRoomId`. Rooms of different types are not interconnected. It is advisable to unify the room ID type.RTC Engine user roles include anchor and audience. Only hosts have permission to streaming. The user role should be specified upon room entry. If it's not specified, the default role is anchor.In e-commerce live streaming scenarios, it is recommended to choose `TRTC_APP_SCENE_LIVE` as the room entry mode.

### Step 2: the Audience Enters the Room to Pull Streams

1. Audience enters the RTC Engine room.

```
public void enterRoomByAudience(String roomId, String userId) {    TRTCCloudDef.TRTCParams params = new TRTCCloudDef.TRTCParams();    // Take the room ID string as an example.    params.strRoomId = roomId;    params.userId = userId;    // UserSig obtained from the business backend.    params.userSig = getUserSig(userId);    // Replace with your SDKAppID.    params.sdkAppId = SDKAppID;    // Specify the audience role.    params.role = TRTCCloudDef.TRTCRoleAudience;    // Enter the room in an interactive live streaming scenario.    mTRTCCloud.enterRoom(params, TRTCCloudDef.TRTC_APP_SCENE_LIVE);}// Event callback for the result of entering the room.@Overridepublic void onEnterRoom(long result) {    if (result > 0) {        // result indicates the time taken (in milliseconds) to join the room.        Log.d(TAG, "Enter room succeed");    } else {        // result indicates the error code when you fail to enter the room.        Log.d(TAG, "Enter room failed");    }}
```

2. Audience subscribes to the anchor's audio and video streams.

```
@Overridepublic void onUserAudioAvailable(String userId, boolean available) {    // The remote user publishes/unpublishes their audio.    // Under the automatic subscription mode, you do not need to do anything. The SDK will automatically play the remote user's audio.}@Overridepublic void onUserVideoAvailable(String userId, boolean available) {    // The remote user publishes/unpublishes the primary video.    if (available) {        // Subscribe to the remote user's video stream and bind the video rendering control.        mTRTCCloud.startRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, TXCloudVideoView view);    } else {        // Unsubscribe to the remote user's video stream and release the rendering control.        mTRTCCloud.stopRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);    }}
```

3. Audience sets the rendering mode for the remote video (optional).

```
TRTCCloudDef.TRTCRenderParams params = new TRTCCloudDef.TRTCRenderParams();params.mirrorType = TRTCCloudDef.TRTC_VIDEO_MIRROR_TYPE_AUTO;   // Video mirror modeparams.fillMode = TRTCCloudDef.TRTC_VIDEO_RENDER_MODE_FILL;     // Video fill modeparams.rotation = TRTCCloudDef.TRTC_VIDEO_ROTATION_0;           // Video rotation angle// Set the rendering mode for the remote video.mTRTCCloud.setRemoteRenderParams(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, params)
```

### Step 3: the Audience Interacts via Mic

1. The audience is switched to the anchor role.

```
// Switched to the anchor role.mTRTCCloud.switchRole(TRTCCloudDef.TRTCRoleAnchor);// Event callback for switching the role.@Overridepublic void onSwitchRole(int errCode, String errMsg) {    if (errCode == TXLiteAVCode.ERR_NULL) {        // Role switched successfully.       }}
```

2. Audience start local audio and video capture and streaming.

```
// Obtain the video rendering control for displaying the co-broadcasting audience's local video preview.TXCloudVideoView mTxcvvAudiencePreviewView = findViewById(R.id.live_cloud_view_sub);// Set video encoding parameters to determine the picture quality seen by remote users.TRTCCloudDef.TRTCVideoEncParam encParam = new TRTCCloudDef.TRTCVideoEncParam();encParam.videoResolution = TRTCCloudDef.TRTC_VIDEO_RESOLUTION_480_270;encParam.videoFps = 15;encParam.videoBitrate = 550;encParam.videoResolutionMode = TRTCCloudDef.TRTC_VIDEO_RESOLUTION_MODE_PORTRAIT;mTRTCCloud.setVideoEncoderParam(encParam);// boolean mIsFrontCamera can specify using the front/rear camera for video capture.mTRTCCloud.startLocalPreview(mIsFrontCamera, mTxcvvAudiencePreviewView);// Here you can specify the audio quality, from low to high as SPEECH/DEFAULT/MUSIC.mTRTCCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_DEFAULT);
```

> **Note:**You can set the video encoding parameters [TRTCVideoEncParam](https://trtc.io/document/35153?product=rtcengine&menulabel=core%20sdk&platform=android#trtcvideoencparam) according to business needs. For the best combinations of resolutions and bitrates for each tier, see [Resolution and Bitrate Reference Table](https://trtc.io/document/35153?product=rtcengine&menulabel=core%20sdk&platform=android#.E5.88.86.E8.BE.A8.E7.8E.87.E7.A0.81.E7.8E.87.E5.8F.82.E7.85.A7.E8.A1.A8).

3. The audience leaves the seat and stops streaming.

```
// Switched to the audience role.mTRTCCloud.switchRole(TRTCCloudDef.TRTCRoleAudience);// Event callback for switching the role.@Overridepublic void onSwitchRole(int errCode, String errMsg) {    if (errCode == TXLiteAVCode.ERR_NULL) {        // Stop camera capture and streaming.        mTRTCCloud.stopLocalPreview();        // Stop microphone capture and streaming.        mTRTCCloud.stopLocalAudio();    }}
```

### Step 4: Exiting and Dissolving the Room

1. Leave the room.

```
public void exitRoom() {    mTRTCCloud.stopLocalAudio();    mTRTCCloud.stopLocalPreview();    mTRTCCloud.exitRoom();}// Event callback for exiting the room.@Overridepublic void onExitRoom(int reason) {    if (reason == 0) {        Log.d(TAG, "Actively call exitRoom to exit the room.");    } else if (reason == 1) {        Log.d(TAG, "Removed from the current room by the server.");    } else if (reason == 2) {        Log.d(TAG, "The current room has been dissolved.");    }}
```

> **Note:**After all resources occupied by the SDK are released, the SDK will throw the `onExitRoom` callback notification to inform you.If you wish to call `enterRoom` again or switch to another audio and video SDK, wait for the `onExitRoom` callback before proceeding. Otherwise, you may encounter various exceptional issues such as the camera, microphone device being forcibly occupied.

2. Dissolve the room.
  - **Server dissolves the room.**

RTC Engine provides the server-side numeric type room dismissing API [`DismissRoom`](https://trtc.io/document/34269?product=rtcengine&menulabel=core%20sdk&platform=android) and the string type room dismissing API [DismissRoomByStrRoomId](https://trtc.io/document/39631?product=rtcengine&menulabel=core%20sdk&platform=android). You can call the server-side numeric type room dismissing API to remove all users from the room and dismiss the room.

  - **Client dissolves the room.**

The clients have no API for directly dismissing a room, and each is required to call [exitRoom](https://trtc.io/document/50762?product=rtcengine&menulabel=core%20sdk&platform=android#4651ae2c9ff5aa99442102e0d77a8606) to exit the room. After all anchors and audiences exit the room, the room will be automatically dismissed according to RTC Engine room lifecycle rules. For details, see [RTC Engine > Exit the Room](https://trtc.io/document/62045?product=rtcengine&menulabel=core%20sdk&platform=android#5055ad66-53b1-4539-88ec-6992d45bb0fd).

> **Note:**It is recommended that after the end of live streaming, you call the room dissolvement API on the server to ensure the room is dissolved. This will prevent audiences from accidentally entering the room and incurring unexpected charges.

## Advanced Features

### Product Information Pop-Up

The product information pop-up window feature can be implemented through Chat [Custom Message](#68e894f0-b443-48c9-974b-18a8afa4e0bb) or through [SEI Information](#742cb382-d825-4d72-b802-62dadf597932). The 2 implementation methods are introduced as follows.

#### Custom Message

Custom messages rely on Tencent Cloud [Chat](https://trtc.io/products/chat) capability. You should activate the service in advance and import the Chat SDK. For detailed directions, see [Voice Room Integration Guide - Integration Preparation](https://www.tencentcloud.com/document/product/647/73428#98a99507-e454-4eb9-b483-7ee3daa488b0).

1. Send custom messages.
  - Method 1: The anchor sends product pop-up related custom group messages on the client.

```
// Construct product pop-up message bodyJSONObject jsonObject = new JSONObject();try {    jsonObject.put("cmd", "item_popup_msg");    JSONObject msgJsonObject = new JSONObject();    msgJsonObject.put("itemNumber", 1); // Item number    msgJsonObject.put("itemPrice", 199.0);  // Item price    msgJsonObject.put("itemTitle", "xxx");  // Item title    msgJsonObject.put("itemUrl", "xxx");// Item URL    jsonObject.put("msg", msgJsonObject);} catch (JSONException e) {    e.printStackTrace();}String data = jsonObject.toString();// Send custom group messages (it is recommended that product pop-up messages should be set to high priority)V2TIMManager.getInstance().sendGroupCustomMessage(data.getBytes(), mRoomId,        V2TIMMessage.V2TIM_PRIORITY_HIGH, new V2TIMValueCallback<V2TIMMessage>() {            @Override            public void onError(int i, String s) {                // Failed to send product pop-up message            }            @Override            public void onSuccess(V2TIMMessage v2TIMMessage) {                // Successfully sent product pop-up message                // Locally rendering of product pop-up effect            }        });
```

  - Method 2: The backend operators sends product pop-up related custom group messages on the server.

Request URL sample:

```
https://xxxxxx/v4/group_open_http_svc/send_group_msg?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

Request packet body sample:

```
{    "GroupId": "@TGS#12DEVUDHQ",    "Random": 2784275388,    "MsgPriority": "High",  // The priority of the message. It is recommended to set product pop-up messages to high priority    "MsgBody": [        {            "MsgType": "TIMCustomElem",             "MsgContent": {                // itemNumber: item number; itemPrice: item price; itemTitle: item title; itemUrl: item URL                "Data": "{\\"cmd\\": \\"item_popup_msg\\", \\"msg\\": {\\"itemNumber\\": 1, \\"itemPrice\\": 199.0, \\"itemTitle\\": \\"xxx\\", \\"itemUrl\\": \\"xxx\\"}}"            }        }    ]}
```

2. Receive custom messages.

Other users in the room receive callback for custom group messages, then proceed with message parsing and product pop-up effect rendering.

```
// Custom group messages received.V2TIMManager.getInstance().addSimpleMsgListener(new V2TIMSimpleMsgListener() {    @Override    public void onRecvGroupCustomMessage(String msgID, String groupID, V2TIMGroupMemberInfo sender, byte[] customData) {        String customStr = new String(customData);        if (!customStr.isEmpty()) {            try {                JSONObject jsonObject = new JSONObject(customStr);                String command = jsonObject.getString("cmd");                JSONObject messageJsonObject = jsonObject.getJSONObject("msg");                if (command.equals("item_popup_msg")) {                    int itemNumber = messageJsonObject.getInt("itemNumber");  // Item number                    double itemPrice = messageJsonObject.getDouble("itemPrice");  // Item price                    String itemTitle = messageJsonObject.getString("itemTitle");  // Item title                    String itemUrl = messageJsonObject.getString("itemUrl");  // Item URL                    // Render product pop-up effect based on item number, item price, item title, and item URL                }            } catch (JSONException e) {                e.printStackTrace();            }        }    }});
```

#### SEI Information

SEI information will be inserted into the anchor's video stream for transmission, achieving precise sync between the product information pop-up and the anchor's live streaming.

1. Send SEI information.

The anchor sends SEI messages related to product pop-up windows in the RTC Engine client.

```
// Construct product pop-up message bodyJSONObject jsonObject = new JSONObject();try {    jsonObject.put("cmd", "item_popup_msg");    JSONObject msgJsonObject = new JSONObject();    msgJsonObject.put("itemNumber", 1); // Item number    msgJsonObject.put("itemPrice", 199.0);  // Item price    msgJsonObject.put("itemTitle", "xxx");  // Item title    msgJsonObject.put("itemUrl", "xxx");// Item URL    jsonObject.put("msg", msgJsonObject);} catch (JSONException e) {    e.printStackTrace();}String data = jsonObject.toString();// Send SEI informationmTRTCCloud.sendSEIMsg(data.getBytes(), 1);
```

2. Receive SEI information.

The audience receives SEI messages in the RTC Engine client, then conducts message parsing and product pop-up window effect rendering.

```
mTRTCCloud.setListener(new TRTCCloudListener() {    @Override    public void onRecvSEIMsg(String userId, byte[] data) {        String dataStr = new String(data);        if (!dataStr.isEmpty()) {            try {                JSONObject jsonObject = new JSONObject(dataStr);                String command = jsonObject.getString("cmd");                JSONObject messageJsonObject = jsonObject.getJSONObject("msg");                if (command.equals("item_popup_msg")) {                    int itemNumber = messageJsonObject.getInt("itemNumber");  // Item number                    double itemPrice = messageJsonObject.getDouble("itemPrice");  // Item price                    String itemTitle = messageJsonObject.getString("itemTitle");  // Item title                    String itemUrl = messageJsonObject.getString("itemUrl");  // Item URL                    // Render product pop-up effect based on item number, item price, item title, and item URL                }            } catch (JSONException e) {                e.printStackTrace();            }        }    }});
```

### Product Explanation Replay

By playing pre-recorded product explanation videos, the product explanation replay feature is implemented.

First, it is necessary to [initialize the player](https://www.tencentcloud.com/document/product/647/73428#325fd7f9-70ac-4f5d-bb20-5af704f79022), then start playing the recorded video. TXVodPlayer supports two playback modes, which you can choose according to your needs:

Using the URL Method

Using the FileId Method

```
// Play URL video resourceString url = "http://1252463788.vod2.myqcloud.com/xxxxx/v.f20.mp4";mVodPlayer.startVodPlay(url); // Play local video resourcesString localFile = "/sdcard/video.mp4";mVodPlayer.startVodPlay(localFile);
```

```
// Recommended to use the new API below// The psign means player signature. For more information about the signature and how to generate it, see: https://cloud.tencent.com/document/product/266/42436TXPlayInfoParams playInfoParam = new TXPlayInfoParams(1252463788, // The appId of the cloud platform account    "4564972819220421305", // The fileId of video    "psignxxxxxxx"); // Player signaturemVodPlayer.startVodPlay(playInfoParam);// Old API, not recommendedTXPlayerAuthBuilder authBuilder = new TXPlayerAuthBuilder();authBuilder.setAppId(1252463788);authBuilder.setFileId("4564972819220421305");mVodPlayer.startVodPlay(authBuilder);
```

Playback control: adjust the progress, pause playback, resume playback, and end playback.

```
// Adjust the progress (seconds)mVodPlayer.seek(time);// Pause playbackmVodPlayer.pause();// Resume playbackmVodPlayer.resume();// End playback (clear the last frame)mVodPlayer.stopPlay(true);
```

> **Note:**Terminate the View control when playback ends, particularly before the next startVodPlay. Otherwise, it may generate a large number of memory leaks and screen flicker issues.Meanwhile, when exiting the playback interface, remember to call the onDestroy() function of the render View. Otherwise, it may lead to memory leaks and a "Receiver not registered" warning.@Overridepublic void onDestroy() {    super.onDestroy();    mVodPlayer.stopPlay(true); // True means clearing the last frame    mPlayerView.onDestroy(); }

### Cross-Room Mic-Connection PK

1. Either party initiates the cross-room mic-connection PK.

```
public void connectOtherRoom(String roomId, String userId) {    try {        JSONObject jsonObj = new JSONObject();        ? ? // The digit room ID is roomId.        jsonObj.put("strRoomId", roomId);        jsonObj.put("userId", userId);        mTRTCCloud.ConnectOtherRoom(jsonObj.toString());    } catch (JSONException e) {        e.printStackTrace();    }}// Result callback for requesting cross-room mic-connection.@Overridepublic void onConnectOtherRoom(String userId, int errCode, String errMsg) {    // The user ID of the anchor in the other room you want to initiate the cross-room link-up.    // Error code. ERR_NULL indicates the request is successful.    // Error message.}
```

> **Note:**Both local and remote users participating in the cross-room mic-connection must be in the anchor role and must have audio/video uplink capabilities.Cross-room mic-connection with multiple room anchors can be achieved by calling `ConnectOtherRoom() `multiple times. Currently, a room can connect with up to three other room anchors at most, and up to 10 anchors in a room can conduct cross-room mic-connection PK with anchors in other rooms.

2. All users in both rooms will receive a callback indicating that the audio and video streams from the PK anchor in the other room are available.

```
@Overridepublic void onUserAudioAvailable(String userId, boolean available) {    // The remote user publishes/unpublishes their audio.    // Under the automatic subscription mode, you do not need to do anything. The SDK will automatically play the remote user's audio.}@Overridepublic void onUserVideoAvailable(String userId, boolean available) {    // The remote user publishes/unpublishes the primary video.    if (available) {        // Subscribe to the remote user's video stream and bind the video rendering control.        mTRTCCloud.startRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, TXCloudVideoView view);    } else {        // Unsubscribe to the remote user's video stream and release the rendering control.        mTRTCCloud.stopRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);    }}
```

3. Either party exits the cross-room mic-connection PK.

```
// Exit the cross-room mic-connection.mTRTCCloud.DisconnectOtherRoom();// Result callback for exiting cross-room mic-connection.@Overridepublic void onDisConnectOtherRoom(int errCode, String errMsg) {    super.onDisConnectOtherRoom(errCode, errMsg);}
```

> **Note:**After calling `DisconnectOtherRoom()`, you may exit the cross-room mic-connection PK with all other room anchors.Either the initiator or the receiver can call `DisconnectOtherRoom()` to exit the cross-room mic-connection PK.

### Integrate the Third-Party Beauty Features

RTC Engine supports integrating third-party beauty effect products. The example of Beauty AR is used next to demonstrate the process of integrating the third-party beauty effects.

1. Integrate the Beauty AR SDK, and apply for authorization License. For details, see the [Access Preparation](#430d5e7a-f889-480b-8d79-9160a99b17fe) step for implementation.
2. Resource copying (if any). If your resource files are built in the assets directory, you need to copy them to the App's private directory before use.

```
XmagicResParser.setResPath(new File(getFilesDir(), "xmagic").getAbsolutePath());//loading// Copy resource files to the private directory. Only need to do it once.XmagicResParser.copyRes(getApplicationContext());
```

If your resource file is [dynamically downloaded from the internet](https://trtc.io/document/60206?product=beautyar&menulabel=core%20sdk&platform=android#dynamically-downloading-.60assets.60-resources), you need to set the resource file path after the download is successful.

```
XmagicResParser.setResPath(local path of the downloaded resource file);
```

3. Set video data callback for third-party beauty effects by passing the results of the Beauty AR SDK processing each frame of data into the RTC Engine SDK for rendering processing.

```
mTRTCCloud.setLocalVideoProcessListener(TRTCCloudDef.TRTC_VIDEO_PIXEL_FORMAT_Texture_2D, TRTCCloudDef.TRTC_VIDEO_BUFFER_TYPE_TEXTURE, new TRTCCloudListener.TRTCVideoFrameListener() {    @Override    public void onGLContextCreated() {        // The OpenGL environment has already been set up internally within the SDK. At this point, the initialization of third-party beauty features can be done.        if (mXmagicApi == null) {            XmagicApi mXmagicApi = new XmagicApi(context, XmagicResParser.getResPath(), new XmagicApi.OnXmagicPropertyErrorListener());        } else {            mXmagicApi.onResume();        }    }    @Override    public int onProcessVideoFrame(TRTCCloudDef.TRTCVideoFrame srcFrame, TRTCCloudDef.TRTCVideoFrame dstFrame) {        // Callback for integrating with third-party beauty components for video processing.        if (mXmagicApi != null) {            dstFrame.texture.textureId = mXmagicApi.process(srcFrame.texture.textureId, srcFrame.width, srcFrame.height);        }        return 0;    }    @Override    public void onGLContextDestory() {        // The internal OpenGL environment within the SDK has been terminated. At this point, proceed to clean up resources for third-party beauty features.        mXmagicApi.onDestroy();    }});
```

> **Note:**Step 1 and Step 2 vary depending on differing implementation methods of third-party beauty effect products, and **Step 3** is **a universal and important step** for RTC Engine's integration with third-party beauty effects.

### Dual-Stream Encoding Mode

When the dual-stream encoding mode is enabled, the current user's encoder outputs two video streams, a high-definition large screen and a low-definition small screen, at the same time (but only one audio stream). In this way, other users in the room can choose to subscribe to the high-definition large screen or low-definition small screen based on their network conditions or screen sizes.

1. Enable large-and-small-screen dual-stream encoding mode.

```
public void enableDualStreamMode(boolean enable) {    // Video encoding parameters for the small-screen stream (customizable).    TRTCCloudDef.TRTCVideoEncParam smallVideoEncParam = new TRTCCloudDef.TRTCVideoEncParam();    smallVideoEncParam.videoResolution = TRTCCloudDef.TRTC_VIDEO_RESOLUTION_480_270;    smallVideoEncParam.videoFps = 15;    smallVideoEncParam.videoBitrate = 550;    smallVideoEncParam.videoResolutionMode = TRTCCloudDef.TRTC_VIDEO_RESOLUTION_MODE_PORTRAIT;    mTRTCCloud.enableEncSmallVideoStream(enable, smallVideoEncParam);}
```

> **Note:**When the dual-stream encoding mode is enabled, it will consume more CPU and network bandwidth. Therefore, it may be considered for use on Mac, Windows, or high-performance Pads. It is not recommended for mobile devices.

2. Choose the type of remote user's video stream to pull.

```
// Optional video stream types when subscribing to a remote user's video stream.mTRTCCloud.startRemoteView(userId, streamType, videoView);// You can switch the size of the specified remote user's screen at any time.mTRTCCloud.setRemoteVideoStreamType(userId, streamType);
```

> **Note:**When the dual-stream encoding mode is enabled, you can specify the video stream type as `TRTC_VIDEO_STREAM_TYPE_SMALL` with `streamType` to pull a low-quality small video for viewing.

### View Rendering Control

RTC Engine has many APIs that require you to control the video screen. All these APIs require you to specify a video rendering control. On the Android platform, `TXCloudVideoView` is used as the video rendering control, and both `SurfaceView` and `TextureView` rendering solutions are supported. Below are the methods for specifying the type of the rendering control and updating the video rendering control.

1. If you want mandatory use of a certain scheme, or to convert the local video rendering control to `TXCloudVideoView`, you can code as follows.

```
TextureView
```

2. If your business is involved in interaction scenarios that require switching display areas, you can use the RTC Engine SDK to update the local preview screen and the remote user's video rendering control feature.

```
// Update local preview screen rendering control.mTRTCCloud.updateLocalView(videoView);// Update the remote user's video rendering control.mTRTCCloud.updateRemoteView(userId, streamType, videoView);
```

> **Note:**Pass in `videoView` as the target video rendering control. `streamType` only supports `TRTC_VIDEO_STREAM_TYPE_BIG` and `TRTC_VIDEO_STREAM_TYPE_SUB`.

## Exception Handling

### Exception Handling

When the RTC Engine SDK encounters an unrecoverable error, the error is thrown in the `onError` callback. For details, see [Error Code Table](https://trtc.io/document/35130?product=rtcengine&menulabel=core%20sdk&platform=android#336ef58d7636c75f9aa0c87753e08e7c).

1. UserSig related. UserSig verification failed can cause room entry failure. You can use [UserSig tool](https://console.trtc.io/usersig) for verification.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_INVALID_USER_SIG | -3320 | Room entry parameter userSig is incorrect. Check if `TRTCParams.userSig` is empty. |
| ERR_TRTC_USER_SIG_CHECK_FAILED | -100018 | UserSig verification failed. Check if the parameter `TRTCParams.userSig` is filled in correctly or has expired. |

2. Check-in/out related. If room entry fails, please first check whether the parameters are correct. The room entry and exit API must be called in a paired manner. Even if room entry fails, the room exit API must be called.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_CONNECT_SERVER_TIMEOUT | -3308 | Room entry request timed out. Check if your internet connection is lost or if a VPN is enabled. You may also attempt to switch to 4G for testing. |
| ERR_TRTC_INVALID_SDK_APPID | -3317 | Room entry parameter sdkAppId is incorrect. Check if `TRTCParams.sdkAppId` is empty. |
| ERR_TRTC_INVALID_ROOM_ID | -3318 | Room entry parameter roomId is incorrect. Check if `TRTCParams.roomId` or `TRTCParams.strRoomId` is empty. Note that roomId and strRoomId cannot be used interchangeably. |
| ERR_TRTC_INVALID_USER_ID | -3319 | Room entry parameter userId is incorrect. Check if `TRTCParams.userId` is empty. |
| ERR_TRTC_ENTER_ROOM_REFUSED | -3340 | Room entry request denied. Check if `enterRoom` is called consecutively to enter a room with the same ID. |

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
// Set the rendering parameters for the local video.TRTCCloudDef.TRTCRenderParams params = new TRTCCloudDef.TRTCRenderParams();params.mirrorType = TRTCCloudDef.TRTC_VIDEO_MIRROR_TYPE_ENABLE; // Video mirror modeparams.fillMode = TRTCCloudDef.TRTC_VIDEO_RENDER_MODE_FILL;     // Video fill modeparams.rotation = TRTCCloudDef.TRTC_VIDEO_ROTATION_0;           // Video rotation anglemTRTCCloud.setLocalRenderParams(params);// Set the video mirror mode for the encoder output.mTRTCCloud.setVideoEncoderMirror(true);
```

### Adjustment of Camera Scale, Focus, and Switch

In e-commerce livestreaming scenarios, the anchor may need custom adjustment of the camera. The RTC Engine SDK's device management class provides APIs for such needs.

1. Query and set the zoom factor for the camera.

```
// Get the maximum zoom factor for the camera (only for mobile devices).float zoomRatio = mTRTCCloud.getDeviceManager().getCameraZoomMaxRatio();// Set the zoom factor for the camera (only for mobile devices).// Value range is 1 - 5. 1 means the furthest field of view (normal lens), and 5 means the closest field of view (zoom lens). The maximum recommended value is 5, exceeding this may result in blurry video.mTRTCCloud.getDeviceManager().setCameraZoomRatio(zoomRatio);
```

2. Set the focus feature and position of the camera.

```
// Enable or disable the camera's autofocus feature (only for mobile devices).mTRTCCloud.getDeviceManager().enableCameraAutoFocus(false);// Set the focus position of the camera (only for mobile devices).// The precondition for using this API is to first disable the autofocus feature using enableCameraAutoFocus.mTRTCCloud.getDeviceManager().setCameraFocusPosition(int x, int y);
```

3. Determine and switch to front or rear cameras.

```
// Determine if the current camera is the front camera (only for mobile devices).boolean isFrontCamera = mTRTCCloud.getDeviceManager().isFrontCamera();// Switch to front or rear cameras (only for mobile devices).// Passing true means switching to front, and passing false means switching to rear.mTRTCCloud.getDeviceManager().switchCamera(!isFrontCamera);
```


---
*Source: [https://trtc.io/document/73432](https://trtc.io/document/73432)*
