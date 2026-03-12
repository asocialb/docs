# TUIChat

The following content will show you how to set chat interface self Definition options.

## Message list

### Set background color and image

API's function: Set the chat interface message list background color and background image, effective for all chat interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swiftvar backgroundColor: UIColor? {    get {        return TUIChatConfig.shared.backgroudColor    }    set {        TUIChatConfig.shared.backgroudColor = newValue ?? .black    }}var backgroundImage: UIImage? {    get {        return TUIChatConfig.shared.backgroudImage    }    set {        TUIChatConfig.shared.backgroudImage = newValue ?? UIImage()    }}
```

```
// TUIChatConfig_Minimalist.h/** * Customize the backgroud color of message list interface. * This configuration takes effect in all message list interfaces. */@property (nonatomic, strong) UIColor *backgroudColor;/** * Customize the backgroud image of message list interface. * This configuration takes effect in all message list interfaces. */@property (nonatomic, strong) UIImage *backgroudImage;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the message list interface.TUIChatConfig_Minimalist.shared.backgroundColor = UIColor.tui_color(withHex: "#E1FFFF")TUIChatConfig_Minimalist.shared.backgroundImage = UIImage.init(named: "your_background_image")
```

```
// When to call: Before initializing the message list interface.[TUIChatConfig_Minimalist sharedConfig].backgroudColor = [UIColor tui_colorWithHex:@"#E1FFFF"];[TUIChatConfig_Minimalist sharedConfig].backgroudImage = [UIImage imageNamed:@"your_background_image"];
```

Result:

| Set Background Color | Set Background Image | Default |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6db41c5c5e1d11efb927525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/73c796345e1d11efb927525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6fde144a5e1d11efb36952540075b605.png) |

### Set user avatar and corner radius

API Function: Sets the user avatar type and corner radius. Currently supported types are rectangle, circle, rounded rectangle. Only the rounded rectangle type uses the corner radius. Effective for the message list, conversation list, and contact list.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** *  Customize the style of avatar. *  The default value is TUIAvatarStyleCircle. *  This configuration takes effect in all avatars. */public var avatarStyle: TUIAvatarStyle_Minimalist {    get {        return TUIAvatarStyle_Minimalist(rawValue: TUIConfig.default().avatarType.rawValue)!    }    set {        TUIConfig.default().avatarType = TUIKitAvatarType(rawValue: newValue.rawValue)!    }}/** *  Customize the corner radius of the avatar. *  This configuration takes effect in all avatars. */public var avatarCornerRadius: CGFloat {    get {        return TUIConfig.default().avatarCornerRadius    }    set {        TUIConfig.default().avatarCornerRadius = newValue    }}
```

```
// TUIChatConfig_Minimalist.htypedef NS_ENUM(NSInteger, TUIAvatarStyle) {    TUIAvatarStyleRectangle,    TUIAvatarStyleCircle,    TUIAvatarStyleRoundedRectangle,};/** *  Customize the style of avatar. *  The default value is TUIAvatarStyleCircle. *  This configuration takes effect in all avatars. */@property (nonatomic, assign) TUIAvatarStyle avatarStyle;/** *  Customize the corner radius of the avatar. *  This configuration takes effect in all avatars. */@property (nonatomic, assign) CGFloat avatarCornerRadius;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the TUIKit interfaces.TUIChatConfig_Minimalist.shared.avatarStyle = .rectangle// Set cornerRadiusTUIChatConfig_Minimalist.shared.avatarStyle = .roundedRectangleTUIChatConfig_Minimalist.shared.avatarCornerRadius = 10
```

```
// When to call: Before initializing the TUIKit interfaces.[TUIChatConfig_Minimalist sharedConfig].avatarStyle = TUIAvatarStyleRectangle;// Set cornerRadius[TUIChatConfig_Minimalist sharedConfig].avatarStyle = TUIAvatarStyleRoundedRectangle;[TUIChatConfig_Minimalist sharedConfig].avatarCornerRadius = 10;
```

Result:

| Default circular avatar | Set rounded rectangle avatar | Set rectangular avatar |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/18df3ab25b9f11ef8f105254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3d6d3aca5b9f11efb927525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3ef9038d5b9f11ef8f105254002693fd.png) |

### Enable group grid avatar

API Function: Set group avatar to display as nine-grid. Effective for message lists, conversation lists, and contact lists.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Display the group avatar in the nine-square grid style. * The default value is YES. * This configuration takes effect in all groups. */public var enableGroupGridAvatar: Bool {    get {        return TUIConfig.default().enableGroupGridAvatar    }    set {        TUIConfig.default().enableGroupGridAvatar = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Display the group avatar in the nine-square grid style. * The default value is YES. * This configuration takes effect in all groups. */@property (nonatomic, assign) BOOL enableGroupGridAvatar;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the TUIKit interfaces.TUIChatConfig_Minimalist.shared.enableGroupGridAvatar = false
```

```
// When to call: Before initializing the TUIKit interfaces.[TUIChatConfig_Minimalist sharedConfig].enableGroupGridAvatar = NO;
```

Result:

| Disable group avatar as nine-grid | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e875e4e55e1d11ef998b525400f69702.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e8035fe35e1d11ef8357525400bdab9d.png) |

### Enable typing indicator

API function: Enable the "typing" indicator. Effective for all 1v1 chat message interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** *  Enable the display "Alice is typing..." on one-to-one chat interface. *  The default value is YES. *  This configuration takes effect in all one-to-one chat message list interfaces. */public var enableTypingIndicator: Bool {    get {        return TUIChatConfig.shared.enableTypingStatus    }    set {        TUIChatConfig.shared.enableTypingStatus = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** *  Enable the display "Alice is typing..." on one-to-one chat interface. *  The default value is YES. *  This configuration takes effect in all one-to-one chat message list interfaces. */@property (nonatomic, assign) BOOL enableTypingIndicator;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the message list interface.TUIChatConfig_Minimalist.shared.enableTypingIndicator = false
```

```
// When to call: Before initializing the message list interface.[TUIChatConfig_Minimalist sharedConfig].enableTypingIndicator = NO;
```

Result:

| Enable "Typing" | Disable "Typing" |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b91bf9b25ba511efb927525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b705d0a65ba511efb36952540075b605.png) |

### Enable message read receipt

API function: Enable read receipt. Once enabled, read information can be viewed in message details. Effective for all messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** *  When sending a message, set this flag to require message read receipt. *  The default value is NO. *  This configuration takes effect in all chat message list interfaces. */public var isMessageReadReceiptNeeded: Bool {    get {        return TUIChatConfig.shared.msgNeedReadReceipt    }    set {        TUIChatConfig.shared.msgNeedReadReceipt = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** *  When sending a message, set this flag to require message read receipt. *  The default value is NO. *  This configuration takes effect in all chat message list interfaces. */@property (nonatomic, assign) BOOL isMessageReadReceiptNeeded;
```

Sample code:

Swift

Objective-C

```
// When to call: Before sending messages. TUIChatConfig_Minimalist.shared.isMessageReadReceiptNeeded = true
```

```
// When to call: Before sending messages. [TUIChatConfig_Minimalist sharedConfig].isMessageReadReceiptNeeded = YES;
```

Result:

| Enable read receipt | Disable read receipt |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea7b1d2f5ba611efb927525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e930b85a5ba611ef81cf525400d5f8ef.png) |

### Hide long-press message menu button

API's function: Hide specified buttons in the long-press message menu, effective for all chat messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Hide the items in the pop-up menu when user presses the message. */public class func hideItemsWhenLongPressMessage(_ items: TUIChatItemWhenLongPressMessage_Minimalist) {    let value = items.rawValue    TUIChatConfig.shared.enablePopMenuReplyAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.reply.rawValue) == 0    TUIChatConfig.shared.enablePopMenuEmojiReactAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.emojiReaction.rawValue) == 0    TUIChatConfig.shared.enablePopMenuReferenceAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.quote.rawValue) == 0    TUIChatConfig.shared.enablePopMenuPinAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.pin.rawValue) == 0    TUIChatConfig.shared.enablePopMenuRecallAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.recall.rawValue) == 0    TUIChatConfig.shared.enablePopMenuTranslateAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.translate.rawValue) == 0    TUIChatConfig.shared.enablePopMenuConvertAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.convert.rawValue) == 0    TUIChatConfig.shared.enablePopMenuForwardAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.forward.rawValue) == 0    TUIChatConfig.shared.enablePopMenuSelectAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.select.rawValue) == 0    TUIChatConfig.shared.enablePopMenuCopyAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.copy.rawValue) == 0    TUIChatConfig.shared.enablePopMenuDeleteAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.delete.rawValue) == 0    TUIChatConfig.shared.enablePopMenuInfoAction = (value & TUIChatItemWhenLongPressMessage_Minimalist.info.rawValue) == 0}
```

```
// TUIChatConfig_Minimalist.htypedef NS_OPTIONS(NSInteger, TUIChatItemWhenLongPressMessage_Minimalist) {    TUIChatItemWhenLongPressMessage_Minimalist_None = 0,    TUIChatItemWhenLongPressMessage_Minimalist_Reply = 1 << 0,    TUIChatItemWhenLongPressMessage_Minimalist_EmojiReaction = 1 << 1,    TUIChatItemWhenLongPressMessage_Minimalist_Quote = 1 << 2,    TUIChatItemWhenLongPressMessage_Minimalist_Pin = 1 << 3,    TUIChatItemWhenLongPressMessage_Minimalist_Recall = 1 << 4,    TUIChatItemWhenLongPressMessage_Minimalist_Translate = 1 << 5,    TUIChatItemWhenLongPressMessage_Minimalist_Convert = 1 << 6,    TUIChatItemWhenLongPressMessage_Minimalist_Forward = 1 << 7,    TUIChatItemWhenLongPressMessage_Minimalist_Select = 1 << 8,    TUIChatItemWhenLongPressMessage_Minimalist_Copy = 1 << 9,    TUIChatItemWhenLongPressMessage_Minimalist_Delete = 1 << 10,    TUIChatItemWhenLongPressMessage_Minimalist_Info = 1 << 11,};/** * Hide the items in the pop-up menu when user presses the message. */+ (void)hideItemsWhenLongPressMessage:(TUIChatItemWhenLongPressMessage_Minimalist)items;
```

Sample code:

Swift

Objective-C

```
// When to call: Before displaying the pop-up menu when user presses the message. TUIChatConfig_Minimalist.hideItemsWhenLongPressMessage([.reply, .recall, .select])
```

```
// When to call: Before displaying the pop-up menu when user presses the message. [TUIChatConfig_Minimalist hideItemsWhenLongPressMessage:TUIChatItemWhenLongPressMessage_Minimalist_Reply|TUIChatItemWhenLongPressMessage_Minimalist_Recall|TUIChatItemWhenLongPressMessage_Minimalist_Select];
```

Result:

| Do not hide any buttons | Hide the Forward button |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3cce1d985ba911efb36952540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f5fee8a5ba911efb66652540055f650.png) |

### Hide video and audio call button

API's function: Hide the audio and video call buttons at the top of the message list, effective for all chat message interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** *  Hide the "Video Call" button in the message list header. *  The default value is NO. */public var hideVideoCallButton: Bool {    get {        return !TUIChatConfig.shared.enableVideoCall    }    set {        TUIChatConfig.shared.enableVideoCall = !newValue    }}/** *  Hide the "Audio Call" button in the message list header. *  The default value is NO. */public var hideAudioCallButton: Bool {    get {        return !TUIChatConfig.shared.enableAudioCall    }    set {        TUIChatConfig.shared.enableAudioCall = !newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** *  Hide the "Video Call" button in the message list header. *  The default value is NO. */@property (nonatomic, assign) BOOL hideVideoCallButton;/** *  Hide the "Audio Call" button in the message list header. *  The default value is NO. */@property (nonatomic, assign) BOOL hideAudioCallButton;
```

Sample code:

Swift

Objective-C

```
// When to call: Before entering the message list interface.TUIChatConfig_Minimalist.shared.hideVideoCallButton = falseTUIChatConfig_Minimalist.shared.hideAudioCallButton = false
```

```
// When to call: Before entering the message list interface.[TUIChatConfig_Minimalist sharedConfig].hideVideoCallButton = YES;[TUIChatConfig_Minimalist sharedConfig].hideAudioCallButton = YES;
```

Result:

| Hide video call button | Hide audio call button | Default Value |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/383499645bac11efb36952540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/183f87f25e1e11ef998b525400f69702.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3662c42a5bac11efb927525400fdb830.png) |

### Enable floating window for call

API's function: Enable the audio and video call floating window. If enabled, you can float the audio and video call interface in a small window on the chat interface. Effective for all audio and video call interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Turn on audio and video call floating windows, * The default value is YES. */public var enableFloatWindowForCall: Bool {    get {        return TUIChatConfig.shared.enableFloatWindowForCall    }    set {        TUIChatConfig.shared.enableFloatWindowForCall = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Turn on audio and video call floating windows, * The default value is YES. */@property (nonatomic, assign) BOOL enableFloatWindowForCall;
```

Sample code:

Swift

Objective-C

```
// When to call: Before entering the message list interface.TUIChatConfig_Minimalist.shared.enableFloatWindowForCall = false
```

```
// When to call: Before entering the message list interface.[TUIChatConfig_Minimalist sharedConfig].enableFloatWindowForCall = NO;
```

### Enable multi-device login for call

API's function: Enable multi-device log in for audio and video calls, effective for all audio and video calls.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Enable multi-terminal login function for audio and video calls * The default value is NO. */public var enableMultiDeviceForCall: Bool {    get {        return TUIChatConfig.shared.enableMultiDeviceForCall    }    set {        TUIChatConfig.shared.enableMultiDeviceForCall = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Enable multi-terminal login function for audio and video calls * The default value is NO. */@property (nonatomic, assign) BOOL enableMultiDeviceForCall;
```

Sample code:

Swift

Objective-C

```
// When to call: Before entering the message list interface.TUIChatConfig_Minimalist.shared.enableMultiDeviceForCall = true
```

```
// When to call: Before entering the message list interface.[TUIChatConfig_Minimalist sharedConfig].enableMultiDeviceForCall = YES;
```

### Set custom top view

API's function: Set a custom view at the top of the chat interface, effective for all chat message interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Add a custom view at the top of the chat interface. * This view will be displayed at the top of the message list and will not slide up. */public class func setCustomTopView(_ view: UIView) {    TUIBaseChatViewController_Minimalist.customTopView = view}
```

```
// TUIChatConfig_Minimalist.h/** * Add a custom view at the top of the chat interface. * This view will be displayed at the top of the message list and will not slide up. */+ (void)setCustomTopView:(UIView *)view;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the message list interface.// tipsView is your customized view.TUIChatConfig_Minimalist.shared.setCustomTopView(tipsView)
```

```
// When to call: Before initializing the message list interface.// tipsView is your customized view.[TUIChatConfig_Minimalist setCustomTopView:tipsView];
```

Result:

| Set custom view | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/386e940f5bb411ef998b525400f69702.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/386d655c5bb411efb927525400fdb830.png) |

### Set not to update the unread count

API function: Set the upcoming message to not update the conversation unread count. Effective for all messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Set this parameter when the sender sends a message, and the receiver will not update the unread count after receiving the message. * The default value is NO. */public var isExcludedFromUnreadCount: Bool {    get {        return TUIConfig.default().isExcludedFromUnreadCount    }    set {        TUIConfig.default().isExcludedFromUnreadCount = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Set this parameter when the sender sends a message, and the receiver will not update the unread count after receiving the message. * The default value is NO. */@property (nonatomic, assign) BOOL isExcludedFromUnreadCount;
```

Sample code:

Swift

Objective-C

```
// When to call: Before sending messages.TUIChatConfig_Minimalist.shared.isExcludedFromUnreadCount = true
```

```
// When to call: Before sending messages.[TUIChatConfig_Minimalist sharedConfig].isExcludedFromUnreadCount = YES;
```

### Set not to update the conversation lastMsg

API function: Set the upcoming message to not update the conversation lastMsg. Effective for all messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Set this parameter when the sender sends a message, and the receiver will not update the last message of the conversation after receiving the message. * The default value is NO. */public var isExcludedFromLastMessage: Bool {    get {        return TUIConfig.default().isExcludedFromLastMessage    }    set {        TUIConfig.default().isExcludedFromLastMessage = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Set this parameter when the sender sends a message, and the receiver will not update the last message of the conversation after receiving the message. * The default value is NO. */@property (nonatomic, assign) BOOL isExcludedFromLastMessage;
```

Sample code:

Swift

Objective-C

```
// When to call: Before sending messages.TUIChatConfig_Minimalist.shared.isExcludedFromLastMessage = true
```

```
// When to call: Before sending messages.[TUIChatConfig_Minimalist sharedConfig].isExcludedFromLastMessage = YES;
```

### Set message recall interval

API function: Set message recall time interval, effective for all messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Time interval within which a message can be recalled after being sent. * The default value is 120 seconds. * If you want to adjust this configuration, please modify the setting on Chat Console synchronously: https://trtc.io/document/34419?platform=web&product=chat&menulabel=uikit#message-recall-settings */public var timeIntervalForAllowedMessageRecall: UInt {    get {        return TUIChatConfig.shared.timeIntervalForMessageRecall    }    set {        TUIChatConfig.shared.timeIntervalForMessageRecall = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Time interval within which a message can be recalled after being sent. * The default value is 120 seconds. * If you want to adjust this configuration, please modify the setting on Chat Console synchronously: https://trtc.io/document/34419?platform=web&product=chat&menulabel=uikit#message-recall-settings */@property (nonatomic, assign) NSUInteger timeIntervalForAllowedMessageRecall;
```

Sample code:

Swift

Objective-C

```
// When to call: Before sending messages.TUIChatConfig_Minimalist.shared.timeIntervalForAllowedMessageRecall = 90
```

```
// When to call: Before sending messages.[TUIChatConfig_Minimalist sharedConfig].timeIntervalForAllowedMessageRecall = 90;
```

### Set maximum recording duration for voice and video messages

API function: Set the maximum recording duration for voice and video messages, effective for all voice and video messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Maximum audio recording duration, no more than 60s. * The default value is 60 seconds. */public var maxAudioRecordDuration: TimeInterval {    get {        return TUIChatConfig.shared.maxAudioRecordDuration    }    set {        TUIChatConfig.shared.maxAudioRecordDuration = newValue    }}/** * Maximum video recording duration, no more than 15s. * The default value is 15 seconds. */public var maxVideoRecordDuration: TimeInterval {    get {        return TUIChatConfig.shared.maxVideoRecordDuration    }    set {        TUIChatConfig.shared.maxVideoRecordDuration = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Maximum audio recording duration, no more than 60s. * The default value is 60 seconds. */@property (nonatomic, assign) CGFloat maxAudioRecordDuration;/** * Maximum video recording duration, no more than 15s. * The default value is 15 seconds. */@property (nonatomic, assign) CGFloat maxVideoRecordDuration;
```

Sample code:

Swift

Objective-C

```
// When to call: Before recording audio or video messages.TUIChatConfig_Minimalist.shared.maxAudioRecordDuration = 10TUIChatConfig_Minimalist.shared.maxVideoRecordDuration = 10
```

```
// When to call: Before recording audio or video messages.[TUIChatConfig_Minimalist sharedConfig].maxAudioRecordDuration = 10;[TUIChatConfig_Minimalist sharedConfig].maxVideoRecordDuration = 10;
```

### Enable custom ringtones

API function: Set the ringtone on Android devices to a built-in custom ringtone upon receiving a message, effective for all messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Enable custom ringtone. * This config takes effect only for Android devices. */public var enableAndroidCustomRing: Bool {    get {        return TUIConfig.default().enableCustomRing    }    set {        TUIConfig.default().enableCustomRing = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Enable custom ringtone. * This config takes effect only for Android devices. */@property (nonatomic, assign) BOOL enableAndroidCustomRing;
```

Sample code:

Swift

Objective-C

```
// When to call: Before sending messages.TUIChatConfig_Minimalist.shared.enableAndroidCustomRing = true
```

```
// When to call: Before sending messages.[TUIChatConfig_Minimalist sharedConfig].enableAndroidCustomRing = YES;
```

### Set to play voice messages using loudspeakers by default

API's function: Set the default playback for voice message to use the speaker instead of the earpiece. Effective for all voice messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Call this method to use speakers instead of handsets by default when playing voice messages. */public static func setPlayingSoundMessageViaSpeakerByDefault() {    if TUIVoiceMessageCellData.getAudioplaybackStyle() == .handset {        TUIVoiceMessageCellData.changeAudioPlaybackStyle()    }}
```

```
// TUIChatConfig_Minimalist.h/** * Call this method to use speakers instead of handsets by default when playing voice messages. */+ (void)setPlayingSoundMessageViaSpeakerByDefault;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the Message interface.TUIChatConfig_Minimalist.setPlayingSoundMessageViaSpeakerByDefault()
```

```
// When to call: Before initializing the Message interface.[TUIChatConfig_Minimalist setPlayingSoundMessageViaSpeakerByDefault];
```

### Register custom message

API's function: Register custom Definition messages. Please refer to the documentation for usage scenarios [Add custom messages](https://www.tencentcloud.com/zh/document/product/1047/50043).

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Register custom message. * - Parameters: *   - businessID: Customized messageâs businessID, which is unique. *   - messageCellClassName: Customized message's MessagCell class name. *   - messageCellDataClassName: Customized message's MessagCellData class name. */public func registerCustomMessage(businessID: String, messageCellClassName: String, messageCellDataClassName: String) {    TUIChatConfig.shared.registerCustomMessage(businessID: businessID, messageCellClassName: messageCellClassName, messageCellDataClassName: messageCellDataClassName, styleType: .minimalist)}
```

```
// TUIChatConfig_Minimalist.h/** * Register custom message. * - Parameters: *   - businessID: Customized messageâs businessID, which is unique. *   - cellName: Customized message's MessagCell class name. *   - cellDataName: Customized message's MessagCellData class name. */- (void)registerCustomMessage:(NSString *)businessID         messageCellClassName:(NSString *)cellName     messageCellDataClassName:(NSString *)cellDataName;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the Message List interface.TUIChatConfig_Minimalist.shared.registerCustomMessage(businessID: "text_link", messageCellClassName: "TUILinkCell", messageCellDataClassName: "TUILinkCellData")
```

```
// When to call: Before initializing the Message List interface.[[TUIChatConfig_Minimalist sharedConfig] registerCustomMessage:BussinessID_TextLink                                           messageCellClassName:@"TUILinkCell"                                      messageCellDataClassName:@"TUILinkCellData"];
```

### Insert a local tips message

API's function: Insert a local tips message to the specified chat.

API prototype:

Swift

Objective-C

```
// TUIChatBaseDataProvider.swift/** * Insert local tips message. * - Parameters: *   - content: tips message content *   - chatID: if is group chat,chatID is group id,if is single chat,chatID is user id *   - isGroup: whether is group chat */class func insertLocalTipsMessage(_ content: String, chatID: String, isGroup: Bool)
```

```
// TUIChatBaseDataProvider.h/** * Insert local tips message. * - Parameters: *   - content: tips message content *   - chatID: if is group chat,chatID is group id,if is single chat,chatID is user id *   - isGroup: whether is group chat */+ (void)insertLocalTipsMessage:(NSString *)content chatID:(NSString *)chatID isGroup:(BOOL)isGroup;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the Message List interface.TUIChatBaseDataProvider.insertLocalTipsMessage("Test Tips", chatID: "100480", isGroup: false)
```

```
// When to call: Before initializing the Message List interface.[TUIChatBaseDataProvider insertLocalTipsMessage:@"Test Tips" chatID:@"100480" isGroup:NO];
```

### Customize events when click and long press the user avatar

API's function: Event callback for user clicks and long presses on the user avatar in the message list.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swiftpublic protocol TUIChatConfigDelegate_Minimalist: NSObjectProtocol {    /**     * Tells the delegate a user's avatar in the chat list is clicked.     * Returning YES indicates this event has been intercepted, and Chat will not process it further.     * Returning NO indicates this event is not intercepted, and Chat will continue to process it.     */    func onUserAvatarClicked(view: UIView, messageCellData: TUIMessageCellData) -> Bool    /**     * Tells the delegate a user's avatar in the chat list is long pressed.     * Returning YES indicates that this event has been intercepted, and Chat will not process it further.     * Returning NO indicates that this event is not intercepted, and Chat will continue to process it.     */    func onUserAvatarLongPressed(view: UIView, messageCellData: TUIMessageCellData) -> Bool}
```

```
// TUIChatConfig_Minimalist.h@protocol TUIChatConfigDelegate_Minimalist <NSObject>/** * Tells the delegate a user's avatar in the chat list is clicked. * Returning YES indicates this event has been intercepted, and Chat will not process it further. * Returning NO indicates this event is not intercepted, and Chat will continue to process it. */- (BOOL)onUserAvatarClicked:(UIView *)view messageCellData:(TUIMessageCellData *)celldata;/** * Tells the delegate a user's avatar in the chat list is long pressed. * Returning YES indicates that this event has been intercepted, and Chat will not process it further. * Returning NO indicates that this event is not intercepted, and Chat will continue to process it. */- (BOOL)onUserAvatarLongPressed:(UIView *)view messageCellData:(TUIMessageCellData *)celldata;@end
```

Sample code:

Swift

Objective-C

```
TUIChatConfig_Minimalist.shared.delegate = selffunc onUserAvatarClicked(view: UIView, messageCellData: TUIMessageCellData) -> Bool {    // Customize your own action when user avatar is clicked.    print("onUserAvatarClicked")    return true}func onUserAvatarLongPressed(view: UIView, messageCellData: TUIMessageCellData) -> Bool {    // Customize your own action when user avatar is long pressed.    print("onUserAvatarLongPressed")    return true}
```

```
[TUIChatConfig_Minimalist sharedConfig].delegate = self;// TUIChatConfigDelegate_Minimalist- (BOOL)onUserAvatarClicked:(UIView *)view messageCellData:(TUIMessageCellData *)celldata {    // Customize your own action when user avatar is clicked.    NSLog(@"onUserAvatarClicked, cellData: %@", celldata);    return YES;}- (BOOL)onUserAvatarLongPressed:(UIView *)view messageCellData:(TUIMessageCellData *)celldata {    // Customize your own action when user avatar is long pressed.    NSLog(@"onUserAvatarLongPressed, cellData: %@", celldata);    return YES;}
```

### Customize events when click and long press the message

API's function: Event callback for user clicks and long presses on messages in the message list.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swiftpublic protocol TUIChatConfigDelegate_Minimalist: NSObjectProtocol {    /**     * Tells the delegate a message in the chat list is clicked.     * Returning YES indicates that this event has been intercepted, and Chat will not process it further.     * Returning NO indicates that this event is not intercepted, and Chat will continue to process it.     */    func onMessageClicked(view: UIView, messageCellData: TUIMessageCellData) -> Bool    /**     * Tells the delegate a message in the chat list is long pressed.     * Returning YES indicates that this event has been intercepted, and Chat will not process it further.     * Returning NO indicates that this event is not intercepted, and Chat will continue to process it.     */    func onMessageLongPressed(view: UIView, messageCellData: TUIMessageCellData) -> Bool}
```

```
// TUIChatConfig_Minimalist.h@protocol TUIChatConfigDelegate_Minimalist <NSObject>/** * Tells the delegate a message in the chat list is clicked. * Returning YES indicates that this event has been intercepted, and Chat will not process it further. * Returning NO indicates that this event is not intercepted, and Chat will continue to process it. */- (BOOL)onMessageClicked:(UIView *)view messageCellData:(TUIMessageCellData *)celldata;/** * Tells the delegate a message in the chat list is long pressed. * Returning YES indicates that this event has been intercepted, and Chat will not process it further. * Returning NO indicates that this event is not intercepted, and Chat will continue to process it. */- (BOOL)onMessageLongPressed:(UIView *)view messageCellData:(TUIMessageCellData *)celldata;@end
```

Sample code:

Swift

Objective-C

```
TUIChatConfig_Minimalist.sharedConfig.delegate = selffunc onMessageClicked(view: UIView, messageCellData: TUIMessageCellData) -> Bool {    // Customize your own action when message is clicked.    print("onMessageClicked")    return true}func onMessageLongPressed(view: UIView, messageCellData: TUIMessageCellData) -> Bool {    // Customize your own action when message is long pressed.    print("onMessageLongPressed")    return true}
```

```
[TUIChatConfig_Minimalist sharedConfig].delegate = self;// TUIChatConfigDelegate_Minimalist- (BOOL)onMessageClicked:(UIView *)view messageCellData:(TUIMessageCellData *)celldata {    // Customize your own action when message is clicked.    NSLog(@"onMessageClicked, cellData: %@", celldata);    return YES;}- (BOOL)onMessageLongPressed:(UIView *)view messageCellData:(TUIMessageCellData *)celldata {    // Customize your own action when message is long pressed.    NSLog(@"onMessageLongPressed, cellData: %@", celldata);    return YES;}
```

## Message Style

### Set the style of text messages

API's function: Set the text color and font for sent and received text messages. Effective for all text messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * The color of send text message. */public var sendTextMessageColor: UIColor? {    get {        return TUITextMessageCell_Minimalist.outgoingTextColor    }    set {        TUITextMessageCell_Minimalist.outgoingTextColor = newValue    }}/** * The font of send text message. */public var sendTextMessageFont: UIFont? {    get {        return TUITextMessageCell_Minimalist.outgoingTextFont ?? UIFont()    }    set {        TUITextMessageCell_Minimalist.outgoingTextFont = newValue    }}/** * The color of receive text message. */public var receiveTextMessageColor: UIColor? {    get {        return TUITextMessageCell_Minimalist.incommingTextColor ?? UIColor()    }    set {        TUITextMessageCell_Minimalist.incommingTextColor = newValue    }}/** * The font of receive text message. */public var receiveTextMessageFont: UIFont? {    get {        return TUITextMessageCell_Minimalist.incommingTextFont ?? UIFont()    }    set {        TUITextMessageCell_Minimalist.incommingTextFont = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * The color of send text message. */@property(nonatomic, assign) UIColor *sendTextMessageColor;/** * The font of send text message. */@property(nonatomic, assign) UIFont *sendTextMessageFont;/* * The color of receive text message. */@property(nonatomic, assign) UIColor *receiveTextMessageColor;/** * The font of receive text message. */@property(nonatomic, assign) UIFont *receiveTextMessageFont;
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.shared.sendTextMessageColor = UIColor.tui_color(withHex: "#00BFFF")TUIChatConfig_Minimalist.shared.sendTextMessageFont = UIFont.systemFont(ofSize: 20)TUIChatConfig_Minimalist.shared.receiveTextMessageColor = UIColor.tui_color(withHex: "#2E8B57")TUIChatConfig_Minimalist.shared.receiveTextMessageFont = UIFont.systemFont(ofSize: 20)
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist sharedConfig].sendTextMessageColor = [UIColor tui_colorWithHex:@"#00BFFF"];[TUIChatConfig_Minimalist sharedConfig].sendTextMessageFont = [UIFont systemFontOfSize:20];[TUIChatConfig_Minimalist sharedConfig].receiveTextMessageColor = [UIColor tui_colorWithHex:@"#2E8B57"];[TUIChatConfig_Minimalist sharedConfig].receiveTextMessageFont = [UIFont systemFontOfSize:20];
```

Result:

| Set text message color | Set text message font | Default |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc5114485e0a11ef81cf525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/809603185e0b11ef8357525400bdab9d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ba37fe5f5e0a11efb36952540075b605.png) |

### Set the style of system messages

API's function: Set the font, color, and background color of system notification messages. Effective for all system notification messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * The text color of system message. */public var systemMessageTextColor: UIColor? {    get {        return TUISystemMessageCellData.textColor    }    set {        TUISystemMessageCellData.textColor = newValue    }}/** * The font of system message. */public var systemMessageTextFont: UIFont? {    get {        return TUISystemMessageCellData.textFont    }    set {        TUISystemMessageCellData.textFont = newValue    }}/** * The background color of system message. */public var systemMessageBackgroundColor: UIColor? {    get {        return TUISystemMessageCellData.textBackgroundColor    }    set {        TUISystemMessageCellData.textBackgroundColor = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * The text color of system message. */@property (nonatomic, strong) UIColor *systemMessageTextColor;/** * The font of system message. */@property (nonatomic, strong) UIFont *systemMessageTextFont;/** * The background color of system message. */@property (nonatomic, strong) UIColor *systemMessageBackgroundColor;
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.shared.systemMessageTextColor = UIColor.tui_color(withHex: "#FF8C00")TUIChatConfig_Minimalist.shared.systemMessageTextFont = UIFont.systemFont(ofSize: 24)TUIChatConfig_Minimalist.shared.systemMessageBackgroundColor = UIColor.tui_color(withHex: "#F0FFF0")
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist sharedConfig].systemMessageTextColor = [UIColor tui_colorWithHex:@"#FF8C00"];[TUIChatConfig_Minimalist sharedConfig].systemMessageTextFont = [UIFont systemFontOfSize:24];[TUIChatConfig_Minimalist sharedConfig].systemMessageBackgroundColor = [UIColor tui_colorWithHex:@"#F0FFF0"];
```

Result:

| Set the font, color, and background color of system notification messages | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d85589285e0a11efb66652540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c9e0d6925e0a11efb66652540055f650.png) |

## Message Layout

### Set the message layout

API's function: Set the layout for various types of messages, effective for specified messages.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Text message cell layout of my sent message. */public func sendTextMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .text, isSender: true)}/** * Text message cell layout of my received message. */public func receiveTextMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .text, isSender: false)}/** * Image message cell layout of my sent message. */public func sendImageMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .image, isSender: true)}/** * Image message cell layout of my received message. */public func receiveImageMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .image, isSender: false)}/** * Voice message cell layout of my sent message. */public func sendVoiceMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .voice, isSender: true)}/** * Voice message cell layout of my received message. */public func receiveVoiceMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .voice, isSender: false)}/** * Video message cell layout of my sent message. */public func sendVideoMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .video, isSender: true)}/** * Video message cell layout of my received message. */public func receiveVideoMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .video, isSender: false)}/** * Other message cell layout of my sent message. */public func sendMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .other, isSender: true)}/** * Other message cell layout of my received message. */public func receiveMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .other, isSender: false)}/** * System message cell layout. */public func systemMessageLayout() -> TUIMessageCellLayout {    return getMessageLayout(ofType: .system, isSender: false)}
```

```
// TUIMessageCellLayout.h@interface TUIMessageCellLayout : NSObject/** * The insets of message */@property(nonatomic, assign) UIEdgeInsets messageInsets;/** * The insets of bubble content. */@property(nonatomic, assign) UIEdgeInsets bubbleInsets;/** * The insets of avatar */@property(nonatomic, assign) UIEdgeInsets avatarInsets;/** * The size of avatar */@property(nonatomic, assign) CGSize avatarSize;@end// TUIChatConfig_Minimalist.h/** * Text message cell layout of my sent message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *sendTextMessageLayout;/** * Text message cell layout of my received message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *receiveTextMessageLayout;/** * Image message cell layout of my sent message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *sendImageMessageLayout;/** * Image message cell layout of my received message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *receiveImageMessageLayout;/** * Voice message cell layout of my sent message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *sendVoiceMessageLayout;/** * Voice message cell layout of my received message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *receiveVoiceMessageLayout;/** * Video message cell layout of my sent message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *sendVideoMessageLayout;/** * Video message cell layout of my received message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *receiveVideoMessageLayout;/** * Other message cell layout of my sent message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *sendMessageLayout;/** * Other message cell layout of my received message. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *receiveMessageLayout;/** * System message cell layout. */@property(nonatomic, assign, readonly) TUIMessageCellLayout *systemMessageLayout;
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.shared.receiveTextMessageLayout().bubbleInsets = UIEdgeInsets(top: 30, left: 30, bottom: 30, right: 30)TUIChatConfig_Minimalist.shared.sendTextMessageLayout().avatarInsets = UIEdgeInsets(top: 30, left: 0, bottom: 0, right: 30)TUIChatConfig_Minimalist.shared.sendTextMessageLayout().bubbleInsets = UIEdgeInsets(top: 0, left: 0, bottom: 10, right: 20)
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist sharedConfig].receiveTextMessageLayout.bubbleInsets = UIEdgeInsetsMake(30, 30, 30, 30);[TUIChatConfig_Minimalist sharedConfig].sendTextMessageLayout.avatarInsets = UIEdgeInsetsMake(30, 0, 0, 30);[TUIChatConfig_Minimalist sharedConfig].sendTextMessageLayout.bubbleInsets = UIEdgeInsetsMake(0, 0, 10, 20);
```

Result:

| Set the avatar size | Set the avatar inset | Set bubble inset |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fb80777f5e2211ef9bf1525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6275451e5e2011efb66652540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cd45ba315e1f11ef9bf1525400a9236a.png) |

## Message bubble

### Enable message bubble display

API's function: Enable message bubble display, effective for all chat interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Enable the message display in the bubble style. * The default value is YES. */public var enableMessageBubbleStyle: Bool {    get {        return TIMConfig.shared.enableMessageBubble    }    set {        TIMConfig.shared.enableMessageBubble = newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** * Enable the message display in the bubble style. * The default value is YES. */@property(nonatomic, assign) BOOL enableMessageBubbleStyle;
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.shared.enableMessageBubbleStyle = false
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist sharedConfig].enableMessageBubbleStyle = NO;
```

Result:

| Do not display message bubbles | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/916ed3d65e2211efb927525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/93707a875e2211ef998b525400f69702.png) |

### Set bubble background image

API's function: Set bubble background images, effective for all chat interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** * Set the background image of the last sent message bubble in consecutive messages. */public var sendLastBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.outgoingBubble    }    set {        TUIBubbleMessageCell_Minimalist.outgoingBubble = newValue ?? UIImage()    }}/** * Set the background image of the non-last sent message bubble in consecutive message. */public var sendBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.outgoingSameBubble    }    set {        TUIBubbleMessageCell_Minimalist.outgoingSameBubble = newValue ?? UIImage()    }}/** * Set the background image of the sent message bubble in highlight status. */public var sendHighlightBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.outgoingHighlightedBubble    }    set {        TUIBubbleMessageCell_Minimalist.outgoingHighlightedBubble = newValue ?? UIImage()    }}/** * Set the light background image when the sent message bubble needs to flicker. */public var sendAnimateLightBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.outgoingAnimatedHighlightedAlpha20    }    set {        TUIBubbleMessageCell_Minimalist.outgoingAnimatedHighlightedAlpha20 = newValue ?? UIImage()    }}/** * Set the dark background image when the sent message bubble needs to flicker. */public var sendAnimateDarkBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.outgoingAnimatedHighlightedAlpha50    }    set {        TUIBubbleMessageCell_Minimalist.outgoingAnimatedHighlightedAlpha50 = newValue ?? UIImage()    }}/** * Set the background image of the last received message bubble in consecutive message. */public var receiveLastBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.incommingBubble    }    set {        TUIBubbleMessageCell_Minimalist.incommingBubble = newValue ?? UIImage()    }}/** * Set the background image of the non-last received message bubble in consecutive message. */public var receiveBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.incommingSameBubble    }    set {        TUIBubbleMessageCell_Minimalist.incommingSameBubble = newValue ?? UIImage()    }}/** * Set the background image of the received message bubble in highlight status. */public var receiveHighlightBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.incommingHighlightedBubble    }    set {        TUIBubbleMessageCell_Minimalist.incommingHighlightedBubble = newValue ?? UIImage()    }}/** * Set the light background image when the received message bubble needs to flicker. */public var receiveAnimateLightBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.incommingAnimatedHighlightedAlpha20    }    set {        TUIBubbleMessageCell_Minimalist.incommingAnimatedHighlightedAlpha20 = newValue ?? UIImage()    }}/** * Set the dark background image when the received message bubble needs to flicker. */public var receiveAnimateDarkBubbleBackgroundImage: UIImage? {    get {        return TUIBubbleMessageCell_Minimalist.incommingAnimatedHighlightedAlpha50    }    set {        TUIBubbleMessageCell_Minimalist.incommingAnimatedHighlightedAlpha50 = newValue ?? UIImage()    }}
```

```
// TUIChatConfig_Minimalist.h/** * Set the background image of the last sent message bubble in consecutive messages. */@property (nonatomic, strong) UIImage *sendLastBubbleBackgroundImage;/** * Set the background image of the non-last sent message bubble in consecutive message. */@property (nonatomic, strong) UIImage *sendBubbleBackgroundImage;/** * Set the background image of the sent message bubble in highlight status. */@property (nonatomic, strong) UIImage *sendHighlightBubbleBackgroundImage;/** * Set the light background image when the sent message bubble needs to flicker. */@property (nonatomic, strong) UIImage *sendAnimateLightBubbleBackgroundImage;/** * Set the dark background image when the sent message bubble needs to flicker. */@property (nonatomic, strong) UIImage *sendAnimateDarkBubbleBackgroundImage;/** * Set the background image of the last received message bubble in consecutive message. */@property (nonatomic, strong) UIImage *receiveLastBubbleBackgroundImage;/** * Set the background image of the non-last received message bubble in consecutive message. */@property (nonatomic, strong) UIImage *receiveBubbleBackgroundImage;/** * Set the background image of the received message bubble in highlight status. */@property (nonatomic, strong) UIImage *receiveHighlightBubbleBackgroundImage;/** * Set the light background image when the received message bubble needs to flicker. */@property (nonatomic, strong) UIImage *receiveAnimateLightBubbleBackgroundImage;/** * Set the dark background image when the received message bubble needs to flicker. */@property (nonatomic, strong) UIImage *receiveAnimateDarkBubbleBackgroundImage;
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.shared.sendLastBubbleBackgroundImage = [UIImage imageNamed:@"SenderTextNodeBkg@3x.png"];TUIChatConfig_Minimalist.shared.sendBubbleBackgroundImage = [UIImage imageNamed:@"SenderTextNodeBkg_Same@3x.png"];TUIChatConfig_Minimalist.shared.receiveLastBubbleBackgroundImage = [UIImage imageNamed:@"ReceiverTextNodeBkg@3x.png"];TUIChatConfig_Minimalist.shared.receiveBubbleBackgroundImage = [UIImage imageNamed:@"ReceiverTextNodeBkg_Same@3x.png"];
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist sharedConfig].sendLastBubbleBackgroundImage = [UIImage imageNamed:@"SenderTextNodeBkg@3x.png"];[TUIChatConfig_Minimalist sharedConfig].sendBubbleBackgroundImage = [UIImage imageNamed:@"SenderTextNodeBkg_Same@3x.png"];[TUIChatConfig_Minimalist sharedConfig].receiveLastBubbleBackgroundImage = [UIImage imageNamed:@"ReceiverTextNodeBkg@3x.png"];[TUIChatConfig_Minimalist sharedConfig].receiveBubbleBackgroundImage = [UIImage imageNamed:@"ReceiverTextNodeBkg_Same@3x.png"];
```

Result:

| Set bubble background image | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8b05565f5e2211efb36952540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8c923e825e2211ef998b525400f69702.png) |

## Input bar

### Display Input bar

API's function: Display the input box in the chat interface, effective for all chat interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** *  Show the input bar in the message list interface. *  The default value is YES. */public var showInputBar: Bool {    get {        return !TUIChatConfig.shared.enableMainPageInputBar    }    set {        TUIChatConfig.shared.enableMainPageInputBar = !newValue    }}
```

```
// TUIChatConfig_Minimalist.h/** *  Show the input bar in the message list interface. *  The default value is YES. */@property(nonatomic, assign) BOOL showInputBar;
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.shared.showInputBar = false
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist sharedConfig].showInputBar = NO;
```

Result:

| Hide input bar | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/389140915e2711ef8357525400bdab9d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/975094e35e2711ef8357525400bdab9d.png) |

### Hide options in more menu (global)

API's function: Hide buttons in the more menu, effective for all chat interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/** *  Hide items in more menu. */public class func hideItemsInMoreMenu(_ items: TUIChatInputBarMoreMenuItem) {    let value = items.rawValue    TUIChatConfig.shared.enableWelcomeCustomMessage = (value & TUIChatInputBarMoreMenuItem.customMessage.rawValue) == 0    TUIChatConfig.shared.showRecordVideoButton = (value & TUIChatInputBarMoreMenuItem.recordVideo.rawValue) == 0    TUIChatConfig.shared.showTakePhotoButton = (value & TUIChatInputBarMoreMenuItem.takePhoto.rawValue) == 0    TUIChatConfig.shared.showAlbumButton = (value & TUIChatInputBarMoreMenuItem.album.rawValue) == 0    TUIChatConfig.shared.showFileButton = (value & TUIChatInputBarMoreMenuItem.file.rawValue) == 0}
```

```
// TUIChatConfig_Minimalist.h/** *  Hide items in more menu. */+ (void)hideItemsInMoreMenu:(TUIChatInputBarMoreMenuItem_Minimalist)items;
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.hideItemsInMoreMenu([.customMessage, .recordVideo, .file])
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist hideItemsInMoreMenu:TUIChatInputBarMoreMenuItem_Minimalist_CustomMessage|TUIChatInputBarMoreMenuItem_Minimalist_RecordVideo|TUIChatInputBarMoreMenuItem_Minimalist_File];
```

Result:

| Hide part of the options | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3da030b05e2711efb927525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3f094d515e2711efb927525400fdb830.png) |

### Hide options in the more menu (local)

API's function: Hide buttons in the more menu, effective for specified chat interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig.swiftpublic protocol TUIChatInputBarConfigDataSource: AnyObject {/***  Implement this method to add new items to the more list of the specified model only for the minimalist version.*/func shouldHideItems(of model: TUIChatConversationModel) -> TUIChatInputBarMoreMenuItem}
```

```
// TUIChatConfig.h@protocol TUIChatInputBarConfigDataSource <NSObject>/***  Implement this method to add new items to the more list of the specified model only for the minimalist version.*/- (TUIChatInputBarMoreMenuItem)inputBarShouldHideItemsInMoreMenuOfModel:(TUIChatConversationModel *)model;@end
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.shared.inputBarDataSource = selffunc shouldHideItems(of model: TUIChatConversationModel) -> TUIChatInputBarMoreMenuItem {    if model.groupID == "your target groupID" {        return [.customMessage, .recordVideo, .file]    }    return [.none]}
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist sharedConfig].inputBarDataSource = self;- (TUIChatInputBarMoreMenuItem)inputBarShouldHideItemsInMoreMenuOfModel:(TUIChatConversationModel *)model {    if ([model.groupID isEqualToString:@"your target groupID"]) {        return TUIChatInputBarMoreMenuItem_CustomMessage|TUIChatInputBarMoreMenuItem_RecordVideo|TUIChatInputBarMoreMenuItem_File;    }    return TUIChatInputBarMoreMenuItem_None;}
```

### Add options to the more menu (local)

API's function: Add options to the more menu, effective for specified chat interfaces.

API prototype:

Swift

Objective-C

```
// TUIChatConfig.swiftpublic protocol TUIChatInputBarConfigDataSource: AnyObject {    /**     *  Implement this method to add new items to the more menu of the specified model only for the classic version.     */    func shouldAddNewItemsToMoreList(of model: TUIChatConversationModel) -> [TUICustomActionSheetItem]?}
```

```
// TUIChatConfig.h@protocol TUIChatInputBarConfigDataSource <NSObject>/** *  Implement this method to add new items to the more list of the specified model only for the minimalist version. */- (NSArray<TUICustomActionSheetItem *> *)inputBarShouldAddNewItemsToMoreListOfModel:(TUIChatConversationModel *)model;@end
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfig_Minimalist.shared.inputBarDataSource = selffunc shouldAddNewItemsToMoreList(of model: TUIChatConversationModel) -> [TUICustomActionSheetItem]? {    let item1 = TUICustomActionSheetItem(title: "item1", leftMark: UIImage(named: "item1.png") ?? UIImage()) { _ in        print("item1 is clicked")    }    let item2 = TUICustomActionSheetItem(title: "item2", leftMark: UIImage(named: "item2.png") ?? UIImage()) { _ in        print("item1 is clicked")    }    return [item1, item2]}
```

```
// When to call: After initializing the message list interface and before entering it.[TUIChatConfig_Minimalist sharedConfig].inputBarDataSource = self;- (NSArray<TUICustomActionSheetItem *> *)inputBarShouldAddNewItemsToMoreListOfModel:(TUIChatConversationModel *)model {    TUICustomActionSheetItem *item1 = [[TUICustomActionSheetItem alloc] initWithTitle:@"item1" leftMark:[UIImage imageNamed:@"item1.png"] withActionHandler:^(UIAlertAction * _Nonnull action) {        NSLog(@"item1 is clicked");    }];        TUICustomActionSheetItem *item2 = [[TUICustomActionSheetItem alloc] initWithTitle:@"item2" leftMark:[UIImage imageNamed:@"item2.png"] withActionHandler:^(UIAlertAction * _Nonnull action) {        NSLog(@"item2 is clicked");    }];        return @[item1, item2];}
```

Result:

| Adding item | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8f134e815e2711ef81cf525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/429088c05e2711ef998b525400f69702.png) |

### Add emoji group

API function: Add emoji groups to the emoji menu, effective across all chat interfaces. For use cases, please refer to the documentation [Adding Custom Emojis](https://www.tencentcloud.com/zh/document/product/1047/52396).

API prototype:

Swift

Objective-C

```
// TUIChatConfig_Minimalist.swift/*** Add sticker group.*/public func addStickerGroup(_ group: TUIFaceGroup) {    if let service = TIMCommonMediator.shared.getObject(for: TUIEmojiMeditorProtocol.self) {        service.appendFaceGroup(group)    } else {        print("Failed to get TUIEmojiMeditorProtocol service")    }}
```

```
// TUIChatConfig_Minimalist.h/** * Add sticker group. */- (void)addStickerGroup:(TUIFaceGroup *)group;
```

Sample code:

Swift

Objective-C

```
// When to call: After initializing the message list interface and before entering it.let group4350 = TUIFaceGroup()group4350.groupIndex = 1group4350.groupPath = bundlePath + "/4350/"group4350.faces = faces4350group4350.rowCount = 2group4350.itemCountPerRow = 5group4350.menuPath = bundlePath + "/4350/menu"TUIChatConfig_Minimalist.shared.addStickerGroup(group4350)
```

```
// When to call: After initializing the message list interface and before entering it.TUIFaceGroup *group4350 = [[TUIFaceGroup alloc] init];group4350.groupIndex = 1;group4350.groupPath = [bundlePath stringByAppendingPathComponent:@"4350/"]; group4350.faces = faces4350;group4350.rowCount = 2;group4350.itemCountPerRow = 5;group4350.menuPath = [bundlePath stringByAppendingPathComponent:@"4350/menu"];[[TUIChatConfig_Minimalist sharedConfig] addStickerGroup:group4350];
```


---
*Source: [https://trtc.io/document/65370](https://trtc.io/document/65370)*
