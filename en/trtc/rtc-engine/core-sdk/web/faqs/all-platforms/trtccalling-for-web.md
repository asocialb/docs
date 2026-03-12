# TRTCCalling for Web

## Basics

### What is TRTCCalling?

TRTCCalling is an RTC solution based on TRTC and TIM. It supports one-to-one and group audio/video calls and allows quick integration.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3bf198dc3a7c11ed8e47525400463ef7.png)

### Does TRTCCalling support string-type `roomID`?

`roomID` can be a string, but it must be a numeric string.

## Environment

### What browsers does the TRTC Web SDK support?

For details about browser support, please see [Browsers Supported](https://web.sdk.qcloud.com/trtc/webrtc/doc/zh-cn/tutorial-05-info-browser.html).
If your browser is not listed in the above document, you can open the [TRTC compatibility check](https://web.sdk.qcloud.com/trtc/webrtc/demo/detect/index.html) page with the browser to test whether it fully supports WebRTC.

### How do I test my current network quality?

Please see [Network Quality Check Before Calls](https://web.sdk.qcloud.com/trtc/webrtc/doc/zh-cn/tutorial-24-advanced-network-quality.html) for detailed directions.

### I can run the Chat H5 demo successfully locally, but when it is deployed to the server and accessed via an IP address, I canât make audio/video calls. What should I do?

- **Background**: After running the Chat H5 demo locally, the user can send messages and make audio/video calls using localhost. When the project is deployed to the server and accessed via an IP address, text messages can be sent and received, the server responds to console requests properly, and the console reports no errors, but the user fails to make audio/video calls and cannot obtain video.
- **Cause**: Chat uses the TRTCCalling SDK for audio/video calls, but the user uses HTTP for access.
- **Solution**: Make sure the TRTCCalling SDK is accessed via HTTPS or localhost.

## Integration

### Why canât I receive the `NO_RESP` event in the online demo of TRTCCalling?

- **Solution**: You will receive the event when both conditions are met.

### What should I do if I canât hear the audio of remote users when accessing TRTCCalling using WeChatâs built-in browser on iOS?

- Solution: We have addressed this problem in v1.0.0. Please update TRTCCalling to v1.0.0 or a later version.

### What should I do if the error âuncaught (in promise) TypeError: cannot read property 'stop' of nullâ occurs when I call `hangup()` of TRTCCalling?

- **Solution**: You only need to call `hangup()` once. The subsequent operations are performed within TRTCCalling. You only need to pay attention to operations related to your business.

### On Chrome 90, `trtccalling.js` prompts âUnsupported TRTCClient. Your browser is not compatible with the applicationâ. What should I do?

- **Cause**: Your Chat version is too old. It does not have a compatibility check mechanism.
- **Solution**: Update Chat to the latest version.

### What should I do if the error âTypeError: Cannot read property 'getVideoTracks' of nullâ occurs when I make a call?

- **Solution**: Call device-related APIs (such as `startRemoteView` and `startLocalView`) asynchronously, or update TRTCCalling to v1.0.0.

### What should I do if the error âTSignaling._onMessageReceived unknown bussinessID=undefinedâ occurs in an application (`SDKAppID`) that imports TRTCCalling via script?

- **Cause**: `bussinessId=undefined` indicates that the TSignaling version is too old. The signaling feature in old TSignaling versions is flawed.
- **Solution**: Update TSignaling and make sure that **the file name of TSignaling is**`tsignaling-js`**during import.**

### What should I do if the error âUncaught (in promise) Error: You can call `createCustomMessage` only when the SDK is readyâ occurs?

- **Solution**: Update TRTCCalling to v1.0.0 and call the API after receiving the `SDK_READY` callback.

### What should I do if the error âUncaught (in promise) RTCError: duplicated play() call observed, please stop() firstly <INVALID_OPERATION 0x1001>â occurs?

- **Solution**: Do not call `startRemoteView` during an audio call.

### What should I do if the error âUncaught (in promise) Error: inviteID is invalid or invitation has been processedâ occurs?

- **Cause**: A user can enter a TRTC room without granting access to audio/video devices, but if the user hangs up, a user in a native application will not be notified.
- **Solution**: TRTCCalling 1.0.0 requests camera/mic access beforehand and does not allow users to enter a room before they grant the access. We recommend you update TRTCCalling to v1.0.0 or a later version.

### After a call is made, log is printed at the callee side (which indicates that the call invitation is received), but why is the `handleNewInvitationReceived` callback not received?

- **Solution**: Update TRTCCalling and TSignaling to the latest version.

### What should I do if I fail to make another call after a call is rejected?

- **Solution**: Update TRTCCalling to v1.0.3 or a later version.

### What should I do if the error âError: TRTCCalling.call - failed to access the userâs deviceâ occurs?

- **Solution**:
  - Run the [TRTC support level test](https://web.sdk.qcloud.com/trtc/webrtc/demo/detect/index.html).
  - Check in Chrome Settings (chrome://settings/content) whether your Chrome has allowed the website using TRTCCalling to access the camera/mic.

### Does TRTCCalling for web support receiving messages offline?

- However, it supports sending offline push notifications. You can set the message to send using [offlinePushInfo](https://www.tencentcloud.com/document/product/647/46660#) in `call` or `groupCall`.


---
*Source: [https://trtc.io/document/43096](https://trtc.io/document/43096)*
