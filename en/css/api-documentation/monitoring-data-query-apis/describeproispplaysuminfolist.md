# DescribeProIspPlaySumInfoList

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query the average traffic per second, total traffic, and number of total requests by country/region, district, and ISP in a certain period of time.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).
This document describes the parameters for Signature V1. It's recommended to use the V3 signature, which provides higher security. Note that for Signature V3, the common parameters need to be placed in the HTTP Header. [See details](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | Common parameter. The value used for this API: DescribeProIspPlaySumInfoList. |
| Version | Yes | String | Common parameter. The value used for this API: 2018-08-01. |
| Region | No | String | Common parameter. This parameter is not required for this API. |
| StartTime | Yes | String | Start time (Beijing time). |
| EndTime | Yes | String | End time (Beijing time). In the format of `yyyy-mm-dd HH:MM:SS`. Note: `EndTime` and `StartTime` only support querying data for the last day. |
| StatType | Yes | String | Statistics type. Valid values: Province (district), Isp (ISP), CountryOrArea (country or region). |
| PlayDomains.N | No | Array of String | Playback domain name list. If it is left empty, it refers to all playback domain names. |
| PageNum | No | Integer | Page number. Value range: [1,1000]. Default value: 1. |
| PageSize | No | Integer | Number of entries per page. Value range: [1,1000]. Default value: 20. |
| MainlandOrOversea | No | String | Region. Valid values: Mainland (data for Mainland China), Oversea (data for regions outside Mainland China), China (data for China, including Hong Kong, Macao, and Taiwan), Foreign (data for regions outside China, excluding Hong Kong, Macao, and Taiwan), Global (default). If this parameter is left empty, data for all regions will be queried. |
| OutLanguage | No | String | Language used in the output field. Valid values: Chinese (default), English. Currently, country/region, district, and ISP parameters support multiple languages. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TotalFlux | Float | Total traffic. |
| TotalRequest | Integer | Total number of requests. |
| StatType | String | Statistics type. |
| PageSize | Integer | Number of results per page. |
| PageNum | Integer | Page number. |
| TotalNum | Integer | Total number of results. |
| TotalPage | Integer | Total number of pages. |
| DataInfoList | Array of [ProIspPlaySumInfo](https://intl.cloud.tencent.com/document/api/267/30767#ProIspPlaySumInfo) | Aggregated data list by district, ISP, or country/region. |
| AvgFluxPerSecond | Float | Download speed in MB/s. Calculation method: total traffic/total duration. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DescribeProIspPlaySumInfoList
&PlayDomains.0=5000.playdomain.com
&StartTime=2019-03-01 00:00:00
&EndTime=2019-03-01 12:00:00
&StatType=Province
&<Common request parameters>
```

#### Output Example

```
{
  "Response": {
    "DataInfoList": [
      {
        "Name": "Shandong",
        "TotalFlux": 50.0,
        "TotalRequest": 50,
        "AvgFluxPerSecond": 10.1
      }
    ],
    "TotalFlux": 100.0,
    "TotalRequest": 100,
    "AvgFluxPerSecond": 100,
    "PageSize": 10,
    "PageNum": 1,
    "TotalNum": 10,
    "TotalPage": 2,
    "StatType": "Province",
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
Tencent Cloud SDK 3.0 for NodeJS
Tencent Cloud SDK 3.0 for .NET
Tencent Cloud SDK 3.0 for C++

### Command Line Interface

Tencent Cloud CLI 3.0

## 6. Error Code

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://intl.cloud.tencent.com/document/api/267/30851#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81).

| Error Code | Description |
| --- | --- |
| FailedOperation | Operation failed. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |


---
*Source: [https://www.tencentcloud.com/document/product/267/36096](https://www.tencentcloud.com/document/product/267/36096)*
