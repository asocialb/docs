# API Document

Beauty AR SDK Core Interface Class `XmagicApi.java`, utilized for initializing the SDK, updating beauty metric values, invoking animated effects, amongst other features.

**The overall calling process of each API is as follows:**

****

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bcc69c0c7c9811ef8829525400fdb830.png)

## List of static properties and methods of XmagicApi

| API | Description |
| --- | --- |
| VERSION | The SDK version number can be retrieved via XmagicApi.VERSION (added in V3.5.0). |
| [setLibPathAndLoad](https://www.tencentcloud.com/document/product/1143/45399#989ae975-c50e-4e8e-9c5c-b36420e93d52) | Set the path of the '.so' Library. If the '.so' Library is built into the apk package, this interface is not needed. |
| [addAiModeFilesFromAssets](https://www.tencentcloud.com/document/product/1143/45399#addAiModeFilesFromAssets) | Transfer the content located within the directories Light3DPlugin, LightCore, LightHandPlugin, LightBodyPlugin, LightSegmentPlugin under application assets to your designated directory. |
| [addAiModeFiles](https://www.tencentcloud.com/document/product/1143/45399#addAiModeFiles) | Copy the AI model files downloaded by the client to the corresponding folders. |
| [getDeviceLevel](https://www.tencentcloud.com/document/product/1143/45399#42998e0d-f44e-4989-9d9f-b24f908be308) | Get the device level. |

### Static method: setLibPathAndLoad

Set the path of the so Library and trigger loading.

If the so Library is built into the apk package, this interface is not needed. If the so Library is downloaded dynamically, it should be invoked before authentication and `new XmagicApi()`.

- Passing in null indicates loading the so from the default path. Please ensure that the so is built into the APK package.
- Pass in non-null: such as `data/data/package name/files/xmagic_libs`, the so will be loaded from this directory.

```
static boolean setLibPathAndLoad(String path)
```

### Static method: addAiModeFilesFromAssets

SDK's Model Resource Files can be built into the assets directory of the apk package or downloaded dynamically. If they are built into the assets directory, the model resource files need to be copied to the specified directory before the SDK is used for the first time. This operation only needs to be done once. After upgrading the SDK version, it needs to be executed again.

- context applicationcontext.
- resDir is the root directory for storing SDK model resources. This directory is the same as the path parameter passed in when creating a new XmagicApi() object.
- Returned values:
  - 0: Copy successful
  - -1: denotes that the context is null
  - -2: denotes an IO error

```
static int addAiModeFilesFromAssets(Context context, String resDir)
```

### Static method: addAiModeFiles

If you have not embedded the SDK's model resource file in the APK package but download it dynamically, after downloading and decompressing, you can call this method to copy the downloaded SDK model resource files to the corresponding folder.

- inputResDir is the directory of the successfully downloaded model files.
- resDir is the root directory for storing SDK model resources. This directory is the same as the path parameter passed in when creating a new XmagicApi() object.
- Returned values:
  - 0: denotes success
  - -1: inputResDir is not exists
  - -2: Signifies an IO error

```
static int addAiModeFiles(String inputResDir, String resDir)
```

### Static method: getDeviceLevel

Obtain device level, added in V3.7.0. You can [enable or disable the related SDK feature](https://www.tencentcloud.com/document/product/1143/60201#818a373c-f0db-4900-bccb-8df0279cf35e) based on the device level, or set [high-performance mode](https://www.tencentcloud.com/document/product/1143/60201#18d060d6-5511-4476-b4ad-e3bec0a3f17e) on lower-level phones.

> **Note:**During versions V3.7.0 - V3.9.0, if you need to call the `getDeviceLevel` method before `new XmagicApi,` you must include the benchmark folder from the SDK's assets directory into your APK's assets. If you call `getDeviceLevel` after `new XmagicApi`, there is no need to include it.We will optimize this issue in version V3.9.1.

```
static DeviceLevel getDevicLevel(Context context)public enum DeviceLevel {    DEVICE_LEVEL_VERY_LOW(1),    DEVICE_LEVEL_LOW(2),    DEVICE_LEVEL_MIDDLE(3),    DEVICE_LEVEL_MIDDLE_HIGH(4),    DEVICE_LEVEL_HIGH(5);    private final int value;    DeviceLevel(int value) {        this.value = value;    }    public int getValue() {        return value;    }}
```

## List of Public Methods of XmagicApi

| API | Description |
| --- | --- |
| [XmagicApi](https://www.tencentcloud.com/document/product/1143/45399#xmagicapi) | constructor. |
| [process](https://www.tencentcloud.com/document/product/1143/45399#process) | Methods for rendering data with the SDK, used for processing images or video streams. |
| [setEffect](https://www.tencentcloud.com/document/product/1143/45399#32a345ed-73c4-4c60-bc7e-3f91b9a4755c) | Set effects such as beauty, aesthetic shape, filters, makeup, stickers, and segmentation, and can be invoked in any thread. |
| [setXmagicLogLevel](https://www.tencentcloud.com/document/product/1143/45399#47d69b19-adc7-494a-8f31-0bdb7aa88002) | Set the SDK's log level, which defaults to `Log.WARN`. During development and debugging, it can be set to `Log.DEBUG` if necessary. For official release, make sure to set it to `Log.WARN` or `Log.ERROR` to avoid performance issues caused by excessive logging.**Invoke after new XmagicApi().** |
| [setFeatureEnableDisable](https://www.tencentcloud.com/document/product/1143/45399#818a373c-f0db-4900-bccb-8df0279cf35e) | Enable or disable specific capability. |
| [setAIDataListener](https://www.tencentcloud.com/document/product/1143/45399#setaidatalistener) | Configure the callback for face, gesture, and body detection statuses. |
| [setAudioMute](https://www.tencentcloud.com/document/product/1143/45399#849a8119-8319-4c27-9aad-f01d4324288a) | Toggle mute when using motion effect material. Parameter: true means mute, false means not mute. |
| [onPause](https://www.tencentcloud.com/document/product/1143/45399#b43e74aa-9bcb-46c8-9196-a183e02645bd) | Pause the sound playback in the special effects, can be bound to the Activity onPause lifecycle. |
| [onResume](https://www.tencentcloud.com/document/product/1143/45399#onresume) | Resume the sound playback in the special effects, can be bound to the Activity onResume lifecycle. |
| [onDestroy](https://www.tencentcloud.com/document/product/1143/45399#ondestroy) | Terminate `xmagic`, which necessitates its invocation within the `GL` thread. |
| [setImageOrientation](https://www.tencentcloud.com/document/product/1143/45399#dfab4171-cde2-47b9-816c-3db1d1f2e008) | Set the image orientation so that AI can recognize faces from different directions. If set, the direction provided by `sensorChanged` will be ignored. |
| [sensorChanged](https://www.tencentcloud.com/document/product/1143/45399#sensorchanged) | Use the system sensor to judge the current phone's rotation angle, so that the AI can recognize faces in different orientations. |
| [isDeviceSupport](https://www.tencentcloud.com/document/product/1143/45399#c5145f76-a413-42e7-b5d6-14da23aa3648) | Pass the path of a dynamic effect material to the SDK, and detect whether the current device fully supports this dynamic effect. |
| [isSupportBeauty](https://www.tencentcloud.com/document/product/1143/45399#issupportbeauty) | Determine whether the current device supports refinement (OpenGL3.0). |
| [exportCurrentTexture](https://www.tencentcloud.com/document/product/1143/45399#31497bd0-15d2-45ae-959b-19102b2ea0ba) | Retrieve the screen on the current texture |
| [setTipsListener](https://www.tencentcloud.com/document/product/1143/45399#10104f21-9c05-4ee0-96ed-370683785227) | Setting up callback functions for animated hint text, designated to display hints on the frontend page. |
| [setSyncMode](https://www.tencentcloud.com/document/product/1143/45399#15b2378c-671a-4b1d-a8e9-d103963fa7cf) | Set up synchronized video frame processing. |

### XmagicApi Constructor Method

```
public XmagicApi(Context context, EffectMode effectMode, String resDir)public XmagicApi(Context context, EffectMode effectMode, String resDir,OnXmagicPropertyErrorListener xmagicPropertyErrorListener)@Deprecatedpublic XmagicApi(Context context, String resDir)@Deprecatedpublic XmagicApi(Context context, String resDir,OnXmagicPropertyErrorListener xmagicPropertyErrorListener)public interface OnXmagicPropertyErrorListener {    void onXmagicPropertyError(String errorMsg, int code);}public enum EffectMode{    NORMAL(0),    PRO(1);    private final int value;    EffectMode(int value) {        this.value = value;    }    public int getValue() {        return value;    }}
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| context | Context | context. |
| effectMode | EffectMode | This parameter was added in V3.9.0.It is used to specify performance and effect modes, with possible values being NORMAL and PRO. NORMAL can meet most scenarios with better performance but fewer features. Please choose according to your needs.For the specific differences between the two, see: [EffectMode (High Performance Mode) Usage Guide](https://www.tencentcloud.com/document/product/1143/73786). |
| resDir | String | SDK model resource file directory. Before using the SDK, you need to designate a directory to store the SDK's model resource files. It is recommended to use the app's private directory:`resDir = context.getFilesDir().getAbsolutePath() + "/xmagic"` Additionally, before instantiating XmagicApi, please first invoke the static method [addAiModeFilesFromAssets](https://www.tencentcloud.com/document/product/1143/60201#addAiModeFilesFromAssets) or [addAiModeFiles](https://www.tencentcloud.com/document/product/1143/60201#addAiModeFiles) of XmagicApi to copy the model resource files to resDir. |
| xmagicPropertyErrorListener | OnXmagicPropertyErrorListener | Error Callback Interface. During the use of the SDK, this interface will callback some internal error information. Generally used during development and debugging. |

OnXmagicPropertyErrorListener returns a table of error codes and their meanings:

| Error code | Meaning |
| --- | --- |
| -1 | Unknown error. |
| -100 | 3D engine resource initialization failed. |
| -200 | GAN materials are not supported. |
| -300 | This device does not support this material component. |
| -400 | The template JSON content is empty. |
| -500 | The SDK version is too low. |
| -600 | Splitting is not supported. |
| -700 | OpenGL is not supported. |
| -800 | Scripting is not supported. |
| 5,000 | The resolution of the split background image exceeds 2160x3840. |
| 5001 | Insufficient memory required to segment the background image. |
| 5002 | Failed to parse the video segmentation of the background. |
| 5003 | Background video segment exceeds 200 seconds. |
| 5004 | Background video segment format unsupported. |
| 5005 | Background image segment possesses rotation angle |

### process

Methods for rendering data with the SDK, used for processing images or video streams. When processing video streams, it can be used within the camera data callback function.

```
// Render the textureint process(int srcTextureId, int srcTextureWidth, int srcTextureHeight) // Render the bitmapBitmap process(Bitmap bitmap, boolean needReset)
```

| Parameter | Meaning |
| --- | --- |
| int srcTextureId | The texture that needs to be rendered. The type is: OpenGL 2D texture format, and the pixel format is RGBA. |
| int srcTextureWidth | Width of the texture that needs to be rendered. |
| int srcTextureHeight | Height of the texture that needs to be rendered. |
| Bitmap bitmap | The recommended maximum size is 2160 x 4096. Larger images have poor face recognition results or cannot get faces recognized and are likely to cause OOM problems. Shrink such images first before passing them in. |
| boolean needReset | In the following scenarios, set needReset to true:Processing an image for the first time, or switching images.First time using partition.Initial use of animated effects.First-time usage of makeup. |

### setEffect

Set effects such as beauty, aesthetic shape, filters, makeup, stickers, and segmentation, and can be invoked in any thread. For specific parameters, see [Effect Parameters](https://www.tencentcloud.com/document/product/1143/60207).

```
void setEffect(String effectName, int effectValue, String resourcePath, Map<String, String> extraInfo)
```

### setXmagicLogLevel

**Invoke after new XmagicApi().** Set the SDK's log level, which defaults to `Log.WARN`. During development and debugging, it can be set to `Log.DEBUG` if necessary. For official release, make sure to set it to `Log.WARN` or `Log.ERROR` to avoid performance issues caused by excessive logging.

If `ITELogger` is set, the SDK's internal logs will be redirected to the user.

```
public void setXmagicLogLevel(int level);public void setXmagicLogLevel(int level, final ITELogger logger);public interface ITELogger{    void log(int severity, String tag, String msg);    void log(int severity, String tag, String msg, Throwable throwable);}
```

### setFeatureEnableDisable

Enable or disable a specific capability as needed.

```
void setFeatureEnableDisable(String featureName, boolean enable)
```

| Parameter | Meaning |
| --- | --- |
| String featureName | Name of the atomic capabilityValid values:`XmagicConstant.FeatureName.SEGMENTATION_SKIN` Skin Segmentation Capability, after enabling, can make the skin smoothing and whitening areas more accurate.`XmagicConstant.FeatureName.SEGMENTATION_FACE_BLOCK` Face Occlusion Detection Capability, after enabling, can avoid makeup being applied to occluded areas.`XmagicConstant.FeatureName.WHITEN_ONLY_SKIN_AREA ` Whitening only works on skin`XmagicConstant.FeatureName.SMART_BEAUTY` Intelligent Beauty (reduces beauty and makeup effects for men and babies)`XmagicConstant.FeatureName.ANIMOJI_52_EXPRESSION` Face Expression Capability`XmagicConstant.FeatureName.BODY_3D_POINT` Body Point Capability`XmagicConstant.FeatureName.HAND_DETECT` Gesture Detection Capability |
| boolean enable | true indicates to enable this capability, false indicates to disable this capability |

Among the mentioned capabilities, the commonly used ones are `SEGMENTATION_SKIN` and `SEGMENTATION_FACE_BLOCK`. The SDK will enable these two capabilities by default based on the value of [getDeviceLevel](https://www.tencentcloud.com/document/product/1143/60201#42998e0d-f44e-4989-9d9f-b24f908be308). If you need to enable them manually, it is recommended to enable `SEGMENTATION_SKIN` when level >= 4, and enable `SEGMENTATION_FACE_BLOCK` when level >= 5.

### setAIDataListener

```
public void setAIDataListener(final XmagicAIDataListener aiDataListener);public interface OnAIDataListener {    void onFaceDataUpdated(List<TEFaceData> faceDataList);      void onBodyDataUpdated(List<TEBodyData> bodyDataList);    void onAIDataUpdated(String jsonString);    @Deprecated    void onHandDataUpdated(List<TEHandData> handDataList);}
```

#### onFaceDataUpdated

The SDK will callback after starting to process the image. When a face is recognized, it callbacks List<FaceData>, the size of the list is the number of faces. When there are no faces, it callbacks an empty List.

The definition of TEFaceData is as follows: points are coordinates for 83 face points, each with x and y coordinates, so the length of points is fixed at 166. The coordinate values are not based on the original input image but are face coordinates obtained after scaling the short edge of the original image to 256.

Therefore, it is recommended to use the callback data here only to determine whether there are faces in the current screen and how many faces there are. If you need higher precision face points, please use the data from `onAIDataUpdated` callback.

```
public class TEFaceData {    public float[] points;    public TEFaceData() {    }    public TEFaceData(float[] points) {        this.points = points;    }}
```

#### onHandDataUpdated

Deprecated interface, no data callback. The old version SDK callbacks when gesture effects are set and gestures are recognized.

If gesture data is needed, please use the data from `onAIDataUpdated` callback.

#### onBodyDataUpdated

Callbacks when body attributes are set and the body is recognized; no callbacks in other cases. The callback is the coordinates of the body's 42 points, the coordinate values are based on the width and height of the input image. If a point is not detected, the coordinate value is 0.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea781ab698f411f0aa4252540044a08e.png)

#### onAIDataUpdated

Callback detailed data of face, gesture, and body 3D usually requires a specific license to have data. An example data is as follows:

- For detailed information about `face_info`, please check [Facial Keypoint Detection](https://www.tencentcloud.com/document/product/1143/60310).
- For detailed information about `hand_info`, please check [Gesture Recognition](https://www.tencentcloud.com/document/product/1143/60309).
- For detailed information about `body_3d_info`, please check [Body Keypoints Android](https://www.tencentcloud.com/document/product/1143/53584) and [Body Keypoints iOS](https://www.tencentcloud.com/document/product/1143/52661).

```
{    "face_info": [{        "expression_weights": [0.001172, 0, 0.029249, ... , 0.060041, 0],        "face_256_point": [211.844238, 673.247192, ... , 339.247925, 654.792603],        "face_256_visible": [0.163925, 0.14921, ... , 0.99887, 0.99887],        "face_3d_info": {            "pitch": -3.860844850540161,            "pitch_fixed": 2.1123428344726562,            "roll": -12.797032356262207,            "roll_fixed": 1.3187808990478516,            "transform": [                [0.8919625878334045, 0.2843534052371979, 0.3514907658100128, 0],                [-0.17628398537635803, 0.9346542954444885, -0.3087802827358246, 0],                [-0.41632509231567383, 0.21345829963684082, 0.88380366563797, 0],                [-0.020958196371793747, -0.04502145200967789, -0.6078543663024902, 1]            ],            "yaw": 24.824481964111328,            "yaw_fixed": 25.02082061767578        },        "left_eye_high_vis_ratio": 0,        "left_eyebrow_high_vis_ratio": 0,        "mouth_high_vis_ratio": 1,        "out_of_screen": false,        "right_eye_high_vis_ratio": 1,        "right_eyebrow_high_vis_ratio": 0.821429,        "trace_id": 21    }],    "hand_info": {        "gesture": "PAPER",        "hand_point_2d": [180.71888732910156, 569.2958984375, ... , 353.8714294433594, 836.246826171875]    },    "body_3d_info": {        "imageHeight": 652,        "imageWidth": 320,        "items": [{            "index": 1,            "pose": [0.049122653901576996, ... , 0],            "position_x": [190.47494506835938, 235.23098754882812, ... , 4.948424339294434, 173.59298706054688],            "position_y": [777.2109375, 836.488037109375, ... , 161.19752502441406, 405.83905029296875],            "position_z": [0, 0, ... , 0, 0],            "rotation": [{                "data": [0.9944382905960083, -0.09695644676685333, -0.0411277711391449, 0.000708006089553237]            },              ......            {                "data": [0.9907779693603516, 0.13549542427062988, 0, 0]            }, {                "data": [1, 0, 0, 0]            }]        }]    }}
```

### setAudioMute

Whether to mute when using animation materials (Added in V2.5.0):

Parameter: true indicates mute, false denotes non-mute.

### onPause

Pause the sound playback in the special effects, can be bound to the Activity onPause lifecycle.

```
void onPause()
```

### onResume

Resume the sound playback in the special effects, can be bound to the Activity onResume lifecycle.

```
void onResume()
```

### onDestroy

Clears GL thread resources and needs to be called within the GL thread. Sample code:

```
// Refer to the sample code in `TECameraBaseActivity.java`public void onGLContextDestroy() {    if (this.mXMagicApi != null) {        this.mXMagicApi.onDestroy();        this.mXMagicApi = null;    }}
```

### setImageOrientation

```
void setImageOrientation(TEImageOrientation orientation)public enum TEImageOrientation {    ROTATION_0,    ROTATION_90,    ROTATION_180,    ROTATION_270}
```

Set the image orientation so that AI can recognize faces from different directions. If set, the direction provided by `sensorChanged` will be ignored. Example directions are as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea9e70ec98f411f08bb25254005ef0f7.png)

If the image you provide to the SDK is always upright (Rotation = 0), then you do not need to invoke this interface.

### sensorChanged

```
void sensorChanged(android.hardware.SensorEvent event, android.hardware.Sensor accelerometer)
```

Use the system sensor to determine the current phone's rotation angle, so that the AI can recognize faces in different orientations. Note: If a fixed direction is set through `setImageOrientation`, the direction provided by `sensorChanged` will be ignored.

Usage example:

```
public class MyActivity implements SensorEventListener {    private SensorManager mSensorManager;    private Sensor mAccelerometer;        @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        mSensorManager = (SensorManager) getSystemService(Context.SENSOR_SERVICE);        mAccelerometer = mSensorManager.getDefaultSensor(Sensor.TYPE_ACCELEROMETER);    }            @Override    protected void onResume() {        super.onResume();        mSensorManager.registerListener(this, mAccelerometer, SensorManager.SENSOR_DELAY_NORMAL);    }    @Override    protected void onPause() {        super.onPause();        mSensorManager.unregisterListener(this);    }    @Override    public void onSensorChanged(SensorEvent event) {        if (mXMagicApi != null) {            mXMagicApi.sensorChanged(event, mAccelerometer);        }    }}
```

### isDeviceSupport

```
boolean isDeviceSupport(String motionResPath)
```

Pass the path of a dynamic effect material to the SDK, and detect whether the current device fully supports this dynamic effect.

For example, if a dynamic effect contains lipstick, facial stickers, and background segmentation, if the current device does not support background segmentation, this interface will return false. False does not mean that the dynamic effect cannot be used at all, but some effects cannot be presented.

### isSupportBeauty

Determine whether the current model supports beauty (OpenGL3.0). Currently, most mobile phones on the market support OpenGL3.0, so usually there is no need to use this interface.

```
boolean isSupportBeauty()
```

### exportCurrentTexture

Retrieve the screen on the current texture

```
void exportCurrentTexture(ExportTextureCallback callback)public interface ExportTextureCallback {    void onCallback(Bitmap bitmap);}
```

### setTipsListener

Establish the callback for animated effect cues, utilized for displaying prompts onto the frontend page. For instance, certain materials might instruct users to nod their heads, extend their palms, or make a heart shape.

**Note: The callback method may not be on the main thread.**

```
void setTipsListener(XmagicApi.XmagicTipsListener effectTipsListener)
```

**XmagicTipsListener includes the following methods:**

```
public interface XmagicTipsListener {    /**     * Display tips.     * @param tips The returned prompt text information.     * @param tipsIcon The file path of the tips icon. You can parse the corresponding image based on the file path. If it's a pag file, you need to use pagView to display it.     *                  Note: tipsIcon may be empty, return null if not configured in the material.     * @param type Tips category, 0 means both tips and tipsIcon have values, 1 means it is a pag material and only tipsIcon has values.     * @param duration Tips display duration, in milliseconds.     */    void tipsNeedShow(String tips, String tipsIcon, int type, int duration);    /**     * Hide tips.     * @param tips The returned prompt text information.     * @param tipsIcon The file path of the tips icon. You can parse the corresponding image based on the file path. If it's a pag file, you need to use pagView to display it.     *                 Note: tipsIcon may be empty, return null if not configured in the material.     * @param type Tips category, 0 means both tips and tipsIcon have values, 1 means it is a pag material and only tipsIcon has values.     */    void tipsNeedHide(String tips, String tipsIcon, int type);}
```

**The example code is as follows:**

```
public void tipsNeedShow(final String tips, String tipsIcon, int type, int duration) {    final int tipsType = type;    final String tipsIconPath = tipsIcon;    mMainThreadHandler.post(new Runnable() {        @Override        public void run() {            if (tipsType == 0) {                if (!TextUtils.isEmpty(tipsIconPath) && !mImageTipsIsShow) {                    mTipsImageView.setVisibility(View.VISIBLE);                    Bitmap bitmap = BitmapUtils.decodeSampleBitmap(AEModule.getContext(), tipsIconPath, Integer.MAX_VALUE, Integer.MAX_VALUE);                    mTipsImageView.setImageBitmap(bitmap);                    mImageTipsIsShow = true;                } else {                    mTipsImageView.setVisibility(View.GONE);                }                mTipsTextView.setText(tips);            } else {                pagFile = PAGFile.Load(tipsIconPath);                tipsPAGView.post(new Runnable() {@                    Override                    public void run() {                        if (pagFile != null) {                            tipsPAGView.setRepeatCount(-1);                            tipsPAGView.setComposition(pagFile);                            tipsPAGView.setProgress(0);                            tipsPAGView.play();                            tipsPAGView.setVisibility(View.VISIBLE);                        }                    }                });            }        }    });}public void tipsNeedHide(String tips, String tipsIcon, int type) {    final int tipsType = type;    final String tipsIconPath = tipsIcon;    mMainThreadHandler.post(new Runnable() {        @Override        public void run() {            if (tipsType == 0) {                mTipsContainer.setVisibility(View.GONE);                mImageTipsIsShow = false;            } else {                tipsPAGView.post(new Runnable() {                    @Override                    public void run() {                        tipsPAGView.stop();                        tipsPAGView.setVisibility(View.GONE);                    }                });            }        }    });}
```

### setSyncMode

Some recognition and rendering logic inside the SDK is processed asynchronously. By calling this interface, you can make the SDK process the input images synchronously for the next `syncFrameCount` frames to meet specific requirements in certain scenarios. For example, before processing the first frame, calling this interface allows the SDK to process several frames synchronously, which can prevent unfiltered images from being displayed. However, this may increase the black screen duration before the first frame is rendered, so please use it as needed.

```
void setSyncMode(boolean isSync, int syncFrameCount)
```

| Parameter | Meaning |
| --- | --- |
| isSync | Whether to process image frames synchronously. |
| syncFrameCount | The number of frames to be processed synchronously. The value must be >= 0. If set to -1, it indicates an unlimited number of frames. |


---
*Source: [https://trtc.io/document/60201](https://trtc.io/document/60201)*
