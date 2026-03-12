# DescribeStreamPlayInfoList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query the playback data. It supports querying the playback details by stream name and aggregated data by playback domain name. Data in the last 4 minutes or so cannot be queried due to delay.
Note: to query by `AppName`, you need to submit a ticket first. After your application succeeds, it will take about 5 business days (subject to the time in the reply) for the configuration to take effect.

A maximum of 500 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeStreamPlayInfoList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | The start time of the request, supports data query for the last one month, the gap between the start time and the end time cannot exceed twenty-four hours. Interface request supports two time formats: |
| EndTime | Yes | String | The end time of the request, supports data query for the last one month, the gap between the start time and the end time cannot exceed twenty-four hours. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format,for details,see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| PlayDomain | No | String | Playback domain name, If this parameter is left empty, data of live streams of all playback domain names will be queried. |
| StreamName | No | String | Stream name (exact match). If this parameter is left empty, full playback data will be queried. |
| AppName | No | String | Push address. Its value is the same as the `AppName` in playback address. It supports exact match, and takes effect only when `StreamName` is passed at the same time. If it is left empty, the full playback data will be queried. Note: to query by `AppName`, you need to submit a ticket first. After your application succeeds, it will take about 5 business days (subject to the time in the reply) for the configuration to take effect. |
| ServiceName | No | String | Service name. Valid values: LVB, LEB. If this parameter is left empty, all data of LVB and LEB will be queried. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [DayStreamPlayInfo](https://www.tencentcloud.com/document/api/267/30767#DayStreamPlayInfo) | Statistics list at a 1-minute granularity. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
POST / HTTP/1.1
Host: live.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeStreamPlayInfoList
<Common request parameters>

{
    "PlayDomain": "5000.playdomain.com",
    "StreamName": "stream1",
    "EndTime": "2019-03-01 00:03:00",
    "StartTime": "2019-03-01 00:00:00"
}
```

#### Output Example

```json
{
    "Response": {
        "DataInfoList": [
            {
                "Time": "2019-03-01 00:00:00",
                "Bandwidth": 10.0,
                "Flux": 75.0,
                "Request": 50,
                "Online": 10
            },
            {
                "Time": "2019-03-01 00:02:00",
                "Bandwidth": 20.0,
                "Flux": 150.0,
                "Request": 50,
                "Online": 20
            },
            {
                "Time": "2019-03-01 00:03:00",
                "Bandwidth": 30.0,
                "Flux": 225.0,
                "Request": 50,
                "Online": 30
            }
        ],
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
| InternalError | Internal error. |
| InternalError.DBError | DB execution error. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37297](https://www.tencentcloud.com/document/product/267/37297)*
