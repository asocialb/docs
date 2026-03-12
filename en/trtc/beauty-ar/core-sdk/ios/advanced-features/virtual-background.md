# Virtual Background

Accurately removes the background in real time and applies a virtual background (customizable):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2e17cf2bbc8e11eda534525400c56988.png)

### iOS Integration Guide

iOS SDK Integration Guide. See [Integrating Core SDK (iOS)](https://www.tencentcloud.com/document/product/1143/60193).

### Methodology

```
- (void)setEffect:(NSString * _Nullable)effectName effectValue:(int)effectValue  resourcePath:(NSString * _Nullable)resourcePath extraInfo:(NSDictionary * _Nullable)extraInfo;
```

detailed parameter description, see [setEffect](https://www.tencentcloud.com/document/product/1143/60202#setEffect).

### Virtual Background Settings

```
NSString *path = [[[NSBundle mainBundle] pathForResource:@"segmentMotionRes" ofType:@"bundle"] stringByAppendingPathComponent:@"video_segmentation_blur_75"];[_xMagicKit setEffect:EFFECT_MOTION effectValue:0 resourcePath:path extraInfo:nil];
```

### Custom Background Settings

```
 NSString *resourcePath = [[[NSBundle mainBundle] pathForResource:@"segmentMotionRes" ofType:@"bundle"] stringByAppendingPathComponent:@"video_empty_segmentation"]; NSMutableDictionary *dic = [NSMutableDictionary dictionary]; dic[@"segType"] = @"custom_background"; dic[@"bgType"] = 0;//Background type. 0 means image, 1 means video. dic[@"bgPath"] = @"/var/mobile/Containers/Data/Application/06B00BBC-9060-450F-8D3A-F6028D185682/Documents/MediaFile/image.png"; //Absolute path of custom background image. If video is selected as custom background, perform compression transcoding process and use the absolute path after processing. [_xMagicKit setEffect:EFFECT_SEGMENTATION effectValue:0 resourcePath:resourcePath extraInfo:dic];
```


---
*Source: [https://trtc.io/document/60197](https://trtc.io/document/60197)*
