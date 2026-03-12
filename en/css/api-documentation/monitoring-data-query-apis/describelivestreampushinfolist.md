# DescribeLiveStreamPushInfoList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query the push information of all real-time streams, including client IP, server IP, frame rate, bitrate, domain name, and push start time.

A maximum of 500 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeLiveStreamPushInfoList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| PushDomain | No | String | Push domain name. |
| AppName | No | String | Push path, which is the same as the `AppName` in push and playback addresses and is `live` by default. |
| PageNum | No | Integer | Number of pages, Value range: [1,10000], Default value: 1. |
| PageSize | No | Integer | Number of entries per page, Value range: [1,1000], Default value: 200. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [PushDataInfo](https://www.tencentcloud.com/document/api/267/30767#PushDataInfo) | Live stream statistics list. |
| TotalNum | Integer | Total number of live streams. |
| TotalPage | Integer | Total number of pages. |
| PageNum | Integer | Page number where the current data resides. |
| PageSize | Integer | Number of live streams per page. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeLiveStreamPushInfoList
&PushDomain=5000.pushdomain.com
&AppName=live
&PageNum=1
&PageSize=1000
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "DataInfoList": [
            {
                "StreamName": "test1",
                "AppName": "live",
                "ClientIp": "127.0.0.1",
                "ServerIp": "127.0.0.1",
                "VideoFps": 100,
                "VideoSpeed": 100,
                "AudioFps": 40,
                "AudioSpeed": 40,
                "AsampleRate": 48000,
                "PushDomain": "5000.pushdomain.com",
                "BeginPushTime": "2019-02-01 00:00:00",
                "Acodec": "AAC",
                "Vcodec": "H264",
                "Resolution": "350*350",
                "MetaAudioSpeed": 22,
                "MetaFps": 30,
                "MetaVideoSpeed": 4885
            }
        ],
        "PageNum": 1,
        "PageSize": 1000,
        "TotalNum": 1,
        "TotalPage": 1,
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
| FailedOperation.HasNotLivingStream | No live stream. |
| FailedOperation.QueryUploadInfoFailed | Failed to query the upload information. |
| InternalError | Internal error. |
| InternalError.InvalidRequest | Invalid request. |
| InternalError.QueryProIspPlayInfoError | Failed to query the playback information by ISP and district. |
| InternalError.QueryUploadInfoFailed | Failed to query the upload information. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37303](https://www.tencentcloud.com/document/product/267/37303)*
