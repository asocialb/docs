# DescribeAreaBillBandwidthAndFluxList

## 1. API Description

Domain name for API request: live.tencentcloudapi.com.

This API is used to query the billable LVB bandwidth and traffic data outside Chinese mainland.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://intl.cloud.tencent.com/document/api/267/30763).
This document describes the parameters for Signature V1. It's recommended to use the V3 signature, which provides higher security. Note that for Signature V3, the common parameters need to be placed in the HTTP Header. [See details](https://intl.cloud.tencent.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | Common parameter. The value used for this API: DescribeAreaBillBandwidthAndFluxList. |
| Version | Yes | String | Common parameter. The value used for this API: 2018-08-01. |
| Region | No | String | Common parameter. This parameter is not required for this API. |
| StartTime | Yes | String | Start time point in the format of yyyy-mm-dd HH:MM:SS. |
| EndTime | Yes | String | End time point in the format of yyyy-mm-dd HH:MM:SS. The difference between the start time and end time cannot be greater than 1 days. |
| PlayDomains.N | No | Array of String | LVB playback domain name. If it is left blank, the full data will be queried. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| DataInfoList | Array of [BillAreaInfo](https://intl.cloud.tencent.com/document/api/267/30767#BillAreaInfo) | Detailed data information. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.tencentcloudapi.com/?Action=DescribeAreaBillBandwidthAndFluxList
&PlayDomains.0=5000.playdomain.com
&StartTime=2019-02-0100:00:00
&EndTime=2019-02-0100:10:00
&<Common request parameters>
```

#### Output Example

```
{
  "Response": {
    "DataInfoList": [
      {
        "Name": "Middle East/Africa",
        "Countrys": [
          {
            "Name": "United Arab Emirates",
            "BandInfoList": [
              {
                "Bandwidth": 6.95,
                "Flux": 260.7,
                "PeakTime": "2020-09-09 00:00:00",
                "Time": "2020-09-09 00:05:00"
              },
              {
                "Bandwidth": 5.84,
                "Flux": 219.09,
                "PeakTime": "2020-09-09 00:05:00",
                "Time": "2020-09-09 00:10:00"
              }
            ]
          }
        ]
      }
    ],
    "RequestId": "xx"
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
*Source: [https://www.tencentcloud.com/document/product/267/38514](https://www.tencentcloud.com/document/product/267/38514)*
