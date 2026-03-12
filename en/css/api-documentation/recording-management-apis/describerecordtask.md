# DescribeRecordTask

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to retrieve a list of recording tasks that were started and ended within a specified time range.

Prerequisites:
This API is only used to query recording tasks created by the CreateRecordTask interface.
It cannot retrieve recording tasks that have been deleted by the DeleteRecordTask interface or tasks that have expired (platform retains for 3 months).

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeRecordTask. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/267/30763#region-list) supported by the product. This API only supports: ap-bangkok, ap-guangzhou, ap-hongkong, ap-jakarta, ap-mumbai, ap-seoul, ap-singapore, ap-tokyo, eu-frankfurt, na-ashburn, na-siliconvalley, na-toronto, sa-saopaulo. |
| StartTime | Yes | Integer | The start time of the tasks to retrieve in Unix timestamp. The time range should not be earlier than 90 days before the current time, and the query span should not exceed one week. |
| EndTime | Yes | Integer | The end time of the tasks to retrieve in Unix timestamp. The EndTime must be greater than the StartTime. The time range should not be earlier than 90 days before the current time, and the query span should not exceed one week. (Note: the start and end times of the task must be within the query time range). |
| StreamName | No | String | Stream name. |
| DomainName | No | String | Push domain name. |
| AppName | No | String | Push path. |
| ScrollToken | No | String | Page token used for batch retrieval: If a single request cannot retrieve all data, the interface will return a ScrollToken. The next request carrying this token will start retrieving from the next record. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| ScrollToken | String | Page token: When the request does not return all data, this field indicates the token of the next record. When this field is empty, it means there is no more data. |
| TaskList | Array of [RecordTask](https://www.tencentcloud.com/document/api/267/30767#RecordTask) | List of recording tasks. When this field is empty, it means all data has been returned. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeRecordTask
&AppName=live
&DomainName=5000.live.push.com
&StreamName=livetest
&StartTime=1595779200
&EndTime=1595865600
&<common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "eac6b301-a322-493a-8e36-83b295459397",
        "ScrollToken": "",
        "TaskList": [
            {
                "TaskId": "UpTbk5RSVhRQFkAAfHwQCCjcRD0lRFcZ0xTSlNTQltlRVRLU1JAWW9EUb",
                "DomainName": "5000.live.push.com",
                "AppName": "live",
                "StreamName": "livetest",
                "StartTime": 1595779900,
                "EndTime": 1595789900,
                "TemplateId": 123,
                "Stopped": 1595783500
            },
            {
                "TaskId": "UpTbk5RSVhRQFkAAfHwQCCjcRD0lRFcZ0xTSlNTQltlRVRLFszdDWW9EUb",
                "DomainName": "5000.live.push.com",
                "AppName": "live",
                "StreamName": "livetest",
                "StartTime": 1595789900,
                "EndTime": 1595799900,
                "TemplateId": 0,
                "Stopped": 0
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
*Source: [https://www.tencentcloud.com/document/product/267/56133](https://www.tencentcloud.com/document/product/267/56133)*
