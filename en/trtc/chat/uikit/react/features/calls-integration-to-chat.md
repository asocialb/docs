# Calls integration to chat

TUICallKit is an audio and video call UI component launched by Tencent Cloud. By integrating this component, you can experience the audio and video call feature with just a few lines of code in your chat application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e21dfd61765d11ef8829525400fdb830.png)

- React version 18+ (17.x versions are not supported)
- TypeScript
- [Node.js](https://nodejs.org/en/) version 16+
- npm (use a version that matches the Node version in use)

## Step 1: Enable the Audio and Video Call Capability

Before using the audio and video services provided by Tencent Cloud, you need to go to the Console to enable the audio and video services for your application. For detailed steps, please refer to [Activate Service.](https://www.tencentcloud.com/document/product/647/59832)

## Step 2: Download the TUICallKit Component

Download the `TUICallKit` component via [npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-vue), version 3.3.6 and above:

```
npm i @tencentcloud/call-uikit-react
```

## Step 3: Import and Invoke the TUICallKit Component

- You only need to add two lines of code to experience the call feature. Import `TUICallKit` and invoke the `TUICallKit` component.
- In the `<ChatHeader />` component, enable Call, display the Icon, and set `enableCall` to `true`.

> **Note:**If you have not yet integrated TUIKit, please follow [Integrate TUIKit](https://www.tencentcloud.com/document/product/1047/50055?lang=en&pg=) documentation to first integrate TUIKit. The TUIKit version should be updated to v2.2.7 or above.The TUICallKit component allows you to add styles for controlling the position, width, and height of TUICallKit.

```
// Import TUICallKitimport { TUICallKit } from '@tencentcloud/call-uikit-react';
```

```
// If you are displaying on the PC end, please add styles to initialize the TUICallKit position. For H5 display, this is not requiredconst callStyle: React.CSSProperties = {  position: 'fixed',  top: '50%',  left: '50%',  zIndex: '999',  transform: 'translate(-50%, -50%)',};
```

```
// Please use the TUICallKit component within the UIKitProviderreturn (  <div style={{display: 'flex', height: '100vh'}}>    <UIKitProvider language={"en-US"}>      <TUICallKit style={callStyle} />       <div style={{maxWidth: '400px'}}>         <Profile />         <ConversationList />      </div>      <Chat>        <ChatHeader enableCall={true}/>         <MessageList />        <MessageInput />      </Chat>      <ChatSetting />    </UIKitProvider>  </div>);
```

## Step 4: Launch the project

```
 npm run start
```

## Step 5: Make your first call

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e218ec5b765d11ef82535254002693fd.png)

## FAQs

#### How to disable the audio/video call feature?

- To disable the audio/video call button, set the `nbableCall` attribute to `false` in the ` <ChatHeader /> ` component. If `enableCall` is not specified, the default is `false`.

```
return (  <div style={{display: 'flex', height: '100vh'}}>    <UIKitProvider language={"en-US"}>      <TUICallKit style={callStyle} />      <div style={{maxWidth: '400px'}}>         <Profile />         <ConversationList />      </div>      <Chat>        <ChatHeader enableCall={false}/>         <MessageList />        <MessageInput />      </Chat>      <ChatSetting />    </UIKitProvider>  </div>);
```

### How do I purchase a package?

Please refer to the purchase link to [purchase the official version](https://www.tencentcloud.com/document/product/1047/34577).

## Technical consultation

If you need anything or have feedback, you can contact: info_rtc@tencent.com. Alternatively, join the [Telegram technical group](https://t.me/tencent_imsdk) or the [WhatsApp group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik) for support from professional engineers to solve your problems.


---
*Source: [https://trtc.io/document/64468](https://trtc.io/document/64468)*
