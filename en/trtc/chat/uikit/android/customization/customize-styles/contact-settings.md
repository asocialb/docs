# Contact Settings

The following will guide you through how to hide the contact setting options.

## Hide contact setting options

API Function: Hide Contact Settings Options. This setting is effective for all contacts.

API prototype:

```
// FriendConfig.javapublic static final int ALIAS = 1;public static final int MUTE_AND_PIN = 2;public static final int BACKGROUND = 3;public static final int BLOCK = 4;public static final int CLEAR_CHAT_HISTORY = 5;public static final int DELETE = 6;public static final int ADD_FRIEND = 7;@IntDef({ALIAS, MUTE_AND_PIN, BACKGROUND, BLOCK, CLEAR_CHAT_HISTORY, DELETE, ADD_FRIEND})private @interface Items {}/** * Hide items in contact config interface. */public static void hideItemsInContactConfig(@Items int... items)
```

Sample code:

```
// When to call: Before initializing contact setting interface. // Valid for contacts.FriendConfig.hideItemsInContactConfig(FriendConfig.BLOCK,                                       FriendConfig.CLEAR_CHAT_HISTORY,                                       FriendConfig.DELETE);// Valid for strange users who have not been added to the contact.FriendConfig.hideItemsInContactConfig(FriendConfig.ADD_FRIEND);
```

Result of Contact Settings:

| Hide Partial Options | Hide All Options | Default |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b976082f8f4a11efa11a525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b974eb8b8f4a11efac345254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b97c475a8f4a11efa22452540055f650.png) |

Result of Users Not Yet Added to Contacts:

| Hide Adding Friends | Default |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b97dd70d8f4a11efac345254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b97825918f4a11efac345254002693fd.png) |


---
*Source: [https://trtc.io/document/65368](https://trtc.io/document/65368)*
