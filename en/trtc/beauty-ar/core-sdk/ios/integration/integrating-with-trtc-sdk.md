# Integrating With TRTC SDK

This documentation explains integrating and using the TEBeautyKit library in the TRTC SDK project**.**

Refer to [TRTC_Adapter_Example](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/iOS/latest/TRTC-API-Example.zip).

## Integration Steps

1. (Optional) Integrate [TRTCAdapter](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/iOS/latest/TRTCAdapter.framework.zip). The TRTCAdapter.framework is used to receive video callbacks from the TRTC SDK, process them internally using the beauty filter SDK, and then return them to the TRTC SDK. If you need to perform custom processing on the video stream, you can skip this step.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c845f7cffdc011f0905652540097cba1.png)

2. Integration [TEBeautyKit](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/iOS/TEBeautyKit/latest/TEBeautyKit.zip)ï¼Edit the Podfile and append the following code snippet and execution `pod ``install`.

```
# Replace S1-07 with the package you purchasedpod 'TEBeautyKit/S1-07', :podspec => 'https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/iOS/TEBeautyKit/latest/TEBeautyKit.podspec'
```

3. Integration [Panel Resources](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/Android/beauty_panel_json/beauty_panel_latest.zip)ï¼download the resource package and incorporate it into your main project. The contents can be found in the [appendix](https://www.tencentcloud.com/document/product/1143/60194#c3effdcb-00ed-4641-ad95-6fbeda7476d0).
4. Integration [Effect Resources](https://www.tencentcloud.com/document/product/1143/60193#b5698a64-4751-4eea-9bf5-0c833697e5b4).

## Usage Guide

### Step 1. Authenticate

After the application is launched, a beauty filter authentication must be performed to enable the normal use of beauty features. See the [authentication error code](https://www.tencentcloud.com/document/product/1143/60193#.E6.AD.A5.E9.AA.A4.E4.B8.80.EF.BC.9A.E9.89.B4.E6.9D.83)

```
[TEBeautyKit setTELicense:@"your license" key:@"your key" completion:^(NSInteger authresult, NSString * _Nullable errorMsg) {  NSLog(@"----------result: %zd  %@",authresult,errorMsg);}];
```

### Step 2. Configuration Panel Resource Path

The beauty data and icon assets on the beauty panel are available in [beauty_panel.zip](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/Android/beauty_panel_json/beauty_panel_latest.zip). As per the API documentation, you may pass the corresponding JSON file path and customize the settings according to your specific requirements.

```
- (void)configPanel {    NSBundle *bundle = [NSBundle mainBundle];    NSString *beautyJsonPath = [bundle pathForResource:@"beauty" ofType:@"json"]; //Beauty    NSString *lutJsonPath = [bundle pathForResource:@"lut" ofType:@"json"]; //filter    NSString *motion2dJsonPath = [bundle pathForResource:@"motion_2d" ofType:@"json"]; //2D stickers    NSMutableArray *resArray = [[NSMutableArray alloc] init];    [resArray addObject:@{TEUI_BEAUTY : beautyJsonPath}];    [resArray addObject:@{TEUI_LUT : lutJsonPath}];    [resArray addObject:@{TEUI_MOTION_2D : motion2dJsonPath}];    /// Set up resources    [[TEUIConfig shareInstance] setTEPanelViewResources:resArray];}
```

### Step 3. Initialize and incorporate TEPanelView

TEPanelView is a custom panel view used to display the data configured in Step 2.

```
- (void)addPanelView {    TEPanelView *tePanelView = [[TEPanelView alloc] init];    tePanelView.delegate = self;    [self.view addSubview:tePanelView];    [tePanelView mas_makeConstraints:^(MASConstraintMaker *make) {        make.width.bottom.mas_equalTo(self.view);        make.left.right.mas_equalTo(self.view);        make.height.mas_equalTo(230 + self.view.safeAreaInsets.bottom);    }];}
```

If TRTCAdapter is not integrated, please refer directly to [step 7](#98c89154-351f-4e49-9786-3c1b681cf7a2).

### Step 4: Adapter Binding for Beautification

```
/// create adapter- (TEBeautyTRTCAdapter *)trtcAdapter {    if (!_trtcAdapter) {        _trtcAdapter = [[TEBeautyTRTCAdapter alloc] init];    }    return  _trtcAdapter;}/// bind__weak __typeof(self)weakSelf = self;[self.trtcAdapter bind:self.trtcCloud onCreatedXmaicApi:^(XMagic * _Nullable xmagicApi) {   __strong typeof(self) strongSelf = weakSelf;   strongSelf.teBeautyKit.xmagicApi = xmagicApi;   [strongSelf.teBeautyKit setLogLevel:YT_SDK_ERROR_LEVEL];   strongSelf.tePanelView.teBeautyKit = strongSelf.teBeautyKit;   [strongSelf.tePanelView setDefaultBeauty]; } onDestroyXmaicApi:^{    __strong typeof(self) strongSelf = weakSelf;    [strongSelf.teBeautyKit onDestroy];    strongSelf.teBeautyKit = nil; }];
```

### Step 5: Parameter Change Notification Adapter

```
/// Notify the Adapter of the Front and Rear Cameras: Whether to Encode a Mirror Image[self.trtcAdapter notifyCameraChanged:self.isFrontCamera isEncoderMirror:self.isEncoderMirror];/// Notify the Adapter of Screen Orientation Changes[self.trtcAdapter setDeviceOrientation:currOrientation];
```

### Step 6: Unlink the adapter and terminate the beauty enhancement feature

```
 [self.trtcAdapter unbind]; self.trtcAdapter = nil;
```

### Step 7: TRTCAdapter is not integrated.

Listen for TRTC video callbacks, process the beauty effects within the callback, and then return the processed video to TRTC.

1. Initialization

```
- (void)initXMagic {    __weak __typeof(self)weakSelf = self;    [TEBeautyKit createXMagic:EFFECT_MODE_PRO onInitListener:^(TEBeautyKit * _Nullable beautyKit) {        __strong typeof(self)strongSelf = weakSelf;        strongSelf.teBeautyKit = beautyKit;        strongSelf.tePanelView.teBeautyKit = strongSelf.teBeautyKit;        [strongSelf.tePanelView setDefaultBeauty];        [strongSelf.teBeautyKit setLogLevel:YT_SDK_ERROR_LEVEL];        [strongSelf.teBeautyKit registerSDKEventListener:strongSelf];    }];}
```

2. Processing video data

```
- (uint32_t)onProcessVideoFrame:(TRTCVideoFrame *)srcFrame dstFrame:(TRTCVideoFrame *)dstFrame {    YTProcessOutput *output = [self.teBeautyKit processTexture:srcFrame.textureId                                                  textureWidth:srcFrame.width                                                 textureHeight:srcFrame.height                                                    withOrigin:YtLightImageOriginTopLeft                                               withOrientation:YtLightCameraRotation0];    dstFrame.textureId = output.textureData.texture;    return 0;}
```

3. Destroy Beauty Filter

```
- (void)destroyXMagic {   [self.teBeautyKit onDestroy];   self.teBeautyKit = nil;}
```


---
*Source: [https://trtc.io/document/73773](https://trtc.io/document/73773)*
