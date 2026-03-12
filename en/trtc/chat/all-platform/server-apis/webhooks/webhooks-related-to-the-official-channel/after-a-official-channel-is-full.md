# After a Official Channel Is Full

## Feature Overview

This webhook allows the app backend to monitor in real-time if the subscription count for the Official Channel has reached its limit, ensuring users can subscribe.

## Notes

- To enable the webhook, you must configure the Webhook URL and toggle on the corresponding protocol. For more information on the configuration method, see [Webhook Configuration](https://www.tencentcloud.com/document/product/1047/34520).
- During this webhook, the Chat backend initiates an HTTP POST request to the app backend.
- After receiving the webhook request, the app backend must check whether the SDKAppID contained in the request URL is the `SDKAppID` of the app.
- For additional safety-related concerns, please refer to the [Webhook Overview: Security Considerations](https://www.tencentcloud.com/document/product/1047/34354) document.

## Webhook Triggering Scenarios

- App users subscribe to the Official Channel through the client.
- The app admin adds subscribers via the REST API.

## Webhook Triggering Timing

After a user successfully subscribes to the Official Channel.

## API Calling Description

### Sample request URL

In the subsequent example, the webhook URL configured within the app is `https://www.example.com`.
**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json&ClientIP=$ClientIP&OptPlatform=$OptPlatform
```

### Request parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST. |
| www.example.com | Webhook URL. |
| SdkAppid | SDKAppID assigned by the Chat console when an app is created. |
| CallbackCommand | Fixed as:OfficialAccount.CallbackAfterOfficialAccountFull. |
| contenttype | Fixed value: JSON. |
| ClientIP | Client IP, such as: 127.0.0.1. |
| OptPlatform | Client Platform, for values please refer to [Webhook Overview: Webhook Protocol](https://www.tencentcloud.com/document/product/1047/34354) for the meaning of the OptPlatform parameter. |

### Sample request

```
{    "CallbackCommand": "OfficialAccount.CallbackAfterOfficialAccountFull", // Webhook command    "Official_Account" : "@TOA#_test_OA_for_penn",    "EventTime": 1670574414123// Millisecond Level, Event Trigger Timestamp		}
```

### Request fields

| Object | Features | Feature |
| --- | --- | --- |
| CallbackCommand | String | Webhook command. |
| Official_Account | String | User ID of the Official Channel with the maximum number of subscribers. |
| EventTime | Integer | Event trigger timestamp in milliseconds. |

### Sample response

After the app backend records that the supported number of subscribers for the Official Channel has reached its limit, it sends the webhook response package.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore response results}
```

### Response fields

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Mandatory | Processed Request Result:OK: Indicates successful processingFAIL: Indicates failure |
| ErrorCode | Integer | Mandatory | Error Code, 0 means response results can be ignored. |
| ErrorInfo | String | Mandatory | Error message. |

## References

- [Webhook Overview](https://www.tencentcloud.com/document/product/1047/34354)
- REST API:[Adding Subscribers](https://www.tencentcloud.com/document/product/1047/60760#)


---
*Source: [https://trtc.io/document/60801](https://trtc.io/document/60801)*
