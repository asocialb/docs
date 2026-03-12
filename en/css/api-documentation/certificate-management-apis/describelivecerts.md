# DescribeLiveCerts

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to get the certificate information list.

A maximum of 500 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeLiveCerts. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| CertInfoSet | Array of [CertInfo](https://intl.cloud.tencent.com/document/api/267/30767#CertInfo) | Certificate information list. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DescribeLiveCerts
&<Common request parameters>
```

#### Output Example

```
{
    "Response": {
        "CertInfoSet": [
            {
                "CertId": 1000,
                "CertName": "testName",
                "Description": "testDesc",
                "CreateTime": "2018-11-30T15:50:12Z",
                "HttpsCrt": "xxx",
                "CertType": 0,
                "CertExpireTime": "2018-12-30T15:50:12Z",
                "DomainList": [
                    "5000.livepush.play.com"
                ]
            }
        ],
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://intl.cloud.tencent.com/document/api/267/30851#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation.InvokeVideoApiFail | An exception occurred while manipulating the VOD API. |
| InternalError | Internal error. |
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.CrtDomainNotFound | No certificate was found. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30778](https://www.tencentcloud.com/document/product/267/30778)*
