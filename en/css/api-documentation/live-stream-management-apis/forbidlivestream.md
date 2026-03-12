# ForbidLiveStream

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to disable a stream. You can set a time to resume the stream.
Note:

As long as the correct stream name is passed in, the stream will be disabled successfully.
If you want a stream to be disabled only if the push domain, push path, and stream name match, please submit a ticket.
If you have configured domain groups, you must pass in the correct push domain in order to disable a stream.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: ForbidLiveStream. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| AppName | Yes | String | Push path, which is the same as the AppName in push and playback addresses and is "live" by default. |
| DomainName | Yes | String | Your push domain name. |
| StreamName | Yes | String | Stream name. |
| ResumeTime | No | String | The time (in UTC format) to resume the stream, such as 2018-11-29T19:00:00Z. |
| Reason | No | String | Reason for forbidding. Note: Be sure to enter the reason for forbidding to avoid any faulty operations. Length limit: 2,048 bytes. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Disabling a stream

This example shows you how to disable a stream.

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=ForbidLiveStream
&DomainName=5000.livepush.myqcloud.com
&AppName=live
&StreamName=stream1
&ResumeTime=2018-11-24T12:00:00Z
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
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
| FailedOperation | Operation failed. |
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
*Source: [https://www.tencentcloud.com/document/product/267/30794](https://www.tencentcloud.com/document/product/267/30794)*
