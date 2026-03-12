# DescribeLiveDomainReferer

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query referer allowlist/blocklist configuration of a live streaming domain name.
Referer information is included in HTTP requests. After you enable referer configuration, live streams using RTMP or WebRTC for playback will not authenticate the referer and can be played back normally. To make the referer configuration effective, the HTTP-FLV or HLS protocol is recommended for playback.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeLiveDomainReferer. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainName | Yes | String | Playback domain name |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RefererAuthConfig | [RefererAuthConfig](https://intl.cloud.tencent.com/document/api/267/30767#RefererAuthConfig) | Referer allowlist/blocklist configuration of a domain name |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DescribeLiveDomainReferer
&DomainName=5000.liveplay.myqcloud.com
&<Common request parameters>
```

#### Output Example

```
{
    "Response": {
        "RefererAuthConfig": {
            "DomainName": "5000.liveplay.myqcloud.com",
            "Enable": 1,
            "Type": 0,
            "AllowEmpty": 1,
            "Rules": "xxx.com;yyy.com"
        },
        "RequestId": "8e50cdb5-56dc-408b-89b0-31818958d424"
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
*Source: [https://www.tencentcloud.com/document/product/267/40611](https://www.tencentcloud.com/document/product/267/40611)*
