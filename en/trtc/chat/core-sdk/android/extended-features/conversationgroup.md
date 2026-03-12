# ConversationGroup

### Plugin Feature

Starting from version 7.3, the conversation group plugin `TUIConversationGroupPlugin` can be integrated. The conversation group plugin is a UI closed-source library that depends on `TUIConversation`. After the plugin is integrated, you can create groups, delete groups, edit groups, hide groups, and reorder groups.

### Android Integration

`TUIConversationGroupPlugin` is a closed-source plugin that needs to be integrated via gradle. Find the build.gradle of the app and add the dependency of the group plugin in dependencies.

Classic version

```
  dependencies {    ...    # Integrate the conversation feature.    api project(':tuiconversation')    ...    # Integrate the conversation group plugin, which is supported starting from version 7.3.    api "com.tencent.imsdk:tuiconversationgroup-plugin:7.3.4358"    ...}
```

### iOS Integration

`TUIConversationGroupPlugin`, like ordinary TUIKit components, can be quickly integrated via CocoaPods. Detailed integration steps can be found in [Integrating Basic Features](https://trtc.io/zh/document/60521).

For the conversation group plugin, you only need to add one line to Podfile to complete the integration:

Classic version

```
# Uncomment the next line to define a global platform for your project# ...  # Integrate the conversation feature.  pod 'TUIConversation/UI_Classic'   ...  # Integrate the conversation group plugin, which is supported starting from version 7.3.  pod 'TUIConversationGroupPlugin'  ...end
```

> **Note**`TUIConversationGroupPlugin` depends on `TUIConversation`. Integrating `TUIConversationGroupPlugin` alone will cause feature anomalies and the conversation group interface cannot be displayed normally.`TUIConversationGroupPlugin` is supported starting from version 7.3. To use the conversation group plugin, upgrade `TUIConversation` to version 7.3 or later.


---
*Source: [https://trtc.io/document/67621](https://trtc.io/document/67621)*
