# Custom Capturing and Rendering

This tutorial mainly introduces the advanced usage of custom capturing and custom rendering.

## Custom Capturing

By default, [trtc.startLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) and [trtc.startLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalAudio) will start camera and microphone, [trtc.startScreenShare()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startScreenShare) will start screen sharing.

You can specify the audioTrack or videoTrack parameters of [trtc.startLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) [trtc.startLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalAudio) [trtc.startScreenShare()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startScreenShare) to publish the custom capturing [MediaStreamTrack](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack).

```
// Passing an audioTrack parameter to publish a custom audioTrack.await trtc.startLocalAudio({ option: { audioTrack }});// If microphoneId and audioTrack are set at the same time, the capture priority is // microphoneId > audioTrack, but it is not recommended to mix them.
```

```
// Passing an videoTrack parameter to publish a custom videoTrack on the main stream.await trtc.startLocalVideo({ option: { videoTrack }});// If you set cameraId, useFrontCamera, videoTrack at the same time, the capture priority is// cameraId > useFrontCamera > videoTrack, but it is not recommended to mix them.
```

```
// Passing an videoTrack parameter to publish a custom videoTrack on the sub stream.await trtc.startScreenShare({ option: { videoTrack }});
```

> ****[What is the main/sub stream?](https://trtc.io/document/37340#what-is-the-main-sub-stream)

There are usually several ways to capture audioTrack and videoTrack:

- Use [getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia) to capture the camera and microphone.
- Use [getDisplayMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getDisplayMedia) to capture screen sharing.
- Use [videoElement.captureStream](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/captureStream) to capture the audio and video being played in the video tag.
- Use [canvas.captureStream](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/captureStream) to capture the content in the canvas.

### Capture the Video Being Played in the Video Element

```
// Check if your current browser supports capturing streams from video elementsif (!HTMLVideoElement.prototype.captureStream) {  console.log('your browser does not support capturing stream from video element');  return}// Get the video tag that is playing video on your pageconst video = document.getElementById('your-video-element-ID');// Capture the video stream from the playing videoconst stream = video.captureStream();const audioTrack = stream.getAudioTracks()[0];const videoTrack = stream.getVideoTracks()[0];await trtc.startLocalVideo({ option:{ videoTrack } });await trtc.startLocalAudio({ option:{ audioTrack } });
```

### Capture the Content in the Canvas

```
// Check if your current browser supports capturing streams from canvas elementsif (!HTMLCanvasElement.prototype.captureStream) {  console.log('your browser does not support capturing stream from canvas element');  return}// Get your canvas tagconst canvas = document.getElementById('your-canvas-element-ID');// Capture a 15 fps video stream from the canvasconst fps = 15;const stream = canvas.captureStream(fps);const videoTrack = stream.getVideoTracks()[0];await trtc.startLocalVideo({ option:{ videoTrack } });
```

## Custom Rendering

By default, when calling [trtc.startLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) or [trtc.startRemoteVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo), you need to pass in the **view** parameter. The SDK will create a video element under the specified **view** element to play the video.

If you need to customize the rendering, and do not need the SDK to play the video, you can refer to the following steps:

1. Do not fill in the **view** parameter or pass in **null** when calling the [trtc.startLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) or [trtc.startRemoteVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo).
2. Listen for the [TRTC.EVENT.TRACK](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.TRACK) event, the SDK will trigger this event when there is a new MediaStreamTrack, then you can get the MediaStreamTrack for custom rendering.
3. Use your own player for video rendering.
4. If you use custom rendering, the [VIDEO_PLAY_STATE_CHANGED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.VIDEO_PLAY_STATE_CHANGED) event will not be triggered. You need to listen for the **mute/unmute/ended**events of the video track [MediaStreamTrack](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack) to detect the state of the video track.

```
trtc.on(TRTC.EVENT.TRACK, event => {  // userId === '' means event.track is a local track, otherwise it's a remote track  const isLocal = event.userId === '';   // Usually the sub stream is a screen-sharing video stream.  const isSubStream = event.streamType === TRTC.TYPE.STREAM_TYPE_SUB;   const mediaStreamTrack = event.track;   const kind = event.track.kind; // audio or video})
```


---
*Source: [https://trtc.io/document/59663](https://trtc.io/document/59663)*
