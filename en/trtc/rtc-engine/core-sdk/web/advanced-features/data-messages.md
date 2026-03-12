# Data Messages

There are two ways to transfer your application data messages to the users in the room.

## Demo

## Custom Message

- Supported SDK version: v5.6.0+
- Only [TRTC.TYPE.ROLE_ANCHOR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.ROLE_ANCHOR) can call [trtc.sendCustomMessage](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#sendCustomMessage).
- You should call this api after [TRTC.enterRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom) successfully.
- The custom message will be sent in order and as reliably as possible, but it's possible to loss messages in a very bad network. The receiver will also receive the message in order.

### Send Custom Message

| Name | Type | Description |
| --- | --- | --- |
| cmdId | number | `required`message Id. Integer, range [1, 10]. You can set different cmdId for different types of messages to reduce the delay of transferring message. |
| data | ArrayBuffer | `required`message data.Maximum 1KB(Byte) sent in a single call.Maximum 30 calls per secondMaximum 8KB sent per second. |

```
const trtc = TRTC.create();await trtc.enterRoom({ sdkAppId, userId, userSig, roomId: 12345 })// send custom messageconst data = new TextEncoder().encode('hello').buffer;trtc.sendCustomMessage({ cmdId: 1, data });
```

### Receive Custom Message

Listen for the event [TRTC.EVENT.CUSTOM_MESSAGE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.CUSTOM_MESSAGE) to receive custom message.

```
// receive custom messagetrtc.on(TRTC.EVENT.CUSTOM_MESSAGE, event => {   // event.userId: remote userId.   // event.cmdId: message cmdId.   // event.seq: message sequence number.   // event.data: custom message data, type is ArrayBuffer.   console.log(`received custom msg from ${event.userId}, message: ${new TextDecoder().decode(event.data)}`)})
```

## SEI Message

The header of a video frame has a header block called supplemental enhancement information (**SEI**). It is additional data inserted into the video bitstream to convey extra information. You can add a lot of information into SEI, such as parameters of the camera or encoder; time; closed captions; lyrics; and copyright info.

### Send SEI Message

You can use [trtc.sendSEIMessage](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#sendSEIMessage) to send SEI message. Because the SEI is inserted to the video stream, you should call it after you started local video.

```
// 1. enable SEIconst trtc = TRTC.create({ enableSEI: true })// 2. enter room & start local videoawait trtc.enterRoom({ sdkAppId, userId, userSig, roomId: 12345 })await trtc.startLocalVideo();// 3. send SEIconst unit8Array = new Uint8Array([1, 2, 3]);trtc.sendSEIMessage(unit8Array.buffer);
```

> **Note:**Supported SDK version: v5.3.0+. Supported browsers: Chrome 86+, Edge 86+, Opera 72+ browsers(Chromium Based Browser M86+).Maximum 1KB(Byte) sent in a single call, maximum 30 calls per second, maximum 8KB sent per second.Since SEI is sent along with video frames, there is a possibility that video frames may be lost due to poor network, and therefore SEI may be lost as well. The number of times it can be sent can be increased within the frequency limit, and the business side needs to do message de-duplication on the receiving side.SEI cannot be sent without [trtc.startLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) and cannot be received without [trtc.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo).Only H264 encoder is supported to send and receive SEI.

### Receive SEI Message

Refer to [TRTC.EVENT.SEI_MESSAGE](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.SEI_MESSAGE)

```
// 1. enable SEIconst trtc = TRTC.create({ enableSEI: true })// 2. receive SEItrtc.on(TRTC.EVENT.SEI_MESSAGE, event => { console.log(`received sei message from ${event.userId}, data: ${event.data}, streamType: ${event.streamType}`)})
```


---
*Source: [https://trtc.io/document/59662](https://trtc.io/document/59662)*
