# AI-Generated Content Scenario

## Overview

Tencent Cloud's services enhance AI-generated content by integrating quality inspection and advanced imaging technologies, leading to smoother and more lifelike outcomes.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8c8c6228032a11f08c4452540044a08e.png)

## Scenarios

### Quality Discrimination during the Collection and Cleansing Phase of Training Materials

- Requirement: Filter out low-quality videos.
- Solution: By using Tencent MPS quality inspection, videos with format and visual problems can be removed to improve training video quality.'''

### Enhancing Video Resolution, Frame Rate, and Color Fidelity

- Requirement: There is a need to enhance the resolution, frame rate, and color effects of the generated video to achieve a clearer and smoother visual experience.
- Solution: In the context of video generation, the video super-resolution capability can further improve the clarity of AI-generated videos and achieve a smoother visual effect through intelligent frame interpolation.

### Meeting Compliance and Information Traceability Requirements

- ​Requirement: Incorporate essential watermarking into the generated results to ensure traceability and compliance with regulatory requirements.
- ​Solution: Implement the addition of emergent and concealed watermarks to the outputs of large-scale models, ensuring traceability and compliance of information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/98c4d481085a11f09cbb525400454e06.png)

## Feature Overview and Integration Method

| Feature | Description | How to use |
| --- | --- | --- |
| Quality Inspection | Media Quality Inspection Supports:Format Quality InspectionVideo & Audio Content Quality InspectionNo-Reference quality assessmentDuring the material cleansing phase of model training, this feature is capable of detecting issues related to video formats, as well as identifying problems within the visuals such as color distortion, low lighting, vignetting, abnormal contrast, blur, and mosaic effects. By conducting quality inspections and eliminating problematic videos, the overall content quality of the training materials will be significantly enhanced. | Refer to the [Media Quality Inspection Integration](https://www.tencentcloud.com/document/product/1041/67727) documentation. |
| Video Enhancement | The feature improves video by deblurring, reducing noise, enhancing details, text, color, faces, and resolution, and interpolating frames. It can upscale 720P or 1080P videos to 2K or 4K, further improving quality through frame interpolation, detail, and color enhancement.. | Refer to the [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33627) documentation. |
| Image/Video Watermark | Supports the addition of both visible watermarks and invisible watermarks to videos, fulfilling requirements for information traceability and compliance.Supports customization of watermark styles, including watermark images, positions, and sizes. |  |


---
*Source: [https://www.tencentcloud.com/document/product/1041/68753](https://www.tencentcloud.com/document/product/1041/68753)*
