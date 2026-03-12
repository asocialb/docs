# Cross-Room Co-Hosting & Battles

In the live streaming room, to enhance the atmosphere and quickly attract followers, the anchor can invite anchors from other live streaming rooms to engage in mic connecting or online PK. The audience in the mic-connected live streaming room can listen to or watch the interaction of multiple anchors at the same time, which can increase the fun of interactive live streaming and stimulate the audience's desire to rank and give gifts. Below are three specific implementations of different cross-room PK mic-connection solutions.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/feed4e1bbead11f0b4c35254001c06ec.png)

## Regular Cross-room Mic-connection PK Solution

### **Use Cases**

A simple cross-room mic-connection scenario for two or more rooms with a small number of anchors.

### Scheme Principle

By default, only users in the same room can have audio and video communication, and the audio and video streams between different rooms are isolated. Through cross-room mic-connection, the audio and video stream of an anchor in another room can be published in the current room, while the audio and video stream of the current anchor will also be published in the target anchor's room. This allows anchors in different rooms to share audio and video streams across rooms, enabling audiences in each room to watch the audio and video of both anchors.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c8f3d4b4d7ab11ee9409525400c26da5.png)

### Implementation Process

When Anchor A in Room "101" establishes a cross-room call with Anchor B in Room "102" through [ConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50762#d7e553b397dcc62ffbe0456fdbb1c072):

- Users in room 101 will receive two event callbacks from anchor B: `onRemoteUserEnterRoom(B)` and `onUserVideoAvailable(B,true)`. Therefore, users in room 101 can subscribe to the audio and video of anchor B.
- Users in room 102 will receive two event callbacks from anchor A: `onRemoteUserEnterRoom(A)` and `onUserVideoAvailable(A,true)`. Therefore, users in room 102 can subscribe to the audio and video of anchor A.

> **Note:**For single-anchor cross-room PK between two rooms, only one anchor needs to call `ConnectOtherRoom` to establish the cross-room connection. Please do not call it in both directions.Anchors can establish cross-room connections with multiple room anchors by calling `ConnectOtherRoom` multiple times. Currently, a single anchor can connect with up to **9** other room anchors.

#### Real-time cross-room mic interaction

In an RTC scenario, the cross-room competition process is straightforward. Anchors and cross-room competition anchors mutually pull RTC single streams, and the audience simultaneously pulls the RTC single streams of both anchors and cross-room competition anchors. The audience can independently control the subscription logic of the media streams of anchors and cross-room connecting anchors. The real-time interactive cross-room call process is shown in the diagram below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98e34b55beae11f0b0cf525400e889b2.png)

> **Note:**In real-time interactive cross-room competition scenes, audiences in the room can independently control the logic of subscribing to the media streams of cross-room connecting anchors, or it can be changed by the room owner to [change the uplink capability of a cross-room anchor in their rooms](https://trtc.io/document/50762?product=rtcengine&menulabel=core%20sdk&platform=android#f74725866e0df9e3763df166f1692c88).

### Sample Code

1. Either party initiates the cross-room mic-connection PK.

Android

iOS

```
public void connectOtherRoom(String roomId, String userId) {    try {        JSONObject jsonObj = new JSONObject();        // Take the room ID string as an example, numeric room ID key:roomId        jsonObj.put("strRoomId", roomId);        jsonObj.put("userId", userId);        mTRTCCloud.ConnectOtherRoom(jsonObj.toString());    } catch (JSONException e) {        e.printStackTrace();    }}// Result callback for requesting cross-room mic-connection.@Overridepublic void onConnectOtherRoom(String userId, int errCode, String errMsg) {    // userId: The user ID of the anchor in the other room you want to initiate the cross-room link-up    // errCode: Error code. ERR_NULL indicates the request is successful    // errMsg: Error message.}
```

```
- (void)connectOtherRoom:(NSString *)roomId {    NSMutableDictionary *jsonDict = [[NSMutableDictionary alloc] init];    // Take the room ID string as an example, numeric room ID key:roomId    [jsonDict setObject:roomId forKey:@"strRoomId"];    [jsonDict setObject:self.userId forKey:@"userId"];    NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDict options:NSJSONWritingPrettyPrinted error:nil];    NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];    [self.trtcCloud connectOtherRoom:jsonString];}// Result callback for requesting cross-room mic-connection.- (void)onConnectOtherRoom:(NSString *)userId errCode:(TXLiteAVError)errCode errMsg:(NSString *)errMsg {    // userId: The user ID of the anchor in the other room you want to initiate the cross-room link-up    // errCode: Error code. ERR_NULL indicates the request is successful    // errMsg: Error message}
```

> **Note:**Both local and remote users participating in the cross-room competition must be in the anchor role and must have audio or video uplink capabilities.For single-anchor cross-room PK between two rooms, only one anchor needs to call `ConnectOtherRoom` to establish the cross-room connection. Please do not call it in both directions.

2. All users in both rooms will receive a callback indicating that the audio and video streams from the PK anchor in the other room are available.

Android

iOS

```
@Overridepublic void onUserAudioAvailable(String userId, boolean available) {    // The remote user publishes/unpublishes their audio.    // Under the automatic subscription mode, you do not need to do anything. The SDK will automatically play the remote user's audio.}@Overridepublic void onUserVideoAvailable(String userId, boolean available) {    // The remote user publishes/unpublishes the primary video.    if (available) {        // Subscribe to the remote user's video stream and bind the video rendering control.        mTRTCCloud.startRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, view);    } else {        // Unsubscribe to the remote user's video stream and release the rendering control.        mTRTCCloud.stopRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);    }}
```

```
- (void)onUserAudioAvailable:(NSString *)userId available:(BOOL)available {    // The remote user publishes/unpublishes their audio.    // Under the automatic subscription mode, you do not need to do anything. The SDK will automatically play the remote user's audio.}- (void)onUserVideoAvailable:(NSString *)userId available:(BOOL)available {    // The remote user publishes/unpublishes the primary video.    if (available) {        // Subscribe to the remote user's video stream and bind the video rendering control.        [self.trtcCloud startRemoteView:userId streamType:TRTCVideoStreamTypeBig view:self.remoteView];    } else {        // Unsubscribe to the remote user's video stream and release the rendering control.        [self.trtcCloud stopRemoteView:userId streamType:TRTCVideoStreamTypeBig];    }}
```

3. Either party exits the cross-room mic-connection PK.

Android

iOS

```
// Exiting cross-room mic-connection.mTRTCCloud.DisconnectOtherRoom();// Result callback for exiting cross-room mic-connection.@Overridepublic void onDisConnectOtherRoom(int errCode, String errMsg) {    super.onDisConnectOtherRoom(errCode, errMsg);}
```

```
// Exiting cross-room mic-connection.[self.trtcCloud disconnectOtherRoom];// Result callback for exiting cross-room mic-connection.- (void)onDisconnectOtherRoom:(TXLiteAVError)errCode errMsg:(NSString *)errMsg {}
```

> **Note:**Either the initiator or the receiver of the cross-room mic-connection PK can call [DisconnectOtherRoom](https://trtc.io/document/50762?product=rtcengine&menulabel=core%20sdk&platform=android#71e28e2184ffae717c6d768d9f757ad7) to end the cross-room mic-connection PK.

## Server-Side Cross-Room Mic-Connection PK Solution

### **Use Cases**

Multiple rooms PK, each room has multiple anchors pure server-side cross-room mic-connection scenario.

### Scheme Principle

The server initiates multiple mixed-stream forwarding tasks. Each forwarding task pulls an Agent robot user into its RTC Engine room to pull the stream and simultaneously pulls one or more Feed robot users to push the mixed audio and video stream back to other RTC Engine rooms participating in the cross-room PK and mic connection. This way, users in different rooms can subscribe to the mixed-stream pusback audio and video streams of other rooms, realizing cross-room PK and mic connection.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5c3e09e1c37011f0a6dd5254005ef0f7.png)

### Implementation Process

#### Real-Time Cross-Room Mic Interaction

1. Host of Room A initiates a cross-room PK request (business signaling) to Host of Room B and Host of Room N.
2. Host of Room B and Host of Room N agree to the cross-room PK request (business signaling).
3. The business backend simultaneously starts N mixed-stream pushing room tasks [StartPublishCdnStream](https://www.tencentcloud.com/document/api/647/48247).
  - Task 1: A_Agent robot receives the media stream of Room A's host, and after mixed-streaming by the RTC Engine backend, A_Feed robot pushes it back to Room B and Room N.
  - Task 2: B_Agent robot receives the media stream of Room B's host, and after mixed-streaming by the RTC Engine backend, B_Feed robot pushes it back to Room A and Room N.
  - Task N: N_Agent robot receives the media stream of Room N's host, and after mixed-streaming by the RTC Engine backend, N_Feed robot pushes it back to Room A and Room B.
4. Users in Room A, Room B, and Room N pull the mixed audio and video streams from each other and start cross-room PK.
5. When cross-room PK ends, the business backend stops the N hybrid push-back room tasks through TaskId [StopPublishCdnStream](https://www.tencentcloud.com/document/api/647/48246).

> **Note:**This solution supports up to 11 rooms for cross-room PK with link-mic simultaneously, and each room supports up to 16 hosts for link-mic simultaneously.The robot ID must not conflict with the IDs of regular users in the room, or the forwarding tasks may end abnormally if the robot user is kicked out of the RTC Engine room.

### Sample Code

The following example shows the parameter body for cross-room PK hybrid push-back room tasks in a pure audio scene.

Task 1

Task 2

Task N

```
{  "SdkAppId": 1400000000,  "RoomId": "A",  "RoomIdType": 1,  "AgentParams": {    "UserId": "A_Agent",    "UserSig": "eJwtjMEKgkAUAP9lz2Hv6b40oU...",    "MaxIdleTime": 50  },  "WithTranscoding": 1,  "AudioParams": {    "AudioEncode": {      "Codec": 0,      "SampleRate": 48000,      "Channel": 2,      "BitRate": 64    }  },  "FeedBackRoomParams": [    {      "RoomId": "B",      "RoomIdType": 1,      "UserId": "A_Feed",      "UserSig": "eJwtzEELgkAUBOD-sldD3745..."    },    {      "RoomId": "N",      "RoomIdType": 1,      "UserId": "A_Feed",      "UserSig": "eJwtzEELgkAUBOD-sldD3745..."    }  ]}
```

```
{  "SdkAppId": 1400000000,  "RoomId": "B",  "RoomIdType": 1,  "AgentParams": {    "UserId": "B_Agent",    "UserSig": "eJwtjMEKgkAUAP9lz2Hv6b40oU...",    "MaxIdleTime": 50  },  "WithTranscoding": 1,  "AudioParams": {    "AudioEncode": {      "Codec": 0,      "SampleRate": 48000,      "Channel": 2,      "BitRate": 64    }  },  "FeedBackRoomParams": [    {      "RoomId": "A",      "RoomIdType": 1,      "UserId": "B_Feed",      "UserSig": "eJwtzEELgkAUBOD-sldD3745..."    },    {      "RoomId": "N",      "RoomIdType": 1,      "UserId": "B_Feed",      "UserSig": "eJwtzEELgkAUBOD-sldD3745..."    }  ]}
```

```
{  "SdkAppId": 1400000000,  "RoomId": "N",  "RoomIdType": 1,  "AgentParams": {    "UserId": "N_Agent",    "UserSig": "eJwtjMEKgkAUAP9lz2Hv6b40oU...",    "MaxIdleTime": 50  },  "WithTranscoding": 1,  "AudioParams": {    "AudioEncode": {      "Codec": 0,      "SampleRate": 48000,      "Channel": 2,      "BitRate": 64    }  },  "FeedBackRoomParams": [    {      "RoomId": "A",      "RoomIdType": 1,      "UserId": "N_Feed",      "UserSig": "eJwtzEELgkAUBOD-sldD3745..."    },    {      "RoomId": "B",      "RoomIdType": 1,      "UserId": "N_Feed",      "UserSig": "eJwtzEELgkAUBOD-sldD3745..."    }  ]}
```

> **Note:**In a pure audio scene, the RTC Engine backend will by default mix the audio streams of all hosts in the room. You can also specify the audio mixing whitelist through the audio parameter [McuAudioParams](https://www.tencentcloud.com/document/api/647/36760#mcuaudioparams).

## Cross-Room PK Mic-Connection Solution Comparison Analysis

The above introduced three different cross-room PK connection implementation schemes, each with different use cases. The following is a comparison analysis of different cross-room mic-connection schemes from four dimensions.

| Solution Type | Solution Strength | Solution Disadvantages | Room and User Limit | Recommended Use Cases |
| --- | --- | --- | --- | --- |
| [Regular Cross-Room PK Mic-Connection Solution](https://www.tencentcloud.com/document/product/1228/70319#e3142169-41a1-4245-abe9-7f5aa77105b5) | The call logic for two-person PK is simple | The call logic for multi-person PK is complex | A single host can PK with up to 9 other hosts in different rooms | Two rooms, single host (double) cross-room PK |
| [Server-side cross-room PK mic-connection scheme](https://www.tencentcloud.com/document/product/1228/70319#d92e56fe-4616-47b4-9877-8c9d7538f6ba) | Pure server-side scheme, client-side does not require additional processing | There are additional costs for robot streaming and mixing | Support up to 11 rooms for cross-room PK at the same time, each room supports up to 16 hosts participating in cross-room PK at the same time | Multiple rooms, multi-host (multi-person) cross-room PK, pure server-side management |


---
*Source: [https://trtc.io/document/74579](https://trtc.io/document/74579)*
