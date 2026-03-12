# Virtual Background

Accurately removes the background in real time and applies a virtual background (customizable):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f3efaa5ea4c111f0b1565254001c06ec.png)

### Android Integration Guide

Android SDK Integration Guide. See [Integrating Core SDK  (Android)](https://www.tencentcloud.com/document/product/1143/60195).

### Methodology

```
setEffect(String effectName, int effectValue, String resourcePath, Map<String, String> extraInfo)
```

Detailed parameter description, see [setEffect](https://www.tencentcloud.com/document/product/1143/60201#32a345ed-73c4-4c60-bc7e-3f91b9a4755c).

### Virtual Background Settings

```
mXmagicApi.setEffect(EffectName.EFFECT_SEGMENTATION, 45, AppConfig.motionResPath + "/segmentMotionRes/video_segmentation_blur_45", null);
```

### Custom Background Settings

```
 Map<String, String> extraInfo = new HashMap<>(); extraInfo.put("segType", "custom_background"); extraInfo.put("bgType", "0"); extraInfo.put("bgPath", imgPath); mXmagicApi.setEffect(EffectName.EFFECT_SEGMENTATION, 0, AppConfig.motionResPath + "/segmentMotionRes/video_empty_segmentation", extraInfo);
```

###


---
*Source: [https://trtc.io/document/60311](https://trtc.io/document/60311)*
