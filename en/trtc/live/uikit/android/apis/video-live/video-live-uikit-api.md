# Video Live UIKit API

## API Introduction

VideoLiveKit is a live streaming component with a **UI interface,** using the VideoLiveKit API, you can quickly implement an online live streaming scenario through simple interfaces. If you want to experience and debug interactive live streaming, please refer to [Run Demo](https://www.tencentcloud.com/document/product/647/60454#). If you want to integrate our feature directly into your project, please read [Quick Integration (TUILiveKit)](https://www.tencentcloud.com/document/product/647/60037#).

## API Overview

| **API** | **Description** |
| --- | --- |
| [createInstance](https://www.tencentcloud.com/document/product/647/61638#d147f174-e55a-4ba2-bbaf-2792c9419650) | Create a VideoLiveKit instance (Singleton Pattern) |
| [startLive](https://www.tencentcloud.com/document/product/647/61638#c6f79ba4-2dc1-4d65-82b3-e52d3ef28f2f) | Start a live room using roomId. |
| [joinLive](https://www.tencentcloud.com/document/product/647/61638#34d62c35-ff96-4250-be5a-a518ed341a5d) | Join a live room using roomId. |

## API Details

### createInstance

Obtain a VideoLiveKit instance.

```
static VideoLiveKit createInstance(Context context)
```

**Parameter:**

| **Parameter** | **Type** | **Description** | **Default Value** | **Meaning** |
| --- | --- | --- | --- | --- |
| context | Context | Mandatory | - | Android context object |

**Returned value:**VideoLiveKit

### startLive

Start a live room using roomId.

```
void startLive(String roomId);
```

**Parameter:**

| **Parameter** | **Type** | **Description** | **Default Value** | **Meaning** |
| --- | --- | --- | --- | --- |
| roomId | String | Mandatory | - | Live Streaming Room ID |

**Return Value:**void

### joinLive

Join a live room using roomId.

```
void joinLive(String roomId);
```

**Parameter:**

| **Parameter** | **Type** | **Description** | **Default Value** | **Meaning** |
| --- | --- | --- | --- | --- |
| roomId | String | Mandatory | - | Live Streaming Room ID |

**Return Value:**void


---
*Source: [https://trtc.io/document/61638](https://trtc.io/document/61638)*
