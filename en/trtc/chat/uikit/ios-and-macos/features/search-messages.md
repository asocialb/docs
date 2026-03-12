# Search Messages

Local search is implemented in the TUISearch component of TUIKit. It allows users to quickly find the expected information from massive amounts of complex data, such as the chat history, contacts, and group chats. It can also be used as an operations tool to easily and efficiently navigate to extensive content.

> **Note:**The local search feature is only available on the Chat Pro edition ãPro Plus edition or Enterprise edition. To use it, [purchase the Pro edition ãPro Plus edition or Enterprise edition](https://www.tencentcloud.com/document/product/1047/34577). For more information, see [Pricing](https://www.tencentcloud.com/document/product/1047/34350).

## Feature Demonstration

The search API UI consists of three parts: the first part is for friend search, the second part is for group and group member search, and the third part is for message search, where messages are classified by conversation.
[Download and install the app](https://www.tencentcloud.com/document/product/1047/34279) to experience it now.

## Integration Guide

The following introduces how to integrate the TUISearch component.

### Purchasing the package

[Purchase the Pro edition ãPro Plus edition or Enterprise edition](https://www.tencentcloud.com/document/product/1047/34577).

### Integrating TUISearch

Add the following content to your Podfile:

```
// Integrate TUISearchpod 'TUISearch'
```

Run `pod instal`.

### Logging in to TUIKit

You need to call `TUILogin` of `TUICore` to log in to TUIKit. Initialization is implemented inside the login API by default, and no additional call to the initialization API is required.

Swift

Objective-C

```
TUILogin.login(SDKAppID, userID: userID, userSig: userSig) {    // Login succeeded    print("login succeeded")} fail: { code, desc in    // Login failed    print("login failed, \\(code): \\(desc)")}
```

```
[TUILogin login:SDKAPPID userID:userID userSig:userSig succ:^{   // Login succeeded} fail:^(int code, NSString *msg) {   // Login failed}];
```

### Starting the search UI

If you have integrated the TUIConversation and TUISearch components, no additional processing is required at this point and searchBar is displayed above the conversation list by default.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b033b04c135911efbf645254007bbd8c.png)

If you have integrated only TUISearch, you can directly initialize TUISearchBar and add it to your own view.
The search UI logic and UI are encapsulated inside TUISearchBar. After adding TUISearchBar, you can click it to trigger a search.

Sample code:

Swift

Objective-C

```
// initlet searchBar = TUISearchBar()// self.containerView is your own viewself.containerView.addSubview(searchBar)
```

```
// initTUISearchBar *searchBar = [[TUISearchBar alloc] init];// self.containerView is your own view[self.containerView addSubview:searchBar];
```

## FAQs

#### How do I search for custom messages?

You need to use the `createCustomMessage:desc:extension` API to create and send a custom message, and specify the text to search in the `desc` parameter.

- If you use the `createCustomMessage` API to create a custom message, a binary data stream is saved locally, and the custom message cannot be searched.
- If you configure the offline push feature and specify the `desc` parameter, the custom message will also be pushed offline, and the content specified in the `desc` parameter will be displayed in the notification bar.
- If you do not need the offline push feature, use the `disablePush` parameter in `V2TIMOfflinePushInfo` of the `sendMessage` API to disable it.
- If you do not want the searched text to be displayed as the pushed content, use the `desc` parameter in `V2TIMOfflinePushInfo` to specify the pushed content.

#### How do I search for rich media messages?

Rich media messages include file, image, audio, and video messages.

- For a file message, the filename is usually displayed on the UI. Therefore, you can set the `fileName` parameter as the searched content when creating a file message. If `fileName` is not set, the system gets the filename from `filePath` and saves it to both the local device and the server.
- For an image, audio, or video message, the thumbnail or duration is usually displayed on the UI. In this case, you can specify the message type for search but cannot specify keywords for search.


---
*Source: [https://trtc.io/document/50037](https://trtc.io/document/50037)*
