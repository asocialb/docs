# TUILiveListManager

Copyright (c) 2024 Tencent. All rights reserved.

Module:   TUILiveListManager @ TUIKitEngine

Function: Live Streaming Related Interface

**TUILiveListManager**

## TUILiveListManager

| Function List | Description |
| --- | --- |
| [onLiveInfoChanged](https://www.tencentcloud.com/document/product/647/67260#onLiveInfoChanged) | Live Streaming Information Change Callback |
| [addObserver](https://www.tencentcloud.com/document/product/647/67260#setObserver) | Add Event Callback |
| [removeObserver](https://www.tencentcloud.com/document/product/647/67260#efc0a6c0-9ac3-4012-810e-c6d4ad12fa71) | Remove event callbacks |
| [setLiveInfo](https://www.tencentcloud.com/document/product/647/67260#setLiveInfo) | Modify Live Streaming Information |
| [getLiveInfo](https://www.tencentcloud.com/document/product/647/67260#getLiveInfo) | Retrieve Live Streaming Information |
| [fetchLiveList](https://www.tencentcloud.com/document/product/647/67260#fetchLiveList) | Getting the Live Stream List |

## Struct type

| Function List | Description |
| --- | --- |
| [TUILiveInfo](https://www.tencentcloud.com/document/product/647/67260#TUILiveInfo) | Live Streaming Information |

## Enumeration Types

| Enumeration Types | Description |
| --- | --- |
| [TUILiveModifyFlag](https://www.tencentcloud.com/document/product/647/67260#TUILiveModifyFlag) | Modify Flags for Live Streaming Room |

## onLiveInfoChanged

**onLiveInfoChanged**

| OnLiveInfoChanged onLiveInfoChanged | ([TUILiveInfo](https://www.tencentcloud.com/document/product/647/67260#TUILiveInfo) TUILiveInfo |
| --- | --- |
|  | [TUILiveModifyFlag](https://www.tencentcloud.com/document/product/647/67260#TUILiveModifyFlag) modifyFlag) |

#### Live Streaming Information Change Callback

| Parameters | Description |
| --- | --- |
| TUILiveInfo | Live Streaming Room Information |
| modifyFlagList | List of Changed Value Flags |

## addObserver

**setObserver**

| void setObserver | (TUILiveListObserver observer) |
| --- | --- |

#### Add Event Callback

You can receive live room event notifications through TUILiveListManagerObserver

| Parameters | Description |
| --- | --- |
| observer | Instance to Monitor |

## removeObserver

**removeObserver**

| void setObserver | (TUILiveListObserver observer) |
| --- | --- |

#### Remove event callbacks

You can receive live room event notifications through TUILiveListManagerObserver

| Parameters | Description |
| --- | --- |
| observer | Instance to Monitor |

## setLiveInfo

**setLiveInfo**

| Future<TUIActionCallback> setLiveInfo | ([TUILiveInfo](https://www.tencentcloud.com/document/product/647/67260#TUILiveInfo) TUILiveInfo |
| --- | --- |
|  | [TUILiveModifyFlag](https://www.tencentcloud.com/document/product/647/67260#TUILiveModifyFlag) modifyFlag) |

#### Modify Live Streaming Information

| Parameters | Description |
| --- | --- |
| roomId | Room ID |
| coverUrl | Profile Photo URL |
| categoryList | Live Room Category Tag |
| isPublicVisible | Is Public |
| activityStatus | Live room active status: user-defined Definition tag |

## getLiveInfo

**getLiveInfo**

| Future<TUIValueCallBack<TUILiveInfo>> getLiveInfo | (String roomId) |
| --- | --- |

#### Retrieve Live Streaming Information

| Parameters | Description |
| --- | --- |
| callback | Callback of API call, used to notify the success or failure of the API call |
| roomId | Room ID |

## fetchLiveList

**fetchLiveList**

| Future<TUIValueCallBack<TUILiveListResult>> fetchLiveList | (String cursor |
| --- | --- |
|  | int count) |

#### Getting the Live Stream List

| Parameters | Description |
| --- | --- |
| count | Number of Pulls each time |
| cursor | List Index |

## TUILiveModifyFlag

**TUILiveModifyFlag**

#### Modify Flags for Live Streaming Room

| Enumeration | Value | Description |
| --- | --- | --- |
| ACTIVITY_STATUS | 0x0100 | ActivityStatus: Live Room Activity Status, supports custom settings |
| COVER_URL | 0x0200 | CoverUrl: Live Room Cover |
| CATEGORY | 0x0400 | Category: Live Room Category |
| PUBLISH | 0x0800 | Publish: Live Room Public Tag |

## TUILiveInfo

**TUILiveInfo**

#### Live Streaming Information

| Enumeration Types | Description |
| --- | --- |
| activityStatus | Live room active status: user-defined Definition tag |
| categoryList | Live Room Category Tag |
| coverUrl | Live Room Cover |
| isPublicVisible | Is Live Room Public |
| roomInfo | Room Information (Read Only) |
| viewCount | Total View Count |


---
*Source: [https://trtc.io/document/67260](https://trtc.io/document/67260)*
