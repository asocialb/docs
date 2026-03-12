# Configuring Segmentation

The segmentation module needs to be enabled during initialization to implement virtual backgrounds. For more information, see [Custom Stream or Image](https://www.tencentcloud.com/document/product/1143/50102) and [Built-in Camera](https://www.tencentcloud.com/document/product/1143/50101).

## Setting the Background

```
const config = {  module: {      beautify: true, // Whether to enable the effect module, which offers beautification and makeup effects as well as stickers      segmentation: true // Whether to enable the segmentation module, which allows you to change the background      segmentationLevel: 0 // Switch background segmentation models supported since Versions 1.0.19  },  auth: authData, // The authentication information  input: stream, // The input stream  beautify: { // The effect parameters for initialization (optional)      whiten: 0.1,      dermabrasion: 0.3,      eye: 0.2,      chin: 0,      lift: 0.1,      shave: 0.2  },  background: {      type: 'blur' // Blur the background  }}const sdk = new ArSdk(  // Pass in a config object to initialize the SDK  config)
```

- You can also change the background.

```
sdk.setBackground({  type: 'image', // The background image  src: 'https://webar-static.tencent-cloud.com/assets/background/1.jpg'})
```

- Support video-type dynamic backgrounds (**supported from version 1.0.23**):

```
sdk.setBackground({  type: 'video', // The background video  src: 'https://webar-static.tencent-cloud.com/assets/background/video-bg-1.mp4',})
```

## Using Transparent Backgrounds

```
sdk.setBackground({    type: 'transparent'})
```

> **Note:**Keep the following in mind:Segmentation is supported on both mobile and desktop browsers.Because WebRTC does not support alpha channels, you can only use transparent backgrounds locally. Background transparency will not work after publishing.Background transparency is supported on desktop Chrome and Firefox, but not supported on desktop or mobile Safari.Starting from version 1.0.19 and above, switching background segmentation models is supported, with parameters: 0, 1, 2.Level 0 has the best performance but relatively average segmentation results. Level 1 has a moderate performance and effect. Level 2 has the best segmentation results and the longest inference time, suitable for applications with high requirements for segmentation effects and low performance requirements.


---
*Source: [https://trtc.io/document/50105](https://trtc.io/document/50105)*
