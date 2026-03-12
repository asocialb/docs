# Audio/Video Transcoding Template

## Overview

You can preset different processing parameters for different application scenarios by configuring audio/video transcoding templates, so that they can be reused later.

- If you need to process video files, you can configure [video transcoding templates](#video), including general video transcoding templates, Top Speed Codec (TSC) transcoding templates, video adaptive bitrate streaming templates, and remuxing templates.
- If you need to process audio-only files, you can configure [audio transcoding templates](#audio), including general audio transcoding templates, TSC audio transcoding templates, and audio adaptive bitrate streaming templates.

For a brief introduction to each feature, refer to the table below:

| Applicable Input Source | Feature | Description |
| --- | --- | --- |
| Video | General transcoding | It can reduce the video bitrate and change the encoding standard, resolution, frame rate, and other parameters of the original bitstream, thus adapting to playback on different terminals and in different network environments. |
|  | TSC transcoding | TSC transcoding is an "upgrade" of General Transcoding. It can adaptively optimize different types of videos, providing users with a clearer viewing experience at lower bandwidth. While ensuring or even improving image quality, it can save bandwidth costs by 50%+. |
|  | Video adaptive bitrate streaming | It can convert the input original video file into multiple bitstreams suitable for playback in different scenarios, so that users can choose a video with an appropriate bitrate for playback based on their network, thereby enhancing user experiences. |
|  | Remuxing | It can change the container format of the original video file. |
| Audio | General audio transcoding | It can reduce the audio bitrate and change the encoding standard, sample rate, channel, and other parameters, thus adapting to playback on different terminals and in different network environments. |
|  | TSC audio transcoding | TSC audio transcoding is an "upgrade" of general audio transcoding. It can adaptively optimize different types of audio to provide users with a better audio experience with lower bandwidth. |
|  | Audio adaptive bitrate streaming | It can convert the input original audio file into multiple bitstreams suitable for playback in different scenarios, thereby adapting to different network conditions and enhancing user experiences. |

## Video Transcoding Templates

### 1. General Transcoding

MPS provides preset General Transcoding Templates, which can be used directly. You can also click [Create template](https://console.tencentcloud.com/mps/templates/avs?tab=video) to customize your own General Transcoding Templates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6eb8e10d8f8011ef9897525400d5f8ef.png)

#### **Table of Detailed Configuration Item Description**

| Item |  |  | Description |
| --- | --- | --- | --- |
| Template name | Max 64 characters; supports Chinese characters, letters, digits, spaces, underscores (_), hyphens (-), and periods |  | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods. |
| Container format |  |  | MP4, FLV, HLS, MXF, MOV, TS, WEBM, and MKV. |
| Configuration Item |  |  | Video parameters (required) and audio parameters (optional). |
| Segmentation Rules(configurable when the container format is HLS) | Multipart Format |  | TS, MP4. |
|  | Data Sharding |  | Segment File (segment), Single File (single-file).Note: Single File requires the server to support byte range requests. Not all HLS devices and players support a single file/byte range. |
|  | Average Segmentation Duration |  | The following two methods are supported:AutomaticCustom: Fill in the average segment duration (in s). |
|  | Segment Duration at Startup |  | This configuration item is disabled by default.Once it is enabled, you can set a special average duration for the first few segments of the video. For example, set the first segment to have a shorter duration than other segments to reduce video buffering time and improve user experiences. Enter an integer value greater than or equal to 1. |
|  | Number of Effected Segments |  | It is used to specify the number of the first few video segments to take effect when Segment Duration at Startup is enabled. Enter an integer value greater than or equal to 1. |
| Video Parameters | Encoding standard |  | H.264, H.264 intra, H.265, AV1, H.266, MV-HEVC, MPEG2, VP8, and VP9. |
|  | Resolution & Bitrate | Bitrate Control Mode | The following four bitrate control modes are supported:VBR (default): variable bitrate. The bitrate of the output is adjusted dynamically based on the complexity of video images, resulting in higher image quality. It is suitable for storage scenarios as well as applications requiring high image quality.ABR: average bitrate. The average bitrate of the output video is kept stable to the greatest extent, but short-term bitrate fluctuations are allowed. It is suitable for scenarios where minimizing the overall bitrate is required while a certain image quality is maintained.CBR: constant bitrate. The bitrate of the output is kept constant during the video encoding process without considering changes in image complexity. It is suitable for scenarios with strict network bandwidth requirements.CRF: constant quality factor. Video quality is controlled by setting a quality factor to achieve constant quality encoding of videos, with the bitrate adjusted automatically based on the complexity of the content. It is suitable for scenarios requiring stable image quality. |
|  |  | CRF Value | Video constant bitrate control factor, supporting the following two modes:Automatic: The CRF value is automatically selected.Custom: The range of the CRF value is 0 to 51, where 0 means lossless compression and 51 means maximum compression. The typically recommended value range is 18 to 28, where 18 represents a low compression ratio with high quality and 28 represents a high compression ratio with low quality.**Note:**When the bitrate control mode is set to VBR and the CRF value is configured, MPS will process the video in VBR mode according to the CRF value and the average bitrate upper limit, to balance the video quality, bitrate, transcoding efficiency, and file size.When the bitrate control mode is set to CRF, the average bitrate upper limit setting will be invalid, and encoding will be performed according to the CRF value.When the bitrate control mode is set to ABR or CBR, the CRF does not need to be set. |
|  |  | Proportional Compression Bitrate | Disabled (default).Enabled: The bitrate of the output video will be adjusted based on the input compression ratio. |
|  |  | Compression Ratio | It is used when Proportional Compression Bitrate is enabled. The compression ratio is an integer within the range of [0, 100]. |
|  |  | Recommended Settings | Select the desired output video quality, such as Standard Definition (SD), and the preset video bitrate, resolution, and audio bitrate will be automatically populated for you.Note: different encoding standards have varying recommended parameters. For more details, refer to the [Appendix](https://www.tencentcloud.com/document/product/1041/48784#fe61b9c0-463b-4857-97c9-188c6d0c2c71). |
|  |  | Average Bitrate | The following two modes are supported:No video bitrate limit is set.Custom: It is customized within the range of [128, 35000] (in Kbps). |
|  |  | Resolution | The following three modes are supported:Keep the original: The resolution is consistent with that of the source video.Scale: The image is scaled proportionally according to the long or short side (width or height), with a size range of [128, 4096] (in px).Custom: Both the long and short sides (width and height) can be scaled in custom proportion, with a size range of [128, 4096] (in px). |
|  |  | Display Aspect Ratio (SAR) | It is used when the resolution is set to Custom and the aspect ratio of the video differs from that of the source video. The sample aspect ratio (SAR) refers to the pixel aspect ratio of the video and is used to specify the shape of pixels. The following three modes are supported:Keep the origin (default)1 **:** 12 **:** 1 |
|  |  | Padding Rules | It is used when the resolution is set to Custom and the aspect ratio of the video differs from that of the source video. The following five modes are supported:Scale to fill: This will scale the video image to fill the entire display area, which may cause distortion.Black bars: (default) Black bars are added around the video to maintain the original aspect ratio, which may waste some display space.White bars: It is similar to the mode of black bars, but white bars are added on the top and bottom/left and right sides of the video.Gaussian Blur: Applies a Gaussian Blur effect to the stretched or filled areas to reduce visual discomfort.Intelligent cropping: The video image to be retained is intelligently selected at the time of video cropping. |
|  | Frame Rate |  | The following two video frame rate setting modes are supported:Keep the original: The frame rate is consistent with that of the source video.Custom: The frame rate is customized within the range of [1, 120] (in FPS). If the set value exceeds the source frame rate, duplicate frames will be inserted to make up for it. |
|  | GOP | Same Origin of GOP Structure | Disabled (default).Enabled: The GOP is consistent with that of the source file. Once it is enabled, no other GOP parameters need to be set. |
|  |  | GOP Length | The following two modes are supported:AutomaticCustom: Enter an integer number of frames or duration (in seconds). |
|  |  | Adaptive I-Frame Decision | Disabled (default).Enabled: MPS will automatically identify transition points between different scenarios in the video and adaptively insert keyframes (I-frames) at these points, thereby improving the video's random accessibility and encoding efficiency. |
|  |  | Max. Number of Consecutive B Frames | Supported options: Automatic, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, and 16.When the encoding standard is set to H.264 or H.265, it is recommended to select [Automatic] so that MPS can select the optimal number of B frames. |
|  |  | GOP Duration at Startup | Disabled (default).Enabled: It is used to set the GOP duration of the video at startup (in seconds). |
|  |  | GOP Quantity at Startup | It is used when GOP Duration at Startup is enabled.It is used to set the first x GOPs of the video to take effect at startup, where x is input by the user. |
|  | More | Encoder Level | The default value is Automatic.If H.264 is selected as the encoding standard, the following options are supported: Automatic, 1, 1.1, 1.2, 1.3, 2, 2.1, 2.2, 3, 3.1, 3.2, 4, 4.1, 4.2, 5, and 5.1.If H.265 is selected as the encoding standard, the following options are supported: Automatic, 1, 2, 2.1, 3, 3.1, 4, 4.1, 5, 5.1, 5.2, 6, 6.1, 6.2, and 8.5.If H.266, MV-HEVC, or AV1 is selected as the encoding standard, this option is not available. |
|  |  | profile | This configuration item is available only when H.264 is selected as the encoding standard. Different profiles are suitable for different scenarios.Auto(default): Automatically select the most suitable profile.Baseline: Supports only I/P frames and non-interlaced scenarios, suitable for video calls and mobile videos.Main: The mainstream profile, providing I-frames, P-frames, and B-frames. It supports both non-interlaced and interlaced modes, mainly used in mainstream audio and video consumer products like video players and streaming media transmission devices.High: The highest encoding level, adding 8x8 prediction to Main Profile and supporting customized quantization, widely used in Blu-ray storage and high-definition television. |
|  |  | Bit | 8 (default) and 10 |
|  |  | Keep Original Timestamp | Disabled (default)Enabled |
| Audio Parameters | Audio Transcoding |  | Enabled: Audio transcoding parameters can be set.Disabled: The original audio is used. |
|  | Encoding standard |  | When the container format is MP4, the corresponding encoding standards are AAC and MP3.When the container format is FLV, the corresponding encoding standard is AAC.When the container format is HLS, the corresponding encoding standard is AAC.When the container format is MXF, the corresponding encoding standards are PCM16 and PCM24.When the container format is MOV, the corresponding encoding standards are AAC and MP3.When the container format is TS, the corresponding encoding standards are AAC and MP3.When the container format is WEBM, the corresponding encoding standard is Opus.When the container format is MKV, the corresponding encoding standards are AAC and Opus. |
|  | Sample rate |  | 7350, 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000, 64000, 88200, 96000, etc., in Hz. For more details, see [Appendix: Supported Audio Sample Rates](https://www.tencentcloud.com/document/product/1041/48784#audiosamplerate). |
|  | Bitrate |  | The following two modes are supported:Keep the originalCustom: It is customized within the range of [26, 256] (in Kbps). |
|  | Channel |  | Mono-channel, Dual-channel, Multichannel. |

### 2. TSC Transcoding

MPS provides preset TSC templates, which can be used directly. You can also click [Create template](https://console.tencentcloud.com/mps/templates/avs?tab=tehd) to customize your own TSC templates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c9e84e1eb62311ef8c01525400fdb830.png)

#### **Table of Detailed Configuration Item Description**

| Item |  |  | Description |
| --- | --- | --- | --- |
| Template name |  |  | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods. |
| Container format |  |  | MP4, FLV, HLS, MXF, MOV, TS, WEBM, and MKV. |
| Configuration Item |  |  | Video parameters (required) and audio parameters (optional). |
| Segmentation Rules | Multipart Format |  | Segmentation rules can be configured when the container format is HLS.For details, see the section [General Transcoding - Table of Detailed Configuration Item Description](#SegmentationRules) above. |
|  | Data Sharding |  |  |
|  | Average Segmentation Duration |  |  |
|  | Segment Duration at Startup |  |  |
|  | Number of Effected Segments |  |  |
| Video Parameters | Encoding standard |  | H.264, H.264 intra, H.265, AV1, H.266, MV-HEVC, MPEG2, VP8, and VP9. |
|  | Intelligent Scenario Configuration |  | Disabled (default)Enabled: Video scenarios and transcoding strategies applicable for the template parameter can be selected. MPS will intelligently adjust underlying processing parameters based on the selected scenarios and strategies to achieve better transcoding effects for different scenario characteristics. |
|  | Applicable video scenarios |  | MPS provides several preset video scenarios, with different processing modes configured to adapt to different scenario characteristics:General Transcoding Scenarios: General transcoding compression scenarios.PGC High-Definition Movie and TV Drama: The focus is on the viewing experience of movies and TV dramas at the time of compression. ROI encoding is applied based on the characteristics of movies and TV dramas, while high-quality video and audio contents are retained.High-Definition Material: This scenario involves material resource categories with extremely high requirements for picture quality and includes many transparent picture elements. The compression achieves almost visually lossless quality.User-Generated Content (UGC): It is suitable for a wide range of UGC/short video scenarios. It optimizes the encoding bitrate and image quality based on the characteristics of short videos and improves business QoS/QoE metrics.Showroom/e-commerce category: Emphasizes detail clarity and ROI area enhancement during compression, with particular attention to maintaining image quality in facial areas.Education Category: The emphasis is on the clarity and readability of text and images at the time of compression to help students better comprehend the content, ensuring the clear conveyance of instructional material. |
|  | Transcoding strategy |  | TSC transcoding supports the **Standard Compression** and **Extreme Compression** strategies. Different strategies have different underlying transcoding models, which will affect the bitrate, image quality, and other results.Standard Compression: Standard TSC transcoding, which provides three options:Low Compression - Image quality preferredMedium Compression - Comprehensive optimizationHigh Compression - Bitrate preferredFrom top to bottom, the higher the compression level, the smaller the output video file size, and the greater the image quality loss. Using any option of this strategy **only incurs TSC transcoding fees.**Extreme Compression: An "upgraded version" of standard compression, **with the highest compression level**, which maximizes the compression bitrate while ensuring a certain level of image quality, significantly saving bandwidth and storage costs. Using this strategy **incurs both TSC transcoding and audio/video enhancement - artifacts removal fees.** For details, see [Billing Description](https://www.tencentcloud.com/document/product/1041/49204#tsc-transcoding). **Note:**If the output video is intended for viewing on a TV, it is not recommended to use the extreme compression strategy. |
|  | Resolution & Bitrate | Bitrate Control Mode | *For details, see the section*[General Transcoding - Table of Detailed Configuration Item Description](#Resolution) *above.* |
|  |  | CRF Value |  |
|  |  | Proportional Compression Bitrate |  |
|  |  | Compression Ratio |  |
|  |  | Recommended Settings |  |
|  |  | Average Bitrate |  |
|  |  | Resolution |  |
|  |  | Display Aspect Ratio (SAR) |  |
|  |  | Padding Rules |  |
|  | Frame Rate |  | *For details, see the section*[General Transcoding - Table of Detailed Configuration Item Description](#FrameRate) *above.* |
|  | GOP | Same Origin of GOP Structure | *For details, see the section*[General Transcoding - Table of Detailed Configuration Item Description](#GOP)*above.* |
|  |  | GOP Length |  |
|  |  | Adaptive I-Frame Decision |  |
|  |  | Max. Number of Consecutive B Frames |  |
|  |  | GOP Duration at Startup |  |
|  |  | GOP Quantity at Startup |  |
|  | More | Encoder Level | *For details, see the section* [General Transcoding - Table of Detailed Configuration Item Description](#More) *above.* |
|  |  | profile |  |
|  |  | Bit |  |
|  |  | Keep Original Timestamp |  |
| Audio Parameters | Audio Transcoding |  | *For details, see the section* [General Transcoding - Table of Detailed Configuration Item Description](#AudioParameters) *above.* |
|  | Encoding standard |  |  |
|  | Sample rate |  |  |
|  | Bitrate |  |  |
|  | Channel |  |  |

### **3. Video Adaptive Bitrate Streaming Template**

MPS provides preset Video Adaptive Bitrate Streaming Templates, which can be used directly. You can also click [Create template](https://console.tencentcloud.com/mps/templates/avs?tab=ads) to customize your own Video Adaptive Bitrate Streaming Templates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/251f008eb62411ef8c01525400fdb830.png)

#### **Table of Detailed Configuration Item Description**

| Item |  |  | Description |
| --- | --- | --- | --- |
| Template Name |  |  | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods. |
| Template Description |  |  | Max 256 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods. |
| Packaging Format |  |  | HLS, MPEG-DASH. |
| Multipart Format (HLS Packaging Options) |  |  | MP4, MP4+Packed Audio, TS, TS+Packed Audio. |
| Data sharding (HLS Packaging Options) |  |  | Segment File (segment), Single File (single-file). |
| Resolution |  |  | Disallow low resolution video to high resolution conversionAllow low resolution video to high resolution conversion: Transcoding a low-resolution original video to high resolution does not directly enhance the image quality. If you desire to improve the quality effect of the video, you can use the [Audio and Video Enhancement](https://console.tencentcloud.com/mps/templates/enhs) feature. |
| Substream Information | Transcoding Type |  | You can select a transcoding type for each substream, supporting **General transcoding** or **TSC transcoding**. |
|  | Video Parameters | Encoding standard | H.264, H.265, AV1 ,MV-HEVC. |
|  |  | Intelligent Scenario Configuration | If the substream transcoding type is TSC transcoding, this configuration is supported.For configuration instructions, see the section [TSC Transcoding - Table of Detailed Configuration Item Description](#Intelligent) above. |
|  |  | Applicable video scenarios |  |
|  |  | Transcoding policy |  |
|  |  | Bitrate & Resolution | For details, see the section [General Transcoding - Table of Detailed Configuration Item Description](#Resolution) above. |
|  |  | Frame Rate | For details, see the section [General Transcoding - Table of Detailed Configuration Item Description](#FrameRate) above.**Note:**The frame rate configuration of each substream must be consistent. |
|  |  | GOP | For details, see the section [General Transcoding - Table of Detailed Configuration Item Description](#GOP) above.**Note:**The GOP configuration of each substream must be consistent. |
|  |  | More | For details, see the section [General Transcoding - Table of Detailed Configuration Item Description](#More) above. |
|  |  | Segmentation Rules | Segmentation rules can be configured when the container format is HLS.For details, see the section [General Transcoding - Table of Detailed Configuration Item Description](#SegmentationRules) above.**Note:**The segmentation rules for each substream are consistent by default. If needed, you can click **"Configure Different Rules"** to set distinct average segment durations and initial segment lengths for substreams.![](https://staticintl.cloudcachetci.com/cms/backend-cms/18ed8196b79711ef9448525400fdb830.png) |
|  | Audio Parameters | Basic | Audio Transcoding, Encoding standard, Sample rate, Bitrate, Channel.*For details, see the section* [General Transcoding - Table of Detailed Configuration Item Description](https://www.tencentcloud.com/document/product/1041/48784#AudioParameters) *above.* |
|  |  | More | Prerequisite: when the container format is HLS, this setting can be configured.More: when the output audio tracks and sound channels do not have a complete one-to-one correspondence with the input ones, this advanced setting can be used to adjust or mix the input audio tracks/sound channels.After expanding, you can configure the **selector type**, **audio track serial number/sound channel serial number**, and **whether to enable manual mixing**. |
|  |  | Selector Type | If the input audio track has only one sound channel, select **audio track SN**. If the input audio track has multiple channels, select **audio track SN + sound channel SN**. |
|  |  | Audio Track SN | Fill in the specific audio track serial numbers to indicate which input audio tracks you need to use.The audio track SN corresponds to the stream index value of an audio track. It can be 0 or a positive integer. Multiple audio track SNs should be separated by commas and filled in according to output sound channel SNs. |
|  |  | Audio Track SN.Sound Channel SN | Fill in the specific audio track serial numbers and sound channel serial numbers to indicate which input audio tracks and sound channels you need to use.The integer parts represent audio track SNs, and the decimal parts represent sound channel SNs. The audio track SN is the stream index value of an audio track, which can be 0 or a positive integer. The decimal parts support a maximum of 2 decimal places, and the number should be in the range of 0 to 63. For example, for an audio track with a stream index value of 1, 1.0 represents the first sound channel of this audio track, and 1.1 represents the second sound channel of this audio track. Multiple values should be separated by commas, and the audio track SNs should follow the order of output sound channel SNs. |
|  |  | Manual Mixing | If manual mixing is not enabled, when you fill in the audio track SN, the system will sequentially use the filled audio tracks as the respective output sound channels of this output audio track in the order filled.If manual audio mix is not enabled, when you fill in the audio track SN.sound channel SN, the system will sequentially use the filled sound channels as the respective output sound channels of this output audio track in the order filled.Enable the feature of multi-audio track mixing and complete mixing settings based on multiple input audio tracks to meet the configuration requirements of output audio tracks. |
|  |  | Number of Input Channels | This number depends on the number of audio track SNs (or audio track/sound channel SNs) you have filled in. |
|  |  | Number of Output Channels | Select the number of output sound channels. |
|  |  | Mixing Details | Configure the output audio track's sound channels based on the input audio tracks. The matrix's row data represents the input audio tracks, and the matrix's column data represents each sound channel of the output audio tracks. For each sound channel of the output audio tracks, you can configure in the corresponding column, fill in which input audio tracks are mixed to form this sound channel, and fill in the decibel value for the mixing of input audio tracks. The value can be filled with a number between -60 and 6, supporting up to 3 decimal places. Among them, -60 represents mute, 0 represents maintaining the original volume, and the default value is -60.For instance, if the L(0) channel in the first column is a mix of the audio track in the first row and the second row with original volume, fill '0' in the first column's first and second row input boxes. |
|  | Add Audio Track |  | If you want to include multiple audio tracks in the output file and perform individual configuration for each track, you can do this through **Add Audio Track**.If **More** settings are not enabled and multiple audio tracks are not **added**, the number of audio tracks in the output will be consistent with the input. |

### 4. Remuxing Template

The system provides remuxing templates, which can be used directly. Currently, the system provides templates for transcoding to MP4 and HLS formats, with no support for custom remuxing templates.

#### System Preset Remuxing Template List

| Template Name | Template ID | Container Format |
| --- | --- | --- |
| Transformat-MP4 | 9 | MP4 |
| Transformat-HLS | 6 | HLS |

### Appendix: Recommended Settings

To accommodate varying requirements for video clarity, it is recommended that you configure the video bitrate, resolution, and audio bitrate according to the following suggested parameters. Please note:

- The recommended settings vary across different encoding standards. For instance, the suggested video bitrate under the H.265 encoding standard is generally 60% of that recommended for the H.264 encoding standard.
- Compared to standard video transcoding, ultra-high-definition rapid transcoding recommends a lower video bitrate configuration.

| Encoding standards | Recommended settings level | Resolution setting | **General Transcoding** | **TSC Transcoding** | Audio bitrate setting (Kbps) |
| --- | --- | --- | --- | --- | --- |
|  |  |  | Video bitrate setting (Kbps) |  |  |
| H.264H.264intraVP9 | SD | (Long side) Proportionally scaled * (Short side) 480 | 1200 | 720 | 64 |
|  | HD | (Long side) Proportionally scaled * (Short side) 720 | 2500 | 1500 | 96 |
|  | FHD | (Long side) Proportionally scaled * (Short side) 1080 | 6000 | 3600 |  |
|  | 2K | (Long side) Proportionally scaled * (Short side) 1440 | 8000 | 4800 | 128 |
|  | 4K | (Long side) Proportionally scaled * (Short side) 2160 | 20000 | 12000 |  |
| H.265 | SD | (Long side) Proportionally scaled * (Short side) 480 | 720 | 432 | 64 |
|  | HD | (Long side) Proportionally scaled * (Short side) 720 | 1500 | 900 | 96 |
|  | FHD | (Long side) Proportionally scaled * (Short side) 1080 | 3600 | 2160 |  |
|  | 2K | (Long side) Proportionally scaled * (Short side) 1440 | 4800 | 2880 | 128 |
|  | 4K | (Long side) Proportionally scaled * (Short side) 2160 | 12000 | 7200 |  |
| AV1 | SD | (Long side) Proportionally scaled * (Short side) 480 | 540 | 324 | 64 |
|  | HD | (Long side) Proportionally scaled * (Short side) 720 | 1125 | 675 | 96 |
|  | FHD | (Long side) Proportionally scaled * (Short side) 1080 | 2700 | 1620 |  |
|  | 2K | (Long side) Proportionally scaled * (Short side) 1440 | 3600 | 2160 | 128 |
|  | 4K | (Long side) Proportionally scaled * (Short side) 2160 | 9000 | 5400 |  |
| H.266 | SD | (Long side) Proportionally scaled * (Short side) 480 | 420 | 252 | 64 |
|  | HD | (Long side) Proportionally scaled * (Short side) 720 | 875 | 525 | 96 |
|  | FHD | (Long side) Proportionally scaled * (Short side) 1080 | 2100 | 1260 |  |
|  | 2K | (Long side) Proportionally scaled * (Short side) 1440 | 2800 | 1680 | 128 |
|  | 4K | (Long side) Proportionally scaled * (Short side) 2160 | 7000 | 4200 |  |
| MV-HEVC | FHD | (Long side) Proportionally scaled * (Short side) 1080 | 9000 | 5400 | 96 |
|  | 2K | (Long side) Proportionally scaled * (Short side) 1440 | 12000 | 7200 | 128 |
|  | 4K | (Long side) Proportionally scaled * (Short side) 2160 | 30000 | 18000 |  |
|  | 8K | (Long side) Proportionally scaled * (Short side) 4320 | 75000 | 45000 | 256 |
| MPEG2 | SD | (Long side) Proportionally scaled * (Short side) 480 | 1800 | 1080 | 64 |
|  | HD | (Long side) Proportionally scaled * (Short side) 720 | 3750 | 2250 | 96 |
|  | FHD | (Long side) Proportionally scaled * (Short side) 1080 | 9000 | 5400 |  |
|  | 2K | (Long side) Proportionally scaled * (Short side) 1440 | 12000 | 7200 | 128 |
|  | 4K | (Long side) Proportionally scaled * (Short side) 2160 | 30000 | 18000 |  |
| VP8 | SD | (Long side) Proportionally scaled * (Short side) 480 | 1560 | 936 | 64 |
|  | HD | (Long side) Proportionally scaled * (Short side) 720 | 3250 | 1950 | 96 |
|  | FHD | (Long side) Proportionally scaled * (Short side) 1080 | 7800 | 4680 |  |
|  | 2K | (Long side) Proportionally scaled * (Short side) 1440 | 10400 | 6240 | 128 |
|  | 4K | (Long side) Proportionally scaled * (Short side) 2160 | 26000 | 15600 |  |

## Audio Transcoding Templates

### 1. General Audio Transcoding Template

MPS provides preset General Audio Transcoding Templates, which can be used directly. You can also click [Create template](https://console.tencentcloud.com/mps/templates/avs?tab=audio) to customize your own General Audio Transcoding Templates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9b1b74db902211efb3eb525400bdab9d.png)

#### **Table of Detailed Configuration Item Description**

| Item | Description |
| --- | --- |
| Template Name | Support Chinese characters, letters, digits, underscores, hyphens, and dots, with a length of up to 64 chars. |
| Container Format | MP3, FLAC, OGG, M4A. |
| Audio Parameter Encoding Standard | When the container format is MP3, the corresponding encoding standard is MP3.When the container formats are FLAC and OGG, the corresponding encoding standard is FLAC.When the container format is M4A, the corresponding encoding standards are MP3, AAC, and AC3. |
| Sample Rate | Multiple sample rates such as 32000Hz, 44100Hz, and 48000Hz are supported. For more details, see [Appendix: Supported Audio Sample Rates](https://www.tencentcloud.com/document/product/1041/48784#audiosamplerate). |
| Bitrate (Audio Bitrate) | The audio bitrate can be the same as that of the source file or be customized within the range of [26, 256] (in Kbps). |
| Sound Channel | Mono-channel, Dual-channel. |

Templates created are displayed in the [General Audio Transcoding Template](https://console.tencentcloud.com/mps/templates/avs?tab=audio) list. You can view, edit, or delete custom templates, but preset templates can be viewed only, not edited or deleted.

#### **System Preset General Audio Transcoding Template List**

| Template Name | Template ID | Format | Bitrate | Codec | SoundSystem | SampleRate |
| --- | --- | --- | --- | --- | --- | --- |
| Audio-M4A-24Kbps | 1100 | M4A | 24kbps | AAC | Stereo | 44100Hz |
| Audio-M4A-48Kbps | 1110 | M4A | 48kbps | AAC | Stereo | 44100Hz |
| Audio-M4A-96Kbps | 1120 | M4A | 96kbps | AAC | Stereo | 44100Hz |
| Audio-M4A-192Kbps | 1130 | M4A | 192kbps | AAC | Stereo | 44100Hz |
| Audio-M4A-256Kbps | 1140 | M4A | 256kbps | AAC | Stereo | 44100Hz |
| Audio-MP3-128Kbps | 1010 | MP3 | 128kbps | MP3 | Stereo | 44100Hz |
| Audio-MP3-320Kbps | 1020 | MP3 | 320kbps | MP3 | Stereo | 44100Hz |

### 2. TSC Audio Transcoding Template

MPS provides preset TSC Audio Transcoding Templates, which can be used directly. You can also click [Create template](https://console.tencentcloud.com/mps/templates/avs?tab=audio-tehd) to customize your own TSC Audio Transcoding Templates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/76200b78902611efb3eb525400bdab9d.png)

#### **Table of Detailed Configuration Item Description**

| Item | Description |
| --- | --- |
| Template Name | Support Chinese characters, letters, digits, underscores, hyphens, and dots, with a length of up to 64 chars. |
| Container Format | M4A |
| Audio Parameter Encoding Standard | AAC |
| Sample rate | Multiple sample rates such as 32000Hz, 44100Hz, and 48000Hz are supported. |
| Bitrate (Audio Bitrate) | The audio bitrate can be the same as that of the source file or be customized within the range of [26, 256] (in Kbps). |
| Sound Channel | Mono-channel, Dual-channel, Multichannel. |

Templates created are displayed in the [TSC Audio Transcoding Template](https://console.tencentcloud.com/mps/templates/avs?tab=audio-tehd) list. You can view, edit, or delete custom templates, but preset templates can be viewed only, not edited or deleted.

#### System Preset TSC Audio Transcoding Template List

| Template Name | Template ID | Container Format | Audio Bitrate | Codec | SoundSystem | Sample Rate |
| --- | --- | --- | --- | --- | --- | --- |
| TESHD-Audio-M4A-192Kbps | 100730 | M4A | 192kbps | AAC | Stereo | 44100Hz |
| TESHD-Audio-M4A-256Kbps | 100740 | M4A | 256kbps | AAC | Stereo | 44100Hz |

### 3. Audio Adaptive Bitrate Streaming Template

MPS provides preset Audio Adaptive Bitrate Streaming Templates, which can be used directly. You can also click [Create template](https://console.tencentcloud.com/mps/templates/avs?tab=ads-audio) to customize your own Audio Adaptive Bitrate Streaming Templates.

| Item |  | Description |
| --- | --- | --- |
| Template Name |  | Support Chinese characters, letters, digits, underscores, hyphens, and dots, with a length of up to 64 chars. |
| Template Description |  | The length cannot exceed 256 characters. |
| Packaging Format |  | HLS, MPEG-DASH. |
| Substream Information | Template | Substream parameters for **General Audio Transcoding** or **TSC Audio Transcoding** are selected. |
| Audio Parameters | Encoding standard | When the packaging format is HLS, the corresponding encoding standards are AAC and AC3.When the packaging format is MPEG-DASH, the corresponding encoding standards are AAC, MP3, FLAC, and AC3. |
|  | Sample rate | Multiple sample rates such as 32000Hz, 44100Hz, and 48000Hz are supported. |
|  | Audio Bitrate | The audio bitrate can be the same as that of the source file or be customized within the range of [26, 256] (in Kbps). |
|  | Channel | Mono-channel, Dual-channel, Multichannel. |
|  | More | Prerequisite: when the container format is HLS, this setting can be configured.More: when the output audio tracks and sound channels do not have a complete one-to-one correspondence with the input ones, this advanced setting can be used to adjust or mix the input audio tracks/sound channels.After expanding, you can configure the selector type, audio track serial number/sound channel serial number, and whether to enable manual mixing. |
|  | Selector Type | If the input audio track has only one sound channel, select audio track SN. If the input audio track has multiple channels, select audio track SN + sound channel SN. |
|  | Audio Track SN | Fill in the specific audio track serial numbers to indicate which input audio tracks you need to use.The audio track SN corresponds to the stream index value of an audio track. It can be 0 or a positive integer. Multiple audio track SNs should be separated by commas and filled in according to output sound channel SNs. |
|  | Audio Track SN.Sound Channel SN | Fill in the specific audio track serial numbers and sound channel serial numbers to indicate which input audio tracks and sound channels you need to use.The integer parts represent audio track SNs, and the decimal parts represent sound channel SNs. The audio track SN is the stream index value of an audio track, which can be 0 or a positive integer. The decimal parts support a maximum of 2 decimal places, and the number should be in the range of 0 to 63. For example, for an audio track with a stream index value of 1, 1.0 represents the first sound channel of this audio track, and 1.1 represents the second sound channel of this audio track. Multiple values should be separated by commas, and the audio track SNs should follow the order of output sound channel SNs. |
|  | Manual Mixing | If manual mixing is not enabled, when you fill in the audio track SN, the system will sequentially use the filled audio tracks as the respective output sound channels of this output audio track in the order filled.If manual audio mix is not enabled, when you fill in the audio track SN.sound channel SN, the system will sequentially use the filled sound channels as the respective output sound channels of this output audio track in the order filled.Enable the feature of multi-audio track mixing and complete mixing settings based on multiple input audio tracks to meet the configuration requirements of output audio tracks. |
|  | Number of Input Channels | This number depends on the number of audio track SNs (or audio track/sound channel SNs) you have filled in. |
|  | Number of Output Channels | Select the number of output sound channels. |
|  | Mixing Details | Configure the output audio track's sound channels based on the input audio tracks. The matrix's row data represents the input audio tracks, and the matrix's column data represents each sound channel of the output audio tracks. For each sound channel of the output audio tracks, you can configure in the corresponding column, fill in which input audio tracks are mixed to form this sound channel, and fill in the decibel value for the mixing of input audio tracks. The value can be filled with a number between -60 and 6, supporting up to 3 decimal places. Among them, -60 represents mute, 0 represents maintaining the original volume, and the default value is -60.For instance, if the L(0) channel in the first column is a mix of the audio track in the first row and the second row with original volume, fill '0' in the first column's first and second row input boxes. |
|  | Add Audio Track | If you want to include multiple audio tracks in the output file and perform individual configuration for each track, you can do this through Add Audio Track.If More settings are not enabled and multiple audio tracks are not added, the number of audio tracks in the output will be consistent with the input. |

Templates created are displayed in the [Audio Adaptive Bitrate Streaming Template](https://console.tencentcloud.com/mps/templates/avs?tab=ads-audio) list. You can view, edit, or delete custom templates, but preset templates can be viewed only, not edited or deleted.

#### System Preset Template List

| Template Name | Template ID | Packaging Format | Substreams | Substream details |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  |  |
|  |  |  |  | Transcoding Type | Audio Bitrate | Codec | SoundSystem | Sample Rate |
| Adaptive-PureAudio-HLS | 30 | HLS | 1 | Standard audio transcoding | Same as source audio | AAC | Stereo | 44100Hz |

## Appendix: Supported Audio Sample Rates

The supported audio sample rates vary according to different audio encoding standards, as detailed in the table below:

| Audio Encoding Standard | AAC | MP3 | Opus | PCM16 | PCM24 | FLAC | AC3 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Supported Audio Sample Rates | 7350Hz8000Hz11025Hz12000Hz16000Hz22050Hz24000Hz32000Hz44100Hz48000Hz64000Hz88200Hz96000Hz | 8000Hz11025Hz12000Hz16000Hz22050Hz24000Hz32000Hz44100Hz48000Hz | 8000Hz12000Hz16000Hz24000Hz48000Hz | 48000Hz | 48000Hz | 8000Hz16000Hz22050Hz24000Hz32000Hz44100Hz48000Hz88200Hz96000Hz176400Hz192000Hz | 32000Hz44100Hz48000Hz |

> **Note：**When using the TSC Audio Transcoding feature with AAC audio encoding standard, the following audio sample rates are **unavailable**:7350Hz8000Hz11025Hz12000Hz


---
*Source: [https://www.tencentcloud.com/document/product/1041/48784](https://www.tencentcloud.com/document/product/1041/48784)*
