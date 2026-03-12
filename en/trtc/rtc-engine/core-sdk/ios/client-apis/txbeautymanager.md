# TXBeautyManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: beauty filter and image processing parameter configurations

Function: you can modify parameters such as beautification, filter, and green screen

**TXBeautyManager**

## TXBeautyManager

| FuncList | DESC |
| --- | --- |
| [setBeautyStyle:](https://www.tencentcloud.com/document/product/647/50758#89215cdfd5905aa81993b53b8c6b66be) | Sets the beauty (skin smoothing) filter algorithm. |
| [setBeautyLevel:](https://www.tencentcloud.com/document/product/647/50758#b5fedd8ce52caee75365c967a92b08e4) | Sets the strength of the beauty filter. |
| [setWhitenessLevel:](https://www.tencentcloud.com/document/product/647/50758#6e5243ac8d73b038a9c603a3ee7f7e38) | Sets the strength of the brightening filter. |
| [enableSharpnessEnhancement:](https://www.tencentcloud.com/document/product/647/50758#19b6a86699f384e98f6071f2040aed3a) | Enables clarity enhancement. |
| [setRuddyLevel:](https://www.tencentcloud.com/document/product/647/50758#821ebd8ee9c03f1b5e5ae77121cc61c3) | Sets the strength of the rosy skin filter. |
| [setFilter:](https://www.tencentcloud.com/document/product/647/50758#f73520b36361749d3f59eeb6db50f940) | Sets color filter. |
| [setFilterStrength:](https://www.tencentcloud.com/document/product/647/50758#4115cda15fa0692c38d1fe4b825a8b81) | Sets the strength of color filter. |
| [setGreenScreenFile:](https://www.tencentcloud.com/document/product/647/50758#c161a410f89d9f10e10dad0f1aaa6cf7) | Sets green screen video. |
| [setEyeScaleLevel:](https://www.tencentcloud.com/document/product/647/50758#2bf78eafcb88db8fdd9398eb4011619b) | Sets the strength of the eye enlarging filter. |
| [setFaceSlimLevel:](https://www.tencentcloud.com/document/product/647/50758#da3ed5adfa61941f1a11adc9938e9ba5) | Sets the strength of the face slimming filter. |
| [setFaceVLevel:](https://www.tencentcloud.com/document/product/647/50758#8350cda9b6a217967d8274cc39ccc6e6) | Sets the strength of the chin slimming filter. |
| [setChinLevel:](https://www.tencentcloud.com/document/product/647/50758#c3a377df9b943cbb361e87e2c9c7c47d) | Sets the strength of the chin lengthening/shortening filter. |
| [setFaceShortLevel:](https://www.tencentcloud.com/document/product/647/50758#98f562ff406656d9808f5a830403f301) | Sets the strength of the face shortening filter. |
| [setFaceNarrowLevel:](https://www.tencentcloud.com/document/product/647/50758#86fc487ad9836db7ef9e563917fcead9) | Sets the strength of the face narrowing filter. |
| [setNoseSlimLevel:](https://www.tencentcloud.com/document/product/647/50758#15b40583cade49e0487647d7f5c26d7c) | Sets the strength of the nose slimming filter. |
| [setEyeLightenLevel:](https://www.tencentcloud.com/document/product/647/50758#b02bf69415717f60da87233ab2a1bbf8) | Sets the strength of the eye brightening filter. |
| [setToothWhitenLevel:](https://www.tencentcloud.com/document/product/647/50758#3d97ddad87942486cb07496a4587447f) | Sets the strength of the teeth whitening filter. |
| [setWrinkleRemoveLevel:](https://www.tencentcloud.com/document/product/647/50758#a412c7fb9fcea0dc7c10d96a9aca95a5) | Sets the strength of the wrinkle removal filter. |
| [setPounchRemoveLevel:](https://www.tencentcloud.com/document/product/647/50758#846593213cef3d1f7b249586d209f0bf) | Sets the strength of the eye bag removal filter. |
| [setSmileLinesRemoveLevel:](https://www.tencentcloud.com/document/product/647/50758#aaded62695d2171b734016192ecf4fcb) | Sets the strength of the smile line removal filter. |
| [setForeheadLevel:](https://www.tencentcloud.com/document/product/647/50758#b608f5fe8511f829d131d32fc62654ab) | Sets the strength of the hairline adjustment filter. |
| [setEyeDistanceLevel:](https://www.tencentcloud.com/document/product/647/50758#2d0cb800cea51b9f8b09325e6adadb8d) | Sets the strength of the eye distance adjustment filter. |
| [setEyeAngleLevel:](https://www.tencentcloud.com/document/product/647/50758#643e7e93c2cbea98c2476b5cbc3d997d) | Sets the strength of the eye corner adjustment filter. |
| [setMouthShapeLevel:](https://www.tencentcloud.com/document/product/647/50758#f0d2c61efb5538d843e0a90128515b2a) | Sets the strength of the mouth shape adjustment filter. |
| [setNoseWingLevel:](https://www.tencentcloud.com/document/product/647/50758#17b9e0789d34ccd780fd271a5bd4cc6d) | Sets the strength of the nose wing narrowing filter. |
| [setNosePositionLevel:](https://www.tencentcloud.com/document/product/647/50758#12fc79a32b974f74a544af7ce164b54a) | Sets the strength of the nose position adjustment filter. |
| [setLipsThicknessLevel:](https://www.tencentcloud.com/document/product/647/50758#bf90775c7125cb53ff972e9fe447a282) | Sets the strength of the lip thickness adjustment filter. |
| [setFaceBeautyLevel:](https://www.tencentcloud.com/document/product/647/50758#4f4731a58b72b8cbc33ad84f4c397de9) | Sets the strength of the face shape adjustment filter. |
| [setMotionTmpl:inDir:](https://www.tencentcloud.com/document/product/647/50758#7f66b71987061e914cdfc9f756d3b762) | Selects the AI animated effect pendant. |
| [setMotionMute:](https://www.tencentcloud.com/document/product/647/50758#3146072ddea1c320588b1a27bc8bff2e) | Sets whether to mute during animated effect playback. |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXBeautyStyle](https://www.tencentcloud.com/document/product/647/50758#b6b1551f48bb1f502733fb8a0e8028b2) | Beauty (skin smoothing) filter algorithm. |

## setBeautyStyle:

**setBeautyStyle:**

| - (void)setBeautyStyle: | ([TXBeautyStyle](https://www.tencentcloud.com/document/product/647/50758#b6b1551f48bb1f502733fb8a0e8028b2))beautyStyle |
| --- | --- |

**Sets the beauty (skin smoothing) filter algorithm.**

TRTC has multiple built-in skin smoothing algorithms. You can select the one most suitable for your product needs:

| Param | DESC |
| --- | --- |
| beautyStyle | Beauty filter style. ` TXBeautyStyleSmooth `: smooth; ` TXBeautyStyleNature `: natural; ` TXBeautyStylePitu `: Pitu |

## setBeautyLevel:

**setBeautyLevel:**

| - (void)setBeautyLevel: | (float)beautyLevel |
| --- | --- |

**Sets the strength of the beauty filter.**

| Param | DESC |
| --- | --- |
| beautyLevel | Strength of the beauty filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

## setWhitenessLevel:

**setWhitenessLevel:**

| - (void)setWhitenessLevel: | (float)whitenessLevel |
| --- | --- |

**Sets the strength of the brightening filter.**

| Param | DESC |
| --- | --- |
| whitenessLevel | Strength of the brightening filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

## enableSharpnessEnhancement:

**enableSharpnessEnhancement:**

| - (void)enableSharpnessEnhancement: | (BOOL)enable |
| --- | --- |

**Enables clarity enhancement.**

## setRuddyLevel:

**setRuddyLevel:**

| - (void)setRuddyLevel: | (float)ruddyLevel |
| --- | --- |

**Sets the strength of the rosy skin filter.**

| Param | DESC |
| --- | --- |
| ruddyLevel | Strength of the rosy skin filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

## setFilter:

**setFilter:**

| - (void)setFilter: | (nullable TXImage *)image |
| --- | --- |

**Sets color filter.**

The color filter is a color lookup table image containing color mapping relationships. You can find several predefined filter images in the official demo we provide.

The SDK performs secondary processing on the original video image captured by the camera according to the mapping relationships in the lookup table to achieve the expected filter effect.

| Param | DESC |
| --- | --- |
| image | Color lookup table containing color mapping relationships. The image must be in PNG format. |

## setFilterStrength:

**setFilterStrength:**

| - (void)setFilterStrength: | (float)strength |
| --- | --- |

**Sets the strength of color filter.**

The larger this value, the more obvious the effect of the color filter, and the greater the color difference between the video image processed by the filter and the original video image.

The default strength is 0.5, and if it is not sufficient, it can be adjusted to a value above 0.5. The maximum value is 1.

| Param | DESC |
| --- | --- |
| strength | Value range: [0, 1]. The greater the value, the more obvious the effect. Default value: 0.5 |

## setGreenScreenFile:

**setGreenScreenFile:**

| - (int)setGreenScreenFile: | (nullable NSString *)path |
| --- | --- |

**Sets green screen video.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

The green screen feature enabled by this API is not capable of intelligent keying. It requires that there be a green screen behind the videoed person or object for further chroma keying.

| Param | DESC |
| --- | --- |
| path | Path of the video file in MP4 format. An empty value indicates to disable the effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setEyeScaleLevel:

**setEyeScaleLevel:**

| - (int)setEyeScaleLevel: | (float)eyeScaleLevel |
| --- | --- |

**Sets the strength of the eye enlarging filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| eyeScaleLevel | Strength of the eye enlarging filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceSlimLevel:

**setFaceSlimLevel:**

| - (int)setFaceSlimLevel: | (float)faceSlimLevel |
| --- | --- |

**Sets the strength of the face slimming filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| faceSlimLevel | Strength of the face slimming filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceVLevel:

**setFaceVLevel:**

| - (int)setFaceVLevel: | (float)faceVLevel |
| --- | --- |

**Sets the strength of the chin slimming filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| faceVLevel | Strength of the chin slimming filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setChinLevel:

**setChinLevel:**

| - (int)setChinLevel: | (float)chinLevel |
| --- | --- |

**Sets the strength of the chin lengthening/shortening filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| chinLevel | Strength of the chin lengthening/shortening filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates that the chin is shortened, and a value greater than 0 indicates that the chin is lengthened. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceShortLevel:

**setFaceShortLevel:**

| - (int)setFaceShortLevel: | (float)faceShortLevel |
| --- | --- |

**Sets the strength of the face shortening filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| faceShortLevel | Strength of the face shortening filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceNarrowLevel:

**setFaceNarrowLevel:**

| - (int)setFaceNarrowLevel: | (float)faceNarrowLevel |
| --- | --- |

**Sets the strength of the face narrowing filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| level | Strength of the face narrowing filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setNoseSlimLevel:

**setNoseSlimLevel:**

| - (int)setNoseSlimLevel: | (float)noseSlimLevel |
| --- | --- |

**Sets the strength of the nose slimming filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| noseSlimLevel | Strength of the nose slimming filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setEyeLightenLevel:

**setEyeLightenLevel:**

| - (int)setEyeLightenLevel: | (float)eyeLightenLevel |
| --- | --- |

**Sets the strength of the eye brightening filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| eyeLightenLevel | Strength of the eye brightening filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setToothWhitenLevel:

**setToothWhitenLevel:**

| - (int)setToothWhitenLevel: | (float)toothWhitenLevel |
| --- | --- |

**Sets the strength of the teeth whitening filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| toothWhitenLevel | Strength of the teeth whitening filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setWrinkleRemoveLevel:

**setWrinkleRemoveLevel:**

| - (int)setWrinkleRemoveLevel: | (float)wrinkleRemoveLevel |
| --- | --- |

**Sets the strength of the wrinkle removal filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| wrinkleRemoveLevel | Strength of the wrinkle removal filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setPounchRemoveLevel:

**setPounchRemoveLevel:**

| - (int)setPounchRemoveLevel: | (float)pounchRemoveLevel |
| --- | --- |

**Sets the strength of the eye bag removal filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| pounchRemoveLevel | Strength of the eye bag removal filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setSmileLinesRemoveLevel:

**setSmileLinesRemoveLevel:**

| - (int)setSmileLinesRemoveLevel: | (float)smileLinesRemoveLevel |
| --- | --- |

**Sets the strength of the smile line removal filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| smileLinesRemoveLevel | Strength of the smile line removal filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setForeheadLevel:

**setForeheadLevel:**

| - (int)setForeheadLevel: | (float)foreheadLevel |
| --- | --- |

**Sets the strength of the hairline adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| foreheadLevel | Strength of the hairline adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setEyeDistanceLevel:

**setEyeDistanceLevel:**

| - (int)setEyeDistanceLevel: | (float)eyeDistanceLevel |
| --- | --- |

**Sets the strength of the eye distance adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| eyeDistanceLevel | Strength of the eye distance adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to widen, and a value greater than 0 indicates to narrow. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setEyeAngleLevel:

**setEyeAngleLevel:**

| - (int)setEyeAngleLevel: | (float)eyeAngleLevel |
| --- | --- |

**Sets the strength of the eye corner adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| eyeAngleLevel | Strength of the eye corner adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setMouthShapeLevel:

**setMouthShapeLevel:**

| - (int)setMouthShapeLevel: | (float)mouthShapeLevel |
| --- | --- |

**Sets the strength of the mouth shape adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| mouthShapeLevel | Strength of the mouth shape adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to widen, and a value greater than 0 indicates to narrow. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setNoseWingLevel:

**setNoseWingLevel:**

| - (int)setNoseWingLevel: | (float)noseWingLevel |
| --- | --- |

**Sets the strength of the nose wing narrowing filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| noseWingLevel | Strength of the nose wing adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to widen, and a value greater than 0 indicates to narrow. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setNosePositionLevel:

**setNosePositionLevel:**

| - (int)setNosePositionLevel: | (float)nosePositionLevel |
| --- | --- |

**Sets the strength of the nose position adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| nosePositionLevel | Strength of the nose position adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to lift, and a value greater than 0 indicates to lower. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setLipsThicknessLevel:

**setLipsThicknessLevel:**

| - (int)setLipsThicknessLevel: | (float)lipsThicknessLevel |
| --- | --- |

**Sets the strength of the lip thickness adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| lipsThicknessLevel | Strength of the lip thickness adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to thicken, and a value greater than 0 indicates to thin. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceBeautyLevel:

**setFaceBeautyLevel:**

| - (int)setFaceBeautyLevel: | (float)faceBeautyLevel |
| --- | --- |

**Sets the strength of the face shape adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| faceBeautyLevel | Strength of the face shape adjustment filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and the greater the value, the more obvious the effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setMotionTmpl:inDir:

**setMotionTmpl:inDir:**

| - (void)setMotionTmpl: | (nullable NSString *)tmplName |
| --- | --- |
| inDir: | (nullable NSString *)tmplDir |

**Selects the AI animated effect pendant.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| tmplDir | Directory of the animated effect material file |
| tmplName | Animated effect pendant name |

## setMotionMute:

**setMotionMute:**

| - (void)setMotionMute: | (BOOL)motionMute |
| --- | --- |

**Sets whether to mute during animated effect playback.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect. Some animated effects have audio effects, which can be disabled through this API when they are played back.

| Param | DESC |
| --- | --- |
| motionMute | ` YES `: mute; ` NO `: unmute |

## TXBeautyStyle

**TXBeautyStyle**

**Beauty (skin smoothing) filter algorithm.**

TRTC has multiple built-in skin smoothing algorithms. You can select the one most suitable for your product needs.

| Enum | Value | DESC |
| --- | --- | --- |
| TXBeautyStyleSmooth | 0 | Smooth style, which uses a more radical algorithm for more obvious effect and is suitable for show live streaming. |
| TXBeautyStyleNature | 1 | Natural style, which retains more facial details for more natural effect and is suitable for most live streaming use cases. |
| TXBeautyStylePitu | 2 | Pitu style, which is provided by YouTu Lab. Its skin smoothing effect is between the smooth style and the natural style, that is, it retains more skin details than the smooth style and has a higher skin smoothing degree than the natural style. |


---
*Source: [https://trtc.io/document/50758](https://trtc.io/document/50758)*
