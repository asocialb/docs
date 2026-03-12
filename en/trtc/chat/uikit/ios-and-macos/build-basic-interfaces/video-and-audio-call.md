# Video and Audio Call

This article will guide you in building the audio and video call feature.

## Display Effect

The video call effect is shown in the following figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12b743962c7911efa01d5254005235d8.png)

The audio call effect is shown in the following figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12ad60622c7911ef918f52540005b090.png)

## Environment Requirements

- Xcode 10 or later
- iOS 9.0 or later

## Preconditions

Before building the interface, please ensure that you have completed the following 4 things:

1. Created an application in the console.
2. Created some user accounts in the console.
3. Integrated with `TUICallKit`.
4. Called the `login` API in `TUILogin` to log in to the component.

> **Note:**All components use this API to log in. You can log in once every time you start the application.Please make sure that the login is successful, and we recommend that you do the following in the callback of successful login.

If you haven't completed the above 4 steps, please refer to the corresponding steps in [Getting Started](https://trtc.io/document/60520) first, otherwise you may encounter obstacles when implementing the following features.

If you have already completed them, please continue reading below.

## Integration steps

1. log in to [Chat Console](https://console.trtc.io/) to activate the audio and video service. For detailed steps, refer to the document: [Activate Service](https://trtc.io/document/59832).
2. In the pop-up dialog to activate the TRTC `TRTC` service, click "Confirm". The system will create a TRTC application with the same SDKAppID as the current Chat application in the [TRTC console](https://trtc.io/login?s_url=https://console.trtc.io/), allowing reuse of accounts and authentication.
3. Integrate the `TUICallKit` component. In the podfile, add the following content:

```
// Integrate the TUICallKit componentpod 'TUICallKit_Swift'
```

After integrating the `TUICallKit` component, "Video Call" and "Voice Call" buttons will automatically appear on the chat interface and contact profile screen. When users click on these buttons, `TUICallKit` will display the call invitation UI and send a call invitation request to the other party.

When a user receives a call invitation online, `TUICallKit` automatically displays the call receiving UI, allowing the user to accept or reject the call.

When a user receives a call invitation offline, offline push capabilities must be utilized to wake up the app call.

Starting a call from the message page is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea5560fc2c7411efb0275254006c0558.png)

Starting a call from the contacts page is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea3c0b232c7411efa01d5254005235d8.png)

## Add Offline Push Notifications

For details, refer to the documentation: [Offline Push](https://trtc.io/document/54923). After configuration, when you click a received audio and video call notification pushed offline, `TUICallKit` will automatically open the audio/video call invitation interface.

## Add AI Noise Reduction

After integrating `TUIChat` and `TUICallkit` components, when you send a VMS in the chat interface, you can record VMS with AI noise reduction and automatic gain control. Below is a comparison of VMS recorded simultaneously with two phones:

> **Note:**This feature requires the purchase of the  Pro edition ãPro Plus edition or Enterprise edition. After the plan expires, VMS recording will switch to the system API for recording.Only supported in SDK 7.0 and later versions.

## More practices

You can locally [run the TUIKitDemo source code](https://trtc.io/document/45913) to explore more interface implementations.

## Contact Us

If you have any questions about this article, feel free to join the [Telegram Technical Group](https://t.me/+EPk6TMZEZMM5OGY1), where you will receive reliable technical support.


---
*Source: [https://trtc.io/document/61225](https://trtc.io/document/61225)*
