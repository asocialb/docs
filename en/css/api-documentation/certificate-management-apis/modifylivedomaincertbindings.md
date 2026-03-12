# ModifyLiveDomainCertBindings

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to bind a certificate to multiple playback domains and update the HTTPS configuration of the domains.
If a self-owned certificate is used, it will be automatically uploaded to Tencent Cloud’s SSL Certificate Service.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: ModifyLiveDomainCertBindings. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainInfos.N | Yes | Array of [LiveCertDomainInfo](https://intl.cloud.tencent.com/document/api/267/30767#LiveCertDomainInfo) | The playback domains to bind and whether to enable HTTPS for them. |
| CloudCertId | No | String | The SSL certificate ID assigned by Tencent Cloud. For details, see https://intl.cloud.tencent.com/document/api/400/41665?from_cn_redirect=1 |
| CertificatePublicKey | No | String | The public key of the certificate. You can specify either `CloudCertId` or the public/private key. If both are specified, the private and public key parameters will be ignored. If you pass in only the public and private keys, the corresponding certificate will be uploaded to Tencent Cloud SSL Certificate Service, which will generate a `CloudCertId` for the certificate. |
| CertificatePrivateKey | No | String | The private key of the certificate. You can specify either `CloudCertId` or the public/private key. If both are specified, the private and public key parameters will be ignored. If you pass in only the public and private keys, the corresponding certificate will be uploaded to Tencent Cloud SSL Certificate Service, which will generate a `CloudCertId` for the certificate. |
| CertificateAlias | No | String | The remarks for the certificate in Tencent Cloud SSL Certificate Service. This parameter will be ignored if `CloudCertId` is specified. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| MismatchedDomainNames | Array of String | The domains skipped due to certificate mismatch. |
| Errors | Array of [BatchDomainOperateErrors](https://intl.cloud.tencent.com/document/api/267/30767#BatchDomainOperateErrors) | The domains that the API failed to bind, including those in `MismatchedDomainNames`, and the error information. Note: This field may return null, indicating that no valid values can be obtained. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ModifyLiveDomainCertBindings
<Common request parameters>

{
    "CloudCertId": "hZy2N9vF",
    "DomainInfos": [
        {
            "DomainName": "abc.tst.com.cn",
            "Status": 1
        }
    ]
}
```

#### Output Example

```
{
    "Response": {
        "RequestId": "cb91d382-e9be-4688-9008-d57088271b5f",
        "MismatchedDomainNames": [],
        "Errors": []
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
| FailedOperation.AuthError | You do not have permission to perform this operation. |
| FailedOperation.CannotBeDeletedIssued | Failed to delete the certificate because it has been issued. |
| FailedOperation.CannotBeDeletedWithinHour | Free certificates cannot be deleted within one hour of application. |
| FailedOperation.CertificateExists | The certificate already exists. |
| FailedOperation.CertificateInvalid | The certificate is invalid. |
| FailedOperation.CertificateMismatch | The certificate and the private key do not match. |
| FailedOperation.CertificateNotFound | The certificate does not exist. |
| FailedOperation.ConfigCDNFailed | CDN configuration failed. |
| FailedOperation.ExceedsFreeLimit | The number of free certificates exceeded the limit. |
| FailedOperation.InvalidCertificateStatusCode | Invalid certificate status. |
| FailedOperation.InvalidParam | Invalid parameter. |
| FailedOperation.NetworkError | The CA system is busy. Try again later. |
| FailedOperation.NoProjectPermission | You do not have permission to operate this project. |
| FailedOperation.NoRealNameAuth | You haven’t completed identity verification. |
| InternalError | Internal error. |
| InternalError.ConnectDbError | Database connection error. |
| InternalError.CrtDateInUsing | The certificate is in use. |
| InternalError.CrtDateNotFound | The certificate does not exist. |
| InternalError.CrtDateNotLegal | The certificate is invalid. |
| InternalError.CrtDateOverdue | The certificate has expired. |
| InternalError.CrtDomainNotFound | There is no related domain name. |
| InternalError.CrtKeyNotMatch | The certificate key does not match. |
| InternalError.DBError | DB execution error. |
| InternalError.NetworkError | Internal network error. |
| InvalidParameter | Invalid parameter. |
| InvalidParameter.CloudCrtIdError | Incorrect Tencent Cloud-hosted certificate ID. |
| InvalidParameter.CrtDateInUsing | The certificate is in use. |
| InvalidParameter.CrtDateNotFound | The certificate does not exist. |
| InvalidParameter.CrtDateNotLegal | The certificate is invalid. |
| InvalidParameter.CrtDateOverdue | The certificate has expired. |
| InvalidParameter.CrtDomainNotFound | Unable to find the domain. |
| InvalidParameter.CrtKeyNotMatch | The certificate key does not match. |
| InvalidParameter.CrtOrKeyNotExist | The certificate content or private key was not provided. |
| LimitExceeded.RateLimitExceeded | Reached the API rate limit. |
| ResourceNotFound.CrtDateNotFound | The certificate does not exist. |
| ResourceNotFound.CrtDomainNotFound | No certificate was found. |
| ResourceNotFound.DomainNotExist | The domain name does not exist or is not matched. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/49644](https://www.tencentcloud.com/document/product/267/49644)*
