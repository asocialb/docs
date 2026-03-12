# DescribeGroupProIspPlayInfoList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query the downstream playback data by district and ISP.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeGroupProIspPlayInfoList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | The start time of the request, supports data query for the last one month, the gap between the start time and the end time cannot exceed one month. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format, for details, see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| EndTime | Yes | String | The end time of the request, supports data query for the last one month, the gap between the start time and the end time cannot exceed one month. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format,for details,see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| PlayDomains.N | No | Array of String | Playback domain name. If this parameter is left empty, full data will be queried. |
| ProvinceNames.N | No | Array of String | District list. If this parameter is left empty, data for all districts will be returned. |
| IspNames.N | No | Array of String | ISP list. If this parameter is left empty, data of all ISPs will be returned. |
| MainlandOrOversea | No | String | Within or outside Mainland China. Valid values: Mainland (data for Mainland China), Oversea (data for regions outside Mainland China). If this parameter is left empty, data for all regions will be queried. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [GroupProIspDataInfo](https://www.tencentcloud.com/document/api/267/30767#GroupProIspDataInfo) | Data content. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeGroupProIspPlayInfoList
&StartTime=2019-03-29 09:00:00
&EndTime=2019-03-29 09:10:00
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "DataInfoList": [
            {
                "DetailInfoList": [
                    {
                        "Bandwidth": 863.073,
                        "Flux": 6473.05,
                        "Online": 540,
                        "Request": 449,
                        "Time": "2019-03-29 09:00:00"
                    },
                    {
                        "Bandwidth": 891.49,
                        "Flux": 6686.173,
                        "Online": 524,
                        "Request": 455,
                        "Time": "2019-03-29 09:05:00"
                    },
                    {
                        "Bandwidth": 847.715,
                        "Flux": 6357.859,
                        "Online": 612,
                        "Request": 578,
                        "Time": "2019-03-29 09:10:00"
                    }
                ],
                "IspName": "China Telecom",
                "ProvinceName": "Guangdong"
            },
            {
                "DetailInfoList": [
                    {
                        "Bandwidth": 213.405,
                        "Flux": 1600.537,
                        "Online": 132,
                        "Request": 184,
                        "Time": "2019-03-29 09:00:00"
                    },
                    {
                        "Bandwidth": 215.738,
                        "Flux": 1618.032,
                        "Online": 125,
                        "Request": 122,
                        "Time": "2019-03-29 09:05:00"
                    },
                    {
                        "Bandwidth": 226.96,
                        "Flux": 1702.203,
                        "Online": 131,
                        "Request": 131,
                        "Time": "2019-03-29 09:10:00"
                    }
                ],
                "IspName": "China Unicom",
                "ProvinceName": "Guangdong"
            }
        ],
        "RequestId": "3c140219-cfe9-470e-b241-907877d6fb03"
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
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://www.tencentcloud.com/document/product/267/36097](https://www.tencentcloud.com/document/product/267/36097)*
