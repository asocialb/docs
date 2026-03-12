# Scenario Solution

## Scenario Introduction

Online claw machines use video streaming and remote control technology to enable users to control physical claw machines in real time from their smartphones, tablets, or computers. The experience rivals in-person gameplay while enabling online audience interaction and engagement.

**Key Capabilities with RTC Engine:**

[RTC Engine](https://trtc.io/document/35078?product=rtcengine&menulabel=core%20sdk&platform=web) provides the following capabilities to power seamless online claw machine experiences:

- **Ultra-low latency**: End-to-end audio and video latency below 300ms
- **Cross-platform support**: Play anytime, anywhere on WeChat Mini Programs, iOS, Android, or Web
- **Cloud recording**: Capture exciting gameplay moments for marketing and expanding application reach

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fc6041dfd64611f0aecd5254007c27c5.png)

## Implementation Overview

A complete online claw machine solution requires multiple functional modules, including [Media Service](https://www.tencentcloud.com/document/product/647/75310#media-service) and [Signaling Service](https://www.tencentcloud.com/document/product/647/75310#signaling-service). The following table outlines key actions and features for each module:

| Functional Module | Key Actions and Features |
| --- | --- |
| Media service | Publishing and subscribing to audio and video streams |
| Signaling service | Remote control |

**Overall Architecture**

The online claw machine business architecture operates as follows:

**Hardware Setup:**

- Two cameras are installed on the claw machine for video capture and streaming

**Player Workflow:**

1. Players enter the game interface and join the RTC Engine room linked to the claw machine
2. Players view real-time video streams from the machine's cameras
3. After inserting coins or topping up their account, players control the claw to grab toys

**Audience Participation:**

- Audience members can join the game room to watch players in action

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1160037ad64711f097cb5254005ef0f7.png)

### Media Service

#### Push Audio and Video Streams

##### RTMP Streaming

Most network cameras and streaming boxes support RTMP streaming. With RTC Engine's [RTMP streaming into room](https://trtc.io/document/62716?product=rtcengine&menulabel=core%20sdk&platform=web) feature, you can push video streams directly from these devices to RTC Engine rooms.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/16ed03cad64711f0ab505254001c06ec.png)

To implement RTMP streaming:

1. Use TRTC's [RTMP generation rules](https://trtc.io/document/62716?product=rtcengine&menulabel=core%20sdk&platform=web#9aa9dfc5-84a2-4583-898c-f07d25c01750) to generate the corresponding RTMP streaming address.
2. Manually configure the RTMP streaming address on your claw machine's network camera or streaming box.
3. Start the RTMP network camera or streaming box to push the video stream to the RTC Engine room.

> **Note:**The related fees are as follows:**Feature Unlock:**The **RTMP streaming into room** feature requires a subscription to [RTC-Engine Packages](https://trtc.io/document/56025?product=rtcengine&menulabel=core%20sdk&platform=web) **Standard** or **Pro Edition**.**Usage Fees:****Transcoding fees**: Incurred when using the streaming feature. See [Mixed Stream Transcoding and Bypass Streaming Billing Instructions](https://trtc.io/document/47631?product=rtcengine&menulabel=core%20sdk&platform=web).**Robot audio duration fees**: Charged for the streaming robot in the room.*Note: Fees waived until August 15, 2024. Charges begin August 16, 2024.***Audio and video call fees**: Incurred when audience members subscribe to the streamed content. See [Audio and Video Duration Billing Instructions](https://trtc.io/document/42734?product=rtcengine&menulabel=core%20sdk&platform=web).

##### RTC Engine Streaming

Alternatively, some hardware vendors partner with TRTC to integrate the RTC Engine SDK directly into network cameras or streaming boxes, enabling them to capture video and push it directly to RTC Engine rooms.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4379fadbd64711f0929b525400bf7822.png)

To set this up:

1. Manually configure the `SDKAppID`, `UserId`, `RoomId`, and `UserSig` on your claw machine's RTC Engine webcam or streaming box.
2. Start the RTC Engine webcam or streaming box to push the video stream to the RTC Engine room.

#### Pull Audio and Video Streams

Once the claw machine successfully pushes audio and video streams to the RTC Engine room, usersâwhether players or audience membersâcan enter the corresponding RTC Engine room to watch the claw machine feed in real time.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/494dfbb5d64711f097cb5254005ef0f7.png)

Implementation steps:

1. Integrate the RTC Engine SDK into your application.
2. Configure your business server to deliver the necessary SDK parametersâ`SDKAppID`, `UserId`, `RoomId`, and `UserSig`âto your application.
3. Users enter the RTC Engine room corresponding to the claw machine through your application and call the pull-stream API provided by the RTC Engine SDK to receive and watch the real-time audio and video stream.

### Signaling Service

The signaling service synchronizes control signals between the application and the claw machine. Off-the-shelf hardware control modules with various network communication modes are readily available and require only configuration and debuggingâno additional development needed.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f771ec3d64711f091e252540044a08e.png)

**Communication Flow:**

1. The application calls the instruction API on your business backend.
2. Your backend constructs a hexadecimal serial port message and sends it to the hardware network module via the Netty service.
3. The hardware module processes the serial port message and controls the claw machine through its serial port.

Beyond core media and signaling services, the solution offers additional capabilities to enhance user experience.

### Recording Serviceï¼Extended featuresï¼

Replay functionality significantly enhances user engagement. Users can rewatch exciting momentsâespecially successful grabsâto relive their victories and refine their techniques. RTC Engine's cloud recording makes this easy to implement.

##### RTC Engine Cloud Recording

RTC Engine's On-Cloud Recording operates independently from Cloud Streaming Services (CSS), using a dedicated real-time recording backend. This provides a complete, unified recording experience with two recording modes:

**Single Stream Recording**

Record each user's audio and video stream as separate files:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/616a6e69d64711f097cb5254005ef0f7.png)

**Mix-Stream Recording**

Merge all audio and video streams from the room into a single file:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/68727799d64711f098a7525400e889b2.png)

## Key Business Logic

To ensure optimal performance in online claw machine scenarios, several key technical optimizations are essential.

### Low Latency Optimization

Online claw machine solutions require extremely low latency because control commands must synchronize with rapid signaling transmission. Standard RTC Engine latency (300-500ms) is insufficientâlatency must be reduced to 100-300ms or lower.

The following optimizations target every point in the transmission link:

****

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a69fa09bd65a11f0a501525400454e06.png)

**Optimization Strategies:**

1. **Use RTC Engine SDK for capture and streaming**

Integrate the RTC Engine SDK directly into network cameras or streaming boxes to stream video to RTC Engine rooms. This bypasses standard RTMP distribution, reducing end-to-end latency from 300-500ms to 100-300ms.

2. **Configure low-latency stream playback**

Set the buffer size to 80-100ms and enable software decoding:

Android

iOS

Web

```
JSONObject jsonObject = new JSONObject();try {    jsonObject.put("api", "SetAudioCacheParams");    JSONObject params = new JSONObject();    params.put("min_cache_time", 80); // Local minimum audio cache duration    params.put("max_cache_time", 100); // Local maximum audio cache duration    jsonObject.put("params", params);    mTRTCCloud.callExperimentalAPI(String.format(Locale.ENGLISH, jsonObject.toString()));} catch (JSONException e) {    e.printStackTrace();}JSONObject jsonObject = new JSONObject();try {    jsonObject.put("api", "setDecoderStrategy");    JSONObject params = new JSONObject();    params.put("codecType", 1); // Set software decoding    jsonObject.put("params", params);    mTRTCCloud.callExperimentalAPI(String.format(Locale.ENGLISH, jsonObject.toString()));} catch (JSONException e) {    e.printStackTrace();}
```

```
NSDictionary *jsonDic = @{    @"api": @"SetAudioCacheParams",    @"params": @{                  @"min_cache_time": @(80),                  @"max_cache_time": @(100)                }};NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDic options:NSJSONWritingPrettyPrinted error:nil];NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[trtcCloud callExperimentalAPI:jsonString];NSDictionary *jsonDic = @{    @"api": @"setDecoderStrategy",    @"params": @{                 @"codecType": @(1)                }};NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDic options:NSJSONWritingPrettyPrinted error:nil];NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[trtcCloud callExperimentalAPI:jsonString];.... // Code for joining a room
```

```
const trtc = TRTC.create();// Enter the room.try {  await trtc.enterRoom({     strRoomId,    scene:'rtc',     sdkAppId,     userId,     userSig,    playoutDelay: { min: 80, max: 100 } // Modify local delay    });  console.log('Room entry successful. ');} catch (error) {  console.error('Room entry failed. ' + error);}
```

> **Note:****Version Requirements:****Client (Android, iOS)**: [RTC Engine 12.4](https://trtc.io/document/39426?product=rtcengine&menulabel=core%20sdk&platform=android) or later (earlier versions cause local configurations to override cloud control)**Web**: [RTC Engine Web 5.10.0](https://www.npmjs.com/package/trtc-sdk-v5) or later (earlier versions do not support this feature)**Production Deployment:**The above latency configuration is for testing only. For production deployment, [contact us](https://trtc.io/contact) for cloud control configuration.If latency remains unsatisfactory, [contact us](https://trtc.io/contact) for further optimization.

3. **Keep firmware up to date**

Camera firmware with integrated RTC Engine SDK is continuously optimized for latency reduction. Upgrade to the latest firmware version when experiencing latency issues.

4. **Optimize video encoding parameters**

```
# Video encoding settingsencoding format: H264resolution: 1080P/720P/540P/360P # Set based on clarityBitrate control: VBR # Variable bitrateI-frame interval: 50 # 1-200 Lower I-frame interval reduces delayBitrate: 2000kbps/1200kbps/850kbps/550kbps # Bitrate setting, higher bitrate improves clarityFrame rate: 30 # 20-60 fpsBaseProfile: enable # Disabling B-frames in BaseProfile can further reduce delay
```

5. **Enable cloud control optimization.**

Activate the QoS low-latency policy to reduce jitter buffer caching and significantly lower streaming latency. [Contact us](https://trtc.io/contact) to enable this feature.

### First Frame Time Optimization

In online claw machine and coin pusher scenarios, first frame loading speed directly impacts user experience. **First frame time** is the total duration from when a user clicks to enter a room until the first visual is rendered.

**Common Bottlenecks:**

- Business API response delays (authentication, room information retrieval)
- Resource contention between component loading and stream playback

Use instrumentation to identify and resolve bottlenecks at each stage, as illustrated below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/777a6911d65711f0929b525400bf7822.png)

**Optimization Strategies:**

1. **API preloading**: Request authentication and room information asynchronously to reduce critical path dependencies.
2. **Prioritize RTC streaming**: Complete RTC Engine room entry and stream playback before loading other services.
3. **Dynamic downgrade**: Disable optional features (such as gift animations) under weak network conditions.

### Android Camera Video Quality Optimization

Some cameras require Android system motherboards to implement streaming (RTMP+RTC) without native RTC Engine SDK integration. The following techniques optimize video quality on legacy devices by leveraging hardware encoding capabilities:

1. **Custom video capture**: Directly call system APIs to capture camera feed, enabling flexible parameter adjustment and easier debugging.

```
// Enable custom video capturemTRTCCloud.enableCustomVideoCapture(TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, true);mTRTCCloud.setDefaultStreamRecvMode(false, false);// Enable custom camera captureprivate CustomCameraCapture mCustomCameraCapture;private CustomFrameRender   mCustomFrameRender;// Use video texture to process collected data, reduce memory consumption, and send video framesprivate CustomCameraCapture.VideoFrameReadListener mVideoFrameReadListener = new CustomCameraCapture.VideoFrameReadListener() {    @Override    public void onFrameAvailable(EGLContext eglContext, int textureId, int width, int height) {        TRTCCloudDef.TRTCVideoFrame videoFrame = new TRTCCloudDef.TRTCVideoFrame();        videoFrame.texture = new TRTCCloudDef.TRTCTexture();        videoFrame.texture.textureId = textureId;        videoFrame.texture.eglContext14 = eglContext;        videoFrame.width = width;        videoFrame.height = height;        videoFrame.pixelFormat = TRTCCloudDef.TRTC_VIDEO_PIXEL_FORMAT_Texture_2D;        videoFrame.bufferType = TRTCCloudDef.TRTC_VIDEO_BUFFER_TYPE_TEXTURE;        mTRTCCloud.sendCustomVideoData(TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG ,videoFrame);    }};mCustomCameraCapture = new CustomCameraCapture();mCustomFrameRender = new CustomFrameRender(mUserId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);// Start camera capturemCustomCameraCapture.startInternal(mVideoFrameReadListener);// Set custom rendermTRTCCloud.setLocalVideoRenderListener(TRTCCloudDef.TRTC_VIDEO_PIXEL_FORMAT_Texture_2D, TRTCCloudDef.TRTC_VIDEO_BUFFER_TYPE_TEXTURE, mCustomFrameRender);final TextureView textureView = new TextureView(this);mLocalRenderView.addVideoView(textureView);mCustomFrameRender.start(textureView);
```

> **Infoï¼**For complete custom video pre-processing code, see [Demo](https://github.com/Tencent-RTC/TRTC_Android/blob/main/TRTC-API-Example/Advanced/CustomCamera/src/main/java/com/tencent/trtc/customcamera/CustomCameraActivity.java).

2. **Video hardware encoding**: Use the experimental API [callExperimentalAPI](https://trtc.io/document/50762?platform=android&product=rtcengine&menulabel=core%20sdk#c6c3457a98b055087f5811b88b663ad7) and set both width and height to multiples of 16 to adapt to Android device hardware encoding parameters. The following are two reference video parameter groups:
  - High resolution encoding parameters: 768x1024 20fps 1500kbps.
  - Medium resolution encoding parameters: 480x640 20fps 900kbps.

```
public static final int ENCODE_WIDTH = 480;public static final int ENCODE_HEIGHT = 640;JSONObject jsonObject = new JSONObject();try {    jsonObject.put("api", "setVideoEncodeParamEx");    JSONObject params = new JSONObject();    params.put("codecType", 1);    params.put("videoWidth", ENCODE_WIDTH);    params.put("videoHeight", ENCODE_HEIGHT);    params.put("videoFps", 20);    params.put("videoBitrate", 1500);    params.put("minVideoBitrate", 300);    params.put("streamType", 0);    params.put("resolutionMode", 1);    jsonObject.put("params", params);} catch (JSONException e) {    throw new RuntimeException(e);}mTRTCCloud.callExperimentalAPI(jsonObject.toString());
```

3. **Speech audio capture**: Due to low latency requirements, audio functionality is necessary. However, Android devices may have insufficient audio performance. If using default audio quality, performance may not meet requirements. Call the [startLocalAudio](https://trtc.io/document/50762?platform=android&product=rtcengine&menulabel=core%20sdk#a127184d8d223906a5413d9610d6d22d) API and set the [TRTC_AUDIO_QUALITY_SPEECH](https://trtc.io/document/50768?platform=android&product=rtcengine&menulabel=core%20sdk#9ccda47c68c6d873c7938428e0f9fd5d) parameter.

```
mTRTCCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_SPEECH);
```

4. **Use the latest Android SDK**: The Android SDK is continuously optimized in new versions, so always use the latest version for debugging.

## Supporting Products

| System Level | Product Name | Applicable Scenarios |
| --- | --- | --- |
| Access Layer | [RTC Engine](https://trtc.io/document/35078?product=rtcengine&menulabel=core%20sdk&platform=android) | Provides low-latency, high-quality real-time audio and video interaction solutions, serving as the foundational infrastructure for audio/video call scenarios. |
| Cloud Services | [Video on Demand (VOD)](https://www.tencentcloud.com/document/product/266) | Offers integrated high-quality media services for audio-video content, including production and upload, storage, transcoding, media processing, media AI, accelerated distribution and playback, and copyright protection. |
| Data Storage | [Cloud Object Storage (COS)](https://www.tencentcloud.com/document/product/436) | Provides storage services for audio and video recording files and audio and video slicing files. |


---
*Source: [https://trtc.io/document/75310](https://trtc.io/document/75310)*
