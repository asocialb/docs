# Voice Room UIKit API

## API Introduction

VoiceRoomKit is a voice chat room component **with UI interface,** using the VoiceRoomKit API, you can quickly implement a voice chat room through simple interfaces. If you want to experience and debug the voice chat room, please read [Demo Rapid Deployment](https://www.tencentcloud.com/document/product/647/63378#). If you want to integrate our feature directly into your project, please read [Quick Integration (TUILiveKit)](https://www.tencentcloud.com/document/product/647/60335#).

## API Overview

| **API** | **Description** |
| --- | --- |
| [createInstance](https://www.tencentcloud.com/document/product/647/66794#d147f174-e55a-4ba2-bbaf-2792c9419650) | Obtain a VoiceRoomKit object instance. |
| [createRoom](https://www.tencentcloud.com/document/product/647/66794#c6f79ba4-2dc1-4d65-82b3-e52d3ef28f2f) | Create a voice chat room live streaming room. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/66794#34d62c35-ff96-4250-be5a-a518ed341a5d) | Enter a voice chat room live streaming room using roomId. |

## API Details

### createInstance

Obtain a VoiceRoomKit object instance.

```
static VoiceRoomKit createInstance(Context context)
```

**Parameter:**

| **Parameter** | **Type** | **Note** | **Default value** | **Meaning** |
| --- | --- | --- | --- | --- |
| context | Context | Mandatory | - | Android context object |

**Return Value:**VoiceRoomKit

### createRoom

Create a voice chat room live streaming room.

```
void createRoom(String roomId, VoiceRoomDefine.CreateRoomParams params);
```

**Parameter:**

| **Parameter** | **Type** | **Note** | **Default value** | **Meaning** |
| --- | --- | --- | --- | --- |
| roomId | String | Mandatory | - | Live Streaming Room ID |
| params | [CreateRoomParams](https://www.tencentcloud.com/document/product/647/66794#dc90ee9d-a1c6-4933-b7b1-7899a76eae0e) | Mandatory | - | Create Live Room Parameters |

**Return Value:**void

### enterRoom

Enter a voice chat room live streaming room using roomId.

```
void enterRoom(String roomId);
```

**Parameter:**

| **Parameter** | **Type** | **Note** | **Default value** | **Meaning** |
| --- | --- | --- | --- | --- |
| roomId | String | Mandatory | - | Live Streaming Room ID |

**Return Value:**void

## VoiceRoomDefine Introduction

VoiceRoomKit is the UIKit layer data model class for voice chat rooms, mainly including the following data structures:

### CreateRoomParams

Parameters object when creating a voice chat room live streaming, mainly including the following configuration parameters:

| **Parameter** | **Type** | **Note** | **Default value** | **Meaning** |
| --- | --- | --- | --- | --- |
| roomName | String |  | "" | Voice chat room name |
| maxAnchorCount | int |  | 10 | Maximum number of users on stage |
| seatMode | String | Mandatory |  | Mic On Mode is divided into the following two types:FREE_TO_TAKE(1): Free to Join the Podium mode, where the audience can join the seat freely without applying.APPLY_TO_TAKE(2): Apply to Join the Mic mode, where the audience needs the host's or administrator's approval to join the seat. |


---
*Source: [https://trtc.io/document/66794](https://trtc.io/document/66794)*
