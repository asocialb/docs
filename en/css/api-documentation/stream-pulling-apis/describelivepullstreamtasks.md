# DescribeLivePullStreamTasks

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query the stream pulling tasks created by `CreateLivePullStreamTask`.
The tasks returned are sorted by last updated time in descending order.

A maximum of 30 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeLivePullStreamTasks. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/267/30763#region-list) supported by the product. This API only supports: ap-bangkok, ap-beijing, ap-guangzhou, ap-hongkong, ap-mumbai, ap-seoul, ap-shanghai, ap-singapore, ap-tokyo, eu-frankfurt, na-ashburn, na-siliconvalley. |
| TaskId | No | String | The task ID. |
| PageNum | No | Integer | The number of page to start from. Default value: 1. |
| PageSize | No | Integer | The maximum number of records per page. Default value: 10. Valid values: Any integer between 1 and 20. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskInfos | Array of [PullStreamTaskInfo](https://www.tencentcloud.com/document/api/267/30767#PullStreamTaskInfo) | The information of stream pulling tasks. |
| PageNum | Integer | The page number. |
| PageSize | Integer | The number of records per page. |
| TotalNum | Integer | The total number of records. |
| TotalPage | Integer | The total number of pages. |
| LimitTaskNum | Integer | The maximum number of tasks allowed. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeLivePullStreamTasks
<Common Request Parameters>

{
    "TaskId": "123"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskInfos": [
            {
                "AppName": "live",
                "Region": "ap-beijing",
                "CallbackInfo": "",
                "CallbackEvents": [
                    "TaskStart",
                    "TaskExit"
                ],
                "CallbackUrl": "",
                "CreateBy": "yourname",
                "DomainName": "yourdomain.com",
                "EndTime": "2020-04-25T00:30:00Z",
                "ErrorInfo": "",
                "PushArgs": "txsecret=7cbb8f382a21e8d2f6cd8098100d3b8e&txtime=5ea0450d",
                "SourceType": "PullLivePushLive",
                "SourceUrls": [
                    "http://yourdomain/live/test.flv"
                ],
                "StartTime": "2020-04-20T00:30:00Z",
                "Status": "enable",
                "StreamName": "teststream",
                "Comment": "xx",
                "TaskId": "10054",
                "UpdateBy": "",
                "UpdateTime": "2020-04-23T05:07:43Z",
                "CreateTime": "2020-04-20T05:07:43Z",
                "VodLoopTimes": -1,
                "VodRefreshType": "ImmediateNewSource",
                "VodLocalMode": 0,
                "BackupSourceType": "",
                "BackupSourceUrl": "",
                "WatermarkList": [],
                "RecentPullInfo": {
                    "FileUrl": "http://yourdomain/live/test.flv",
                    "OffsetTime": 95,
                    "LoopedTimes": 0,
                    "ReportTime": "2020-04-23T08:20:39Z"
                }
            }
        ],
        "PageNum": 1,
        "PageSize": 10,
        "TotalNum": 1,
        "TotalPage": 1,
        "LimitTaskNum": 20,
        "RequestId": "3c140219-cfe9-470e-b241-907877d6fb03"
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
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.UserNotExist | The CSS service has not been activated. |


---
*Source: [https://www.tencentcloud.com/document/product/267/48355](https://www.tencentcloud.com/document/product/267/48355)*
