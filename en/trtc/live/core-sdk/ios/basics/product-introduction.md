# Product Introduction

**AtomicXCore** is an SDK designed for scenarios such as **Video Live Streaming,** **Conferencing**, **Voice Chat Rooms**, and **Calling**. It provides a âUI-lessâ integration approach, allowing you to focus exclusively on UI development and quickly build fully-featured, highly customizable real-time interactive applications.

## Use Cases

**AtomicXCore** encapsulates all the business logic required to build a wide range of complex scenarios, enabling you to concentrate entirely on custom UI design.

### Video Live Streaming

- **Use Cases**

| **Social Entertainment** | **Gaming Interaction** | **E-commerce Shopping** |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/23655c32cf7811f0800752540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/236495c7cf7811f084a45254005ef0f7.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/23700cdecf7811f0b638525400e889b2.png) |

- **Core Features**
  - **HD Live Streaming**: Delivers stable, high-definition streaming and viewing experiences.
  - **Audience Co-hosting**: Enables audio and video co-hosting between audience members and streamers.
  - **Cross-room Connection / PK**: Supports cross-room co-hosting and PK (Player Kill) competitions between streamers.
  - **Live Chat**: Allows real-time public chat messaging between audience and streamers.
  - **Gifts and Likes**: Supports sending gifts, full-screen gift animations, and like interactions.
- **Quick Start**

| **Platform** | **Documentation Entry** | **Supported Language/Framework** |
| --- | --- | --- |
| Android | [Quick Start](https://www.tencentcloud.com/document/product/647/74593) | Kotlin / Java |
| iOS | [Quick Start](https://www.tencentcloud.com/document/product/647/74594) | Swift / Objective-C |
| Web | [Quick Start](https://www.tencentcloud.com/document/product/647/74840) | Vue / TypeScript |

### Voice Chat Room

- **Use Cases**

| **Group Chat** | **Karaoke** | **Cross-room Connection** |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e969b88acf7811f0800752540099c741.png)  | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c85b35bbcf7811f098d1525400bf7822.png)  |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1cbc3630cf7911f093295254001c06ec.png)  |

- **Core Features**
  - **High-quality Voice Chat**: Provides advanced audio processing, including echo cancellation (AEC) and AI-powered noise reduction.
  - **Seat Management**: Enables room owners to lock or mute seats, manage audience requests to join, and send host invitations.
  - **Cross-room Connection**: Facilitates co-hosting between room owners across different rooms.
  - **Live Chat**: Supports real-time public chat messaging between audience and hosts.
  - **Gifts and Likes**: Allows sending gifts, displaying full-screen gift animations, and liking interactions.
- **Quick Start**

| **Platform** | **Documentation Entry** | **Supported Language/Framework** |
| --- | --- | --- |
| Android | [Quick Start](https://www.tencentcloud.com/document/product/647/74681) | Kotlin / Java |
| iOS | [Quick Start](https://www.tencentcloud.com/document/product/647/74682) | Swift / Objective-C |

## **AtomicXCore** Core Concepts

| **Concept** | **Definition** | **Example** |
| --- | --- | --- |
| `Store` (State Manager) | `Store` is the logic and state manager for AtomicXCore scenario modules (such as calls, live streaming, live chat). | â¢ `CallListStore`: Call Manager â¢ `LiveListStore`: Live Stream List Manager â¢ `ChatStore`: Live Chat Manager |
| `State` (State Data) | A snapshot of the data managed by a `Store`, typically represented as a `struct`. The UI updates automatically by subscribing to changes in State. | â¢ `CallParticipantState`: Call Participant State â¢ `LiveSeatState`: Live Room Seat State |
| `Action` (Business Method) | Business operation methods provided by a `Store`. Invoking an `Action` is the only way to update the `State`. | â¢ `likeStore.sendLike():` Send a like in live streamâ¢ `barrageStore.sendTextMessage()`: Send a barrage messageâ¢ `coGuestStore.applyForSeat()`: Apply for co-hosting |
| `Event` (Event Notification) | One-time callback notifications published by a `Store`, used for handling asynchronous events such as triggering UI animations or prompts. | â¢ `GiftEvent.onReceiveGift`: Gift Received Event â¢ `HostEvent.onInvitationReceived`: Host Invitation Received Event |

## **AtomicXCore** Working Principle

**AtomicXCore** abstracts each business function as a `Store` (State Manager). Follow these core steps to integrate **AtomicXCore**:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98cf7230cf7a11f0aecd525400454e06.png)

### 1. Get Store Instance (State Manager)

The `Store` is the dedicated logic and state manager for each business module (such as live chat, gifts, calls). Perform all operations through the corresponding `Store`.

### 2. Subscribe to State

`State` is a snapshot of the current data in the `Store`. Your UI should subscribe to changes in `State` and update automaticallyâdo not modify `State` directly.

### 3. Call Action (Method)

`Action` methods are the only way to update `State`. When a user interacts with the UI (for example, clicking the like button), invoke the appropriate `Action` method from the `Store`. The `Store` will process the business logic (which may include network requests) and update its `State` upon success. All subscribers to the previous `State` are notified automatically, triggering a UI refresh.

### 4. Subscribe to Event

`Event` notifications differ from `State`. `State` reflects the current status (for example, total likes), while `Event` indicates what just happened (for example, a gift was received).

Use `Event` notifications to trigger one-time UI effects, such as animations or pop-up prompts.


---
*Source: [https://trtc.io/document/74811](https://trtc.io/document/74811)*
