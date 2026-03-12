# AddLiveDomain

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to add a domain name. Only one domain name can be submitted at a time, and it must have an ICP filing.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: AddLiveDomain. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainName | Yes | String | Domain name. |
| DomainType | Yes | Integer | Domain name type. 0: push domain name. 1: playback domain name. |
| PlayType | No | Integer | Pull domain name type: 1: Mainland China. 2: global. 3: outside Mainland China. Default value: 1. |
| IsDelayLive | No | Integer | Whether it is LCB: 0: LVB, 1: LCB. Default value: 0. |
| IsMiniProgramLive | No | Integer | Whether it is LVB on Mini Program. 0: LVB. 1: LVB on Mini Program. Default value: 0. |
| VerifyOwnerType | No | String | The domain verification type. Valid values (the value of this parameter must be the same as `VerifyType` of the `AuthenticateDomainOwner` API): dnsCheck: Check immediately whether the verification DNS record has been added successfully. If so, record this verification result. fileCheck: Check immediately whether the verification HTML file has been uploaded successfully. If so, record this verification result. dbCheck: Check whether the domain has already been verified. If you do not pass a value, `dbCheck` will be used. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Adding a domain name

#### Input Example

```
https://live.tencentcloudapi.com/?Action=AddLiveDomain
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
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| FailedOperation.DeleteDomainInLockedTime | The domain name cannot be deleted because it incurred traffic in the last 2 days and is in locked state. |
| FailedOperation.DomainAdded | The domain has already been added. |
| FailedOperation.DomainGslbFail | Failed to configure the domain rule. |
| FailedOperation.DomainNeedRealName | The domain has not been verified. |
| FailedOperation.DomainNeedVerifyOwner | The ownership of the domain has not been verified. |
| FailedOperation.HostOutLimit | The number of domain names exceeded the upper limit (100). |
| FailedOperation.ParentDomainAdded | The domain’s parent domain has already been added. |
| FailedOperation.SubDomainAdded | The domain’s subdomain has already been added. |
| InternalError | Internal error. |
| InternalError.ChineseCharacterDetected | Chinese domain names are not supported currently. Please check the domain name format. |
| InternalError.ConnectDbError | Database connection error. |
| InternalError.DBError | DB execution error. |
| InternalError.DomainAlreadyExist | The domain name is already connected elsewhere. Please check whether the entered domain name is correct, and if yes, you can add it again after successful ownership verification. |
| InternalError.DomainFormatError | The domain name format is incorrect. Please enter a valid one. |
| InternalError.DomainGslbFail | Failed to add the GSLB rule. |
| InternalError.DomainIsFamous | The domain name is already connected elsewhere. Please check whether the entered domain name is correct, and if yes, you can add it again after successful ownership verification. |
| InternalError.DomainIsLimited | Your domain name is unavailable. Please enter a correct domain name. |
| InternalError.DomainNoRecord | The domain name has no ICP filing. |
| InternalError.DomainTooLong | The domain name length exceeds the limit. |
| InternalError.InvalidInput | Parameter check failed. |
| InternalError.InvalidUser | Account information error. |
| InternalError.NetworkError | Internal network error. |
| InvalidParameter | Invalid parameter. |
| InvalidParameter.DomainAlreadyExist | The domain name already exists. |
| InvalidParameter.DomainFormatError | The domain name format is incorrect. Please enter a valid one. |
| InvalidParameter.DomainHitBlackList | This domain name is on the blocklist. |
| InvalidParameter.DomainIsFamous | A blocklisted domain name is used. |
| InvalidParameter.DomainIsLimited | The domain name is restricted. Please submit a ticket for application to remove the restrictions. |
| InvalidParameter.DomainTooLong | The domain name exceeds the length limit. |
| InvalidParameter.MpHostDelete | It is not allowed to add a Mini Program domain name deleted in the same month. |
| InvalidParameter.MpPluginNoUse | The WeChat Mini Program plug-in is unauthorized. |
| ResourceNotFound.DomainNoRecord | The domain name has no ICP filing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.InvalidUser | This API is not supported for the user. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/35189](https://www.tencentcloud.com/document/product/267/35189)*
