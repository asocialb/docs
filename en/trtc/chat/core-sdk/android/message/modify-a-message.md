# Modify a Message

## Feature Description

This feature enables any participant in a conversation to modify a successfully sent message in the conversation. The message will be synced to all the participants in the conversation once modified successfully.

> **Noteï¼** This feature is supported only by the Enhanced edition on v6.2 or later.

## Effect

You can use this API to change the `cloudCustomData` of a message, implementing features such as message reply and message quote as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c82b38af215311efb2cb5254006568c0.png)

## API Description

### Modifying a Message

A conversation participant can call `modifyMessage` ([Java](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMMessageManager.html#a5464602189e6af536540e86e8bcbbe73) / [Swift](https://im.sdk.qcloud.com/doc/en/swift_V2TIMManager+Message.html#v2timmanager.modifymessage(msg:completion:)) / [Objective-C](https://im.sdk.qcloud.com/doc/en/categoryV2TIMManager_07Message_08.html#a7609c2dd8550e43b23d24069200d37cb) /Â [C++](https://im.sdk.qcloud.com/doc/en/classV2TIMMessageManager.html#ae4123dd87276906605d8d4be6a56b5ad)) to modify a sent message in the conversation.
The SDK allows any conversation participant to modify a message in the conversation. You can add more restrictions at the business layer, for example, only allowing the message sender to modify the message.

Currently, the following information of a message can be modified:

- `cloudCustomData` ([Java](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMMessage.html#a9335c9c326a2bfa8f4e6951cb9714e62) / [Swift](https://im.sdk.qcloud.com/doc/en/swift_V2TIMMessage.html#v2timmessage.cloudcustomdata) / [Objective-C](https://im.sdk.qcloud.com/doc/en/interfaceV2TIMMessage.html#a99a1c55f183244cc56588e9769dac4d0) /Â [C++](https://im.sdk.qcloud.com/doc/en/structV2TIMMessage.html#a3417bf1a2828a99c0db54edae7e78da4))
- `V2TIMTextElem` ([Java](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMTextElem.html) / [Swift](https://im.sdk.qcloud.com/doc/en/swift_V2TIMTextElem.html) / [Objective-C](https://im.sdk.qcloud.com/doc/en/interfaceV2TIMTextElem.html) /Â [C++](https://im.sdk.qcloud.com/doc/en/structV2TIMTextElem.html))
- `V2TIMCustomElem` ([Java](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMCustomElem.html) / [Swift](https://im.sdk.qcloud.com/doc/en/swift_V2TIMCustomElem.html) / [Objective-C](https://im.sdk.qcloud.com/doc/en/interfaceV2TIMCustomElem.html) /Â [C++](https://im.sdk.qcloud.com/doc/en/structV2TIMCustomElem.html))
- `V2TIMLocationElem` ([Java](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMLocationElem.html) / [Swift](https://im.sdk.qcloud.com/doc/en/swift_V2TIMLocationElem.html) /  [Objective-C](https://im.sdk.qcloud.com/doc/en/interfaceV2TIMLocationElem.html)/Â [C++](https://im.sdk.qcloud.com/doc/en/structV2TIMLocationElem.html))
- `V2TIMFaceElem` ([Java](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMFaceElem.html) / [Swift](https://im.sdk.qcloud.com/doc/en/swift_V2TIMFaceElem.html) / [Objective-C](https://im.sdk.qcloud.com/doc/en/interfaceV2TIMFaceElem.html) /Â [C++](https://im.sdk.qcloud.com/doc/en/structV2TIMFaceElem.html))

Sample code:

Java

Swift

Objective-C

C++

```
// The original message object in the conversation is `originMessage`.// Modify the `cloudCustomData` information of the message objectoriginMessage.setCloudCustomData("modify_cloud_custom_data".getBytes());// If the message is a text message, modify the text message contentif (V2TIMMessage.V2TIM_ELEM_TYPE_TEXT == originMessage.getElemType()) {  originMessage.getTextElem().setText("modify_text");}V2TIMManager.getMessageManager().modifyMessage(originMessage, new V2TIMCompleteCallback<V2TIMMessage>() {  @Override  public void onComplete(int code, String desc, V2TIMMessage message) {    // After the message is modified, `message` is the modified message object.  }});
```

```
// The original message object in the conversation is `originMessage`.var originMessage: V2TIMMessage!// Modify the `cloudCustomData` information of the message objectoriginMessage.cloudCustomData = "modify_cloud_custom_data".data(using: .utf8)// If the message is a text message, modify the text message contentif originMessage.elemType == .V2TIM_ELEM_TYPE_TEXT {    originMessage.textElem?.text = "modify_text"}// modifyMessageV2TIMManager.shared.modifyMessage(msg: originMessage) { code, desc, msg in    // After the message is modified, `msg` is the modified message object.}
```

```
// Original message object in the conversationV2TIMMessage *originMessage; // Modify the `cloudCustomData` information of the message objectoriginMessage.cloudCustomData = [@"modify_cloud_custom_data" dataUsingEncoding:NSUTF8StringEncoding];// If the message is a text message, modify the text message contentif (V2TIM_ELEM_TYPE_TEXT == originMessage.elemType) {    originMessage.textElem.text = @"modify_text";}[[V2TIMManager sharedInstance] modifyMessage:originMessage completion:^(int code, NSString *desc, V2TIMMessage *msg) {    // After the message is modified, `msg` is the modified message object.}];
```

```
template <class T>class CompleteCallback final : public V2TIMCompleteCallback<T> {public:    using InternalCompleteCallback =        std::function<void(int, const V2TIMString&, const T&)>;    CompleteCallback() = default;    ~CompleteCallback() override = default;    void SetCallback(InternalCompleteCallback complete_callback) { complete_callback_ = std::move(complete_callback); }    void OnComplete(int error_code, const V2TIMString& error_message, const T& value) override {        if (complete_callback_) {            complete_callback_(error_code, error_message, value);        }    }private:    InternalCompleteCallback complete_callback_;};// V2TIMMessage originMessage;std::string str = u8"modify_cloud_custom_data";// Modify the `cloudCustomData` information of the message objectoriginMessage.cloudCustomData = {reinterpret_cast<const uint8_t*>(str.data()), str.size()};if (originMessage.elemList.Size() == 1) {    V2TIMElem* elem = originMessage.elemList[0];    if (elem->elemType == V2TIMElemType::V2TIM_ELEM_TYPE_TEXT) {        // If the message is a text message, modify the text message content        auto textElem = static_cast<V2TIMTextElem*>(elem);        textElem->text = "modify_text";    }}auto callback = new CompleteCallback<V2TIMMessage>{};callback->SetCallback([=](int error_code, const V2TIMString& error_message, const V2TIMMessage& message) {    // After the message is modified, `message` is the modified message object.    delete callback;});V2TIMManager::GetInstance()->GetMessageManager()->ModifyMessage(originMessage, callback);
```

### Message Modified Notification

Conversation participants call `addAdvancedMsgListener` ([Java](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMMessageManager.html#aaccdec10b9fbee5e43eaf908e359c823) / [Swift](https://im.sdk.qcloud.com/doc/en/swift_V2TIMManager+Message.html#v2timmanager.addadvancedmsglistener(listener:)) /  [Objective-C](https://im.sdk.qcloud.com/doc/en/categoryV2TIMManager_07Message_08.html#acf794752cc6bfa786aea5cd7fabadfab) /Â [C++](https://im.sdk.qcloud.com/doc/en/classV2TIMMessageManager.html#a498688ee0f672f114e28d830761dfbf8)) to add the advanced message listener.

After a message in the conversation is modified, all the participants will receive the `onRecvMessageModified` callback ([Java](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMAdvancedMsgListener.html#ade079c0c996ee408abdc9cc83ab56e40) / [Swift](https://im.sdk.qcloud.com/doc/en/swift_V2TIMAdvancedMsgListener.html#v2timadvancedmsglistener.onrecvmessagemodified(msg:)) / [Objective-C](https://im.sdk.qcloud.com/doc/en/protocolV2TIMAdvancedMsgListener-p.html#a1fb56e509cecc32663ebd460c1de88cb) /Â [C++](https://im.sdk.qcloud.com/doc/en/classV2TIMAdvancedMsgListener.html#ab404888951cc78732a2f77d85d4b96e8)), which contains the modified message object.

Sample code:

Java

Swift

Objective-C

C++

```
V2TIMAdvancedMsgListener advancedMsgListener = new V2TIMAdvancedMsgListener() {  // Notification of the message content modification  @Override  public void onRecvMessageModified(V2TIMMessage msg) {      // `msg` is the modified message object.  }};// Add a message listenerV2TIMManager.getMessageManager().addAdvancedMsgListener(advancedMsgListener);
```

```
// Add a message listenerV2TIMManager.sharedInstance().addAdvancedMsgListener(self)/// Notification of the message content modificationfunc onRecvMessageModified(_ msg: V2TIMMessage) {       // `msg` is the modified message object. }
```

```
// Add a message listener[[V2TIMManager sharedInstance] addAdvancedMsgListener:self];/// Notification of the message content modification- (void)onRecvMessageModified:(V2TIMMessage *)msg {    // `msg` is the modified message object.}
```

```
class AdvancedMsgListener final : public V2TIMAdvancedMsgListener {public:    // Notification of the message content modification    void OnRecvNewMessage(const V2TIMMessage& message) override {        // `message` is the modified message object.    }    // Other members ...};// Note that `advancedMsgListener` should not be released before the IM SDK is uninitialized,// otherwise the message callback cannot be called.AdvancedMsgListener advancedMsgListener;V2TIMManager::GetInstance()->GetMessageManager()->AddAdvancedMsgListener(&advancedMsgListener);
```


---
*Source: [https://trtc.io/document/48006](https://trtc.io/document/48006)*
