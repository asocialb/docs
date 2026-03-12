# Integrating With TRTC SDK

BeautyAR Flutter SDK requires dependence on the BeautyAR SDK of the Android/iOS end. Through the Plugins provided by Flutter, the native end features can be exposed to the Flutter client. Therefore, when integrating the beauty filter features, you need to manually integrate the SDK of the native end.

## Running Demo

[Download the demo project](https://github.com/Tencent-RTC/TencentEffect_Flutter), modify the `demo/lib` under the `main.dart` file, add your `licenseUrl` and `licenseKey` in this file. The sample code for using beauty features in TRTC is primarily located in `demo/lib/page/trtc_page.dart` and `demo/lib/main.dart`.

Android

iOS

1. In demo/app, find the build.gradle file, open the file, and change the value of `applicationId` to the package name you used when applying for the license.
2. In demo/lib, execute `flutter pub get`.
3. Use Android Studio to open the demo project and run it.
1. In the demo directory, execute `flutter pub get`.
2. In the demo/ios directory, execute `pod install`.
3. Use Xcode to open Runner.xcworkspace.
4. Change the project's `bundle ID` (it needs to be the same as the bundle ID you provided when applying for the license).

## SDK Integration

### Native Integration

Android

iOS

1. In the app module, find the build.gradle file and add the Maven repository URL for your corresponding package. For example, if you choose the S1-04 package, add the following:

```
dependencies {   implementation 'com.tencent.mediacloud:TencentEffect_S1-04:latest.release'}
```

**For the Maven URL corresponding to each package, please refer to the**[documentation](https://www.tencentcloud.com/document/product/1143/60195#e39cf4dd-0b61-47c1-92e8-710e762da797). The latest version number of the SDK can be found in the [Release Notes](https://www.tencentcloud.com/document/product/1143/60203).

2. In your project, find the `android/app` module and locate the `src/main/assets` folder. Copy the `demo/android/app/src/main/assetslut` and `MotionRes` folders from the demo project to your own project's `android/app/src/main/assets`. If your project doesn't have an assets folder, you can create one manually.
3. **If you are using an Android of the Tencent Effect SDK that is lower than 3.9**, you will need to locate the AndroidManifest.xml file under the app module, and add the following Tag in the application section:

```
   <uses-native-library            android:name="libOpenCL.so"            android:required="false" />        //true indicates that libOpenCL is essential for the current app. Without this library, the system will not allow the app to install        //false indicates that libOpenCL is not essential for the current app. The app can be installed normally with or without this library. If the device has this library, GAN-type special effects in the Tencent Special Effects SDK (e.g., fairy tale face, comics face) will function normally. If the device does not have this library, GAN-type effects won't work, but it will not affect the use of other features within the SDK.        //For information about uses-native-library, please refer to the Android official website: https://developer.android.com/guide/topics/manifest/uses-native-library-element
```

After adding, it looks as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f7d94bd2ac9f11ef9b4c525400bdab9d.png)

4. Obfuscation configuration
  - If you enable compile optimization (setting minifyEnabled to true) when packaging the release, it will trim some code that is not called in the Java layer. This code may possibly be invoked by the native layer, thus causing the ` no xxx method` exception.
  - If you enabled such compile optimization, you should add these keep rules to avoid trimming xmagic's code:

```
-keep class com.tencent.xmagic.** { *;}-keep class org.light.** { *;}-keep class org.libpag.** { *;}-keep class org.extra.** { *;}-keep class com.gyailib.**{ *;}-keep class com.tencent.cloud.iai.lib.** { *;}-keep class com.tencent.beacon.** { *;}-keep class com.tencent.qimei.** { *;}-keep class androidx.exifinterface.** { *;}-keep class com.tencent.effect.** { *;}
```

Copy the xmagic folder from the ios/Runner directory of the demo project to the ios/Runner directory of your project. After adding, it looks as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/857dd4e4a55a11ef888a52540075b605.png)

> **Note:**The materials copied from the demo project are **test materials**. Official materials need to be obtained from us by [contacting staff](https://www.tencentcloud.com/document/product/1143/51280) after purchasing a package, and then re-added. **Adding assets to an iOS project requires operations in Xcode**âmanually import them via `Add Files to "Runner"`and verify successful inclusion in `Build Phase â Copy Bundle Resources`.

### Flutter Integration

#### **Method 1**

Remote Dependencies, add the following reference in your project's pubspec.yaml file:

```
  tencent_effect_flutter:   git:     url: https://github.com/Tencent-RTC/TencentEffect_Flutter
```

#### **Method 2:**

Local Dependencies, download the latest version of [tencent_effect_flutter](https://github.com/Tencent-RTC/TencentEffect_Flutter), then add the folders android, ios, lib and the files pubspec.yaml, tencent_effect_flutter.iml to your project directory, and then add the following reference in your project's pubspec.yaml file: (refer to demo)

```
tencent_effect_flutter:    path: ../
```

Run the following command:

```
flutter pub get
```

> **Note:**tencent_effect_flutter only provides a bridging, the beauty feature relies on beauty SDKs provided by each platform, so if you need to update the beauty SDK, you can upgrade the SDK using the following steps:AndroidiOSFind the build.gradle file under the app module in your project, and change the `implementation 'com.tencent.mediacloud:TencentEffect_S1-04:latest.release'` field's `latest.release` to the latest version number.If you need to change the package, you need to modify the `TencentEffect_S1-04` field to your package field.**Need to change package type and SDK version:**The dependency for the Beauty Flutter SDK needs to be changed to a local dependency.Find the `ios/tencent_effect_flutter.podspec` file under the Beauty Flutter SDK, open it and change `TencentEffect_All` to the package you need, and you can also change the version number to the version you need.Execute the pod update command in the ios directory of your project.

## SDK usage

### 1. Associated with RTC

Associated with tencent_rtc_sdk

Associated with tencent_trtc_cloud

Android

iOS

Add the following code to the `onCreate` method of `FlutterActivity`:

Java

Kotlin

```
TRTCPlugin.setBeautyProcesserFactory(new XmagicProcesserFactory());
```

```
TRTCPlugin.setBeautyProcesserFactory(XmagicProcesserFactory())
```

As follows:

Java

Kotlin

```
import android.os.Bundle;import androidx.annotation.Nullable;import com.tencent.trtcplugin.TRTCPlugin;import com.tencent.effect.tencent_effect_flutter.XmagicProcesserFactory;import io.flutter.embedding.android.FlutterActivity;public class MainActivity extends FlutterActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        TRTCPlugin.setBeautyProcesserFactory(new XmagicProcesserFactory());    }}
```

```
import android.os.Bundleimport android.os.PersistableBundleimport com.tencent.trtcplugin.TRTCPluginimport io.flutter.embedding.android.FlutterActivityimport com.tencent.effect.tencent_effect_flutter.XmagicProcesserFactoryclass MainActivity: FlutterActivity() {    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        TRTCPlugin.setBeautyProcesserFactory(XmagicProcesserFactory())    }}
```

Add the following code snippet to the `didFinishLaunchingWithOptions` method within the AppDelegate file located in the ios/Runner directory:

Swift

Object-C

```
let instance = XmagicProcesserFactory()TencentRTCCloud.setBeautyProcesserFactory(factory: instance)
```

```
XmagicProcesserFactory *instance = [[XmagicProcesserFactory alloc] init];[TencentRTCCloud setBeautyProcesserFactoryWithFactory:instance];
```

As follows:

Swift

Object-C

```
import UIKitimport Flutterimport tencent_rtc_sdkimport tencent_effect_flutter@UIApplicationMain@objc class AppDelegate: FlutterAppDelegate {  override func application(    _ application: UIApplication,    didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?  ) -> Bool {    GeneratedPluginRegistrant.register(with: self)      let instance = XmagicProcesserFactory()      TencentRTCCloud.setBeautyProcesserFactory(factory: instance)    return super.application(application, didFinishLaunchingWithOptions: launchOptions)  }}
```

```
#import "AppDelegate.h"#import "GeneratedPluginRegistrant.h"@import tencent_effect_flutter;@import tencent_rtc_sdk;@implementation AppDelegate- (BOOL)application:(UIApplication *)application    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {     [GeneratedPluginRegistrant registerWithRegistry:self];     XmagicProcesserFactory *instance = [[XmagicProcesserFactory alloc] init];     [TencentRTCCloud setBeautyProcesserFactoryWithFactory:instance];  return [super application:application didFinishLaunchingWithOptions:launchOptions];}@end
```

Android

iOS

In the onCreate method of the application class (or the onCreate method of FlutterActivity), add the following code:

```
import android.os.Bundle;import androidx.annotation.Nullable;import com.tencent.effect.tencent_effect_flutter.XmagicProcesserFactory;import io.flutter.embedding.android.FlutterActivity;import com.tencent.trtcplugin.TRTCCloudPlugin;public class MainActivity extends FlutterActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        TRTCCloudPlugin.register(new XmagicProcesserFactory());    }}
```

Add the following code within the didFinishLaunchingWithOptions method of your application's AppDelegate class:

```
#import "AppDelegate.h"#import "GeneratedPluginRegistrant.h"@import tencent_effect_flutter;@import tencent_trtc_cloud;@implementation AppDelegate- (BOOL)application:(UIApplication *)application    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {    [GeneratedPluginRegistrant registerWithRegistry:self];    XmagicProcesserFactory *instance = [[XmagicProcesserFactory alloc] init];    [TencentTRTCCloud registerWithCustomBeautyProcesserFactory:instance];  return [super application:application didFinishLaunchingWithOptions:launchOptions];}@end
```

### 2. Call the resource initialization API

v0.3.5.0 and later

Before v0.3.1.1

```
void _initSettings(InitXmagicCallBack callBack) async {  String resourceDir = await ResPathManager.getResManager().getResPath();  TXLog.printlog('$TAG method is _initResource ,xmagic resource dir is $resourceDir');  TencentEffectApi.getApi()?.setResourcePath(resourceDir);  /// Resource copying only needs to be done once. In the current version, if copied successfully once, there is no need to copy the resources again.  /// Copying the resource only needs to be done once. Once it has been successfully copied in the current version, there is no need to copy it again in future versions.  if (await isCopiedRes()) {    callBack.call(true);    return;  } else {    _copyRes(callBack);  }}void _copyRes(InitXmagicCallBack callBack) {  _showDialog(context);  TencentEffectApi.getApi()?.initXmagic((result) {    if (result) {      saveResCopied();    }    _dismissDialog(context);    callBack.call(result);    if (!result) {      Fluttertoast.showToast(msg: "initialization failed");    }  });}
```

```
String dir =  await BeautyDataManager.getInstance().getResDir(); TXLog.printlog('The file path: $dir'); TencentEffectApi.getApi()?.initXmagic(dir,(reslut) {     _isInitResource = reslut;     callBack.call(reslut);     if (!reslut) {         Fluttertoast.showToast(msg: "Failed to initialize the resources");     } });
```

### 3. Perform beauty authorization

```
TencentEffectApi.getApi()?.setLicense(licenseKey, licenseUrl,           (errorCode, msg) {         TXLog.printlog("Print the authentication result errorCode = $errorCode   msg = $msg");         if (errorCode == 0) {            // Authentication succeeded         }       });
```

### 4. Enable/Disable Beauty Filter

> **Note:**The beautification feature must be enabled after the camera is activated and disabled before the camera is turned off. Enabling and disabling the feature should always be used in pairs.

tencent_rtc_sdk

tencent_trtc_cloud

```
///Enable beauty mode/// Set to true to enable beauty mode, set to false to disable beauty mode_enableCustomBeautyByNative(bool open) {  TRTCCloud trtcCloud = await TRTCCloud.sharedInstance();  trtcCloud.callExperimentalAPI("{\\"api\\": \\"enableVideoProcessByNative\\", \\"params\\": {\\"enable\\": $open}}");}
```

```
///Enable beauty mode/// Set to true to enable beauty mode, set to false to disable beauty mode var enableCustomVideo = await trtcCloud.enableCustomVideoProcess(open);
```

### 5. Set Beauty Attributes

v0.3.5.0 and later

Before v0.3.1.1

For specific beauty attributes, refer to [Beauty Attributes Table](https://www.tencentcloud.com/document/product/1143/58946).

```
TencentEffectApi.getApi()?.setEffect(sdkParam.effectName!,    sdkParam.effectValue, sdkParam.resourcePath, sdkParam.extraInfo)
```

```
TencentEffectApi.getApi()?.updateProperty(_xmagicProperty!);/// You can call `BeautyDataManager.getInstance().getAllPannelData()` to get all the properties and call `updateProperty` to set properties.
```

### 6. Set other properties

- **Pause Beauty Sound Effects**

```
 TencentEffectApi.getApi()?.onPause();
```

- **Resume Beauty Sound Effects**

```
TencentEffectApi.getApi()?.onResume();
```

- **Monitor Beauty Events**

```
TencentEffectApi.getApi()     ?.setOnCreateXmagicApiErrorListener((errorMsg, code) {       TXLog.printlog("Error creating an effect object errorMsg = $errorMsg , code = $code"); });   /// Needs to be set before creating the beauty filter
```

- **Set Callback for Face, Gesture, and Body Detection Status**

```
TencentEffectApi.getApi()?.setAIDataListener(XmagicAIDataListenerImp());
```

- **Set Callback Function for Dynamic Prompt Messages**

```
TencentEffectApi.getApi()?.setTipsListener(XmagicTipsListenerImp());
```

- **Configure the Callback of Facial Keypoints and Other Data (only available in S1-05 and S1-06)**

```
TencentEffectApi.getApi()?.setYTDataListener((data) {   TXLog.printlog("setYTDataListener  $data"); });
```

- **Remove All Callbacks**

You need to remove all callbacks when terminating the page:

```
 TencentEffectApi.getApi()?.setOnCreateXmagicApiErrorListener(null); TencentEffectApi.getApi()?.setAIDataListener(null); TencentEffectApi.getApi()?.setYTDataListener(null); TencentEffectApi.getApi()?.setTipsListener(null);
```

> **Note**For more information on the APIs, see [API Documentation](https://www.tencentcloud.com/document/product/1143/60200). For others, refer to the [Demo Project](https://github.com/Tencent-RTC/TencentEffect_Flutter).

### 7. Add Data to and Remove Data from the Effect Panel

#### **Add effect resources**:

Add your resource file to the corresponding folder as described in step 1. For example, to add a 2D animated effect resource:

Android

iOS

You should put the resource in `android/xmagic/src.main/assets/MotionRes/2dMotionRes` of your project:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/85959747a55a11efadbf525400fdb830.png)

Also add the resource to `ios/Runner/xmagic/2dMotionRes.bundle` of your project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/859368cca55a11ef9021525400f69702.png)

#### Beauty Panel Configuration:

V0.3.5.0 and later

V0.3.1.1 and earlier

The demo provides a simple beauty panel UI. The panel's properties are configured through JSON files([JSON Files](https://www.tencentcloud.com/document/product/1143/60196#c3effdcb-00ed-4641-ad95-6fbeda7476d0)), located as shown in the following diagram. The implementation of the panel can be referred from the demo project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/85840d50a55a11ef9b7a525400d5f8ef.png)

In the classes BeautyDataManager, BeautyPropertyProducer, BeautyPropertyProducerAndroid, and BeautyPropertyProducerIOS, you can independently configure the beauty panel data.

#### **Delete Beauty Resources**

For some licenses that do not authorize certain beauty and body shaping features, these features should not be displayed on the beauty panel. You need to remove these features from the beauty panel data configuration.

For example, to delete the Lipstick Effect, remove the following code from the getBeautyData method in both the BeautyPropertyProducerAndroid and BeautyPropertyProducerIOS classes.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/85a223fba55a11ef9b7a525400d5f8ef.png)


---
*Source: [https://trtc.io/document/73778](https://trtc.io/document/73778)*
