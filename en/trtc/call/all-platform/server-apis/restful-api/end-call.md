# End Call

## Feature Description

The App admin can use this API to end call.

## API Call Description

### Sample Request URL

```
https://console.tim.qq.com/v4/call_engine_http_srv/end_call?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

### Request Parameters

The following table lists only the parameters involved in modification when calling this API and its description. For more details about the parameters, please refer to [REST API Introduction](https://www.tencentcloud.com/document/product/647/68926).

| Parameters | Overview |
| --- | --- |
| xxxxxx | SDKAppID is located in the country/region of the dedicated domain name:China: `console.tim.qq.com`Singapore: `adminapisgp.im.qcloud.com`Seoul: `adminapikr.im.qcloud.com`Frankfurt: `adminapiger.im.qcloud.com`Silicon Valley: `adminapiusa.im.qcloud.com`Jakarta: `adminapiidn.im.qcloud.com` |
| v4/call_engine_http_srv/end_call | Request API. |
| sdkappid | The SDKAppID assigned by the IM console when creating an application. |
| identifier | must be an App administrator account. For more details, see App admin. |
| usersig | The generated signature by an App administrator account. For details, see [generate UserSig](https://www.tencentcloud.com/document/product/647/35166). |
| random | Enter a random 32-bit unsigned integer in the range of [0, 4294967295]. |
| contenttype | The request format is fixed as `json`. |

### Maximum Calling Frequency

200 requests per second.

### Sample Request Packet

**Basic form**

```
{  "CallId": "055662e1-bc8a-469c-a334-1126c8c17d58"}
```

### Request Packet Fields

| Field | Type | Attribute | Overview |
| --- | --- | --- | --- |
| CallId | String | Required | Call ID |

### Response Package Example

**Basic form**

```
{    "ErrorCode": 0,    "ErrorInfo": "",    "ActionStatus": "OK",    "RequestId": "Id-431454f25a44462d8155bdff4fed38cc-O-Seq-19029769"}
```

### Response Packet Fields

| Field | Type | Overview |
| --- | --- | --- |
| ErrorCode | Integer | Error code: 0 indicates success, non-0 indicates failure. |
| ErrorInfo | String | Error Message. |
| ActionStatus | String | Request processing result. OK: processing successful; FAIL: processing failed. |
| RequestId | String | Unique request ID, returned for each request. RequestId is required for locating a problem. |

## Error Code Description

Unless a network error occurs (such as 502 error), the HTTP return code of this API is 200. The actual error code and error information are represented by ErrorCode and ErrorInfo in the response payload.

Common error codes (60000 to 79999), please refer to the [Error Code](https://www.tencentcloud.com/document/product/647/54901) document.

Private error codes of this API are as follows:

| Error Code | Description |
| --- | --- |
| 101001 | Internal server error, please retry. |
| 101002 | Invalid parameter. Check whether the request is correct according to the error description. |
| 101004 | The call does not exist, or it may have existed but has already ended. |


---
*Source: [https://trtc.io/document/74506](https://trtc.io/document/74506)*
