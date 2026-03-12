# DescribeLiveTranscodeTotalInfo

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query transcoding usage. You can use it to query data in the past three months.
Notes:
If the start time and end time are on the same day, the data returned will be on a 5-minute basis.
If the start time and end time are not on the same day or if the data of specified domains is queried, the data returned will be on an hourly basis.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeLiveTranscodeTotalInfo. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | The start time of the request, supports data query for the last three months, the gap between the start time and the end time cannot exceed three months. Interface request supports two time formats: |
| EndTime | Yes | String | The end time of the request, supports data query for the last three months, the gap between the start time and the end time cannot exceed three months. Interface request supports two time formats: |
| PushDomains.N | No | Array of String | List of push domains to query. If this parameter is left empty, the data of all domains is queried. If this parameter is specified, the data returned will be on an hourly basis. |
| MainlandOrOversea | No | String | Valid values: `Mainland`: queries transcoding data in the Chinese mainland `Oversea`: queries transcoding data outside the Chinese mainland By default, the data both in and outside the Chinese mainland is queried. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [TranscodeTotalInfo](https://intl.cloud.tencent.com/document/api/267/30767#TranscodeTotalInfo) | List of transcoding data Note: This field may return `null`, indicating that no valid value can be found. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeLiveTranscodeTotalInfo
<Common request parameters>

{
    "EndTime": "2019-03-01 12:00:00",
    "StartTime": "2019-03-01 00:00:00"
}
```

#### Output Example

```
{
    "Response": {
        "DataInfoList": [
            {
                "Time": "2019-03-01 00:00:00",
                "Duration": 100,
                "ModuleCodec": "",
                "Resolution": "540*480"
            }
        ],
        "RequestId": "c8465603-c3a6-44bc-8354-a9b67bf44301"
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://intl.cloud.tencent.com/document/api/267/30851#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation | Operation failed. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://www.tencentcloud.com/document/product/267/44907](https://www.tencentcloud.com/document/product/267/44907)*
