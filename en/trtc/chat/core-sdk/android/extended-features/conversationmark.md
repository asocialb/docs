# ConversationMark

### Plugin Feature

Starting from version 7.3, the conversation mark plugin `TUIConversationMarkPlugin` can be integrated. The conversation mark plugin is a UI closed-source library that depends on `TUIConversation`. After the plugin is integrated, you can mark and unmark conversations in `TUIConversation`.

### Android Integration

`TUIConversationMarkPlugin` is a closed-source plugin that needs to be integrated via gradle. Find the build.gradle of the app and add the mark plugin dependency in the dependencies.

Classic version

```
  dependencies {    ...    # Integrate the conversation feature.    api project(':tuiconversation')    ...    # Integrate the conversation mark plugin, which is supported starting from version 7.3.    api "com.tencent.imsdk:tuiconversationmark-plugin:7.3.4358"    ...}
```

### iOS Integration

`TUIConversationMarkPlugin`, like ordinary TUIKit components, can be quickly integrated via CocoaPods. Detailed integration steps can be found in [Integrating Basic Features](https://trtc.io/zh/document/60521).

For the conversation mark plugin, you only need to add one line to Podfile to complete the integration:

Classic version

```
# Uncomment the next line to define a global platform for your project# ...  # Integrate the conversation feature.  pod 'TUIConversation/UI_Classic'   ...  # Integrate the conversation mark plugin, which is supported starting from version 7.3.  pod 'TUIConversationMarkPlugin'  ...end
```

> **Note**`TUIConversationMarkPlugin` depends on `TUIConversation`. Integrating `TUIConversationMarkPlugin` alone will cause feature anomalies and the conversation mark interface cannot be displayed normally.`TUIConversationMarkPlugin` is supported starting from version 7.3. To use the conversation mark plugin, upgrade `TUIConversation` to version 7.3 or later.


---
*Source: [https://trtc.io/document/67618](https://trtc.io/document/67618)*
