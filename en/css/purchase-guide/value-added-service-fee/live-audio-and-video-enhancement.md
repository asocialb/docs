# Live Audio and Video Enhancement

Live audio and video enhancement features include a variety of processing technologies, such as SDR to HDR conversion, frame interpolation, super resolution, overall enhancement, noise reduction, color enhancement, scratch removal, banding removal, detail enhancement, low-light enhancement, face enhancement, and text enhancement. These features are used for video quality remastering and significantly improve the subjective quality of audio and video. Audio enhancement includes audio noise reduction and volume equalization. Audio noise reduction removes background noise, highlighting vocals and other key audio elements, allowing listeners to focus on essential information. Volume equalization adjusts the overall loudness level of audio based on different playback environments and listener needs. In noisy environments, increasing the loudness ensures clear communication, while in quiet environments, lowering the loudness avoids causing disturbances.

Live audio and video enhancement features can be used individually or in combination to improve live stream video quality in different scenarios. Billing for audio and video enhancement is based on the enhancement features used and the resolution and frame rate of the enhanced live stream video. The specific billing rules are described below.

## Notes

- The default billing mode for live audio and video enhancement is daily pay-as-you-go.
- Starting from 00:00 on October 1, 2023, the billing for audio and video enhancement features will be calculated separately based on the enhancement features used and the resolution and frame rate of the enhanced live stream video. Billing will start on October 2.
- When you use video enhancement or combine video and audio enhancement features, it should be paired with Top Speed Codec (TSC) transcoding, which will incur [TSC transcoding](https://www.tencentcloud.com/document/product/267/39604) fees. TSC transcoding packages can offset the postpaid daily usage fees for TSC transcoding but cannot offset the postpaid daily usage fees for audio and video enhancement.
- When you use only the audio enhancement feature, it can be paired with either standard transcoding or TSC transcoding, which will incur [standard transcoding](https://www.tencentcloud.com/document/product/267/39604#.E6.A0.87.E5.87.86.E8.BD.AC.E7.A0.81) or [TSC transcoding](https://www.tencentcloud.com/document/product/267/39604#.E6.9E.81.E9.80.9F.E9.AB.98.E6.B8.85.E8.BD.AC.E7.A0.81) fees. Standard transcoding packages and TSC transcoding packages can offset their corresponding postpaid daily usage fees but cannot offset the postpaid daily usage fees for audio enhancement.

## Video Enhancement Feature Description

| Enhancement Feature | Description |
| --- | --- |
| SDR to HDR Conversion | Converts SDR videos to HDR and increases the color depth to up to 10 bits to represent a wider gamut and display more color details. |
| Frame Interpolation | Inserts additional video frames between the original live stream video frames, resulting in a smoother and more visually pleasing viewing experience. |
| Super Resolution | Offers high-resolution models (default) and low-resolution models. |
| Overall Enhancement | Uses AI-based analysis to improve the overall image quality by balancing image textures, removing compression artifacts, and enhancing key details. |
| Noise Reduction | Removes the random noise introduced from the camera and the environment during live streaming while maintaining audio/video details. |
| Color Enhancement | Restores video colors that may have been distorted due to camera or storage issues and enhances colors so they are more pleasing to viewers. |
| Scratch Removal | Repairs damages in live streaming video, such as scratches and snowflake-like spots, improving the overall quality of the video. |
| Banding (Artifact) Removal | Repairs distortions caused by repeated compressions of videos during transcoding, such as blocking artifacts, ringing artifacts, color contamination, and mosquito noise. |
| Detail Enhancement | Enhances key details in live streaming video to improve video clarity and provide a better viewing experience. |
| Low-Light Enhancement | Automatically recognizes scenes and adaptively enhances video images to increase details and contrast in dark areas and improve image quality, especially in low-light scenes. |
| Face Enhancement | Enhances key facial features with the help of face recognition technologies. |
| Text Enhancement | Improves the clarity and readability of the text shown during a live stream. |

## Audio Enhancement Feature Description

| Enhancement Feature | Description |
| --- | --- |
| Audio noise reduction | Audio noise reduction removes background noise, emphasizing vocals and other key audio elements, enabling listeners to focus on critical information. |
| Volume equalization | Volume equalization adjusts the overall loudness of audio based on playback environments and listener preferences. In noisy environments, it increases loudness for clear communication, while in quiet settings, it reduces loudness to avoid causing disturbances. |

### Pricing

##### SDR to HDR Conversion

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) |
| --- | --- | --- | --- |
| SDR to HDR Conversion | Unlimited | Unlimited | 0.0705 |

##### Frame Interpolation

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Frame Interpolation | 720P | 30fps | 0.1058 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.2116 |  |
|  |  | 120fps | 0.4233 |  |
|  | 1080P | 30fps | 0.2381 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.4762 |  |
|  |  | 120fps | 0.9524 |  |
|  | 2K | 30fps | 0.4233 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.8466 |  |
|  |  | 120fps | 1.6931 |  |
|  | 4K | 30fps | 0.9524 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 1.9048 |  |
|  |  | 120fps | 3.8095 |  |
|  | 8K | 30fps | 3.8095 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 7.619 |  |
|  |  | 120fps | 15.2381 |  |

##### Super Resolution

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Super Resolution | 720P | 30fps | 0.0529 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0882 |  |
|  |  | 120fps | 0.194 |  |
|  | 1080P | 30fps | 0.1058 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.2116 |  |
|  |  | 120fps | 0.4233 |  |
|  | 2K | 30fps | 0.194 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.3704 |  |
|  |  | 120fps | 0.7584 |  |
|  | 4K | 30fps | 0.4233 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.8466 |  |
|  |  | 120fps | 1.6931 |  |
|  | 8K | 30fps | 1.6931 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 3.3862 |  |
|  |  | 120fps | 6.7725 |  |

##### Overall Enhancement

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Overall Enhancement | 720P | 30fps | 0.1411 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.2822 |  |
|  |  | 120fps | 0.5644 |  |
|  | 1080P | 30fps | 0.3175 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.6349 |  |
|  |  | 120fps | 1.2698 |  |
|  | 2K | 30fps | 0.5644 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 1.1287 |  |
|  |  | 120fps | 2.2575 |  |
|  | 4K | 30fps | 1.2698 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 2.5397 |  |
|  |  | 120fps | 5.0794 |  |
|  | 8K | 30fps | 5.0794 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 10.1587 |  |
|  |  | 120fps | 20.3175 |  |

##### Noise Reduction

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Noise Reduction | 720P | 30fps | 0.0353 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0705 |  |
|  |  | 120fps | 0.1587 |  |
|  | 1080P | 30fps | 0.0882 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.1764 |  |
|  |  | 120fps | 0.3527 |  |
|  | 2K | 30fps | 0.1587 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.3175 |  |
|  |  | 120fps | 0.6349 |  |
|  | 4K | 30fps | 0.3527 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.7055 |  |
|  |  | 120fps | 1.4109 |  |
|  | 8K | 30fps | 1.4109 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 2.8219 |  |
|  |  | 120fps | 5.6437 |  |

##### Color Enhancement

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Color Enhancement | 720P | 30fps | 0.0176 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0353 |  |
|  |  | 120fps | 0.0705 |  |
|  | 1080P | 30fps | 0.0353 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.0705 |  |
|  |  | 120fps | 0.1411 |  |
|  | 2K | 30fps | 0.0705 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.1235 |  |
|  |  | 120fps | 0.2469 |  |
|  | 4K | 30fps | 0.1411 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.2822 |  |
|  |  | 120fps | 0.5644 |  |
|  | 8K | 30fps | 0.5644 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 1.1287 |  |
|  |  | 120fps | 2.2575 |  |

##### Scratch Removal

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Scratch Removal | 720P | 30fps | 0.1764 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.3527 |  |
|  |  | 120fps | 0.7231 |  |
|  | 1080P | 30fps | 0.4056 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.8113 |  |
|  |  | 120fps | 1.6226 |  |
|  | 2K | 30fps | 0.7231 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 1.4462 |  |
|  |  | 120fps | 2.8924 |  |
|  | 4K | 30fps | 1.6226 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 3.2451 |  |
|  |  | 120fps | 6.4903 |  |
|  | 8K | 30fps | 6.4903 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 12.9806 |  |
|  |  | 120fps | 25.9612 |  |

##### Banding Removal

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Banding Removal | 720P | 30fps | 0.0176 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0353 |  |
|  |  | 120fps | 0.0705 |  |
|  | 1080P | 30fps | 0.0353 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.0705 |  |
|  |  | 120fps | 0.1411 |  |
|  | 2K | 30fps | 0.0705 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.1235 |  |
|  |  | 120fps | 0.2469 |  |
|  | 4K | 30fps | 0.1411 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.2822 |  |
|  |  | 120fps | 0.5644 |  |
|  | 8K | 30fps | 0.5644 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 1.1287 |  |
|  |  | 120fps | 2.2575 |  |

##### Detail Enhancement

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Detail Enhancement | 720P | 30fps | 0.0071 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0159 |  |
|  |  | 120fps | 0.0317 |  |
|  | 1080P | 30fps | 0.0176 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.0353 |  |
|  |  | 120fps | 0.0705 |  |
|  | 2K | 30fps | 0.0317 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.0635 |  |
|  |  | 120fps | 0.1252 |  |
|  | 4K | 30fps | 0.0705 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.1411 |  |
|  |  | 120fps | 0.2822 |  |
|  | 8K | 30fps | 0.2822 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 0.5644 |  |
|  |  | 120fps | 1.1287 |  |

##### Low-Light Enhancement

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Low-Light Enhancement | 720P | 30fps | 0.0176 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.0353 |  |
|  |  | 120fps | 0.0705 |  |
|  | 1080P | 30fps | 0.0353 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.0705 |  |
|  |  | 120fps | 0.1411 |  |
|  | 2K | 30fps | 0.0705 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.1235 |  |
|  |  | 120fps | 0.2469 |  |
|  | 4K | 30fps | 0.1411 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 0.2822 |  |
|  |  | 120fps | 0.5644 |  |
|  | 8K | 30fps | 0.5644 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 1.1287 |  |
|  |  | 120fps | 2.2575 |  |

##### Face Enhancement

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Face Enhancement | 720P | 30fps | 0.1235 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.2293 |  |
|  |  | 120fps | 0.4762 |  |
|  | 1080P | 30fps | 0.2646 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.5291 |  |
|  |  | 120fps | 1.0582 |  |
|  | 2K | 30fps | 0.4762 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.9347 |  |
|  |  | 120fps | 1.8871 |  |
|  | 4K | 30fps | 1.0582 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 2.1164 |  |
|  |  | 120fps | 4.2328 |  |
|  | 8K | 30fps | 4.2328 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 8.4656 |  |
|  |  | 120fps | 16.9312 |  |

##### Text Enhancement

| Enhancement Feature | Resolution | Frame Rate | Price (USD/Min) | Remarks (the long side is whichever dimension is longer) |
| --- | --- | --- | --- | --- |
| Text Enhancement | 720P | 30fps | 0.0705 | Long side ≤ 1280 and short side ≤ 720 |
|  |  | 60fps | 0.1235 |  |
|  |  | 120fps | 0.2469 |  |
|  | 1080P | 30fps | 0.1411 | Long side ≤ 1936 and short side ≤ 1088 |
|  |  | 60fps | 0.2646 |  |
|  |  | 120fps | 0.5291 |  |
|  | 2K | 30fps | 0.2469 | Long side ≤ 2560 and short side ≤ 1440 |
|  |  | 60fps | 0.4762 |  |
|  |  | 120fps | 0.9524 |  |
|  | 4K | 30fps | 0.5291 | Long side ≤ 4096 and short side ≤ 2160 |
|  |  | 60fps | 1.0582 |  |
|  |  | 120fps | 2.1164 |  |
|  | 8K | 30fps | 2.1164 | Long side > 4096 or short side > 2160 |
|  |  | 60fps | 4.2328 |  |
|  |  | 120fps | 8.4656 |  |

##### Audio Enhancement

| Enhancement Feature | Price (USD/min) |
| --- | --- |
| Audio noise reduction | 0.0176 |
| Volume equalization | 0.0176 |

### Billing Overview

- Billing Item: Live stream enhancement duration (prices vary based on enhancement features used and the resolution and frame rate of the enhanced video).
- Billing Rules: The default billing mode is daily pay-as-you-go. The fees are calculated based on the audio/video enhancement features used and the resolution and frame rate after enhancement. Your audio/video enhancement durations each natural day are multiplied by the corresponding unit prices.

### Billing formula

Live stream enhancement duration fee = audio/video enhancement duration × unit price of the corresponding enhancement feature (determined by resolution and frame rate).

## Billing Example

If you started a 100-minute live stream on October 1, 2023, using **Text Enhancement, Low-Light Enhancement** for video, and **Audio Noise Reduction** for audio, with the output stream transcoded using TSC transcoding in **H.264 format, 1080P resolution** , and  **30fps** , the live streaming audio and video enhancement bill for October 2, 2023, would be calculated as follows:

**TSC Transcoding** Fees: USD 0.0443/min x 100 min = USD 4.43

**Text Enhancement** Fees: USD 0.1411/min x 100 min = USD 14.11

**Low-Light Enhancement** Fees: USD 0.0353/min x 100 min = USD 3.53

**Audio noise reduction** Fees: USD 0.0176/min x 100 min = USD 1.76

> **Note:**If your live streaming business operates at a large scale and the daily billing method does not meet your needs, you can contact our sales team to negotiate customized billing methods and pricing. For more details, feel free to [submit a ticket](https://console.tencentcloud.com/workorder/category).


---
*Source: [https://www.tencentcloud.com/document/product/267/57045](https://www.tencentcloud.com/document/product/267/57045)*
