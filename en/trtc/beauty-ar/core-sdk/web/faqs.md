# FAQs

This document answers questions you may encounter when using Beauty AR Web.

### The makeup, sticker, and other settings are not taking effect, and the console keeps showing 'waiting for AI init'.

To reduce the package size, the SDK has implemented modular loading. When initializing the SDK, configure the modules to be loaded based on the **module** parameter. The makeup, and stickers depend on the **beautify module**, which needs to be set to true to enable them. For more details, please refer to the [API documentation](https://www.tencentcloud.com/document/product/1143/50106)."

### What should I do if the image is upside down and lags when I run the demo in Chrome?

As the SDK uses the GPU for acceleration, you need to toggle on **Use hardware acceleration when available** in the browserâs settings.

### The console display error âFailed to execute 'getContext' on 'OffscreenCanvas': The provided value 'experimental-webgl' is not a valid enum value of type OffscreenRenderingContextTypeâ

This is usually because hardware acceleration in the browser is not enabled.

### The page crashes when using the SDK in a 32-bit browser.

The SDK will consume a certain amount of memory during operation, typically not exceeding 500MB. It is recommended to use a 64-bit browser. The memory limit for a single tab in a 32-bit browser is usually no more than 1GB, and this limit is shared with other tabs. This can lead to insufficient memory situations, especially when multiple tabs are open or when the application itself is memory-intensive, causing the browser page to crash.

### Can I use the Beauty AR Web SDK to beautify live streams published in a web live streaming application?

Yes. The SDK can work as an intermediate rendering processor for live streaming. It supports multiple input/output sources. For information about how to easily extend your web application and quickly implement beauty filters and effects, see [Publishing over WebRTC](https://www.tencentcloud.com/document/product/1143/53886) and [Publishing with TRTC](https://www.tencentcloud.com/document/product/1143/53885).

### Will my signature service be frequently called?

### Will the effect displayed after the call to the SDK differ from the effect previewed in the customization tool in the console?

### How do I use the `localhost` for local development?

The Web License will verify the domain information during use, so it is essential to ensure that the actual running domain matches the domain specified when applying for the license; otherwise, a domain verification failure error will occur.

However, this does not apply to localhost addresses, as localhost is automatically validated. Therefore, you can use localhost for local development without any port restrictions."

### Why is the website unable to access the camera?

- User Not Authorized: When accessing for the first time, the browser will prompt an authorization request. If the user denies it, they need to enable permissions manually. Solution: Guide the user to re-authorize in the browser settings (Chrome: Settings > Privacy and security > Camera > Allow specified sites).
- ââAccessing from an Insecure Environment: Browsers require HTTPS or a local environment (localhost://127.0.0.1); access is typically blocked under HTTP. Solution: Deploy HTTPS or use localhost during development; temporarily allow HTTP addresses during debugging by visiting chrome://flags/#unsafely-treat-insecure-origin-as-secureã

### Why is "streamurl authentication failed" displayed in the console after LEB publishing failed?

### Why is an error reported when I call `getEffectList` to pull material resources?

This is usually because the timing of the call is incorrect. Be sure to **call**`getEffectList`**when or after the**`created`**API of the SDK is called back**. At that point, the business interaction logic can be implemented based on the material data. For the specific use cases, see [Best Practices](https://www.tencentcloud.com/document/product/1143/53886).

### Why does echo occur when I preview the video effect after web is connected to the built-in camera of the SDK?

```
const output = await sdk.getOutput()const video = document.createElement('video')document.body.appendChild(video)video.setAttribute('muted', '')video.volume = 0video.srcObject = output
```

### Why does the SDK report an authentication failure and the API returns 401?

### Why does the SDK report 'This project does not exist'?

The error is caused by an invalid license provided during SDK initialization. Please verify that the license is completed correctly and that it is within its valid period. Additionally, if the token and license parameters are swapped in position, this error may also occur.


---
*Source: [https://trtc.io/document/51233](https://trtc.io/document/51233)*
