# Get Real-Time Call Status

## Feature Description

App admins can get real-time call status use this API.

> **Warning:**If you use the deprecated interfaces`TUICallKit.call()` or `TUICallKit.groupCall()`to initiate a call, please check the**Deprecated Document** directory. If you have any questions, you can contact: info_rtc@tencent.com.

## API Call Description

### Sample Request URL

```
https://xxxxxx/v4/call_engine_http_srv/get_call_info?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

### Request Parameters

The following table only lists the parameters involved in modification when calling this API and their descriptions. For more details about the parameters, please see [REST API Introduction](https://www.tencentcloud.com/document/product/647/68926).

| Parameter | Description |
| --- | --- |
| xxxxxx | Dedicated domain name corresponding to the country/region where the SDKAppID resides:China: `console.tim.qq.com`Singapore: `adminapisgp.im.qcloud.com`Seoul: `adminapikr.im.qcloud.com`Frankfurt: `adminapiger.im.qcloud.com`Silicon Valley: `adminapiusa.im.qcloud.com`Jakarta: `adminapiidn.im.qcloud.com` |
| v4/call_engine_http_srv/get_call_info | Request API |
| sdkappid | Assigned SDKAppID in the Chat console when creating an application |
| identifier | Must be an App administrator account. For more details, see [App Administrator](https://trtc.io/document/33517). |
| usersig | Generated signature of the App administrator account. For specific operations, see [Generate UserSig](https://trtc.io/document/34385) |
| random | Enter a random 32-bit unsigned integer in the range of [0,4294967295] |
| contenttype | The request format has a fixed value of `json` |

### Maximum Calling Frequency

200 times/second.

### Sample Request Packet

**Basic form**

```
{  "CallId": "055662e1-bc8a-469c-a334-1126c8c17d58"}
```

### Request Packet Fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| CallId | String | Required | Call ID |

### Sample Response Package Body

**Basic form**

```
{	"ErrorCode": 0,	"ErrorInfo": "",	"ActionStatus": "OK",	"RequestId": "Id-431454f25a44462d8155bdff4fed38cc-O-Seq-19029769",	"Response": {		"CallInfo": {			"CallId": "055662e1-bc8a-469c-a334-1126c8c17d58",			"MediaType": "Audio",			"ChatGroupId": "",			"RoomId": "",			"RoomIdType": 0		},		"UserList": [{				"User_Account": "user1",				"Status": "Calling"			},			{				"User_Account": "user2",				"Status": "Waiting"			}		]	}}
```

### Response Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| ErrorCode | Integer | Error code: 0 indicates success, non-zero indicates failure |
| ErrorInfo | String | Error message |
| ActionStatus | String | Request processing result. OK: processing successful; FAIL: processing failed |
| RequestId | String | Unique request ID. It is returned for each request. RequestId is required for locating a problem |
| CallId | String | Call ID |
| MediaType | String | Media type:`Video` video call`Audio` audio call |
| ChatGroupId | String | IM group ID |
| RoomId | String | TRTC Room ID |
| RoomIdType | Integer | TRTC room ID type:`1` digit room number`2` string Room Number |
| UserList | Array | Call Member List |
| User_Account | String | ID of the calling user |
| Status | String | Call status`Calling` on a call`Waiting` waiting to connect |

## Error Code Description

Unless a network error (for example, 502 error) occurs, the HTTP return code of this API is always 200. The actual error code and error information are represented by ErrorCode and ErrorInfo in the response packet body.

For common error codes (60000 to 79999), see the [Error Code](https://www.tencentcloud.com/document/product/647/54901) document.

The private error codes of this API are as follows:

| Error Code | Description |
| --- | --- |
| 101001 | Internal server error, please retry. |
| 101002 | Invalid parameter. Check whether the request is correct according to the error description. |
| 101004 | The call does not exist, or it once existed but has now ended. |


---
*Source: [https://trtc.io/document/68932](https://trtc.io/document/68932)*
