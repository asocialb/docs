# DeleteLiveDomain

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to delete an added LVB domain name.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DeleteLiveDomain. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainName | Yes | String | Domain name to be deleted. |
| DomainType | Yes | Integer | Type. 0: push, 1: playback. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Deleting domain name

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DeleteLiveDomain
&DomainName=www.test.com
&DomainType=0
&<Common request parameters>
```

#### Output Example

```
{
    "Response": {
        "RequestId": "eac6b301-a322-493a-8e36-83b295459397"
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
| FailedOperation.DeleteDomainInLockedTime | The domain name cannot be deleted because it incurred traffic in the last 2 days and is in locked state. |
| FailedOperation.JiFeiNoEnoughFund | The billing platform returned an error of insufficient balance. |
| FailedOperation.NotFound | No records found. |
| FailedOperation.TagUnbindError | Failed to unbind the tag. Try unbinding it manually. |
| InternalError | Internal error. |
| InternalError.ConnectDbError | Database connection error. |
| InternalError.DBError | DB execution error. |
| InternalError.NetworkError | Internal network error. |
| InvalidParameter.DomainAlreadyExist | The domain name already exists. |
| InvalidParameter.DomainFormatError | The domain name format is incorrect. Please enter a valid one. |
| InvalidParameter.DomainIsLimited | The domain name is restricted. Please submit a ticket for application to remove the restrictions. |
| ResourceNotFound.DomainNotExist | The domain name does not exist or is not matched. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/35188](https://www.tencentcloud.com/document/product/267/35188)*
