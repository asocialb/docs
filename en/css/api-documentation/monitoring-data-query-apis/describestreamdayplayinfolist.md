# DescribeStreamDayPlayInfoList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query the playback data of each stream at the day level, including the total traffic.

A maximum of 500 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeStreamDayPlayInfoList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| DayTime | Yes | String | Date in the format of YYYY-mm-dd Data is available at 3am Beijing Time the next day. You are recommended to query the latest data after this time point. Data in the last 3 months can be queried. |
| PlayDomain | No | String | Playback domain name. |
| PageNum | No | Integer | Page number. Value range: [1,1000]. Default value: 1. |
| PageSize | No | Integer | Number of entries per page. Value range: [100,1000]. Default value: 1,000. |
| MainlandOrOversea | No | String | Valid values: Mainland: query data for Mainland China, Oversea: query data for regions outside Mainland China, Default: query data for all regions. |
| ServiceName | No | String | Service name. Valid values: LVB, LEB. If this parameter is left empty, all data of LVB and LEB will be queried. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [PlayDataInfoByStream](https://www.tencentcloud.com/document/api/267/30767#PlayDataInfoByStream) | Playback data information list. |
| TotalNum | Integer | Total number. |
| TotalPage | Integer | Total number of pages. |
| PageNum | Integer | Page number where the current data resides. |
| PageSize | Integer | Number of entries per page. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeStreamDayPlayInfoList
&PlayDomain=5000.livepush.com
&DayTime=2019-02-21
&PageNum=1
&PageSize=1000
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "DataInfoList": [
            {
                "StreamName": "test1",
                "TotalFlux": 500.0
            }
        ],
        "TotalNum": 100,
        "TotalPage": 1,
        "PageNum": 1,
        "PageSize": 1000,
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
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/36095](https://www.tencentcloud.com/document/product/267/36095)*
