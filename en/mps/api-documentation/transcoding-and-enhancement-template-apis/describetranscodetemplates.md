# DescribeTranscodeTemplates

## 1. API Description

Domain name for API request: mps.intl.tencentcloudapi.com.

This API is used to get the list of transcoding templates based on unique template ID. The return result includes all eligible custom and [preset transcoding templates](https://intl.cloud.tencent.com/document/product/266/33476?from_cn_redirect=1#.E9.A2.84.E7.BD.AE.E8.BD.AC.E7.A0.81.E6.A8.A1.E6.9D.BF).

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/1041/33628).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: DescribeTranscodeTemplates. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: 2019-06-12. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). This parameter is not required for this API. |
| Definitions.N | No | Array of Integer | Unique ID filter of transcoding templates. Array length limit: 100. |
| Type | No | String | Template type filter. Valid values: Preset: Preset template;Custom: Custom template. |
| ContainerType | No | String | Container format filter. Valid values: Video: Video container format that can contain both video stream and audio stream;PureAudio: Audio container format that can contain only audio stream. |
| TEHDType | No | String | TESHD filter, which is used to filter common transcoding or ultra-fast HD transcoding templates. Valid values: Common: Common transcoding template;TEHD: TESHD template. |
| Offset | No | Integer | Paging offset. Default value: 0. |
| Limit | No | Integer | Number of returned entries. Default value: 10. Maximum value: 100. |
| TranscodeType | No | String | The template type (replacing `TEHDType`). Valid values: Common: Common transcoding templateTEHD: TESHD templateEnhance: Audio/Video enhancement template. This parameter is left empty by default, which indicates to return all types of templates. |
| Name | No | String | Filter condition for transcoding template identifiers, with a length limit of 64 characters. |
| SceneType | No | String | Video scenario. Optional values:  normal: General transcoding scenario: General transcoding and compression scenario.  pgc: PGC HD TV shows and movies: At the time of compression, focus is placed on the viewing experience of TV shows and movies and ROI encoding is performed according to their characteristics, while high-quality contents of videos and audio are retained.  materials_video: HD materials: Scenario involving material resources, where requirements for image quality are extremely high and there are many transparent images, with almost no visual loss during compression.  ugc: UGC content: It is suitable for a wide range of UGC/short video scenarios, with an optimized encoding bitrate for short video characteristics, improved image quality, and enhanced business QOS/QOE metrics.  e-commerce_video: Fashion show/e-commerce: At the time of compression, emphasis is placed on detail clarity and ROI enhancement, with a particular focus on maintaining the image quality of the face region.  educational_video: Education: At the time of compression, emphasis is placed on the clarity and readability of text and images to help students better understand the content, ensuring that the teaching content is clearly conveyed.  no_config: Not configured. |
| CompressType | No | String | Transcoding policy. Optional values:  ultra_compress: Extreme compression: Compared to standard compression, this policy can maximize bitrate compression while ensuring a certain level of image quality, thus greatly saving bandwidth and storage costs.  standard_compress: Comprehensively optimal: The compression ratio and image quality are balanced, and files are compressed as much as possible without a noticeable reduction in subjective image quality. Only audio and video TSC transcoding fees are charged for this policy.  high_compress: Bitrate priority: Priority is given to reducing file size, which may result in certain image quality loss. Only audio and video TSC transcoding fees are charged for this policy.  low_compress: Image quality priority: Priority is given to ensuring image quality, and the size of compressed files may be relatively large. Only audio and video TSC transcoding fees are charged for this policy.  no_config: Not configured. |
| EnhanceSceneType | No | String | Enhancement scenario configuration. Valid values: common: common enhancement parameters, which are basic optimization parameters suitable for various video types, enhancing overall image quality.AIGC: overall resolution enhancement. It uses AI technology to improve the overall video resolution and image clarity.short_play: enhance facial and subtitle details, emphasizing characters' facial expressions and subtitle clarity to improve the viewing experience.short_video: optimize complex and diverse image quality issues, tailoring quality enhancements for the complex scenarios such as short videos to address various visual issues.game: fix motion blur and enhance details, with a focus on enhancing the clarity of game details and restoring blurry areas during motions to make the image content during gaming clearer and richer.HD_movie_series: provide a smooth playback effect for UHD videos. Standard 4K HDR videos with an FPS of 60 are generated to meet the needs of broadcasting/OTT for UHD videos. Formats for broadcasting scenarios are supported.LQ_material: low-definition material/old video restoration. It enhances overall resolution, and solves issues of old videos, such as low resolution, blur, distortion, scratches, and color temperature due to their age.lecture: live shows, e-commerce, conferences, and lectures. It improves the face display effect and performs specific optimizations, including face region enhancement, noise reduction, and artifacts removal, for scenarios involving human explanation, such as live shows, e-commerce, conferences, and lectures. |
| EnhanceTranscodeType | No | String | Enhanced transcoding type. Valid values: Common: standard transcoding.TEHD-100: top speed codec video transcoding.TEHD-200: top speed codec audio transcoding. |
| EnhanceType | No | String | Enhancement type. Valid values: VideoEnhance: video enhancement only.AudioEnhance (audio enhancement only).VideoAudioEnhance: video and audio enhancement included. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TotalCount | Integer | Number of eligible entries. |
| TranscodeTemplateSet | Array of [TranscodeTemplate](https://www.tencentcloud.com/document/api/1041/33690#TranscodeTemplate) | List of transcoding template details. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Obtaining Transcoding Templates

This example shows you how to obtain transcoding templates.

#### Input Example

```
POST / HTTP/1.1
Host: mps.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeTranscodeTemplates
<Common request parameters>

{
    "Definitions": [
        100010
    ]
}
```

#### Output Example

```json
{
    "Response": {
        "TotalCount": 1,
        "TranscodeTemplateSet": [
            {
                "Definition": "100010",
                "Container": "mp4",
                "Name": "MP4-FLU",
                "Comment": "",
                "Type": "Preset",
                "RemoveVideo": 0,
                "RemoveAudio": 0,
                "VideoTemplate": {
                    "Codec": "libx264",
                    "Fps": 25,
                    "Bitrate": 400,
                    "ResolutionAdaptive": "open",
                    "Width": 0,
                    "Height": 360,
                    "FillType": "stretch",
                    "Gop": 0,
                    "VideoProfile": "",
                    "VideoLevel": "",
                    "SegmentType": 0,
                    "FpsDenominator": 1,
                    "Stereo3dType": "",
                    "HlsTime": 0,
                    "Mode": "ABR",
                    "Sar": "",
                    "NoScenecut": 0,
                    "BitDepth": 8,
                    "RawPts": 0,
                    "ScenarioBased": 0,
                    "SceneType": "",
                    "CompressType": ""
                },
                "AudioTemplate": {
                    "Codec": "libfdk_aac",
                    "Bitrate": 64,
                    "SampleRate": 44100,
                    "AudioChannel": 2
                },
                "ContainerType": "Video",
                "CreateTime": "2020-03-04T07:39:36+08:00",
                "UpdateTime": "2024-09-27T17:33:53+08:00",
                "TEHDConfig": null,
                "EnhanceConfig": null,
                "AliasName": ""
            }
        ],
        "RequestId": "817e02a2-abcd-efgh-a2c8-d32169733eaa"
    }
}
```

## 5. Developer Resources

### SDK

TencentCloud API 3.0 integrates SDKs that support various programming languages to make it easier for you to call APIs.

Tencent Cloud SDK 3.0 for Python
Tencent Cloud SDK 3.0 for Java
Tencent Cloud SDK 3.0 for PHP
Tencent Cloud SDK 3.0 for Go
Tencent Cloud SDK 3.0 for Node.js
Tencent Cloud SDK 3.0 for .NET
Tencent Cloud SDK 3.0 for C++

### Command Line Interface

Tencent Cloud CLI 3.0

## 6. Error Code

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/1041/33691#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation.InvalidMpsUser | Operation failed: unauthorized MPS user. |
| InternalError | Internal error. |
| InternalError.AccessDBError | Data error. |
| InvalidParameterValue | Incorrect parameter value. |
| InvalidParameterValue.ContainerType | Incorrect parameter value: ContainerType. |
| InvalidParameterValue.Definitions | Parameter error: Definitions. |
| InvalidParameterValue.Limit | Parameter error: Limit. |
| InvalidParameterValue.TEHDType | Incorrect parameter value: invalid `TEHD Type` . |
| InvalidParameterValue.Type | Parameter error: incorrect `Type` value. |
| ResourceNotFound.TemplateNotExist | The resource does not exist: the template does not exist. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33655](https://www.tencentcloud.com/document/product/1041/33655)*
