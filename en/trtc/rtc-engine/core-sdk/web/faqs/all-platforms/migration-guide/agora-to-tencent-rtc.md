# Agora to Tencent RTC

Welcome to the Tencent RTC Engine SDK Migration Guide. This document is designed for developers to efficiently transition code implementations from Agora Video SDK to Tencent RTC Engine SDK. To ensure fast and seamless migration, we provide step-by-step **Tencent RTC Engine application setup guides** and fundamental **RTC functionality/API code comparisons** through code samples.

If you are planning to integrate Tencent RTC Engine SDK into a new project, we recommend to get started with our [Sample Demo](https://trtc.io/document/35607?platform=web&product=rtcengine&menulabel=coresdk) or [Integration](https://trtc.io/document/59649?platform=web&product=rtcengine&menulabel=coresdk) guides. To learn more Tencent RTC Engine capabilities, visit [Product Introduction](https://trtc.io/document/35078?platform=web&product=rtcengine&menulabel=coresdk).

## Create a Tencent RTC Engine Application

In order to access Tencent RTC Engine services, a Tencent RTC Engine application and its credentials are required. You can create a new Tencent RTC Engine application in the Tencent RTC console by following these steps:

1. Sign up or sign in your [Tencent RTC Account](https://trtc.io/login?s_url=https://console.trtc.io), and log in to your [Tencent RTC Console](https://console.trtc.io/).
2. Click **Create Application** in the **Application** section.
3. In the popup page, enter your application name, select **RTC Engine**, and then click **Create**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/66d506895bd611f0ba94525400454e06.png)

Once you have a Tencent RTC Engine application, obtain the following credentials in **Basic Information** section:

- **SDKAppID**: this is an auto-generated ID that uniquely identifies your Tencent RTC application.
- **SDKSecretKey**: this is one of the key parameters used to generate the security signature `UserSig`, which ensures the secure access of Tencent RTC services. For more information about this credential and `UserSig` calculation, see [UserSig](https://trtc.io/document/35166?platform=web&product=rtcengine&menulabel=coresdk).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9e7cd4c75bda11f0922d5254007c27c5.png)

## Install Tencent RTC Engine SDK

Tencent RTC Engine SDK is available for various popular platforms, ensuring comprehensive cross-platform compatibility spanning web, desktops, and mobile platforms. You can install Tencent RTC Engine SDK that suits your current implemention in following ways:

Web

Flutter

React Native

**Install using**`npm`:

1. Install [trtc-sdk-v5](https://www.npmjs.com/package/trtc-sdk-v5)  in your Web project:

```
npm install trtc-sdk-v5 --save
```

2. Import module in your script:

```
import TRTC from 'trtc-sdk-v5'
```

**Install using HTML**`<script>`:

Download the SDK file `trtc.js` from [Github](https://github.com/Tencent-RTC/TRTC_Web/blob/main/SDK/trtc.js), and include the following code in your webpage:

```
<script src="/your_path/trtc.js"></script>
```

Install [tencent_rtc_sdk](https://pub.dev/packages/tencent_rtc_sdk) in your Flutter project:

```
flutter pub add tencent_rtc_sdk
```

1. Install [trtc-react-native](https://www.npmjs.com/package/trtc-react-native) in your React Native project:

```
npm install trtc-react-native --save# oryarn add trtc-react-native
```

2. Import module in your script:

```
import TRTCCloud, { TRTCParams, TRTCCloudDef } from 'trtc-react-native'
```

## Term Comparison

This section compares the terms used for key RTC concepts by Tencent RTC Engine and Agora. To learn more about Tencent RTC Engine glossary, visit [Product Concepts](https://trtc.io/document/37714?platform=web&product=rtcengine&menulabel=coresdk).

| Tencent RTC Engine Term | Agora Term | Explanation |
| --- | --- | --- |
| Room | Channel | The group that connects the RTC participants together. |
| Anchor | Host | A **room user type** that has the streaming permission and is able to **publish** audio and video streams to the server.The anchor/host is also able to **subscribe** and **play back** the audio and video streams of other anchors/hosts. |
| Audience | Audience | A **room user type** that can only **subscribe** to other anchors/hosts. |

## Functionality & API Comparison

This section lists some code samples that compares the implementations of common RTC functionalities in Agora Video SDK and Tencent RTC Engine SDK:

1. [Initialize a Tencent RTC / Agora client instance](#bd19165b-c40e-48e9-9009-1d50a97ec953)
2. [Join an Tencent RTC room / Agora channel](#46f66456-7b9f-460a-9d33-5eaa85efb315)
3. [Set up event listeners](#d07aabe3-11c5-4d2d-bfb6-62aafea8cbeb)
4. [Collect, publish, and unpublish local Tencent RTC streams / Agora tracks](#7e426826-e092-41ef-82ad-451301309b79)
5. [Subscribe and play remote Tencent RTC streams / Agora tracks](#4fce7a6a-83d4-4bdc-8a91-334582ba0347)
6. [Leave the Tencent RTC room / Agora channel](#ef5131fe-8234-41e1-a1b8-4fff54dc4ab6)

### Initialize a Tencent RTC/Agora client instance

Web

Flutter

React Native

**Agora**

```
// Create an Agora Web clientconst agoraWebClient = AgoraRTC.createClient({    mode: "rtc",    codec: "vp8"});
```

**Tencent RTC**

```
// Create a TRTC Web clientconst trtcWebClient = TRTC.create();
```

**Agora**

```
RtcEngine agoraFlutterEngine = createAgoraRtcEngine();await agoraFlutterEngine.initialize(    const RtcEngineContext(appId: "<app id>"));
```

**Tencent RTC**

```
// Create a TRTC instanceTRTCCloud trtcFlutterEngine = await TRTCCloud.sharedInstance();
```

**Agora**

```
const agoraRNEngine = createAgoraRtcEngine();await agoraRNEngine.initialize({ appId: "<app id>" });
```

**Tencent RTC**

```
// Create a TRTC instanceconst trtcRNEngine = TRTCCloud.sharedInstance();
```

### Join an Tencent RTC room/Agora channel

Web

Flutter

React Native

**Agora**

```
await agoraWebClient.join(appId, channelName, token, userId);
```

**Tencent RTC**

```
try {	await trtcWebClient.enterRoom({		// Your application's SDKAppID		sdkAppId: 12345678,		userId: "<custom user id>",		// User signature, generated from your appliction's SDKSecretKey		userSig: "<user signature>",		roomId: 1234	});		console.log('Entered the room successfully');} catch (error) {	console.error('Failed to enter the room ' + error);}
```

**Agora**

```
await agoraFlutterEngine.joinChannel(    token: "<your token>",    channelId: "<channel id>",    // user id    uid: 0    options: const ChannelMediaOptions(        autoSubscribeVideo: true,        autoSubscribeAudio: true,        publishCameraTrack: true,        publishMicrophoneTrack: true    ) );
```

**Tencent RTC**

```
trtcFlutterEngine.enterRoom(    TRTCParams(        // Your application's SDKAppID        sdkAppId: 12345678,        userId: "<custom user id>",        // User signature, generated from your appliction's SDKSecretKey        userSig: "<user signature>",        roomId: 1234,        // Enter the room as Anchor        role: TRTCRoleType.anchor,    ),    TRTCAppScene.live);print("Enter the room successfully");
```

**Agora**

```
const token = "<your token>";const channelName = "<your channel id>";const localUserId = 0;agoraRNEngine.joinChannel(    token,     channelName,     localUserId,     {        autoSubscribeVideo: true,        autoSubscribeAudio: true,        publishCameraTrack: true,        publishMicrophoneTrack: true    });
```

**Tencent RTC**

```
trtcRNEngine.enterRoom(    new TRTCParams({        // Your application's SDKAppID        sdkAppId: 12345678,        userId: "<custom user id>",        // User signature, generated from your appliction's SDKSecretKey        userSig: "<user signature>",        roomId: 1234    }),    // Enter the room in audio and video call scenarios    TRTCCloudDef.TRTC_APP_SCENE_VIDEOCALL);
```

### Set up event listeners

Web

Flutter

React Native

**Agora**

```
agoraWebClient.on("user-joined", async (user, mediaType) => {	console.log("User joins the channel");});
```

**Tencent RTC**

```
User $
```

**Agora**

```
agoraFlutterEngine.registerEventHandler(    RTCEngineEventHandler(        onUserJoined: (RtcConnection connection, int remoteUid, int elapsed) {            print("Remote user $remoteUid joined");        },    ));
```

**Tencent RTC**

```
// Define a TRTCCloudListener with relative eventsTRTCCloudListener listener = TRTCCloudListener(    onEnterRoom: (result) {        if(result > 0) {            print("Enter room success.");        }    },    onRemoteUserEnterRoom: (userId) {        print("Remote user $userId enters the room.")    },    onError: (errCode, errMsg) {        print("Error $errCode: $errMsg");    });// Register the event listener with TRTC enginetrtcFlutterEngine.registerListener(listener);
```

**Agora**

```
agoraRNEngine.registerEventHandler({    onUserJoined: (connection, uid) {        console.log(`Remote user ${uid} joins the room`);    }});
```

**Tencent RTC**

```
const onRtcListener = useCallback((type:TRTCCloudListener, params:any) => {    if (type === TRTCCloudListener.onEnterRoom) {        if (params.result > 0) {            console.log("Enter room success.");        }    } else if (type === TRTCCloudListener.onRemoteUserEnterRoom) {        console.log(`Remote user ${params.userId} enters the room.`);    } else if (type === TRTCCloudListener.onError) {        console.error(`Error ${params.errCode}: ${params.errMsg}.`);    }});trtcRNEngine.registerListener(onRtcListener);
```

### Collect, publish, and unpublish local Tencent RTC streams/Agora tracks

Web

Flutter

React Native

Assume the container HTML element for local audio and video is:

```
<div class="local-video-container" width="1920" height="1080"></div>
```

**Agora**

```
// Capture both microphone and camera tracksconst [microphoneTrack, cameraTrack] = await agoraWebClient.createMicrophoneAndCameraTracks();// Renderconst localMediaContainer = document.getElementById('local-video-container');cameraTrack.play(localMediaContainer);// Publish microphone and camera tracksawait agoraWebClient.publish([microphoneTrack, cameraTrack]);// Unpublish tracksawait agoraWebClient.unpublish();
```

**Tencent RTC**

```
const view = document.getElementById('local-video-container');// Local video stream// Get the list of available camerasconst cameraList = await TRTC.getCameraList();if(cameraList[0]) {	// Start collecting video	// Publish the first (available) camera's video stream to the current room	await trtcWebClient.startLocalVideo({		view,		options: { cameraId: cameraList[0].deviceId }	});}// Unpublish and stop collecting videoawait trtcWebClient.stopLocalVideo();// Local audio stream// Get the list of available microphones.const microphoneList = await TRTC.getMicrophoneList();if(microphoneList[0]) {	// Start collecting audio	// Publish the first (available) microphone's audio stream to the current room	await trtcWebClient.startLocalAudio({		options: { microphoneId: microphoneList[0].deviceId }	});}// Unpublish and stop collecting audioawait trtc.stopLocalAudio();
```

**Agora**

```
// Local video track// Display the local video by enabling the video module and starting local video previewawait agoraFlutterEngine.enableVideo();await agoraFlutterEngine.startPreview();// Render the local video via AgoraVideoView widgetWidget _localVideo() {    return AgoraVideoView(        controller: VideoViewController(            rtcEngine: agoraFlutterEngine,            canvas: const VideoCanvas(                 // Specify the local user id                uid: 0,                // Set the video rendering mode                renderMode: RenderModeType.renderModeHidden            )        )    );}// Disable the video module and stop local video previewagoraFlutterEngine.disableVideo();agoraFlutterEngine.stopPreview();// Local audio track is enabled by default in Agora
```

**Tencent RTC**

```
// Local video streamimport 'package:tencent_rtc_sdk/trtc_cloud_video_view.dart';// Before enabling the camera preview, you can set the local video rendering parameterstrtcFlutterEngine.setLocalRenderParams(    TRTCRenderParams(        fillMode: TRTCVideoFillMode.fill,        mirrorType: TRTCVideoMirrorType.auto,        rotation: TRTCVideoRotation.rotation0    ));// Render the local video via TRTCCloudVideoView widgetWidget _localVideo() {    return TRTCCloudVideoView(        key: ValueKey(0),        onViewCreated: (viewId) {            // Set to 'false' if using rear camera            bool useFrontCamera = true;            // Start local video preview using front camera            trtcFlutterEngine.startLocalPreview(useFrontCamera, viewId);                        // Stop local video preview            trtcFlutterEngine.stopLocalPreview();        }    )}// Local audio stream// Enable the audio module and start publishing local audiotrtcFlutterEngine.startLocalAudio(TRTCAudioQuality.speech);// Disable the audio module and stop publishing local audiotrtcFlutterEngine.stopLocalAudio();
```

**Agora**

```
<RtcSurfaceView     canvas={{ uid: 0 }}     style={ width: '90%', height: 200 }/><!-- Local audio track is enabled by default in Agora -->
```

**Tencent RTC**

```
import { TXVideoView } from 'trtc-react-native';
```

```
<TXVideoView.LocalView    style={{ width: 1080, height: 1080 }}/>
```

```
// Enable the audio module and start publishing local audiotrtcRNEngine.startLocalAudio();// Disable the audio module and stop publishing local audiotrtcRNEngine.stopLocalAudio();
```

### Subscribe and play remote Tencent RTC streams/Agora tracks

Web

Flutter

React Native

Assume the container HTML element for remote audio and video is:

```
<div class="remote-video-container" width="1920" height="1080"></div>
```

**Agora**

```
agoraWebClient.on("user-published", async (user, mediaType) => {	// Initiate a subscription	await client.subscribe(user, mediaType);	// Subscribe to an audio track	if (mediaType === "audio") {		const audioTrack = user.audioTrack;		// Automatically play audio		audioTrack.play();	} else {		const videoTrack = user.videoTrack;		// Automatic video playback		videoTrack.play('remote-video-container');	 }});
```

**Tencent RTC**

```
// Video (listen for TRTC.EVENT.REMOTE_VIDEO_AVAILABLE)trtcWebClient.on(TRTC.EVENT.REMOTE_VIDEO_AVAILABLE, ({ userId, streamType }) => {	// To play the video image, you need to place an HTMLElement in the DOM	// Assume this is a <div> element and has the id of `${userId}_${streamType}`	const view = `${userId}_${streamType}`;	// Start rendering remote video	trtcWebClient.startRemoteVideo({ userId, streamType, view });});// Audio (listen for TRTC.EVENT.REMOTE_AUDIO_AVAILABLE)trtcWebClient.on(TRTC.EVENT.REMOTE_AUDIO_AVAILABLE, event => {	// Start playing remote audio	trtcWebClient.muteRemoteAudio(event.userId, false);});
```

**Agora**

```
// Remote video track// Render the remote video of a joined user, also via AgoraVideoView widgetWidget _remoteVideo(remoteuid, channelid) {    return AgoraVideoView(        controller: VideoViewController.remote(            rtcEngine: agoraFlutterEngine,            canvas: const VideoCanvas(uid: remoteuid),            connection: const RtcConnection(channelId: channelid)        )    );}// Local audio track is enabled by default in Agora
```

**Tencent RTC**

```
// Remote video streamimport 'package:tencent_rtc_sdk/trtc_cloud_video_view.dart';// You can also set the remote video rendering parameters before renderingtrtcFlutterEngine.setRemoteRenderParams(    TRTCRenderParams(        fillMode: TRTCVideoFillMode.fill,        mirrorType: TRTCVideoMirrorType.auto,        rotation: TRTCVideoRotation.rotation0    ));// Render the remote video, also via TRTCCloudVideoView widgetWidget _remoteVideo(remoteuid) {    return TRTCCloudVideoView(        key: ValueKey(0),        onViewCreated: (viewId) {            // Start remote video view            trtcFlutterEngine.startRemoteView(                remoteuid,                TRTCVideoStreamType.big,                viewId            );                        // Stop remote video view            trtcFlutterEngine.stopLocalPreview(                remoteuid,                TRTCVideoStreamType.big,            );        }    )}// Remote audio stream// Mute/unmute a remote user's audio streambool isMuted = true;trtcFlutterEngine.muteRemoteAudio(remoteuid, isMuted);
```

**Agora**

```
<React.Fragment key={remoteUid}>    <RtcSurfaceView        canvas={{ uid: remoteUid }}        style={ width: '90%', height: 200 }    /></React.Fragment>
```

```
// Mute/unmute a remote user's audio streamlet isMuted = true;trtcRNEngine.muteRemoteAudioStream(remoteuid, isMuted);
```

**Tencent RTC**

```
import { TXVideoView } from 'trtc-react-native';// Stop remote video playbacktrtcRNEngine.stopRemoteView(remoteuid, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);// Mute/unmute remote audio playbacklet isMuted = true;trtcRNEngine.muteRemoteAudio(remoteuid, isMuted);
```

```
<TXVideoView.RemoteView    userId={remoteUserId}    streamType={TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG}    style={{ width: 1080, height: 1080 }}/>
```

### Leave the Tencent RTC room/Agora channel

Web

Flutter

React Native

**Agora**

```
await agoraWebClient.leave();
```

**Tencent RTC**

```
await trtcWebClient.exitRoom();// Destroy the client instance and release releated resource if neededtrtcWebClient.destroy();
```

**Agora**

```
await agoraFlutterEngine.leaveChannel();
```

**Tencent RTC**

```
await trtcFlutterEngine.exitRoom();// Destroy the client instance and release releated resource if neededtrtcFlutterEngine.destroySharedInstance();
```

**Agora**

```
agoraRNEngine.leaveChannel();
```

**Tencent RTC**

```
trtcRNEngine.exitRoom();// Destroy the client instance and release releated resource if neededtrtcRNEngine.destroySharedInstance();
```

## Conclusion

The preceding sections provide a subset of functional-equivalent implementations between Agora Video SDK and Tencent RTC Engine SDK. For more comprehensive details on Tencent RTC Engine features and documentations, visit [Feature overview](https://trtc.io/document/35428?platform=web&product=rtcengine&menulabel=coresdk) for more information.

Tencent RTC is committed to offering cost-effective, low-latency, and high-quality interactive audio/video services. If you need developer support or any further assistance regarding Tencent RTC Engine SDK integration, please feel free to [Contact Us](https://trtc.io/contact), or reach us through [Discord](https://discord.com/invite/hq7jW7zChW) and [Telegram](https://t.me/+EPk6TMZEZMM5OGY1). We will ensure a smooth integration and address any queries you may have.


---
*Source: [https://trtc.io/document/71655](https://trtc.io/document/71655)*
