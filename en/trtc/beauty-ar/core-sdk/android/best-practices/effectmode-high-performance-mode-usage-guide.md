# EffectMode (High-Performance Mode) Usage Guide

## EffectMode

Starting from SDK V3.9.0, when creating an SDK, you must specify EffectMode, which has two values: EffectMode_Normal and EffectMode_Pro.

- EffectMode_Normal is equivalent to the "High Performance Mode" of the older SDK version.
- EffectMode_Pro is equivalent to the default mode of the old SDK version.

The differences between the two are as follows:

## High performance mode

- "High performance mode" was a concept before SDK V3.9.0. At that time, the SDK had two modes: high performance mode and default mode.
- From V3.9.0 onwards, high performance mode became EffectMode_Normal and default mode became EffectMode_Pro.
- For the differences between high performance mode and default mode, please refer to the differences between EffectMode_Normal and EffectMode_Pro mentioned above.

## **How to set EffectMode in V3.9.0 and later versions**

Android

iOS

Flutter

uniapp

**Method 1**

If you are directly using the `XmagicApi` object, then **please specify EffectMode when creating** the `XmagicApi` **object in the constructor method**:

```
public XmagicApi(Context context, EffectMode effectMode, String resDir)public XmagicApi(Context context, EffectMode effectMode, String resDir, OnXmagicPropertyErrorListener xmagicPropertyErrorListener)
```

**Method 2**

If you are using the TEBeautyKit object, you can call the following method to enable high performance mode.

```
public TEBeautyKit(Context context, EffectMode effectMode)public static void create(@NonNull Context context, EffectMode effectMode, @NonNull OnInitListener initListener)
```

The EffectMode is defined as follows:

```
public enum EffectMode{    NORMAL(0),    PRO(1);        private final int value;        EffectMode(int value) {        this.value = value;    }        public int getValue() {        return value;    }}
```

**Method 1**

If you are directly using the `XMagic` object, then you need to specify EffectMode when initializing `XMagic`, as shown in the following code:

```
NSDictionary *assetsDict = @{@"core_name":@"LightCore.bundle",                             @"root_path":[[NSBundle mainBundle] bundlePath],                             @"effect_mode":@(effectMode)};self.xmagic = [[XMagic alloc] initWithRenderSize:CGSizeMake(720, 1280) assetsDict:assetsDict];
```

**Method 2**

If you are using the TEBeautyKit object, please pass in the EffectMode parameter when calling the createXMagic method.

```
+ (void)createXMagic:(EffectMode)effectMode onInitListener:(OnInitListener _Nullable )onInitListener;
```

The EffectMode is defined as follows:

```
typedef NS_ENUM(NSInteger, EffectMode) {    EFFECT_MODE_NORMAL = 0,    EFFECT_MODE_PRO = 1,};
```

You can enable it by calling the `TencentEffectApi` method `setDowngradePerformance`.

> **Note:**This method needs to be called before activating beauty features, i.e., before the `enableCustomVideoProcess` method in `TRTC or Live`.

You can enable it by calling the `XmagicApi` method `setDowngradePerformance`.

> **Note:**This method needs to be called before activating beauty features, i.e., before the `enableCustomVideoProcess` method.

## How to enable high performance mode before V3.9.0

Android

iOS

Flutter

uniapp

**Method 1**

If you are directly using the `XmagicApi` object, then **please call** the following interface immediately after creating the `XmagicApi` **object** to enable high-performance mode:

- For SDK 3.7.0 and later: Call the `enableHighPerformance` method.
- For SDK before 3.7.0: Call the `setDowngradePerformance` method.

**Method 2**

If you are using the TEBeautyKit object, you can call the following method to enable high performance mode.

```
  /** * @param context                 ApplicationContext * @param isEnableHighPerformance Does it enable high-performance pattern? */public TEBeautyKit(Context context, boolean isEnableHighPerformance)     /** * * Asynchronously create a TEBeautyKit object * @param context Android application context * @param isEnableHighPerformance Whether to enable enhanced mode * @param initListener Initialization callback interface */public static void create(@NonNull Context context, boolean isEnableHighPerformance, @NonNull OnInitListener initListener)
```

**Method 1**

If you are directly using the `XMagic` object, you can enable it during the initialization of `XMagic`:

- For SDK 3.7.0 and later: please set `enableHighPerformance` to YES in the assetsDict dictionary.
- For SDK prior to 3.7.0: please set `setDowngradePerformance` to YES in the assetsDict dictionary.

```
NSDictionary *assetsDict = @{@"core_name":@"LightCore.bundle",@"root_path":[NSBundle mainBundle] bundlePath],@"setDowngradePerformance":@(YES)//YES: Enables high-performance mode; NO: Does not enable high-performance mode. By default, high-performance mode is not enabled.};self.xmagic = [[XMagic alloc] initWithRenderSize:CGSizeMake(720, 1280) assetsDict:assetsDict];
```

**Method 2**

If you are using the TEBeautyKit object, you can call the following method to enable high performance mode.

```
 /** * * Create a TEBeautyKit object * @param isEnableHighPerformance Whether to enable high-performance mode. YES: Enable high-performance mode; NO: Do not enable high-performance mode * @param initListener Initialization callback interface */  + (void)create:(BOOL)isEnableHighPerformance onInitListener:(OnInitListener _Nullable )onInitListener;
```

You can enable it by calling the `TencentEffectApi` method `setDowngradePerformance`.

> **Note:**This method needs to be called before activating beauty features, i.e., before the `enableCustomVideoProcess` method in `TRTC or Live`.

You can enable it by calling the `XmagicApi` method `setDowngradePerformance`.

> **Note:**This method needs to be called before activating beauty features, i.e., before the `enableCustomVideoProcess` method.


---
*Source: [https://trtc.io/document/73786](https://trtc.io/document/73786)*
