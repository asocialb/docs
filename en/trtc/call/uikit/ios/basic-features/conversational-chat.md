# Conversational Chat

Chat provides multi-platform chat APIs, user interface components, and server-side APIs, enabling you to build a fully functional chat application in ten minutes. In the chat application, you can easily add audio and video call features with just up to three lines of code.

## Integration demonstration

After integrating Chat and TUICallKit, you can easily initiate audio and video calls on the chat messages page and user information page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/52b4086eb2ea11ef9d2952540055f650.png)

## Quick Integration

### Preparations

- Please ensure your application has [integrated Chat](https://trtc.io/document/60521?platform=ios%20and%20macos&product=chat&menulabel=uikit).

### Activate Service

1. Log in to the [chat console](https://console.trtc.io/) to activate audio and video services. For detailed steps, refer to the documentation [Activate Service](https://trtc.io/document/60220).
2. In the pop-up dialog box for activating the TRTC service, click "Confirm". The system will create a TRTC application with the same SDKAppID as the current chat application. The [TRTC console](https://trtc.io/login?s_url=https://console.trtc.io/) allows reuse of account and authentication.

### Integrate TUICallKit.

Add the following content to your Podfile:

```
// Integrate the TUICallKit componentpod 'TUICallKit'
```

After integrating the TUICallKit component, the chat interface and contact information interface will by default display "video call" and "voice call" buttons. When the user clicks the button, TUICallKit will automatically display the call invitation UI and send a call invitation request to the other party.


---
*Source: [https://trtc.io/document/66906](https://trtc.io/document/66906)*
