# Official channel 

Official account features are similar to those of WeChat's official accounts, offering customers subscription and publishing features. Through the related interfaces for official accounts, users can create and manage official accounts, publish articles and rich media messages, interact with fans, and fans can also send private messages to the official account. Meanwhile, the app's back end can statistically manage and operate related data through RestAPI + third-party callback.

## Introduction to Official Account Data Structure

### Official Account Basic Information

| Field Name | Type | Description | Remarks |
| --- | --- | --- | --- |
| Official_Account | String | Unique Identifier of Official Account | Read-only. Official Account ID, ensured to be unique within the App, its format prefix is @TOA#_. Additionally, the App can also self-define the Official Account ID. |
| Owner_Account | String | Official Account Creator ID | Read-only. |
| Name | String | Official Account Name | Readable and writable. Maximum length of 150 bytes, cannot be adjusted. |
| Introduction | String | Official Account Description | Readable and writable. Maximum length of 400 bytes, cannot be adjusted. |
| FaceUrl | String | Official Account Avatar URL | Readable and writable. Maximum length of 500 bytes, cannot be adjusted. |
| MaxSubscriberNum | Integer | Maximum Number of Subscribers for Official Account | Readable and writable. The current default value is 100000. |
| SubscriberNum | Integer | Current number of people subscribing to the Official Account | Read-only. |
| LastMsgTime | Integer | Time of the last message sent between the Official Account and the Subscriber | Read-only. |
| CreateTime | Integer | Creation Time of the Official Account | Read-only. |
| Organization | String | Group organization the Official Account belongs to | Readable and writable. Maximum length of 500 bytes, cannot be adjusted. |
| CustomString | String | Official Account Information Dimensions Custom Definition Field | Readable and writable. Maximum length of 3000 bytes, cannot be adjusted. |

### Subscriber Basic Information

| Field Name | Type | Description | Remarks |
| --- | --- | --- | --- |
| Subscriber_Account | String | Subscriber User ID | Read-only. |
| SubscribeTime | Integer | Subscription period | Read-only. |
| MsgFlag | String | Message receiving option | Message Receiving Options, including:AcceptAndNotify means to receive and alertAcceptNotNotify means to receive without alert (will not trigger offline push)Discard means to block Official Account Messages (no messages will be pushed to the client) |
| CustomString | String | Subscriber User Dimension Custom Definition Fields | Readable and writable. Maximum length of 3000 bytes, cannot be adjusted. |

## Custom Definition Official Account ID

By default, when an App creates a Official Account, Chat will assign a default ID to the newly created Official Account. This ID will start with @TOA#_ and is guaranteed to be unique within the App.
To make the Official Account ID simpler, easier to remember and spread, Chat supports custom Definition ID by Apps when creating Official Accounts through REST API. The custom Definition ID must consist of printable ASCII characters (0x20-0x7e), be no longer than 48 bytes, and must start with @TOA#_, but cannot be @TOA#_@TOA# (to avoid confusion with the default assigned Official Account ID).


---
*Source: [https://trtc.io/document/60813](https://trtc.io/document/60813)*
