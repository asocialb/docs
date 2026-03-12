# Enable AI Denoiser

The AI Denoiser plugin reduces noise during calls and minimizes the impact of environmental noise on communication. It effectively suppresses keyboard sounds, collisions, and other noises, making it particularly suitable for scenarios sensitive to transient noise, such as conference settings.

This article introduces how to apply the AI Denoiser to the local audio stream in TRTC applications. [Click here to experience it online](https://trtc.io/demo/homepage/#/detail?scene=trtc&active=ai) with the denoiser demo.

## Prerequisites

- For usage fee details, see TRTC [Edition Features and Pricing](https://trtc.io/document/56025#f10b65d1-6e8d-41e3-8686-84909b00a1a2).
- Supported browsers
  - Chrome 66+, Edge 79+, Safari 14.1+, Firefox 76+.
  - For Android systems, the Chrome version must be above 92.

To make the best use of the AI Denoiser, it is recommended to use the latest version of the Chrome browser.

> **Note:**If there is background music in the microphone input, the denoiser plugin may treat it as noise and eliminate it.

## Implementation Process

#### Deploy Static Resources

This plugin relies on static resource files. To ensure the browser can load and run these files properly, complete the following steps:

1. Publish the `node_modules/trtc-sdk-v5/assets` directory to a CDN or static resource server.
2. Pass your CDN address to the `assetsPath` parameter when creating the TRTC instance, for example: `TRTC.create({ assetsPath: 'https://xxx/assets' })`. The SDK will load the relevant resource files as needed.

> **Note:**If your version is below `v5.10.0`, you need to publish `node_modules/trtc-sdk-v5/plugins/ai-denoiser/denoiser-wasm.js` to the CDN and place it in the same public directory, such as `https://xxx/assets`.If the Host URL of the files in the directory differs from the Host URL of the web application, you need to enable the CORS policy for the file domain.Do not place the directory files under an HTTP service, as loading HTTP resources under an HTTPS domain will be blocked by browser security policies.

#### Enable denoiser

```
const trtc = TRTC.create({ assets: 'https://xxx/assets' });await trtc.startLocalAudio();await trtc.startPlugin('AIDenoiser', {  sdkAppId: 123456,  userId: 'user_123',  userSig: 'XXXXXXXX'});
```

#### Disable denoiser

```
await trtc.stopPlugin('AIDenoiser');
```

## API Description

### trtc.startPlugin('AIDenoiser', options)

Used to enable denoiser.

#### options:

| Name | Type | Description |
| --- | --- | --- |
| assetsPath | `string` | The location where the `denoiser-wasm.js` file is stored. If your version is below `v5.5.2`, you need to pass the assets resource directory through this parameter. |
| sdkAppId | `number` | The sdkAppId of the current application |
| userId | `string` | The userId of the current user |
| userSig | `string` | The userSig of the current user |

### trtc.stopPlugin('AIDenoiser')

Used to disable denoiser.


---
*Source: [https://trtc.io/document/59658](https://trtc.io/document/59658)*
