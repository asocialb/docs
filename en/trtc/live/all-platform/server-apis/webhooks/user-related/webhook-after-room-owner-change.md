# Webhook After Room Owner Change

## Feature Description

The App backend can view room owner change information through the investigation.

## Note

- To enable this callback, you need to configure the callback URL and turn on the switch corresponding to this callback. For the configuration method, see [Webhook Configuration](https://www.tencentcloud.com/document/product/647/64418).
- The callback direction is from the Live backend to the App backend via an HTTP POST request.
- After receiving a callback request, the App backend needs to verify whether the value of the SDKAppID parameter in the request URL is its own SDKAppID.

## Callback Triggering Scenarios

- App user successfully modified the room owner through the client.
- App admin successfully modified the room owner via REST API.

## Callback Triggering Timing

The room owner was successfully modified.

## API Description

### Sample Request URL

In the following example, the callback URL configured for the App is `https://www.example.com`.

**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json
```

### Request Parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST. |
| www.example.com | Callback URL. |
| SdkAppid | The SDKAppID assigned in the Chat console when creating an application |
| CallbackCommand | Fixed as Live.CallbackAfterChangeOwner |
| contenttype | The value is fixed as JSON. |

### Sample Request Packet

```
{    "CallbackCommand":"Live.CallbackAfterChangeOwner",    "RoomId":"room_id",    "EventTime":1703589922780,    "Operator_Account":"admin",    "CurrentOwner_Account": "user2",    "OriginalOwner_Account": "user1"}
```

### Request Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Callback command. |
| RoomId | String | room ID |
| CurrentOwner_Account | String | new owner |
| OriginalOwner_Account | String | original owner |
| Operator_Account | String | Operator |
| EventTime | Interger | Event trigger timestamp, in milliseconds. |

### Sample Response Packet

The response packet is returned after the App backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore the callback result}
```

### Response Packet Fields

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Required | Request processing result. OK: processing successful; FAIL: processing failed. |
| ErrorCode | Integer | Required | Error code. Fill in 0 here to ignore the callback result. |
| ErrorInfo | String | Required | Error Message |

## References

- [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412)


---
*Source: [https://trtc.io/document/72553](https://trtc.io/document/72553)*
