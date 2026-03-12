# TUILiveLayoutManager

Copyright (c) 2024 Tencent. All rights reserved.

Module:   TUILiveLayoutManager @ TUIKitEngine

Live stream decoration relevant APIs

**TUILiveLayoutManager**

## TUILiveLayoutObserver

| Function List | Description |
| --- | --- |
| [onLiveVideoLayoutChanged](https://www.tencentcloud.com/document/product/647/69267#b14e71e05f158078257d550657844e88) | Live stream layout changes occurred |

## TUILiveLayoutManager

| Function List | Description |
| --- | --- |
| [addObserver](https://www.tencentcloud.com/document/product/647/69267#671b0fad38ffd4d3a962589f5146025a) | Add event callback |
| [removeObserver](https://www.tencentcloud.com/document/product/647/69267#907d7e4c59a653984e8555fdc5159039) | Remove event callback |

## onLiveVideoLayoutChanged

**Live stream layout changes occurred**

```
OnLiveVideoLayoutChanged onLiveVideoLayoutChanged = (String roomId, String layoutInfo) {};
```

| Parameter | Description |
| --- | --- |
| roomId | room ID |
| layoutInfo | Latest layout information of the picture |

## addObserver

**Add event callback**

```
 void addObserver(TUILiveLayoutObserver observer);
```

| Parameter | Description |
| --- | --- |
| observer | The instances being listened to |

## removeObserver

**Remove event callback**

```
 void removeObserver(TUILiveLayoutObserver observer);
```

| Parameter | Description |
| --- | --- |
| observer | The instances being listened to |


---
*Source: [https://trtc.io/document/69267](https://trtc.io/document/69267)*
