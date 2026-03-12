# Floating Window

This article will introduce how to use the Floating Window feature.

## Expected outcome

| **Web Floating Window** | **Web Full Screen** | **HTML5 Floating Window** |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0367f70c18f911efac7f5254007bbd8c.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e729ca6018f811ef942e525400720cb5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8bea254c18f811ef957f525400f65c2a.png) |

## Floating Window feature

Method 1: Use the `enableFloatWindow(enable: boolean)` API to enable/disable the Floating Window.

```
import { TUICallKitAPI } from "@trtc/calls-uikit-react";try {  await TUICallKitAPI.enableFloatWindow(enable: Boolean)} catch (error: any) {  alert(`[TUICallKit] enableFloatWindow failed. Reason: ${error}`);}
```

Method 2: Control the Floating Window and the Full Screen on/off through attribute control.

- The `allowedMinimized` attribute controls the enabling/disabling of the Floating Window.
- The `allowedMinimized` attribute controls the enabling/disabling of the Full Screen.

React

Vue

```
<TUICallKit     allowedMinimized={true}     allowedFullScree={true}    />
```

```
<TUICallKit    :allowedMinimized="true"    :allowedFullScreen="true"   />
```


---
*Source: [https://trtc.io/document/59842](https://trtc.io/document/59842)*
