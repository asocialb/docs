# API Document

`TencentEffectApi` is the core API class of the Beauty AR Flutter SDK. It offers capabilities including setting the effect strength and applying animated effects.

## Public Member APIs

| API | Description |
| --- | --- |
| [setResourcePath](https://www.tencentcloud.com/document/product/1143/60200#f8005e55-d1ac-4c64-be24-0401ff6b4f49) | Set the local storage path of beauty resources (V0.3.5.0 version) |
| [initXmagic](https://www.tencentcloud.com/document/product/1143/60200#initxmagic) | Initializes data. You need to call this API before using the Beauty AR SDK**ï¼V0.3.1.1 and earlierï¼.** |
| [setLicense](https://www.tencentcloud.com/document/product/1143/60200#setlicense) | Configures the license. |
| [setXmagicLogLevel](https://www.tencentcloud.com/document/product/1143/60200#setxmagicloglevel) | Sets the log level of the SDK. We recommend you set it to `Log.DEBUG` for debugging and `Log.WARN` for official release. If you set it to `Log.DEBUG` in a production environment, the output of a large amount of log data may affect your applicationâs performance. |
| [onResume](https://www.tencentcloud.com/document/product/1143/60200#onresume) | Resumes rendering. Call this API when the page is visible. |
| [onPause](https://www.tencentcloud.com/document/product/1143/60200#onpause) | Pauses rendering. Call this API when the page is invisible. |
| [setDowngradePerformance](https://www.tencentcloud.com/document/product/1143/60200#a0bfdc09-97fc-4c1d-a000-46a2196123cc) | Invoke this method to enable the high-performance pattern. Upon the activation of the high-performance pattern, the system CPU/GPU resources occupied by beauty filters are minimized, thereby reducing heat generation and latency issues in the mobile device. It is particularly suitable for prolonged use on low-end devices. |
| [setAudioMute](https://www.tencentcloud.com/document/product/1143/60200#0ca59006-7e84-4abe-8803-abc4ad7669e1) | set muteï¼**Because some stickers have sound**ï¼ |
| [setFeatureEnableDisable](https://www.tencentcloud.com/document/product/1143/60200#9a632a6a-9785-4e03-a282-429a81de0415) | enable or disable the feature |
| [setEffect](https://www.tencentcloud.com/document/product/1143/60200#32a345ed-73c4-4c60-bc7e-3f91b9a4755c) | Updates an effect propertyï¼**V0.3.5.0 Version**ï¼ |
| [setOnCreateXmagicApiErrorListener](https://www.tencentcloud.com/document/product/1143/60200#setoncreatexmagicapierrorlistener) | Configures the callback for creating an effect object. The callback will be triggered if an error occurs. |
| [setTipsListener](https://www.tencentcloud.com/document/product/1143/60200#settipslistener) | Configures the callback for animated effect tips. The tips can be displayed on the UI. |
| [setYTDataListener](https://www.tencentcloud.com/document/product/1143/60200#setytdatalistener) | Configure the callback of facial keypoints and other data, callback will only be available with the License authorization required to acquire facial keypoints (such as Atomic Capability X102). |
| [setAIDataListener](https://www.tencentcloud.com/document/product/1143/60200#setaidatalistener) | Configures the callback of face, gesture, and body detection results. |
| [isSupportBeauty](https://www.tencentcloud.com/document/product/1143/60200#issupportbeauty) | Checks whether the current device supports effects (OpenGL 3.0). |
| [getDeviceAbilities](https://www.tencentcloud.com/document/product/1143/60200#getdeviceabilities) | Gets a list of Beauty AR capabilities supported by the current device. |
| [isDeviceSupportMotion](https://www.tencentcloud.com/document/product/1143/60200#2c38d93b-e4bb-4e5e-b7bd-16f4fe8782e3) | Check if the current device supports this material. |

## API Description

### setResourcePath ï¼V0.3.5.0ï¼

To set the local path for storing beauty resources

```
/// Set the local path for storing beauty resources. This method must be called before using beauty effects./// Added in v0.3.5.0.
void setResourcePath(String xmagicResDir);
```

#### Parameters

| Parameter | Description |
| --- | --- |
| String xmagicResDir | The resource directory. |

### initXmagic

Initialize beauty data. In versions prior to `V0.3.1.1`, this method must be called before using beauty effects. Starting from `V0.3.5.0`, this method only needs to be called once per version, and the setResourcePath method must be called before this method to set the resource path. In `V0.3.5.0`, the previous xmagicResDir parameter has been removed. Please refer to the latest demo for more information.

**V0.3.5.0 :**

```
void initXmagic(InitXmagicCallBack callBack);typedef InitXmagicCallBack = void Function(bool reslut);
```

**V0.3.1.1 and earlier :**

This API is used to initialize the SDK.

```
void initXmagic(String xmagicResDir,InitXmagicCallBack callBack);typedef InitXmagicCallBack = void Function(bool reslut);
```

#### Parameters

| Parameter | Description |
| --- | --- |
| String xmagicResDir | The resource directory. |
| InitXmagicCallBack callBack | The initialization callback. |

### setLicense

This API is used to set the license.

```
  ///Set the sdk licensevoid setLicense(String licenseKey, String licenseUrl, LicenseCheckListener checkListener);//The callback of the authorization resulttypedef LicenseCheckListener = void Function(int errorCode, String msg);
```

#### Parameters

| Parameter | Description |
| --- | --- |
| String licenseKey | The license key. |
| String licenseUrl | The license URL. |
| LicenseCheckListener checkListener | The callback of the authorization result. |

### setXmagicLogLevel

This API is used to set the log level of the SDK.

```
void setXmagicLogLevel(int logLevel);
```

#### Parameters

| Parameter | Description |
| --- | --- |
| int logLevel | You can set the log level using a type defined for `LogLevel`. |

### onResume

This API is used to resume effect rendering.

```
void onResume();
```

### onPause

This API is used to pause effect rendering.

```
void onPause();
```

### setDowngradePerformanceï¼V0.3.1.1ï¼

Invoke this method to enable the high-performance pattern

```
void setDowngradePerformance();
```

### setAudioMuteï¼V0.3.1.1ï¼

To set the mute status, the parameter "true" represents mute, while "false" represents unmute.

```
/// Is the background music muted?
void setAudioMute(bool isMute);
```

### setFeatureEnableDisableï¼V0.3.1.1ï¼

enable or disable one feature

```
/// enable or disable one feature 
void setFeatureEnableDisable(String featureName, bool enable);
```

#### Parameter

| Parameter | Meaning |
| --- | --- |
| String featureName | feature NameValuesï¼`"ai.3dmmV2.enable"` facial expressions feature.`"ai.body3dpoint.enable"` 3D body data feature.`"ai.hand.enable"` gesture detection.`"beauty.onlyWhitenSkin" `  Brightening only applies to skin.`"ai.segmentation.skin.enable"` segmentation skin.`"auto_beauty_switch"`  smart beauty(reducing the intensity of beauty and makeup effects for males and babies). |
| boolean enable | "true" indicates enabling a capability, while "false" indicates disabling a capability.**Note: If it is in downgrade mode, enabling skin segmentation is not allowed.** |

### setEffectï¼V0.3.5.0ï¼

You can set  beautification, filters, makeup, stickers, and segmentation effects. This can be done from any thread. Please refer to the specific parameters for more details in [Effect Parameters](https://www.tencentcloud.com/document/product/1143/60207#)ã

```
///update beautification parameters
void setEffect(String effectName,int effectValue,String? resourcePath,Map<String,String>? extraInfo);
```

### setOnCreateXmagicApiErrorListener

This API is used to configure the callback for errors for the creation of an effect object.

```
  void setOnCreateXmagicApiErrorListener(OnCreateXmagicApiErrorListener? errorListener);/// The callback for errors for the creation of an effect objecttypedef OnCreateXmagicApiErrorListener = void Function(String errorMsg, int code);
```

#### Parameters

| Parameter | Description |
| --- | --- |
| OnCreateXmagicApiErrorListener? errorListener | The callback for errors for the creation of an effect object. |

Error codes:

| Error Code | Description |
| --- | --- |
| -1 | Unknown error. |
| -100 | Failed to initialize the 3D engine. |
| -200 | GAN materials are not supported. |
| -300 | The device does not support this material component. |
| -400 | The JSON template is empty. |
| -500 | The SDK version is too old. |
| -600 | Keying is not supported. |
| -700 | OpenGL is not supported. |
| -800 | The script is not supported. |
| 5000 | The resolution of the video to be keyed exceeds 2160 x 3840. |
| 5001 | Insufficient memory for keying. |
| 5002 | Failed to parse the video to be keyed. |
| 5003 | The video to be keyed is longer than 200 seconds. |
| 5004 | Unsupported video format for keying. |

### setTipsListener

This API is used to configure the callback for animated effect tips. The tips can be displayed on the UI, asking users to nod, show their palms, or make finger hearts.

```
void setTipsListener(XmagicTipsListener? xmagicTipsListener);abstract class XmagicTipsListener {  /// Show the tip  /// @param tips: The content of the tip (string).  /// @param tipsIcon: The icon for the tip.  /// @param type: The display type. If it is set to `0`, both the tip string and icon will be displayed. If it is set to `1`, only the icon will be displayed for PAG materials.  /// @param duration: How long (milliseconds) to show the tip.  void tipsNeedShow(String tips, String tipsIcon, int type, int duration);  /// *  /// Hide the tip  /// @param tips: The content of the tip (string).  /// @param tipsIcon: The icon for the tip.  /// @param type: The display type. If it is set to `0`, both the tip string and icon will be displayed. If it is set to `1`, only the icon will be displayed for PAG materials.  void tipsNeedHide(String tips, String tipsIcon, int type);}
```

#### Parameters

| Parameter | Description |
| --- | --- |
| XmagicTipsListener xmagicTipsListener | The callback implementation class. |

### setYTDataListener

This API is used to configure the callback of facial keypoints and other data.

```
  /// Configure the callback of facial keypoints and other data (only available in S1 - 05 and S1 - 06)void setYTDataListener(XmagicYTDataListener? xmagicYTDataListener);Configure the callback of facial keypoints and other dataabstract class XmagicYTDataListener {  // YouTu AI data  void onYTDataUpdate(String data);}
```

`onYTDataUpdate` returns a JSON string structure that contains the information of up to 5 faces:

```
{ "face_info":[{  "trace_id":5,  "face_256_point":[    180.0,    112.2,    ...  ],  "face_256_visible":[    0.85,    ...  ],  "out_of_screen":true,  "left_eye_high_vis_ratio:1.0,  "right_eye_high_vis_ratio":1.0,  "left_eyebrow_high_vis_ratio":1.0,  "right_eyebrow_high_vis_ratio":1.0,  "mouth_high_vis_ratio":1.0 }, ... ]}
```

#### Fields

| Field | Type | Range | Description |
| --- | --- | --- | --- |
| trace_id | int | [1,INF) | The face ID. If the faces obtained from a continuous video stream have the same face ID, they belong to the same person. |
| face_256_point | float | [0,screenWidth] or [0,screenHeight] | 512 values in total for 256 facial keypoints. (0,0) is the top-left corner of the screen. |
| face_256_visible | float | [0,1] | The visibility of the 256 facial keypoints. |
| out_of_screen | bool | true/false | Whether only part of the face is captured. |
| left_eye_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the left eye. |
| right_eye_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the right eye. |
| left_eyebrow_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the left eyebrow. |
| right_eyebrow_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the right eyebrow. |
| mouth_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the mouth. |

#### Parameters

| Parameter | Description |
| --- | --- |
| XmagicYTDataListener | The callback implementation class. |

### setAIDataListener

This API is used to configure the callback of face, gesture, and body detection results.

```
void setAIDataListener(XmagicAIDataListener? aiDataListener);abstract class XmagicAIDataListener {  void onFaceDataUpdated(String faceDataList);  void onHandDataUpdated(String handDataList);  void onBodyDataUpdated(String bodyDataList);}
```

### ~~isBeautyAuthorized~~

This API is used to check whether the current license supports a particular type of effects. It can only check the authorization of `BEAUTY` and `BODY_BEAUTY` effects. The result returned determines the value of `XmagicProperty.isAuth`. If `isAuth` is `false`, you can disable the corresponding effects on the UI.

```
Future<List<XmagicProperty>> isBeautyAuthorized(      List<XmagicProperty> properties);
```

#### Parameters

| Parameter | Description |
| --- | --- |
| List<XmagicProperty> properties | The type of effects to check. |

### isSupportBeauty

This API is used to check whether the current device supports effects (OpenGL 3.0).

```
  Future<bool> isSupportBeauty();
```

#### Response

A Boolean value indicating whether effects are supported.

### getDeviceAbilities

This API is used to get a list of Beauty AR capabilities supported by the current device. You can use it together with `getPropertyRequiredAbilities`.

```
  Future<Map<String, bool>> getDeviceAbilities();
```

#### Response

`Map<String,Boolean>`:

- key: The name of a capability (the material name).
- value: Whether the current device supports the capability.

### isDeviceSupportMotion (V0.3.5.0)

To check if the current device supports a particular material

```
Future<bool> isDeviceSupportMotion(String motionResPath);
```

#### Parameters

| Parameter | Description |
| --- | --- |
| motionResPath | the sticker local file path |


---
*Source: [https://trtc.io/document/60200](https://trtc.io/document/60200)*
