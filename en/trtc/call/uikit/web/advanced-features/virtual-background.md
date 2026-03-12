# Virtual Background

TUICallKit has launched a new feature for virtual backgrounds, allowing users to set a blurry or image background during video calls. This hides the real calling environment, protects privacy, and makes the call more interesting. Next, this article will detail how to use this feature in the TUICallKit component.

## Integration effect

The display effect of the TUICallKit component after integrating the virtual background feature is as follows.

| Original Camera | Blurry Background Effect | Image Background Effect |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5086419d19a211ef942e525400720cb5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4aec318019a211ef942e525400720cb5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/429c593719a211ef87e352540019e87e.png) |

## Preparation Requirements

Before using the Virtual Background feature provided by Tencent Cloud, you need to visit the Console to activate Audio and Video Services for your application and purchase the `Group Call` package. For specific steps, please see [Activate Service.](https://www.tencentcloud.com/document/product/647/59832)

## Enable Blurry Background

TUICallKit's UI design supports setting a blurry background. By calling the following interface, you can display a feature button for the blurry background on the UI. Clicking the button will directly enable the blurry background feature.

> **Noteï¼**H5 is not supported yet, only PC supports it.

```
import { TUICallKitAPI } from "@trtc/calls-uikit-vue"; TUICallKitAPI.enableVirtualBackground(true);
```

## Setting Image Background (Optional)

Implementing the image background requires users to save the image locally. After saving, call the following interface for setting (currently, only images with a local path are supported,  images of uri are not supported yet).

```
import { TUICallKitAPI } from "@trtc/calls-uikit-vue"; TUICallKitAPI.getTUICallEngineInstance().setVirtualBackground(imagePath: string)
```

## FAQs

### Enabling blurry background has no response or is delayed

- Ensure you have purchased the audio and video call `Group Call` package, see [Activate Service.](https://www.tencentcloud.com/document/product/647/59832)
- When the network is poor, the virtual background model file may not be completely downloaded, resulting in failure to open the virtual background.

### Can the virtual background be turned on if the camera is turned off?

Not available.


---
*Source: [https://trtc.io/document/60487](https://trtc.io/document/60487)*
