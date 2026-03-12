# MessageInput

## Overview

MessageInput is a fully functional message input component, providing core chat input features such as text editing, emoji selection, file attachment, and send button. It supports various custom options, including input behavior configuration, toolbar customization, component replacement, and slot expansion, meeting the personalized requirements of different chat scenarios.

## Props

| Field | Type | Default Value | Description |
| --- | --- | --- | --- |
| [autoFocus](#0633f6e0-65d3-41d6-a379-cb3bded1cbe6) | boolean | true | Whether to auto-focus into the input box |
| [disabled](#8c176ad9-d21a-4630-b391-4b875c9c38e4) | boolean | false | Whether to disable the input component |
| [hideSendButton](#b8151dc8-e87b-4237-a5e7-2530fbfbf3a6) | boolean | false | Whether to hide the send button |
| [placeholder](#da6cb1d1-3a46-4e13-8e74-42f8fefb9f2c) | string | '' | Input box placeholder text |
| [className](#12dafe1a-7a5e-4b65-bb6e-2aaf3a43563a) | string | undefined | Root container custom CSS class name |
| [style](#89805682-5b73-4480-b45a-7e441b3cce5d) | React.CSSProperties | undefined | Root container custom inline style |
| [attachmentPickerMode](#e7acec21-6bf4-435e-b6c2-d9d74093dfbb) | 'collapsed' \| 'expanded' | 'collapsed' | Attachment selector display mode |
| [actions](#17ac5267-8cad-460e-ad41-444702871b93) | MessageInputActions | ['EmojiPicker', 'AttachmentPicker'] | Toolbar action button configuration |
| [slots](#f1a3b8c4-0ab6-46bd-b2b0-453d06738818) | MessageInputSlots | undefined | Slot Configuration Object |
| [TextEditor](#abb5c4e3-61e1-4909-ae58-d29e8e95e88b) | JSX.Element | undefined | Custom Text Editor Component |
| [EmojiPicker](#29fef4a0-d8fb-4d5c-9eee-df7c3c2af65b) | JSX.Element | undefined | Custom Emoji Selector Component |
| [AttachmentPicker](#75289d5b-078f-4b09-a351-4490ec9663a6) | JSX.Element | undefined | Custom Attachment Selector Component |
| [FilePicker](#e7acec21-6bf4-435e-b6c2-d9d74093dfbb) | JSX.Element | undefined | Custom File Selector Component |
| [ImagePicker](#e7acec21-6bf4-435e-b6c2-d9d74093dfbb) | JSX.Element | undefined | Custom Image Selector Component |
| [VideoPicker](#e7acec21-6bf4-435e-b6c2-d9d74093dfbb) | JSX.Element | undefined | Custom Video Selector Component |

## Prop Explanation

### autoFocus

**type**: `boolean`

autoFocus is used to set whether to auto-focus into the input box when mounting, default value is `true`.

### disabled

**type**: `boolean`

disabled is used to set whether to disable the entire input component, including text input and all operation buttons, default value is `false`.

### hideSendButton

**type**: `boolean`

hideSendButton is used to set whether to hide the send button, suitable for scenarios where custom send trigger mode is needed, default value is `false`.

### placeholder

**type**: `string`

placeholder is used to set the placeholder text for the input box, default value is an empty string.

### className

type: `string`

className is used to set the custom CSS class name for the root container, default value is `undefined`.

### style

**type**: `React.CSSProperties`

style is used to set the custom inline style for the root container, default value is `undefined`.

### attachmentPickerMode

**type**: `'collapsed' | 'expanded'`

attachmentPickerMode is used to set the display mode of the attachment selector, default value is `'collapsed'`.

- `collapsed`: Collapse mode, unfold options after clicking
- `expanded`: Expanded mode, display all options directly

> **Note:**By default, AttachmentPicker refers to the attachment selector, including file selection, image selection, and video selection.When the attachmentPickerMode is "collapsed", click the attachment selector to pop up a menu displaying file selection, image selection, and video selection.When attachmentPickerMode is "expanded", the attachment selector expands by default, displaying file selection, image selection, and video selection in tile display.

### actions

**type**: `MessageInputActions`

Actions for configuration toolbar display action buttons, default value `['EmojiPicker', 'AttachmentPicker']`.

```
type BuiltInAction =  | 'EmojiPicker'  | 'ImagePicker'  | 'FilePicker'  | 'VideoPicker'  | 'AttachmentPicker';type CustomAction = {  key: string;  label?: string | undefined;  component?: React.ComponentType<any> | undefined;  className?: string | undefined;  style?: React.CSSProperties | undefined;  iconSize?: number | undefined;};type MessageInputActions = Array<BuiltInAction | CustomAction>;
```

#### Example1: Customizing Toolbar Button Sequence

```
import { Chat, MessageInput } from '@tencentcloud/chat-uikit-react';function ChatWithCustomActions() {  // Custom button sequence: file, image, video, emoji  const customActions = ['FilePicker', 'ImagePicker', 'VideoPicker', 'EmojiPicker'];    return (    <Chat>      <MessageInput actions={customActions} />    </Chat>  );}
```

The rendering is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7b9cdb0623d11f0bac1525400454e06.png)

#### Example 2: Adding Custom Action Buttons - Customer Service System Quick Reply

```
import { Chat, MessageInput, useMessageInputState } from '@tencentcloud/chat-uikit-react';// Quick reply componentfunction QuickReplyPicker() {  const { setContent } = useMessageInputState();    const quickReplies = [    'Hello, happy to serve you!',    'Please wait, I will check for you...',    'Thank you for your consultation, any other issues?',    The issue has been resolved. Have a pleasant life!,  ];  const handleQuickReply = (text: string) => {    setContent(text);  };  return (    <div style={{ position: 'relative' }}>      <button title="quick reply">â¡</button>      <div style={{        position: 'absolute',        bottom: '100%',        left: 0,        background: 'white',        border: '1px solid #ccc',        borderRadius: '4px',        padding: '8px',        minWidth: '200px'      }}>        {quickReplies.map((reply, index) => (          <div            key={index}            onClick={() => handleQuickReply(reply)}            style={{              padding: '4px 8px',              cursor: 'pointer',              borderRadius: '2px'            }}          >            {reply}          </div>        ))}      </div>    </div>  );}function CustomerServiceChat() {  const actions = [    {      key: 'quickReply',      label: 'quick reply',      component: QuickReplyPicker    },    'EmojiPicker',    'FilePicker'  ];    return (    <Chat>      <MessageInput actions={actions} />    </Chat>  );}
```

The rendering is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d9f5658666d511f0924f5254005ef0f7.png)

### slots

**type**: `MessageInputSlots`

Slots are used to insert custom content at specific locations in the input component, default value is `undefined`.

```
interface MessageInputSlots {  headerToolbar?: () => React.ReactNode;  footerToolbar?: () => React.ReactNode;  leftInline?: () => React.ReactNode;  rightInline?: () => React.ReactNode;  inputPrefix?: () => React.ReactNode;  inputSuffix?: () => React.ReactNode;}
```

![MessageInput architecture diagram](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7d0aae5623d11f0ad0f5254005ef0f7.png)

#### Example 1: Adding Message Statistics Display

```
import { Chat, MessageInput, useMessageInputState } from '@tencentcloud/chat-uikit-react';function ChatWithMessageStats() {  const { inputRawValue } = useMessageInputState();    // Header toolbar: Display character statistics  const HeaderToolbar = () => !inputRawValue    ? null    : (      <div style={{        padding: '4px 12px',        fontSize: '12px',        color: '#666',        borderBottom: '1px solid #eee',      }}      >        Character count:        {' '}        {inputRawValue?.reduce((acc, item) => acc + (item.type === 'text' ? item.content.length : 1), 0) || 0}        /500      </div>    );  // toolbar: display sending notification  const FooterToolbar = () => (    <div style={{      padding: '4px 12px',      fontSize: '12px',      color: '#999',      textAlign: 'right'    }}>      Press Ctrl+Enter to enter a new line    </div>  );  return (    <Chat>      <MessageInput         slots={{          headerToolbar: HeaderToolbar,          footerToolbar: FooterToolbar        }}      />    </Chat>  );}
```

The rendering is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7b8bf50623d11f0a64452540099c741.png)

#### Example 2: Input Box Prefix/Suffix Feature

```
import { Chat, MessageInput } from '@tencentcloud/chat-uikit-react';function ChatWithInputPrefixSuffix() {  // Input box prefix: @reminder feature  const InputPrefix = () => (    <button       style={{         border: 'none',         background: 'transparent',        color: '#1890ff',        cursor: 'pointer'      }}      onClick={() => {        // Trigger @user selection        console.log('toggle on @user selection')      }}    >      @    </button>  );  // Input box suffix: voice input  const InputSuffix = () => (    <button      style={{        border: 'none',        background: 'transparent',        cursor: 'pointer'      }}      onClick={() => {        // Start voice input        console.log('start voice input')      }}    >      ð¤    </button>  );  return (    <Chat>      <MessageInput         slots={{          inputPrefix: InputPrefix,          inputSuffix: InputSuffix        }}      />    </Chat>  );}
```

The rendering is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7d0d55c623d11f097ec52540044a08e.png)

#### Example 3: Fully Customizing the Toolbar on Both Sides

```
import { Chat, MessageInput } from '@tencentcloud/chat-uikit-react';function ChatWithCustomToolbars() {  // Left-side toolbar: only retain emoji and images  const LeftInline = () => (    <div style={{ display: 'flex', gap: '8px' }}>      <button>ð</button>      <button>ð·</button>    </div>  );  // toolbar on the right: custom sending area  const RightInline = () => (    <div style={{ display: 'flex', alignItems: 'center', gap: '8px' }}>      <span style={{ fontSize: '12px', color: '#666' }}>        Enter      </span>      <button        style={{          padding: '6px 12px',          background: '#1890ff',          color: 'white',          border: 'none',          borderRadius: '4px',          cursor: 'pointer'        }}      >        Send      </button>    </div>  );  return (    <Chat>      <MessageInput         slots={{          leftInline: LeftInline,          rightInline: RightInline        }}      />    </Chat>  );}
```

The rendering is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7b6dc29623d11f0a64452540099c741.png)

### TextEditor

**type**: `JSX.Element`

TextEditor is used to replace the default text editor component. Default value: `undefined`.

#### Example: Integrating a Rich Text Editor

```
import { Chat, MessageInput, useMessageInputState } from '@tencentcloud/chat-uikit-react';// Custom rich text editorfunction RichTextEditor() {  const { sendMessage } = useMessageInputState();  const [inputValue, setInputValue] = useState('');  const handleContentChange = (content: string) => {    setInputValue(content);  };  const handleKeyDown = (e: React.KeyboardEvent) => {    // Enter to send message    if (e.key === 'Enter') {      // Trigger sending logic      e.preventDefault();      sendMessage(inputValue);      // Clear input in editable div      const editableDiv = document.querySelector('.editable-div');      if (editableDiv) {        editableDiv.textContent = '';      }    }  };  return (    <div style={{      flex: 1,      border: '1px solid #d9d9d9',      borderRadius: '6px',      padding: '8px 12px',      minHeight: '32px',      maxHeight: '120px',      overflow: 'auto',    }}    >      <div        contentEditable        className="editable-div"        style={{          outline: 'none',          minHeight: '20px',          lineHeight: '20px',        }}        onInput={(e) => {          handleContentChange(e.currentTarget.textContent || '');        }}        onKeyDown={handleKeyDown}      />    </div>  );}function ChatWithRichTextEditor() {  return (    <Chat>      <MessageInput TextEditor={<RichTextEditor />} />    </Chat>  );}
```

The rendering is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7b56124623d11f0bac1525400454e06.png)

### EmojiPicker

type: `JSX.Element`

EmojiPicker replaces the default emoji selector component, default value `undefined`.

#### Example: Custom Emoji Panel

```
import { Chat, MessageInput, useMessageInputState } from '@tencentcloud/chat-uikit-react';// Custom Emoji Selectorfunction CustomEmojiPicker() {  const { insertContent } = useMessageInputState();  const emojiCategories = {    common: ['ð', 'ð', 'ð¥°', 'ð', 'ð¤', 'ð­', 'ð¡', 'ð'],    hands: ['ð', 'ð¤', 'ð', 'ð', 'âï¸', 'ð¤', 'ð¤', 'ð'],    animals: ['ð¶', 'ð±', 'ð­', 'ð¹', 'ð°', 'ð¦', 'ð»', 'ð¼'],  };  const [activeCategory, setActiveCategory] = useState('common');  const [showPicker, setShowPicker] = useState(false);  const insertEmoji = (emoji: string) => {    insertContent(emoji);    setShowPicker(false);  };  return (    <div style={{ position: 'relative' }}>      <button        onClick={() => setShowPicker(!showPicker)}        style={{ border: 'none', background: 'transparent', cursor: 'pointer' }}      >        ð      </button>      {showPicker && (        <div style={{          position: 'absolute',          bottom: '100%',          left: 0,          background: 'white',          border: '1px solid #ccc',          borderRadius: '8px',          padding: '12px',          width: '280px',          boxShadow: '0 4px 12px rgba(0,0,0,0.1)',        }}        >          {/* Category tag */}          <div style={{ display: 'flex', marginBottom: '8px' }}>            {Object.keys(emojiCategories).map(category => (              <button                key={category}                onClick={() => setActiveCategory(category)}                style={{                  padding: '4px 8px',                  border: 'none',                  background: activeCategory === category ? '#1890ff' : 'transparent',                  color: activeCategory === category ? 'white' : '#666',                  borderRadius: '4px',                  cursor: 'pointer',                  fontSize: '12px',                }}              >                {category}              </button>            ))}          </div>          {/* Emoji grid */}          <div style={{            display: 'grid',            gridTemplateColumns: 'repeat(8, 1fr)',            gap: '4px',          }}          >            {emojiCategories[activeCategory].map(emoji => (              <button                key={emoji}                onClick={() => insertEmoji(emoji)}                style={{                  border: 'none',                  background: 'transparent',                  fontSize: '20px',                  cursor: 'pointer',                  padding: '4px',                  borderRadius: '4px',                }}              >                {emoji}              </button>            ))}          </div>        </div>      )}    </div>  );}function ChatWithCustomEmoji() {  return (    <Chat>      <MessageInput EmojiPicker={<CustomEmojiPicker />} />    </Chat>  );}
```

The rendering is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7d124c8623d11f0b30d5254007c27c5.png)

### AttachmentPicker

type: `JSX.Element`

AttachmentPicker is used to replace the default attachment selector component, default value is `undefined`.

#### Example: Attachment Selector for Storage Integration

```
import { Chat, MessageInput } from '@tencentcloud/chat-uikit-react';// Attachment Selector with Cloud Storage Integrationfunction CloudAttachmentPicker() {  const [showPicker, setShowPicker] = useState(false);    const attachmentTypes = [    { key: 'local', label: 'local file', icon: 'ð' },    { key: 'cloud', label: 'cloud file', icon: 'âï¸' },    { key: 'recent', label: 'recent file', icon: 'ð' },    { key: 'screenshot', label: 'screenshot', icon: 'ð·' }  ];  const handleAttachmentSelect = async (type: string) => {    switch (type) {      case 'local':        // Open local file selection        const input = document.createElement('input');        input.type = 'file';        input.multiple = true;        input.onchange = (e) => {          const files = (e.target as HTMLInputElement).files;          console.log('selected local files:', files);        };        input.click();        break;              case 'cloud':        // Toggle on cloud file selection        console.log('Toggle on cloud file selection');        break;              case 'recent':        // Display recent files        console.log('Display recent files');        break;              case 'screenshot':        // Start screenshot        console.log('start screenshot')        break;    }    setShowPicker(false);  };  return (    <div style={{ position: 'relative' }}>      <button         onClick={() => setShowPicker(!showPicker)}        style={{ border: 'none', background: 'transparent', cursor: 'pointer' }}      >        ð      </button>            {showPicker && (        <div style={{          position: 'absolute',          bottom: '100%',          left: 0,          background: 'white',          border: '1px solid #ccc',          borderRadius: '8px',          padding: '8px',          minWidth: '160px',          boxShadow: '0 4px 12px rgba(0,0,0,0.1)'        }}>          {attachmentTypes.map(type => (            <div              key={type.key}              onClick={() => handleAttachmentSelect(type.key)}              style={{                display: 'flex',                alignItems: 'center',                gap: '8px',                padding: '8px 12px',                cursor: 'pointer',                borderRadius: '4px',                fontSize: '14px'              }}            >              <span>{type.icon}</span>              <span>{type.label}</span>            </div>          ))}        </div>      )}    </div>  );}function ChatWithCloudAttachment() {  return (    <Chat>      <MessageInput AttachmentPicker={<CloudAttachmentPicker />} />    </Chat>  );}
```

The rendering is shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7ba5f92623d11f092fe525400bf7822.png)

## Summary

The MessageInput component provides complete message input functionality and various custom options. By reasonably configuring Props and using the slot system, you can create an input interface that meets specific business requirements. It is recommended to choose an appropriate customized scheme based on real-world usage scenarios and maintain good user experience and performance.


---
*Source: [https://trtc.io/document/72088](https://trtc.io/document/72088)*
