# Enhanced Mode User Guide

## What is Enhanced Mode

In the SDK, it is recommended to set the beauty parameters in the range of 0 to 100 or -100 to 100 (see [Effect Parameters](https://www.tencentcloud.com/document/product/1143/60207)). Adjusting parameters within this range typically achieves satisfactory beauty effects. If adjusting a parameter to the maximum or minimum value still does not meet your needs, you may consider using Enhanced Mode. Enhanced Mode can make the beauty effects more pronounced, such as more noticeable skin smoothing and slimming the face further.

## How to Use Enhanced Mode

In versions after SDK 3.5.0, we have optimized the method of using Enhanced Mode. **You just need to set larger values in the SDK**, for example, if the suggested value range is -100 to 100, then you can set -120 to 120 in the SDK.

Android

iOS

Flutter

uniapp

1. **If you are using our UI component TEBeautyKit:**

Call the `enableEnhancedMode` method of `TEBeautyKit`. After the call, TEBeautyKit will multiply the value displayed on the panel by an appropriate multiplier before setting it in the SDK. For example, if the Face Slimming Value set on the UI panel is 80, TEBeautyKit will multiply it by 1.2 to make it 96 before setting it in the SDK.

2. **If you are not using TEBeautyKit but are directly using XmagicApi instead:**

When calling the setEffect method of XmagicApi, just multiply the value by an appropriate multiplier.

1. **If you are using our UI component TEBeautyKit:**

In `TEPanelView`, call the `setEnhancedMode` method. After the call, TEBeautyKit will multiply the value displayed on the panel by an appropriate multiplier before setting it to the SDK. For example, if the Face Slimming Value set on the UI panel is 80, TEBeautyKit will multiply it by 1.2 to make it 96 before setting it to the SDK.

```
 /** * * Enabling Enhanced Mode * @param enhancedMode Whether to enable Enhanced Mode. YES: Enable Enhanced Mode; NO: Do not enable Enhanced Mode. By default, Enhanced Mode is not enabled. */  [self.tePanelView setEnhancedMode:YES];
```

2. **If you are not using TEBeautyKit but are directly using** `XMagic` **object:**

When calling the setEffect method, just multiply the value by an appropriate multiplier.

1. Call the `enableEnhancedMode` method of `TencentEffectApi` to enable Enhanced Mode.
2. When you set beauty parameters with the `setEffect` method, the maximum value of `effectValue` can be the maximum value recommended in the table below.

```
void setEffect(String effectName,int effectValue,String? resourcePath,Map<String,String>? extraInfo);
```

1. Call the `enableEnhancedMode` method of `XmagicApi` to enable Enhanced Mode.
2. When you set beauty parameters with the `setEffect` method, the maximum value of `effectValue` can be the maximum value recommended in the table below.

```
/** * Updating Beauty Object * @param effect Structure as follows * { *     effectName:"", Non-empty string. Refer to the Beauty Parameters table. *     effectValue: Numerical value, usually in the range of -100 to 100. Refer to the Beauty Parameters table on the official website. *     resourcePath: Path of the resource file. Refer to the Beauty Parameters table https://www.tencentcloud.com/document/product/1143/60207 *     extraInfo: A map collection. For specific values, refer to the Beauty Parameters table. * } */static setEffect(effect)
```

## Recommended Enhancement Multiplier for Enhanced Mode

We provide a reference value for the enhancement multiplier. It is not recommended to exceed our suggested value. Otherwise, the beauty effect may deteriorate. See below for the reference value:

| Beauty Item Name | Recommended Maximum Enhancement Multiplier |
| --- | --- |
| Whitening, shortening the face, V-face, eye distance, nose position, removal of laugh lines, lipstick, three-dimensional appearance | 1.3x |
| Eye lightening | 1.5x |
| Blush | 1.8x |
| Others | 1.2x |
|  |  |
|  |  |
|  |  |


---
*Source: [https://trtc.io/document/73785](https://trtc.io/document/73785)*
