# Start Call (By Robot)

## Feature Description

The App admin can use this API to initiate a robot call.

## API Call Description

### Sample Request URL

```
https://console.tim.qq.com/v4/call_engine_http_srv/start_call_by_robot?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

### Request Parameters

The following table lists only the parameters involved in modification when calling this API and their descriptions. For more details about the parameters, please refer to [REST API Introduction](https://www.tencentcloud.com/document/product/647/68926).

| Parameters | Overview |
| --- | --- |
| xxxxxx | SDKAppID resides in the country/region where the dedicated domain name is located.China: `console.tim.qq.com`Singapore: `adminapisgp.im.qcloud.com`Seoul: `adminapikr.im.qcloud.com`Frankfurt: `adminapiger.im.qcloud.com`Silicon Valley: `adminapiusa.im.qcloud.com`Jakarta: `adminapiidn.im.qcloud.com` |
| v4/call_engine_http_srv/start_call_by_robot | Request API. |
| sdkappid | The SDKAppID assigned by the IM console when creating an application. |
| identifier | Must be an App administrator account. For more details, see App admin. |
| usersig | The generated signature of the App administrator account. For specific operations, see [generate UserSig](https://www.tencentcloud.com/document/product/647/35166). |
| random | Enter a random 32-bit unsigned integer, value ranges from 0 to 4294967295. |
| contenttype | The request format is fixed as `json`. |

### Maximum Calling Frequency

200 times/second.

### Sample Request Packet

**Basic form**

```
{    "Robot_Account":"user1",    "CalleeList_Account":["user5"],    "Timeout":300000,    "UserData":"userdata-12345687",    "CallInfo":{        "MediaType": "Audio",        "RoomIdType":2,        "RoomId":"roomid-1234"    },    "OfflinePushInfo": {        "PushFlag": 0,        "Title":"This is the push title",        "Desc": "This is the offline push content"        "Ext": "This is the transmitted content"    }}
```

### Request Packet Fields

| Field | Type | Attribute | Overview |
| --- | --- | --- | --- |
| Robot_Account | String | Required | Caller robot UserID. The backend does not perform heartbeat health check or busy line check on this UserID. |
| CalleeList_Account | Array | Required | Callee UserID list. |
| Timeout | Integer | Required | Timeout period (unit: ms), range: 10000 - 600000 ms. |
| UserData | String | Optional | Custom data will be passed to the callee side through call initiation notification, with a maximum of 1000 bytes. |
| CallInfo | Object | Required | Call information. |
| MediaType | String | Required | Media type:Video call Audio call |
| RoomId | String | Optional | TRTC Room ID. |
| RoomIdType | Integer | Optional | RoomId type:`1`:digit room ID.`2`:string Room Number. |
| OfflinePushInfo | Object | Optional | Offline Push Notification Configuration. Please see [Message Format Description](https://www.tencentcloud.com/document/product/1047/33527). |

### Response Payload Example

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
| RequestId | String | Unique request ID, returned for each request. To troubleshoot a request, its RequestId should be provided. |

## Error Code Description

Unless a network error occurs (such as 502), this API's HTTP return code is 200. The actual error code and error information are in the response payload's ErrorCode and ErrorInfo.

Common error codes (60000 to 79999), see the [Error Code](https://www.tencentcloud.com/document/product/647/54901) document.

Private error codes of this API are as follows:

| Error Code | Description |
| --- | --- |
| 101001 | Internal server error, please retry. |
| 101002 | Invalid parameter. Check whether the request is correct according to the error description. |
| 101004 | The call does not exist, or it may have existed but has already ended. |


---
*Source: [https://trtc.io/document/74505](https://trtc.io/document/74505)*
