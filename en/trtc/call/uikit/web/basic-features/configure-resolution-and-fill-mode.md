# Configure Resolution and Fill Mode

Introduction to how to set resolution, fill pattern.

## Setting resolution, fill pattern

The TUICallKit component provides numerous feature switches, allowing for selective enabling or disabling as needed. For specifics, refer to [Introduction to TUICallKit Attributes](https://www.tencentcloud.com/document/product/647/51015).

- `VideoDisplayMode`: Display mode of the frame.
- `VideoResolution`: Call resolution.

React

Vue

```
import { VideoDisplayMode, VideoResolution } from "@trtc/calls-uikit-react";<TUICallKit    videoDisplayMode={VideoDisplayMode.CONTAIN}    videoResolution={VideoResolution.RESOLUTION_1080P} />
```

```
import { VideoDisplayMode, VideoResolution } from "@trtc/calls-uikit-vue";<TUICallKit    :videoDisplayMode="VideoDisplayMode.CONTAIN"    :videoResolution="VideoResolution.RESOLUTION_1080P" />
```

### videoDisplayMode

There are three values for the `videoDisplayMode` display mode:

- `VideoDisplayMode.CONTAIN`
- `VideoDisplayMode.COVER`
- `VideoDisplayMode.FILL`, the default value is `VideoDisplayMode.COVER`.

| **Attribute** | **Value** | **Description** |
| --- | --- | --- |
| videoDisplayMode | VideoDisplayMode.CONTAIN | Ensuring the full display of video content is our top priority.The dimensions of the video are scaled proportionally until one side aligns with the frame of the viewing window.In case of discrepancy in sizes between the video and the display window, the video is scaled - on the premise of maintaining the aspect ratio - to fill the window, resulting in a black border around the scaled video. |
|  | VideoDisplayMode.COVER | Priority is given to ensure that the viewing window is filled.The video size is scaled proportionally until the entire window is filled.If the video's dimensions are different from those of the display window, the video stream will be cropped or stretched to match the window's ratio. |
|  | VideoDisplayMode.FILL | Ensuring that the entire video content is displayed while filling the window does not guarantee preservation of the original video's proportion.The dimensions of the video will be stretched to match those of the window. |

### videoResolution

The resolution `videoResolution` has three possible values:

- `VideoResolution.RESOLUTION_480P`
- `VideoResolution.RESOLUTION_720P`
- `VideoResolution.RESOLUTION_1080P`, the default value is `VideoResolution.RESOLUTION_480P`.

**Resolution Explanation:**

| **Video Profile** | **Resolution (W x H)** | **Frame Rate (fps)** | **Bitrate (Kbps)** |
| --- | --- | --- | --- |
| 480p | 640 Ã 480 | 15 | 900 |
| 720p | 1280 Ã 720 | 15 | 1500 |
| 1080p | 1920 Ã 1080 | 15 | 2000 |

**Frequently Asked Questions:**

- iOS 13&14 does not support encoding videos higher than 720P. It is suggested to limit the highest collection to 720P on these two system versions. Refer to [iOS Safari known issue case 12](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-02-info-webrtc-issues.html#h2-4).
- Firefox does not permit the customization of video frame rates (default is set to 30fps).
- Due to the influence of system performance usage, camera collection capabilities, browser restrictions, and other factors, the actual values of video resolution, frame rate, and bit rate may not necessarily match the set values exactly. In such scenarios, the browser will automatically adjust the Profile to get as close to the set values as feasible.


---
*Source: [https://trtc.io/document/59835](https://trtc.io/document/59835)*
