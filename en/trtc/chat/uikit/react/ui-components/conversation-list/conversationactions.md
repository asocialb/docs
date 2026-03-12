# ConversationActions

`ConversationActions` component is responsible for row operations on a single session, supported by default with delete conversation, pin conversation to top/unpin, and mute/unmute features.

## Basic Usage

When using `ConversationActions` in `ConversationList`, you can customize it directly through the top-level `actionsConfig` parameter of `ConversationList`. `actionsConfig` supports default conversation operation feature toggles, event response, adding new custom action items, and basic UI customization.

For advanced customization, you can create new components through `ConversationActions`.

### Using ActionsConfig Basic Customization

```
import { UIKitProvider, ConversationList } from "@tencentcloud/chat-uikit-react";import type { ConversationModel } from "@tencentcloud/chat-uikit-react";const App = () => {  return (    <UIKitProvider>      <ConversationList        actionsConfig={{          enablePin: false,          onConversationDelete: (conversation: ConversationModel) => { console.log('Delete conversation success'); },          customConversationActions: {            'custom-actions-1': {               label: 'custom-actions',               onClick: (conversation: ConversationModel) => { console.log(conversation); },             },          },      }}/>    </UIKitProvider>  );}
```

### Custom ConversationActions Component

```
import { UIKitProvider, ConversationList, ConversationActions } from "@tencentcloud/chat-uikit-react";import type { ConversationActionsProps } from '@tencentcloud/chat-uikit-react';const CustomConversationActions = (props: ConversationActionsProps) => {  return <ConversationActions {...props} enableDelete={false} />;};const App = () => {  return (    <UIKitProvider>      <ConversationList        style={{ maxWidth: '300px', height: '600px' }}        ConversationActions={CustomConversationActions}      />    </UIKitProvider>  );}
```

## Props

`ConversationActions` component API type `ConversationActionsProps` is based on `ConversationActionsConfig` API and expanded.

| **ConversationActionsProps** |  |  |  |
| --- | --- | --- | --- |
| **Parameter Name** | **Type** | **Default Value** | **Note** |
| **conversation*****(Required)*** | ConversationModel | - | This parameter is required and represents the session for the current rendered conversation operation. |
| className | String | - | Custom root element class name. |
| style | React.CSSProperties | - | Custom root element style. |
| ConversationActionsConfig |  |  |  |
| **Parameter Name** | **Type** | **Default Value** | **Note** |
| enablePin | Boolean | true | Whether to display the pin to top feature button. |
| enableMute | Boolean | true | Whether to display the do not disturb feature button. |
| enableDelete | Boolean | true | Whether to display the deletion feature button. |
| onConversationPin | (conversation: ConversationModel, e?: React.MouseEvent) => void | - | Customize the behavior of pinning/unpinning conversations. |
| onConversationMute | (conversation: ConversationModel, e?: React.MouseEvent)=> void | - | Customize the behavior of do not disturb/cancel Do Not Disturb session. |
| onConversationDelete | (conversation: ConversationModel, e?: React.MouseEvent) => void | - | Customize the behavior of deleting conversations. |
| customConversationActions | Record<string, [ConversationActionItem](#96079c71-233e-442e-96ef-ba91fbd5e201)> | - | Custom session operation items. |
| PopupIcon | ReactElement | - | Custom action pop-up icon. |
| PopupElements | ReactElement[] | - | Content of the custom action popup. |
| onClick | (e: React.MouseEvent, key?: string, conversation?: ConversationModel) => void | - | Callback function for click action. |

## Customize Component

### Basic Feature Switch

By setting the `enablePin`, `enableDelete`, and `enableMute` parameters, you can flexibly control the display of conversation pinning, mute message notification, and conversation deletion in `ConversationActions`.

```
<ConversationActions enablePin={false} />
```

```
enableDelete
```

```
enableMute
```

| `enablePin={false}` | `enableDelete={false}` | `enableMute={false} ` |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e7be41055e2f11f091585254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e7baa5d75e2f11f0b324525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e7be68215e2f11f091585254001c06ec.png) |

### Event Response

`ConversationActions` component supports delete conversation, pin conversation to top/unpin, and mute/unmute features by default. If the event response of existing functionality does not meet your needs, you can customize the event response handling function and override it. In addition to customizing feature event responses, you can also obtain basic click event response through onClick.

```
import { ConversationList, ConversationActions, Toast } from '@tencentcloud/chat-uikit-react';import type { ConversationActionsProps, ConversationModel } from '@tencentcloud/chat-uikit-react';const CustomConversationActions = (props: ConversationActionsProps) => {  return (    <ConversationActions      {...props}      onConversationDelete={(conversation: ConversationModel) => {        conversation.deleteConversation().then(() => {          Toast({ text: 'delete conversation successfully!', type: 'info' });        }).catch(() => {          Toast({ text: 'delete conversation failed!', type: 'error' });        });      }}    />  );};<ConversationList ConversationActions={CustomConversationActions} />
```

### customConversationActions

`customConversationActions` is used to add new custom action items to the ConversationActions list.

| ConversationActionItem |  |  |  |
| --- | --- | --- | --- |
| **Parameter Name** | **Type** | **Default Value** | **Note** |
| enable | Boolean | true | Whether to enable custom action items. |
| label | String | - | Display content of custom action items. |
| onClick | (conversation: ConversationModel, e?: React.MouseEvent) => void | - | Callback function for clicking a custom action item. |

Here is an example of adding new custom action items using `customConversationActions`:

```
import { ConversationList, ConversationActions } from '@tencentcloud/chat-uikit-react';import type { ConversationActionsProps, ConversationModel } from '@tencentcloud/chat-uikit-react';const CustomConversationActions = (props: ConversationActionsProps) => {  return (    <ConversationActions       {...props}       customConversationActions={{        'custom-actions-1': {           label: 'custom-actions',           onClick: (conversation: ConversationModel) => { console.log(conversation); },         },      }}    />  );};     <ConversationList ConversationActions={CustomConversationActions} />
```

| **Before modification** | **After modification** |
| --- | --- |
| ****![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e7c05dbf5e2f11f097ec52540044a08e.png)**** | ****![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e7c27bfd5e2f11f097ec52540044a08e.png)**** |

### UI Interface Customization

You can customize the wakeup popup button style through the `PopupIcon` parameter and the popup content through `PopupElements`.

The following is example code for secondary development on the basis of the default `ConversationActions` component to customize a new awakening button style:

```
import { ConversationList, ConversationActions, ConversationActionsProps } from '@tencentcloud/chat-uikit-react';import type { ConversationActionsProps } from '@tencentcloud/chat-uikit-react';const CustomConversationActions = (props: ConversationActionsProps) => {  const customIcon = <div>Custom Icon</div>  return (    <ConversationActions {...props} PopupIcon={customIcon} />  );};     <ConversationList ConversationActions={CustomConversationActions} />
```

| **Before modification** | **After modification** |
| --- | --- |
| ****![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e7bc736e5e2f11f092fe525400bf7822.png) | ****![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e7cccf8a5e2f11f0b30d5254007c27c5.png) |


---
*Source: [https://trtc.io/document/64707](https://trtc.io/document/64707)*
