# DescribeTimeShiftRecordDetail

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query the time shifting details of a specific time period (up to 24 hours). You need to call `DescribeTimeShiftStreamList` first to get the request parameters of this API.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeTimeShiftRecordDetail. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/267/30763#region-list) supported by the product. This API only supports: ap-singapore, eu-frankfurt. |
| Domain | Yes | String | The push domain. |
| AppName | Yes | String | The push path. |
| StreamName | Yes | String | The stream name. |
| StartTime | Yes | Integer | The start time, which must be a Unix timestamp. |
| EndTime | Yes | Integer | The end time, which must be a Unix timestamp. |
| DomainGroup | No | String | The group the push domain belongs to. You don’t need to specify this parameter if the domain doesn’t belong to any group or the group name is an empty string. |
| TransCodeId | No | Integer | The transcoding template ID. You don’t need to specify this parameter if the transcoding template ID is `0`. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RecordList | Array of [TimeShiftRecord](https://www.tencentcloud.com/document/api/267/30767#TimeShiftRecord) | The number of sessions recorded. Note: This field may return null, indicating that no valid values can be obtained. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 DescribeTimeShiftRecordDetail

Queries time shifting details

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeTimeShiftRecordDetail
<Common Request Parameters>

{
    "Domain": "5000.live.push.com",
    "AppName": "live",
    "StreamName": "livetest",
    "StartTime": 1668064484,
    "EndTime": 1668064584,
    "DomainGroup": "",
    "TransCodeId": 330587
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "xxx",
        "RecordList": [
            {
                "Sid": "xxx",
                "StartTime": 1668064484,
                "EndTime": 1668064584
            }
        ]
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
| InternalError | Internal error. |
| InternalError.GetConfigError | Error getting the configuration. |
| InternalError.NetworkError | Internal network error. |
| InvalidParameter | Invalid parameter. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://www.tencentcloud.com/document/product/267/53720](https://www.tencentcloud.com/document/product/267/53720)*
