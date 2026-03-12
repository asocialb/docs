# CreateAigcVideoTask

## 1. API Description

Domain name for API request: mps.intl.tencentcloudapi.com.

This API is used to create AI video generation tasks.

A maximum of 10 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/1041/33628).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: CreateAigcVideoTask. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: 2019-06-12. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). This parameter is not required for this API. |
| ModelName | No | String | Model name. Supported models:Hunyuan, Hailuo, Kling, Vidu, OS, GV. |
| ModelVersion | No | String | Specific version number of the model. By default, the system uses the supported stable version of the model.1. Hailuo: [02 and 2.3].2. Kling: [2.0, 2.1, 2.5, O1, and 2.6].3. Vidu: [q2, q2-pro, and q2-turbo].4. GV: [3.1].5. OS: [2.0]. |
| SceneType | No | String | Scenario for the generated video.Note: Not all models support scenarios.1. Kling supports motion control (motion_control).2. Mingmou supports landscape-to-portrait conversion (land2port).3. Vidu supports special effect templates (template_effect). |
| Prompt | No | String | Description of the generated video. (Note: A maximum of 2000 characters is supported.) This parameter is required when no reference image is specified. |
| NegativePrompt | No | String | Content you want to prevent the model from generating.Note: Not all models support this.For example:Top lighting and bright color.People and animals.Multiple vehicles and wind. |
| EnhancePrompt | No | Boolean | The default value is False, meaning the model follows instructions strictly. For better results with more nuanced prompts, set this parameter to True to automatically optimize the input prompt and improve generation quality. |
| ImageUrl | No | String | Image URL for video generation. The URL must be accessible from the public network.Note:1. The recommended image size is no more than 10 MB. Different models have different size limits.2. Supported image formats: JPEG and PNG.3. If the OS model is used, the input image dimension should be 1280x720 or 720x1280. |
| LastImageUrl | No | String | The model will generate a video using the image of this parameter as the ending frame.Models that support this parameter:1. GV. If the ending frame image is specified, ImageUrl is required as the starting frame.2. Kling. Version 2.1 supports starting and ending frames with a resolution of 1080P.3. Vidu. q2-pro and q2-turbo support starting and ending frames.Note:1. The recommended image size is no more than 10 MB. Different models have different limits.2. Supported image formats: JPEG and PNG. |
| ImageInfos.N | No | Array of [AigcVideoReferenceImageInfo](https://www.tencentcloud.com/document/api/1041/33690#AigcVideoReferenceImageInfo) | List of up to 3 asset images, used to describe the images the model should use for video generation.Model that supports multiple images:1. GV. If multiple images are specified, ImageUrl and LastImageUrl are unavailable.2. Vidu supports video generation with multiple reference images. The q2 model accepts 1 to 7 images. The ReferenceType in ImageInfos can be used to specify the subject ID for the input.Note:1. The image size cannot exceed 10 MB.2. Supported image formats: JPEG and PNG. |
| VideoInfos.N | No | Array of [AigcVideoReferenceVideoInfo](https://www.tencentcloud.com/document/api/1041/33690#AigcVideoReferenceVideoInfo) |  |
| Duration | No | Integer | Duration of the generated video.Note:1. Kling supports 5 and 10 seconds. Default value: 5 seconds.2. The std mode of Hailuo supports 6 and 10 seconds, and other modes support 6 seconds. Default value: 6 seconds.3. Vidu supports 1 to 10 seconds.4. GV supports 8 seconds. Default value: 8 seconds.5. OS supports 4, 8, and 12 seconds. Default value: 8 seconds. |
| ExtraParameters | No | [AigcVideoExtraParam](https://www.tencentcloud.com/document/api/1041/33690#AigcVideoExtraParam) | Additional parameters required. |
| StoreCosParam | No | [AigcStoreCosParam](https://www.tencentcloud.com/document/api/1041/33690#AigcStoreCosParam) | COS bucket information for the file result. Note: COS is required and the MPS_QcsRole role needs to be created and authorized. |
| AdditionalParameters | No | String | Special scenario parameters required by the model, formatted as a JSON serialized string.Example:{"camera_control":{"type":"simple"}} |
| Operator | No | String | API operator name. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | ID of the successfully created task. The task progress and generation results can be obtained by calling the query API. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Request Example

#### Input Example

```
POST / HTTP/1.1
Host: mps.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateAigcVideoTask
<Common request parameters>

{
    "ModelName": "GV",
    "Prompt": "move the picture",
    "NegativePrompt": "Top lighting,bright colors",
    "EnhancePrompt": false,
    "ImageUrl": "https://1500039689.vod-**.com/6cd2c44bvodcq1500039689/179cafb25145403699605999621/**oxE6jcA.png",
    "LastImageUrl": "https://aigc-**-image-1303333058.cos.ap-guangzhou.myqcloud.com/xxx_8655.png",
    "Duration": 8,
    "ExtraParameters": {
        "Resolution": "720P",
        "AspectRatio": "16:9"
    },
    "StoreCosParam": {
        "CosBucketName": "aigc-***-video-1**58",
        "CosBucketRegion": "ap-guangzhou",
        "CosBucketPath": "my_cos_file"
    },
    "Operator": "admin"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskId": "2147**3792",
        "RequestId": "643fb583-0032-44ac-bfa8-bef25e310998"
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

There is no error code related to the API business logic. For other error codes, please see [Common Error Codes](https://www.tencentcloud.com/document/api/1041/33691#common-error-codes).


---
*Source: [https://www.tencentcloud.com/document/product/1041/76487](https://www.tencentcloud.com/document/product/1041/76487)*
