# TXBeautyManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: beauty filter and image processing parameter configurations

Function: you can modify parameters such as beautification, filter, and green screen

**TXBeautyManager**

## TXBeautyManager

| FuncList | DESC |
| --- | --- |
| [setBeautyStyle](https://www.tencentcloud.com/document/product/647/50766#d3fdd4986152f2b9418bef94aaa62575) | Sets the beauty (skin smoothing) filter algorithm. |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/50766#0f1ab9f5e3c2150d3b7acc043636993b) | Sets the strength of the beauty filter. |
| [setWhitenessLevel](https://www.tencentcloud.com/document/product/647/50766#4156425a7c70c41fd9eb92b0afead869) | Sets the strength of the brightening filter. |
| [enableSharpnessEnhancement](https://www.tencentcloud.com/document/product/647/50766#3fdef66469d194422353bbdd1582b116) | Enables clarity enhancement. |
| [setRuddyLevel](https://www.tencentcloud.com/document/product/647/50766#e910671c2d434f192746135b222b1f26) | Sets the strength of the rosy skin filter. |
| [setFilter](https://www.tencentcloud.com/document/product/647/50766#b68995a74e5e1f8a74d1d601002df436) | Sets color filter. |
| [setFilterStrength](https://www.tencentcloud.com/document/product/647/50766#67fa5ec3f6ad3e6ee221a2419f5fbf1c) | Sets the strength of color filter. |
| [setGreenScreenFile](https://www.tencentcloud.com/document/product/647/50766#cc40b48dfcfca3652eb1b14d1951cb03) | Sets green screen video. |
| [setEyeScaleLevel](https://www.tencentcloud.com/document/product/647/50766#499ecdc88602c0180a2e429a43f6479c) | Sets the strength of the eye enlarging filter. |
| [setFaceSlimLevel](https://www.tencentcloud.com/document/product/647/50766#1541edd89ed993dc95cccc1ad7da2096) | Sets the strength of the face slimming filter. |
| [setFaceVLevel](https://www.tencentcloud.com/document/product/647/50766#db51c69a28d817bc0e9887a3031ea418) | Sets the strength of the chin slimming filter. |
| [setChinLevel](https://www.tencentcloud.com/document/product/647/50766#24a531bdfa6c2cac251cebbcbe33bf9e) | Sets the strength of the chin lengthening/shortening filter. |
| [setFaceShortLevel](https://www.tencentcloud.com/document/product/647/50766#7a74136e5fdb9113c55b38ac5fb68ad0) | Sets the strength of the face shortening filter. |
| [setFaceNarrowLevel](https://www.tencentcloud.com/document/product/647/50766#355fd6987714bf4f1e77e3692d71ce1c) | Sets the strength of the face narrowing filter. |
| [setNoseSlimLevel](https://www.tencentcloud.com/document/product/647/50766#e91f334ff8acdc7a0ada260f1ec9af7a) | Sets the strength of the nose slimming filter. |
| [setEyeLightenLevel](https://www.tencentcloud.com/document/product/647/50766#98bfa71c0efce410fcad9a54e71cd23c) | Sets the strength of the eye brightening filter. |
| [setToothWhitenLevel](https://www.tencentcloud.com/document/product/647/50766#46fa131a69e36b2c53fea50ccbedb5ca) | Sets the strength of the teeth whitening filter. |
| [setWrinkleRemoveLevel](https://www.tencentcloud.com/document/product/647/50766#ae65bfc2413b2e30e5c4d415edea8dc1) | Sets the strength of the wrinkle removal filter. |
| [setPounchRemoveLevel](https://www.tencentcloud.com/document/product/647/50766#7eb3906cc8d8c824f51245648c1ad314) | Sets the strength of the eye bag removal filter. |
| [setSmileLinesRemoveLevel](https://www.tencentcloud.com/document/product/647/50766#35faeed6286e030cc373206171860792) | Sets the strength of the smile line removal filter. |
| [setForeheadLevel](https://www.tencentcloud.com/document/product/647/50766#6fff839e209eca06c177c3a6b52e1322) | Sets the strength of the hairline adjustment filter. |
| [setEyeDistanceLevel](https://www.tencentcloud.com/document/product/647/50766#af54d76bb28ae3482a5c6c35fb500cbf) | Sets the strength of the eye distance adjustment filter. |
| [setEyeAngleLevel](https://www.tencentcloud.com/document/product/647/50766#fa64d8156a269b767701f84f93a83f5e) | Sets the strength of the eye corner adjustment filter. |
| [setMouthShapeLevel](https://www.tencentcloud.com/document/product/647/50766#f8548ba279ca3a3a726597dabf5d48ee) | Sets the strength of the mouth shape adjustment filter. |
| [setNoseWingLevel](https://www.tencentcloud.com/document/product/647/50766#c2cd7b9bd4a3079e419628af9f1c7da2) | Sets the strength of the nose wing narrowing filter. |
| [setNosePositionLevel](https://www.tencentcloud.com/document/product/647/50766#7fa2f6542f50b66d7831ce876655502d) | Sets the strength of the nose position adjustment filter. |
| [setLipsThicknessLevel](https://www.tencentcloud.com/document/product/647/50766#20ba318ec854b3cac9f975cf79791edf) | Sets the strength of the lip thickness adjustment filter. |
| [setFaceBeautyLevel](https://www.tencentcloud.com/document/product/647/50766#1f320ba994f61fab04b195796d7dc6ad) | Sets the strength of the face shape adjustment filter. |
| [setMotionTmpl](https://www.tencentcloud.com/document/product/647/50766#be3f0f9f80456be2a2e9c598f3164bc5) | Selects the AI animated effect pendant. |
| [setMotionMute](https://www.tencentcloud.com/document/product/647/50766#b249750633c498650d73c15902de468e) | Sets whether to mute during animated effect playback. |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXBeautyStyle](https://www.tencentcloud.com/document/product/647/50766#44ff20d9497c2c1b3661d7c4cc695ba7) | Beauty (skin smoothing) filter algorithm. |

## setBeautyStyle

**setBeautyStyle**

| void setBeautyStyle | (int beautyStyle) |
| --- | --- |

**Sets the beauty (skin smoothing) filter algorithm.**

TRTC has multiple built-in skin smoothing algorithms. You can select the one most suitable for your product needs:

| Param | DESC |
| --- | --- |
| beautyStyle | Beauty filter style. ` TXBeautyStyleSmooth `: smooth; ` TXBeautyStyleNature `: natural; ` TXBeautyStylePitu `: Pitu |

## setBeautyLevel

**setBeautyLevel**

| void setBeautyLevel | (float beautyLevel) |
| --- | --- |

**Sets the strength of the beauty filter.**

| Param | DESC |
| --- | --- |
| beautyLevel | Strength of the beauty filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

## setWhitenessLevel

**setWhitenessLevel**

| void setWhitenessLevel | (float whitenessLevel) |
| --- | --- |

**Sets the strength of the brightening filter.**

| Param | DESC |
| --- | --- |
| whitenessLevel | Strength of the brightening filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

## enableSharpnessEnhancement

**enableSharpnessEnhancement**

| void enableSharpnessEnhancement | (boolean enable) |
| --- | --- |

**Enables clarity enhancement.**

## setRuddyLevel

**setRuddyLevel**

| void setRuddyLevel | (float ruddyLevel) |
| --- | --- |

**Sets the strength of the rosy skin filter.**

| Param | DESC |
| --- | --- |
| ruddyLevel | Strength of the rosy skin filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

## setFilter

**setFilter**

| void setFilter | (Bitmap image) |
| --- | --- |

**Sets color filter.**

The color filter is a color lookup table image containing color mapping relationships. You can find several predefined filter images in the official demo we provide.

The SDK performs secondary processing on the original video image captured by the camera according to the mapping relationships in the lookup table to achieve the expected filter effect.

| Param | DESC |
| --- | --- |
| image | Color lookup table containing color mapping relationships. The image must be in PNG format. |

## setFilterStrength

**setFilterStrength**

| void setFilterStrength | (float strength) |
| --- | --- |

**Sets the strength of color filter.**

The larger this value, the more obvious the effect of the color filter, and the greater the color difference between the video image processed by the filter and the original video image.

The default strength is 0.5, and if it is not sufficient, it can be adjusted to a value above 0.5. The maximum value is 1.

| Param | DESC |
| --- | --- |
| strength | Value range: [0, 1]. The greater the value, the more obvious the effect. Default value: 0.5 |

## setGreenScreenFile

**setGreenScreenFile**

| int setGreenScreenFile | (String path) |
| --- | --- |

**Sets green screen video.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

The green screen feature enabled by this API is not capable of intelligent keying. It requires that there be a green screen behind the videoed person or object for further chroma keying.

| Param | DESC |
| --- | --- |
| path | Path of the video file in MP4 format. An empty value indicates to disable the effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setEyeScaleLevel

**setEyeScaleLevel**

| int setEyeScaleLevel | (float eyeScaleLevel) |
| --- | --- |

**Sets the strength of the eye enlarging filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| eyeScaleLevel | Strength of the eye enlarging filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceSlimLevel

**setFaceSlimLevel**

| int setFaceSlimLevel | (float faceSlimLevel) |
| --- | --- |

**Sets the strength of the face slimming filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| faceSlimLevel | Strength of the face slimming filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceVLevel

**setFaceVLevel**

| int setFaceVLevel | (float faceVLevel) |
| --- | --- |

**Sets the strength of the chin slimming filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| faceVLevel | Strength of the chin slimming filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setChinLevel

**setChinLevel**

| int setChinLevel | (float chinLevel) |
| --- | --- |

**Sets the strength of the chin lengthening/shortening filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| chinLevel | Strength of the chin lengthening/shortening filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates that the chin is shortened, and a value greater than 0 indicates that the chin is lengthened. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceShortLevel

**setFaceShortLevel**

| int setFaceShortLevel | (float faceShortLevel) |
| --- | --- |

**Sets the strength of the face shortening filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| faceShortLevel | Strength of the face shortening filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceNarrowLevel

**setFaceNarrowLevel**

| int setFaceNarrowLevel | (float faceNarrowLevel) |
| --- | --- |

**Sets the strength of the face narrowing filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| level | Strength of the face narrowing filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setNoseSlimLevel

**setNoseSlimLevel**

| int setNoseSlimLevel | (float noseSlimLevel) |
| --- | --- |

**Sets the strength of the nose slimming filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| noseSlimLevel | Strength of the nose slimming filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setEyeLightenLevel

**setEyeLightenLevel**

| int setEyeLightenLevel | (float eyeLightenLevel) |
| --- | --- |

**Sets the strength of the eye brightening filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| eyeLightenLevel | Strength of the eye brightening filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setToothWhitenLevel

**setToothWhitenLevel**

| int setToothWhitenLevel | (float toothWhitenLevel) |
| --- | --- |

**Sets the strength of the teeth whitening filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| toothWhitenLevel | Strength of the teeth whitening filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setWrinkleRemoveLevel

**setWrinkleRemoveLevel**

| int setWrinkleRemoveLevel | (float wrinkleRemoveLevel) |
| --- | --- |

**Sets the strength of the wrinkle removal filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| wrinkleRemoveLevel | Strength of the wrinkle removal filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setPounchRemoveLevel

**setPounchRemoveLevel**

| int setPounchRemoveLevel | (float pounchRemoveLevel) |
| --- | --- |

**Sets the strength of the eye bag removal filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| pounchRemoveLevel | Strength of the eye bag removal filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setSmileLinesRemoveLevel

**setSmileLinesRemoveLevel**

| int setSmileLinesRemoveLevel | (float smileLinesRemoveLevel) |
| --- | --- |

**Sets the strength of the smile line removal filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| smileLinesRemoveLevel | Strength of the smile line removal filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setForeheadLevel

**setForeheadLevel**

| int setForeheadLevel | (float foreheadLevel) |
| --- | --- |

**Sets the strength of the hairline adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| foreheadLevel | Strength of the hairline adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setEyeDistanceLevel

**setEyeDistanceLevel**

| int setEyeDistanceLevel | (float eyeDistanceLevel) |
| --- | --- |

**Sets the strength of the eye distance adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| eyeDistanceLevel | Strength of the eye distance adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to widen, and a value greater than 0 indicates to narrow. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setEyeAngleLevel

**setEyeAngleLevel**

| int setEyeAngleLevel | (float eyeAngleLevel) |
| --- | --- |

**Sets the strength of the eye corner adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| eyeAngleLevel | Strength of the eye corner adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, and ` 9 ` indicates the most obvious effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setMouthShapeLevel

**setMouthShapeLevel**

| int setMouthShapeLevel | (float mouthShapeLevel) |
| --- | --- |

**Sets the strength of the mouth shape adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| mouthShapeLevel | Strength of the mouth shape adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to widen, and a value greater than 0 indicates to narrow. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setNoseWingLevel

**setNoseWingLevel**

| int setNoseWingLevel | (float noseWingLevel) |
| --- | --- |

**Sets the strength of the nose wing narrowing filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| noseWingLevel | Strength of the nose wing adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to widen, and a value greater than 0 indicates to narrow. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setNosePositionLevel

**setNosePositionLevel**

| int setNosePositionLevel | (float nosePositionLevel) |
| --- | --- |

**Sets the strength of the nose position adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| nosePositionLevel | Strength of the nose position adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to lift, and a value greater than 0 indicates to lower. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setLipsThicknessLevel

**setLipsThicknessLevel**

| int setLipsThicknessLevel | (float lipsThicknessLevel) |
| --- | --- |

**Sets the strength of the lip thickness adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| lipsThicknessLevel | Strength of the lip thickness adjustment filter. Value range: [-9, 9]. ` 0 ` indicates to disable the filter, a value smaller than 0 indicates to thicken, and a value greater than 0 indicates to thin. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setFaceBeautyLevel

**setFaceBeautyLevel**

| int setFaceBeautyLevel | (float faceBeautyLevel) |
| --- | --- |

**Sets the strength of the face shape adjustment filter.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| faceBeautyLevel | Strength of the face shape adjustment filter. Value range: [0, 9]. ` 0 ` indicates to disable the filter, and the greater the value, the more obvious the effect. |

**Return Desc:**

0: Success; -5: feature of license not supported.

## setMotionTmpl

**setMotionTmpl**

| void setMotionTmpl | (String tmplPath) |
| --- | --- |

**Selects the AI animated effect pendant.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect.

| Param | DESC |
| --- | --- |
| tmplPath | Directory of the animated effect material file |

## setMotionMute

**setMotionMute**

| void setMotionMute | (boolean motionMute) |
| --- | --- |

**Sets whether to mute during animated effect playback.**

This interface is only available in the enterprise version SDK (the old version has been offline, if you need to use the advanced beauty function in the new version SDK, please refer to [Tencent Beauty Effect SDK](https://www.tencentcloud.com/document/product/1143/53942)) in effect. Some animated effects have audio effects, which can be disabled through this API when they are played back.

| Param | DESC |
| --- | --- |
| motionMute | ` true `: mute; ` false `: unmute |

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
*Source: [https://trtc.io/document/50766](https://trtc.io/document/50766)*
