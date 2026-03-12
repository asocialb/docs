# Web Push

The TXLivePusher SDK is used to push streams for LEB (ultra-low latency streaming). It can push audio and video the browser captures from the camera, screen, or a local media file to live streaming servers via WebRTC.

You can use the WebRTC protocol for live streaming on the web. On the PC side, you can also use the OBS tool for WebRTC live streaming. For specific operation methods, please refer to the [OBS WebRTC Live Streaming](/document/product/267/57042) related content.

The advantage of using Web for WebRTC live streaming is that there is no need to install additional software, and you can operate directly in the browser. This article will introduce the operation method for live streaming using **Web**.

> **Note**With WebRTC, each push domain name can be used for up to **1000 concurrent streams** by default. If you want to push more streams, please [submit a ticket](https://console.tencentcloud.com/workorder/category).

## Basics

Below are some basics you need to know before integrating the SDK.

### Splicing push URLs

To use Tencent Cloud live streaming services, you need to splice push URLs in the format required by Tencent Cloud, which consists of four parts.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9081715851e911ee84f2525400494e51.png)

An authentication key is not required. You can enable push authentication if you need hotlink protection. For details, see [Splicing Live Streaming URLs](https://intl.cloud.tencent.com/document/product/267/38393).

### Browser support

Web live streaming is based on WebRTC implementation and relies on the operating system and browser support for WebRTC. Currently, the latest versions of Chrome, Edge, Firefox, and Safari browsers support Web live streaming.

> **Note：**The audio/video capturing feature is poorly supported on mobile browsers. For example, mobile browsers do not support screen recording, and only iOS 14.3 and later allow requesting camera access. Therefore, the push SDK is mainly used on desktop browsers. The latest version of Chrome, Firefox, and Safari all support push for LEB.

## SDK Integration

### Step 1. Prepare the page

Add an initialization script to the (desktop) page from which streams are to be pushed.

```
<script src="https://video.sdk.qcloudecdn.com/web/TXLivePusher-2.1.1.min.js" charset="utf-8"></script>
```

> **Note**The script needs to be imported into the `body` part of the HTML code. If it is imported into the `head` part, an error will be reported.

### Step 2. Add a container to the HTML page

Add a player container to the section of the page where local video is to be played. This is achieved by adding a div and giving it a name, for example, `id_local_video`. Local video will be rendered in the container. To adjust the size of the container, style the div using CSS, Below is an example code:

```
<div id="id_local_video" style="width:100%;height:500px;display:flex;align-items:center;justify-content:center;"></div>
```

### Step 3. Push streams

1. **Generate an instance of the push SDK:**

Generate an instance of the global object `TXLivePusher`. All subsequent operations will be performed via the instance.

```
const livePusher = new TXLivePusher();
```

2. **Specify the local video player container:**
Specify the div for the local video player container, which is where audio and video captured by the browser will be rendered.

```
livePusher.setRenderView('id_local_video');
```

> **Note**The video element generated via `setRenderView`is unmuted by default. To mute video, obtain the video element using the code below.livePusher.videoView.muted = true;=

3. **Set audio/video quality:**
Audio/video quality should be set before capturing. You can specify quality parameters if the default settings do not meet your requirements.

```
// Set video qualitylivePusher.setVideoQuality('720p');// Set audio qualitylivePusher.setAudioQuality('standard');// Set the frame rate
```

4. **Capture streams:**
You can capture streams from the camera, mic, screen and local media files. If capturing is successful, the player container will start playing the audio/video captured.

```
// Turn the camera onlivePusher.startCamera();// Turn the mic onlivePusher.startMicrophone();
```

5. **Push streams:**
Pass in the LEB push URL to start pushing streams. For the format of push URLs, see[Splicing Live Streaming URLs](/document/product/267/57043#8a99c4e5-7eef-4a86-aa38-bb88b3701254). You need to replace the prefix `rtmp://` with `webrtc://`.

```
livePusher.startPush('webrtc://domain/AppName/StreamName?txSecret=xxx&txTime=xxx');
```

> **Note**Before push, make sure that audio/video streams are captured successfully, or you will fail to call the push API. You can use the code below to push streams automatically after audio/video is captured, that is, after the callback for capturing the first audio or video frame is received. If both audio and video are captured, push starts only after both the callback for capturing the first audio frame and that for the first video frame are received.// Automatically push the stream after collecting the camera footagelivePusher.startCamera().then(function () { livePusher.startPush('webrtc://domain/AppName/StreamName?txSecret=xxx&txTime=xxx');}).catch(function (error) { console.log('Failed to open camera: '+ error.toString());});
> // Automatically push the stream after collecting the camera and microphonePromise.all([livePusher.startCamera(), livePusher.startMicrophone()]).then(function() { livePusher.startPush('webrtc://domain/AppName/StreamName?txSecret=xxx&txTime=xxx');});

6. **Stop push:**

```
livePusher.stopPush();
```

7. **Stop capturing audio and video:**

```
// Turn the camera offlivePusher.stopCamera();// Turn the mic offlivePusher.stopMicrophone();
```

## Advanced Features

### Compatibility

The SDK provides a static method to check whether a browser supports WebRTC.

```
TXLivePusher.checkSupport().then(function(data) {    // Whether WebRTC is supported    if (data.isWebRTCSupported) {        console.log('WebRTC Support');    } else {        console.log('WebRTC Not Support');    }    // Whether H.264 is supported    if (data.isH264EncodeSupported) {        console.log('H264 Encode Support');    } else {        console.log('H264 Encode Not Support');    }});
```

### Event callbacks

The SDK supports callback event notifications. You can set an observer to receive callbacks of the SDK’s status and WebRTC-related statistics.

```
livePusher.setObserver({
  // Warnings for push
  onWarning: function(code, msg) {
    console.log(code, msg);
  },
  // Push status
  onPushStatusUpdate: function(status, msg) {
    console.log(status, msg);
  },
```

### Device management

You can use a device management instance to get the device list, switch devices, and perform other device-related operations.

```
const deviceManager = livePusher.getDeviceManager();let cameraDeviceId = null;// Get device listdeviceManager.getDevicesList().then(function(data) {  data.forEach(function(device) {    console.log(device.type, device.deviceId, device.deviceName);    if (device.type === 'video') {      cameraDeviceId = device.deviceId;    }  });  // Switch camera device  if (cameraDeviceId) {    deviceManager.switchCamera(cameraDeviceId);  }});
```


---
*Source: [https://www.tencentcloud.com/document/product/267/57043](https://www.tencentcloud.com/document/product/267/57043)*
