# FAQs

## Environment-related Issues

### What platforms does TUIRoomKit Web support?

Please refer to [TRTC Web SDK's browser support](/document/product/647/41664) for TUIRoomEngine Web supported platforms.

For environments not listed above, you can open the [TRTC Capability Test](https://web.sdk.qcloud.com/trtc/webrtc/demo/detect/index.html) in your current browser to test if it fully supports WebRTC features.

### Why can TUIRoomKit be used normally in local development testing, but not when deployed online?

Considering user safety and privacy issues, browsers restrict web pages to only capture mic and Camera in secure environments (such as https, localhost, file:// protocols). HTTP protocol is insecure, and browsers will prohibit media device capturing under HTTP protocol.

If everything works fine in your local development testing, but you cannot capture Camera and mic after deploying the page, please check if your web page is deployed on HTTP protocol. If so, please use HTTPS to deploy your web page and ensure a qualified HTTPS security certificate.

For more details, please refer to [the URL domain and protocol restrictions description](/document/product/647/41664).

### TDoes TUIRoomKit Web support integration with iframe?

Yes, it does. To integrate TUIRoom Web in an iframe, you need to add attributes to the iframe tag to enable related permissions, as shown below.

```
// Enable mic, Camera, Screen Sharing, and full-screen permissions<iframe allow="microphone; camera; display-capture; display; fullscreen;">
```

## Compilation-related Issues

### Webpack 5 importing TUIRoomEngine SDK error: webpack < 5 used to include polyfills for node.js core modules by default. This is no longer the case. Verify if you need this module and configure a polyfill for it.

The error is caused by the removal of the automatic inclusion of nodejs core module polyfills in webpack5. You can add configureWebpack configuration in vue.config.js to solve this problem.

```
module.exports = defineConfig({  // ...  configureWebpack: (config) => {    config.resolve.fallback = {      ...config.resolve.fallback,      url: false,      path: false,      fs: false,      crypto: false,    };  }});
```

## Function-related Issues

#### Can tim-js-sdk and @tencentcloud/tuiroom-engine-js be introduced in the project at the same time?

Yes, they can. You can create a tim instance object through TIM in tim-js-sdk and pass it to the init interface when initializing TUIRoomEngine.

```
await TUIRoomEngine.init({ sdkAppId: 0,   // Fill in your applied sdkAppId userId: '',    // Fill in your business-related userId userSig: '',   // Fill in the userSig calculated by the server or locally tim,    // Pass in the tim instance});
```

Also, you can get the tim instance used internally by TUIRoomEngine through the roomEngine.getTIM method.


---
*Source: [https://trtc.io/document/54894](https://trtc.io/document/54894)*
