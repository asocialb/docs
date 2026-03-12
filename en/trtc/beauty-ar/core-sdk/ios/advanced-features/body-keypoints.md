# Body Keypoints

## Overview

This capability processes the OpenGL textures of the camera and outputs 3D body data. You can pass the data to Unity to drive your model or use the data to implement other features.

## Integration (iOS)

Follow the directions in [Integrating Tencent Effect SDK](https://www.tencentcloud.com/document/product/1143/60193) to integrate the Tencent Effect SDK.

### API calls

1. Enable the feature (XMagic.h).

```
- (void)setFeatureEnableDisable:(NSString *_Nonnull)featureName enable:(BOOL)enable;
```

Set `featureName` to `XmagicConstant.FeatureName.BODY_3D_POINT`.

2. Configure the data callback (XMagic.h).

**Version 2.6.0** and earlier versions use the following method.

```
//XMagic.h- (void)registerSDKEventListener:(id<YTSDKEventListener> _Nullable)listener;@implementation listener- (void)onYTDataEvent:(id)event{    NSLog(@"YTData %@", event);}@end
```

`onYTDataEvent` returns a JSON string.

  - `face_info` is facial data, which is not used by this capability.
  - For the meanings of fields in `body_3d_info`, see below.

**Version 3.0.0**uses the following method.

```
//XMagic.h- (void)registerSDKEventListener:(id<YTSDKEventListener> _Nullable)listener;- (void)onAIEvent:(id)event{    NSDictionary *eventDict = (NSDictionary *)event;    if (eventDict[@"ai_info"] != nil) {      NSLog(@"ai_info %@",eventDict[@"ai_info"]);    }}
```

`eventDict[@"ai_info"] ` returns a JSON string.

  - `face_info` is facial data, which is not used by this capability.
  - For the meanings of fields in `body_3d_info`, see below.

## Body Keypoints and Descriptions

For details about body keypoints, see [Body Keypoints and Descriptions](https://www.tencentcloud.com/document/product/1143/74184#c3fe9b5b-8422-4fcb-84aa-781a126dd4f6).


---
*Source: [https://trtc.io/document/74185](https://trtc.io/document/74185)*
