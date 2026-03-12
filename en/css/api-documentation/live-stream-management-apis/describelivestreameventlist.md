# DescribeLiveStreamEventList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query stream push/interruption events.

Notes:

This API is used to query stream push/interruption records, and should not be relied too much upon in important business scenarios.
You can use the
IsFilter
parameter of this API to filter and get required push records.

A maximum of 300 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeLiveStreamEventList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | Start time. |
| EndTime | Yes | String | End time. In UTC format, such as 2018-12-29T20:00:00Z. This cannot be after the current time and cannot be more than 30 days after the start time. |
| AppName | No | String | Push path, which is the same as the AppName in push and playback addresses and is "live" by default. |
| DomainName | No | String | Push domain name. |
| StreamName | No | String | Stream name; query with wildcard (*) is not supported; fuzzy match by default. The IsStrict field can be used to change to exact query. |
| PageNum | No | Integer | Page number to get. Default value: 1. Note: Currently, query for up to 10,000 entries is supported. |
| PageSize | No | Integer | Number of entries per page. Maximum value: 100. Value range: any integer between 1 and 100. Default value: 10. Note: currently, query for up to 10,000 entries is supported. |
| IsFilter | No | Integer | Whether to filter. No filtering by default. 0: No filtering at all. 1: Filter out the failing streams and return only the successful ones. |
| IsStrict | No | Integer | Whether to query exactly. Fuzzy match by default. 0: Fuzzy match. 1: Exact query. Note: This parameter takes effect when StreamName is used. |
| IsAsc | No | Integer | Whether to display in ascending order by end time. Descending order by default. 0: Descending. 1: Ascending. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| EventList | Array of [StreamEventInfo](https://www.tencentcloud.com/document/api/267/30767#StreamEventInfo) | List of streaming events. |
| PageNum | Integer | Page number. |
| PageSize | Integer | Number of entries per page. |
| TotalNum | Integer | Total number of eligible ones. |
| TotalPage | Integer | Total number of pages. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeLiveStreamEventList
&DomainName=yourdomain.test.com
&AppName=live
&StreamName=stream
&StartTime=2019-01-04T12:00:00Z
&EndTime=2019-01-04T20:00:00Z
&PageNum=1
&PageSize=10
&IsFilter=1
&IsStrict=0
&IsAsc=0
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "EventList": [
            {
                "AppName": "live",
                "ClientIp": "180.163.8.244",
                "DomainName": "yourdomain.test.com",
                "Duration": 0,
                "Resolution": "640*352",
                "StopReason": "The client interrupted the stream",
                "StreamEndTime": "2019-01-04T11:59:58Z",
                "StreamName": "stream",
                "StreamStartTime": "2019-01-04T11:59:58Z"
            }
        ],
        "PageNum": 1,
        "PageSize": 10,
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
| FailedOperation | Operation failed. |
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| InternalError | Internal error. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.UserNotExist | The CSS service has not been activated. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30800](https://www.tencentcloud.com/document/product/267/30800)*
