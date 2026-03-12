# DescribeLiveStreamOnlineList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to get the list of ongoing live streams. It queries the information of live streams after they are pushed successfully.

Notes:

This API is used to query the list of active live streams only, and should not be relied too much upon in important business scenarios.
This API can query up to 20,000 streams. To query more streams, please contact our after-sales service team.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeLiveStreamOnlineList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| DomainName | No | String | Push domain name. If you use multiple paths, enter the `DomainName`. |
| AppName | No | String | Push path, which is the same as the `AppName` in push and playback addresses and is `live` by default. If you use multiple paths, enter the `AppName`. |
| PageNum | No | Integer | Page number to get. Default value: 1. |
| PageSize | No | Integer | Number of entries per page. Maximum value: 100.  Value: any integer between 10 and 100. Default value: 10. |
| StreamName | No | String | Stream name, which is used for exact query. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TotalNum | Integer | Total number of eligible ones. |
| TotalPage | Integer | Total number of pages. |
| PageNum | Integer | Page number. |
| PageSize | Integer | Number of entries displayed per page. |
| OnlineInfo | Array of [StreamOnlineInfo](https://www.tencentcloud.com/document/api/267/30767#StreamOnlineInfo) | Active push information list. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeLiveStreamOnlineList
&DomainName=5000.livepush.myqcloud.com
&AppName=live
&PageNum=1
&PageSize=10
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "OnlineInfo":[{
            {
                "StreamName": "5000_abcdefg",
                "AppName": "live",
                "DomainName": "5000.livepush.myqcloud.com",
                "PublishTimeList": [{
                    {
                        "PublishTime": "2017-10-24T12:00:00Z"
                    }
                ]
            }
        ],
        "TotalNum": 1,
        "TotalPage": 1,
        "PageNum": 1,
        "PageSize": 10,
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/267/30851#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| InternalError | Internal error. |
| InternalError.CallOtherSvrError | Error calling internal service. |
| InternalError.ConfigNotExist | The configuration does not exist. |
| InternalError.GetBizidError | Error getting user account. |
| InternalError.GetStreamInfoError | Failed to get the stream information. |
| InternalError.GetUpstreamInfoError | Error getting the live stream source information. |
| InternalError.NotPermmitOperat | No permission to operate. |
| InternalError.StreamStatusError | Exceptional stream status. |
| InternalError.UpdateDataError | Failed to update data. |
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.UserNotExist | The CSS service has not been activated. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30798](https://www.tencentcloud.com/document/product/267/30798)*
