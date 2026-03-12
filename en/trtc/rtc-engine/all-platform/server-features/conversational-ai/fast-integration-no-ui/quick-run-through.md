# Quick Run-Through

This document describes how to implement a solution for conversational AI based on the RTC Engine SDK.

## Overview

In this solution, the service of RTC Engine is called based on the RTC Engine SDK. You can call the API of conversational AI to use this service with an extremely low latency. This solution is a very flexible integration solution. You can integrate third-party LLMs and TTS applications according to the actual business needs to improve business efficiency. In addition, technological optimizations for real-time voice denoising, AI interruption, and context management are made to continuously improve user experience.

## Architecture Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/468c07c321b211f08caa5254005ef0f7.png)

## Business Process Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5070390d21b211f09e67525400bf7822.png)

## Integration Instructions

### Prerequisites

[Activate the Service](https://www.tencentcloud.com/document/product/647/69002).

### I. Integrating the RTC Engine SDK

#### Step 1: Import the RTC Engine SDK Into the Project and Enter the Room

- [Integration Guide for iOS Without UI](https://trtc.io/document/62044?platform=ios&product=rtcengine&menulabel=sdk)
- [Integration Guide for Android Without UI](https://trtc.io/document/62045?platform=android&product=rtcengine&menulabel=sdk)
- [Integration Guide for Web & H5 Without UI](https://trtc.io/document/59649?platform=web&product=rtcengine&menulabel=sdk)
- [Integration Guide for Flutter Without UI](https://trtc.io/document/64203?platform=flutter&product=rtcengine&menulabel=sdk)

#### Step 2: Releasing the Audio Stream

Android&iOS&Flutter

Web&H5

You can call startLocalAudio to enable capture via microphone. You need to set the quality parameter to determine the capture mode. Note that a large quality value does not always ensure high quality. You need to set a proper value for different business scenarios. (This parameter actually indicates the scene.)

**SPEECH mode is recommended for conversational AI scenarios**. In this mode, the audio module of the SDK focuses on refining the voice signal and filtering out ambient noise as much as possible. In addition, this mode can ensure the quality of audio data in environments with poor network quality. Therefore, this mode applies to scenarios that focus on vocal communication, such as "video calls" and "online meetings".

Android

iOS&Mac

Flutter

```
// Enable capture via microphone and set the mode to SPEECH mode (strong denoising capability and resistance to poor network conditions).mCloud.startLocalAudio(Tencent RTCCloudDef.Tencent RTC_AUDIO_QUALITY_SPEECH );
```

```
self.trtcCloud = [Tencent RTCCloud sharedInstance];// Enable capture via microphone and set the mode to SPEECH mode (strong denoising capability and resistance to poor network conditions).[self.trtcCloud startLocalAudio:Tencent RTCAudioQualitySpeech];
```

```
// Enable capture via microphone and set the mode to SPEECH mode (strong denoising capability and resistance to poor network conditions).trtcCloud.startLocalAudio(Tencent RTCAudioQuality.speech);
```

Use the [trtc.startLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/TRTC.html#startLocalAudio) method to enable the microphone and release the audio stream to the room.

```
await trtc.startLocalAudio();
```

> **Note:**Conversational AI scenarios have high requirements for the denoising capability of the audio capture end. For a better experience, it is recommended to [enable the AI Denoiser](https://trtc.io/document/59658?platform=web&product=rtcengine&menulabel=sdk). In addition, a denoising model specially trained for conversational AI scenarios is provided. You can contact the business manager or [submit a ticket](https://trtc.io/contact) to contact us.

### II. Initiating an AI Conversation

#### Starting an AI Conversation: StartAIConversation

Call the [StartAIConversation](https://trtc.io/document/64963) API in the backend to add the chatbot to the room and initiate an AI conversation.

> **Note:**The value of `RoomId` should be consistent with that of `RoomId` used by the client to add the chatbot to the room. The room ID types (number/string) should also be the same, which means that the chatbot and user need to be in the same room.The values of `LLMConfig` and `TTSConfig` are in JSON format and need to be configured properly before you can successfully initiate an AI conversation.

**Descriptions of currently supported** `STTConfig``LLMConfig` **and** `TTSConfig` **configurations:**

- [Speech-to-Text(STTConfig)](https://www.tencentcloud.com/document/product/647/69592)
- [Large Language Model Configuration(LLMConfig)](https://www.tencentcloud.com/document/product/647/68338#)
- [Text-To-Speech Configuration(TTSConfig)](https://www.tencentcloud.com/document/product/647/68340#)

**It is recommended to verify the parameters of** `LLMConfig` **and** `TTSConfig` **in the following ways before you call the**[**StartAIConversation**](https://trtc.io/document/64963)**API for the first time. The detailed information is as follows:**

- [Conversational AI Parameter Verification](https://github.com/notedit/trtc-ai-api-check)
- [Conversational AI Parameter Validation (Online Address)](https://trtc-ai-api-check.streamlit.app/ !af5d234383ad4ec12a56602a8c21a115)

> **Note:**If no issue occurs after you perform all the above steps, you can now have a conversation with AI.

### III. Receiving the Data of AI Conversation Subtitles and Chatbot Status

You can use the [Receive Custom Messages](https://www.tencentcloud.com/document/product/647/47866) provided by the RTC Engine SDK to listen to callbacks in the client to receive the data such as real-time subtitles and chatbot statuses. **The cmdID value is fixed at 1**.

#### Receiving Real-Time Subtitles

Message format:

```
{  "type": 10000, // 10000 indicates the subtitles are real-time subtitles.  "sender": "user_a", // User ID of the sender (speaker).  "receiver": [], // List of receivers' user IDs. The message is actually broadcasted in the room.  "payload": {     "text":"", // Text recognized by speech recognition.     "translation_text":"", // Translated text.     "start_time":"00:00:01", // Start time of a sentence.     "end_time":"00:00:02", // End time of a sentence.     "roundid": "xxxxx", // Unique ID of a conversation round.     "end": true // If the value is true, the sentence is a complete one.  }}
```

#### Receiving the Chatbot Status Data

Message format:

```
{  "type": 10001, // Chatbot status.  "sender": "user_a", // User ID of the sender, which is the chatbot ID in this case.  "receiver": [], // List of receivers' user IDs. The message is actually broadcasted in the room.  "payload": {    "roundid": "xxx", // Unique ID of a conversation round.    "timestamp": 123,    "state": 1,      // 1: listening; 2: thinking; 3: speaking; 4: interrupted.  }}
```

#### Example Code

Android

iOS

Web&H5

```
@Overridepublic void onRecvCustomCmdMsg(String userId, int cmdID, int seq, byte[] message) {    String data = new String(message, StandardCharsets.UTF_8);    try {        JSONObject jsonData = new JSONObject(data);        Log.i(TAG, String.format("receive custom msg from %s cmdId: %d seq: %d data: %s", userId, cmdID, seq, data));    } catch (JSONException e) {        Log.e(TAG, "onRecvCustomCmdMsg err");        throw new RuntimeException(e);    }}
```

```
func onRecvCustomCmdMsgUserId(_ userId: String, cmdID: Int, seq: UInt32, message: Data) {    if cmdID == 1 {        do {            if let jsonObject = try JSONSerialization.jsonObject(with: message, options: []) as? [String: Any] {                print("Dictionary: \\(jsonObject)")                // handleMessage(jsonObject)            } else {                print("The data is not a dictionary.")            }        } catch {            print("Error parsing JSON: \\(error)")        }    }}
```

```
trtcClient.on(Tencent RTC.EVENT.CUSTOM_MESSAGE, (event) => {    let data = new TextDecoder().decode(event.data);    let jsonData = JSON.parse(data);    console.log(`receive custom msg from ${event.userId} cmdId: ${event.cmdId} seq: ${event.seq} data: ${data}`);            if (jsonData.type == 10000 && jsonData.payload.end == false) {        // Subtitle intermediate state    } else if (jsonData.type == 10000 && jsonData.payload.end == true) {       // That is all for this sentence.     }});
```

> **Note:**Some conversational AI callbacks in the client are provided. For details, see: [Conversational AI status callback](https://www.tencentcloud.com/document/product/647/68332#), [Conversational AI Subtitle Callback](https://www.tencentcloud.com/document/product/647/68333#), [Conversational AI Metrics Callback](https://www.tencentcloud.com/document/product/647/68334#), [Conversational AI Error Callback](https://www.tencentcloud.com/document/product/647/68335#).

### IV. Sending Custom Messages

Custom messages of RTC Engine are uniformly sent via the client, **cmdID is fixed at 2**.

See [Sending and Receiving Messages](https://www.tencentcloud.com/document/product/647/47866).

- You can skip the ASRï¼STTï¼ process by sending custom text and communicate directly with the AI service through text.

```
  {  "type": 20000, // Send a custom text message in the client.  "sender": "user_a", // User ID of the sender. The server will check if this user ID is valid.  "receiver": ["user_bot"], // List of receivers' user IDs. You need to enter the chatbot user ID only. The server will check if this user ID is valid.  "payload": {    "id": "uuid", // Message ID for troubleshooting. You can use the UUID.    "message": "xxx", // Message content.    "timestamp": 123 // Timestamp for troubleshooting.  }}
```

- You can send an interruption signal to perform interruption.

```
{  "type": 20001, // Send an interruption signal in the client.  "sender": "user_a", // User ID of the sender. The server will check if this user ID is valid.  "receiver": ["user_bot"], // List of receivers' user IDs. You need to enter the chatbot user ID only. The server will check if this user ID is valid.  "payload": {    "id": "uuid", // Message ID for troubleshooting. You can use the UUID.    "timestamp": 123 // Timestamp for troubleshooting.  }}
```

#### Example Code

Android

iOS

Web&H5

```
public void sendInterruptCode() {    try {        int cmdID = 0x2;        long time = System.currentTimeMillis();        String timeStamp = String.valueOf(time/1000);        JSONObject payLoadContent = new JSONObject();        payLoadContent.put("timestamp", timeStamp);        payLoadContent.put("id", String.valueOf(GenerateTestUserSig.SDKAPPID) + "_" + mRoomId);        String[] receivers = new String[]{robotUserId};        JSONObject interruptContent = new JSONObject();        interruptContent.put("type", AICustomMsgType.AICustomMsgType_Send_Interrupt_CMD);        interruptContent.put("sender", mUserId);        interruptContent.put("receiver", new JSONArray(receivers));        interruptContent.put("payload", payLoadContent);        String interruptString = interruptContent.toString();        byte[] data = interruptString.getBytes("UTF-8");        Log.i(TAG, "sendInterruptCode :" + interruptString);        mTencent RTCCloud.sendCustomCmdMsg(cmdID, data, true, true);    } catch (UnsupportedEncodingException e) {        e.printStackTrace();    } catch (JSONException e) {        throw new RuntimeException(e);    }}
```

```
@objc func interruptAi() {    print("interruptAi")    let cmdId = 0x2    let timestamp = Int(Date().timeIntervalSince1970 * 1000)    let payload = [        "id": userId + "_\\(roomId)" + "_\\(timestamp)", // Message ID, can use UUID; used for troubleshooting.        "timestamp": timestamp // Timestamp, used for troubleshooting.    ] as [String : Any]    let dict = [        "type": 20001,        "sender": userId,        "receiver": [botId],        "payload": payload    ] as [String : Any]    do {        let jsonData = try JSONSerialization.data(withJSONObject: dict, options: [])        self.trtcCloud.sendCustomCmdMsg(cmdId, data: jsonData, reliable: true, ordered: true)    } catch {        print("Error serializing dictionary to JSON: \\(error)")    }}
```

```
const message = {  "type": 20001,  "sender": "user_a",  "receiver": ["user_bot"],  "payload": {    "id": "uuid",    "timestamp": 123  }};trtc.sendCustomMessage({  cmdId: 2,  data: new TextEncoder().encode(JSON.stringify(message)).buffer});
```

### V. Stopping the AI Conversation and Exiting the RTC Engine Room

1. Stop the AI conversation task in the server.

Call the [StopAIConversation](https://trtc.io/document/65296) API through the backend and terminate this conversation.

2. Exit the RTC Engine room in the client. For details, see:
- [Integration Guide for iOS Without UI](https://trtc.io/document/62044?platform=ios&product=rtcengine&menulabel=sdk)
- [Integration Guide for Android Without UI](https://trtc.io/document/62045?platform=android&product=rtcengine&menulabel=sdk)
- [Integration Guide for Web & H5 Without UI](https://trtc.io/document/59649?platform=web&product=rtcengine&menulabel=sdk)
- [Integration Guide for Flutter Without UI](https://trtc.io/document/64203?platform=flutter&product=rtcengine&menulabel=sdk)

### VI. Other Features

#### 1. Other Server APIs

- **Query the AI conversation task status:**[**DescribeAIConversation**](https://trtc.io/document/64964)

You can query the AI conversation task status. The four values below can be returned.

  1.1. `Idle` indicates that the task has not started.
  1.2. `Preparing` indicates that the task is in preparation.
  1.3. `InProgress` indicates that the task is running.
  1.4. `Stopped` indicates that the task has been stopped and resources are being cleaned up.
- **Update AI conversation startup parameters:** [**UpdateAIConversation**](https://trtc.io/document/64962)

You can update the timbre of TTS dynamically during a conversation.

- **Control an AI conversation task:** [**ControlAIConversation**](https://trtc.io/document/64965)

You can call this API when you want the chatbot to actively broadcast the text.

#### 2. Enabling Server Callbacks

See [Conversational AI Server Callback](https://www.tencentcloud.com/document/product/647/68331#).

> **Note:**The callback address is set in the RTC Engine console for conversational AI callbacks.You can use these callbacks together with the [room and media callback](https://www.tencentcloud.com/document/product/647/39558) of RTC Engine.

#### 3. Other Advanced Features

| Feature | Operation Instruction |
| --- | --- |
| Intelligent interruption | [Intelligent interruption](https://www.tencentcloud.com/document/product/647/65319#) |
| Context management | [How to implement context management](https://www.tencentcloud.com/document/product/647/65318#) |
| Function call | [Click here to view an example.](https://github.com/Tencent-RTC/trtc-conversation-ai-example/tree/main/llm_function_call) |


---
*Source: [https://trtc.io/document/68337](https://trtc.io/document/68337)*
