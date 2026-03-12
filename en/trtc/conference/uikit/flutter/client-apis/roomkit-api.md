# RoomKit API

## Introduction

The TUIRoomKit API is a multi-person meeting component with an **Including UI Interface**. By using the TUIRoomKit API, you can quickly implement a meeting-like scenario through a simple interface. For more detailed integration steps, see: [Integration](https://www.tencentcloud.com/document/product/647/57508#).

This document will provide a detailed introduction to the classes and related interfaces you may use in Flutter TUIRoomKit. By referring to this document, you can gain a more comprehensive understanding of how to use Flutter TUIRoomKit.

## ConferenceMainPage

Conference Main Page

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4a022c4d0e9911ef8c545254000781d8.png)

| Parameter | Type | Description |
| --- | --- | --- |
| conferenceId | String | Conference ID required for creating or joining a conference |
| isCreateConference | bool | Whether it is for creating a conference (true for creating, false for joining) |
| conferenceParams | [ConferenceParams](https://www.tencentcloud.com/document/product/647/60356#ConferenceParams) | Parameters related to creating or joining a conference |
| conferenceObserver | [ConferenceObserver](https://www.tencentcloud.com/document/product/647/60356#ConferenceObserver) | Conference status change callback listener |

> **Noteï¼**When you use [ConferenceSession](https://www.tencentcloud.com/document/product/647/60356#f09c9c3b-4eeb-4fee-879c-51eef62ab13d) to create or join a conference, you do not need to pass any of the parameters here.

## ConferenceSession

When you expect to navigate to the conference page after successfully creating/joining a conference, you can use the `ConferenceSession` class to perform related operations.

| Parameter | Type | Description |
| --- | --- | --- |
| isMuteMicrophone | bool | Whether to mute the microphone (default is false) |
| isOpenCamera | bool | Whether to turn on the camera (default is false) |
| isSoundOnSpeaker | bool | Whether to use speakers (default is true) |
| name | String | Conference name (default is your conference ID, it is invalid when joining the conference) |
| enableMicrophoneForAllUser | bool | Whether to enable microphone permission for all members (default is true, invalid when joining a conference) |
| enableCameraForAllUser | bool | Whether to enable camera permissions for all members (default is true, invalid when joining a conference) |
| enableMessageForAllUser | bool | Whether to enable the speaking permission of all members (default is true, invalid when joining a conference) |
| enableSeatControl | bool | Whether to enable speaking mode on stage (default is false, invalid when joining a conference) |
| onActionSuccess | VoidCallback | Callback for successful creation/joining of a conference. You can navigate to the meeting page in this callback. |
| onActionError | Function ([ConferenceError](https://www.tencentcloud.com/document/product/647/60356#ConferenceError),  String) | Callback for failed creation/joining of a conference. |

### newInstance

Create a new ConferenceSession object.

```
factory ConferenceSession.newInstance(String id)
```

| Parameter | Type | Description |
| --- | --- | --- |
| id | String | Conference ID required for creating or joining a conference |

### quickStart

Quickly create conference interfaces.

```
Future<void> quickStart()
```

### join

Join the conference interface.

```
Future<void> join()
```

> **Noteï¼**Before calling the quick conference creation or joining conference interface, you need to complete all the parameters of the ConferenceSession that you need to set. For details, please refer to [Pre-conference Control](https://www.tencentcloud.com/document/product/647/59974#67fc07af-5df6-445f-a705-bd49643e0047).When navigating directly to [ConferenceMainPage](https://www.tencentcloud.com/document/product/647/60356#ConferenceMainPage) and passing in relevant parameters to create/join a conference, there is no need to use `ConferenceSession`.

## ConferenceParams

| Parameter | Type | Description |
| --- | --- | --- |
| isMuteMicrophone | bool | Whether to mute the microphone (default is false) |
| isOpenCamera | bool | Whether to turn on the camera (default is false) |
| isSoundOnSpeaker | bool | Whether to use speakers (default is true) |
| name | String | Conference name (default is your conference ID, it is invalid when joining the conference) |
| enableMicrophoneForAllUser | bool | Whether to enable microphone permission for all members (default is true, invalid when joining a conference) |
| enableCameraForAllUser | bool | Whether to enable camera permissions for all members (default is true, invalid when joining a conference) |
| enableMessageForAllUser | bool | Whether to enable the speaking permission of all members (default is true, invalid when joining a conference) |
| enableSeatControl | bool | Whether to enable speaking mode on stage (default is false, invalid when joining a conference) |
| onActionSuccess | VoidCallback | Callback for successful creation/joining of a conference. You can navigate to the meeting page in this callback. |
| onActionError | Function ([ConferenceError](https://www.tencentcloud.com/document/product/647/60356#ConferenceError),  String) | Callback for failed creation/joining of a conference. |

## ConferenceObserver

### onConferenceStarted

Conference start event.

```
Function(String conferenceId, ConferenceError error) onConferenceStarted
```

| Parameter | Type | Description |
| --- | --- | --- |
| conferenceId | String | Conference id |
| error | [ConferenceError](https://www.tencentcloud.com/document/product/647/60356#ConferenceError) | Error code |

### onConferenceJoined

Join the conference event.

```
Function(String conferenceId, ConferenceError error) onConferenceJoined
```

| Parameter | Type | Description |
| --- | --- | --- |
| conferenceId | String | Conference Id |
| error | [ConferenceError](https://www.tencentcloud.com/document/product/647/60356#ConferenceError) | Error code |

### onConferenceFinished

Meeting end event, this callback will be triggered when the meeting is actively ended or the meeting is dismissed.

```
Function(String conferenceId) onConferenceFinished
```

| Parameter | Type | Description |
| --- | --- | --- |
| conferenceId | String | Conference Id |

### onConferenceExited

Exit meeting event, this callback will be triggered when actively exiting the meeting or being kicked out of the meeting.

```
Function(String conferenceId) onConferenceFinished
```

| Parameter | Type | Description |
| --- | --- | --- |
| conferenceId | String | Conference Id |

## ConferenceError

Error code

| Enumeration | Value | Description |
| --- | --- | --- |
| success | 0 | Operation Successful |
| errFailed | -1 | Temporarily Unclassified General Error |
| errConferenceIdNotExist | -2100 | Room Does Not Exist When Entering, May Have Been Closed |
| errConferenceIdInvalid | -2105 | Illegal Custom Room ID, Must Be Printable ASCII Characters (0x20-0x7e), Up to 48 Bytes Long |
| errConferenceIdOccupied | -2106 | Room ID is Already in Use, Please Choose Another Room ID |
| errConferenceNameInvalid | -2107 | Illegal Room Name, Maximum 30 Bytes, Must Be UTF-8 Encoding if Contains Chinese Characters |


---
*Source: [https://trtc.io/document/60356](https://trtc.io/document/60356)*
