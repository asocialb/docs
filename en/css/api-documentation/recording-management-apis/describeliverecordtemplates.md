# DescribeLiveRecordTemplates

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to get the recording template list.

A maximum of 500 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: DescribeLiveRecordTemplates. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| IsDelayLive | No | Integer | Whether it is an LCB template. Default value: 0. 0: LVB. 1: LCB. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| Templates | Array of [RecordTemplateInfo](https://www.tencentcloud.com/document/api/267/30767#RecordTemplateInfo) | Recording template information list. |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=DescribeLiveRecordTemplates
&IsDelayLive=1
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
        "Templates": [
            {
                "TemplateId": 1000,
                "TemplateName": "testName",
                "IsDelayLive": 1,
                "Description": "test",
                "FlvParam": {
                    "Enable": 0,
                    "RecordInterval": 1800,
                    "StorageTime": 6000,
                    "VodSubAppId": 123456
                },
                "Mp4Param": {
                    "ClassId": 0,
                    "StorageMode": "xx",
                    "StorageTime": 0,
                    "VodSubAppId": 0,
                    "VodFileName": "xx",
                    "Enable": 0,
                    "RecordInterval": 0,
                    "Procedure": "xx"
                },
                "AacParam": {
                    "ClassId": 0,
                    "StorageMode": "xx",
                    "StorageTime": 0,
                    "VodSubAppId": 0,
                    "VodFileName": "xx",
                    "Enable": 0,
                    "RecordInterval": 0,
                    "Procedure": "xx"
                },
                "Mp3Param": {
                    "ClassId": 0,
                    "StorageMode": "xx",
                    "StorageTime": 0,
                    "VodSubAppId": 0,
                    "VodFileName": "xx",
                    "Enable": 0,
                    "RecordInterval": 0,
                    "Procedure": "xx"
                },
                "HlsParam": {
                    "Enable": 1,
                    "RecordInterval": 1800,
                    "StorageTime": 600,
                    "VodSubAppId": 123456
                },
                "HlsSpecialParam": {
                    "FlowContinueDuration": 60
                }
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
| InternalError | Internal error. |
| InternalError.ArgsNotMatch | For the transcoding template adding API. |
| InternalError.ConfInUsed | The template is in use. |
| InternalError.ConfNotFound | The template does not exist. |
| InternalError.InvalidInput | Parameter check failed. |
| InternalError.NotFound | The record does not exist. |
| InternalError.RuleAlreadyExist | The rule has already been configured. |
| InternalError.RuleInUsing | The rule is in use. |
| InternalError.RuleNotFound | The rule does not exist. |
| InvalidParameter | Invalid parameter. |
| InvalidParameterValue | Invalid parameter value. |
| MissingParameter | Parameter missing. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30839](https://www.tencentcloud.com/document/product/267/30839)*
