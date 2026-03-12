# Integrating TEBeautyKit

## Features

To facilitate customers' quick integration of the beauty effect and simplify the development of UI panels, we provide the beauty effect UI component: TEBeautyKit. It includes further encapsulation of the SDK and customizable UI panels, as shown in the figure below. If you prefer not to use this UI, see [Integrating Core SDK  (Android)](https://www.tencentcloud.com/document/product/1143/60195).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8011db4fd1bc11f08f8f525400454e06.png)

## Demo Project: **TEBeautyDemo**

Clone the [demo project](https://github.com/Tencent-RTC/TencentEffect_Android) from GitHub, follow the instructions in the TEBeautyDemo/README document to run TEBeautyDemo, and then refer to this document for detailed steps on integrating the SDK with UI.

## Integrate TEBeautyKit

> **Note:**This library only supports **Tencent Effect SDK V3.5.0** and later versions.

### Step 1: Add dependency library

- [Integrate BeautyAR SDK](https://www.tencentcloud.com/document/product/1143/60195#.E9.9B.86.E6.88.90.E5.87.86.E5.A4.87)
- [Integrate BeautyAR Resources](https://www.tencentcloud.com/document/product/1143/60195#d45c5308-0cf3-4ed7-99ad-4e6156981a89)

### Step 2: Add TEBeautyKit dependency

Source Code Integration (Recommended)

Maven Integration

Downloading AAR Integration

1. Copy the TEBeautyKit module from the [demo project](https://github.com/Tencent-RTC/TencentEffect_Android/tree/main/TEBeautyDemo) into your project, and modify the SDK package type and version number in `tebeautykit/build.gradle` to match the SDK package type and version number in Step 1.

```
implementation 'com.tencent.mediacloud:TencentEffect_S1-04:SDK version number'
```

2. Then add the dependency on the TEBeautyKit module in the relevant module of your app:

```
implementation project(':tebeautykit')
```

1. Add the dependency on the TEBeautyKit library in your app's dependencies. The SDK version number should match the version number in Step 1.

```
dependencies{    ...    implementation 'com.tencent.mediacloud:TEBeautyKit:SDK version number'}
```

2. Since TEBeautyKit also depends on components like Gson and OkHttp, you need to add the following dependencies:

```
dependencies{    implementation 'com.google.code.gson:gson:2.8.2'    implementation 'com.squareup.okhttp3:okhttp:3.9.0'    implementation 'com.github.bumptech.glide:glide:4.12.0'    implementation 'androidx.appcompat:appcompat:1.0.0'    implementation 'androidx.constraintlayout:constraintlayout:2.1.3'    implementation 'androidx.recyclerview:recyclerview:1.2.1'}
```

1. [Download TEBeautyKit](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/Android/latest/tebeautykit_latest.zip) (The downloaded file will be a zip file. Extract it to get the AAR file.)
2. Copy the `tebeautykit-xxxx.aar` file to the app project's `libs` directory.
3. Open the app module's `build.gradle` and add the dependency reference:

```
dependencies{    ...    implementation fileTree(dir: 'libs', include: ['*.jar','*.aar'])}
```

4. Since TEBeautyKit also depends on components like Gson and OkHttp, you need to add the following dependencies:

```
dependencies{    implementation 'com.google.code.gson:gson:2.8.2'    implementation 'com.squareup.okhttp3:okhttp:3.9.0'    implementation 'com.github.bumptech.glide:glide:4.12.0'    implementation 'androidx.appcompat:appcompat:1.0.0'    implementation 'androidx.constraintlayout:constraintlayout:2.1.3'    implementation 'androidx.recyclerview:recyclerview:1.2.1'}
```

### Step 3: Add the Panel JSON File

Obtain the panel configuration file from the [demo project](https://github.com/Tencent-RTC/TencentEffect_Android/tree/main/TEBeautyDemo)'s `demo/src/main/assets/beauty_panel`, or click here to [download](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/Android/latest/beauty_panel-2024-05-14.zip) and unzip it. The file includes configurations for beauty, body beauty, filters, dynamic effect stickers, and segmentation properties. Select a set of JSON files according to your package type and place them in the `assets/beauty_panel` folder in your project (the **panel_icon** folder also needs to be placed in this directory).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f9bcf8d012c511f1a92352540097cba1.png)

The downloaded archive contains the files as shown above. Each package name corresponds to several JSON files. The table below explains each JSON file.

| **File** | **Description** |
| --- | --- |
| beauty.json | Configuration file for beauty effect, shaping, image adjustment, etc. |
| beauty_base_shape.json | Configuration file for basic face shaping. |
| beauty_body.json | Configuration file for body beauty. |
| beauty_general_shape.json | Configuration file for general face shaping. |
| beauty_image.json | Image Quality Adjustment Configuration File. |
| beauty_makeup.json | Single-Point Makeup Configuration File. |
| beauty_shape.json | Premium Styling Configuration File. |
| beauty_template | Beauty Filter Template Configuration File. |
| light_makeup.json | Light Makeup Configuration File. |
| lut.json | Filter configuration file. Note: Since different customers use different filter materials, customers can configure according to the JSON structure after downloading (refer to [JSON File Structure Description](#1ee2863b-9110-4bbc-8b47-29f6484cb077)) and delete the default configuration. |
| makeup.json | Configuration file for full-face makeup style. Note: Since different customers use different materials for full-face makeup style, customers can configure according to the JSON structure after downloading (refer to [JSON File Structure Description](#1ee2863b-9110-4bbc-8b47-29f6484cb077)). |
| motion_2d.json | 2d Dynamic effect sticker configuration file. Note: Since different customers use different dynamic effect sticker materials, customers can configure according to the JSON structure after downloading (refer to [JSON File Structure Description](#1ee2863b-9110-4bbc-8b47-29f6484cb077)). |
| motion_3d.json | 3D animated sticker configuration file. Note: Since different clients may utilize varying animated sticker materials, customers can customize the configuration according to the JSON structure after downloading (refer to [JSON File Structure Description](#1ee2863b-9110-4bbc-8b47-29f6484cb077) for details). |
| motion_gesture.json | Gesture animation sticker configuration file. Note: Since different clients may use varying animation sticker materials, customers can customize the configuration according to the JSON structure after downloading (refer to [JSON File Structure Description](#1ee2863b-9110-4bbc-8b47-29f6484cb077)). |
| segmentation.json | Background segmentation (virtual background) configuration file. Note: Since different customers use different segmentation materials, customers can configure according to the JSON structure after downloading (refer to [JSON File Structure Description](#1ee2863b-9110-4bbc-8b47-29f6484cb077)). |
| panel_icon | This folder is used for storing images configured in the JSON file, and must be added. |

## Use TEBeautyKit

We strongly recommend that you refer to the `TEMenuActivity.java` and `TECameraBaseActivity.java` of the [demo project](https://github.com/Tencent-RTC/TencentEffect_Android/tree/main/TEBeautyDemo)'s to understand how to integrate TEBeautyKit.

### Step 1: Authenticate

1. Apply for authorization to obtain the license URL and license key. Please refer to the [License Guide](https://trtc.io/document/60219).
2. Set the URL and key in the initialization code of the related business module to **trigger license download to avoid downloading temporarily before use**. For example, in our demo project, the download is triggered in the onCreate method of the application. However, we do not recommend triggering it here in your project because network permission might not be available or there could be a high rate of network failure at this time. Please choose a more appropriate time to trigger the license download.

```
// If you only want to trigger the download or update the license without caring about the authentication result, input null for the fourth parameter.//TEApplication.javaTEBeautyKit.setTELicense(context, LicenseConstant.mXMagicLicenceUrl, LicenseConstant.mXMagicKey, null);
```

3. Perform authentication before actually using the beauty feature (e.g., before launching the camera):

```
//TEMenuActivity.javaTEBeautyKit.setTELicense(context, LicenseConstant.mXMagicLicenceUrl, LicenseConstant.mXMagicKey, new TELicenseCheckListener() {         @Override         public void onLicenseCheckFinish(int errorCode, String msg) {             // Note: This callback may not be on the calling thread.             if (errorCode == TELicenseCheck.ERROR_OK) {                 // Authentication succeeded.             } else {                 // Authentication failed.             }         }     });
```

**Authentication error code description:**

| Error Code | Description |
| --- | --- |
| 0 | Success |
| -1 | Invalid input parameters, such as empty URL or KEY |
| -3 | Download failure. Please check your network settings. |
| -4 | TE authorization information read locally is empty, possibly due to I/O failure. |
| -5 | Content of the VCUBE TEMP license file is empty, possibly due to I/O failure. |
| -6 | JSON fields in the v_cube.license file are incorrect. Please contact the Tencent Cloud team to deal with it. |
| -7 | Signature verification failed. Please contact the Tencent Cloud team to deal with it. |
| -8 | Decryption failed. Please contact the Tencent Cloud team to deal with it. |
| -9 | JSON fields in the TELicense field are incorrect. Please contact the Tencent Cloud team to deal with it. |
| -10 | The TE authorization information parsed from the network is empty. Please contact the Tencent Cloud team to deal with it. |
| -11 | Failed to write TE authorization information to a local file, possibly due to I/O failure |
| -12 | Download failed, and parsing local assets also failed. |
| -13 | Authentication failed. Please check if the .so file is in the package or if the .so path is set correctly. |
| 3004/3005 | Invalid authorization. Please contact the Tencent Cloud team to deal with it. |
| 3015 | Bundle ID/Package Name mismatch. Check if the Bundle ID/Package Name used by your app is consistent with the applied one, and ensure you are using the correct license file. |
| 3018 | The license file has expired. You need to apply for a renewal from Tencent Cloud. |
| Others | Please contact the Tencent Cloud team to deal with it. |

### Step 2: Set the path

```
    //TEMenuActivity.java  String resPath = new File(getFilesDir(), AppConfig.getInstance().getBeautyFileDirName()).getAbsolutePath();  TEBeautyKit.setResPath(resPath);
```

### Step 3: Copy resources

The resource files mentioned here consist of two parts:

- The SDK model files, located in the `assets` directory of the SDK's AAR package.
- Filter and dynamic effect resource files, located in the `assets` directory of the demo project, named `lut` and `MotionRes` respectively.

Before using the beauty effect, you need to copy the above resources to the resPath set in Step 2. If the SDK version is not updated, you only need to copy it once. After a successful copy, you can record it in the SharedPreference of the app, so that you do not need to copy it again next time. For details, refer to the `copyRes` method of `TEMenuActivity.java` in the demo project.

```
//TEMenuActivity.javaprivate void copyRes() {
    if (!isNeedCopyRes()) {
        return;
    }
    new Thread(() -> {
        TEBeautyKit.copyRes(getApplicationContext());
    }).start();
}
```

### Step 4: Initialize TEBeautyKit and add the view to the page

```
//TECameraBaseActivity.javaTEBeautyKit.create(this.getApplicationContext(), beautyKit -> {    mBeautyKit = beautyKit;    initBeautyView(beautyKit);});public void initBeautyView(TEBeautyKit beautyKit){        List<TEPanelDataModel> panelDataModels = TEUIConfig.getInstance().getPanelDataList();TEUIConfig.getInstance().getPanelDataList();        panelDataModels.clear();        //Add the corresponding JSON based on the package features        TEPanelDataModel template = new TEPanelDataModel("beauty_panel/beauty_template.json", TEUIProperty.UICategory.BEAUTY_TEMPLATE);        TEPanelDataModel beauty1 = new TEPanelDataModel("beauty_panel/beauty.json", TEUIProperty.UICategory.BEAUTY);new TEPanelDataModel("beauty_panel/beauty.json", TEUIProperty.UICategory.BEAUTY);        TEPanelDataModel beauty2 = new TEPanelDataModel("beauty_panel/beauty_image.json", TEUIProperty.UICategory.BEAUTY);new TEPanelDataModel("beauty_panel/beauty_image.json", TEUIProperty.UICategory.BEAUTY);        TEPanelDataModel beauty4 = new TEPanelDataModel("beauty_panel/beauty_shape.json", TEUIProperty.UICategory.BEAUTY);        TEPanelDataModel beauty3 = new TEPanelDataModel("beauty_panel/beauty_makeup.json", TEUIProperty.UICategory.BEAUTY);        TEPanelDataModel lut = new TEPanelDataModel("beauty_panel/lut.json", TEUIProperty.UICategory.LUT);new TEPanelDataModel("beauty_panel/lut.json", TEUIProperty.UICategory.LUT);        TEPanelDataModel lightMakeup = new TEPanelDataModel("beauty_panel/light_makeup.json",new TEPanelDataModel("beauty_panel/light_makeup.json",                TEUIProperty.UICategory.LIGHT_MAKEUP);        TEPanelDataModel makeup = new TEPanelDataModel("beauty_panel/makeup.json", TEUIProperty.UICategory.MAKEUP);        TEPanelDataModel motion = new TEPanelDataModel("beauty_panel/motion_2d.json", TEUIProperty.UICategory.MOTION);        TEPanelDataModel motion2 = new TEPanelDataModel("beauty_panel/motion_3d.json", TEUIProperty.UICategory.MOTION);        TEPanelDataModel motion_gesture = new TEPanelDataModel("beauty_panel/motion_gesture.json",new TEPanelDataModel("beauty_panel/motion_gesture.json",                TEUIProperty.UICategory.MOTION);        TEPanelDataModel seg = new TEPanelDataModel("beauty_panel/segmentation.json", TEUIProperty.UICategory.SEGMENTATION);        panelDataModels.add(template);        panelDataModels.add(beauty1);        panelDataModels.add(beauty2);        panelDataModels.add(beauty4);        panelDataModels.add(beauty3);        panelDataModels.add(lut);        panelDataModels.add(lightMakeup);        panelDataModels.add(makeup);        panelDataModels.add(motion);        panelDataModels.add(motion2);        panelDataModels.add(motion_gesture);        panelDataModels.add(seg);        mTEPanelView = new TEPanelView(this);    mTEPanelView.setTEPanelViewCallback(this);    mTEPanelView.setupWithTEBeautyKit(beautyKit);    mTEPanelView.showView(this);    this.mPanelLayout.addView(mTEPanelView, new LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.WRAP_CONTENT));}
```

Depending on your subscription plan, fill in the corresponding feature JSON accordingly. For instance, if your plan does not include segmentation, there is no need to add `segmentation.json`. Similarly, if your package does not support 3D stickers, you should omit `motion_3d.json`.

### Step 5: Use beauty effect

We assume you have already implemented the camera application, can start the camera normally, and can call back the camera's SurfaceTexture texture information to Activity for beauty effect processing, as shown below:

```
//TECameraBaseActivity.java@Overridepublic int onCustomProcessTexture(int textureId, int textureWidth, int textureHeight) {     // The beauty effect SDK processes the textureId here, adds beauty effects and special effects for it, and returns the processed new textureID.}
```

If you have not yet implemented the camera application, you can refer to `TECameraBaseActivity.java` in the demo project and use the `GLCameraXView` component to add it to your Activity's layout for quick camera preview:

```
<com.tencent.demo.camera.camerax.GLCameraXView       android:id="@+id/te_camera_layout_camerax_view"     android:layout_width="match_parent"      android:layout_height="match_parent"     app:back_camera="false"      app:surface_view="false"    app:transparent="true" />
```

The beauty effect SDK processes each frame of data and returns the corresponding processing results. For detailed information on the process method, see the [API Documentation](https://www.tencentcloud.com/document/product/1143/60201).

```
//TECameraBaseActivity.java@Override
public int onCustomProcessTexture(int textureId, int textureWidth, int textureHeight) {
    return mBeautyKit.process(textureId, textureWidth, textureHeight);
}
```

### Step 6: Manage the lifecycle

- Lifecycle method onResume: It is recommended to call it in the `Activity`'s `onResume()` method. When called, it will resume the sound in the effects.

```
mBeautyKit.onResume();
```

- Lifecycle method onPause: It is recommended to call it in the Activity's `onPause()` method. When called, it will pause the sound in the effects.

```
mBeautyKit.onPause();
```

- Beauty effect release SDK: It is called when the OpenGL environment is being terminated. **It needs to be called in the GL thread, and cannot be called in the main thread (Activity's onDestroy);** otherwise, it may cause resource leaks and result in a white or black screen after multiple entries and exits.

```
@Override
public void onGLContextDestroy() {
    mBeautyKit.onDestroy();
}
```

### Step 7: Export and import beauty effect parameters

Export the current beauty effect parameters and save them in SharedPreference:

```
String json = mBeautyKit.exportInUseSDKParam();
if (json != null) {
    getSharedPreferences("demo_settings", Context.MODE_PRIVATE).edit().      putString("current_beauty_params", json).commit();
}
```

Next time when initializing TEBeautyKit, import this string to modify the default beauty effect:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f9c736547c8111ef8631525400a9236a.png)

## Appendix

### Panel JSON File Elucidation

- **Beautify,  body shaping.**

****

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2db7d35ac0b111ee9000525400461a83.png)

****

| Field | Description |
| --- | --- |
| displayName | Chinese Name. |
| displayNameEn | English Name. |
| hasSubTitle | Whether to include and display subheadings. |
| verticalLayout | Is the list of beauty attributes vertically scrollable. |
| id | The beauty filter template contains this data field, which is absent in other JSON files, serving as an identifier for the template. |
| icon | Image URL, supports both local and online images in Setting. Local images can come from assets and SD resources. As depicted above, assets images and SD card images are set as the full image path, while online images are set to their corresponding http link in Setting |
| sdkParam | The Beautification SDK entails four attributes, refer to the beautification parameter table for more insights |
| effectName | Key attributes for beautification, reference the [attribute parameter table](https://www.tencentcloud.com/document/product/1143/60207). |
| effectValue | Setting the attribute intensity, refer to the [attribute parameter table](https://www.tencentcloud.com/document/product/1143/60207). |
| resourcePath | Setting the resource path, refer to the [attribute parameter table](https://www.tencentcloud.com/document/product/1143/60207). |
| extraInfo | Setting other information, refer to the [attribute parameter table](https://www.tencentcloud.com/document/product/1143/60207). |
| uiState | Whether the current attribute is selected or in use, there are a total of 3 possible values:0: Not used and not selected.1: In use.2: Selected and in use. |

- **Filter, sticker, segmentation.**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2dbc518fc0b111ee9000525400461a83.png)

The configuration of filters and dynamic effect stickers is primarily identical, hence, the filterâs JSON is used for illustration here. Two new fields, downloadPath and resourceUri, have been added.

| Field | Description |
| --- | --- |
| downloadPath | If your filter material is downloaded from the internet, the configuration here represents the local storage location post-download. This pathway is a **relative path**; the full path is the combination of [Step 2](https://www.tencentcloud.com/document/product/1143/60196#1af9a4f7-925a-48fb-86e9-03e4753ce7d1) **+ the path set here** |
| resourceUri | If your material needs to be downloaded via network, configure the network address here, as in the third red box in the image above. However, if your filter material is local, configure the corresponding local address according to the image above. |

- **Makeup**

****

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2db6f138c0b111ee9000525400461a83.png)

An additional field `makeupLutStrength` under `extraInfo` has been included in the Full Style Makeup. This field is used to moderate the intensity of filters in the Full Style Makeup material<5> (configure this if the Full Style Makeup material supports filter intensity modulation). Refer to the beauty parameter table for this field.

### TEBeautyKit Method Descriptions

```
//Asynchronously creating the TEBeautyKit objectpublic static void create(@NonNull Context context, @NonNull OnInitListener initListener)//isEnableHighPerformance: Does High Performance Pattern is active?//After the High Performance Pattern is enabled, the system CPU/GPU resources occupied by Beauty enhancement are less, which reduces phone heating and stutters. Itâs more suitable for long-term use on lower-end devices.//However, please note: after enabling the high performance pattern, the following beauty options will be disabled://1.Eye section: Eye width, Eye height, Elimination of eye bags //2.Eyebrows: angle, distance, height, length, thickness, eyebrow peak//3. Mouth: Smile Lip//4. Facial: Slimming (natural, goddess, handsome), tightening lower jaw, wrinkle removal, removing nasolabial folds. It is recommended to use "face shape" to achieve a comprehensive, large-eyed, slimming effectpublic static void create(@NonNull Context context, boolean isEnableHighPerformance, @NonNull OnInitListener initListener)//The constructor of TEBeautyKit used for synchronously creating the TEBeautyKit objectpublic TEBeautyKit(Context context)/**
 * @param context                 ApplicationContext
 * @param isEnableHighPerformance Does it enable high-performance pattern?
 */
public TEBeautyKit(Context context, boolean isEnableHighPerformance)  /**
 * Set the mute state
 *
 * @param isMute true indicates mute
 */
public void setMute(boolean isMute)/**
 * If you are carrying out beauty processing on pictures, you need to invoke this method to set the type of the data source, which could either be a camera data source or a picture data source.
 * Camera data source: XmagicApi.PROCESS_TYPE_CAMERA_STREAM   Picture data source: XmagicApi.PROCESS_TYPE_PICTURE_DATA.
 * @param type The default type is a video stream.
 */
public void setBeautyStreamType(int type)/**
 * Enable or disable a specific feature
 *
 * @param featureName This takes a value from XmagicConstant.FeatureName
 * @param enable      true signifies enabling, false signifies disabling
 */
public void setFeatureEnableDisable(String featureName, boolean enable)/**
 * Perform beautification on the image
 *
 * @param bitmap
 * @param needReset
 * @return
 */
public Bitmap process(Bitmap bitmap, boolean needReset) /**
 * Process each frame of video/camera data
 *
 * @param textureId The id of the texture. This texture requires a texture type of GL_TEXTURE_2D and a pixel texture format of RGBA
 * @param width     Texture width
 * @param height    Texture height
 * @return Processed texture ID
 */
public int process(int textureId, int width, int height) /**
 * Update beauty properties
 *
 * @param paramList
 */
public void setEffectList(List<TEUIProperty.TESDKParam> paramList) /**
 * Updating the beauty attribute
 *
 * @param teParam
 */
public void setEffect(TEUIProperty.TESDKParam teParam)/**
 * Enable or disable enhanced pattern
 *
 * @param enableEnhancedMode true indicates the activation of the enhanced pattern, false deactivates the enhanced pattern
 * @return A return value of true indicates a state change has occurred, false indicates no change in state
 */
public boolean enableEnhancedMode(boolean enableEnhancedMode)/**
 * Retrieve the currently active beauty attributes as a string.
 * Clients can save the exported string locally and call the `setLastParamList` method after creating a TEPanelView object.
 * @return
 */
public String exportInUseSDKParam() /**
 * Used to restore the sound in stickers
 * Restore the Gyroscope sensor
 */
public void onResume() /**
 * Used for pausing the audio in stickers
 * Pause the gyroscope sensor
 */
public void onPause() /**
 * Destroy the beautifying effects
 * Note: It is essential to invoke this method in the GL thread
 */
public void onDestroy() /**
 * Set event listener, used for listening to Smartphone direction events, for adapter
 * @param listener Event listener callback
 */
public void setEventListener(EventListener listener)/**
 * SettingsetAIDataListener callback
 *
 * @param aiDataListener
 */
public void setAIDataListener(XmagicApi.XmagicAIDataListener aiDataListener)/**
 * Callback function for Setting motion effect tips, used to display the tips on the front-end page.
 *
 * @param tipsListener
 */
public void setTipsListener(XmagicApi.XmagicTipsListener tipsListener)/**
 * Intercept the screen on the current texture
 *
 * @param callback
 */
public void exportCurrentTexture(XmagicApi.ExportTextureCallback callback)/**
 * Set the anti-clockwise degree of texture rotation.
 * Primary Function: Used for the SDK's internal rotation of texture, post rotation to a certain degree, faces are upright, enabling in-house SDK to identify faces.
 * By default, the SDK internally utilizes the sensor to ascertain the required degree of rotation.
 *
 * @param orientation Values can only be 0,90,180,270
 */
public void setImageOrientation(TEImageOrientation orientation)/**
 * Determine if the current device supports this material
 *
 * @param motionResPath The path to the material file
 * @return
 */
public boolean isDeviceSupport(String motionResPath)/**
 * Access the on and off state of the beauty effect
 *
 * @return EffectState
 */
public EffectState getEffectState()/**
 * Indicates whether the beautification feature is enabled
 *
 * @param effectState ENABLED signifies it's turned on, DISABLED signifies it's turned off
 */
public void setEffectState(EffectState effectState) /**
 * Strategy implementation class for enhancing pattern settings. If not configured, the default implementation will be utilized.
 *
 * @param teParamEnhancingStrategy Class for enhancing pattern processing.
 */
public void setParamEnhancingStrategy(TEParamEnhancingStrategy teParamEnhancingStrategy) //The following are the static methods/**
 * Specifying the directory for beautification resources
 *
 * @param resPath
 */
public static void assignResPath(String resPath)/** * Unpack resource files from apk's assets to a specified path. First, you need to set the path: {@link #setResPath(String)}.  * This should be called once after first install of the App, or after an App update. * Copy xmagic resource from assets to local path. */public static boolean copyRes(Context context)/**
 * Carry out beauty enhancement authorization check
 * Attention: while using this method, if the callback interface isn't configured, authentication will not be performed (only network download of authentication information will be made), 
 * Therefore, you can refer to the demo not to configure the callback while calling in application, but call this method again before using the TEBeautyKit object (configuring callback interface) for authentication.
 * @param context                Application context
 * @param licenseKey             The licenseKey applied for on the platform
 * @param licenseUrl             The licenseUrl applied for on the platform
 * @param teLicenseCheckListener Authentication callback interface
 */
public static void setTELicense(Context context, String licenseUrl, String licenseKey, TELicenseCheck.TELicenseCheckListener teLicenseCheckListener)
```

### TEUIConfig explanation

- **Alter the panel color**
  - Global modification: After accessing the object through `TEUIConfig.getInstance()`, you can adjust the panel color by modifying the following fields.
  - Partial Modification: Using the `new TEUIConfig` object, adjust the panel color by modifying the following fields, and update the panel style using the `TEPanelView.updateUIConfig` method.

```
@ColorInt
public int panelBackgroundColor = 0x66000000;  //Default background color
@ColorInt
public int panelDividerColor = 0x19FFFFFF;  //Separator color
@ColorInt
public int panelItemCheckedColor = 0xFF006EFF;  //Selected item color
@ColorInt
public int textColor = 0x99FFFFFF; //Text color
@ColorInt
public int textCheckedColor = 0xFFFFFFFF; //Selected text color
@ColorInt
public int seekBarProgressColor = 0xFF006EFF; //Progress bar color
```

JSON file of the configuration panel

new version method

old version method

```
       List<TEPanelDataModel> panelDataModels = TEUIConfig.getInstance().getPanelDataList();        panelDataModels.clear();        //Add the corresponding JSON according to the package features        TEPanelDataModel template = new TEPanelDataModel("beauty_panel/beauty_template.json", TEUIProperty.UICategory.BEAUTY_TEMPLATE);        TEPanelDataModel beauty1 = new TEPanelDataModel("beauty_panel/beauty.json", TEUIProperty.UICategory.BEAUTY);        TEPanelDataModel beauty2 = new TEPanelDataModel("beauty_panel/beauty_image.json", TEUIProperty.UICategory.BEAUTY);        TEPanelDataModel beauty4 = new TEPanelDataModel("beauty_panel/beauty_shape.json", TEUIProperty.UICategory.BEAUTY);        TEPanelDataModel beauty3 = new TEPanelDataModel("beauty_panel/beauty_makeup.json", TEUIProperty.UICategory.BEAUTY);         TEPanelDataModel lut = new TEPanelDataModel("beauty_panel/lut.json", TEUIProperty.UICategory.LUT);        TEPanelDataModel lightMakeup = new TEPanelDataModel("beauty_panel/light_makeup.json",                TEUIProperty.UICategory.LIGHT_MAKEUP);        TEPanelDataModel makeup = new TEPanelDataModel("beauty_panel/makeup.json", TEUIProperty.UICategory.MAKEUP);        TEPanelDataModel motion = new TEPanelDataModel("beauty_panel/motion_2d.json", TEUIProperty.UICategory.MOTION);        TEPanelDataModel motion2 = new TEPanelDataModel("beauty_panel/motion_3d.json", TEUIProperty.UICategory.MOTION);        TEPanelDataModel motion_gesture = new TEPanelDataModel("beauty_panel/motion_gesture.json",                TEUIProperty.UICategory.MOTION);        TEPanelDataModel seg = new TEPanelDataModel("beauty_panel/segmentation.json", TEUIProperty.UICategory.SEGMENTATION);                panelDataModels.add(template);        panelDataModels.add(beauty1);        panelDataModels.add(beauty2);        panelDataModels.add(beauty4);        panelDataModels.add(beauty3);        panelDataModels.add(lut);        panelDataModels.add(lightMakeup);        panelDataModels.add(makeup);        panelDataModels.add(motion);        panelDataModels.add(motion2);        panelDataModels.add(motion_gesture);        panelDataModels.add(seg);
```

```
/*** Set the JSON file path for the beauty panel* @param beauty The JSON file path for beauty attributes, set to null if not available* @param beautyBody The JSON file path for body sculpting attributes, set to null if not available* @param lut The JSON file path for filter attributes, set to null if not available* @param motion The JSON file path for motion sticker attributes, set to null if not available* @param makeup The JSON file path for full makeup style attributes, set to null if not available* @param segmentation The JSON file path for segmentation attributes, set to null if not available*/public void setTEPanelViewRes(String beauty, String beautyBody, String lut, String motion, String makeup, String segmentation)
```

Updating Panel Language

```
//When the client program detects a modification to the system's font, it may invoke this function. At present, the panel only supports Chinese and English.public void setSystemLocal(Locale locale)
```

### Description of TEPanelView

```
/**
 * This is utilized for setting the previously used beauty effect data, with the intent to revert the beauty panel back to its prior state.
 * Note: This method needs to be used prior to the {@link #showView(TEPanelViewCallback tePanelViewCallback)}} method.
 *
 * @param lastParamList The beauty data, which is accessible through the {@link TEBeautyKit#exportInUseSDKParam()} ()}} method, and then stored, to be passed as a string when starting the beauty feature the next time.
 */
void setLastParamList(String lastParamList);

/**
 * Present the beauty panel
 * @param tePanelViewCallback The interface callback for panel events
 */
void showView(TEPanelViewCallback tePanelViewCallback);

/**
 * Synchronizes with TEBeautyKit object, which the beauty panel calls directly to set attributes when a user selects an item.
 * @param beautyKit The TEBeautyKit object
 */
void setupWithTEBeautyKit(TEBeautyKit beautyKit);/**
 * Select Self-Definition split or green screen item from the Settings, because the green screen or Self-Definition split button jumps to the gallery after clicking,
 * Only after the user has selected a picture or video, the corresponding item can be selected. If the user cancels the operation during this process, the corresponding item cannot be selected
 *
 * @param uiProperty
 */
void validatePanelViewItem(TEUIProperty uiProperty);/**
 * Configuring the UI of the current panel
 * @param uiConfig
 */
void updateUIConfig(TEUIConfig uiConfig);
```


---
*Source: [https://trtc.io/document/60196](https://trtc.io/document/60196)*
