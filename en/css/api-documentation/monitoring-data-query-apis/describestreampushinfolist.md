# DescribeStreamPushInfoList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to get the push data of a stream, including the audio/video frame rate, bitrate, elapsed time, and codec.

A maximum of 40 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeStreamPushInfoList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| StreamName | Yes | String | The stream name. |
| StartTime | Yes | String | The start time of the request, supports data query for the last seven days, the gap between the start time and the end time cannot exceed three hours. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format, for details, see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| EndTime | Yes | String | The end time of the request, supports data query for the last seven days, the gap between the start time and the end time cannot exceed three hours. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format,for details,see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| PushDomain | No | String | The push domain. |
| AppName | No | String | The push path, which should be the same as `AppName` in the push and playback URL. The default value is `live`. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [PushQualityData](https://www.tencentcloud.com/document/api/267/30767#PushQualityData) | Returned data list. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeStreamPushInfoList
&StartTime=2019-06-21 12:00:00
&EndTime=2019-06-21 12:01:02
&StreamName=abcd
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "DataInfoList": [
            {
                "StreamParam": "xx",
                "ACodec": "AAC",
                "AppName": "live",
                "AudioFps": 43,
                "AudioRate": 131580,
                "AudioTs": 5004,
                "BeginPushTime": "2019-06-21 00:29:12.252",
                "ClientIp": "125.39.132.102",
                "LocalTs": 5000,
                "PushDomain": "123.livepush.myqcloud.com",
                "Resolution": "368*640",
                "Sequence": "10151483429474411508",
                "Time": "2019-06-21 01:10:39.87",
                "VCodec": "H264",
                "VideoFps": 24,
                "VideoRate": 701528,
                "VideoTs": 5032,
                "MateFps": 30,
                "MetaAudioRate": 22,
                "MetaVideoRate": 4885,
                "Bandwidth": 1.0,
                "Flux": 1.0
            }
        ],
        "RequestId": "8e50cdb5-56dc-408b-89b0-31818958d424"
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
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/36094](https://www.tencentcloud.com/document/product/267/36094)*
