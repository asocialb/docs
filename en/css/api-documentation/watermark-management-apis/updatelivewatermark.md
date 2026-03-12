# UpdateLiveWatermark

## 1. API Description

Domain name for API request: live.intl.tencentcloudapi.com.

This API is used to update a watermark.

A maximum of 100 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/267/30763).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: UpdateLiveWatermark. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). The value used for this API: 2018-08-01. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/267/30763). This parameter is not required for this API. |
| WatermarkId | Yes | Integer | Watermark ID. Get the watermark ID in the returned value of the [AddLiveWatermark](https://intl.cloud.tencent.com/document/product/267/30154?from_cn_redirect=1) API call. |
| PictureUrl | Yes | String | Watermark image URL. Unallowed characters in the URL:  ;(){}$>`#"'\| |
| XPosition | Yes | Integer | Display position: X-axis offset in %. Default value: 0. |
| YPosition | Yes | Integer | Display position: Y-axis offset in %. Default value: 0. |
| WatermarkName | No | String | Watermark name. Up to 16 bytes. |
| Width | No | Integer | Watermark width or its percentage of the live streaming video width. It is recommended to just specify either height or width as the other will be scaled proportionally to avoid distortions. The original width is used by default. |
| Height | No | Integer | Watermark height or its percentage of the live streaming video width. It is recommended to just specify either height or width as the other will be scaled proportionally to avoid distortions. The original height is used by default. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| RequestId | String | The unique request ID, which is returned for each request. RequestId is required for locating a problem. |

## 4. Example

### Example1 Sample request

#### Input Example

```
https://live.intl.tencentcloudapi.com/?Action=UpdateLiveWatermark
&WatermarkId=123
&PictureUrl=http://watermark-10005041.cos.myqcloud.com/1251830167/watermark_img_Alogo.png
&XPosition=80
&YPosition=10
&WatermarkName=logo
&<Common request parameters>
```

#### Output Example

```json
{
    "Response": {
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
| InternalError.DBError | DB execution error. |
| InternalError.GetBizidError | Error getting user account. |
| InternalError.WatermarkEditError | An internal error occurred while modifying the watermark. |
| InternalError.WatermarkNotExist | The watermark does not exist. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.WatermarkNotExist | The watermark does not exist. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30818](https://www.tencentcloud.com/document/product/267/30818)*
