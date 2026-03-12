# DescribeLiveDomains

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query domain names by domain name status and type.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: DescribeLiveDomains. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| DomainStatus | No | Integer | Filter by domain name status. 0: disabled, 1: enabled. |
| DomainType | No | Integer | Filter by domain name type. 0: push. 1: playback |
| PageSize | No | Integer | Number of entries per page. Value range: 10-100. Default value: 10. |
| PageNum | No | Integer | Page number to get. Value range: 1-100000. Default value: 1. |
| IsDelayLive | No | Integer | 0: LVB, 1: LCB. Default value: 0. |
| DomainPrefix | No | String | Domain name prefix. |
| PlayType | No | Integer | Playback region. This parameter is valid only when `DomainType` is set to `1`. `1`: Chinese mainland `2`: global `3`: outside Chinese mainland |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| AllCount | Integer | Total number of results. |
| DomainList | Array of [DomainInfo](https://intl.cloud.tencent.com/document/api/267/30767#DomainInfo) | List of domain name details. |
| CreateLimitCount | Integer | The number of domain names that can be added Note: this field may return `null`, indicating that no valid values can be obtained. |
| PlayTypeCount | Array of Integer | The number of domains accelerated in the Chinese mainland, globally, and outside the Chinese mainland respectively. Note: This field may return null, indicating that no valid values can be obtained. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Querying the domain name list

#### Input Example

```
POST / HTTP/1.1
Host: live.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeLiveDomains
<Common request parameters>

{
    "IsDelayLive": "0",
    "PageSize": "10",
    "PageNum": "1",
    "DomainStatus": "1",
    "DomainType": "1"
}
```

#### Output Example

```
{
    "Response": {
        "RequestId": "eac6b301-a322-493a-8e36-83b295459397",
        "AllCount": 2,
        "CreateLimitCount": 0,
        "PlayTypeCount": [
            1,
            2,
            3
        ],
        "DomainList": [
            {
                "Name": "abc.com",
                "IsMiniProgramLive": 0,
                "Type": 1,
                "Status": 1,
                "PlayType": 1,
                "IsDelayLive": 0,
                "CreateTime": "2018-08-29 10:00:00",
                "BCName": 1,
                "CurrentCName": "",
                "TargetDomain": "abc.com.liveplay.myqcloud.com",
                "RentTag": 0,
                "RentExpireTime": "0000-00-00 00:00:00"
            }
        ]
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
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| InternalError | Internal error. |
| InternalError.ConnectDbError | Database connection error. |
| InternalError.DBError | DB execution error. |
| InternalError.GetBizidError | Error getting user account. |
| ResourceNotFound.EmptyData |  |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.InvalidUser | This API is not supported for the user. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/35186](https://www.tencentcloud.com/document/product/267/35186)*
