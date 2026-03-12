# Conversational Chat

Chat provides multi-platform chat APIs, user interface components, and server-side APIs, enabling you to build a fully functional chat application in ten minutes. In the chat application, you can easily add audio and video call features with just up to three lines of code.

## Integration demonstration

After integrating Chat and TUICallKit, you can easily initiate audio and video calls on the chat messages page and user information page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1eed16a2b2ec11ef8c01525400fdb830.png)

## Quick Integration

### Preparations

- Please ensure your application has [integrated Chat](https://trtc.io/document/58585?platform=flutter&product=chat&menulabel=uikit).

### Activate Service

1. Log in to the [chat console](https://console.trtc.io/) to activate audio and video services. For detailed steps, refer to the documentation [Activate Service](https://trtc.io/document/60220).
2. In the pop-up dialog box for activating the TRTC service, click "Confirm". The system will create a TRTC application with the same SDKAppID as the current chat application. The [TRTC console](https://trtc.io/login?s_url=https://console.trtc.io/) allows reuse of account and authentication.

### Integrate TUICallKit.

1. In the console, navigate to your Flutter project's directory and run the following command to install the [tencent_calls_uikit](https://pub.dev/packages/tencent_calls_uikit) plugin:

```
flutter pub add tencent_calls_uikit
```

2. In the Flutter application framework, add TUICallKit.navigatorObserver to navigatorObservers. For example, using the MaterialApp framework, the code is as follows:

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart'; ......class XXX extends StatelessWidget {  const XXX({super.key}); @override  Widget build(BuildContext context) {    return MaterialApp(      navigatorObservers: [TUICallKit.navigatorObserver],      ......    );  }}
```

After integrating the TUICallKit component, the chat interface and contact information interface will by default display "video call" and "voice call" buttons. When the user clicks the button, TUICallKit will automatically display the call invitation UI and send a call invitation request to the other party.


---
*Source: [https://trtc.io/document/66905](https://trtc.io/document/66905)*
