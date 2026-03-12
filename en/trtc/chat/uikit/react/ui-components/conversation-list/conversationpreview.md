# ConversationPreview

`ConversationPreview` is used for previewing session content in the list. The component displays session information, unread count, and provides conversation action feature.

With the aid of atomic information display components, you can freely design and combine your desired `ConversationPreview` layout.

Meanwhile, you can also use the `onConversationSelect` function to define selected session behavior.

### Basic Usage

You can use the `Preview` property of `ConversationList` to customize the preview item for each individual conversation in the list. If the `Preview` property is not specified, the system will automatically adopt the `ConversationPreviewUI` component as the default value.

```
import { ConversationList, ConversationPreviewUI } from '@tencentcloud/chat-uikit-react';import type { ConversationPreviewUIProps } from '@tencentcloud/chat-uikit-react';const CustomConversationPreview = (props: ConversationPreviewUIProps) => {  const { Title } = props;  return (    <ConversationPreviewUI {...props}>      {Title}      <div>Your custom preview UI</div>    </ConversationPreviewUI>  );};<ConversationList Preview={CustomConversationPreviewUI}></ConversationList>
```

### Props

| **Parameter Name** | **Type** | **Default Value** | **Description** |
| --- | --- | --- | --- |
| **conversation*****(Required)*** | ConversationModel | - | Required parameter to indicate the currently rendered conversation list item. |
| isSelected | Boolean | false | Control if the conversation list item UI is in selected status. |
| enableActions | Boolean | true | Control whether to display the conversation operation feature. |
| actionsConfig | [ConversationActionsConfig](https://www.tencentcloud.com/document/product/1047/64707#4cc59d08-632e-4817-a124-cf1fcb8de3c3) | - | For custom session operation configuration. |
| highlightMatchString | String | - | Conversation list item Title highlights matching keywords, commonly used for Conversation Search results. |
| Title | `String ï½ JSX.Element` | ConversationPreviewTitle | Render the title area of the conversation list item. |
| LastMessageAbstract | `String ï½ JSX.Element` | ConversationPreviewAbstract | Render the latest message abstract area of the conversation list item. |
| LastMessageTimestamp | `String ï½ JSX.Element` | ConversationPreviewTimestamp | Render the latest message timestamp area of the conversation list item. |
| Unread | `String ï½ JSX.Element` | ConversationPreviewUnread | Render the unread indicator area of the conversation list item. |
| ConversationActions | `ReactElement` | ConversationActions | Render the conversation operations area of the conversation list item. |
| Avatar | ReactElement | Avatar | Render the avatar area of the conversation list item. |
| onConversationSelect | (conversation: ConversationModel) => void; | - | Specify the attributes of receiving callback when selecting a dialogue in the conversation list. |
| className | String | - | Set a custom name for the root element class in CSS. |
| style | React.CSSProperties | - | Set custom styles for the root element. |

## Custom Case

### Discord-Like Style

Discord is a popular chat application, similar to Skype or Telegram. The message content in Discord is as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/656b6c8c5e3011f0b30d5254007c27c5.png)

By customizing the `ConversationPreview` layout, features, and style, we can quickly achieve a Discord-like effect.

React

CSS

1. Customize the `ConversationListPreview`
2. Switch theme to dark mode

```
import { UIKitProvider, ConversationList, ConversationPreviewUI } from '@tencentcloud/chat-uikit-react';import type { ConversationPreviewUIProps } from '@tencentcloud/chat-uikit-react';const CustomConversationPreview = (props: ConversationPreviewUIProps) => {  const { Title } = props;  return (    <ConversationPreviewUI {...props}>      <span> # </span>      <span>{Title}</span>    </ConversationPreviewUI>  );};const App = () => {    <UIKitProvider theme={'dark'}>      <ConversationList         style={{ maxWidth: '300px', height: '600px' }}         Preview={CustomConversationPreviewUI}       />      ...    </UIKitProvider>}
```

```
.custom-preview-ui {  height: 34px;  border-radius: 6px;  padding: 10px;  margin: 0 10px;  .custom-preview-ui__tag {    margin-right: 10px;    font-size: 16px;    color: #b3b3b4;  }  .custom-preview-ui__title {    font-size: 14px;    color: #b3b3b4;  }  &.uikit-conversation-preview--active {    background-color: #3b3d43;    .custom-preview-ui__tag {      color: #ffffff;    }    .custom-preview-ui__title {      .uikit-conversation-preview__title {        color: #ffffff;      }    }  }}
```

`ConversationListPreview` effect as follows after customization:

| **Before Modification** | **Modified** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6545c5575e3011f091585254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6544f8a25e3011f0bac1525400454e06.png) |

###


---
*Source: [https://trtc.io/document/64705](https://trtc.io/document/64705)*
