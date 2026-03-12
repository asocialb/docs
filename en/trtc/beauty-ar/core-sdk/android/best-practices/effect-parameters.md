# Effect Parameters

When using the `setEffect` feature to refresh the beautification effects, you may refer to the following parameter table. The `effectName` constants, as delineated in the parameter table, are defined within the `XmagicConstant.java` file for Android, and within the `XmagicConstant.h` file for iOS.

## Beautification, Body Beautification

| **Type** | **Name** | effectName |  | **effectValue** | **resourcePath** |
| --- | --- | --- | --- | --- | --- |
|  |  | Constant Name | **Constant  Value** | Effect Intensity | **Resource Path** |
| Beauty filter | Brighten -**Bright White** | BEAUTY_WHITEN0 | beauty.lutFoundationAlpha0 | 0 ~ 100 | Before V3.9.0: NoV3.9.0 and later: ãOptionalãcustom white  lut path |
|  | Brighten -**Natural** | BEAUTY_WHITEN | beauty.lutFoundationAlpha | 0 ~ 100 | Before V3.9.0: NoV3.9.0 and later: ãOptionalãcustom white  lut path |
|  | Brighten - **Pinkish White** | BEAUTY_WHITEN2 | beauty.lutFoundationAlpha2 | 0 ~ 100 | Before V3.9.0: NoV3.9.0 and later: ãOptionalãcustom white  lut path |
|  | Brighten - **Cool White** | BEAUTY_WHITEN3 | beauty.lutFoundationAlpha3 | 0 ~ 100 | Before V3.9.0: NoV3.9.0 and later: ãOptionalãcustom white  lut path |
|  | Black**(V3.7.0)** | BEAUTY_BLACK_1 | beauty.lutBlackAlpha1 | 0 ~ 100 | No |
|  | Brown**(V3.7.0)** | BEAUTY_BLACK_2 | beauty.lutBlackAlpha2 | 0 ~ 100 | No |
|  | Smooth - **Young** | BEAUTY_SMOOTH | smooth.smooth | 0 ~ 100 | No |
|  | Smooth - **Texture****(V3.9.3)** | BEAUTY_SMOOTH2 | smooth.smooth2 | 0 ~ 100 | No |
|  | Smooth - **Realistic****(V3.9.3)** | BEAUTY_SMOOTH3 | smooth.smooth3 | 0 ~ 100 | No |
|  | Smooth - **Classic****(V3.9.3)** | BEAUTY_SMOOTH4 | smooth.smooth4 | 0 ~ 100 | No |
|  | Gan Beauty Skin(AI Beauty Skin)**(V3.9.3)** | BEAUTY_FACE_SKIN_RETOUCH | beauty.skinRetouch | 0 ~ 100 | No |
|  | Skin Highlight(V4.0.0) | BEAUTY_SKIN_HIGHLIGHT | beauty.skinHighlight | 0 ~ 100 | No |
|  | Rosy skin | BEAUTY_ROSY | smooth.rosy | 0 ~ 100 | No |
| Screen Adjustment | Contrast | BEAUTY_CONTRAST | beauty.imageContrastAlpha | -100 ~ 100 | No |
|  | Saturation | BEAUTY_SATURATION | smooth.saturation | -100 ~ 100 | No |
|  | Sharpness | BEAUTY_CLEAR | beauty.lutClearAlpha | 0 ~ 100 | No |
|  | Sharpen | BEAUTY_SHAPE | smooth.sharpen | 0 ~ 100 | No |
|  | Brightness(**V3.8.0)** | BEAUTY_IMAGE_BRIGHTNESS | beauty.imageBrightness | -100 ~ 100 | NO |
|  | Denoise**(V3.6.0)** | BEAUTY_IMAGE_DENOISE | postEffect.denoise | 0 ~ 100 | No |
|  | Warmth | BEAUTY_IMAGE_WARMTH | beauty.imageWarmth | -100 ~ 100 | No |
|  | Tint | BEAUTY_IMAGE_TINT | beauty.imageTint | -100 ~ 100 | No |
| Advanced Aesthetics | Big eyes | BEAUTY_ENLARGE_EYE | basicV7.enlargeEye | 0 ~ 100 | No |
|  | Bright eyes | BEAUTY_EYE_LIGHTEN | beauty.eyeLighten | 0 ~ 100 | No |
|  | Eye distance | BEAUTY_EYE_DISTANCE | basicV7.eyeDistance | -100 ~ 100 | No |
|  | Eye corners | BEAUTY_EYE_ANGLE | basicV7.eyeAngle | -100 ~ 100 | No |
|  | Eye width | BEAUTY_EYE_WIDTH | basicV7.eyeWidth | -100 ~ 100 | No |
|  | Eye height | BEAUTY_EYE_HEIGHT | basicV7.eyeHeight | -100 ~ 100 | No |
|  | Eye position**(V3.8.0)** | BEAUTY_EYE_POSITION | basicV7.eyePosition | -100 ~ 100 | No |
|  | Eye out corner**(V3.9.0)** | BEAUTY_EYE_OUT_CORNER | basicV7.eyeOutCorner | -100 ~ 100 | No |
|  | Eye bags | BEAUTY_FACE_REMOVE_EYE_BAGS | beauty.removeEyeBags | 0 ~ 100 | No |
|  | Angle of eyebrows | BEAUTY_EYEBROW_ANGLE | basicV7.eyebrowAngle | -100 ~ 100 | No |
|  | Eyebrow distance | BEAUTY_EYEBROW_DISTANCE | basicV7.eyebrowDistance | -100 ~ 100 | No |
|  | Eyebrow height | BEAUTY_EYEBROW_HEIGHT | basicV7.eyebrowHeight | -100 ~ 100 | No |
|  | Eyebrow length | BEAUTY_EYEBROW_LENGTH | basicV7.eyebrowLength | -100 ~ 100 | No |
|  | Thickness of the eyebrows | BEAUTY_EYEBROW_THICKNESS | basicV7.eyebrowThickness | -100 ~ 100 | No |
|  | Eyebrow ridge | BEAUTY_EYEBROW_RIDGE | basicV7.eyebrowRidge | -100 ~ 100 | No |
|  | Nose size | BEAUTY_NOSE_THIN | basicV7.thinNose | 0 ~ 100 | No |
|  | Nose wings | BEAUTY_NOSE_WING | basicV7.noseWing | -100 ~ 100 | No |
|  | Nose position | BEAUTY_NOSE_HEIGHT | basicV7.noseHeight | -100 ~ 100 | No |
|  | Nasal bridge | BEAUTY_NOSE_BRIDGE_WIDTH | basicV7.noseBridgeWidth | -100 ~ 100 | No |
|  | Nasion | BEAUTY_NASION | basicV7.nasion | -100 ~ 100 | No |
|  | White teeth | BEAUTY_TOOTH_WHITEN | beauty.toothWhiten | 0 ~ 100 | No |
|  | Lip shape | BEAUTY_MOUTH_SIZE | basicV7.mouthSize | -100 ~ 100 | No |
|  | Lip height | BEAUTY_MOUTH_HEIGHT | basicV7.mouthHeight | -100 ~ 100 | No |
|  | Lip Width | BEAUTY_MOUTH_WIDTH | basicV7.mouthWidth | -100 ~ 100 | No |
|  | Lip position | BEAUTY_MOUTH_POSITION | basicV7.mouthPosition | -100 ~ 100 | No |
|  | Smiling lips | BEAUTY_SMILE_FACE | basicV7.smileFace | -100 ~ 100 | No |
|  | Face width | BEAUTY_FACE_THIN | basicV7.thinFace | 0 ~ 100 | No |
|  | Slim face - **Natural** | BEAUTY_FACE_NATURE | basicV7.natureFace | 0 ~ 100 | No |
|  | Slim face -**Goddess** | BEAUTY_FACE_GODNESS | basicV7.godnessFace | 0 ~ 100 | No |
|  | Slim face - **Handsome** | BEAUTY_FACE_MALE_GOD | basicV7.maleGodFace | 0 ~ 100 | No |
|  | V-shaped face | BEAUTY_FACE_V | basicV7.vFace | 0 ~ 100 | No |
|  | Slim jaw | BEAUTY_FACE_JAW | basicV7.faceJaw | 0 ~ 100 | No |
|  | Face length | BEAUTY_FACE_SHORT | basicV7.shortFace | 0 ~ 100 | No |
|  | Face shape | BEAUTY_FACE_BASIC | liquefaction.basic3 | 0 ~ 100 | No |
|  | Chin | BEAUTY_FACE_THIN_CHIN | basicV7.chin | -100 ~ 100 | No |
|  | Forehead | BEAUTY_FACE_FOREHEAD | basicV7.forehead | -100 ~ 100 | No |
|  | Forehead2**(V3.9.1)** | BEAUTY_FACE_FOREHEAD2 | basicV7.forehead2 | -100 ~ 100 | No |
|  | Wrinkles | BEAUTY_FACE_REMOVE_WRINKLE | beauty.removeWrinkle | 0 ~ 100 | No |
|  | Smile lines | BEAUTY_FACE_REMOVE_LAW_LINE | beauty.removeLawLine | 0 ~ 100 | No |
|  | Cheekbones | BEAUTY_FACE_THIN_CHEEKBONE | basicV7.cheekboneThin | 0 ~ 100 | No |
| Single-point makeup | Lipstick |  BEAUTY_MOUTH_LIPSTICK | beauty.faceFeatureLipsLut | 0 ~ 100 | The absolute path of the lipstick image on the mobile phone or the relative path to the beauty model file directoryExample:`/images/beauty/lips_fuguhong.png` |
|  | Blush | BEAUTY_FACE_RED_CHEEK | beauty.faceFeatureRedCheek | 0 ~ 100 | Example:`/images/beauty/saihong_jianyue.png` |
|  | Contour |  BEAUTY_FACE_SOFTLIGHT | beauty.faceFeatureSoftlight | 0 ~ 100 | Example:`/images/beauty/liti_ziran.png` |
|  | HairColor**(V3.7.0)** | BEAUTY_HAIR_COLOR_LUT | beauty.hairColorLut | 0 ~ 100 | Exampleï¼`/images/hair_color/red.png` |
|  | Eyeshadow |  BEAUTY_FACE_EYE_SHADOW | beauty.faceFeatureEyesMakeup.eyeShadow | 0 ~ 100 | Example:`/images/beauty/eyes_makeup_eye_shadow_0-albatross.png` |
|  | Eyeliner |  BEAUTY_FACE_EYE_LINER | beauty.faceFeatureEyesMakeup.eyeLiner | 0 ~ 100 | Example:`/images/beauty/eyes_makeup_eye_liner_0.png` |
|  | Eyelashes |  BEAUTY_FACE_EYELASH | beauty.faceFeatureEyesMakeup.eyelash | 0 ~ 100 | Example:`/images/beauty/eyes_makeup_eyelash_0.png` |
|  | Eyebrows |  BEAUTY_FACE_EYEBROW | beauty.faceFeatureEyesMakeup.eyebrow | 0 ~ 100 | Example:`/images/beauty/eyes_makeup_eyebrow_0.png` |
|  | Eyeball |  BEAUTY_FACE_EYEBALL | beauty.faceFeatureEyesMakeup.eyeball | 0 ~ 100 | Example:`/images/beauty/eyes_makeup_eyeball_0.png` |
|  | Eyelids**(V3.8.0)** | BEAUTY_FACE_MAKEUP_EYELIDS | beauty.faceFeatureEyesMakeup.eyelids | 0 ~ 100 | Exampleï¼`/images/beauty/eyes_makeup_eyelids_kaishan.png` |
|  | Wocan**(V3.8.0)** | BEAUTY_FACE_MAKEUP_EYEWOCAN | beauty.faceFeatureEyesMakeup.eyewocan | 0 ~ 100 | Exampleï¼`/images/beauty/eyes_makeup_eye_wocan_keai.png` |
| Body beautification | One-click slimming | BODY_AUTOTHIN_BODY_STRENGTH | body.autothinBodyStrength | 0 ~ 100 | No |
|  | Long legs | BODY_LEG_STRETCH | body.legStretch | 0 ~ 100 | No |
|  | Thin legs | BODY_SLIM_LEG_STRENGTH | body.slimLegStrength | 0 ~ 100 | No |
|  | Slim waist | BODY_WAIST_STRENGTH | body.waistStrength | 0 ~ 100 | No |
|  | Slim shoulders | BODY_THIN_SHOULDER_STRENGTH | body.thinShoulderStrength | 0 ~ 100 | No |
|  | Breast Adjust | BODY_ENLARGE_CHEST_STRENGTH | body.enlargeChestStrength | -100 ~ 100 | No |
|  | Head size | BODY_SLIM_HEAD_STRENGTH | body.slimHeadStrength | 0 ~ 100 | No |

## Filters, Cosmetics, Motion Effects, Segmentation

| Type | effectName |  | effectValue | **resourcePath** | **extraInfo** |
| --- | --- | --- | --- | --- | --- |
|  | Constant Name | **Constant  Value** | **Effect Intensity** | **Resource Path** | Additional Parameters (Key-Value Pair Type) |
| **Filter** |  EFFECT_LUT | lut | 0 ~ 100 | The absolute path of the filter image on the mobile device, for instance:`/data/user/0/com.tencent.pitumotiondemo.effects/files/xmagic/light_material/lut/aiqing_lf.png`If you wish to cancel the filter, enter null here | No |
| **Light makeup****ï¼V3.9.0ï¼** | EFFECT_LIGHT_MAKEUP | light.makeup | 0~100 | Absolute path to beauty materials on the mobile phone.To cancel beauty makeup, fill in 'null' here |  **[Optional]**`makeupLutStrength`: The filter strength in the makeup material, with a value ranging from "0" to "100" |
| **Makeup** |  EFFECT_MAKEUP | makeup | 0 ~ 100 | Absolute path to beauty materials on the mobile phone.To cancel beauty makeup, fill in 'null' here | **[Optional]**`makeupLutStrength`: The filter strength in the makeup material, with a value ranging from "0" to "100"**[Optional]**`mergeWithCurrentMotion`: Represents whether to superimpose on the current motion effect, "true" or "false". If this field is not filled, it is considered to be false |
| **Motion** |  EFFECT_MOTION | motion | No | The absolute path of the motion graphics material on the mobile device, for instance:`/data/user/0/com.tencent.pitumotiondemo.effects/files/xmagic/light_material/motion/video_keaituya`If you wish to cancel the motion effect, fill in 'null' here | **[Optional]**`mergeWithCurrentMotion`: "true" or "false", indicating whether it is to be superimposed on the current motion effect. If this field is not filled out, it is assumed to be false |
| **Background Demarcation****ï¼ordinaryï¼** |  EFFECT_SEGMENTATION | segmentation | No | The absolute path of the background segmentation material on the mobile phoneIf you want to cancel the segmentation, fill in null here | **[Optional]**`mergeWithCurrentMotion`: "true" or "false", indicating whether it is to be superimposed on the current motion effect. If this field is not filled out, it is assumed to be false |
| **Background Demarcation****ï¼Green Screen_1ï¼** |  EFFECT_SEGMENTATION | segmentation | No | The absolute path of the background segmentation green screen material 1 on the mobile phone. If you want to cancel the segmentation, fill in null here | **[Required]**`segType`:"green_background"**[Required]**`bgType`: User-Defined Background Type, "0" represents images (supported image formats: **png, jpg, jpeg**) or pag, "1" represents videos**[Required]**`bgPath`: User-Defined Background Image or Video Path**[Optional]**`keyColor`: Green Screen Color RGB, the format is like "#00ff00"**[Optional]**`tex_protect_rect`ï¼Green screen protection area refers to the region that remains unaffected and is not replaced. For instance:`"[0.0,0.0,0.3,0.3]",`The bottom-left corner of the screen has coordinates (0,0), and the top-right corner has coordinates (1,1).**[Optional]**`mergeWithCurrentMotion`: "true" or "false", indicates whether to overlay it on the current animation effect. If this field is not filled in, it is considered as false |
| **Background Demarcation****ï¼Green Screen V2 ï¼****(V3.9.2)** |  EFFECT_SEGMENTATION | segmentation | No | The absolute path of the background segmentation green screen material 2 on the mobile phone.If you want to cancel the segmentation, fill in null here | **[Required]**`segType`:"green_background_v2"**[Required]**`bgType`: User-Defined Background Type, "0" represents images (supported image formats: **png, jpg, jpeg**) or pag, "1" represents videos**[Required]**`bgPath`: User-Defined Background Image or Video Path**[Optional]**`mergeWithCurrentMotion`: "true" or "false", indicates whether to overlay it on the current animation effect. If this field is not filled in, it is considered as false**[Optional]** `green_params_v2`ï¼Green screen effect fine-tuning parameters, such as `"[30,20,1,30,1]"`. [Detailed parameter description](https://www.tencentcloud.com/document/product/1143/73789).**[Optional]** `tex_protect_rect`ï¼Green screen protection area refers to the region that remains unaffected and is not replaced. For instance:`"[0.0,0.0,0.3,0.3]",`The bottom-left corner of the screen has coordinates (0,0), and the top-right corner has coordinates (1,1). |
| **Background Demarcation****ï¼Blue Screen V2 ï¼****(V3.9.2)** |  EFFECT_SEGMENTATION | segmentation | No | The absolute path of the background segmentation blue screen material on the mobile phone.If you want to cancel the segmentation, fill in null here | **[Required]**`segType`:"green_background_v2"**[Required]**`bgType`: User-Defined Background Type, "0" represents images (supported image formats: **png, jpg, jpeg**) or pag, "1" represents videos**[Required]**`bgPath`: User-Defined Background Image or Video Path**[Optional]**`mergeWithCurrentMotion`: "true" or "false", indicates whether to overlay it on the current animation effect. If this field is not filled in, it is considered as false**[Optional]** `green_params_v2`ï¼Green screen effect fine-tuning parameters, such as `"[35,8,1,10,1]"`. [Detailed parameter description](https://www.tencentcloud.com/document/product/1143/73789).**[Optional]** `tex_protect_rect`ï¼Green screen protection area refers to the region that remains unaffected and is not replaced. For instance:`"[0.0,0.0,0.3,0.3]",`The bottom-left corner of the screen has coordinates (0,0), and the top-right corner has coordinates (1,1). |
| **Background Demarcation****ï¼Customï¼** |  EFFECT_SEGMENTATION | segmentation | No | The absolute path of the background segmentation material on the mobile phoneIf you want to cancel the segmentation, fill in null here | **[Required]**`segType`:"custom_background"**[Required]**`bgType`:  User-defined background type, "0" denotes image (supported image formats: **png, jpg, jpeg**) or pag, "1" indicates a video**[Required]**`bgPath`: Pathway for the user-defined background image or video**[Optional]**`mergeWithCurrentMotion`:"true" or "false", specifies whether to overlay on the current motion effect. If this field is left blank, itâs assumed to be false |


---
*Source: [https://trtc.io/document/60207](https://trtc.io/document/60207)*
