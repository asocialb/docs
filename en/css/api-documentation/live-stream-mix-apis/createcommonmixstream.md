# CreateCommonMixStream

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to create a general stream mix. It can be used basically in the same way as the legacy `mix_streamv2.start_mix_stream_advanced` API.
Note: currently, up to 16 streams can be mixed.
Best practice: https://intl.cloud.tencent.com/document/product/267/45566?from_cn_redirect=1

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: CreateCommonMixStream. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| MixStreamSessionId | Yes | String | ID of a stream mix session (from applying for the stream mix to cancelling it). This parameter can contain up to 80 bytes of letters, digits, and underscores. |
| InputStreamList.N | Yes | Array of [CommonMixInputParam](https://www.tencentcloud.com/document/api/267/30767#CommonMixInputParam) | Input stream list for stream mix. |
| OutputParams | Yes | [CommonMixOutputParams](https://www.tencentcloud.com/document/api/267/30767#CommonMixOutputParams) | Output stream parameter for stream mix. |
| MixStreamTemplateId | No | Integer | Input template ID. If this parameter is set, the output will be generated according to the default template layout, and there is no need to enter the custom position parameters. |
| ControlParams | No | [CommonMixControlParams](https://www.tencentcloud.com/document/api/267/30767#CommonMixControlParams) | Special control parameter for stream mix. If there are no special needs, leave it empty. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Applying for stream mix — using template 40

This example shows you how to use a preset stream mix template to mix streams.

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateCommonMixStream
<Common request parameters>

{
    "MixStreamTemplateId": 40,
    "MixStreamSessionId": "test_room",
    "InputStreamList": [
        {
            "LayoutParams": {
                "ImageLayer": 1
            },
            "InputStreamName": "test_stream1"
        },
        {
            "LayoutParams": {
                "ImageLayer": 2
            },
            "InputStreamName": "test_stream2"
        }
    ],
    "OutputParams": {
        "OutputStreamName": "test_stream1"
    }
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "3c140219-cfe9-470e-b241-907877d6fb03"
    }
}
```

### Example2 Applying for stream mix — using custom layout parameters

This example shows you how to use a custom layout.

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateCommonMixStream
<Common request parameters>

{
    "InputStreamList": [
        {
            "LayoutParams": {
                "ImageLayer": 1,
                "ImageHeight": 720,
                "ImageWidth": 1280
            },
            "InputStreamName": "test_stream1"
        },
        {
            "LayoutParams": {
                "ImageLayer": 2,
                "ImageHeight": 320,
                "ImageWidth": 240,
                "LocationX": 100,
                "LocationY": 100
            },
            "InputStreamName": "test_stream2"
        }
    ],
    "OutputParams": {
        "OutputStreamName": "test_stream1"
    },
    "MixStreamSessionId": "test_room"
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "3c140219-cfe9-470e-b241-907877d6fb03"
    }
}
```

### Example3 Applying for stream mix — using cropping parameters

This example shows you how to use cropping parameters.

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateCommonMixStream
<Common request parameters>

{
    "InputStreamList": [
        {
            "LayoutParams": {
                "ImageLayer": 1,
                "ImageHeight": 720,
                "ImageWidth": 1280
            },
            "InputStreamName": "test_stream1"
        },
        {
            "LayoutParams": {
                "ImageLayer": 2,
                "ImageHeight": 320,
                "ImageWidth": 240,
                "LocationX": 100,
                "LocationY": 100
            },
            "InputStreamName": "test_stream2",
            "CropParams": {
                "CropWidth": 240,
                "CropHeight": 320,
                "CropStartLocationX": 100,
                "CropStartLocationY": 100
            }
        }
    ],
    "OutputParams": {
        "OutputStreamName": "test_stream1"
    },
    "MixStreamSessionId": "test_room"
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "3c140219-cfe9-470e-b241-907877d6fb03"
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/267/30851#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation | Operation failed. |
| FailedOperation.CallOtherSvrError | Failed to call the third-party service. |
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| FailedOperation.CancelSessionNotExist | The canceled stream mix session does not exist. |
| FailedOperation.GetPictureUrlError | Unable to get the watermark URL. |
| FailedOperation.GetStreamResolutionError | Failed to get the input stream length and width. |
| FailedOperation.ProcessMixError | Failed to start stream mix. |
| FailedOperation.StreamNotExist | The stream does not exist. |
| InternalError | Internal error. |
| InternalError.JiFeiOtherError | The billing platform returned other errors. |
| InvalidParameter | Invalid parameter. |
| InvalidParameter.CancelSessionNotExist | The canceled session does not exist. |
| InvalidParameter.InputNumLimitExceeded | The number of inputs exceeds the limit. |
| InvalidParameter.InvalidBackgroudResolution | Invalid background length and width. |
| InvalidParameter.InvalidBitrate | Invalid output bitrate. |
| InvalidParameter.InvalidCropParam | The cropped area overflows the original image. |
| InvalidParameter.InvalidLayerParam | Invalid layer parameter. |
| InvalidParameter.InvalidOutputStreamID | The output stream ID is already used. |
| InvalidParameter.InvalidOutputType | Invalid output type. Please check whether `OutputPram-StreamId` and `OutputType` match. |
| InvalidParameter.InvalidPictureID | The watermark ID was not set. |
| InvalidParameter.InvalidRoundRectRadius | Invalid corner radius of the rounded rectangle. |
| InvalidParameter.OtherError | Other errors. |
| InvalidParameter.SessionOutputStreamChanged | The output stream of the same session has changed. |
| InvalidParameter.TemplateNotMatchInputNum | The template does not match the number of input streams. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/35997](https://www.tencentcloud.com/document/product/267/35997)*
