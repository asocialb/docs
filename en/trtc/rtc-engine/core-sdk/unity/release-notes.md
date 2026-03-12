# Release Notes

## Version 12.4 @ April 6, 2025

#### Improvements

- All Platforms: Optimize vad precision in TRTCVolumeInfo status parameters.
- Android: Supports Low Energy Bluetooth (BLE) connection.
- Mac: Full-screen capture with highlighted border filtering.

#### Bug fixing

- Android: Fixed an issue where some devices would switch to speaker mode when changing headphones while the microphone was active.
- All Platforms: Fixed the 'Cold Voice' sound effect muting issue.
- Android & iOS: Camera supports a Long-Time No-Frame Detection Strategy.

#### Interface behavior adjustment

1. Custom Preprocessing Format Matching Logic Adjustment.
  - The TRTCVideoPixelFormat_Texture_2D format is internally mapped to RGBA32.
  - TRTCVideoBufferType_Texture only supports combination with TRTCVideoPixelFormat_Texture_2D.
2. iOSï¼Screen Sharing Updates System Triggered Pause/Resume Reason.
  - Pause Event: When screen sharing is active and the user taps the system's stop Screen Recording button, onScreenCapturePaused Callback reason code: -4.
  - Resume Event: When screen sharing is paused and the user taps the system's start Screen Recording button, onScreenCaptureResumed Callback reason code: -4.


---
*Source: [https://trtc.io/document/72215](https://trtc.io/document/72215)*
