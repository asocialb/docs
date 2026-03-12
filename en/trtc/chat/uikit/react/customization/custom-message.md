# Custom Message

TUIKit provides default implementation for sending and displaying basic message types such as text, image, voice, video, and file. If these message types do not meet your needs, you can add custom message types.

## Basic Message Type

| Message Type | Display Effect |
| --- | --- |
| Text messages |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/09173f52621911f0ad0f5254005ef0f7.png) |
| Image messages |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3a62057e621911f0ad0f5254005ef0f7.png) |
| Video messages |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d3e482a621a11f097ec52540044a08e.png) |
| File messages |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/63df7501621a11f0b324525400e889b2.png) |

## Custom Notification

If the basic message type cannot meet your needs, you can use custom messages based on actual business needs.

| Custom Message Preset Style | Display Effect |
| --- | --- |
| Hypertext messages |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/36e096e5622b11f0bac1525400454e06.png) |
| Rating messages |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/40124a67622b11f0b30d5254007c27c5.png) |
| Order messages |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/349600bd623111f0bac1525400454e06.png) |

The following context uses sending a hypertext that can navigate to the browser as a custom message to help you quickly understand the implementation process.

### Thinking Requires Customized Data

For a message that can go to another website, a description text and a url link are required.

```
import { TUIChatService } from "@tencentcloud/chat-uikit-engine";const sendCustomMessageParams = {    payload: {      data: JSON.stringify({        Welcome to the Tencent Cloud family        url: 'https://cloud.tencent.com/document/product/269'      }),      description: "text_with_link",      extension: "text_with_link"    },};// simulation send a custom messageTUIChatService.sendCustomMessage(sendCustomMessageParams)    .catch(err => { /** */ });
```

Send custom messages. Reference [ChatEngine API Documentation](https://web.sdk.qcloud.com/im/doc/chat-engine/ITUIChatService.html#sendCustomMessage).

### 2. Creating Components That Parse Custom Data

Here create a CustomMessage component. When the type of message is custom message and the extended fields of the message equal the `text_with_link` defined above, we can custom render the content; if it is other types of messages, use default Message component to render.

```
import { TUIChatEngine } from '@tencentcloud/chat-uikit-engine';import { UIKitProvider,  Message } from '@tencentcloud/chat-uikit-react';function CustomMessage(props: React.ComponentProps<typeof Message>) {  if (props.message.type === TUIChatEngine.TYPES.MSG_CUSTOM) {    const { data, extension } = props.message.payload;    if (data && extension === 'text_with_link') {      const { text, url } = JSON.parse(data);      return (        <div style={{          backgroundColor: 'lightblue',          padding: '10px',          borderRadius: '10px',        }}        >          <div>{text}</div>          <a href={url} target="_blank" rel="noopener noreferrer">            Jump to          </a>        </div>      );    }  }  return <Message {...props} />;}function ChatApp() {  return (      <UIKitProvider language="auto" theme="light">        <div style={{ display: 'flex', height: '100vh' }}>          <ConversationList />          <MessageList Message={CustomMessage} />        </div>      </UIKitProvider>  );}export default ChatApp;
```


---
*Source: [https://trtc.io/document/72002](https://trtc.io/document/72002)*
