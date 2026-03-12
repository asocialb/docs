# DescribeLiveTimeShiftBillInfoList

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query the time-shift video length, time-shift days, and total time-shift period of push domains. The data returned is on a five-minute basis. You can use it for reconciliation.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeLiveTimeShiftBillInfoList. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | The start time for query. You can query data from the past three months. The longest time period that can be queried is one month.  It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| EndTime | Yes | String | The end time for query. You can query data from the past three months. The longest time period that can be queried is one month.  It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| PushDomains.N | No | Array of String | The push domains to query. If you leave this empty, the time shifting billing data of all push domains will be returned. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [TimeShiftBillData](https://intl.cloud.tencent.com/document/api/267/30767#TimeShiftBillData) | The time shifting billing data. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeLiveTimeShiftBillInfoList
<Common request parameters>

{
    "PushDomains": [
        "start-push.elliotxing.com"
    ],
    "StartTime": "2022-05-06T00:30:00Z",
    "EndTime": "2022-05-06T12:30:00Z"
}
```

#### Output Example

```
{
    "Response": {
        "DataInfoList": [
            {
                "Domain": "x.com",
                "Duration": 1,
                "StoragePeriod": 1,
                "Time": "2022-05-06T10:30:00Z"
            },
            {
                "Domain": "x.com",
                "Duration": 1,
                "StoragePeriod": 1,
                "Time": "2022-05-06T10:35:00Z"
            }
        ],
        "RequestId": "ca0bb85f-6b95-4b9f-b85f-fdsafasds"
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
| FailedOperation.NotFound | No records found. |
| InternalError | Internal error. |
| InvalidParameter | Invalid parameter. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/47919](https://www.tencentcloud.com/document/product/267/47919)*
