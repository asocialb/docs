# Image Quality Improvement Scenario

## Overview

Tencent Cloud Media Processing enhances video quality in on-demand and live streaming, boosting user retention and commercial conversion. It offers technical solutions across gaming, talent shows, education, and film, adapting to different content needs with its technical expertise and industry experience.

## Key Requirements

- Enhance video quality by rectifying visual imperfections, thereby presenting a superior viewing experience.
- Capable of intelligently processing on demand, reducing costs and increasing efficiency.

## Our Solutions

### Abundant Audio and Video Enhancement Capabilities

Tencent Cloud Media Processing provides various audio and video enhancement options. Users can use single or multiple features for better results.

| Enhancement Type | Features | Description |
| --- | --- | --- |
| Video Enhancement | Super Resolution | Super-resolution can identify the content and contours of the video, reconstruct the details and local features of the video in high definition, converting low-resolution videos into high-resolution ones, suitable for scenarios like old film restoration. |
|  | Low-light Enhancement | Due to environmental conditions and limitations of the camera hardware, some scenes may suffer from a lack of brightness and contrast, resulting in dark images or missing details. Activating low light enhancement significantly improves the details and contrast in dark areas, enhancing the subjective quality of the human eye. |
|  | HDR | Supports HDR10, and HLG, offering a wider color gamut and more color details, providing higher-quality video content. |
|  | Comprehensive Enhancement | Through AI's comprehensive analytical capabilities, it automatically balances the texture content in the image, enhancing key details while removing compression artifacts and jagged edges, thereby improving the overall subjective perception of the image. |
|  | Color Enhancement | Color enhancement makes the image closer to real colors and enhances them to some extent to meet the preferences of the human eye. |
|  | Detail Enhancement | Detail enhancement focuses on the details in the video that require attention (e.g., the grass on a sports field), making the image content clearer and richer. |
|  | Face Enhancement | Enhance the areas of the video that the human visual system particularly focuses on, such as faces, making the details in these areas clearer and improving subjective perception. |
|  | Scratches Removal | Scratch removal can repair scratches and snowflake spots in the video, restoring damaged content. |
|  | Artifacts Removal | Due to multiple compressions of the video during transcoding or multiple transcoding processes, block effects, ringing effects, chroma bleeding, and mosquito noise are introduced, causing distortions that affect the visual effect. De-compression distortion effectively repairs distortions introduced by encoding. |
|  | Video Noise Reduction | Random noise may be introduced during film shooting due to the camera and environment. This service offers denoising, eliminating random noise in the image without losing detail. |
| Audio Enhancement | Audio Noise Reduction | Removes device noise, environmental noise, etc., suitable for scenarios such as recording classes and post-production of outdoor shooting. |
|  | Audio Separation | Separates human voices from background sounds, or singing voices from accompaniment in audio-video files, creating independent audio materials for post-production artistic processing. |
|  | Volume Equalization | Loudness Normalization: Maintains a consistent overall loudness level, making the playback sound similar in volume, avoiding issues of being too loud or too quiet, and providing a better auditory experience.Volume Leveling: Smoothens overly loud audio segments, avoiding sudden volume changes, and providing a more stable auditory experience. |
|  | Audio Improvement | Noise removal: Reduces unwanted noise or interference in the audio, improving the quality and clarity of the audio.De-essing (Sibilance Suppression): Sibilance refers to the sharp, piercing sounds in audio, often produced when the sound source is close to the microphone. Suppressing sibilance aims to reduce or eliminate this unnatural sound, thereby improving audio quality. |

Refer to the figure below:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ad96c405060a11f0ae895254005ef0f7.png)

The [Media Processing Console](https://console.tencentcloud.com/mps/templates/enhs) lets you create and manage audio and video enhancement templates with pre-configured and customizable parameters for various scenarios, helping you quickly meet your business needs.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f2837141048911f08bc5525400454e06.png)

### On-Demand Processing Solutions

Tencent Cloud's audio and video services offer enhancements and on-demand "Quality Inspection + Transcoding & Enhancement". It allows for cost optimization by inspecting video quality before enhancement. Based on inspection results, a suitable enhancement template is chosen. The improvement is measured by comparing video scores before and after processing.

| Feature | Description | How to use |
| --- | --- | --- |
| Quality Inspection | Quality Inspection includes:Format quality inspection: Detects format issues such as DTS, PTS problems, resolution changes, sampling rate changes, frame loss, and duplicate frames.Supports detecting the image quality of videos, with the specific inspection items as follows: JitterResults, BlurResults, AbnormalLightingResults, CrashScreenResults, BlackWhiteEdgeResults, NoiseResults, MosaicResults etc.No-Reference quality assessment | Refer to the [Media Quality Inspection Integration](https://www.tencentcloud.com/document/product/1041/67727) documentation. |
| Audio and Video Enhancement | In on-demand processing scenarios, the focus is on fixing audio and video issues identified during quality checks through targeted interventions.Low-light EnhancementComprehensive EnhancementFace EnhancementAudio Noise ReductionVideos without issues don't need enhancement, which could help to reduce costs. | Refer to the [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33627) documentation. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/68751](https://www.tencentcloud.com/document/product/1041/68751)*
