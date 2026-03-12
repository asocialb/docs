#  Product features and use cases introduction

## Overview

Tencent RTC currently offers real-time communication products such as Call, Conference, Live, RTC Engine, Chat, and In-game Voice Chat, as well as extended tools like Beauty AR.

| Product | Introduction | Features | Applicable Scenarios | Integration Methods |
| --- | --- | --- | --- | --- |
| [Call](https://www.tencentcloud.com/document/product/647/50989) | One-on-one and group video/audio calls | 1V1 Audio/Video CallGroup Audio/Video CallVirtual BackgroundsInvite to/Join Ongoing CallsCall Status DisplayVideo Call Switch to Audio CallMake/Answer/Decline/Hang Up a CallCall Notifications and Offline Push			Floating WindowCustom RingtonesAI Noise SuppressionOn-Cloud Recording | Audio and Video Social CallRemote healthcareSales and consultingInteractive virtual classroom | UIKits;Core SDK |
| [Conference](https://www.tencentcloud.com/document/product/647/54634) | Large-scale meetings and webinars with video/audio | Virtual BackgroundsScreen SharingAudio Mix by Default				Member Management				Room Management				Free Speech Mode				On-Stage Speech Mode	Microphone ManagementChat in ConferenceMulti-Terminal LoginAI Noise SuppressionOn-Cloud Recording | Audio and video conferencingOnline educationCorporate and professional trainingDigital recruitmentWebinarsRemote healthcare | UIKitsï¼Core SDK |
| [Live](https://trtc.io/document/60034?platform=ios&product=live) | Interactive video and voice live streaming | Go Live							Chat in Live Room/EmojiAnchor Connection and BattleMulti-guestInteractive Gift				Floating Window					Background Music				Audience  ManagementVoice EffectsPC Live Streaming AssistantAI Noise SuppressionOn-Cloud Recording |  Video social networkingVoice chat roomLive performance streamingGame live streamingE-commerce sellingOnline video classroomWeb 3.0 | UIKitsï¼Core SDK |
| [RTC Engine](https://www.tencentcloud.com/document/product/647/35078#) | Fully customizable real-time communication SDKs | Audio/Video CallInteractive Video StreamingOn-cloud RecordingOn-cloud MixTranscodingRelay to CDNConversational AI ServicesSpeech-to-TextAI Noise SuppressionPushing to Rooms over RTMP3D Spatial AudioScaled Video CodingRegion of Interest CodingHigh Video ResolutionVoice Effects | All real-time audio and video call scenarios, such as:Voice/video call social networkingInteractive video live streamingInteractive virtual classroomLarge-scale online eventsRemote healthcare | Core SDK |
| [Chat](https://trtc.io/document/50061?platform=web&product=chat) | All-in-one private and group instant messaging | Rich Media MessagesCommunity Chat ReactionsMessage Read ReceiptsTyping StatusUser Online StatusMessage SearchQuote ReplyMessage TranslationPush NotificationsUser ManagementGroup ManagementContent ModerationChat Analytics | Social media and community messagingRide-hailing, delivery, and food delivery platform chatRemote healthcare chatIn-game chatChat in live roomRetail customer service chat | UIKits;Core SDK |
| [Beauty AR](https://trtc.io/document/60216?platform=web&product=beautyar) | A powerful tool seamlessly integrating beauty filters, makeup, and special effects | Beauty EffectsFiltersMakeup2D Stickers3D StickersVirtual Backgrounds			AnimojiVirtual AvatarsImage Quality AdjustmentBody ShapingMaterial Production Tools | Interactive video live streamingInteractive video callsShort videosGamingAI cameraVideo conferencing | Core SDK |
| [In-game Voice Chat (GME)](https://www.tencentcloud.com/document/product/607/10835?lang=en&pg=) | In-game real-time voice chat | 3D Positional Voice ChatProximity Voice ChatVoice ControlSpeech to TextVoice EffectsAI Noise SuppressionUnlimited Co-anchors | Esports gamesParty gamesMMO/Sandbox gamesVR/AR games | Core SDK |

> **Note:**Call, Conference, Live, and Chat all come with pre-built UIs that meet the needs of most scenarios, and they also support more customized features using the Core SDK. The RTC Engine is a multifunctional toolbox without UI, suitable for all real-time interactive voice and video scenarios, supporting more complex use cases.**UIKits:**Provide pre-made UI components and business logic code that simplify basic work, allow flexible feature customization, and are easy to integrate. They enable rapid integration within a day, accelerating market validation.**Core SDK:** Supports the highest level of customization, allowing the extension of advanced features with more flexible integration options to meet more complex business needs.

## Detailed Product Introduction

### Call

Call is a product with pre-built UI components that allows you to quickly add in-app voice and video calling with just a few lines of code, supporting various communication needs.

#### Features

- Prebuilt UIKits: Provide audio and video call interfaces and functional UIs for iOS, Android, Flutter, and Web platforms. These can be used directly or freely customized using the Core SDK according to requirements.
- Features: Support 1v1 voice/video call,group call, Invite/join ongoing calls, customize incoming call ringtone, customize nickname, avatar, floating window, mute/unmute the ringtone for incoming calls, offline push, virtual background, on-cloud recording, AI noise suppression, global interconnectivity, adapt to poor network conditions, call records and more.
- Latency is below 300 milliseconds, supporting 2K/4K resolutions. Combined with network optimization and efficient encoding, it delivers a smooth and low-lantency real-time interactive experience.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea425bdb236411f09e67525400bf7822.png)

#### Use Cases

- Audio and Video Social Call: Stay connected with friends and family online, share your daily life, create a strong sense of belonging, and bring each other closer.
- Remote Healthcare: Easily access medical and health services through safer and more convenient virtual consultations, improving patient satisfaction and health outcomes.
- Sales and Consultation: Provide a video customer service experience that is accessible anytime, anywhere, build trust with customers through face-to-face conversations, and efficiently solve customer issues.
- Online Education: Easily connect students, tutors, and instructors through voice and video, covering various teaching scenarios such as one-on-one instruction and small group classes.

### Conference

Conference is a product offering pre-built room components for rapid integration of audio and video rooms, enabling low-latency meetings with the fewest code changes.

#### Features

- Prebuilt UIKits: Provide audio and video conference interfaces and functional UIs for iOS, Android, Flutter, Electron, and Web platforms. These can be used directly or freely customized using the Core SDK according to requirements.
- Features:Multi-person video conversation, Rich meeting controls, on-stage speaking mode, floating window, audio and video settings, screen sharing, schedule conference, conference password, basic beauty, in-meeting chat, cloud recording,  AI noise suppression, virtual backgrounds, and more.
- Latency is below 300 milliseconds, supporting 2K/4K resolutions. Combined with network optimization and efficient encoding, it delivers a smooth and low-lantency real-time interactive experience.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/da191c6f2f1511f09e67525400bf7822.png)

#### Use Cases

- Video Conferencing: Significantly enhances the quality of audio and video conferences, providing a seamless and professional meeting experience to facilitate remote collaborative work efficiently.
- Online Education: Offers a wealth of interactive teaching tools to create an immersive virtual classroom environment, improving teaching effectiveness.
- Digital Recruitment: Optimize your digital recruitment process, provide a more intuitive and humanized experience for job seekers through high-quality video interviews and interactive environments, while improving your recruitment efficiency and quality.
- Corporate/Professional Training: Supports various training scenarios, including corporate internal training and professional skills training. Enhances training outcomes and participant satisfaction through online interaction and real-time feedback.
- Webinar: Builds an influential and interactive online seminar, professionally controls the seminar process, and attracts your audience with high-quality audio and video.
- Telehealth/Telemedicine: Provide clear and reliable video conferencing for virtual consultations, improving patient care quality and accessibility.

### Live

Live is a product offering pre-built voice room and video live UI components, allowing developers to quickly integrate immersive live experiences into their apps.

#### Features

- Prebuilt UIKits: Live provides UIKits for both the anchor side and audience side, offering components and interface designs for live streaming services on iOS, Android, Flutter, Electron, and Web platforms. These can be used directly or freely customized using the Core SDK according to requirements, significantly reducing development complexity and time investment.
- Features: Go live, follow anchors, anchor connection and battle, invite audience as guest, live chat, gift, emoji/like interactions, voice effect, face beautification, background music, floating window, pc live streaming assistant, audience list, audience tag, live room list, content moderation and more.
- Latency is below 300 milliseconds, supporting 2K/4K resolutions. Combined with network optimization and efficient encoding, it delivers a smooth and low-lantency real-time interactive experience.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d5253432f2511f0b0b1525400e889b2.png)

#### Use Cases

- Entertainment Live Streaming: Stay connected online with friends and family, share your daily life, create a strong sense of belonging, and bring each other closer.
- Gaming Live Streaming: Engage in interactive gaming live streams with your audience.
- E-commerce Live Streaming: Provide a video customer service experience that is accessible anytime, anywhere, build trust with customers through face-to-face conversations, and efficiently solve customer issues.
- Online Classroom: Easily connect students, mentors, and instructors through voice and video, covering various teaching scenarios such as one-on-one instruction and small group classes.
- Voice Chat Room: A secure and intimate space for various private voice social interactions.
- Web 3.0: Enhance Web 3.0 apps with real-time communication tools, enabling dynamic interactions and a vibrant decentralized ecosystem.

### RTC Engine

RTC Engine is a flexible real-time communication core SDK, like a versatile toolbox without pre-built UI, offering APIs for voice, video, and live streaming to build custom real-time apps.

#### Features

- Highly Customizable: The RTC Engine provides SDKs for platforms including Web, Android, iOS, Electron, Windows, and macOS, enabling developers to quickly integrate and customize a variety of advanced features suitable for complex scenarios.
- Features:  Supports audio and video calls, interactive live streaming, on-cloud recording, on-cloud mixtranscoding, conversational AI services, speech-to-text, AI noise suppression, pushing to rooms over RTMP, 3D spatial audio, scaled video coding, region of interest coding, high video resolution, voice effects and more.
- Latency is below 300 milliseconds, supporting 2K/4K resolutions. Combined with network optimization and efficient encoding, it delivers a smooth and low-lantency real-time interactive experience.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dc4b4cc32f2711f0948f52540099c741.png)

#### Use Cases

Supports all real-time audio and video call scenarios, categorized by different industries, suitable for:

- Entertainment Scenarios: Host PKs, online karaoke, werewolf games, language chat rooms, and other audio and video gameplay.
- Financial/E-commerce Scenarios: Live broadcasting with direct video calls, financial video underwriting, and facial recognition verification.
- Legal/Governmental Scenarios: Online courts, judicial auctions, and facial recognition verification.
- Medical Scenarios: One-on-one video consultations, and online medical consultations.
- Educational Scenarios: Interactive online classrooms.
- Enterprise Tool Scenarios: Audio and video calls, online meetings, and internal corporate training.

> **When to Choose RTC Engine?**If you need more flexible integration options, want to achieve a highly customizable user interface, and require support for more platforms, you can choose RTC Engine;If you have a clear communication scenario, want to quickly launch your project, need ready-to-use UI components, and mainstream platforms can meet your business needs, you can choose other products (Call/Conference/Live).

### Chat

Chat is a product with pre-built UI components for quick instant messaging integration, and can be seamlessly combined with voice and video solutions for enhanced communication.

#### Features

- Prebuilt UIKits: Provide chat interfaces and functional UIs for Web, Android, iOS and macOS, React Native, and Flutter platforms. They can be used directly or freely customized using the Core SDK according to your needs.
- Features:  Rich media messages, community chat, reactions, message read receipts, typing status, user online status, message search, quote reply, message translation, push notifications, user management, group management, content moderation, chat analytics and more.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e9855aa6236411f0a62e525400454e06.png)

#### Usage Scenarios

- Social Media & Community Chatï¼Bridging people and communities through in-App conversations.
- Taxi, Delivery & Food Delivery Platform Chatï¼Connecting consumers, drivers, and customers.
- Telehealth Chatï¼ï¼Elevating patient care through mobile conversations.
- Gaming Chatï¼Elevating gaming interactions through Chat features.
- Live Chatï¼Enhancing Live stream interaction through real-time Chat.
- Retail & E-commerce Customer Serviceï¼Enhancing conversion rates for brands and platforms.
- Web 3.0ï¼Enhance real-time interaction and information sharing to boost member collaboration. Enable KOLs to create group chats and send notifications, similar to Discord, supporting millions of users.

### Beauty AR

Beauty AR leverages Tencent's years of accumulated precise AI capabilities and a wealth of real-time special effects processing to integrate features such as beauty effects, makeup, filters, motion stickers, basic segmentation, gesture recognition, and facial landmark detection. It can provide a rich array of product capabilities for a wide range of video processing scenarios.

#### Features

- Cross-platform SDK: Provides SDKs for Web, Android, iOS, and Flutter platforms, enabling quick and secure integration of beauty effects.
- Features: Beauty effects, filters, makeup, 2 stickers, 3D stickers, virtual background, animoji, virtual avatars, image quality adjustment, body shaping, material production tools and more.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e996cd8f236411f0b0b1525400e889b2.png)

#### Usage Scenarios

- Video call: Various special effects capabilities such as face shape adjustment, special effects filters, beautification and makeup, animated stickers, gesture recognition, and intelligent cutouts are used to achieve an excellent audio and video calling experience.
- Short Video & Live streaming: Use special effect filters, animated stickers, green screen keying, body retouch and other special effect functions to beautify the video in real time, and create unique and wonderful content.
- Conferencing: In conferencing, online classroom and other scenarios, it is easy to change the conference background through precise portrait segmentation technology. By adding intelligent beautification, makeup, filters and animated stickers, video conferencing can also look great.
- AI camera: Based on the precise AI recognition technology, it can quickly locate facial features positions during shooting, perform real-time skin smoothing and brightening, add filters, and naturally beautify every interesting moment in life.

### In-game Voice Chat

Help developers quickly build in-game voice chat, voice messaging, voice-to-text, text-to-speech, text translation, voice changing, and other functionalities.

#### Features

- Deep Customization for Multiple Scenarios: Conducts in-depth optimization of audio and video codecs for gaming scenarios, achieving industry-leading key technical indicators in terms of bitrate, latency, and system resource consumption.
- Top-tier Infrastructure: Self-built gigabit cloud data centers with global coverage, equipped with a top-tier BGP 20-path network and over 800 nodes to provide players with a stable and ultra-fast experience.
- Suitable for various scenarios in all types of games: including voice command, channel communication, team coordination, and voice-to-text transcription.
- Features: 3D positional voice chat, proximity voice chat, voice control, speech to text, voice effects,AIi noise suppression, unlimited co-anchors and more.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea6bc3ba236411f0b0b1525400e889b2.png)

#### Usage Scenarios

- Esports Games: Enables multiple players to have voice chat in real-time with low latency, such as MOBA, battle royale, and FPS games.
- Party Games: Provides amusing real-time interactive features to make party games like Werewolf, Draw & Guess, and trivia games even more fun and exciting.
- MMO/Sandbox Games: Delivers an immersive spatial audio experience in MMO, sandbox, open world, and metaverse games.
- VR/AR Games: Enables players to communicate in the virtual world easily just like in the real world after putting on their VR/AR headset and glasses.


---
*Source: [https://trtc.io/document/69908](https://trtc.io/document/69908)*
