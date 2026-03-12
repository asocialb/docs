# TUIKit Introduction

## TUIKit Overview

TUIKit is a UI component library based on the Tencent Cloud Chat SDK. It provides capabilities such as conversation, chat, search, contacts, group and audio/video call. With TUIKit, you can efficiently develop a UI-included instant messaging application for **mobile and desktop platforms** by integrating a single set of code.

TUIKit streamlines the application development process based on the Tencent Cloud Chat SDK. It helps developers efficiently implement UI features and supports calling corresponding APIs of the Chat SDK to implement instant messaging-related logic and data processing, allowing developers to focus on their own business needs or custom extensions.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d0127d71ed5011ed922b525400088f3a.png)

## TUIKit Components

TUIKit provides various UI components for implementing features such as **chat**, **conversation list**, **contacts management**, **user/group profile**, **search**, and **audio/video calls**. Each UI components is responsible for implementing a different feature module.

These components are used in the same way on both mobile and desktop platforms. The TUIKit will be automatically adapted to different platforms.

The UI effect is as shown below:

Mobile

Desktop

![b3d5bba6d133d3a0f3a4fa7534037f01.png](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0365ed85ed5311ed9c2b525400c56988.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d9de913ed5311ed9c2b525400c56988.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/31200dd8ed5311ed9c2b525400c56988.png)

### Chat component for message sending and receiving

**TIMUIKitChat** is responsible for displaying message UI. You can use it to send different types of messages, reply with emojis, reply or quote messages, view message read receipt details, etc.

It also provides unique capabilities on Desktop, such as sending files by dragging and dropping, taking screenshots, pasting and sending images, and opening the directory where a file message is stored. 
The UI effect is as shown below:

> **Noteï¼**To respect the copyright of emoji designs, the Chat Demo/TUIKit project does not include cutouts of large emoji elements. Please replace them with your own designs or other emoji packs for which you hold the copyright before officially launching for commercial use. **The default smiley face emoji pack shown below is copyrighted by Tencent RTC**, you can upgrade to [Chat Pro Plus Edition and Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it for free.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2bcc4faf97f711ef834b525400f69702.png)

Mobile

Desktop

| Message UI | Send multiple types of messages |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/03663a18ed5511ed922b525400088f3a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/07657c11ed5511ed9c2b525400c56988.png) |

| Reply with emojis/reply/quote a message | Automatic file icon matching |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/14e9e97fed5511ed922b525400088f3a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1b60e1b7ed5511ed922b525400088f3a.png) |

| Message read receipt | Read receipt details |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/227745f5ed5511ed922b525400088f3a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/27ce84e6ed5511ed9c2b525400c56988.png) |

| Group tip messages | Group joining request approval |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2bd80a7eed5511ed922b525400088f3a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/38c39673ed5511ed922b525400088f3a.png) |

| Link parsing preview | Geographical location message |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3de7930fed5511ed9c2b525400c56988.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/41f58e1aed5511ed922b525400088f3a.png) |

The message UI shows message sending and receiving interactions on Desktop.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/512738f0ed5511ed922b525400088f3a.png)

In addition to features displayed on the Mobile tab, **extra features are supported on Desktop**, as shown below:

- **Take screenshots or paste an image in the message sending area to send images directly**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/578dd165ed5511ed922b525400088f3a.png)

- **Drag and drop multiple files to send**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5dcaa138ed5511ed922b525400088f3a.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/69c912c5ed5511ed9c2b525400c56988.png)

- **Hover over a message** to perform operations such as replying with emojis, replying to a message, or forwarding a message.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/74e589fced5511ed9c2b525400c56988.png)

- **Right-click a message** to perform operations such as copying, selecting, deleting, translating and recalling a message.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8c1f450aed5511ed922b525400088f3a.png)

- **Right-click a file sent during chat to open the file directly or open the directory where the file is stored**. Alternatively, click the file message itself to open it.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9d61a072ed5511ed922b525400088f3a.png)

- **Mention (@) group members in a group**. In the group member selection panel, search for group members by entering their name gradually and mention them. The mentioned members will receive notification.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b237d509ed5511ed9c2b525400c56988.png)

- **Historical message panel** supports searching message history by keywords.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/84819014ed6b11ed922b525400088f3a.png)

- **Select multiple messages in a conversation**.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8c0a37ebed6b11ed9c2b525400c56988.png)

### Contacts components

Contacts components are responsible for displaying the information of contacts, group chats, and blocklist of the current user.

Mobile

Desktop

| Contacts (TIMUIKitContact) | Friend request list (TIMUIKitNewContact) |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9b2bea9aed6b11ed9c2b525400c56988.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9e24b2f2ed6b11ed922b525400088f3a.png) |

| List of joined group chats (TIMUIKitGroup) | Blocklist (TIMUIKitBlackList) |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/be4d372aed6b11ed9c2b525400c56988.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2118d35ed6b11ed922b525400088f3a.png) |

- **Contacts - TIMTUIKitContact**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d4faa93aed6b11ed9c2b525400c56988.png)

- **Group list - TIMUIKitGroup**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dcf32095ed6b11ed922b525400088f3a.png)

- **Blocklist - TIMUIKitBlackList**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e483f014ed6b11ed922b525400088f3a.png)

- **Friend request list - TIMUIKitNewContact**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ecc7c8eded6b11ed9c2b525400c56988.png)

### Conversation list components

**TIMUIKitConversation** is responsible for displaying and editing conversation list.

Mobile

Desktop

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f8d269aded6b11ed9c2b525400c56988.png)

- **Conversation list**. The current conversation, pinned conversations and unselected conversations are displayed in different colors.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/01a26b0ded6c11ed9c2b525400c56988.png)

- **Right-click a conversation** to perform operations such as clearing chat messages, pinning the conversation, and deleting the conversation.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/071eb366ed6c11ed9c2b525400c56988.png)

### User profile management component

TIMUIKitProfile is responsible for contacts profile display and management.

Mobile

Desktop

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/168b52d0ed6c11ed922b525400088f3a.png)

The TIMUIKitProfile component supports two display layouts on Desktop for different scenarios: profile card and profile detail page.

- **Profile card** is displayed in various scenarios, such as a one-to-one chat title is clicked or when a member profile photo in group chats is clicked.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1d6e5dc3ed6c11ed9c2b525400c56988.png)

- **Profile detail page**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2483e4f4ed6c11ed922b525400088f3a.png)

### Friend adding and group joining components

**TIMUIKitAddFriend** is a friend adding component. **TIMUIKitAddGroup** is group joining component.

Mobile

Desktop

| Friend adding page (TIMUIKitAddFriend) | Group joining page (TIMUIKitAddGroup) |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/30dd5f2aed6c11ed9c2b525400c56988.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/345589c6ed6c11ed922b525400088f3a.png) |

- **Add friends - TIMUIKitAddFriend**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/403b7f70ed6c11ed9c2b525400c56988.png)

- **Join groups - TIMUIKitAddGroup**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4753aceaed6c11ed9c2b525400c56988.png)

### Group profile management component

**TIMUIKitGroupProfile** is responsible for displaying and managing group profiles, group members, and permissions. The UI effect is shown below:

Mobile

Desktop

| Group profile and management | Group member management |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5658d5f7ed6c11ed922b525400088f3a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5b1d41c7ed6c11ed922b525400088f3a.png) |

| Group joining mode management | Group operations |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/65debecbed6c11ed9c2b525400c56988.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6e7fa9aeed6c11ed922b525400088f3a.png) |

- **Group profile and management**. Group profile is displayed on the right side of the group chat. It has different UI interfaces on Mobile and Desktop, but the features are same.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7706b6bced6c11ed922b525400088f3a.png)

- **Group member management**. View all group members, add and remove group members in the group member section. Specify group admin, mute all group members or mute a specific group member in the group management section.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7d07a738ed6c11ed922b525400088f3a.png)

- **Group notice**. Click the group notice section to edit and post a group notice.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8a532c4bed6c11ed922b525400088f3a.png)

### Local search components

There are two components for local search capabilities: **TIMUIKitSearch** and **TIMUIKitSearchMsgDetail**.

**TIMUIKitSearch** is responsible for local global search, including contacts, group chat, and chat record search. **TIMUIKitSearchMsgDetail** is responsible for searching for chat records in a conversation.

Mobile

Desktop

- **Global search - TIMUIKitSearch**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9a8c1a99ed6c11ed9c2b525400c56988.png)

- **In-conversation search - TIMUIKitSearchMsgDetail**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a17956e5ed6c11ed9c2b525400c56988.png)

- **Global search - TIMUIKitSearch**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aff320f9ed6c11ed9c2b525400c56988.png)

- **In-conversation search - TIMUIKitSearchMsgDetail**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b71be2a6ed6c11ed922b525400088f3a.png)

### Audio/Video call

[TUICallKit](https://www.tencentcloud.com/document/product/647/54896) provides audio and video call features and is only supported on mobile clients.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e3e9c34ded6c11ed922b525400088f3a.png)

### Message push

You can use Tencent's [Flutter push plugin](https://www.tencentcloud.com/document/product/1047/50032) to integrate message push capabilities, including offline and online push capabilities.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f0c0d374ed6c11ed9c2b525400c56988.png)


---
*Source: [https://trtc.io/document/50059](https://trtc.io/document/50059)*
