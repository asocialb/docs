# DescribeDeliverBandwidthList

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query the billable bandwidth of live stream relaying in the last 3 months. The query period is up to 31 days.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeDeliverBandwidthList. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | The start time of the request, supports data query for the last three months, the gap between the start time and the end time cannot exceed a month. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format, for details, see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| EndTime | Yes | String | The end time of the request, supports data query for the last three months, the gap between the start time and the end time cannot exceed a month. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format,for details,see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [BandwidthInfo](https://intl.cloud.tencent.com/document/api/267/30767#BandwidthInfo) | Billable bandwidth of live stream relaying. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DescribeDeliverBandwidthList
&StartTime=2020-01-07 21:10:00
&EndTime=2020-01-07 21:15:00
&<Common request parameters>
```

#### Output Example

```
{
    "Response": {
        "DataInfoList": [
            {
                "Bandwidth": 45927.6,
                "Time": "2020-05-01 00:00:00"
            },
            {
                "Bandwidth": 44494.84,
                "Time": "2020-05-01 00:05:00"
            },
            {
                "Bandwidth": 43061.09,
                "Time": "2020-05-01 00:10:00"
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
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37836](https://www.tencentcloud.com/document/product/267/37836)*
