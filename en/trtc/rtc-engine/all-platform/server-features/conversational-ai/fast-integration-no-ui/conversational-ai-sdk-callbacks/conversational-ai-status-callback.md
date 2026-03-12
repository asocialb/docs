# Conversational AI Status Callback

Conversational AI of Tencent RTC provides rich status callbacks. These status callbacks are sent through custom messages of RTC Engine, enabling easy status switches in the client, including "Listening", "Thinking", "Speaking", and other statuses.

You can use the [Receive Custom Messages feature](https://www.tencentcloud.com/document/product/647/47866) provided by the RTC Engine SDK to listen to callbacks in the client to receive AI conversation status data. **The cmdID value is fixed at 1.**

## Features

1. Real-time synchronization: Status changes can be synchronized to all participants in real time.
2. Flexibility: The custom message format is used to facilitate integration and expansion.
3. Support for multiple statuses: Multiple statuses are supported, such as Listening, Thinking, Speaking, and Interrupted.

## Message Format

Status callback messages are in JSON format. The specific fields are as follows:

| Field | Type | Description |
| --- | --- | --- |
| type | Number | Message type. 10001 indicates the chatbot status. |
| sender | String | User ID of the sender, which is the chatbot ID. |
| receiver | Array | List of receivers' user IDs. The message is actually broadcasted in the room. |
| payload | Object | Message payload. It contains the detailed status information. |

The payload object contains the following fields:

| Field | Type | Description |
| --- | --- | --- |
| roundid | String | Unique ID that identifies a conversation round. |
| timestamp | Number | Timestamp, indicating the specific time of status change. |
| state | Number | Current status code of the chatbot. |

Status code description:

| Status Code | Description |
| --- | --- |
| 1 | Listening |
| 2 | Thinking |
| 3 | Speaking |
| 4 | Interrupted |

## Example Message

```
{  "type": 10001,  "sender": "ai_assistant_001",  "receiver": [],  "payload": {    "roundid": "conversation_789012",    "timestamp": 1629384755,    "state": 2  }}
```

## Use Cases

1. UI feedback: Display corresponding UI elements based on the status, such as the animation of the Listening status.
2. Interaction control: Disable input by certain users when the AI chatbot is thinking or speaking to avoid interruptions.
3. Debugging and analysis: Use status information to perform conversation analysis for better user experience.


---
*Source: [https://trtc.io/document/68332](https://trtc.io/document/68332)*
