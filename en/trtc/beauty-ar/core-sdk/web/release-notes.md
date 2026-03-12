# Release Notes

> **Note:**The Web SDK V2 version has been officially released, compared to V1, V2 offers significant performance improvements, and the API interfaces are backward compatible. We strongly recommend upgrading to V2 to enjoy an enhanced user experience.Please note that in the future, the V1 version will only receive bug fixes and will not provide any new feature updates. Therefore, to ensure you have access to the latest features and optimal performance, please complete your upgrade as soon as possible.

### SDK Version 2.0.2 @ 2026-01-07

- Fixed the issue where the SDK initialization did not set the **module** parameter, resulting in an error.
- Disabled all detections, including gesture detection, when calling the **disable** interface.
- Fixed the issue where the **disable** interface did not turn off the whitening and skin smoothing effects.
- Fixed the issue where repeatedly turning the camera on and off in Windows caused it to freeze unexpectedly.
- Fixed other issues.

### SDK Version 2.0.1 @ 2025-11-28

- Fixed the issue of errors with the Blur background.
- Resolved the problem of abnormal virtual background display when switching scenes in the Safari browser.
- Fixed other issues.

### SDK Version 2.0.0 @ 2025-11-20

- Optimized overall performance, significantly reducing frame processing time and improving rendering frame rates.
- Enhanced the virtual background effect.
- Fixed other issues.

### SDK Version 1.0.28 @ 2025-09-18

- Optimized the Beautify effect performance.
- Fixed the issue of being unable to switch devices when using the built-in camera in Chrome browser.
- Resolved the problem of slightly washed-out video after export.
- Fixed the issue on certain Android devices where the screen freezes when the face moves out of the frame.
- Fixed other issues.

### SDK Version 1.0.27 @ 2025-07-21

- Improve the log reporting system.
- Dynamically adjust the virtual background effects based on device performance.
- Fixed other issues.

### SDK Version 1.0.26 @ 2025-04-29

- Improve the log reporting system.
- The language parameter in the SDK supports Japanese (jp).
- Fixed other issues.

### SDK Version 1.0.25 @ 2025-03-21

- Virtual background supports setting the edge blur level.
- Input supports the HTMLVideoElement  type.
- Supports dynamic configuration for enabling browser worker capabilities.
- Fixed other issues.

### SDK Version 1.0.24 @ 2024-12-13

- Added image processing interface, supporting high-resolution image processing.
- Fixed an error issue when switching virtual background levels.
- Resolved the issue where calling setBeautify had no effect in the ready callback.
- Fixed the screen stuck issue when switching between landscape and portrait modes on iOS.
- Addressed issues with black screens and ineffective beauty effects when using TRTC on iOS 16.

### SDK Version 1.0.23 @ 2024-10-15

- Added support for dynamic backgrounds.
- Added support for full-screen foregrounds.
- Introduced gesture recognition interface.
- Added "isWebGL2Supported" interface to check if the browser supports WebGL2.
- Optimized performance issues.
- Fixed pre-initialization error issues in some browsers.
- Resolved the issue where closing the beauty effect caused the virtual background to freeze.
- Fixed the problem of incomplete display when switching input stream resolutions.
- Fixed other issues.

### SDK Version 1.0.22 @ 2024-05-07

- Added support for internal network proxy mode.
- Optimized beauty effects.
- Improved edge smoothing for virtual backgrounds.
- Optimized performance issues.
- Fixed issues in some browsers where changing resolution led to misalignment of 3D sticker positions and loss of beauty effects.
- Resolved issues with beauty stickers being obstructed.
- Fixed the mirroring issue in Camera mode on Firefox.
- Fixed the non-functional mirror parameter in Input MediaStream mode on Firefox.
- Fixed other issues.

### SDK Version 1.0.21 @ 2023-12-2

- Optimized performance issues.
- Fixed other issues.

### SDK Version 1.0.19 @ 2023-11-20

- Supported Segmentation level.
- Optimized performance issues.
- Fixed other issues.

### SDK Version 1.0.16 @ 2023-10-24

- Optimized performance issues.
- Fixed other issues.

### SDK Version 1.0.11 @ 2023-07-17

- Add hairline, clarity and other beauty parameters.
- Optimized performance issues.
- Fixed other issues.

### SDK Version 1.0.0 @ 2023-02-27

Launched commercial editions.

### SDK Version 0.3.0 @ 2022-10-14

- Added animoji and virtual avatars for web.
- Fixed a memory leak issue.
- Fixed other issues.

### SDK Version 0.2.5 @ 2022-08-01

- Fixed the forced quit of the Weixin browser on Android.
- Fixed the bug where the background did not disappear after being disabled.
- Fixed other issues.

### SDK Version 0.2.3 @ 2022-07-20

- Fixed the adaptation failure when the input source was switched.
- Added support for starting and stopping face detection.
- Fixed other issues.

### SDK Version 0.2.0 @ 2022-06-29

- Added support for keying on web.
- Optimized the integration experience.

### SDK Version 0.1.18 @ 2022-06-17

- Optimized the built-in camera configuration, improved camera management capabilities, and added the local player.
- Added the configuration of delayed initialization.
- Optimized the filter strength settings and overlay effects.

### SDK Version 0.1.12 @ 2022-05-11

- Optimized the SDK performance.
- Added the FPS attribute, which can be used to set the rendering frame rate.

### SDK Version 0.1.9 @ 2022-04-28

- Added built-in stickers.
- Fixed the black screen issue which occurred while switching to the background on mobile web.

### SDK Version 0.1.1 @ 2022-04-13

- Officially released the SDK.


---
*Source: [https://trtc.io/document/51232](https://trtc.io/document/51232)*
