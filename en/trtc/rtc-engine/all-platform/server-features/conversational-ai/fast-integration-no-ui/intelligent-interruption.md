# Intelligent interruption

## Overview

Intelligent Interruption is a crucial feature in real-time voice conversation and directly affects user experiences. Relying on a rich set of interruption schemes, Tencent Real-Time Communication (Tencent RTC) AI conversation provides customers with flexible and powerful solutions to meet various scenario needs. Our intelligent interruption feature is mainly divided into automatic interruption and manual interruption modes, effectively enhancing the fluency and naturalness of conversation.

### Automatic Interruption

Automatic interruption means that the system will automatically trigger interruption based on the user's audio input when specific conditions are detected. It supports two main rules: interruption based on audio duration and interruption based on semantics.

1. **Interruption based on audio duration**
- Users can dynamically configure the interruption duration, which is set to 500 ms by default.
- Adjustable range: 300 ms (more sensitive) to 5,000 ms (to avoid false interruptions).
- Suggestion:
  - For high-interaction scenarios like customer service conversation, shorter duration (for example, 300 ms or 500 ms) is set to enhance response speed.
  - For speech or lecture scenarios, longer duration (for example, 1,000 ms) is set to avoid false interruptions.
2. **Interruption based on semantics**

Based on voice activity detection (VAD) technology, when the server detects that the user has input a semantically complete sentence, it will automatically trigger interruption.

3. **Cooperation between automatic and manual interruptions**

In automatic interruption mode, it is still possible to use the client-side SDK to send custom interruption signals for specific manual interruption control, providing a more refined interactive experience.

### Manual Interruption

Manual interruption refers to an action initiated by the user, which is achieved by sending a custom message through the SDK on the client side. This provides users with a more direct control method. It usually depends on buttons or hotkeys on the user interface.

1. **Interruption signal description**

Manual interruption uses custom messages in the following JSON format:

```
{
  "type": , // Fixed type
  "sender": "user_a", // Sender's userid. The server will verify its validity.
  "receiver": ["user_bot"], // List of receiver userids. The robot's userid is entered.
  "payload": {
    "id": "uuid", // Message id, for debugging purposes
    "timestamp": 123 // Timestamp, for debugging purposes
  }
}
```

2. **Usage**

You can manually interrupt by sending the above custom message through the SDK's `sendCustomCmdMessage` method.

## Use Cases

1. Customer service conversation: Shorter automatic interruption duration is used with manual interruption to achieve quick response and precise control.
2. Online education: Longer automatic interruption duration is used to avoid interrupting students' speeches by mistake. Teachers can use manual interruption for necessary interventions.
3. Group meeting: Automatic and manual interruptions are combined to flexibly manage speaking order and duration.


---
*Source: [https://trtc.io/document/65319](https://trtc.io/document/65319)*
