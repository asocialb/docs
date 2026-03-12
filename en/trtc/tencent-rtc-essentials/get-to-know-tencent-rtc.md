# Get to know Tencent RTC

Leveraging Tencent's 20+ years of experience in network and audio video technologies, Tencent RTC mainly offers multiple people voice and video calls, and low-latency interactive live streaming solutions.At Tencent RTC, we specialize in providing global enterprises with cutting-edge real-time communication solutions. Tencent RTC focuses on delivering high-quality, cost-effective, and low-latency solutions, ensuring seamless and efficient communication for businesses worldwide.

# What are the advantages of Tencent RTC?

- Ultra-high Quality: Be equipped with the same 3A audio engine as Tencent Meeting, Tencent RTC maintains normal voice call quality even at a packet loss rate of 80%, with an average end-to-end latency of less than 300ms globally.
- Low Barrier to Entry and Rapid Integration: Offers a rich array of scenario-specific components and multiple platform code examples for various sectors including entertainment, education, and enterprise services. Official support is provided for cross-platform frameworks such as Flutter and Electron.
- Cross-platform Global Interoperability: Provides cross-platform SDKs for Android, iOS, Windows, Mac, and Web, with a real-time transport network that covers over 200 countries and regions worldwide.
- High-quality Global Deployment: Features worldwide accelerating access with global PoPs, including Asia-Pacific, North America, Europe, the Middle East, Africa, and Latin America.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/10a784212f0511f08caa5254005ef0f7.png)

# What products are included in Tencent RTC?

| Product | Introduction | Features | Applicable Scenarios | Integration Methods |
| --- | --- | --- | --- | --- |
| [Call](https://www.tencentcloud.com/document/product/647/50989) | One-on-one and group video/audio calls | 1V1 Audio/Video CallGroup Audio/Video CallVirtual BackgroundsInvite to/Join Ongoing CallsCall Status DisplayVideo Call Switch to Audio CallMake/Answer/Decline/Hang Up a CallCall Notifications and Offline Push			Floating WindowCustom RingtonesAI Noise SuppressionOn-Cloud Recording | Audio and Video Social CallRemote healthcareSales and consultingInteractive virtual classroom | UIKits;Core SDK |
| [Conference](https://www.tencentcloud.com/document/product/647/54634) | Large-scale meetings and webinars with video/audio | Virtual BackgroundsScreen SharingAudio Mix by Default				Member Management				Room Management				Free Speech Mode				On-Stage Speech Mode	Microphone ManagementChat in ConferenceMulti-Terminal LoginAI Noise SuppressionOn-Cloud Recording | Audio and video conferencingOnline educationCorporate and professional trainingDigital recruitmentWebinarsRemote healthcare | UIKitsï¼Core SDK |
| [Live](https://trtc.io/document/60034?platform=ios&product=live) | Interactive video and voice live streaming | Go Live							Chat in Live Room/EmojiAnchor Connection and BattleMulti-guestInteractive Gift				Floating Window					Background Music				Audience  ManagementVoice EffectsPC Live Streaming AssistantAI Noise SuppressionOn-Cloud Recording |  Video social networkingVoice chat roomLive performance streamingGame live streamingE-commerce sellingOnline video classroomWeb 3.0 | UIKitsï¼Core SDK |
| [RTC Engine](https://www.tencentcloud.com/document/product/647/35078#) | FullyÂ customizable real-time communication SDKs | Audio/Video CallInteractive Video StreamingOn-Cloud RecordingOn-Cloud MixTranscodingRelay to CDNConversational AI ServicesSpeech-to-TextAI Noise SuppressionPushing to Rooms over RTMP3D Spatial AudioScaled Video CodingRegion of Interest CodingHigh Video ResolutionVoice Effects | All real-time audio and video call scenarios, such as:Voice/video call social networkingInteractive video live streamingInteractive virtual classroomLarge-scale online eventsRemote healthcare | Core SDK |
| [Chat](https://trtc.io/document/50061?platform=web&product=chat) | All-in-one private and group instant messaging | Rich Media MessagesCommunity Chat ReactionsMessage Read ReceiptsTyping StatusUser Online StatusMessage SearchQuote ReplyMessage TranslationPush NotificationsUser ManagementGroup ManagementContent ModerationChat Analytics | Social media and community messagingRide-hailing, delivery, and food delivery platform chatRemote healthcare chatIn-game chatChat in live roomRetail customer service chat | UIKitsï¼Core SDK |
| [Beauty AR](https://trtc.io/document/60216?platform=web&product=beautyar) | A powerful tool seamlessly integrating beauty filters, makeup, and special effects | Beauty EffectsFiltersMakeup2D Stickers3D StickersVirtual Backgrounds			AnimojiVirtual AvatarsImage Quality AdjustmentBody ShapingMaterial Production Tools | Interactive video live streamingInteractive video callsShort videosGamingAI cameraVideo conferencing | Core SDK |
| [In-game Voice Chat (GME)](https://www.tencentcloud.com/document/product/607/10835?lang=en&pg=) | In-game real-time voice chat | 3D Positional Voice ChatProximity Voice ChatVoice ControlSpeech to TextVoice EffectsAI Noise SuppressionUnlimited Co-anchors | Esports gamesParty gamesMMO/Sandbox gamesVR/AR games | Core SDK |

> **Noteï¼**Call, Conference, Live, and Chat all come with pre-built UIs that meet the needs of most scenarios, and they also support more customized features using the Core SDK. The RTC Engine is a multifunctional toolbox without UI, suitable for all real-time interactive voice and video scenarios, supporting more complex use cases.**UIKits:**Provide pre-made UI components and business logic code that simplify basic work, allow flexible feature customization, and are easy to integrate. They enable rapid integration within a day, accelerating market validation.**Core SDK:** Supports the highest level of customization, allowing the extension of advanced features with more flexible integration options to meet more complex business needs.

# What is the billing model of Tencent RTC?

The service items of Tencent RTC  (including Call, Conference, Live, and RTC-engine), Chat and Beauty AR follow a combined billing model: a prepaid monthly subscription as the base, with pay-as-you-go charges for excess usage. For more information, please refer to the [Billing Overview](https://www.tencentcloud.com/document/product/647/64149).

**Monthly subscription:**Tencent RTC introduced prepaid package plans starting from March 7, 2023 (UTC+8), unlocking different value-added functional services for various applications (SDKAppIDs). The package plans for Call, Conference, Live, Chat, Beauty AR, RTC Engine, and Monitoring Dashboard are all monthly subscription packages. You can choose the appropriate prepaid package plan for your business scenario.

**Pay-as-you-go:**Tencent RTC defaults to prepaid package billing. When the service usage cannot be deducted by the package or exceeds the balance of the prepaid package, it will be billed based on pay-as-you-go according to your actual business usage.

> **Note:** When you start testing, we recommend beginning with a free trial. Each of our products offers a free trial version, which helps you to make the best choice based on the product features and your business scenarios.When you test with real users or launch your project in a production environment, we suggest purchasing a monthly subscription plan. We have designed a [Starter Plan](https://trtc.io/pricing/promotion) for new users when making their first purchase. It allows you to use our products with a monthly package at a significantly reduced price. During the validity period, the pay-as-you-go billing mode will be enabled for your account, allowing you to scale up at any time. Even if usage exceeds the plan limit, the service will not be interrupted.You can choose which product to use based on your specific scenario. If your business covers multiple product use cases, you can opt to use RTC Engine.


---
*Source: [https://trtc.io/document/69907](https://trtc.io/document/69907)*
