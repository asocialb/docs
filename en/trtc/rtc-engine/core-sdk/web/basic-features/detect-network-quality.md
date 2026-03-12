# Detect Network Quality

Before entering the room or during the call, you can check the user's network quality to check the current network quality. If the user's network quality is poor, it is recommended to guide users to check their network to ensure normal call quality.

This tutorial mainly introduces how to implement network quality detection before the call or during the call based on the [NETWORK_QUALITY](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.NETWORK_QUALITY) event.

## Detect Network Quality During the Call

Refer to [NETWORK_QUALITY](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.NETWORK_QUALITY).

```
const trtc = TRTC.create();trtc.on(TRTC.EVENT.NETWORK_QUALITY, event => {   console.log(`network-quality, uplinkNetworkQuality:${event.uplinkNetworkQuality}, downlinkNetworkQuality: ${event.downlinkNetworkQuality}`)   console.log(`uplink rtt:${event.uplinkRTT} loss:${event.uplinkLoss}`)   console.log(`downlink rtt:${event.downlinkRTT} loss:${event.downlinkLoss}`)})
```

## Detect Network Quality Before the Call

### Implementation process

1. Call [TRTC.create()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.createTRTC) to create two TRTC instances, referred to as uplinkTRTC and downlinkTRTC.
2. Both TRTC instances enter the same room.
3. Use uplinkTRTC to startLocalVideo, and listen to the [NETWORK_QUALITY](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.NETWORK_QUALITY) event to detect the uplink network quality.
4. Use downlinkTRTC to startRemoteVideo, and listen to the [NETWORK_QUALITY](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.NETWORK_QUALITY) event to detect the downlink network quality.
5. The entire process lasts for about 15 seconds, and finally takes the average network quality to roughly determine the uplink and downlink network conditions.

> **Note**
> The detection process will generate a small amount of [Billing](https://www.tencentcloud.com/document/product/647/34610). If the published stream resolution is not specified, it defaults to publishing the video stream with a resolution of 640*480.

### API call sequence

![network-quality-call-sequence](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7cd0d09ce5a011eeb1eb525400b5f95f.png)

### Code Example

```
let uplinkTRTC = null; // Used to detect uplink network qualitylet downlinkTRTC = null; // Used to detect downlink network qualitylet localStream = null; // Stream used for testinglet testResult = {  // Record uplink network quality data  uplinkNetworkQualities: [],  // Record downlink network quality data  downlinkNetworkQualities: [],  average: {    uplinkNetworkQuality: 0,    downlinkNetworkQuality: 0  }}// 1. Test uplink network qualityasync function testUplinkNetworkQuality() {  uplinkTRTC = TRTC.create();  uplinkTRTC.enterRoom({    roomId: 8080,    sdkAppId: 0, // Fill in sdkAppId    userId: 'user_uplink_test',    userSig: '', // userSig of uplink_test    scene: 'rtc'  })  uplinkTRTC.on(TRTC.EVENT.NETWORK_QUALITY, event => {    const { uplinkNetworkQuality } = event;    testResult.uplinkNetworkQualities.push(uplinkNetworkQuality);  });}// 2. Detect downlink network qualityasync function testDownlinkNetworkQuality() {  downlinkTRTC = TRTC.create();  downlinkTRTC.enterRoom({    roomId: 8080,    sdkAppId: 0, // Fill in sdkAppId    userId: 'user_downlink_test',    userSig: '', // userSig    scene: 'rtc'  });  downlinkTRTC.on(TRTC.EVENT.NETWORK_QUALITY, event => {      const { downlinkNetworkQuality } = event;      testResult.downlinkNetworkQualities.push(downlinkNetworkQuality);  })}// 3. Start detectiontestUplinkNetworkQuality();testDownlinkNetworkQuality();// 4. Stop detection after 15s and calculate the average network qualitysetTimeout(() => {  // Calculate the average uplink network quality  if (testResult.uplinkNetworkQualities.length > 0) {    testResult.average.uplinkNetworkQuality = Math.ceil(      testResult.uplinkNetworkQualities.reduce((value, current) => value + current, 0) / testResult.uplinkNetworkQualities.length    );  }  if (testResult.downlinkNetworkQualities.length > 0) {    // Calculate the average downlink network quality    testResult.average.downlinkNetworkQuality = Math.ceil(      testResult.downlinkNetworkQualities.reduce((value, current) => value + current, 0) / testResult.downlinkNetworkQualities.length    );  }      // Detection is over, clean up related states.  uplinkTRTC.exitRoom();  downlinkTRTC.exitRoom();}, 15 * 1000);
```

## Result Analysis

After the above steps, you can get the average uplink network quality and the average downlink network quality. The enumeration values of network quality are as follows:

| Value | Meaning |
| --- | --- |
| 0 | The network quality is unknown, indicating that the current TRTC instance has not established a media connection |
| 1 | The network quality is excellent |
| 2 | The network quality is good |
| 3 | The network quality is average |
| 4 | The network quality is poor |
| 5 | The network quality is extremely poor |
| 6 | The network connection has been disconnected. Note: If the downlink network quality is this value, it means that all downlink connections have been disconnected. |

> **Suggestion**When the network quality is greater than 3, it is recommended to guide the user to check the network and try to change the network, otherwise it is difficult to ensure normal audio and video call.
> You can also reduce bandwidth consumption through the following strategies:If the uplink network quality is greater than 3, you can reduce the bitrate through the [trtc.updateLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalVideo) interface or close the video through the [trtc.stopLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalVideo) method to reduce uplink bandwidth consumption.If the downlink network quality is greater than 3, you can reduce the downlink bandwidth consumption by subscribing to a small stream (refer to: [Optimize Multi-Person Video Calls](https://www.tencentcloud.com/document/product/647/59665)) or only subscribing to audio.


---
*Source: [https://trtc.io/document/59655](https://trtc.io/document/59655)*
