# Supported Platforms

## Supported Platforms

The TRTC Web SDK supports all major browsers such as **Chrome, Edge, Firefox, Safari, and Opera**. In theory, the SDK supports all browsers based on Chromium version 56+.

To ensure the best user experience, you should recommend users to use the latest version each browser on the latest version of the operating system.

Download the latest version of [Chrome](https://www.google.com/intl/en/chrome/), [Edge](https://microsoft.com/edge), [Firefox](https://www.mozilla.org/firefox/new/), [Safari](https://support.apple.com/en-hk/HT201541).

| OS | Browser Type | Version | Subscribing Audio/Video | Publishing Audio/Video | Screen Sharing |
| --- | --- | --- | --- | --- | --- |
| Windows | Chrome | 56+ | Yes | Yes | 72+ |
|  | Firefox | 56+ | Yes | Yes | 66+ |
|  | Edge | 80+ | Yes | Yes | 80+ |
|  | Opera | 46+ | Yes | Yes | 60+ |
|  | Others(Chromium Based) | 56+ | Yes | Yes | 72+ |
| Mac OS | Safari | 11+ | Yes | Yes | 13+ |
|  | Chrome | 56+ | Yes | Yes | 72+ |
|  | Firefox | 56+ | Yes | Yes | 66+[(Note [3])](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-05-info-browser.html#attention3) |
|  | Edge | 80+ | Yes | Yes | 80+ |
|  | Opera | 46+ | Yes | Yes | 60+ |
| Chrome OS | Chrome | 56+ | Yes | Yes | 72+ |
| Android | Chrome | 79+ | Yes | Yes | No |
|  | Edge | 80+ | Yes | Yes | No |
|  | Firefox | 80+ | Yes | Yes | No |
|  | Chrome Webview | 79+ | Yes | Yes | No |
| iOS | Safari | iOS 11+ | Yes | Yes | No |
|  | Chrome | iOS 11+ | Yes | iOS 14.3+ | No |
|  | Edge | iOS 11+ | Yes | iOS 14.3+ | No |
|  | Others(WKWebview Based) | iOS 11+ | Yes | iOS 14.3+ | No |

## Detect Browser's Capabilities

If your browser is not in the list, you can use the API [TRTC.isSupported()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.isSupported) or run a [TRTC Web SDK Support Level Test](https://web.sdk.qcloud.com/trtc/webrtc/demo/detect/index.html) in the browser to test whether it fully supports WebRTC.

Refer to [Detect Capabilities](https://www.tencentcloud.com/document/product/647/59656).

## URL Protocol Support

Because of the [Secure Contexts](https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts) of browsers, there are requirements on the protocol used for access when you use TRTC Web SDK.

| Scenario | Protocol | Subscribing Audio/Video | Publishing Audio/Video | Share Screen | Remarks |
| --- | --- | --- | --- | --- | --- |
| Production | HTTPS | Yes | Yes | Yes | **Recommended** |
| Production | HTTP | Yes | No | No | - |
| Local development | http://localhost | Yes | Yes | Yes | **Recommended** |
| Local development | http://127.0.0.1 | Yes | Yes | Yes | - |
| Local development | http://[local IP address] | Yes | No | No | - |
| Local development | file:/// | Yes | Yes | Yes | - |


---
*Source: [https://trtc.io/document/59733](https://trtc.io/document/59733)*
