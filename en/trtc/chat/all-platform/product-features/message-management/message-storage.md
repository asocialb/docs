# Message Storage

## Roaming Message Storage

Chat supports message roaming, which means that, when users log in on different devices, they still have access to chat history.

By default, roaming C2C chat messages and group messages are stored for 7 days, and they will be deleted thereafter. For the billing details, see [Pricing](https://intl.cloud.tencent.com/document/product/1047/34350).
Different SDK versions allow you to extend the storage time of historical messages for different message types.

| SDK Version | Text | Custom Message | Image | File | Short Audio | Short Video | Rich Media Message |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Android 5.X | â | â | â | â | â | â | â |
| Android 4.X | â | â | â | â | â | â | â |
| Android 3.X | â | â | Ã | Ã | Ã | Ã | Ã |
| Android 2.X | â | â | Ã | Ã | Ã | Ã | Ã |
| iOS 5.X | â | â | â | â | â | â | â |
| iOS 4.X | â | â | â | â | â | â | â |
| iOS 3.X | â | â | Ã | Ã | Ã | Ã | Ã |
| iOS 2.X | â | â | Ã | Ã | Ã | Ã | Ã |
| PC SDK 2.X | â | â | Ã | Ã | Ã | Ã | Ã |
| Web and mini program SDK 2.X | â | â | â | â | â | â | â |
| Web and mini program SDK 1.X | â | â | Ã | Ã | Ã | Ã | Ã |

> **Note:**We recommend you upgrade to the latest SDK version for improved user experience.

## Unread Message Storage

Chat supports the storage of unread messages; that is, messages sent while the user is offline will be stored and pulled upon next login.

For C2C Chat, unread messages in up to 100 conversations are saved for each user for 7 days by default, with up to 250 unread messages in each conversation. Messages exceeding the limits will not be counted as unread messages, but they will still be saved in message roaming. For group chat, there are no such limits.

## Recent Contacts

Similar to the list of recent contacts on QQ, recent contacts display the users who have recently contacted the current user as well as their last messages.

By default, the client will pull the recent contacts through the SDK upon login to display the conversation list, and the recent 100 contacts are stored by default for the same period as the last messages; for example, if no messages have been sent to or received from a contact for 7 days, this contact cannot be obtained in the recent contacts after the last message expires.

## App Local Storage

Users do not need to store messages because the SDK stores received messages by default. Users can call the API to obtain local messages (no network required). Additionally, local messages can be obtained through the getMessage API. When gaps exist in local message history, roaming messages are used to fill in the gaps.

By default, the SDK does not delete user messages, but we provide the option to delete local messages.


---
*Source: [https://trtc.io/document/33524](https://trtc.io/document/33524)*
