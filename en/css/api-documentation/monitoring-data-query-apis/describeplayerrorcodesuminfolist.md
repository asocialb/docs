# DescribePlayErrorCodeSumInfoList

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to query the information of downstream playback error codes.

A maximum of 200 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribePlayErrorCodeSumInfoList. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| StartTime | Yes | String | The start time of the request, supports data query for the last one day, the gap between the start time and the end time cannot exceed one day. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format, for details, see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| EndTime | Yes | String | The end time of the request, supports data query for the last one day, the gap between the start time and the end time cannot exceed one day. Interface request supports two time formats: 1) YYYY-MM-DDThh:mm:ssZ: ISO time format,for details,see [ISO Date Format Description](https://intl.cloud.tencent.com/document/product/267/32941) 2) YYYY-MM-DD hh:mm:ss: When using this format, it represents Beijing time by default. |
| PlayDomains.N | No | Array of String | Playback domain name list. If this parameter is left empty, full data will be queried. |
| PageNum | No | Integer | Number of pages. Value range: [1,1000]. Default value: 1. |
| PageSize | No | Integer | Number of entries per page. Value range: [1,1000]. Default value: 20. |
| MainlandOrOversea | No | String | Region. Valid values: Mainland (data for Mainland China), Oversea (data for regions outside Mainland China), China (data for China, including Hong Kong, Macao, and Taiwan), Foreign (data for regions outside China, excluding Hong Kong, Macao, and Taiwan), Global (default). If this parameter is left empty, data for all regions will be queried. |
| GroupType | No | String | Grouping parameter. Valid values: CountryProIsp (default value), Country (country/region). Grouping is made by country/region + district + ISP by default. Currently, districts and ISPs outside Mainland China cannot be recognized. |
| OutLanguage | No | String | Language used in the output field. Valid values: Chinese (default), English. Currently, country/region, district, and ISP parameters support multiple languages. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| ProIspInfoList | Array of [ProIspPlayCodeDataInfo](https://www.tencentcloud.com/document/api/267/30767#ProIspPlayCodeDataInfo) | Information of error codes starting with 2, 3, 4, or 5 by district and ISP. |
| TotalCodeAll | Integer | Total occurrences of all status codes. |
| TotalCode4xx | Integer | Occurrences of 4xx status codes. |
| TotalCode5xx | Integer | Occurrences of 5xx status codes. |
| TotalCodeList | Array of [PlayCodeTotalInfo](https://www.tencentcloud.com/document/api/267/30767#PlayCodeTotalInfo) | Total occurrences of each status code. |
| PageNum | Integer | Page number. |
| PageSize | Integer | Number of entries per page. |
| TotalPage | Integer | Total number of pages. |
| TotalNum | Integer | Total number of results. |
| TotalCode2xx | Integer | Occurrences of 2xx status codes. |
| TotalCode3xx | Integer | Occurrences of 3xx status codes. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribePlayErrorCodeSumInfoList
&PlayDomains.0=5000.playdomain.com
&StartTime=2019-03-01 00:00:00
&EndTime=2019-03-01 12:00:00
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "ProIspInfoList": [
            {
                "CountryAreaName": "China",
                "ProvinceName": "Shandong",
                "IspName": "China Mobile",
                "Code2xx": 11,
                "Code3xx": 12,
                "Code4xx": 10,
                "Code5xx": 19
            }
        ],
        "TotalCodeList": [
            {
                "Code": "200",
                "Num": 11
            },
            {
                "Code": "302",
                "Num": 12
            },
            {
                "Code": "403",
                "Num": 1000
            },
            {
                "Code": "500",
                "Num": 19
            }
        ],
        "TotalCodeAll": 100,
        "TotalCode2xx": 11,
        "TotalCode3xx": 12,
        "TotalCode4xx": 10,
        "TotalCode5xx": 29,
        "PageNum": 1,
        "PageSize": 10,
        "TotalPage": 10,
        "TotalNum": 100,
        "RequestId": "e6628973-db6a-48f1-9fcd-fe0b3ba54bc9"
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
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37300](https://www.tencentcloud.com/document/product/267/37300)*
