# RoomKit API

## Introduction

TUIRoomKit is an open source UI layer suite for conference SDK, currently only supports Swift language on the iOS platform. The conference UI can be called up through simple API calls.

## TUIRoomKit Interface

| API | Description |
| --- | --- |
| [createInstance](https://www.tencentcloud.com/document/product/647/54857#eeea9b0a-415a-4eb5-943b-0897122b85f4) | Initialize the TUIRoomKit singleton object |
| [destroyInstance](https://www.tencentcloud.com/document/product/647/54857#a07b9445-798a-4128-95d8-5eec3893dd63) | Destroy the TUIRoomKit singleton object |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54857#5b2593e4-ab4a-4e5c-a0a5-ae2e346456af) | Set user information (avatar, nickname) (optional) |
| [createRoom](https://www.tencentcloud.com/document/product/647/54857#657af8a0-cbfa-4808-b122-3f32a4db025c) | Create a room |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54857#ca9fa33b-d588-4643-aece-df6e94a5d2b6) | Enter the room |

### createInstance

Initialize the TUIRoomKit singleton object.

```
public class func createInstance() -> TUIRoomKit
```

### destroyInstance

Destroy the TUIRoomKit singleton object.

```
public class func destroyInstance() -> Void
```

### setSelfInfo(optional)

Set user information (avatar, nickname).

```
public func setSelfInfo(userName: String,                        avatarURL: String,                        onSuccess: @escaping TUISuccessBlock,                          onError: @escaping TUIErrorBlock) -> Void
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| userName | String | Username |
| avatarURL | String | User avatar URL |
| onSuccess | TUISuccessBlock | Successful callback |
| onError | TUIErrorBlock | Failure callback |

### createRoom

Create a room.

```
public func createRoom(roomInfo: TUIRoomInfo,                       onSuccess: @escaping TUISuccessBlock,                         onError: @escaping TUIErrorBlock) -> Void
```

The parameters are as follows:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomInfo | [TUIRoomInfo](https://www.tencentcloud.com/document/product/647/54859#RoomInfo) | Room data |
| onSuccess | TUISuccessBlock | Successful callback |
| onError | TUIErrorBlock | Failure callback |

### enterRoom

Enter the room.

```
public func enterRoom(roomId: String,                  enableAudio: Bool,                  enableVideo: Bool,             isSoundOnSpeaker: Bool,                   onSuccess: @escaping TUISuccessBlock,                      onError: @escaping TUIErrorBlock) -> Void
```

The parameters are as follows:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | Room ID string |
| enableAudio | Bool | Whether to turn on the audio when entering the room |
| enableVideo | Bool | Whether to turn on the video when entering the room |
| isSoundOnSpeaker | Bool | Whether to turn on the speakers when entering the room |
| onSuccess | TUISuccessBlock | Successful callback |
| onError | TUIErrorBlock | Failure callback |


---
*Source: [https://trtc.io/document/54857](https://trtc.io/document/54857)*
