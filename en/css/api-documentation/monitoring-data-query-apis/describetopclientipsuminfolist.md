# DescribeTopClientIpSumInfoList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query the information of the top n client IPs in a certain period of time (top 1,000 is supported currently).

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeTopClientIpSumInfoList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | The start time of the request, supports data query for the last one day, the gap between the start time and the end time cannot exceed four hours. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format, for details, see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| EndTime | Yes | String | The end time of the request, supports data query for the last one day, the gap between the start time and the end time cannot exceed four hours. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format,for details,see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| PlayDomains.N | No | Array of String | Playback domain name. If this parameter is left empty, full data will be queried by default. |
| PageNum | No | Integer | Page number. Value range: [1,1000]. Default value: 1. |
| PageSize | No | Integer | Number of entries per page. Value range: [1,1000]. Default value: 20. |
| OrderParam | No | String | Sorting metric. Valid values: TotalRequest (default value), FailedRequest, TotalFlux. |
| MainlandOrOversea | No | String | Region. Valid values: Mainland (data for Mainland China), Oversea (data for regions outside Mainland China), China (data for China, including Hong Kong, Macao, and Taiwan), Foreign (data for regions outside China, excluding Hong Kong, Macao, and Taiwan), Global (default). If this parameter is left empty, data for all regions will be queried. |
| OutLanguage | No | String | Language used in the output field. Valid values: Chinese (default), English. Currently, country/region, district, and ISP parameters support multiple languages. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| PageNum | Integer | Page number. Value range: [1,1000]. Default value: 1. |
| PageSize | Integer | Number of entries per page. Value range: [1,1000]. Default value: 20. |
| OrderParam | String | Sorting metric. Valid values: "TotalRequest", "FailedRequest", "TotalFlux". |
| TotalNum | Integer | Total number of results. |
| TotalPage | Integer | Total number of result pages. |
| DataInfoList | Array of [ClientIpPlaySumInfo](https://www.tencentcloud.com/document/api/267/30767#ClientIpPlaySumInfo) | Data content. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeTopClientIpSumInfoList
&StartTime=2019-03-01 00:00:00
&EndTime=2019-03-01 04:00:00
&PageSize=2
&PageNum=2
&OrderParam=TotalFlux
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "DataInfoList": [
            {
                "ClientIp": "119.44.7.168",
                "CountryArea": "China",
                "Province": "Hunan",
                "TotalFailedRequest": 4,
                "TotalFlux": 13321.099,
                "TotalRequest": 740
            },
            {
                "ClientIp": "119.44.7.175",
                "CountryArea": "China",
                "Province": "Hunan",
                "TotalFailedRequest": 3,
                "TotalFlux": 12566.334,
                "TotalRequest": 2318
            }
        ],
        "OrderParam": "TotalFlux",
        "PageNum": 2,
        "PageSize": 2,
        "RequestId": "k54e3deb-f318-4147-8a68-3c959642f9ec",
        "TotalNum": 1000,
        "TotalPage": 500
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
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37296](https://www.tencentcloud.com/document/product/267/37296)*
