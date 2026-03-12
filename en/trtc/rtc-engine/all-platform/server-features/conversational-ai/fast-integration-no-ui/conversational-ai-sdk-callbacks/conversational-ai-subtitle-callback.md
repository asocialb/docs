# Conversational AI Subtitle Callback

Conversational AI of Tencent RTC provides the capability to display real-time subtitles. The real-time subtitles are sent through custom messages of Tencent RTC, enabling millisecond-level synchronization with the conversation audio.

You can use the [Receive Custom Messages feature](https://www.tencentcloud.com/document/product/647/47866) provided by the RTC Engine SDK to listen to callbacks in the client to receive data of real-time AI conversation subtitles. **The cmdID value is fixed at 1.**

## Features

1. Real-time synchronization: Subtitles are synchronized with the conversation audio with a millisecond-level latency.
2. Flexibility: The custom message format is used to facilitate integration and expansion.

## Message Format

Real-time subtitle messages are in JSON format. Specific fields are as follows:

| Field | Type | Description |
| --- | --- | --- |
| type | Number | Message type. 10000 indicates real-time subtitles. |
| sender | String | User ID of the sender. |
| receiver | Array | List of receivers' user IDs. The message is actually broadcasted in the room. |
| payload | Object | Message payload. It contains the detailed subtitle information. |

The payload object contains the following fields:

| Field | Type | Description |
| --- | --- | --- |
| text | String | Original text recognized by ASRï¼STTï¼. |
| start_time | String | Start time of a sentence. Format: "HH:MM:SS". |
| end_time | String | End time of a sentence. Format: "HH:MM:SS". |
| roundid | String | Unique ID that identifies a conversation round. |
| end | Boolean | If the value is true, the sentence is a complete one. |

## Example Message

```
{  "type": 10000,  "sender": "user_a",  "receiver": [],  "payload": {    "text": "Hello. Nice to meet you."    "start_time": "00:00:01",    "end_time": "00:00:03",    "roundid": "conversation_123456",    "end": true  }}
```

## Implementation Notes

1. Message processing: Receivers need to correctly parse the JSON message and recognize real-time subtitles based on the type field.
2. Time synchronization: You can use start_time and end_time to ensure the subtitles are properly synchronized with the audio.
3. Conversation segmentation: You can use the end field to determine if a sentence is finished. This can be used for subtitle display or complete conversation storage.

## Parsing a Custom Message with the Web SDK

```
    trtcClient.on(Tencent RTC.EVENT.CUSTOM_MESSAGE, (event) => {        let data = new TextDecoder().decode(event.data);        let jsonData = JSON.parse(data);        console.log(`receive custom msg from ${event.userId} cmdId: ${event.cmdId} seq: ${event.seq} data: ${data}`);                if (jsonData.type == 10000 && jsonData.payload.end == false) {            // The subtitle is not complete.        } else if (jsonData.type == 10000 && jsonData.payload.end == true) {           // The sentence is finished.         }    });
```


---
*Source: [https://trtc.io/document/68333](https://trtc.io/document/68333)*
