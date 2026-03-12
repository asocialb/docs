# DescribeUploadStreamNums

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query the number of LVB upstream channels.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeUploadStreamNums. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | The start time of the request, supports data query for the last one month, the gap between the start time and the end time cannot exceed one month. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format, for details, see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| EndTime | Yes | String | The end time of the request, supports data query for the last one month, the gap between the start time and the end time cannot exceed one month. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format,for details,see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| Domains.N | No | Array of String | LVB domain names. If this parameter is left empty, data of all domain names will be queried. |
| Granularity | No | Integer | Time granularity of the data. Valid values: 5: 5-minute granularity (the query period is up to 1 day) 1440: 1-day granularity (the query period is up to 1 month) Default value: 5 |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [ConcurrentRecordStreamNum](https://intl.cloud.tencent.com/document/api/267/30767#ConcurrentRecordStreamNum) | Detailed data. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeUploadStreamNums
<Common request parameters>

{
    "StartTime": "2020-10-12 00:00:00",
    "EndTime": "2020-10-12 01:01:05",
    "Granularity": 5,
    "Domains": [
        "test.com"
    ]
}
```

#### Output Example

```
{
    "Response": {
        "DataInfoList": [
            {
                "Num": 2557,
                "Time": "2020-10-12 00:00:00"
            },
            {
                "Num": 2544,
                "Time": "2020-10-12 00:05:00"
            },
            {
                "Num": 2516,
                "Time": "2020-10-12 00:10:00"
            },
            {
                "Num": 2542,
                "Time": "2020-10-12 00:15:00"
            },
            {
                "Num": 2546,
                "Time": "2020-10-12 00:20:00"
            },
            {
                "Num": 2565,
                "Time": "2020-10-12 00:25:00"
            },
            {
                "Num": 2557,
                "Time": "2020-10-12 00:30:00"
            },
            {
                "Num": 2558,
                "Time": "2020-10-12 00:35:00"
            },
            {
                "Num": 2545,
                "Time": "2020-10-12 00:40:00"
            },
            {
                "Num": 2567,
                "Time": "2020-10-12 00:45:00"
            },
            {
                "Num": 2584,
                "Time": "2020-10-12 00:50:00"
            },
            {
                "Num": 2585,
                "Time": "2020-10-12 00:55:00"
            },
            {
                "Num": 2566,
                "Time": "2020-10-12 01:00:00"
            }
        ],
        "RequestId": "f54e3deb-f318-4148-8a68-3c959642f9ec"
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


---
*Source: [https://www.tencentcloud.com/document/product/267/39500](https://www.tencentcloud.com/document/product/267/39500)*
