# MessageList State

## MessageListState Overview

`MessageListState` is a status management center related to building message lists, specialized in managing message list status and operations. It provides core features like message list data management, load by page, read receipt settings, and scroll control, making it an important tool to build chat interface.

`MessageListState` adopts a responsive design, can automatically listen to underlying data changes and refresh component status, and provides various business operation methods to satisfy different use cases.

## When to Use MessageListState

When the current MessageList capacity cannot meet the requirement, or if you want to redevelop MessageList with the aid of underlying data, you can use `useMessageListState()` to obtain the original data source and perform redevelopment.

## List of attributes

| Field | Type | Description |
| --- | --- | --- |
| messageList | readonly MessageModel[] \| undefined | Message list data |
| hasMoreOlderMessage | boolean \| undefined | Whether more historical messages can be loaded |
| enableReadReceipt | boolean \| undefined | Whether to enable the receipt feature |
| isDisableScroll | boolean | Disable scrolling |
| setIsDisableScroll | (isDisableScroll: boolean) => void | Method to set the scroll state |
| loadMoreMessage | () => Promise<any> | Method to load more messages |
| setEnableReadReceipt | (enableReadReceipt: boolean \| undefined) => void | Method to set the read receipt status |

## Attribute Details

### messageList

- **Type**: `readonly MessageModel[] | undefined`
- **Description**: The message list data of the current session. This is a read-only array containing all loaded message objects. Each message object contains complete information such as message content, sender, timestamp, and status. When the underlying data is not fully loaded, the value is `undefined`.

### hasMoreOlderMessage

- **Type**: `boolean | undefined`
- **Description**: Indicates whether there are more historical messages to load. When the value is `true`, it means earlier messages can be obtained through the `loadMoreMessage` method; when the value is `false`, it means all historical messages have already been loaded; when the value is `undefined`, it means the loading status is undetermined.

### enableReadReceipt

- **Type**: `boolean | undefined`
- **Description**: Control whether to enable the read receipt feature. When set to `true`, the message will display read status; when set to `false`, it will not show read status; when the value is `undefined`, it means the user has not specified whether to enable the read receipt feature.

### isDisableScroll

- **Type**: `boolean`
- **Description**: Control the scrolling behavior of the message list. When set to `true`, it disables the auto-scroll feature; when set to `false`, it allows normal scrolling. Typically set to `true` when users manually scroll through historical messages to avoid auto-scroll affecting user experience upon new message arrival. This field setting does not disable page scroll. Please use this field for control on the dom side.

### setIsDisableScroll

- **Type**: `(isDisableScroll: boolean) => void`
- **Description**: Method used to set scroll status. Receives a boolean parameter to control whether to disable scroll functionality.

### loadMoreMessage

- **Type**: `() => Promise<any>`
- **Description**: Method to asynchronously load more historical messages. Calling this method sends a server request for earlier message data and auto-updates the `messageList` and `hasMoreOlderMessage` status.

### setEnableReadReceipt

- **Type**: `(enableReadReceipt: boolean | undefined) => void`
- **Description**: Method used to set the receipt feature switch. It accepts a boolean value or `undefined` parameter to control whether to enable read receipt.

## Usage Examples

Here is a complete MessageList component example that shows how to use `messageList`, `hasMoreOlderMessage`, and `loadMoreMessage` to build a message list with pagination loading:

```
import React, { useEffect, useRef, useState } from 'react';import { useMessageListState } from '@tencentcloud/chat-uikit-react';import type { MessageModel } from '@tencentcloud/chat-uikit-react';import './MessageList.scss';interface MessageListProps {  className?: string;}const MessageList: React.FC<MessageListProps> = ({ className }) => {  const {    messageList,    hasMoreOlderMessage,    loadMoreMessage,    isDisableScroll,    setIsDisableScroll,  } = useMessageListState();  const [isLoading, setIsLoading] = useState(false);  const messageListRef = useRef<HTMLDivElement>(null);  const prevScrollHeight = useRef<number>(0);  // load more messages  const handleLoadMore = async () => {    if (isLoading || !hasMoreOlderMessage) return;    setIsLoading(true);    try {      // Record the current scroll height      if (messageListRef.current) {        prevScrollHeight.current = messageListRef.current.scrollHeight;      }      await loadMoreMessage();    } catch (error) {      console.error('Failed to load more messages:', error);    } finally {      setIsLoading(false);    }  };  // Handle scroll event  const handleScroll = (e: React.UIEvent<HTMLDivElement>) => {    const target = e.target as HTMLDivElement;    const { scrollTop, scrollHeight, clientHeight } = target;    // Detect whether scrolled to top, trigger loading more    if (scrollTop === 0 && hasMoreOlderMessage && !isLoading) {      handleLoadMore();    }    // detect whether users are viewing historical message    const isAtBottom = scrollTop + clientHeight >= scrollHeight - 10;    setIsDisableScroll(!isAtBottom);  };  // Keep scroll position (after loading more messages)  useEffect(() => {    if (messageListRef.current && prevScrollHeight.current > 0) {      const newScrollHeight = messageListRef.current.scrollHeight;      const scrollDiff = newScrollHeight - prevScrollHeight.current;      messageListRef.current.scrollTop = scrollDiff;      prevScrollHeight.current = 0;    }  }, [messageList]);  // Auto-scroll to bottom (on message arrival)  useEffect(() => {    if (messageListRef.current && !isDisableScroll) {      messageListRef.current.scrollTop = messageListRef.current.scrollHeight;    }  }, [messageList, isDisableScroll]);  // Render a single message  const renderMessage = (message: MessageModel) => (    <div key={message.ID} className="message-item">      <div className="message-sender">{message.nick || message.from}</div>      <div className="message-content">        {          (() => {            if (message.type === 'TIMTextElem') {              return  <span className="text-message">{message.payload.text}</span>;            } else {              return <span>other message</span>;            }          })()        }      </div>      <div className="message-time">        {new Date(message.time * 1000).toLocaleTimeString()}      </div>    </div>  );  return (    <div className={`im-message-list-container ${className || ''}`}>      {/* load more indicator */}      {hasMoreOlderMessage && (        <div className="load-more-indicator">          {isLoading ? (            <div className="loading">loading...</div>          ) : (            <button onClick={handleLoadMore} className="load-more-btn">              load more messages            </button>          )}        </div>      )}      {/* message list */}      <div        ref={messageListRef}        className="message-list"        onScroll={handleScroll}      >        {messageList?.map(renderMessage)}      </div>      {/* empty state */}      {messageList?.length === 0 && (        <div className="empty-state">          No Messages        </div>      )}    </div>  );};export default MessageList;
```

### Style Reference

```
.im-message-list-container {  display: flex;  flex-direction: column;  flex: 1 1 auto;  overflow: auto hidden;    .load-more-indicator {    padding: 10px;    text-align: center;    border-bottom: 1px solid #eee;        .loading {      color: #666;      font-size: 14px;    }        .load-more-btn {      padding: 8px 16px;      background: #007bff;      color: white;      border: none;      border-radius: 4px;      cursor: pointer;            &:hover {        background: #0056b3;      }    }  }    .message-list {    flex: 1;    overflow-y: auto;    min-height: 0;    padding: 10px;        .message-item {      margin-bottom: 15px;      padding: 10px;      background: #f5f5f5;      border-radius: 8px;            .message-sender {        font-weight: bold;        color: #333;        margin-bottom: 5px;      }            .message-content {        color: #666;        line-height: 1.5;        margin-bottom: 5px;      }            .message-time {        font-size: 12px;        color: #999;        text-align: right;      }    }  }    .empty-state {    flex: 1;    display: flex;    align-items: center;    justify-content: center;    color: #999;    font-size: 14px;  }}
```

This example shows how to:

1. Use `messageList` to render the message list.
2. Determine whether to display the load more button via `hasMoreOlderMessage`.
3. Call `loadMoreMessage` to load by page.
4. Combine `isDisableScroll` and `setIsDisableScroll` to optimize scrolling experience.
5. Handle loading and empty state display.


---
*Source: [https://trtc.io/document/72086](https://trtc.io/document/72086)*
