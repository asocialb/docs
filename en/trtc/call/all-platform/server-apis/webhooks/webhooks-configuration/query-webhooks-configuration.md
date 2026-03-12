# Query Webhooks Configuration

## Feature Description

App admins can query the callback configuration through this API.

> **Warning:**If you use the deprecated interfaces`TUICallKit.call()` or `TUICallKit.groupCall()`to initiate a call, please check the**Deprecated Document** directory. If you have any questions, you can contact: info_rtc@tencent.com.

## API Call Description

### Sample Request URL

```
https://console.tim.qq.com/v4/call_config/get_callback?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

### Request Parameters

The following table only lists the parameters involved in modification when calling this API and their descriptions. For more parameter details, please see [REST API Introduction](https://www.tencentcloud.com/document/product/647/68926#).

| Parameter | Description |
| --- | --- |
| xxxxxx | Dedicated domain name corresponding to the country/region where the SDKAppID resides:China: `console.tim.qq.com`Singapore: `adminapisgp.im.qcloud.com`Seoulï¼ `adminapikr.im.qcloud.com` |
| v4/call_record_http_srv/get_record_by_callid | Request API |
| sdkappid | Assigned SDKAppID in the Chat console when creating an application |
| identifier | Must be an App administrator account. For more details, see [App Administrator](https://trtc.io/document/33517) |
| usersig | Generated signature of the App administrator account. For specific operations, see [Generate UserSig](https://trtc.io/document/34385) |
| random | Enter a random 32-bit unsigned integer. The value ranges from 0 to 4294967295 |
| contenttype | The request format has a fixed value of `json` |

### Maximum Calling Frequency

200 times/second.

### Sample Request Packet

**Basic form**

```
{}
```

### Request Packet Fields

No.

### Sample Response Package Body

**Basic form**

```
{  "ErrorCode": 0,  "ErrorInfo": "",  "ActionStatus": "OK",  "RequestId": "Id-1cc8828fd3d84795ac866ced43b15b5c-O-Seq-61309",  "Response": {      "Url": "http://www.example.com/callback",      "CallbackCommandList": [        "Call.CallbackAfterStartCall",        "Call.CallbackAfterEndCall"      ]  }}
```

### Response Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| ErrorCode | Integer | Error code, 0 indicates success, non-zero indicates failure |
| ErrorInfo | String | Error message |
| ActionStatus | String | Request processing result. OK: successful processing; FAIL: failure |
| RequestId | String | Unique request ID. It is returned for each request. RequestId is required for locating a problem |
| Url | String | The callback address must start with `http/https`. It is recommend using the more secure `https` |
| CallbackCommandList | Array | The command word to trigger the callback, see [Callback Command Word List](https://www.tencentcloud.com/document/product/647/68934#) |

## Error Code Description

Unless a network error (for example, 502 error) occurs, the HTTP return code of this API is always 200. The actual error code and error information are indicated by ErrorCode and ErrorInfo in the response packet body.

For common error codes (60000 to 79999), see the [Error Code](https://www.tencentcloud.com/document/product/647/54901#) document.

The private error codes of this API are as follows:

| Error Code | Description of Meaning |
| --- | --- |
| 100001 | Server internal error, please retry |
| 100002 | Invalid parameter. Check whether the request is correct according to the error description |
| 100301 | The callback configuration does not exist. You can use the create callback configuration interface to create it |


---
*Source: [https://trtc.io/document/68937](https://trtc.io/document/68937)*
