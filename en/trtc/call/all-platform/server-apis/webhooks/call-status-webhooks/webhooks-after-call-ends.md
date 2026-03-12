# Webhooks after Call Ends

## Feature Description

The App backend can monitor in real-time the dynamics of call ending through this callback. Five seconds after call termination, call details can be queried through the call record inquiry API.

## Must-Knows

- To enable the callback, you must configure the callback URL through the REST API and turn on the switch corresponding to this callback protocol. For the configuration method, see [Set Callback Configuration](https://www.tencentcloud.com/document/product/647/68938).
- The direction of the callback is that the Call backend initiates an HTTP POST request to the App backend.
- After receiving a callback request, the App backend needs to verify whether the value of the SDKAppID parameter in the request URL is its own SDKAppID.

## Callback Triggering Scenarios

Call termination.

## Callback Triggering Timing

When the number of call participants is less than or equal to 1, trigger call termination and reclaim.

## API Description

### Sample Request URL

In the following example, the callback URL configured for the App is `https://www.example.com`.

**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json&ClientIP=$ClientIP&OptPlatform=$OptPlatform
```

### Request Parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST |
| www.example.com | Callback URL |
| SdkAppid | Assigned SDKAppID in the Chat console when creating an application |
| CallbackCommand | Fixed as `Call.CallbackAfterEndCall` |
| contenttype | The value is fixed as `json` |
| ClientIP | Client IP address, in the format of `127.0.0.1` |
| OptPlatform | Client platform. For the parameter values, see the description of the OptPlatform parameter in [Third-Party Callback Introduction: Callback Protocol](https://www.tencentcloud.com/zh/document/product/1047/34354#.E5.9B.9E.E8.B0.83.E5.8D.8F.E8.AE.AE) |

### Sample Request Packet

```
{    "CallbackCommand":"Call.CallbackAfterEndCall",    "CallRecord": {		"CallId": "055662e1-bc8a-469c-a334-1126c8c17d58",		"Caller_Account": "10001",		"MediaType": "Audio",		"CallType": "SingleCall",		"StartTime": 1741231146,		"EndTime": 1741231296,		"AcceptTime": 0,		"CallResult": "NotAnswer",		"CalleeList_Account": ["10001", "user2"],		"RoomId": "roomid-1434",		"RoomIdType": 2	}    "EventTime":1703589922780}
```

### Request Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Callback command |
| CallRecord | Struct | Call record information |
| CallId | String | Call ID |
| Caller_Account | String | Caller ID |
| MediaType | String | Media type:`Video` video call`Audio` audio call |
| CallType | String | Call type:`SingleCall` one-to-one call`MultiCall` group call |
| StartTime | Integer | Call initiation timestamp (in seconds) |
| EndTime | Integer | Call end timestamp (in seconds) |
| AcceptTime | Integer | Call connection timestamp (in seconds) |
| CallResult | String | Call result`Cancel`: Caller cancels the call before connecting.`Reject`: recipient decline the call`NotAnswer`: recipient timeout before answering`NormalEnd`: Call connected and ended normally`CallBusy`: call busy`Interrupt`: Call interrupted due to reasons such as network issues`Offline`: The server detects heartbeat expiry, causing the call to end. |
| CalleeList_Account | Array | Call Member List |
| RoomId | String | TRTC Room ID |
| RoomIdType | Integer | RoomId type:`1` Digit room number`2` String room number |
| EventTime | Integer | Event-triggered timestamp in milliseconds |

### Sample Response Packet

The response packet is returned after the App backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore the callback result.}
```

### Response Packet Fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Required | Request processing result. OK: successful processing; FAIL: processing failed |
| ErrorInfo | String | Required | Error message |
| ErrorCode | Integer | Required | Error code. Enter 0 here to ignore the callback result |


---
*Source: [https://trtc.io/document/68940](https://trtc.io/document/68940)*
