# ChatSetting

## Component Overview

`ChatSetting` is an intelligent chat settings component that can automatically render the appropriate settings interface based on the currently activated session type. This component internally integrates two modes: C2C (one-on-one) chat settings and group chat settings, providing users with a uniform chat settings portal.

Core features of components:

- **Automatic adaptation** - The settings interface is automatically switched based on session type
- **Status-driven** - Auto-update content based on the current active session status

## Props Parameters

| Parameter | Type | Default Value | Description |
| --- | --- | --- | --- |
| className | string \| undefined | undefined | Custom CSS class name |
| style | React.CSSProperties \| undefined | undefined | Custom inline style |

## Quick Usage

`ChatSetting` is an independent component that can be used freely. By default, the switch control is on the ChatHeader Component. Alternatively use the useUIOpenControlState Hook to customize the ChatSetting switch.

```
function App() {  const { isChatSettingOpen, setChatSettingOpen } = useUIOpenControlState();    function toggleChatSettingOpen() {    setChatSettingOpen(!isChatSettingOpen);  }    return (     <UIKitProvider>        <div style={{ maxWidth: '300px' }}>          <ConversationList />        </div>        <Chat          PlaceholderEmpty={null}          style={{            display: 'flex',            flexDirection: 'row',            flex: 1,            maxHeight: '100vh',          }}        >          <div style={{            display: 'flex',            flexDirection: 'column',            flex: 1,            minWidth: '0',          }}          >            <button onClick={toggleChatSetting}>toggle</button>            <MessageList />            <MessageInput />          </div>          {isChatSettingOpen && <ChatSetting style={{ width: '350px' }} />}        </Chat>      </UIKitProvider>  );}
```


---
*Source: [https://trtc.io/document/72094](https://trtc.io/document/72094)*
