# Switch Seat(Old version)

## Feature Description

App admin can use this API to move the user to a certain empty microphone slot.

## API Call Description

### Sample Request URL

```
https://xxxxxx/v4/room_engine_http_mic/switch_seat?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

### Request Parameters

The following table lists only the parameters involved in modification when calling this API and their descriptions. For more details about the parameters, please refer to [REST API Introduction](https://www.tencentcloud.com/document/product/647/63398).

| Parameter | Description |
| --- | --- |
| xxxxxx | The dedicated domain name for the country/region where the SDKAppID resides:Singapore: `adminapisgp.im.qcloud.com` |
| v4/room_engine_http_mic/switch_seat | Request API |
| sdkappid | The SDKAppID assigned by the Chat console when creating an application |
| identifier | Must be an App administrator account. For more details, see [app admin](https://www.tencentcloud.com/document/product/647/69882#app-admin). |
| usersig | App administrator account generated signature. For details, see [generate UserSig](https://www.tencentcloud.com/document/product/647/69883) |
| random | Enter a random 32-bit unsigned integer in the range of [0, 4294967295] |
| contenttype | The request format is fixed as `json`. |

### Maximum Calling Frequency

200 times per second.

### Sample Request Packet

**Basic form**

```
{  "RoomId":"room-test",  "ToIndex": 1,  "Member_Account": "user"}
```

### Request Packet Fields

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| RoomId | String | Required | room ID |
| ToIndex | Integer | Required | Seat ID |
| Member_Account | String | Required | User ID |

### Response Package Example

**Basic form**

```
{  "ErrorCode": 0,  "ErrorInfo": "",  "ActionStatus": "OK",  "RequestId": "Id-7c1680be52734bdc8d6de398ab9505e7-O-Seq-57717"}
```

### Response Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| ActionStatus | String | Request processing result. OK: processing successful; FAIL: processing failed. |
| ErrorCode | Integer | Error code: 0 indicates success; non-zero indicates failure. |
| ErrorInfo | String | Error Message |
| RequestId | String | Unique request ID, returned for each request. RequestId is required for locating a problem. |

## Error Code Description

Unless a network error (such as 502) occurs, the HTTP return code of this API is 200. The actual error code and error information are indicated by ErrorCode and ErrorInfo in the response payload.

Common error codes (60000 to 79999), please refer to the [Error Code](https://www.tencentcloud.com/document/product/647/60027) document.

Private error codes of this API are as follows:

| Error Code | Description |
| --- | --- |
| 100001 | Internal server error, please retry. |
| 100002 | Invalid parameter. Check whether the request is correct according to the error description. |
| 100004 | The room does not exist, or it may have existed but has been dismissed. |


---
*Source: [https://trtc.io/document/72552](https://trtc.io/document/72552)*
