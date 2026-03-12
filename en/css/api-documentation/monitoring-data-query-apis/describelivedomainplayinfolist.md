# DescribeLiveDomainPlayInfoList

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query the real-time downstream playback data at the domain name level. As it takes certain time to process data, the API queries quasi-real-time data generated 4 minutes ago by default.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).
This document describes the parameters for Signature V1. It's recommended to use the V3 signature, which provides higher security. Note that for Signature V3, the common parameters need to be placed in the HTTP Header. [See details](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | Common parameter. The value used for this API: DescribeLiveDomainPlayInfoList. |
| Version | Yes | String | Common parameter. The value used for this API: 2018-08-01. |
| Region | No | String | Common parameter. This parameter is not required for this API. |
| PlayDomains.N | No | Array of String | Playback domain name list. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| Time | String | Data time in the format of `yyyy-mm-dd HH:MM:SS`. |
| TotalBandwidth | Float | Real-time total bandwidth. |
| TotalFlux | Float | Real-time total traffic. |
| TotalRequest | Integer | Total number of requests. |
| TotalOnline | Integer | Real-time total number of connections. |
| DomainInfoList | Array of [DomainInfoList](https://intl.cloud.tencent.com/document/api/267/30767#DomainInfoList) | Data by domain name. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DescribeLiveDomainPlayInfoList
&<Common request parameters>
```

#### Output Example

```
{
  "Response": {
    "DomainInfoList": [
      {
        "DetailInfoList": [
          {
            "Bandwidth": 309.998,
            "Flux": 18599.88,
            "MainlandOrOversea": "Mainland",
            "Online": 374,
            "Request": 175
          },
          {
            "Bandwidth": 0,
            "Flux": 0,
            "MainlandOrOversea": "Oversea",
            "Online": 0,
            "Request": 0
          }
        ],
        "Domain": "345.tencent.com"
      },
      {
        "DetailInfoList": [
          {
            "Bandwidth": 134351.765,
            "Flux": 8061105.9,
            "MainlandOrOversea": "Mainland",
            "Online": 130171,
            "Request": 102524
          },
          {
            "Bandwidth": 0,
            "Flux": 0,
            "MainlandOrOversea": "Oversea",
            "Online": 0,
            "Request": 0
          }
        ],
        "Domain": "123.tencent.com"
      }
    ],
    "RequestId": "04b76ebd-487d-4a7a-aca8-82060359feee",
    "Time": "2019-04-07 21:55:00",
    "TotalBandwidth": 2909181.92,
    "TotalFlux": 174550915.2,
    "TotalOnline": 2800396,
    "TotalRequest": 2446274
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
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://www.tencentcloud.com/document/product/267/37304](https://www.tencentcloud.com/document/product/267/37304)*
