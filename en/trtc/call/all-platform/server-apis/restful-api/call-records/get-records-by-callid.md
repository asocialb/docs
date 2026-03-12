# Get Records by CallId

## Feature Description

App admins can use this API to obtain the call record information of the specified CallId.

> **Warning:**If you use the deprecated interfaces`TUICallKit.call()` or `TUICallKit.groupCall()`to initiate a call, please check the**Deprecated Document** directory. If you have any questions, you can contact: info_rtc@tencent.com.

## API Call Description

### Sample Request URL

```
https://xxxxxx/v4/call_record_http_srv/get_record_by_callid?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

### Request Parameters

The following table only lists the parameters involved in modification when calling this API and their descriptions. For more parameter details, please see [REST API Introduction](https://www.tencentcloud.com/document/product/647/68926).

| Parameter | Description |
| --- | --- |
| xxxxxx | Dedicated domain name corresponding to the country/region where the SDKAppID resides:China: `console.tim.qq.com`Singapore: `adminapisgp.im.qcloud.com`Seoul: `adminapikr.im.qcloud.com`Frankfurt: `adminapiger.im.qcloud.com`Silicon Valley: `adminapiusa.im.qcloud.com`Jakarta: `adminapiidn.im.qcloud.com` |
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
{  "CallId": "04c9a0ac-8e38-4a19-be45-349c5ce7911b"}
```

### Request Packet Fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| CallId | String | Required | Call ID |

### Response Package Example

**Basic form**

```
{	"ErrorCode": 0,	"ErrorInfo": "",	"ActionStatus": "OK",	"RequestId": "Id-da9b3ee8bece466d951a9d93965c3d2c-O-Seq-324151555",	"Response": {		"CallRecord": {			"CallId": "04c9a0ac-8e38-4a19-be45-349c5ce7911b",			"Caller_Account": "user1",			"MediaType": "Audio",			"CallType": "MultiCall",			"StartTime": 1739868165,			"EndTime": 1740064224,			"AcceptTime": 1739872743,			"CallResult": "NormalEnd",			"CalleeList_Account": [				"user1",				"user5",				"user2"			],            "RoomId": "roomid-1434",            "RoomIdType": 2		}	}}
```

### Response Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| ErrorCode | Integer | Error code, 0 indicates success, non-zero indicates failure |
| ErrorInfo | String | Error message |
| ActionStatus | String | Request processing result. OK: processing successful; FAIL: processing failed |
| RequestId | String | Unique request ID. It is returned for each request. RequestId is required for locating a problem |
| CallRecord | Struct | Call record information |
| CallId | String | Call ID |
| Caller_Account | String | Caller ID |
| MediaType | String | Media type:`Video` video call`Audio` audio call |
| CallType | String | Call Type:`SingleCall` one-to-one call`MultiCall` group call |
| StartTime | Integer | Call initiation timestamp (in seconds) |
| EndTime | Integer | Call end timestamp (in seconds) |
| AcceptTime | Integer | Call connection timestamp (in seconds) |
| CallResult | String | Call result`Cancel`: caller cancel the call before connecting`Reject`: recipient decline the call`NotAnswer`: recipient timeout before answering`NormalEnd`: Call connected and ended normally`CallBusy`: call busy`Interrupt`: Call interrupted due to reasons such as network issues |
| CalleeList_Account | Array | Call Member List |
| RoomId | String | TRTC Room ID |
| RoomIdType | Integer | RoomId type:`1` digit room number`2` string Room Number |

## Error Code Description

Unless a network error (for example, 502 error) occurs, the HTTP return code of this API is 200. The actual error code and error information are indicated by ErrorCode and ErrorInfo in the response packet body.

For common error codes (60000 to 79999), see the [Error Code](https://www.tencentcloud.com/document/product/647/54901) document.

The private error codes of this API are as follows:

| Error Code | Description |
| --- | --- |
| 101001 | Internal server error, please retry. |
| 101050 | The call record does not exist. |


---
*Source: [https://trtc.io/document/68930](https://trtc.io/document/68930)*
