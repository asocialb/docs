# GroupNote

### Plugin Feature

Starting from version 7.1, the group solitaire plugin `TUIGroupNotePlugin` can be integrated. It is a UI closed-source library that depends on `TUIChat`. Once the plugin is integrated, you can directly initiate group solitaire activities in `TUIChat`.

### Android Integration

`TUIGroupNotePlugin` is a closed-source plugin that needs to be integrated via gradle. Find the build.gradle of the app and add the dependency of the vote plugin in dependencies.

Classic version

```
  dependencies {    ...  # Integrate the chat feature.  api project(':tuichat')  ...  # Integrate solitaire plugin, which is supported starting from version 7.1.  api "com.tencent.imsdk:tuigroupnote-plugin:7.3.4358"  ...}
```

### iOS Integration

`TUIGroupNotePlugin`, like ordinary TUIKit components, can be quickly integrated via CocoaPods. Detailed integration steps can be found in [Integrating Basic Features](https://trtc.io/zh/document/60521).

For the solitaire plugin, you only need to add one line to Podfile to complete the integration:

Classic version

```
# Uncomment the next line to define a global platform for your project# ...  # Integrate the chat feature.  pod 'TUIChat/UI_Classic'   ...  # Integrate solitaire plugin, which is supported starting from version 7.1.  pod 'TUIGroupNotePlugin'  ...end
```

> **Note**`TUIGroupNotePlugin` depends on `TUIChat`. Integrating `TUIGroupNotePlugin` alone will cause feature anomalies and the solitaire interface cannot be displayed normally.`TUIGroupNotePlugin` is supported starting from version 7.1. To use the solitaire plugin, upgrade `TUIChat` to version 7.1 or later.


---
*Source: [https://trtc.io/document/67615](https://trtc.io/document/67615)*
