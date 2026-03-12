# ModifyLivePushAuthKey

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to modify the LVB push authentication key.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: ModifyLivePushAuthKey. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainName | Yes | String | Push domain name. |
| Enable | No | Integer | Whether to enable. 0: disabled; 1: enabled. If this parameter is left empty, the current value will not be modified. |
| MasterAuthKey | No | String | Master authentication key. If this parameter is left empty, the current value will not be modified. |
| BackupAuthKey | No | String | Backup authentication key. If this parameter is left empty, the current value will not be modified. |
| AuthDelta | No | Integer | Validity period in seconds. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Modifying authentication configuration for a push domain

This example shows you how to modify authentication configuration for a push domain.

#### Input Example

```
POST / HTTP/1.1
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ModifyLivePushAuthKey
<Common request parameters>

{
    "DomainName": "abc.com",
    "Enable": 0,
    "MasterAuthKey": "abc*&^",
    "BackupAuthKey": "",
    "AuthDelta": 1
}
```

#### Output Example

```
{
    "Response": {
        "RequestId": "e48b9f8d-d9d1-4de4-a732-5ab8a333c0d8"
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
| InternalError | Internal error. |
| InternalError.ConnectDbError | Database connection error. |
| InternalError.DBError | DB execution error. |
| InternalError.PushDomainNoRecord | The push domain name does not exist. |
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.PushDomainNoRecord | The push domain name does not exist. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30769](https://www.tencentcloud.com/document/product/267/30769)*
