# Integrating TEBeautyKit

## Features

TEBeautyKit is the UI panel library for the Tencent Effect module, used for quick and convenient usage and management of the effect features. The effect is as shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f2d280f9fdbe11f094325254001d6acc.png)

## Integration Steps

1. Integration [TEBeautyKit](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/iOS/TEBeautyKit/latest/TEBeautyKit.zip)ï¼Edit the Podfile and append the following code snippet and execution `pod ``install`.

```
# Replace S1-07 with the package you purchasedpod 'TEBeautyKit/S1-07', :podspec => 'https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/iOS/TEBeautyKit/latest/TEBeautyKit.podspec'
```

2. Integration [Panel Resources](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/Android/beauty_panel_json/beauty_panel_latest.zip), download the resource package and incorporate it into your main project. The contents can be found in the [appendix](#c3effdcb-00ed-4641-ad95-6fbeda7476d0).
3. Integration [Effect Resources](https://www.tencentcloud.com/document/product/1143/60193#b5698a64-4751-4eea-9bf5-0c833697e5b4).

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

### Step 4. Initialize the beauty filter object

1. Initialization

```
- (void)initXMagic {    __weak __typeof(self)weakSelf = self;    [TEBeautyKit createXMagic:EFFECT_MODE_PRO onInitListener:^(TEBeautyKit * _Nullable beautyKit) {        __strong typeof(self)strongSelf = weakSelf;        strongSelf.teBeautyKit = beautyKit;        strongSelf.tePanelView.teBeautyKit = strongSelf.teBeautyKit;        [strongSelf.tePanelView setDefaultBeauty];        [strongSelf.teBeautyKit setLogLevel:YT_SDK_ERROR_LEVEL];        [strongSelf.teBeautyKit registerSDKEventListener:strongSelf];    }];}
```

2. Processing video data

```
#pragma mark AVCaptureVideoDataOutputSampleBufferDelegate- (void)captureOutput:(AVCaptureOutput *)captureOutput didOutputSampleBuffer:(CMSampleBufferRef)sampleBuffer fromConnection:(AVCaptureConnection *)connection {    if (captureOutput == self.videoDataOutput) {        [self mycaptureOutput:captureOutput didOutputSampleBuffer:sampleBuffer fromConnection:connection originImageProcess:YES];    }}- (void)mycaptureOutput:(AVCaptureOutput *)captureOutput didOutputSampleBuffer:(CMSampleBufferRef)inputSampleBuffer fromConnection:(AVCaptureConnection *)connection originImageProcess:(BOOL)originImageProcess {    CVPixelBufferRef pixelBuffer = CMSampleBufferGetImageBuffer(inputSampleBuffer);    YTProcessOutput *output = [self.teBeautyKit processPixelData:pixelBuffer                                                  pixelDataWidth:(int)CVPixelBufferGetWidth(pixelBuffer)                                                 pixelDataHeight:(int)CVPixelBufferGetHeight(pixelBuffer)                                                      withOrigin:YtLightImageOriginTopLeft                                                 withOrientation:YtLightCameraRotation0];    if (output.pixelData.data != nil) {        /// Output video data, render or other processing    }    if (output != nil) {        output.pixelData = nil;        output = nil;    }}
```

3. Destroy Beauty Filter

```
- (void)destroyXMagic {   [self.teBeautyKit onDestroy];   self.teBeautyKit = nil;}
```

## Appendix

### Panel JSON File Description

- **JSON Description**

| **Documentation** | **Explanation** |
| --- | --- |
| beauty.json | Beauty Configuration File |
| beauty_body.json | Beauty Profile Configuration |
| beauty_image.json | Image Quality Adjustment Configuration File |
| beauty_makeup.json | Single-point Makeup Configuration File |
| beauty_shape.json | Premium Styling Configuration File |
| beauty_template_ios.json | Beauty Filter Template Configuration File |
| light_makeup.json | Light Makeup Configuration File |
| lut.json | Filter configuration file. Note: Since different clients utilize distinct filter assets, customers may customize the configuration according to the JSON structure after downloading. |
| makeup.json | Style Makeup Configuration File.  Note: Since different clients utilize distinct style makeup materials, customers may customize the configuration according to the JSON structure after downloading. |
| motion_2d.json | 2D Animation Sticker Configuration File. Note: Since different clients may utilize varying animation sticker materials, after downloading, clients can customize the configuration according to the JSON structure. |
| motion_3d.json | 3D animated sticker configuration file. Note: Since different clients may utilize varying animated sticker materials, customers can customize the configuration according to the JSON structure after downloading. |
| motion_gesture.json | Gesture animation sticker configuration file. Note: Since different clients may use varying animation sticker materials, customers can customize the configuration according to the JSON structure after downloading. |
| segmentation.json | Background Segmentation (Virtual Background) Configuration File. Note: As different clients utilize distinct segmentation materials, customers may customize the configuration according to the JSON structure after downloading. |
| panel_icon | This directory is designated for storing images configured in JSON files, which must be added. |

- **Beauty, Body Shaping.**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f2a2ea4ffdbe11f0a616525400a31896.png)

| Field | Description |
| --- | --- |
| displayName | Chinese Name |
| displayNameEn | English Name |
| icon | Image address, supports setting local images and network images. Local images support assets resources and SD resources. Assets images are as shown in the image above. For SD card images, set the full path of the image. For network images, set the corresponding HTTP link. |
| sdkParam | The effect SDK requires four properties. Refer to the [Effect Parameters table](https://www.tencentcloud.com/document/product/1143/58946) |
| effectName | Effect attribute key, refer to the [Effect Parameters table](https://www.tencentcloud.com/document/product/1143/58946) |
| effectValue | Setting the attribute intensity, refer to the [Effect Parameters table](https://www.tencentcloud.com/document/product/1143/58946) |
| resourcePath | Setting the resource path, refer to the [Effect Parameters table](https://www.tencentcloud.com/document/product/1143/58946) |
| extraInfo | Setting other information, refer to the [Effect Parameters table](https://www.tencentcloud.com/document/product/1143/58946) |

- **Filters, Animated Stickers and Segmentation.**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f2ca67c3fdbe11f08080525400074c32.png)

Since the configuration of **Filters, Animated Stickers and Segmentation** is primarily identical, the JSON for filters is used here for illustration. The fields downloadPath and resourceUri are added here.

| Field | Description |
| --- | --- |
| downloadPath | If your filter material is downloaded from the network, then the configuration here is the location of your material stored locally after download, which is a **relative path**, and the full path is set in `TEDownloader.h` using `basicPath`**+the path set here** |
| resourceUri | If your material needs to be downloaded via network, configure the network address here, as in the third red box in the image above. However, if your filter material is local, configure the corresponding local address according to the figure above. |

- **Makeup**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f2cb2e30fdbe11f08e41525400ecee81.png)

In the Makeup, the `makeupLutStrength` field is added under `extraInfo`. This field is used to adjust the strength of the filter in the makeup material (if this makeup material supports adjusting the filter strength, configure it accordingly). This field can be referenced in the Effect Parameters table.

### TEBeautyKit Method Descriptions

```
/// Create TEBeautyKit object/// - Parameters:/// - effectMode: EFFECT_MODE_NORMAL (high-performance mode) EFFECT_MODE_PRO (default mode)/// When high-performance mode is enabled, the beauty effect uses less system CPU/GPU resources, which can reduce phone heating and lag, making it more suitable for long-term use on low-end devices./// Note: After enabling high-performance mode, the following beauty features will be unavailable:/// 1. Eyes: Eye width, eye height, remove eye bags/// 2. Eyebrows: Angle, distance, height, length, thickness, arch/// 3. Mouth: Smile lips/// 4. Face: Face slimming (natural, goddess, handsome), jawline reduction, wrinkle removal, nasolabial folds removal. It is recommended to use 'Face Shape' to achieve a comprehensive effect of larger eyes and face slimming/// - onInitListener: Callback+ (void)createXMagic:(EffectMode)effectMode onInitListener:(OnInitListener _Nullable)onInitListener;/// Beauty Filter Authentication+ (void)setTELicense:(NSString *)url key:(NSString *)key completion:(callback _Nullable )completion;/// Set beauty mode target- (void)setXMagicApi:(XMagic *_Nullable)xmagicApi;/// Beauty mute- (void)setMute:(BOOL)isMute;/// Set a feature on or off/// @param featureName Values can be found in XmagicConstant.FeatureName/// @param enable true for on, false for off- (void)setFeatureEnableDisable:(NSString *_Nullable)featureName enable:(BOOL)enable;/// Set frame synchronization mode/// @isSync Whether it is synchronous/// @syncFrameCount Number of frames to synchronize. -1 means unlimited. This parameter is meaningless if isSync is false- (void)setSyncMode:(BOOL)isSync syncFrameCount:(int)syncFrameCount;/// Process image beautification- (UIImage *_Nullable)processUIImage:(UIImage *_Nullable)inputImage                 imageWidth:(int)imageWidth                imageHeight:(int)imageHeight                  needReset:(bool)needReset;/// Handle texture/// - Parameters:///   - textureId: Texture ID///   - textureWidth: Texture width///   - textureHeight: Texture height///   - origin: Enum value, when set to YtLightImageOriginBottomLeft, the image is flipped vertically///   - orientation: Enum value: image rotation angle- (YTProcessOutput *_Nullable)processTexture:(int)textureId         textureWidth:(int)textureWidth        textureHeight:(int)textureHeight           withOrigin:(YtLightImageOrigin)origin      withOrientation:(YtLightDeviceCameraOrientation)orientation;      /// Handling CVPixelBufferRef/// - Parameters:/// - pixelData: Image data/// - pixelDataWidth: Image width/// - pixelDataHeight: Image height/// - origin: Enum value, when set to YtLightImageOriginBottomLeft, the image is flipped vertically/// - orientation: Enum value: Image rotation angle- (YTProcessOutput * _Nullable)processPixelData:(CVPixelBufferRef _Nullable )pixelData                      pixelDataWidth:(int)pixelDataWidth                     pixelDataHeight:(int)pixelDataHeight                          withOrigin:(YtLightImageOrigin)origin                     withOrientation:(YtLightDeviceCameraOrientation)orientation;/// Set beauty- (void)setEffect:(TESDKParam *_Nullable)sdkParam;///  Set beauty- (void)setEffectList:(NSArray<TESDKParam *>*_Nullable)sdkParamList;/// Is the beauty enhancement mode turned on- (BOOL)isEnableEnhancedMode;/// Enable beauty enhancement mode- (void)enableEnhancedMode:(BOOL)enable;/// Recover- (void)onResume;/// Pause- (void)onPause;/// Destroy- (void)onDestroy;//Get the current texture image- (void)exportCurrentTexture:(void (^_Nullable)(UIImage * _Nullable image))callback;/// Set log- (void)setLogLevel:(YtSDKLoggerLevel)level;/// Set AIDataListener- (void)setAIDataListener:(id<TEBeautyKitAIDataListener> _Nullable)listener;/// Set TipsListener- (void)setTipsListener:(id<TEBeautyKitTipsListener> _Nullable)listener;/// Save the beauty settings data- (void)saveEffectParam:(TESDKParam *_Nonnull)sdkParam;/// Delete a saved beauty data- (void)deleteEffectParam:(TESDKParam *_Nonnull)sdkParam;/// Clear saved beauty data- (void)clearEffectParam;/// Retrieve saved beauty data- (NSMutableArray<TESDKParam *> *_Nonnull)getInUseSDKParamList;/// Export the beauty data currently in use/// return json string- (NSString *_Nullable)exportInUseSDKParam;/// Set beauty data/// - Parameter params: JSON string/// If you also want to set the panel UI, you only need to call TEPanelView's setExportParamList- (void)setExportedSDKParam:(NSString *_Nonnull)params;/// Enable beauty mode?- (void)enableBeauty:(BOOL)enable;/// SDK event listener interface/// @param listener Event listener callback, mainly divided into AI events, Tips reminder events, and Asset events- (void)registerSDKEventListener:(id<YTSDKEventListener> _Nullable)listener;/// Register callback cleanup interface- (void)clearListeners;
```

### TEUIConfig Descriptions

```
///The colour of the following properties can be modified externally/// Beauty panel background colour@property (nonatomic, strong) UIColor *panelBackgroundColor;/// Divider colour@property (nonatomic, strong) UIColor *panelDividerColor;/// Selected item colour@property (nonatomic, strong) UIColor *panelItemCheckedColor;/// Text colour@property (nonatomic, strong) UIColor *textColor;/// Text selection colour@property (nonatomic, strong) UIColor *textCheckedColor;/// Progress bar colour@property (nonatomic, strong) UIColor *seekBarProgressColor;/// Singleton+ (instancetype)shareInstance;/// Set panel resource path/// - Parameter resources: List of resource paths/// e.g. @[@{TEUI_BEAUTY : @"json file path"}]- (void)setTEPanelViewResources:(NSArray<NSDictionary *> *)resources;/// Get panel resource path- (NSArray<NSDictionary *> *)getTEPanelViewResources;
```

### TEPanelView Description

```
/// Beauty SDK object@property (nonatomic, weak) XMagic *beautyKitApi;/// BeautyKit object@property (nonatomic, strong) TEBeautyKit *teBeautyKit;/// Delegate@property (nonatomic, weak) id<TEPanelViewDelegate> delegate;/// Set exported beauty data- (void)setExportParamList:(NSString *)lastParamList;/// Default beauty- (void)setDefaultBeauty;/// Reset all effects- (void)performFullReset;/// Enhanced mode- (void)setEnhancedMode:(BOOL)enhancedMode;/// Show compare button- (void)isShowCompareBtn:(BOOL)isShow;
```


---
*Source: [https://trtc.io/document/60194](https://trtc.io/document/60194)*
