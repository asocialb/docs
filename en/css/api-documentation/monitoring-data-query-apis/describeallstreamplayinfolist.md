# DescribeAllStreamPlayInfoList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to get the playback data of all streams at a specified time point (accurate to the minute).

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeAllStreamPlayInfoList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| QueryTime | Yes | String | The query time of the request, supports data query for the last one month. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format, for details, see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| PlayDomains.N | No | Array of String | The playback domains to query. If you leave this empty, all playback domains will be queried. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| QueryTime | String | The time point queried, whose format is the same as that of the corresponding request parameter. |
| DataInfoList | Array of [MonitorStreamPlayInfo](https://www.tencentcloud.com/document/api/267/30767#MonitorStreamPlayInfo) | The playback data. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeAllStreamPlayInfoList
&QueryTime=2019-12-12 10:00:00
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        &QueryTime=2019-12-12 10:00:00
        "DataInfoList": [
            {
                "Bandwidth": 1.82,
                "Online": 1,
                "PlayDomain": "domain.test1.com",
                "Protocol": "HLS",
                "Rate": 0,
                "Request": 19,
                "StreamName": "test1",
            },
            {
                "Bandwidth": 1.59,
                "Online": 1,
                "PlayDomain": "domain.test2.com",
                "Protocol": "Flv",
                "Rate": 0,
                "Request": 10,
                "StreamName": "test2"
            },
            {
                "Bandwidth": 3.6,
                "Online": 2,
                "PlayDomain": "domain.test3.com",
                "Protocol": "Flv",
                "Rate": 0,
                "Request": 12,
                "StreamName": "test3"
            }
        ],
        "RequestId": "k54e3deb-f318-4147-8a68-3c959642f9ec"
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
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37306](https://www.tencentcloud.com/document/product/267/37306)*
