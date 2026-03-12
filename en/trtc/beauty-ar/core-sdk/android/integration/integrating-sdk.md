# Integrating SDK

If you wish to quickly integrate and experience the features of BeautyAR, we recommend adopting the [Integrating UIKit](https://www.tencentcloud.com/document/product/1143/60196) approach.

For those integrating beauty effects alongside MLVB SDK /TRTC SDK /Short Video SDK(UGSV), please follow the integration guidelines for [Integrating With MLVB SDK](https://www.tencentcloud.com/document/product/1143/73767), [Integrating With TRTC SDK](https://www.tencentcloud.com/document/product/1143/73768) , and [Integrating With UGSV SDK](https://www.tencentcloud.com/document/product/1143/73769) respectively.

If you prefer not to use UIKit and instead directly implement Core SDK interface calls, you may proceed with this guide for integration.

## Developer Environment Requirements

- Android 7.0 (SDK API level 24) or later versions are recommended.
- Android Studio 3.5 or later versions.

## Demo Project: TEBeauty_API_Example

Clone the [demo project](https://github.com/Tencent-RTC/TencentEffect_Android) from GitHub, where the TEBeautyDemo is a demo project with UI, and the TEBeauty_API_Example is a demo project without UI.

Follow the instructions in the TEBeauty_API_Example/README document to get the TEBeauty_API_Example running, and then combine this text to understand the detailed steps for integrating the SDK without a UI.

## Integrate SDK

> **Noteï¼**In the demo project on GitHub, the SDK is integrated using Maven.

Maven Intergration

Manual Integration (Built-in Resources)

Manual Integration (Dynamic Resource Download)

The  SDK has been released to the mavenCentral repository, and you can configure Gradle to download updates automatically.

1. Add the BeautyAR  SDK dependency in the dependencies section.

```
dependencies {//For example, the S1-04 package is as follows: implementation 'com.tencent.mediacloud:TencentEffect_S1-04:version number'//The version number can be found on the Version History page on the official website, e.g., 3.0.0.13. You can also use latest.release for the version number.//But please note: using latest.release will always keep your SDK version up to date, which might not meet your expectations for versions with major changes. Use latest.release with caution.
```

2. In defaultConfig, specify the CPU architecture for the app.

```
defaultConfig { ndk {     abiFilters "armeabi-v7a", "arm64-v8a" }}
```

> **Note:**Currently, the BeautyAR SDK supports armeabi-v7a and arm64-v8a.

3. Click ![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7a7a79270d811efa016525400bdab9d.png)<2> to automatically download the SDK and integrate it into the project.

#### Maven Address for Each Package

| Version | Maven Address |
| --- | --- |
| A1 - 01 | implementation 'com.tencent.mediacloud:TencentEffect_A1-01:version number' |
| A1 - 02 | implementation 'com.tencent.mediacloud:TencentEffect_A1-02:version number' |
| A1 - 03 | implementation 'com.tencent.mediacloud:TencentEffect_A1-03:version number' |
| A1 - 04 | implementation 'com.tencent.mediacloud:TencentEffect_A1-04:version number' |
| A1 - 05 | implementation 'com.tencent.mediacloud:TencentEffect_A1-05:version number' |
| A1 - 06 | implementation 'com.tencent.mediacloud:TencentEffect_A1-06:version number' |
| S1 - 00 | implementation 'com.tencent.mediacloud:TencentEffect_S1-00:version number' |
| S1 - 01 | implementation 'com.tencent.mediacloud:TencentEffect_S1-01:version number' |
| S1 - 02 | implementation 'com.tencent.mediacloud:TencentEffect_S1-02:version number' |
| S1 - 03 | implementation 'com.tencent.mediacloud:TencentEffect_S1-03:version number' |
| S1 - 04 | implementation 'com.tencent.mediacloud:TencentEffect_S1-04:version number' |
| S1 - 05 | implementation 'com.tencent.mediacloud:TencentEffect_S1-05:version number' |
| S1 - 06 | implementation 'com.tencent.mediacloud:TencentEffect_S1-06:version number' |
| S1 - 07 | implementation 'com.tencent.mediacloud:TencentEffect_S1-07:version number' |

#### Downloading SDK

[Download the SDK](https://trtc.io/sdkDownload?id=beauty) and decompress it. The directory structure is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/de32550570d811efa25e52540075b605.png)

#### Integration

Copy the `xmagic-xxxx.aar` file from the `SDK` folder to your project's `libs` directory.

#### Importing Method

Open the app module's `build.gradle` and add the dependency reference:

```
android{    ...    defaultConfig {        applicationId "Modify it with the package name bound to the authorized license."        ....    }    packagingOptions {        pickFirst '**/libc++_shared.so'    }}dependencies{    ...    compile fileTree(dir: 'libs', include: ['*.jar','*.aar'])//add *.aar}Note:
```

#### Dynamically Downloading Assets, .so Libraries, and Dynamic Effect Resources Guide

To reduce the package size, you can change the download mode of the assets resources, .so libraries, and dynamic effect resources MotionRes (some basic SDKs do not have dynamic effect resources) required by the SDK to the online mode. After successful download, provide the paths of the above files to the SDK through setting.

You can use your existing download service, but we recommend you use the download logic of the demo. For detailed directions on implementing dynamic download, see [Reducing SDK Size](https://www.tencentcloud.com/document/product/1143/60206).

> **Note:****When integrating without Maven, the following dependencies must also be added**SDK Version >=4.1.0dependencies{    implementation 'com.google.code.gson:gson:2.8.5'    implementation 'com.tencent.tav:libpag:4.4.35-noffavc'}SDK Version >=4.0.0dependencies{    implementation 'com.google.code.gson:gson:2.8.5'    implementation 'com.tencent.tav:libpag:4.4.24-noffavc'}SDK Version >=3.9.2dependencies{    implementation 'com.google.code.gson:gson:2.8.2'    implementation 'com.tencent.tav:libpag:4.4.24-noffavc'}SDK Version >=3.5.0dependencies{    implementation 'com.google.code.gson:gson:2.8.2'    implementation 'com.tencent.tav:libpag:4.3.33-noffavc'}SDK Version >=3.2.0implementation 'com.google.code.gson:gson:2.8.2'dependencies{    implementation 'com.google.code.gson:gson:2.8.2'}SDK Version >=2.6.0dependencies{    implementation 'com.google.code.gson:gson:2.8.2'    implementation 'androidx.exifinterface:exifinterface:1.3.3'}If you want to use another version of pag, please click [FAQs](https://www.tencentcloud.com/document/product/1143/60312) to view.

## Integrate Effect Resources

If your package includes dynamic effect and filter features, you need to download the corresponding resources from the [SDK Download Page](https://trtc.io/sdkDownload?id=beauty) and place the dynamic effect and filter materials in the following directories under your project:

- Dynamic effect: `../assets/MotionRes`
- Filter: `../assets/lut`

For more resources configurations, refer to [Material Usage (Android)](https://www.tencentcloud.com/document/product/1143/73782).

## SDK Usage Steps

### Step 1: Authenticate

1. Apply for authorization to obtain the license URL and license key. Please refer to the [License Guide](https://www.tencentcloud.com/document/product/1143/69831).
2. Set the URL and key in the initialization code of the related business module to **trigger license download to avoid downloading temporarily before use**. For example, in our demo project, the download is triggered in the onCreate method of the application. However, we do not recommend triggering it here in your project because network permission might not be available or there could be a high rate of network failure at this time. Please choose a more appropriate time to trigger the license download.

```
//If you only want to trigger the download or update the license without caring about the authentication result, input null for the fourth parameter.TELicenseCheck.getInstance().setXMagicLicense(context, URL, KEY, null);
```

3. Perform authentication before actually using the beauty feature:

```
TELicenseCheck.getInstance().setTELicense(context, URL, KEY, new TELicenseCheckListener() {         @Override         public void onLicenseCheckFinish(int errorCode, String msg) {             //Note: This callback may not be on the calling thread.             if (errorCode == TELicenseCheck.ERROR_OK) {                 // Authentication succeeded.             } else {                 // Authentication failed.             }         }     });
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
| -11 | Failed to write TE authorization information to a local file, possibly due to I/O failure. |
| -12 | Download failed, and parsing local assets also failed. |
| -13 | Authentication failed. Please check if the .so file is in the package or if the .so path is set correctly. |
| 3004/3005 | Invalid authorization. Please contact the Tencent Cloud team to deal with it. |
| 3015 | Bundle ID/Package Name mismatch. Check if the Bundle ID/Package Name used by your app is consistent with the applied one, and ensure you are using the correct license file. |
| 3018 | The license file has expired. You need to apply for a renewal from Tencent Cloud. |
| Others | Please contact the Tencent Cloud team to deal with it. |

### Step 2: Copy resources

The resource files mentioned here consist of two parts:

- The SDK model files, located in the `assets` directory of the SDK's AAR package.
- Filter and dynamic effect resource files, located in the `assets` directory of the demo project, named `lut` and `MotionRes` respectively.

Before using the beauty effect, you need to copy the above resources to the app's private directory. If the SDK version is not updated, you only need to copy it once. After a successful copy, you can record it in the SharedPreference of the app, so that you do not need to copy it again next time. For details, refer to `TEMenuActivity.java` in the demo project.

```
String resPath = new File(getFilesDir(), AppConfig.getInstance().getBeautyFileDirName()).getAbsolutePath();if (!resPath.endsWith(File.separator)) {    resPath = resPath + File.separator;}AppConfig.resPathForSDK = resPath;AppConfig.lutFilterPath = resPath + "light_material/lut";AppConfig.motionResPath = resPath + "MotionRes";new Thread(() -> {    Context context = getApplicationContext();    int addResult = XmagicApi.addAiModeFilesFromAssets(context, AppConfig.resPathForSDK);    Log.d(TAG, "copyRes, add ai model files result = " + addResult);    String lutDirNameInAsset = "lut";    boolean result = FileUtil.copyAssets(context, lutDirNameInAsset, AppConfig.lutFilterPath);    Log.d(TAG, "copyRes, copy lut, result = " + result);    String motionResDirNameInAsset = "MotionRes";    boolean result2 = FileUtil.copyAssets(context, motionResDirNameInAsset, AppConfig.motionResPath);    Log.d(TAG, "copyRes, copy motion res, result = " + result2);}).start();
```

### Step 3: Initialize and use the SDK

1. (Optional) Quickly implement cameras.

We assume you have already implemented the camera application, can start the camera normally, and can call back the camera's SurfaceTexture texture information to Activity for beauty effect processing, as shown below:

```
@Overridepublic int onCustomProcessTexture(int textureId, int textureWidth, int textureHeight) {     // The beauty effect SDK processes the textureId here, adds beauty effects and special effects for it, and returns the processed new textureID.}
```

If you have not yet implemented the camera application, you can refer to `TECameraBaseActivity.java` in the demo project and use the `GLCameraXView` component to add it to your Activity's layout for quick camera preview:

```
<com.tencent.demo.camera.camerax.GLCameraXView       android:id="@+id/te_camera_layout_camerax_view"     android:layout_width="match_parent"      android:layout_height="match_parent"     app:back_camera="false"      app:surface_view="false"    app:transparent="true" />
```

2. Initialize the Beauty SDK on any thread, though it is recommended to do so on a subsidiary thread. **The creation should occur post successful License authentication.**

```
//AppConfig.resPathForSDK is the resource path determined during the resource copy stage.mXmagicApi = new XmagicApi(this, AppConfig.resPathForSDK);
```

**Parameter**

| Parameter | Meaning |
| --- | --- |
| Context context | Context |
| String resDir | Resource file directory. For details, refer to [Step 2](https://www.tencentcloud.com/document/product/1143/45385#.E6.AD.A5.E9.AA.A4.E4.BA.8C.EF.BC.9A.E8.B5.84.E6.BA.90.E6.8B.B7.E8.B4.9D) |
| OnXmagicPropertyErrorListener errorListener | Optional. Callback function implementation class, for handling some error codes during the SDK initialization and usage process. For the meanings of error codes, refer to [API Documentation](https://www.tencentcloud.com/document/product/1143/45399#xmagicapi) |

3. The beauty effect SDK processes each frame of data and returns the corresponding processing results. For detailed information on the process method, see the [API Documentation](https://www.tencentcloud.com/document/product/1143/45399#process).

```
@Overridepublic int onCustomProcessTexture(int textureId, int textureWidth, int textureHeight) {    return mXmagicApi.process(textureId, textureWidth, textureHeight);}
```

4. Set beauty effects or special effects.
  - Use the `setEffect` method for **version 3.5.0 and later**. For detailed information, see the [API Documentation](https://www.tencentcloud.com/document/product/1143/60201#32a345ed-73c4-4c60-bc7e-3f91b9a4755c).
  - Use the `updateProperty` method for **version 3.3.0 and earlier**. For detailed information, see the [API Documentation](https://www.tencentcloud.com/document/product/1143/45399#xmagicproperty).

```
//Use this method for version 3.5.0 and later.mXmagicApi.setEffect(String effectName, int effectValue, String resourcePath, Map<String, String> extraInfo)// For example, set the whitening property with intensity//mXmagicApi.setEffect(XmagicConstant.EffectName.BEAUTY_WHITEN, 50, null,null);// Available input parameter properties can be obtained from XmagicResParser.parseRes().// Use this method for version 3.3.0 and earlier.@DeprecatedmXmagicApi.updateProperty(XmagicProperty<?> p);
```

5. Lifecycle method `onResume`: It is recommended to call it in the `Activity`'s `onResume()` method. When called, it will resume the sound in the effects.

```
mXmagicApi.onResume();
```

6. Lifecycle method `onPause`: It is recommended to call it in the Activity's `onPause()` method. When called, it will pause the sound in the effects.

```
mXmagicApi.onPause();
```

7. Beauty effect release SDK: It is called when the OpenGL environment is being terminated. **It needs to be called in the GL thread, and cannot be called in the main thread (Activity's onDestroy);** otherwise, it may cause resource leaks and result in a white or black screen after multiple entries and exits.

```
@Overridepublic void onGLContextDestroy() {    mXmagicApi.onDestroy();}
```

### Step 4: Obfuscation configuration

- If you enable compile optimization (setting minifyEnabled to true) when packaging the release, it will trim some code that is not called in the Java layer. This code may possibly be invoked by the native layer, thus causing the ` no xxx method` exception.
- If you have enabled such compile optimization, you should add these keep rules to prevent xmagic's code from being trimmed:

```
-keep class com.tencent.xmagic.** { *;}-keep class org.light.** { *;}-keep class org.libpag.** { *;}-keep class org.extra.** { *;}-keep class com.gyailib.**{ *;}-keep class com.tencent.cloud.iai.lib.** { *;}-keep class com.tencent.beacon.** { *;}-keep class com.tencent.qimei.** { *;}-keep class androidx.exifinterface.** { *;}
```

### Attachment (SDK File Structure):

> **Note:**This table lists all the files used by the SDK. Some files may not be included in your package, but this will not affect the usage of that package's feature.

| File Type |  |  | Description |
| --- | --- | --- | --- |
| assets | audio2exp |  | Avatar virtual human voice-driven model: If this feature is not used, the model is not needed. |
|  | benchmark |  | Used for model adaptation. |
|  | Light3DPlugin |  | Used for 3D stickers. |
|  | LightBodyPlugin | LightBody3DModel.bundle | Used for 3D human skeleton points. |
|  |  | LightBodyModel.bundle | Used for the body beauty feature. |
|  | LightCore |  | SDK core model resources |
|  | LightHandPlugin |  | Required for gesture stickers and hand-point capabilities. |
|  | LightSegmentPlugin |  | Required for background segmentation capabilities. |
|  | lut |  | Free filter resources |
| demo_xxx_android_xxxx | - |  | Demo project |
| jniLibs | libace_zplan.so |  | 3D engine library |
|  | libaudio2exp.so |  | Avatar virtual human voice-driven library: If this feature is not used, the library is not needed. |
|  | libc++_shared.so |  | libc_shared.so is a shared library of the C standard library. It provides a set of C standard library functions and classes to support the development and operation of C programs. It is widely used in the Android system and is an essential part of C applications and libraries. If your project already includes a C shared library, you can keep only one copy. |
|  | liblight-sdk.so |  | Light SDK core library |
|  | libpag.so |  | Animation file library that the light SDK depends on |
|  | libtecodec.so |  | Codec library that the light SDK depends on |
|  | libv8jni.so |  | JavaScript parsing library that the light SDK depends on |
|  | libYTCommonXMagic.so |  | Used for license authentication |
| libs | xmagic-xxxx.aar |  | Beauty effect SDK .aar file |
| MotionRes | 2dMotionRes |  | 2D stickers |
|  | 3dMotionRes |  | 3D stickers |
|  | avatarRes |  | Avatar materials |
|  | ganMotionRes |  | Fun stickers |
|  | handMotionRes |  | Gesture stickers |
|  | makeupRes |  | Makeup stickers |
|  | segmentMotionRes |  | Background segmentation stickers |
| unity | aar |  | Bridging AAR required for the unity project |
|  | module |  | Original project for the bridging AAR |


---
*Source: [https://trtc.io/document/60195](https://trtc.io/document/60195)*
