# Integrating With UGSV SDK

## Prerequisites

1. Download and decompress the [demo package](https://liteav.sdk.qcloud.com/download/latest/XiaoShiPin_UGC_iOS_latest.zip), and copy the `xmagickit` folder in the `demo/XiaoShiPin/` directory to the directory of the Podfile in your project.
2. Add the following dependencies to your `Podfile` and run `pod install`.

```
pod 'xmagickit', :path => 'xmagickit/xmagickit.podspec'
```

3. Set `Bundle ID` to the bundle ID bound to your license.

### Environment requirements

- Xcode 11 or later (download from App Store or [here](https://developer.apple.com/xcode/resources/))
- Recommended runtime environment:
  - Device requirements: iPhone 5 or later. iPhone 6 and older models support up to 720p for the front camera.
  - System requirements: iOS 12.0 or later.

## SDK API Integration

### Step 1. Authenticate

Add the following code to `didFinishLaunchingWithOptions` of `AppDelegate` (`LicenseURL` and `LicenseKey` are the authorization information you obtain from Tencent Cloud, see [Activate the Service](https://www.tencentcloud.com/document/product/1143/69831)). If your SDK version is earlier than 2.5.1, you can find `TELicenseCheck.h` in `XMagic.framework`; if your SDK version is 2.5.1 or later, `TELicenseCheck.h` is in `YTCommonXMagic.framework`.

```
[TXUGCBase setLicenceURL:LicenseURL key:LicenseKey];[TELicenseCheck setTELicense:LicenseURL key:LicenseKey completion:^(NSInteger authresult, NSString * _Nonnull errorMsg) {              if (authresult == TELicenseCheckOk) {                   NSLog(@"Authentication successful");               } else {                   NSLog(@"Authentication failed");               }       }];
```

**Authentication error codes:**

| Error Code | Description |
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

### Step 2. Set the SDK material path

```
CGSize previewSize = [self getPreviewSizeByResolution:self.currentPreviewResolution];NSString *beautyConfigPath = [NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES) lastObject];beautyConfigPath = [beautyConfigPath stringByAppendingPathComponent:@"beauty_config.json"];NSFileManager *localFileManager=[[NSFileManager alloc] init];BOOL isDir = YES;NSDictionary * beautyConfigJson = @{};if ([localFileManager fileExistsAtPath:beautyConfigPath isDirectory:&isDir] && !isDir) {    NSString *beautyConfigJsonStr = [NSString stringWithContentsOfFile:beautyConfigPath encoding:NSUTF8StringEncoding error:nil];    NSError *jsonError;    NSData *objectData = [beautyConfigJsonStr dataUsingEncoding:NSUTF8StringEncoding];    beautyConfigJson = [NSJSONSerialization JSONObjectWithData:objectData                                            options:NSJSONReadingMutableContainers                                            error:&jsonError];}NSDictionary *assetsDict = @{@"core_name":@"LightCore.bundle",                            @"root_path":[[NSBundle mainBundle] bundlePath],                            @"tnn_"                            @"beauty_config":beautyConfigJson};// Init beauty kitself.beautyKit = [[XMagic alloc] initWithRenderSize:previewSize assetsDict:assetsDict];
```

### Step 3. Add log and event listeners

```
// Register log[self.beautyKit registerSDKEventListener:self];[self.beautyKit registerLoggerListener:self withDefaultLevel:YT_SDK_ERROR_LEVEL];
```

### Step 4. Configure effects

```
- (int)configPropertyWithType:(NSString *_Nonnull)propertyType withName:(NSString *_Nonnull)propertyName withData:(NSString*_Nonnull)propertyValue withExtraInfo:(id _Nullable)extraInfo;
```

### Step 5. Render the video

In the preprocessing frame callback, construct `YTProcessInput` and pass `textureId` to the SDK for rendering.

```
 [self.xMagicKit process:inputCPU withOrigin:YtLightImageOriginTopLeft withOrientation:YtLightCameraRotation0]
```

### Step 6. Pause/Resume the SDK

```
[self.beautyKit onPause];[self.beautyKit onResume];
```

### Step 7. Add an effect panel to the layout

```
UIEdgeInsets gSafeInset;#if __IPHONE_11_0 && __IPHONE_OS_VERSION_MAX_ALLOWED >= __IPHONE_11_0if(gSafeInset.bottom > 0){}if (@available(iOS 11.0, *)) {    gSafeInset = [UIApplication sharedApplication].keyWindow.safeAreaInsets;} else#endif    {        gSafeInset = UIEdgeInsetsZero;    }dispatch_async(dispatch_get_main_queue(), ^{    // Effect option UI    _vBeauty = [[BeautyView alloc] init];    [self.view addSubview:_vBeauty];    [_vBeauty mas_makeConstraints:^(MASConstraintMaker *make) {        make.width.mas_equalTo(self.view);        make.centerX.mas_equalTo(self.view);        make.height.mas_equalTo(254);        if(gSafeInset.bottom > 0.0){  // Adapt to full-view screen            make.bottom.mas_equalTo(self.view.mas_bottom).mas_offset(0);        } else {            make.bottom.mas_equalTo(self.view.mas_bottom).mas_offset(-10);        }    }];        _vBeauty.hidden = YES;});
```


---
*Source: [https://trtc.io/document/73775](https://trtc.io/document/73775)*
