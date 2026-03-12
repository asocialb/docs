# Poll

### Plugin Feature

Starting from version 7.1, the vote plugin `TUIPollPlugin` can be integrated. The vote plugin is a UI closed-source library that depends on `TUIChat`.

After the plugin is integrated, you can initiate a group vote, view vote statistics results, and participate in others' vote directly in `TUIChat`.

### Android Integration

`TUIPollPlugin` is a closed-source plugin that needs to be integrated via gradle. Find the build.gradle of the app and add the dependency of the vote plugin in dependencies.

Classic version

```
  dependencies {    ...  # Integrate the chat feature.  api project(':tuichat')  ...  # Integrate the vote plugin, which is supported starting from version 7.1.  api "com.tencent.imsdk:tuipoll-plugin:7.3.4358"  ...}
```

### iOS Integration

`TUIPollPlugin`, like ordinary TUIKit components, can be quickly integrated via CocoaPods. For the vote plugin, you only need to add one line to Podfile to complete the integration:

Classic version

```
# Uncomment the next line to define a global platform for your project# ...  # Integrate the chat feature.  pod 'TUIChat/UI_Classic'   ...  # Integrate the vote plugin, which is supported starting from version 7.1.  pod 'TUIPollPlugin'  ...end
```

> **Note:**`TUIPollPlugin` depends on `TUIChat`. Integrating `TUIPollPlugin` alone will cause feature anomalies and the vote interface cannot be displayed normally.`TUIPollPlugin` is supported starting from version 7.1. To use the vote plugin, upgrade `TUIChat` to version 7.1 or later.


---
*Source: [https://trtc.io/document/67611](https://trtc.io/document/67611)*
