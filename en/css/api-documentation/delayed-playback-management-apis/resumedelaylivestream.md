# ResumeDelayLiveStream

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to cancel the delay setting and recover the real-time display of the live streaming image.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: ResumeDelayLiveStream. |
| Version | Yes | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://intl.cloud.tencent.com/document/api/267/30763). This parameter is not required for this API. |
| AppName | Yes | String | Push path, which is the same as the AppName in push and playback addresses and is "live" by default. |
| DomainName | Yes | String | Push domain name. |
| StreamName | Yes | String | Stream name. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=ResumeDelayLiveStream
&DomainName=5000.livepush.myqcloud.com
&AppName=live
&StreamName=stream1
&<Common request parameters>
```

#### Output Example

```
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://intl.cloud.tencent.com/document/api/267/30851#common-error-codes).

| Error Code | Description |
| --- | --- |
| DryRunOperation | DryRun operation. A request will not be successful if the `DryRun` parameter is passed in. |
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
| LimitExceeded | Quota exceeded. |
| MissingParameter | Parameter missing. |
| ResourceInUse | The resource is occupied. |
| ResourceInsufficient | Insufficient resources. |
| ResourceNotFound | The resource is not found. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.UserNotExist | The LVB service has not been activated. |
| ResourceUnavailable | The resource is unavailable. |
| UnauthorizedOperation | Unauthorized operation. |
| UnknownParameter | Unknown parameter. |
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30849](https://www.tencentcloud.com/document/product/267/30849)*
