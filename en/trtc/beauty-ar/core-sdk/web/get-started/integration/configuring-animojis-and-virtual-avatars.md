# Configuring Animojis and Virtual Avatars

The Tencent Effect SDK supports animojis and VR virtual avatars starting from v0.3.0.

## Checking Support

Animojis and VR virtual avatars rely on a WebGL2 environment. The SDK offers a static method for you to check whether a browser supports the capability.

```
import {ArSdk} from 'tencentcloud-webar'if (ArSdk.isAvatarSupported()) {    // Initialize the feature} else {    alert('This browser does not support virtual avatars')    // Hide the feature}
```

## Animojis

### Getting models

After initialization, you can get the built-in models. Currently, the SDK offers four built-in animoji models.

```
const avatarARList = await sdk.getAvatarList('AR')
```

> **Note:**Configuring animojis and virtual avatars will automatically remove other effects such as makeup and stickers, and vice versa.

### Setting a model

After you get the list of built-in models, you can select one by specifying the `EffectId` parameter.

```
ar.setAvatar({  mode: 'AR', // Set the mode to `VR`  effectId: avatarARList[0].EffectId// Pass in the built-in ID}, () => {  // success callback});
```

### Customizing a model

If you need to customize a model, feel free to [contact us](https://trtc.io/contact).

## VR Virtual Avatars

### Getting models

The list of built-in models can be obtained after the SDK is initialized. Currently, the SDK offers 10 virtual avatars.

```
const avatarVRList = await sdk.getAvatarList('VR')
```

### Setting a scene

```
ar.setAvatar({  mode: 'VR', // Set `mode` to `VR`   effectId: avatarVRList[0].EffectId, // Pass in the built-in ID  backgroundUrl: 'https://webar-static.tencent-cloud.com/assets/background/1.jpg',}, () => {    // success callback});
```

> **Note:**To set a VR scene, you need to set the background image URL, or the black background will be used by default.

### Customizing a model

You can quickly customize a virtual avatar in two ways and directly use it in the SDK.

- Option 1. `readyplayer.me`
- Option 2. [Vroid](https://vroid.com/en/studio)

With either option, you need to upload the exported model to CDN and use the URL to set the SDK.

```
ar.setAvatar({  mode: 'VR', // Set `mode` to `VR`   url: 'https://xxxx.glb', // Pass in the built-in ID  backgroundUrl: 'https://webar-static.tencent-cloud.com/assets/background/1.jpg',}, () => {    // success callback});
```

Currently, a custom model can be either in GLB or VRM format.


---
*Source: [https://trtc.io/document/51231](https://trtc.io/document/51231)*
