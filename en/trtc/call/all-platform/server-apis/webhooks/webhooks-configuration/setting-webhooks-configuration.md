# Setting Webhooks Configuration

## Feature Description

App admins can set callback configurations through this API. If it is not the first time to set the configuration, the new configuration will overwrite the old one.

> **Warning:**If you use the deprecated interfaces`TUICallKit.call()` or `TUICallKit.groupCall()`to initiate a call, please check the**Deprecated Document** directory. If you have any questions, you can contact: info_rtc@tencent.com.

## API Call Description

### Sample Request URL

```
https://xxxxxx/v4/call_config/set_callback?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
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

200 times per second.

### Sample Request Packet

**Basic form**

```
{  "Url":"http://www.example.com/callback",  "CallbackCommandList":[    "Call.CallbackAfterStartCall",    "Call.CallbackAfterEndCall",    "Call.CallbackAfterMemberChanged"  ]}
```

### Request Packet Fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| Url | String | Required | The callback address should start with `http/https`. It is recommend using the more secure `https` |
| CallbackCommandList | Array | Required | The command words that can trigger the callback, see [Callback Command Word List](https://www.tencentcloud.com/document/product/647/68934#) |

### Response Package Example

**Basic form**

```
{  "ActionStatus": "OK",  "ErrorInfo": "",  "ErrorCode": 0,  "RequestId": "Id-8c9858f01e954611ae2d4c1b1ed7d583-O-Seq-52720"}
```

### Response Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| ActionStatus | String | Request processing result. OK indicates successful processing. FAIL indicates failure |
| ErrorInfo | String | Error message |
| ErrorCode | Integer | Error code, 0 indicates success, non-zero indicates failure |
| RequestId | String | Unique request ID. It will be returned for each request. RequestId is required for locating a problem |

## Error Code Description

Unless a network error (for example, 502 error) occurs, the HTTP return code of this API is 200. The actual error code and error information are indicated by ErrorCode and ErrorInfo in the response packet body.

For common error codes (60000 to 79999),  see the [Error Code](https://www.tencentcloud.com/document/product/647/54901#) document.

The private error codes of this API are as follows:

| Error Code | Description of Meaning |
| --- | --- |
| 100001 | Server internal error. Please retry |
| 100002 | Invalid parameter. Check whether the request is correct according to the error description |


---
*Source: [https://trtc.io/document/68938](https://trtc.io/document/68938)*
