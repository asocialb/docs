# MessageList

## Component Overview

MessageList is a powerful chat message list component that provides complete message display, interaction, and custom functions. It supports core chat features such as message aggregation, read receipts, message operations, and scroll control, while also offering various custom options to satisfy different business needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c3b8073617111f097ec52540044a08e.png)

## Props Properties

| Field | Type | Default Value | Description |
| --- | --- | --- | --- |
| [alignment](#bb86a868-3c04-4a23-a55d-41434f0eb6b0) | 'left' \| 'right' \| 'two-sided' | 'two-sided' | Message alignment mode.Left: Align all messages left.Right: Align all messages right.two-sided: Send messages align right, receive messages align left. |
| [enableReadReceipt](#74454dca-9a23-4c52-8182-089dc4287c05) | boolean | false | Whether to enable the read receipt feature. |
| [messageActionList](#8467b7d4-9519-4bf2-b932-726db7b78ff6) | IMessageAction[] | undefined | Custom message actions list, such as copy, revoke, delete. |
| [messageAggregationTime](#aea3b710-1bc0-4c49-bc63-e5328a5b2631) | number | 300 | Message aggregation interval (seconds). Consecutive messages from the same sender within this period will be aggregated and displayed. |
| [filter](#15a53ab6-197e-48af-aab6-c08231344b93) | (message: IMessageModel) => boolean | undefined | Message filtering function used to control which messages to display. |
| [className](#425502cf-5987-415f-85cd-807c82cfec6d) | string | undefined | Custom CSS class name. |
| [style](https://www.tencentcloud.com/document/product/1047/72084#cda58725-6b80-455d-84a2-e69a7b758f09) | React.CSSProperties | undefined | Custom inline style. |
| [Message](#5a133d44-be95-424a-926e-8214994872dc) | React.ComponentType | Message | Custom message component. |
| [MessageTimeDivider](#d5ff2021-e852-4210-9040-0f882c5d6d4a) | React.ComponentType | MessageTimeDivider | Custom time dividing line component. |

## Property Explanation

### alignment

Parameter type: `'left' | 'right' | 'two-sided'`

alignment is used to set the message alignment mode, supporting `left`, `right`, and `two-sided` three modes. The default value is `'two-sided'`.

- `two-sided`: Messages from others align left, your messages align right.
- `left`: All messages align left.
- `right`: All messages align right.

### enableReadReceipt

Parameter type: `boolean`

enableReadReceipt is used to set whether the message read receipt feature is enabled. Default value: `false`.

### messageActionList

Parameter type: `IMessageAction[]`

messageActionList are used to set the operation list of messages, such as copy, recall, delete. Default value is the complete message operation list `['copy', 'recall', 'quote', 'forward', 'delete']`.

```
interface IMessageAction {  key: 'copy' | 'recall' | 'quote' | 'forward' | 'delete' | string;  label?: string;  icon?: React.ReactNode;  onClick?: (message: IMessageModel) => void;  visible?: ((message: IMessageModel) => boolean) | boolean;  component?: React.ComponentType<{ message: IMessageModel }>;  style?: React.CSSProperties;}
```

`useMessageAction` can obtain the complete message operation list, then customize as needed.

#### Example1: Change Message Operation List Order

Assume the message action list is displayed in the order of `forward`, `copy`, `recall`, `quote`, `delete`.

```
import { Chat, MessageList, useMessageActions } from '@tencentcloud/chat-uikit-react';const App = () => {  const actions = useMessageActions(['forward', 'copy', 'recall', 'quote', 'delete']);  return (    <Chat>      <MessageList messageActionList={actions} />    </Chat>  );}
```

#### Example 2: Only Show Some Message Actions

Suppose only show `forward`, `copy`, and `recall` operations.

```
import { Chat, MessageList, useMessageActions } from '@tencentcloud/chat-uikit-react';const App = () => {  const actions = useMessageActions(['forward', 'copy', 'recall']);  return (    <Chat>      <MessageList messageActionList={actions} />    </Chat>  );}
```

#### Example 3: Modifying Existing Message Actions

Here is an example of a custom recall operation:

1. Change the tag to 'Recall â ï¸'
2. Change the color to orange
3. Only text messages can be withdrawn
4. key should be consistent with the original operation, use `recall`

```
import TUIChatEngine from '@tencentcloud/chat-uikit-engine';import { Chat, MessageList, useMessageActions } from '@tencentcloud/chat-uikit-react';const ChatApp = () => {  const actions = useMessageActions(['copy', {    key: 'recall',    label: 'Recall â ï¸',    style: {      color: 'orange'    },    visible: (message) => message.type === TUIChatEngine.TYPES.MSG_TEXT,  }, 'quote', 'forward', 'delete']);  return (    <Chat>      <MessageList messageActionList={actions} />    </Chat>  );}
```

The following figure shows the effect.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c235d22617111f0bac1525400454e06.png)

#### Example 4: Adding New Custom Message Actions

If custom message actions are needed, for example, only messages sent by others can be tagged as 'like' and inserted after the 'recall' operation.

```
import { useMessageAction } from '@tencentcloud/chat-uikit-react';import { yourApi } from '@/api/yourApi';const customActions = {  key: 'like',  label: 'Like',  icon: <span>ð</span>,  style: {    color: '#E53888',  },  visible: (message) => message.flow === 'in',  onClick: (message) => {    yourApi.likeMessage(message.ID);  }}function ChatApp() {  const actions = useMessageAction(['forward', 'copy', 'recall', customActions, 'quote', 'delete']);  return <MessageList messageActionList={actions} />;}
```

The following figure shows the effect.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c2f4eb5617111f092fe525400bf7822.png)

### messageAggregationTime

Parameter type: `number`

messageAggregationTime is used to set the message aggregation interval, aggregating consecutive messages from the same sender for display. Default value: `300` (seconds).

### filter

Parameter type: `(message: IMessageModel) => boolean`

filter is used to set the message filtering function to control which messages to display. Default value: `undefined`.

#### Example: Filtering Error Messages Sent by Robots

```
import { MessageList } from '@/components/MessageList';import TUIChatEngine from '@tencentcloud/chat-uikit-engine';const messageFilter = (message) => {  // Filter out text messages where sender nickname contains '_robot' and content includes 'operation-failed'  if (    message.nick?.includes('_robot')     && message.type === TUIChatEngine.TYPES.MSG_TEXT    && message.payload?.text?.includes('operation-failed')  ) {    return false;  }  return true;};function ChatApp() {  return <MessageList filter={messageFilter} />;}
```

### className

Parameter type: `string`

className is used to set the root container's custom CSS class name, default value `undefined`.

### style

Parameter type: `React.CSSProperties`

style is used to set the root container's custom inline style, default value `undefined`.

### Message

Parameter type: `React.ComponentType`

Message is used to set the custom message component, replace the default message rendering component, default value built-in `Message` component.

#### Example: Custom CUSTOM Message Click Redirection Message Component

```
import TUIChatEngine from '@tencentcloud/chat-uikit-engine';import { Chat, MessageList, Message } from '@tencentcloud/chat-uikit-react';function CustomMessage(props) {  const { message } = props;  if (message.type === TUIChatEngine.TYPES.MSG_CUSTOM) {    const { businessID, ...restData } = JSON.parse(message.payload.data);    if (businessID === 'text_link') {      return (        <div>          <div>{restData.text}</div>          <a href={restData.link}>            redirect to public website address {restData.link}          </a>        </div>      );    }  } else {    // Use the default message component for other message types    return <Message {...props} />;  }}function ChatApp() {  return (    <Chat>      <MessageList Message={CustomMessage} />    </Chat>  );}
```

### MessageTimeDivider

Parameter type: `React.ComponentType`

MessageTimeDivider is used to set a custom time dividing line component, default value is the built-in `MessageTimeDivider` component.

#### Example: Time Dividing Line for Working Hour

```
import { Chat, MessageList, MessageTimeDivider } from '@tencentcloud/chat-uikit-react';const BusinessTimeDivider = (props: React.ComponentProps<typeof MessageTimeDivider>) => {  const { prevMessage, currentMessage } = props;  if (!prevMessage || !currentMessage) return null;    // For each message to be rendered, get the time of the current message and the previous message, convert them to date objects, and determine whether they span a day or exceed a 4-hour interval  const currentTime = new Date(currentMessage.time * 1000);  const prevTime = new Date(prevMessage.time * 1000);    // Display only when crossing days or exceeding 4-hour interval  const shouldShow = currentTime.toDateString() !== prevTime.toDateString() ||                    (currentTime.getTime() - prevTime.getTime()) > 4 * 60 * 60 * 1000;    if (!shouldShow) return null;    // Check working hours (9:00-18:00, Monday through Friday)  const isWorkingTime = () => {    const hour = currentTime.getHours();    const day = currentTime.getDay();    return day >= 1 && day <= 5 && hour >= 9 && hour <= 18;  };    const timeLabel = isWorkingTime() ? 'working hour' : 'off hours';  const timeColor = isWorkingTime() ? '#52c41a' : '#faad14';    return (    <div style={{ textAlign: 'center', margin: '16px 0' }}>      <span style={{        backgroundColor: timeColor,        color: 'white',        padding: '2px 8px',        borderRadius: '12px',        marginRight: '8px'      }}>        {timeLabel}      </span>      {currentTime.toLocaleString()}    </div>  );};function ChatApp() {  return (    <Chat>      <MessageList MessageTimeDivider={BusinessTimeDivider} />    </Chat>  );}
```

The effect is shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c2ac958617111f091585254001c06ec.png)

## Summary

The MessageList component provides complete message list functionality and various custom options. By reasonably configuring Props and customizing components, you can create a chat interface that meets business requirements. It is advisable to select appropriate configuration based on specific scenarios in actual use.


---
*Source: [https://trtc.io/document/72085](https://trtc.io/document/72085)*
