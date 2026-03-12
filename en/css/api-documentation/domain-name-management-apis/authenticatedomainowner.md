# AuthenticateDomainOwner

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to verify the ownership of a domain.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: AuthenticateDomainOwner. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainName | Yes | String | The domain to verify. |
| VerifyType | Yes | String | The verification type. Valid values: dnsCheck: Check immediately whether the verification DNS record has been added successfully. If so, record this verification result. fileCheck: Check immediately whether the verification HTML file has been uploaded successfully. If so, record this verification result. dbCheck: Check whether the domain has already been successfully verified. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| Content | String | The content verified. If `VerifyType` is `dnsCheck`, this is the TXT record that should be added for verification. If `VerifyType` is `fileCheck`, this is the file that should be uploaded for verification. |
| Status | Integer | The verification status. If the value of this parameter is 0 or greater, the domain has been verified. If the value of this parameter is smaller than 0, the domain has not been verified. |
| MainDomain | String | The primary domain of the domain verified. Verification is not required if another domain under the same primary domain has been successfully verified. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: AuthenticateDomainOwner
<Common request parameters>

{
    "VerifyType": "dnsCheck",
    "DomainName": "akxynt.cn"
}
```

#### Output Example

```
{
    "Response": {
        "Content": "cssauth_da06159efa92c365182ba5d453a7b65b",
        "MainDomain": "akxynt.cn",
        "RequestId": "20a9d1c1-7b2a-48b5-9a78-c0bccab3dfb6",
        "Status": 0
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
| InvalidParameter | Invalid parameter. |
| InvalidParameter.DomainFormatError | The domain name format is incorrect. Please enter a valid one. |


---
*Source: [https://www.tencentcloud.com/document/product/267/50612](https://www.tencentcloud.com/document/product/267/50612)*
