# Optimize Multi-Person Video Calls

In the multi-person video call scenario, as the number of streaming users increases, both bandwidth consumption and device performance consumption will rise for users who are subscribing streams. If no optimization is done, the experience on low-end devices will be greatly compromised.

This tutorial mainly introduces the best practices for multi-person video call scenario. Through the following two solutions, you can reduce bandwidth consumption and ensure the best call experience.

- **Enable Small Stream**
- **Enable "receiveWhenViewVisible"**

## Enable Small Stream

The small stream refers to encoding two video streams at the same time when the camera is turned on. One is a normal resolution video (referred to as the big stream), and the other is a low-resolution video (referred to as the small stream). At the receiving end, you can choose to receive the big stream or the small stream to save bandwidth.

Applicable scenarios: The small stream is suitable for multi-person video call scenario. Generally, in the page layout of multi-person video call scenario, there will be "a big view and a lot of small view". The video in the big view is the big stream, and the video in the small view is the small stream. This feature will increase the upstream bandwidth slightly, but it can greatly save the downstream bandwidth.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/67c21a53e5ec11ee91ba525400aa857d.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ff14103de5ea11ee8b625254005cb287.png)

### Publish Small Stream on the Publisher

When calling [trtc.startLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo), you can set the **small** parameter to enable small stream encoding.

```
await trtc.startLocalVideo({ option: { small: '120p' }});
```

Since version 5.3.0+, you can turn on/off dynamically the small stream.

```
await trtc.startLocalVideo();// turn on small streamawait trtc.updateLocalVideo({ option: { small: '120p' }});// turn off small streamawait trtc.updateLocalVideo({ option: { small: false }});
```

> **Note**In an environment that does not support enabling small streams, the small parameter will not take effect and will not report an error.

### Subscribe Small Stream on the Subscriber

You can set the **small** parameter of [trtc.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo) to subscribe the small stream. Otherwise, the big stream is subscribed by default.

```
trtc.on(TRTC.EVENT.REMOTE_VIDEO_AVAILABLE, ({ userId, streamType }) => {  trtc.startRemoteVideo({     view: '', // Pass in the elementId or element instance object of the video container.    userId,     streamType,     option: { small: true }  });})
```

> **Note**There is no need to check whether the remote user has published the small stream in advance when subscribing the small stream. If the remote end does not publish the small stream, the SDK will automatically subscribe the big stream.

You can also set the small parameter of [trtc.updateRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateRemoteVideo) to chose subscribing big stream or small stream. It is commonly used to implement the following feature:

- Playing remote video on "big view" when the user clicks the "small view"
- Playing remote video on "small view" when the user clicks the "big view"

```
// Switch to "big view" playback when the user clicks the "small view".await trtc.updateRemoteVideo({   view: '', // Pass in the elementId or element instance object of the "big view" video container.  userId: '', // Pass in the userId of the remote user.  streamType: TRTC.TYPE.STREAM_TYPE_MAIN,   option: { small: false }})// Switch to "small view" playback when the user clicks the "big view".await trtc.updateRemoteVideo({   view: '', // Pass in the elementId or element instance object of the "small view" video container.  userId: '', // Pass in the userId of the remote user.  streamType: TRTC.TYPE.STREAM_TYPE_MAIN,   option: { small: true }})
```

> **Note:**TRTC's video stream has a main stream and a sub stream. The main stream includes the big stream and the small stream, and the sub stream is generally used for screen sharing.When subscribing the video stream, the main stream defaults to subscribe the big stream, and the small parameter can be used to subscribe the small stream.TRTC supports subscribe the **big stream + sub stream**, **small stream + sub stream**, and does not support subscribe the **big stream + small stream** at the same time. The big stream and the small stream are played in the same video view.Only when the publisher enables the small stream, the remote main stream will be switched to the small stream when the small parameter is specified. If there is no small stream, the SDK will automatically subscribe the big stream.There is currently no event notification for successful switching between big and small streams.

## Enable "receiveWhenViewVisible"

In general, in a multi-person video scenario, due to the limitaion of web page size, the subscriber will not display all videos on the page. Therefore, for those remote videos that do not need to be displayed on the page, they do not need to be subscribed. Only when the view is visible should the video stream be subscribed. This is to save traffic and reduce performance overhead.

However, Implementing this feature is not easy for you. Starting with version 5.4.0, the SDK has built-in support for this feature. You only need to set the **receiveWhenViewVisible** and **viewRoot** parameters when calling [trtc.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo) to enable this feature, which is very convenient and fast.

The SDK will automatically check the visibility state of the **view** passed in [trtc.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo). Video streaming will start when the **view** is visible and stop when **view** is not visible.

### Sample code

Assuming your DOM structure for playing videos is as follows:

```
<div id='view-list'>  <div id='view1_main'></div>  <div id='view2_main'></div>  <div id='view3_main'></div></div>
```

```
trtc.on(TRTC.EVENT.REMOTE_VIDEO_AVAILABLE, ({ userId, streamType }) => {  trtc.startRemoteVideo({     view: 'view1_main',    userId,     streamType,     option: {       small: true,      // Enable "receiveWhenViewVisible"      receiveWhenViewVisible: true,       // Pass in the first-level parent element of all view list,       // which is used to calculate the reference relationship between view and viewRoot       // and check whether the view is visible. The default value is document.body.      viewRoot: document.getElementById('view-list')     }  });})
```

### Add loading effect for better user experience

After enabling this feature, when the user scrolls through the video list:

- When the view changes from visible to invisible, the SDK will stop streaming.
- When the view changes from invisible to visible, the SDK will resume streaming.

Since resuming streaming until the video playback is successful is an asynchronous process, a black screen may appear during this process. To provide a better user experience, we recommend adding a loading effect to the video area during this asynchronous process.

You can refer to the following code to check whether to display the loading effect.

```
let isLoading = true;trtc.on(TRTC.EVENT.VIDEO_PLAY_STATE_CHANGED, ({ userId, streamType, state }) => {  // '' is local video  if (userId !== '') return;  // set isLoading to false when remote video is playing.  isLoading = state !== 'PLAYING';  // You can tell which remote user's main/sub stream playback state has changed  // by userId and streamType.});await trtc.stopRemoteVideo({ userId, streamType })// set isLoading to false after stop remote video.isLoading = false;
```

## FAQ

### How does the SDK detect whether a view is visible?

When any pixel point of the view appears in the **viewRoot** area, the view is considered visible. Conversely, when all pixel points of the view are not in the **viewRoot** area, the view is considered invisible.

### Do I need to consider browser compatibility for big and small streams?

Although some browsers do not support enabling big and small streams (such as all browsers on iOS systems and Chrome versions below 63), enabling small stream has no side effects. If the environment does not support it, the SDK will only use the big stream, and the call can proceed normally. You do not need to write additional if-else statements.

You can call [TRTC.isSupported](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.isSupported) to get checkResult.detail.isSmallStreamSupported to confirm whether the current environment supports enabling small stream.


---
*Source: [https://trtc.io/document/59665](https://trtc.io/document/59665)*
