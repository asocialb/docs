# DescribeLiveDomain

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query the LVB domain name information.

A maximum of 500 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeLiveDomain. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainName | No | String | Domain name. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DomainInfo | [DomainInfo](https://intl.cloud.tencent.com/document/api/267/30767#DomainInfo) | Domain name information. Note: this field may return `null`, indicating that no valid value is obtained. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DescribeLiveDomain
&DomainName=yourdomain.test.com
&<Common request parameters>
```

#### Output Example

```
{
    "Response": {
        "RequestId": "eac6b301-a322-493a-8e36-83b295459397",
        "DomainInfo": {
            "Name": "abc.com",
            "Type": 1,
            "Status": 1,
            "CreateTime": "2018-08-29 10:00:00",
            "BCName": 1,
            "TargetDomain": "yourdomain.test2.com",
            "CurrentCName": "yourdomain.test.com",
            "IsDelayLive": 0,
            "RentTag": 0,
            "RentExpireTime": "0000-00-00 00:00:00"
        }
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
| InternalError.DomainNotExist | The domain name does not exist. |
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.DomainNotExist | The domain name does not exist or is not matched. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/35187](https://www.tencentcloud.com/document/product/267/35187)*
