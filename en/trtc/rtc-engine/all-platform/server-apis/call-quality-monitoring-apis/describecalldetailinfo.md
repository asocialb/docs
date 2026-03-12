# DescribeCallDetailInfo

## 1. API Description

Domain name for API request: trtc.intl.tencentcloudapi.com.

This API (the old `DescribeCallDetail`) is used to query the user list and call quality data of a specified time range in the last 14 days. If `DataType` is not null, the data of up to six users during a period of up to one hour can be queried (the period can start and end on different days). If `DataType` is null, the data of up to 100 users can be returned per page (the value of `PageSize` cannot exceed 100). Six users are queried by default. The period queried cannot exceed four hours. This API is used to query call quality and is not recommended for billing purposes.
**Note**:

You can use this API to query historical data or for reconciliation purposes, but we do not recommend you use it for crucial business logic.
If you need to call this API, please upgrade the monitoring dashboard version to "Standard". For more details, please refer to: https://trtc.io/document/54481?product=pricing.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/647/34263).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: DescribeCallDetailInfo. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: 2019-07-22. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/647/34263#region-list) supported by the product. This API only supports: ap-beijing, ap-guangzhou, ap-mumbai, ap-singapore. |
| CommId | Yes | String | The unique ID of a call, whose format is `SdkAppId_CreateTime`, such as `1400xxxxxx_218695_1590065777`. `createTime` is the UNIX timestamp (seconds) when the room was created. Its value can be obtained using the [DescribeRoomInfo](https://intl.cloud.tencent.com/document/product/647/44050?from_cn_redirect=1) API. |
| StartTime | Yes | Integer | The start time, which is a Unix timestamp (seconds) in local time, such as `1590065777`. |
| EndTime | Yes | Integer | The end time, which is a Unix timestamp (seconds) in local time, such as `1590065877`. Note: If `DataType` is not null, the end time and start time cannot be more than one hour apart; if `DataType` is null, the end time and start time cannot be more than four hours apart. |
| SdkAppId | Yes | Integer | The application ID, such as `1400xxxxxx`. |
| UserIds.N | No | Array of String | The users to query. If you do not specify this, the data of six users will be returned. |
| DataType.N | No | Array of String | The metrics to query. If you do not specify this, only the user list will be returned. If you pass in `all`, all metrics will be returned. `appCpu`: The CPU utilization of the application. `sysCpu`: The CPU utilization of the system. `aBit`: The upstream/downstream audio bitrate (bps). `aBlock`: The audio stutter duration (ms). `bigvBit`: The upstream/downstream video bitrate (bps). `bigvCapFps`: The frame rate for capturing videos. `bigvEncFps`: The frame rate for sending videos. `bigvDecFps`: The rendering frame rate. `bigvBlock`: The video stutter duration (ms). `aLoss`: The upstream/downstream audio packet loss. `bigvLoss`: The upstream/downstream video packet loss. `bigvWidth`: The upstream/downstream resolution (width). `bigvHeight`: The upstream/downstream resolution (height). |
| PageNumber | No | Integer | The page number. The default is 0. Note: If `PageNumber` or `PageSize` is not specified, six records will be returned. |
| PageSize | No | Integer | The number of records per page. The default is `6`. Value range: 1-100. Note: If `DataType` is not null, the length of the array `UserIds` and the value of `PageSize` cannot exceed `6`. If `DataType` is null, the length of the array `UserIds` and the value of `PageSize` cannot exceed `100`. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| Total | Integer | The number of records returned. |
| UserList | Array of [UserInformation](https://www.tencentcloud.com/document/api/647/36760#UserInformation) | The user information. Note: This field may return null, indicating that no valid values can be obtained. |
| Data | Array of [QualityData](https://www.tencentcloud.com/document/api/647/36760#QualityData) | The call quality data. Note: This field may return null, indicating that no valid values can be obtained. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Querying the user list and call metrics

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: DescribeCallDetailInfo
<Common request parameters>

{
    "DataType": [
        "bigvCapFps"
    ],
    "CommId": "1400188366_218695_1590065777",
    "EndTime": 1590065877,
    "SdkAppId": 1400188366,
    "StartTime": 1590065777
}
```

#### Output Example

```json
{
    "Response": {
        "Total": 1,
        "UserList": [
            {
                "RoomStr": "218695",
                "UserId": "1716",
                "JoinTs": 1590065777,
                "LeaveTs": 1590067658,
                "Finished": true,
                "DeviceType": "",
                "SdkVersion": "4.3.14",
                "ClientIp": "10.4.1.13"
            }
        ],
        "Data": [
            {
                "Content": [
                    {
                        "Time": 1590065779,
                        "Value": 0
                    },
                    {
                        "Time": 1590065781,
                        "Value": 0
                    },
                    {
                        "Time": 1590065783,
                        "Value": 0
                    },
                    {
                        "Time": 1590065785,
                        "Value": 0
                    },
                    {
                        "Time": 1590065787,
                        "Value": 0
                    },
                    {
                        "Time": 1590065789,
                        "Value": 0
                    }
                ],
                "PeerId": "",
                "UserId": "1716",
                "DataType": "bigvCapFps"
            }
        ],
        "RequestId": "2e12e365-43e8-4efd-902d-906303e2ee4a"
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

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/647/34270#common-error-codes).

| Error Code | Description |
| --- | --- |
| InternalError | Internal error. |
| InternalError.DBError | An error occurred while querying the database. |
| InternalError.EsQueryError | An error occurred during an ES query. |
| InternalError.HttpParaseFalied | Failed to parse the HTTP request. |
| InternalError.InterfaceErr | API error. |
| InternalError.MethodErr | Unsupported method. |
| InvalidParameter | Parameter error. |
| InvalidParameter.BodyParamsError | Failed to parse body parameters. |
| InvalidParameter.EncodeParams | Invalid `EncodeParams`. |
| InvalidParameter.PageNumber | Invalid `PageNumber`. |
| InvalidParameter.PageSize | Invalid `PageSize`. |
| InvalidParameter.PageSizeOversize | The value of `PageSize` exceeds 100. |
| InvalidParameter.QueryScaleOversize | The query period exceeds the limit. |
| InvalidParameter.SdkAppId | `SdkAppId` is incorrect. |
| InvalidParameter.SdkAppid | Inoperable `SdkAppid`. |
| InvalidParameter.StartTimeOversize | The query start time exceeds the range allowed by the current dashboard edition. For details, see https://intl.cloud.tencent.com/document/product/647/81331?from_cn_redirect=1 |
| InvalidParameter.StartTs | Invalid `StartTs`. |
| InvalidParameter.StartTsOversize | The start time for query exceeded the limit. |
| InvalidParameter.UserIdsMorethanSix | The number of users exceeds 6. |
| MissingParameter | Missing parameter. |
| MissingParameter.CommId | `CommId` is missing. |
| MissingParameter.CommIdOrSdkAppId | `SdkAppId` or `CommID` missing. |
| MissingParameter.EndTs | `endTS_s` is missing. |
| MissingParameter.SdkAppId | `SdkAppId` is missing. |
| MissingParameter.StartTs | `startTS_s` is missing. |


---
*Source: [https://trtc.io/document/55013](https://trtc.io/document/55013)*
