# DescribeLiveDomainCertBindings

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query domains bound with certificates.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeLiveDomainCertBindings. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainSearch | No | String | The keyword to use to search for domains. |
| Offset | No | Integer | The number of records to skip before starting to return any results. 0 means to start from the first record and is the default. |
| Length | No | Integer | The maximum number of records to return. The default is 50. If this parameter is not specified, up to 50 records will be returned. |
| DomainName | No | String | The name of a particular domain to query. |
| OrderBy | No | String | Valid values: ExpireTimeAsc: Sort the records by certificate expiration time in ascending order. ExpireTimeDesc: Sort the records by certificate expiration time in descending order. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| LiveDomainCertBindings | Array of [LiveDomainCertBindings](https://intl.cloud.tencent.com/document/api/267/30767#LiveDomainCertBindings) | The information of domains that meet the query criteria. |
| TotalNum | Integer | The number of records returned, which is needed for pagination. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeLiveDomainCertBindings
<Common request parameters>

{
    "DomainSearch": "",
    "DomainName": "abc.com",
    "Offset": 0,
    "Length": 50
}
```

#### Output Example

```
{
    "Response": {
        "RequestId": "3b4a072b-9f74-4baa-9200-1e0858baa7a5",
        "LiveDomainCertBindings": [],
        "TotalNum": 0
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
| InternalError | Internal error. |
| InternalError.ConnectDbError | Database connection error. |
| InternalError.DBError | DB execution error. |
| InvalidParameter | Invalid parameter. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/49645](https://www.tencentcloud.com/document/product/267/49645)*
