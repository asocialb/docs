# Chat

The following content will show you how to set chat interface self Definition options.

## Message list

### Set background color and image

API's function: Set the chat interface message list background color and background image, effective for all chat interfaces.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Customize the backgroud of message list interface. * This configuration takes effect in all message list interfaces. */public static void setBackground(Drawable background)
```

Sample code:

```
// When to call: Before initializing the message list interface.TUIChatConfigMinimalist.setBackground(new ColorDrawable(0xFFE1FFFF));TUIChatConfigMinimalist.setBackground(context.getDrawable(R.drawable.your_background_image));
```

Result:

| Set Background Color | Set Background Image | Default |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9ccdde928f4a11ef9ed652540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9ccfaa5d8f4a11efb3eb525400bdab9d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9cc927b68f4a11ef9ba5525400f69702.png) |

### Set user avatar size and corner radius

API Function: Sets the user avatar size and corner radius.

API prototype:

```
// TUIConfigMinimalist.java/** *  Customize the size of avatar. *  This configuration takes effect in message list. */public static void setMessageListAvatarSize(int size)/** *  Customize the corner radius of the avatar. *  This configuration takes effect in message list. */public static void setMessageListAvatarRadius(int radius)
```

Sample code:

```
// When to call: Before initializing the TUIKit interfaces.// Set sizeTUIConfigMinimalist.setMessageListAvatarSize(50);// Set cornerRadiusTUIConfigMinimalist.setMessageListAvatarRadius(10);
```

Result:

| Default circular avatar | Set rounded rectangle avatar | Set rectangular avatar |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0915cfee8f4f11ef9897525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9d01f12b8f4a11efa11a525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0903034c8f4f11ef9ba5525400f69702.png) |

### Enable group grid avatar

API Function: Set group avatar to display as nine-grid. Effective for conversation lists, and contact lists.

API prototype:

```
// TUIConfigMinimalist.java/** * Display the group avatar in the nine-square grid style. * The default value is true. * This configuration takes effect in all groups. */public static void setEnableGroupGridAvatar(boolean enableGroupGridAvatar)
```

Sample code:

```
// When to call: Before initializing the TUIKit interfaces.TUIConfigMinimalist.setEnableGroupGridAvatar(false);
```

Result:

| Disable group avatar as nine-grid | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9cdda3578f4a11ef9ba5525400f69702.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/091a9ae58f4f11ef9897525400d5f8ef.png) |

### Enable typing indicator

API function: Enable the "typing" indicator. Effective for all 1v1 chat message interfaces.

API prototype:

```
// TUIChatConfigMinimalist.java/** *  Enable the display "Alice is typing..." on one-to-one chat interface. *  The default value is true. *  This configuration takes effect in all one-to-one chat message list interfaces. */public static void setEnableTypingIndicator(boolean enableTypingIndicator)
```

Sample code:

```
// When to call: Before initializing the message list interface.TUIChatConfigMinimalist.setEnableTypingIndicator(false);
```

Result:

| Enable "Typing" | Disable "Typing" |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9ceba5f68f4a11ef9ed652540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0916d90f8f4f11efa22452540055f650.png) |

### Enable message read receipt

API function: Enable read receipt. Once enabled, read information can be viewed in message details. Effective for all messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** *  When sending a message, set this flag to require message read receipt. *  The default value is false. *  This configuration takes effect in all chat message list interfaces. */public static void setMessageReadReceiptNeeded(boolean messageReadReceiptNeeded)
```

Sample code:

```
// When to call: Before sending messages. TUIChatConfigMinimalist.setMessageReadReceiptNeeded(true);
```

Result:

| Enable read receipt | Disable read receipt |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9d14cda98f4a11efa22452540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9d0b31048f4a11efa22452540055f650.png) |

### Hide long-press message menu button

API's function: Hide specified buttons in the long-press message menu, effective for all chat messages.

API prototype:

```
// TUIChatConfigMinimalist.javapublic static final int REPLY = 1;public static final int QUOTE = 2;public static final int EMOJI_REACTION = 3;public static final int PIN = 4;public static final int RECALL = 5;public static final int TRANSLATE = 6;public static final int CONVERT = 7;public static final int FORWARD = 8;public static final int SELECT = 9;public static final int COPY = 10;public static final int DELETE = 11;public static final int INFO = 12;public static final int SPEAKER_MODE_SWITCH = 13;@IntDef({REPLY, QUOTE, EMOJI_REACTION, PIN, RECALL, TRANSLATE, CONVERT, FORWARD, SELECT, COPY, DELETE, INFO, SPEAKER_MODE_SWITCH})public @interface LongPressPopMenuItem {}/** * Hide the items in the pop-up menu when user presses the message. */public static void hideItemsWhenLongPressMessage(@LongPressPopMenuItem int... items)
```

Sample code:

```
// When to call: Before displaying the pop-up menu when user presses the message. TUIChatConfigMinimalist.hideItemsWhenLongPressMessage(TUIChatConfigMinimalist.FORWARD,                                                      TUIChatConfigMinimalist.INFO);
```

Result:

| Do not hide any buttons | Hide the Forward button |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/091e8bff8f4f11ef95ae525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/092b08e28f4f11ef9ba5525400f69702.png) |

### Enable floating window for call

API's function: Enable the audio and video call floating window. If enabled, you can float the audio and video call interface in a small window on the chat interface. Effective for all audio and video call interfaces.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Turn on audio and video call floating windows, * The default value is true. */public static void setEnableFloatWindowForCall(boolean enableFloatWindowForCall)
```

Sample code:

```
// When to call: Before entering the message list interface.TUIChatConfigMinimalist.setEnableFloatWindowForCall(false);
```

### Enable multi-device login for call

API's function: Enable multi-device log in for audio and video calls, effective for all audio and video calls.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Enable multi-terminal login function for audio and video calls * The default value is false. */public static void setEnableMultiDeviceForCall(boolean enableMultiDeviceForCall)
```

Sample code:

```
// When to call: Before entering the message list interface.TUIChatConfigMinimalist.setEnableMultiDeviceForCall(true);
```

### Set custom top view

API's function: Set a custom view at the top of the chat interface, effective for all chat message interfaces.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Add a custom view at the top of the chat interface. * This view will be displayed at the top of the message list and will not slide up. */public static void setCustomTopView(View customTopView)
```

Sample code:

```
// When to call: Before initializing the message list interface.// tipsView is your customized view.TUIChatConfigMinimalist.setCustomTopView(tipsView);
```

Result:

| Set custom view | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9ce991f28f4a11efac345254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/09237a748f4f11ef9ba5525400f69702.png) |

### Set not to update the unread count

API function: Set the upcoming message to not update the conversation unread count. Effective for all messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Set this parameter when the sender sends a message, and the receiver will not update the unread count after receiving the message. * The default value is false. */public static void setExcludedFromUnreadCount(boolean excludedFromUnreadCount)
```

Sample code:

```
// When to call: Before sending messages.TUIChatConfigMinimalist.setExcludedFromUnreadCount(true);
```

### Set not to update the conversation lastMsg

API function: Set the upcoming message to not update the conversation lastMsg. Effective for all messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Set this parameter when the sender sends a message, and the receiver will not update the last message of the conversation after receiving the message. * The default value is false. */public static void setExcludedFromLastMessage(boolean excludedFromLastMessage)
```

Sample code:

```
// When to call: Before sending messages.TUIChatConfigMinimalist.setExcludedFromLastMessage(true);
```

### Set message recall interval

API function: Set message recall time interval, effective for all messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Time interval within which a message can be recalled after being sent. * The default value is 120 seconds. * If you want to adjust this configuration, please modify the setting on Chat Console synchronously: https://trtc.io/document/34419?platform=web&product=chat&menulabel=uikit#message-recall-settings */public static void setTimeIntervalForAllowedMessageRecall(int timeIntervalForAllowedMessageRecall)
```

Sample code:

```
// When to call: Before sending messages.TUIChatConfigMinimalist.setTimeIntervalForAllowedMessageRecall(90);
```

### Set maximum recording duration for voice and video messages

API function: Set the maximum recording duration for voice and video messages, effective for all voice and video messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Maximum audio recording duration, no more than 60s. * The default value is 60 seconds. */public static void setMaxAudioRecordDuration(int maxAudioRecordDuration)/** * Maximum video recording duration, no more than 15s. * The default value is 15 seconds. */public static void setMaxVideoRecordDuration(int maxVideoRecordDuration)
```

Sample code:

```
// When to call: Before recording audio or video messages.TUIChatConfigMinimalist.setMaxAudioRecordDuration(10);TUIChatConfigMinimalist.setMaxVideoRecordDuration(10);
```

### Enable custom ringtones

API function: Set the ringtone on Android devices to a built-in custom ringtone upon receiving a message, effective for all messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Enable custom ringtone. * This config takes effect only for Android devices. */public static void setEnableAndroidCustomRing(boolean enableAndroidCustomRing)
```

Sample code:

```
// When to call: Before sending messages.TUIChatConfigMinimalist.setEnableAndroidCustomRing(true);
```

### Set to play voice messages using loudspeakers by default

API's function: Set the default playback for voice message to use the speaker instead of the earpiece. Effective for all voice messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** * Call this method to use speakers instead of handsets by default when playing voice messages. */public static void setPlayingSoundMessageViaSpeakerByDefault(boolean playingSoundMessageViaSpeakerByDefault)
```

Sample code:

```
// When to call: Before initializing the Message interface.TUIChatConfigMinimalist.setPlayingSoundMessageViaSpeakerByDefault(true);
```

### Register custom message

API's function: Register custom Definition messages. Please refer to the documentation for usage scenarios [Add custom messages](https://www.tencentcloud.com/document/product/1047/50044).

API prototype:

```
// TUIChatConfigMinimalist.java/** * Register custom message. * - Parameters: *   - businessID: Customized messageâs businessID, which is unique. *   - messageBeanClass: Customized message's MessagBean class. *   - messageViewHolderClass: Customized message's MessagViewHolder class. *   - isUseEmptyViewGroup: If true, the user avatar and message bubble will not be displayed. */public static void registerCustomMessage(String businessID, Class<? extends TUIMessageBean> messageBeanClass,    Class<? extends RecyclerView.ViewHolder> messageViewHolderClass, boolean isUseEmptyViewGroup)
```

Sample code:

```
// When to call: Before initializing the Message List interface.TUIChatConfigMinimalist.registerCustomMessage(CUSTOM_LINK_MESSAGE_BUSINESS_ID,                    						  CustomLinkMessageBean.class,                    						  CustomLinkMessageHolder.class,                                              false);
```

### Customize events when click and long press the user avatar

API's function: Event callback for user clicks and long presses on the user avatar in the message list.

API prototype:

```
// TUIChatConfigMinimalist.javapublic interface ChatEventListener {    /**    * Tells the listener a user's avatar in the chat list is clicked.    * Returning true indicates this event has been intercepted, and Chat will not process it further.    * Returning false indicates this event is not intercepted, and Chat will continue to process it.    */    default boolean onUserIconClicked(View view, TUIMessageBean messageBean) {        return false;    }        /**    * Tells the listener a user's avatar in the chat list is long pressed.    * Returning true indicates that this event has been intercepted, and Chat will not process it further.    * Returning false indicates that this event is not intercepted, and Chat will continue to process it.    */    default boolean onUserIconLongClicked(View view, TUIMessageBean messageBean) {        return false;    }}
```

Sample code:

```
TUIChatConfigMinimalist.setChatEventListener(new ChatEventListener() {    @Override    public boolean onUserIconClicked(View view, TUIMessageBean messageBean) {        // Customize your own action when user avatar is clicked.        ToastUtil.toastShortMessage("onUserIconClicked");        return true;    }        @Override    public boolean onUserIconLongClicked(View view, TUIMessageBean messageBean) {        // Customize your own action when user avatar is long pressed.        ToastUtil.toastShortMessage("onUserIconLongClicked");        return true;    }}
```

### Customize events when click and long press the message

API's function: Event callback for user clicks and long presses on messages in the message list.

API prototype:

```
// TUIChatConfigMinimalist.javapublic interface ChatEventListener {     /**     * Tells the listener a message in the chat list is clicked.     * Returning true indicates that this event has been intercepted, and Chat will not process it further.     * Returning false indicates that this event is not intercepted, and Chat will continue to process it.     */    default boolean onMessageClicked(View view, TUIMessageBean messageBean) {        return false;    }    /**     * Tells the listener a message in the chat list is long pressed.     * Returning true indicates that this event has been intercepted, and Chat will not process it further.     * Returning false indicates that this event is not intercepted, and Chat will continue to process it.     */    default boolean onMessageLongClicked(View view, TUIMessageBean messageBean) {        return false;    }}
```

Sample code:

```
TUIChatConfigMinimalist.setChatEventListener(new ChatEventListener() {    @Override    public boolean onMessageClicked(View view, TUIMessageBean messageBean) {        // Customize your own action when message is clicked.        ToastUtil.toastShortMessage("onMessageClicked");        return true;    }        @Override    public boolean onMessageLongClicked(View view, TUIMessageBean messageBean) {        // Customize your own action when message is long pressed.        ToastUtil.toastShortMessage("onMessageLongClicked");        return true;    }}
```

## Message Style

### Set the style of text messages

API's function: Set the text color and font for sent and received text messages. Effective for all text messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** * The color of send text message. */public static void setSendTextMessageColor(int color)/** * The font size of send text message. */public static void setSendTextMessageFontSize(int size)/* * The color of receive text message. */public static void setReceiveTextMessageColor(int color)/** * The font size of receive text message. */public static void setReceiveTextMessageFontSize(int size)
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfigMinimalist.setSendTextMessageColor(0xFF00BFFF);TUIChatConfigMinimalist.setSendTextMessageFontSize(20);TUIChatConfigMinimalist.setReceiveTextMessageColor(0xFF2E8B57);TUIChatConfigMinimalist.setReceiveTextMessageFontSize(23);
```

Result:

| Set text message color | Set text message font | Default |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/09433e598f4f11ef9ed652540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0938612f8f4f11ef9ed652540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0961bc928f4f11efb3eb525400bdab9d.png) |

### Set the style of system messages

API's function: Set the font, color, and background color of system notification messages. Effective for all system notification messages.

API prototype:

```
// TUIChatConfigMinimalist.java/** * The text color of system message. */public static void setSystemMessageTextColor(int color)/** * The font size of system message. */public static void setSystemMessageFontSize(int size)/** * The background of system message. */public static void setSystemMessageBackground(Drawable drawable)
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfigMinimalist.setSystemMessageTextColor(0xFFFF8C00);TUIChatConfigMinimalist.setSystemMessageFontSize(23);TUIChatConfigMinimalist.setSystemMessageBackground(new ColorDrawable(0xFFF0FFF0));
```

Result:

| Set the font, color, and background color of system notification messages | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9d0ca83a8f4a11ef95ae525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/093b95678f4f11efb3eb525400bdab9d.png) |

## Message bubble

### Enable message bubble display

API's function: Enable message bubble display, effective for all chat interfaces.

API prototype:

```
// TUIConfigMinimalist.java/** * Enable the message display in the bubble style. * The default value is true. */public static void setEnableMessageBubbleStyle(boolean enable)
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.TUIConfigMinimalist.setEnableMessageBubbleStyle(false);
```

Result:

| Do not display message bubbles | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9d14d7e88f4a11ef95ae525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/095bd1068f4f11ef9ba5525400f69702.png) |

### Set bubble background image

API's function: Set bubble background images, effective for all chat interfaces.

API prototype:

```
// TUIConfigMinimalist.java/** * Set the background of the last sent message bubble in consecutive messages. */public static void setSendLastBubbleBackground(Drawable drawable)/** * Set the background of the non-last sent message bubble in consecutive message. */public static void setSendBubbleBackground(Drawable drawable)/** * Set the background of the last received message bubble in consecutive message. */public static void setReceiveLastBubbleBackground(Drawable drawable)/** * Set the background of the non-last received message bubble in consecutive message. */public static void setReceiveBubbleBackground(Drawable drawable)/** * Set the light color when the message bubble needs to flicker. */public static void setBubbleHighlightLightColor(int color)/** * Set the dark color when the message bubble needs to flicker. */public static void setBubbleHighlightDarkColor(int color)
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.TUIConfigMinimalist.setSendLastBubbleBackground(context.getDrawable(R.drawable.SenderTextNodeBkg))TUIConfigMinimalist.setSendBubbleBackground(context.getDrawable(R.drawable.SenderTextNodeBkg))TUIConfigMinimalist.setReceiveLastBubbleBackground(context.getDrawable(R.drawable.ReceiverTextNodeBkg));TUIConfigMinimalist.setReceiveBubbleBackground(context.getDrawable(R.drawable.ReceiverTextNodeBkg));
```

Result:

| Set bubble background image | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0963861b8f4f11efa11a525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/094483688f4f11efac345254002693fd.png) |

## Input bar

### Display Input bar

API's function: Display the input box in the chat interface, effective for all chat interfaces.

API prototype:

```
// TUIChatConfigMinimalist.java/** *  Show the input bar in the message list interface. *  The default value is true. */public static void setShowInputBar(boolean showInputBar)
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfigMinimalist.setShowInputBar(false);
```

Result:

| Hide input bar | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0928e02e8f4f11efac345254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0940f2f88f4f11ef9ba5525400f69702.png) |

### Hide options in more menu (global)

API's function: Hide buttons in the more menu, effective for all chat interfaces.

API prototype:

```
// TUIChatConfigMinimalist.java/** *  Hide items in more menu. */public static void hideItemsInMoreMenu(@InputMoreMenuItem int... items)
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfigMinimalist.hideItemsInMoreMenu(TUIChatConfigMinimalist.CUSTOM,                                            TUIChatConfigMinimalist.RECORD_VIDEO,                                            TUIChatConfigMinimalist.FILE);
```

Result:

| Hide part of the options | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0961ba098f4f11ef9ba5525400f69702.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/09621c2b8f4f11ef9897525400d5f8ef.png) |

### Hide options in the more menu (local)

API's function: Hide buttons in the more menu, effective for specified chat interfaces.

API prototype:

```
// TUIChatConfigMinimalist.javapublic static final int CUSTOM = 1;public static final int RECORD_VIDEO = 2;public static final int TAKE_PHOTO = 3;public static final int ALBUM = 4;public static final int FILE = 5;@IntDef({CUSTOM, RECORD_VIDEO, TAKE_PHOTO, ALBUM, FILE})public @interface InputMoreMenuItem {}public interface ChatInputMoreDataSource {    default @InputMoreMenuItem List<Integer> inputBarShouldHideItemsInMoreMenuOfInfo(ChatInfo chatInfo) {        return new ArrayList<>();    }}
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfigMinimalist.setChatInputMoreDataSource(new TUIChatConfigMinimalist.ChatInputMoreDataSource() {    @Override    public List<Integer> inputBarShouldHideItemsInMoreMenuOfInfo(ChatInfo chatInfo) {        return Arrays.asList(TUIChatConfigMinimalist.CUSTOM, TUIChatConfigMinimalist.RECORD_VIDEO,                             TUIChatConfigMinimalist.TAKE_PHOTO, TUIChatConfigMinimalist.ALBUM,                             TUIChatConfigMinimalist.FILE);        }});
```

### Add options to the more menu (local)

API's function: Add options to the more menu, effective for specified chat interfaces.

API prototype:

```
// TUIChatConfigMinimalist.javapublic interface ChatInputMoreDataSource {    default List<InputMoreItem> inputBarShouldAddNewItemToMoreMenuOfInfo(ChatInfo chatInfo) {        return new ArrayList<>();    }}
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.TUIChatConfigMinimalist.setChatInputMoreDataSource(new TUIChatConfigMinimalist.ChatInputMoreDataSource() {    @Override    public List<InputMoreItem> inputBarShouldAddNewItemToMoreMenuOfInfo(ChatInfo chatInfo) {        InputMoreItem inputMoreItem = new InputMoreItem() {            @Override            public void onAction(String chatInfoId, int chatType) {              ToastUtil.toastShortMessage("on click");            }        };        inputMoreItem.setName("item1");        inputMoreItem.setPriority(10000);        inputMoreItem.setIconResId(R.drawable.ic_launcher);                InputMoreItem inputMoreItem2 = new InputMoreItem() {            @Override            public void onAction(String chatInfoId, int chatType) {              ToastUtil.toastShortMessage("on click");            }        };        inputMoreItem2.setName("item1");        inputMoreItem2.setPriority(8000);        inputMoreItem2.setIconResId(R.drawable.ic_launcher);                return Arrays.asList(inputMoreItem, inputMoreItem2);    }});
```

Result:

| Adding item | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/094341de8f4f11ef9ed652540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9cf1c83d8f4a11ef9ed652540075b605.png) |

### Add emoji group

API function: Add emoji groups to the emoji menu, effective across all chat interfaces. For use cases, please refer to the documentation [Adding Custom Emojis](https://www.tencentcloud.com/zh/document/product/1047/52396).

API prototype:

```
// TUIChatConfigMinimalist.java/** * Add sticker group. */public static void addStickerGroup(int groupID, FaceGroup<? extends ChatFace> faceGroup)
```

Sample code:

```
// When to call: After initializing the message list interface and before entering it.FaceGroup faceGroup1 = new FaceGroup();faceGroup1.setPageColumnCount(5);faceGroup1.setPageRowCount(2);faceGroup1.setGroupID(1);faceGroup1.setFaceGroupIconUrl("file:///android_asset/4350/yz00@2x.gif");faceGroup1.setGroupName("4350");for (int i = 0; i <= 17; i++) {      CustomFace customFace = new CustomFace();      String index = "" + i;      if (i < 10) {          index = "0" + i;      }      customFace.setAssetPath("4350/yz" + index + "@2x.gif");      String faceKey = "yz" + index;      customFace.setFaceKey(faceKey);      customFace.setWidth(170);      customFace.setHeight(170);      faceGroup1.addFace(faceKey, customFace);}TUIChatConfigMinimalist.addStickerGroup(1, faceGroup1);
```


---
*Source: [https://trtc.io/document/65365](https://trtc.io/document/65365)*
