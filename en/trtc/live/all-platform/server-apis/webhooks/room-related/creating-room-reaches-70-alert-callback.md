# Creating Room Reaches 70% Alert Callback

## Feature Description

The App backend can view the number of creations in the current room through this callback.

## Precautions

- To enable callback, you must configure the callback URL and turn on the switch corresponding to this callback protocol. For the configuration method, see [Third-Party Callback Configuration](https://www.tencentcloud.com/document/product/647/64420#).
- The callback direction is from the Live backend to the App backend via an HTTP POST request.
- After receiving a callback request, the App backend needs to verify whether the value of the SDKAppID parameter in the request URL is its own SDKAppID.

## Callback Triggering Scenarios

- App users create a room through the client.
- App admins create a room via REST API.

## Callback Triggering Timing

Room created successfully.

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
| https | The request protocol is HTTPS, and the request method is POST. |
| www.example.com | Callback URL |
| SdkAppid | The SDKAppID assigned in the IM console when creating an application |
| CallbackCommand | `Live.CallbackAfterCreateRoomReachingThreshold` |
| contenttype | The value is fixed as `json`. |
| ClientIP | Client IP address, in the format of `127.0.0.1`. |
| OptPlatform | Client platform. For the valid values, see the description of the OptPlatform parameter in Webhook Protocol in [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412#). |

### Sample Request Packet

```
{    "CallbackCommand": "Live.CallbackAfterCreateRoomReachingThreshold",    "Operator_Account": "brennanli",    "EventTime": 1739966441121,    "CurRoomCount": 400,    "MaxRoomCount": 500}
```

### Request Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | callback command |
| Operator_Account | String | Operator UserID that triggers the createRoom request |
| CurRoomCount | String | Current room creation count |
| MaxRoomCount | Array | Maximum room creation count |
| EventTime | Integer | Event trigger timestamp, in milliseconds. |

### Sample Response Packet

The response packet is returned after the App backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore the callback result}
```

### Response Packet Fields

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Required | Request processing result. OK: processing successful; FAIL: processing failed. |
| ErrorInfo | String | Required | Error Message |
| ErrorCode | Integer | Required | Error code. Enter 0 here to ignore the callback result. |

## References

- [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412)


---
*Source: [https://trtc.io/document/70485](https://trtc.io/document/70485)*
