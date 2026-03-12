# Gesture Recognition

## Overview

Input the camera's OpenGL texture and output real-time gesture detection data. You can use this data for further development.

## iOS Integration Guide

Integrate Beauty AR SDK on iOS, for details please refer to: [Integrating SDK (iOS)](https://www.tencentcloud.com/document/product/1143/60193).

## iOS Interface Invocation

1. Turn on the gesture detection feature switch (in Xmagic.h)

```
- (void)setFeatureEnableDisable:(NSString *_Nonnull)featureName enable:(BOOL)enable;
```

Fill in featureName with HAND_DETECT (can be imported from TEDefine.h), and set enable to true.

2. Set data callback (in Xmagic.h)

```
- (void)registerSDKEventListener:(id<YTSDKEventListener> _Nullable)listener;- (void)onAIEvent:(id)event{    NSDictionary *eventDict = (NSDictionary *)event;    if (eventDict[@"ai_info"] != nil) {      NSLog(@"ai_info %@",eventDict[@"ai_info"]);    }}
```

eventDict[@"ai_info"] is the returned JSON structured string data.

## Callback JSON Data Description

In the callback JSON data, the gesture-related data is in "hand_info", and the format is as follows:

```
"hand_info": {â    "gesture": "PAPER",â    "hand_point_2d": [180.71888732910156, 569.2958984375, ... , 353.8714294433594, 836.246826171875]}
```

The explanations of each field in hand_info are as follows:

| Field | Explanation |
| --- | --- |
| gesture | Gesture Type Name |
| hand_point_2d | Captured gesture data information |

The following gestures are currently supported:

| Order | Gesture | Type Name | Example Image |
| --- | --- | --- | --- |
| 1 | Heart | HEART | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/57270e64311a11ee9bd25254005c1bd1.png) |
| 2 | Gestrue with number 5(open) | PAPER | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/56fd6ba7311a11ee8de9525400c56988.png) |
| 3 | Gesture with number 2 | SCISSOR | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5710aad4311a11eeba71525400088f3a.png) |
| 4 | Fist | FIST | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/570d3360311a11ee872a525400cea498.png) |
| 5 | Gesture with number 1 | ONE | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/571a5fd5311a11ee872a525400cea498.png) |
| 6 | I love you | LOVE | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/57184da3311a11ee872a525400cea498.png) |
| 7 | Thumb up | LIKE | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/57243fed311a11ee872a525400cea498.png) |
| 8 | OK | OK | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5731f138311a11ee872a525400cea498.png) |
| 9 | Rock | ROCK | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/573a2c03311a11ee8de9525400c56988.png) |
| 10 | Gesture with number 6 | SIX | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/57487b1d311a11ee872a525400cea498.png) |
| 11 | Gesture with number 8 | EIGHT | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/575df525311a11ee8de9525400c56988.png) |
| 12 | Lift | LIFT | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/57479456311a11eeba71525400088f3a.png) |
| 13 | Gesture with number 3 | THREE | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/577a4ca5311a11ee8de9525400c56988.png) |
| 14 | Gesture with number 4 | FOUR | ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/575872f9311a11ee9bd25254005c1bd1.png) |

If it is an undetected gesture, the gesture type name is OTHER.


---
*Source: [https://trtc.io/document/60199](https://trtc.io/document/60199)*
