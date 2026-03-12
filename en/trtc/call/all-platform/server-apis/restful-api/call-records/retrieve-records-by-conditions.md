# Retrieve Records by Conditions

## Feature Description

App admins can retrieve call records within 7 days under specified conditions using this API.

> **Warning:**If you use the deprecated interfaces`TUICallKit.call()` or `TUICallKit.groupCall()`to initiate a call, please check the**Deprecated Document** directory. If you have any questions, you can contact: info_rtc@tencent.com.

## API Call Description

### Sample Request URL

```
https://xxxxxx/v4/call_record_http_srv/get_record_by_filter?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

### Request Parameters

The following table only lists the parameters involved in modification when calling this API and their descriptions. For more details about the parameters, please see [REST API Introduction](https://www.tencentcloud.com/document/product/647/68926).

| Parameter | Description |
| --- | --- |
| xxxxxx | Dedicated domain name corresponding to the country/region where the SDKAppID resides:China: `console.tim.qq.com`Singapore: `adminapisgp.im.qcloud.com`Seoul: `adminapikr.im.qcloud.com`Frankfurt: `adminapiger.im.qcloud.com`Silicon Valley: `adminapiusa.im.qcloud.com`Jakarta: `adminapiidn.im.qcloud.com` |
| v4/call_record_http_srv/get_record_by_filter | Request API |
| sdkappid | Assigned SDKAppID in the Chat console when creating an application |
| identifier | Must be an App administrator account. For more details, see [App Administrator](https://trtc.io/document/33517) |
| usersig | Generated signature of the App administrator account. For specific operations, see [Generate UserSig](https://trtc.io/document/34385) |
| random | Enter a random 32-bit unsigned integer in the range of [0,4294967295] |
| contenttype | The request format has a fixed value of `json` |

### Maximum Calling Frequency

200 times/second.

### Sample Request Packet

**Basic form**

Query all call records within 7 days, default query the first 10 items on page 1.

```
{}
```

**Specified condition format**

```
{    "StartTime":0,         // Default to 7 days before the current time    "EndTime":1740531683,  // Default to the current time    "CallResult":"NormalEnd",    "CallType":"SingleCall",    "NumberPerPage":2,    "Page":2}
```

### Request Packet Fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| StartTime | Integer | Optional | Search for the call record start time. Default to 7 days before the current time. If the entered time is less than the default time, the backend will automatically adjust it to the default time |
| EndTime | Integer | Optional | Search for the call record end time (in seconds). Default to the current time |
| NumberPerPage | Integer | Optional | Results per page. Default value: 10 |
| Page | Integer | Optional | Query the number of pages. If not filled in, the default is page 1 |

### Sample Response Package Body

**Basic form**

```
{    "ErrorCode": 0,    "ErrorInfo": "",    "ActionStatus": "OK",    "RequestId": "Id-d3d6aa216dcc4cf4a4eee19c4942e740-O-Seq-2556133",    "Response": {        "TotalNum": 141,        "Page":2,        "CallRecordList": [            {                "CallId": "04c9a0ac-8e38-4a19-be45-349c5ce7911b",                "Caller_Account": "147",                "MediaType": "Audio",                "CallType": "SingleCall",                "StartTime": 1739960242,                "EndTime": 1739960245,                "AcceptTime": 1739960244,                "CallResult": "NormalEnd",                "CalleeList_Account": [                    "147",                    "369"                ],                "RoomId": "roomid-1434",                "RoomIdType": 2            },            {                "CallId": "055662e1-bc8a-469c-a334-1126c8c17d58",                "Caller_Account": "3423",                "MediaType": "Video",                "CallType": "SingleCall",                "StartTime": 1739960500,                "EndTime": 1739960507,                "AcceptTime": 1739960503,                "CallResult": "NormalEnd",                "CalleeList_Account": [                    "3423",                    "3243"                ],                "RoomId": "roomid-1434",                "RoomIdType": 2            }        ]    }}
```

### Response Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| ErrorCode | Integer | Error code, 0 indicates success, non-zero indicates failure |
| ErrorInfo | String | Error message |
| ActionStatus | String | Request processing result. OK: processing successful; FAIL: processing failed |
| RequestId | String | Unique request ID. It is returned for each request. RequestId is required for locating a problem |
| TotalNum | Integer | Total number of this query |
| Page | Integer | When Page > 0, there is data. Incrementing Page by 1 allows you to Continue Request for subsequent data |
| CallId | String | Call ID |
| Caller_Account | String | Caller user ID |
| MediaType | String | Media type:`Video` video call`Audio` audio call |
| CallType | String | Call Type:`SingleCall` one-to-one call`MultiCall` group call |
| StartTime | Integer | Call initiation timestamp (in seconds) |
| EndTime | Integer | Call end timestamp (in seconds) |
| AcceptTime | Integer | Call connection timestamp (in seconds) |
| CallResult | Integer | Call result`Cancel`: caller cancel the call before connecting`Reject`: recipient decline the call`NotAnswer`: recipient timeout before answering`NormalEnd`: Call connected and ended normally`CallBusy`: busy line`Interrupt`: Call interrupted due to reasons such as network issues |
| CalleeList_Account | Array | Call Member List |
| RoomId | String | TRTC Room ID |
| RoomIdType | String | RoomId type:`1` digit room number`2` string Room Number |

## Error Code Description

Unless a network error (for example, 502 error) occurs, the HTTP return code of this API is 200. The actual error code and error information are indicated by ErrorCode and ErrorInfo in the response packet body.

For common error codes (60000 to 79999), see the [Error Code](https://www.tencentcloud.com/document/product/647/54901) document.

The private error codes of this API are as follows:

| Error Code | Description of Meaning |
| --- | --- |
| 101001 | Internal server error, please retry |
| 101050 | Call records do not exist |


---
*Source: [https://trtc.io/document/68931](https://trtc.io/document/68931)*
