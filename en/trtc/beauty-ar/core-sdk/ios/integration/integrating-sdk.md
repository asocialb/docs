# Integrating SDK

If you wish to quickly integrate and experience the features of BeautyAR, we recommend adopting the [Integrating UIKit](https://www.tencentcloud.com/document/product/1143/60194) approach.

For those integrating beauty effects alongside MLVB SDK /TRTC SDK /Short Video SDK(UGSV), please follow the integration guidelines for [Integrating With MLVB SDK](https://www.tencentcloud.com/document/product/1143/73774), [Integrating With TRTC SDK](https://www.tencentcloud.com/document/product/1143/73773) , and [Integrating With UGSV SDK](https://www.tencentcloud.com/document/product/1143/73775) respectively.

If you prefer not to use UIKit and instead directly implement Core SDK interface calls, you may proceed with this guide for integration.

## Comprehensive Integration Process

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fe87dcb0a8e311f0b5345254005ef0f7.png)

## Prerequisites

### Environment requirements

- Xcode 11 or later (download from App Store or [here](https://developer.apple.com/xcode/resources/))
- Recommended runtime environment:
  - Device requirements: iPhone 5 or later. iPhone 6 and older models support up to 720p for the front camera.
  - System requirements: iOS 10.0 or later.

### Importing the SDK

You can use CocoaPods or download and import the SDK manually into your project.

CocoaPods

Manual import

Dynamic download and integration

1. **Install CocoaPods.**

Enter the following command in a terminal (you need to install Ruby on your Mac first):

```
sudo gem install cocoapods
```

2. **Create a Podfile.**

Go to the directory of your project and enter the following command to create a Podfile in the directory.

```
pod init
```

3. **Edit the Podfile.**
  - XMagic version before 3.0.1:

Choose an edition for your project and edit the Podfile:

    - **XMagic Standard.**

Edit the Podfile as follows:

```
platform :ios, '9.0'target 'App' dopod 'XMagic'end
```

    - **XMagic Lite.**

The installation package of XMagic Lite is smaller than XMagic Standard. It supports only Basic A1- 00, Basic A1 - 01, and Advanced S1 - 00. Edit the Podfile as follows:

```
platform :ios, '9.0'target 'App' dopod 'XMagic_Smart'end
```

  - XMagic version 3.0.1 and later:

Choose the appropriate version based on your project package and edit the Podfile file:

```
#Please install the corresponding library with 'pod install' based on your package#For example: if your package is of type 'all', then you only need to use pod 'TencentEffect_All'.#For example: if your package is of type 'S1-04', then you only need to use pod 'TencentEffect_S1-04'.pod 'TencentEffect_All'#pod 'TencentEffect_A1-00'#pod 'TencentEffect_A1-01'#pod 'TencentEffect_A1-02'#pod 'TencentEffect_A1-03'#pod 'TencentEffect_A1-04'#pod 'TencentEffect_A1-05'#pod 'TencentEffect_A1-06'#pod 'TencentEffect_S1-00'#pod 'TencentEffect_S1-01'#pod 'TencentEffect_S1-02'#pod 'TencentEffect_S1-03'#pod 'TencentEffect_S1-04'#pod 'TencentEffect_S1-05'#pod 'TencentEffect_S1-06'#pod 'TencentEffect_S1-07'#pod 'TencentEffect_X1-01'#pod 'TencentEffect_X1-02'
```

4. **Update the local repository and install the SDK.**

Enter the following command in a terminal window to update the local repository and install the SDK:

```
pod install
```

5. Under the **Build Settings** tab, add `-ObjC` to **Other Linker Flags**.
6. Change the bundle ID to the bundle ID bound to your license.
1. Download the [SDK and effect resources](https://trtc.io/zh/sdkDownload?id=beauty) and decompress the file. The SDK is in the `frameworks` folder, and the bundle resources are in `resources`.
2. **If your SDK version is earlier than 2.5.1:**

Open your Xcode project and add the frameworks in the `frameworks` folder to your project: Choose the target to run, select the **General** tab, expand **Frameworks, Libraries, and Embedded Content**, and click **+** to add the frameworks downloaded, including `XMagic.framework`, `YTCommonXMagic.framework`, and `libpag.framework`, as well as `MetalPerformanceShaders.framework`, `CoreTelephony.framework`, `JavaScriptCore.framework`, `VideoToolbox.framework`, and `libc++.tbd`. You can also add `Masonry.framework` (control layout) and `SSZipArchive` (file decompression) if necessary.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa9633fc84ee11ed8467525400463ef7.png)

**If your SDK version is 2.5.1 or later:**

Open your Xcode project and add the frameworks in the `frameworks` folder to your project: Choose the target to run, select the **General** tab, expand **Frameworks, Libraries, and Embedded Content**, and click **+** to add the frameworks downloaded, including `XMagic.framework`, `YTCommonXMagic.framework`, `libpag.framework`, `Audio2Exp.framework`, and `TEFFmpeg.framework(Renamed to TECodec.framework after version 3.0.0.)`, as well as `MetalPerformanceShaders.framework`, `CoreTelephony.framework`, `JavaScriptCore.framework`, `VideoToolbox.framework`, and `libc++.tbd`. If necessary, you can also add `Masonry.framework` (control layout) and `SSZipArchive` (file decompression).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa9a2af784ee11eda151525400c56988.png)

3. Add the effect resources in the `resources` folder to your project.
4. Under the **Build Settings** tab, add `-ObjC` to **Other Linker Flags**.
5. Change the bundle ID to the bundle ID bound to your license.

To reduce the SDK package size, you can dynamically download the necessary module resources and animated effect resources (`MotionRes`, not available in some basic editions of the SDK) from a URL and, after download, pass the path of the resources to the SDK.

You can use your existing download service, but we recommend you use the download logic of the demo. For detailed directions on implementing dynamic download, see [Reducing SDK Size](https://www.tencentcloud.com/document/product/1143/60205).

## Importing the effect resources

If your package includes dynamic effect and filter features, you need to download the corresponding resources from the [SDK Download Page](https://trtc.io/zh/sdkDownload?id=beauty), After unzipping, import the bundles from the `resources/motionRes` folder into any directory of your main project as needed. After importing, it should look like the image below, where `lut.bundle` contains the filter resources and the others contain the animation resources.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0035f63bfdbb11f094325254001d6acc.png)

For more resources configurations, refer to [Material Usage (iOS)](https://www.tencentcloud.com/document/product/1143/73781).

### Configuring permissions

Add permission descriptions in the `Info.plist` file. If you donât do so, the application will crash on iOS 10. Grant the application camera access in **Privacy - Camera Usage Description**.

## Directions

### Step 1. Authenticate

1. Apply for a license and get the `LicenseURL` and `LicenseKEY`. See [Activate the Service](https://www.tencentcloud.com/document/product/1143/69831).
2. Set the URL and key in the initialization code of your business module to download the license. Avoid downloading it just before use. You can also trigger the download in the `didFinishLaunchingWithOptions` method of `AppDelegate` (the values of `LicenseURL` and `LicenseKey` are generated when you bound the license in the console).

If your SDK version is earlier than 2.5.1, you can find `TELicenseCheck.h` in `XMagic.framework`; if your SDK version is 2.5.1 or later, `TELicenseCheck.h` is in `YTCommonXMagic.framework`.The SDK can only be used after successful authentication.

```
[TELicenseCheck setTELicense:LicenseURL key:LicenseKey completion:^(NSInteger authresult, NSString * _Nonnull errorMsg) { if (authresult == TELicenseCheckOk) {     NSLog(@"Authentication successful"); } else {     NSLog(@"Authentication failed"); }}];
```

**Authentication error codes:**

| Error Codes | Description |
| --- | --- |
| 0 | Successful. |
| -1 | The input parameter is invalid; for example, the `URL` or `KEY` is empty. |
| -3 | Download failed. Check the network settings. |
| -4 | Unable to obtain any Tencent Effect authentication information from the local system, which may be caused by an I/O failure. |
| -5 | The VCUBE TEMP license file is empty, which may be caused by an I/O failure. |
| -6 | The JSON field in the `v_cube.license` file is incorrect. Please contact Tencent Cloud team for help. |
| -7 | Signature verification failed. Please contact Tencent Cloud team for help. |
| -8 | Decryption failed. Please contact Tencent Cloud team for help. |
| -9 | The JSON field in `TELicense` is incorrect. Please contact Tencent Cloud team for help. |
| -10 | The Tencent Effect authentication information parsed online is empty. Please contact Tencent Cloud team for help. |
| -11 | Failed to write Tencent Effect SDK authentication information to the local file, which may be caused by an I/O failure. |
| -12 | Download failed, and failed to parse local assets. |
| -13 | Authentication failed. |
| Others | Please contact Tencent Cloud team for help. |

### Step 2. Initialize and use the SDK

The following is the process of using the Tencent Effect SDK:

1. Load effect resources.

```
NSDictionary *assetsDict = @{@"core_name":@"LightCore.bundle", @"root_path":[[NSBundle mainBundle] bundlePath]  // The directory where LightCore.bundle is located.};
```

2. Initialize the Xmagic.

```
/**previewSize: View width and heightassetsDict: LightCore.bundle configured in the previous step and its path*/self.xMagicApi = [[XMagic alloc] initWithRenderSize:previewSize assetsDict:assetsDict];
```

3. The SDK processes each frame of data and returns the results.

```
/**Take the device camera data output as an example*///sampleBufferï¼Data output by the device camera-(CMSampleBufferRef)didProcessCPUData:(CMSampleBufferRef)sampleBuffer{    CVPixelBufferRef pixelBuffer = CMSampleBufferGetImageBuffer(sampleBuffer);    YTProcessInput *input = [[YTProcessInput alloc] init];    input.pixelData = [[YTImagePixelData alloc] init];    input.pixelData.data = pixelBuffer;    input.dataType = kYTImagePixelData;    YTProcessOutput *output = [self.xMagicKit process:input];    if (output.pixelData.data != nil) { //output.pixelData.dataï¼Data processed by Beauty Effeck SDK         CMSampleBufferRef outSampleBuffer = [self sampleBufferFromPixelBuffer:output.pixelData.data];        return outSampleBuffer;    }    return nil;}//PixelBuffer to sampleBuffer- (CMSampleBufferRef)sampleBufferFromPixelBuffer:(CVPixelBufferRef)pixelBuffer{    CFRetain(pixelBuffer);    CMSampleBufferRef outputSampleBuffer = NULL;    CMSampleTimingInfo timing = {kCMTimeInvalid, kCMTimeInvalid, kCMTimeInvalid};    CMVideoFormatDescriptionRef videoInfo = NULL;    OSStatus result = CMVideoFormatDescriptionCreateForImageBuffer(NULL, pixelBuffer, &videoInfo);    result = CMSampleBufferCreateForImageBuffer(kCFAllocatorDefault, pixelBuffer, true, NULL, NULL, videoInfo, &timing, &outputSampleBuffer);    CFArrayRef attachments = CMSampleBufferGetSampleAttachmentsArray(outputSampleBuffer, YES);    CFMutableDictionaryRef dict = (CFMutableDictionaryRef)CFArrayGetValueAtIndex(attachments, 0);    CFDictionarySetValue(dict, kCMSampleAttachmentKey_DisplayImmediately, kCFBooleanTrue);    CFRelease(videoInfo);    CFRelease(pixelBuffer);    return outputSampleBuffer;}
```

For more information about the beautification process and API details, see the [API documentation](https://www.tencentcloud.com/document/product/1143/60202#process).

4. Release the Xmagic .

```
// Called where SDK resources need to be released[self.xMagicApi deinit]
```

> **Note:**After completing the above steps, you can control the display timing and other device environment parameters as needed.


---
*Source: [https://trtc.io/document/60193](https://trtc.io/document/60193)*
