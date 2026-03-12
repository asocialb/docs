# Message Search

## **Feature Experience**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d848c7121cea11efbfc25254003441b1.png)

## ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8fb4b0b1cea11ef8f53525400fa9af4.png)

## UI-Included Integration

### Quickly Integrating Message Cloud Search

Web&H5 Vue2&Vue3

Uniapp Vue2&Vue3

#### Step 1. Integrate TUIKit

- If **@tencentcloud/chat-uikit-vue â¥ 2.0.0** is not integrated, follow the [Vue2 & Vue3 TUIKit Quick Integration Guide](https://trtc.io/document/58644?platform=web&product=chat) for integration.

#### Step 2. Activate the cloud search plugin through the console

> **Note:**Each plugin can be tried for 7 days for free once. The service will be discontinued after the trial. Therefore, you need to purchase the plugin in advance. During the trial, only the content of messages generated after the cloud search feature is enabled can be searched, and historical messages cannot be searched. After you purchase the plugin, historical messages will be automatically synchronized and become searchable.

#### Step 3. Search for your first message

After completing [Vue2 & Vue3 TUIKit Quick Integration Guide - Step 6. Send your first message](https://trtc.io/document/58644?platform=web&product=chat#.E6.AD.A5.E9.AA.A47.EF.BC.9A.E5.8F.91.E9.80.81.E6.82.A8.E7.9A.84.E7.AC.AC.E4.B8.80.E6.9D.A1.E6.B6.88.E6.81.AF), search for the message you just sent.

#### Step 1. Integrate TUIKit

- If **@tencentcloud/chat-uikit-uniapp â¥ 2.0.6** is not integrated, follow the [Uniapp TUIKit Quick Integration Guide](https://www.tencentcloud.com/zh/document/product/1047/58649) for integration.

#### Step 2. Activate the cloud search plugin through the console

> **Note:**Each plugin can be tried for 7 days for free once. The service will be discontinued after the trial. Therefore, you need to purchase the plugin in advance. During the trial, only the content of messages generated after the cloud search feature is enabled can be searched, and historical messages cannot be searched. After you purchase the plugin, historical messages will be automatically synchronized and become searchable.

#### Step 3. Search for your first message

After completing [Uniapp TUIKit Quick Integration Guide - Step 6. Send your first message](https://www.tencentcloud.com/zh/document/product/1047/58649#.E6.AD.A5.E9.AA.A44.EF.BC.9A.E8.BF.90.E8.A1.8C.E6.95.88.E6.9E.9C), search for the message you just sent.

### **Independently Introducing Message Cloud Search**

> **Note:****In the step**[Quickly Integrating Message Cloud Search](https://trtc.io/document/60748?platform=web&product=chat#2d8e717e-68ad-437c-adf4-2c6938e51315)**above, all features of message cloud search are introduced by default, and therefore do not need to be introduced independently.**If you want to independently introduce the <TUISearch> for message cloud search, see the following guide.

Web&H5 Vue2&Vue3

Uniapp Vue2&Vue3

#### Prerequisites

- If **@tencentcloud/chat-uikit-vue â¥ 2.0.0**is not integrated, follow the [Vue2 & Vue3 TUIKit Quick Integration Guide](https://trtc.io/document/58644?platform=web&product=chat) for integration.

#### Introducing **<TUISearch>**

On the `.vue` page where you need the **message cloud search** feature, introduce **<TUISearch>**.

##### **<TUISearch>** Parameter Description

| Parameter Name | Type | Description |
| --- | --- | --- |
| searchType | String | global: global search (default) |
|   |   | conversation: search in conversation |

##### **<TUISearch>** Effect Display

| <TUISearch searchType="global" /> | <TUISearch searchType="conversation" /> |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8658f691cea11efb2fd525400f57d1f.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d851abb11cea11ef8e50525400562f24.png) |

##### **Using TUISearch**

```
import { TUISearch } from "@tencentcloud/chat-uikit-vue";// Global search<TUISearch searchType="global" />// Search in conversation<TUISearch searchType="conversation" />
```

##### **Deleting the TUISearch Introduced by Default**

TUIKit comes with `<TUISearch>` integrated by default. If you prefer not to use the default integration method, you can comment out `<TUISearch>` in `TUIKit/index.vue`.

**Uniapp TUISearch supports two integration methods: component and page.**

#### Prerequisites

- If **@tencentcloud/chat-uikit-uniapp â¥ 2.0.6** is not integrated, follow the [Uniapp TUIKit Quick Integration Guide](https://www.tencentcloud.com/zh/document/product/1047/58649#.E6.AD.A5.E9.AA.A44.EF.BC.9A.E8.BF.90.E8.A1.8C.E6.95.88.E6.9E.9C) for integration.

Component-based Introduction

Page-based Introduction

On the `.vue` page where you need the **message cloud search** feature, introduce **<TUISearch>**.

##### **<TUISearch>** Parameter Description

| Parameter Name | Type | Description |
| --- | --- | --- |
| searchType | String | global: global search |
|   |   | conversation: search in conversation (default) |

##### **<TUISearch>** Effect Display

| <TUISearch searchType="global" /> | <TUISearch searchType="conversation" /> |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d9b8e4441cea11ef92fe525400dbceb9.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8bffa261cea11efbfc25254003441b1.png) |

##### **Using TUISearch**

```
// The following is just an example path. Replace it with the path of your project.import { TUISearch } from "/TUIKit/components/TUISearch/index.vue";// Global search<TUISearch searchType="global" />// Search in conversation<TUISearch searchType="conversation" />
```

##### **Deleting the TUISearch Introduced by Default**

TUIKit comes with `<TUISearch>` integrated by default. If you prefer not to use the default integration method, you can comment out `<TUISearch>` in `TUIKit/components/TUIConversation/index.vue`.

##### **Adding a TUISearch Page in pages.json**

```
{  "pages": [    ...,    {      "path": "TUIKit/components/TUISearch/index",      "style": {        "navigationBarTitleText": "Chat records"      }    }  ],  ...}
```

##### **Navigating to the TUISearch Page**

```
uni.navigateTo({   url: "/TUIKit/components/TUISearch/index",});
```

### **Advanced Guide**

#### **Adding Search Message Types**

| Original global search message type list | Global search message type list after addition |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8ed03431cea11efba53525400c60541.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8fc84641cea11efb25c5254003359ae.png) |

Directory location: `src/TUIKit/components/TUISearch/search-type-list.ts`

`searchMessageTypeList` contains all the definitions in the Search Message Types tab. To add search message types not defined in `searchMessageTypeList`, follow the structure below to add them in `searchMessageTypeList`:

```
[keyName: string]: {    key: string; // Specifies the key of the search message type, which must be unique.    label: string; // Specifies the label for rendering the search message type.    value: Array<string>; // Specifies the actual search list for the search message type. };  // For example, to search for custom messagesexport const searchMessageTypeList = {    ...    customMessage: {      key: "customMessage", // Specifies the key of the search message type, which must be unique.      label: "Custom", // Specifies the label for rendering the search message type.      value: [TUIChatEngine.TYPES.MSG_CUSTOM], // Specifies the actual search list for the search message type.    }};
```

Due to TUIKit's use of i18next for internationalization, if you want to claim a new label, add the corresponding international entries in `src/TUIKit/locales/zh_cn/TUISearch.ts` and `src/TUIKit/locales/en/TUISearch.ts` for translation.

To add a type defined in `searchMessageTypeList` to the **global search message type list** or **search in conversation message type list**, you just need to add its `key` to `globalSearchTypeKeys` or `conversationSearchTypeKeys`.

```
// For example, to apply the newly defined customMessage to the global search message type listexport const globalSearchTypeKeys = [..., "customMessage"];// For example, to apply the newly defined customMessage to the search in conversation message type listexport const conversationSearchTypeKeys = [..., "customMessage"];
```

#### **Adding a Time Range for Message Cloud Search**

| Original global search time range list | Global search time range list after addition |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d848f3331cea11efbfc25254003441b1.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d881fb011cea11efb25c5254003359ae.png) |

Directory location: `src/TUIKit/components/TUISearch/search-time-list.ts`

`searchMessageTimeList` contains all definitions in the Search Time Range tab. To add search time range types not defined in `searchMessageTimeList`, follow the structure below to add them in `searchMessageTimeList`:

```
[keyName: string]: {    key: string; // Specifies the key of the message search time range, which must be unique.    label: string; // Specifies the label for rendering the message search time range.    value: {       timePosition: number; // Specifies the start position for message search time range. The default value is 0, indicating searching from the current time.      timePeriod: number; // Specifies the time range to search backward from timePosition.    };};  // For example, to search for messages in the time range of last 2 daysexport const searchMessageTimeList = {   ...   twoDay: {      key: "twoDay", // Specifies the key of the message search time range, which must be unique.      label: "Two days", // Specifies the label for rendering the message search time range.      value: {        timePosition: 0, // Specifies the start position for message search time range. The default value is 0, indicating searching from the current time.        timePeriod: 2 * oneDay; // Specifies the time range to search backward from timePosition.      },  },};
```

Due to TUIKit's use of i18next for internationalization, if you want to claim a new label, add the corresponding international entries in `src/TUIKit/locales/zh_cn/TUISearch.ts` and `src/TUIKit/locales/en/TUISearch.ts` for translation.


---
*Source: [https://trtc.io/document/60748](https://trtc.io/document/60748)*
