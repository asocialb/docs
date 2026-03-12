# TUIKit Introduction

## TUIKit Overview

TUIKit is a UI component library based on Chat SDK. It provides universal UI components to offer features such as conversation, chat, search, contacts, group, and audio/video call features.
With these UI components, you can quickly build your own business logic.
When implementing UI features, components in TUIKit will also call the corresponding APIs of the Chat SDK to implement Chat-related logic and data processing, allowing developers to focus on their own business needs or custom extensions.
Starting from version 6.9.3557, TUIKit provides a new set of minimalist version UI components. The previous version UI components are still retained, which are called the classic version UI components. You can choose either the classic or minimalist version as needed.

Starting from version 7.5.4852, TUIKit has added support for RTL languages (languages with right-to-left text direction, such as Arabic and Hebrew). When the application language is set to an RTL language, TUIKit will automatically switch to RTL style. Additionally, Arabic language has been added to the built-in language options.

## TUIKit Components

TUIKit provides the following UI components: TUISearch, TUIConversation, TUIChat, TUICallKit, TUIContact, TUIGroup, and TUIOfflinePush. Each of these components is responsible for displaying different content.
The UI effect is as shown below:

Minimalist

RTL

Classic

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/231f293f671d11eeabd75254005810a4.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/226ee130671d11ee9ff8525400d917da.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3d2a19eee73011ee91ba525400aa857d.png)

### TUIChat

TUIChat is responsible for message UI display. You can use it to directly send different types of messages, long press on a message to like/reply to/quote messages, query message read receipt details, etc.
The UI effect is as shown below:

Minimalist

RTL

Classic

| Message UI \| Sending Multiple Types of Messages |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d42262a671d11ee94c3525400d793d0.png) |

| Message Liking \| Reply |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d3af3da671d11eeabd75254005810a4.png) |

| Message Read Receipt \| Read Receipt Details |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d22e788671d11eeabd75254005810a4.png) |

| Message UI \| Sending Multiple Types of Messages |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d94afcd671d11ee974d5254005f490f.png) |

| Message Liking \| Reply |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d64e8c2671d11ee9ff8525400d917da.png) |

| Message Read Receipt \| Read Receipt Details |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d4fd9af671d11ee9ff8525400d917da.png) |

| Message UI | Sending Multiple Types of Messages |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7bd3acfe72e11eebbb2525400564496.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7c280e8e72e11ee8b625254005cb287.png) |

| Message Liking | Reply |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7bcc544e72e11eebbb2525400564496.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7bd852be72e11eebbb2525400564496.png) |

| Message Read Receipt | Read Receipt Details |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7c2d638e72e11eeb0c55254001a1c03.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7b108fde72e11ee8b625254005cb287.png) |

### TUIContact

TUIContact is responsible for contacts display and permission setting.
The UI effect is as shown below:

Minimalist

RTL

Classic

| Relationship Chain List \| Contact Profiles and Management |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1d071697671e11eeabd75254005810a4.png) |

| List of Joined Group Chats \| Blocklist |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1ce83001671e11ee974d5254005f490f.png) |

| Relationship Chain List \| Contact Profiles and Management |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1d3b0e46671e11ee94c3525400d793d0.png) |

| List of Joined Group Chats \| Blocklist |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1d32e4c8671e11ee974d5254005f490f.png) |

| Relationship Chain List | Contact Profiles and Management |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4a1b481ee73011eeb0c55254001a1c03.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/28542bfae72f11eebbb2525400564496.png) |

| List of Joined Group Chats | Blocklist |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/285dd780e72f11eeb0c55254001a1c03.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/284494b8e72f11eeb0c55254001a1c03.png) |

> **Note:**To respect the copyright of emoji designs, the Chat Demo/TUIKit project does not include cutouts of large emoji elements. Please replace them with your own designs or other emoji packs for which you hold the copyright before officially launching for commercial use. **The default smiley face emoji pack shown below is copyrighted by Tencent RTC**, you can upgrade to [Chat Pro Plus Edition and Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it for free.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e9f7df7f97f611efaaca525400fdb830.png)

### TUIConversation

TUIConversation is responsible for conversation list display and editing.
The UI effect is as shown below:

Minimalist

RTL

Classic

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6315110f671e11ee9ff8525400d917da.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/63691c92671e11ee94c3525400d793d0.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/504e1e1de72f11ee8b625254005cb287.png)

### TUIGroup

TUIGroup is responsible for managing group profiles, group members, and group permissions.
The UI effect is as shown below:

Minimalist

RTL

Classic

| Group Profile and Management \| Group Member Management |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/82aa7741671e11eeabd75254005810a4.png) |

| Group Joining Mode Management \| Permission Management |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/82cb45b1671e11ee94c3525400d793d0.png) |

| Group Profile and Management \| Group Member Management |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/82b2fab5671e11ee974d5254005f490f.png) |

| Group Joining Mode Management \| Permission Management |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/82fb2198671e11ee9ff8525400d917da.png) |

| Group Profile and Management | Group Member Management |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/663f7764e72f11eeb0c55254001a1c03.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6638b694e72f11ee8b625254005cb287.png) |

| Group Joining Mode Management | Permission Management |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/663dc663e72f11ee8b625254005cb287.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/662853bae72f11ee91ba525400aa857d.png) |

### TUISearch

TUISearch is responsible for local search, including contacts, group chat, and chat record search.
The UI effect is as shown below:

Minimalist

RTL

Classic

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a9b860b0671e11ee974d5254005f490f.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a9f52862671e11ee9ff8525400d917da.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8e0aac45e72f11ee8b625254005cb287.png)

### TUICallKit

TUICallKit is responsible for audio or video calls.
The one-to-one chat UI is as shown below:

| Video Call | Audio Call |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e0b1088d53ab11ee94c3525400d793d0.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e0a9b66953ab11ee94c3525400d793d0.png) |

The group chat UI is as shown below:

| Video Call | Audio Call |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e0b88a9353ab11ee974d5254005f490f.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e0cd144f53ab11ee974d5254005f490f.png) |

If you have integrated TUIChat, TUIContact, and TUICallKit, you can initiate an audio or video call via a TUIChat message page or TUIContact individual profile page.

The UI effect is as shown below:

Minimalist

RTL

Classic

| Initiating a Call via a Message Page \| Initiating a Call via a Profile Page |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ce1c7877671e11ee9ff8525400d917da.png) |

| Initiating a Call via a Message Page \| Initiating a Call via a Profile Page |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ce4954d5671e11ee974d5254005f490f.png) |

| Initiating a Call via a Message Page | Initiating a Call via a Profile Page |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/66252a58e72d11eebbb2525400564496.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6ac7d729e72d11ee91ba525400aa857d.png) |

### TUIOfflinePush

TUIOfflinePush is responsible for displaying messages pushed offline.

The offline push effect is as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ac341ac253ac11eeabd75254005810a4.png)


---
*Source: [https://trtc.io/document/50062](https://trtc.io/document/50062)*
