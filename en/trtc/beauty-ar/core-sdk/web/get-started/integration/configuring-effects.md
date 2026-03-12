# Configuring Effects

The Tencent Effect SDK offers **beautification effects**, **filters**, and **special effects**. For filters and special effects, you need to get the material list first and configure them in the SDK by specifying the effect ID.

## Beautification

You can pass in beautification parameters during initialization. You can also call `setBeautify` of the SDK to set beautification effects.

- Currently, the SDK supports the following beautification effects:

```
type BeautifyOptions = {  whiten?: number, // The brightening effect. Value range: 0-1.  dermabrasion?: number // The smooth skin effect. Value range: 0-1.  lift?: number // The slim face effect. Value range: 0-1.  shave?: number // The face width. Value range: 0-1.  eye?: number // The big eyes effect. Value range: 0-1.  chin?: number // The chin effect. Value range: 0-1.// The following parameters are only available in version 1.0.11 and above  darkCircle?: number; // The dark circle effect. Value range: 0-1.  nasolabialFolds?: number; // The nasolabial folds effect. Value range: 0-1.  cheekbone?: number; // The cheek bone effect. Value range: 0-1.  head?: number; // The head effect. Value range: 0-1.  eyeBrightness?: number; // The eye brightness effect. Value range: 0-1.  lip?: number; // The lip effect. Value range: 0-1.  forehead?: number; // The forehead effect. Value range: 0-1.  nose?: number; // The nose effect. Value range: 0-1.  usm?: number; // The distinct effect. Value range: 0-1.}
```

- Call `setBeautify` of the SDK to set beautification effects:

```
sdk.setBeautify({  whiten: 0.2,  dermabrasion: 0,  lift: 0.3,  shave:0.1,  eye: 0.9,  chin: 0,  â¦â¦})
```

## Filters

Given the relatively high cost of filter design, we offer some built-in filters which you can use directly.

1. Get the built-in filter list:

```
const filterList = await sdk.getCommonFilter()
```

2. Set the filter:

```
sdk.setFilter(filterList[0].EffectId, 0.5)
```

## Special Effects

You can use the SDKâs built-in effects or effects you customized in the [RT-Cube console](https://console.tencentcloud.com/xmagic/creator). To learn about how to customize effects, please [contact us](https://trtc.io/contact).

```
// Get the built-in effects// By default, both makeup effects and stickers are returned. You can also use the `Label` parameter to specify the category of materials to return.const presetEffectList = await sdk.getEffectList({    Type: 'Preset'    // Label: ['Sticker'] (Return only stickers)})// Get the custom effectsconst customEffectList = await sdk.getEffectList({    Type: 'Custom'})// Pass in the request parameters of `getEffectList`const lipList = await sdk.getEffectList({    PageNumber: 0,    PageSize: 10,    Name: '',    Label: ['Lip makeup'], // Specify the specific type of materials to return    Type: 'Custom'})const eyeList = await sdk.getEffectList({    PageNumber: 0,    PageSize: 10,    Name: '',    Label: ['Eye makeup'], // Specify the category of resources to return    Type: 'Custom'})// Use an effectsdk.setEffect([lipList[0].EffectId, eyeList[0].EffectId])// Specify the effect to use and the strength of the effectsdk.setEffect([{    id: lipList[0].EffectId,    intensity: 0.5}, {    id: eyeList[0].EffectId,    intensity: 0.7})// Set only the filter strengthsdk.setEffect([{    id: lipList[0].EffectId,    intensity: 0.5,    filterIntensity: 0}, {    id: eyeList[0].EffectId,    intensity: 0.7,    filterIntensity: 1})
```

> **Note:**When customizing a special effect, you can add a filter to the effect. In such cases, you can use `filterIntensity` to adjust the strength of the filter separately.

## Disabling Detection

The performance overhead of AI detection is high. To reduce resource consumption, the SDK will automatically disable AI detection when no effects are used and enable AI detection again when effects are applied.

```
// Clear all effect settings to disable AI detectionsdk.setBeautify({    whiten: 0,    dermabrasion: 0,    lift: 0,    shave:0,    eye: 0,    chin: 0,    â¦â¦ // reset all parameters to 0})sdk.setEffect('')
```


---
*Source: [https://trtc.io/document/54291](https://trtc.io/document/54291)*
