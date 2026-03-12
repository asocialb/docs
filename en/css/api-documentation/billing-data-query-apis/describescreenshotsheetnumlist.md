# DescribeScreenShotSheetNumList

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

The API is used to query the number of screenshots as an LVB value-added service.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeScreenShotSheetNumList. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | Start time in UTC time in the format of `yyyy-mm-ddTHH:MM:SSZ`. |
| EndTime | Yes | String | End time in UTC time in the format of `yyyy-mm-ddTHH:MM:SSZ`. Data for the last year can be queried. |
| Zone | No | String | Region information. Valid values: Mainland, Oversea. The former is to query data within Mainland China, while the latter outside Mainland China. If this parameter is left empty, data of all regions will be queried. |
| PushDomains.N | No | Array of String | Push domain name (data at the domain name level after November 1, 2019 can be queried). |
| Granularity | No | String | Data granularity. There is a 1.5-hour delay in data reporting. Valid values: `Minute` (5-minute granularity; query period of up to 31 days); `Day` (1-day granularity based on UTC+8:00; query period of up to 186 days) |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [TimeValue](https://intl.cloud.tencent.com/document/api/267/30767#TimeValue) | Data information list. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DescribeScreenShotSheetNumList
&StartTime=2019-11-07T16:00:00Z
&EndTime=2019-11-09T15:59:00Z
&<Common request parameters>
```

#### Output Example

```
{
    "Response": {
        "DataInfoList": [
            {
                "Num": 39623970,
                "Time": "2019-11-07T16:00:00Z"
            },
            {
                "Num": 41876427,
                "Time": "2019-11-08T16:00:00Z"
            }
        ],
        "RequestId": "k54e3deb-f318-4147-8a68-3c959642f9ec"
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
| InternalError | Internal error. |
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37298](https://www.tencentcloud.com/document/product/267/37298)*
