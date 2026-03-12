# Read Receipt

## Overview

The React MessageList component supports read receipt capability, determining whether a single message has been read by the recipient in one-on-one chats. In group chats, it independently determines whether an individual message has been read by a group member.

## Effect Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a64f6ccc61f511f0ad0f5254005ef0f7.png)

## Usage

The React UIKit provides the MessageList component. Setting the `enableReadReceipt` property to `true` in the MessageList component enables read receipt (if left empty, the default value is false).

```
import {  Chat,  ChatHeader,  ConversationList,  MessageInput,  MessageList,} from '@tencentcloud/chat-uikit-react';function App() {  return (    <UIKitProvider>      <div style={{ display: 'flex', height: '100vh' }}>        <ConversationList style={{ minWidth: '30%' }} />        <Chat>          <ChatHeader />          // Enable read receipt          <MessageList enableReadReceipt={true} />          <MessageInput />        </Chat>      </div>    </UIKitProvider>  );}export default App;
```


---
*Source: [https://trtc.io/document/72001](https://trtc.io/document/72001)*
