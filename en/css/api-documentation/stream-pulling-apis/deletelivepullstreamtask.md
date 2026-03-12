# DeleteLivePullStreamTask

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to delete a task created by `CreateLivePullStreamTask`.
Notes:

For the
TaskId
request parameter, pass in the task ID returned by the
CreateLivePullStreamTask
API.
You can query the ID of a task using the
DescribeLivePullStreamTasks
API.

A maximum of 50 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DeleteLivePullStreamTask. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/267/30763#region-list) supported by the product. This API only supports: ap-bangkok, ap-beijing, ap-guangzhou, ap-hongkong, ap-mumbai, ap-seoul, ap-shanghai, ap-singapore, ap-tokyo, eu-frankfurt, na-ashburn, na-siliconvalley. |
| TaskId | Yes | String | The task ID. |
| Operator | Yes | String | The operator. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DeleteLivePullStreamTask
&TaskId=10000
&Operator=zhangsan
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
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
| InternalError.InvalidInput | Parameter check failed. |
| InvalidParameter.TaskNotExist | The task does not exist. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.UserNotExist | The CSS service has not been activated. |


---
*Source: [https://www.tencentcloud.com/document/product/267/48356](https://www.tencentcloud.com/document/product/267/48356)*
