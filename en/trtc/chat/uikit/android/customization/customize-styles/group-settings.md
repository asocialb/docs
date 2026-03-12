# Group Settings

The following will guide you through how to hide group settings options.

## Hide group setting options

API Function: Hide group settings options. This setting is effective for all groups.

API prototype:

```
// GroupConfig.javapublic static final int MUTE_AND_PIN = 1;public static final int MANAGE = 2;public static final int ALIAS = 3;public static final int BACKGROUND = 4;public static final int MEMBERS = 5;public static final int CLEAR_CHAT_HISTORY = 6;public static final int DELETE_AND_LEAVE = 7;public static final int TRANSFER = 8;public static final int DISMISS = 9;@IntDef({MUTE_AND_PIN, MANAGE, ALIAS, BACKGROUND, MEMBERS, CLEAR_CHAT_HISTORY, DELETE_AND_LEAVE, TRANSFER, DISMISS})public @interface Items {}/** * Hide items in group config interface. */public static void hideItemsInGroupConfig(@Items int... items)
```

Sample code:

```
// When to call: Before initializing group setting interface. GroupConfig.hideItemsInGroupConfig(GroupConfig.MUTE_AND_PIN,                                   GroupConfig.MANAGE);
```

Result:

| Hide Partial Options | Hide All Options | Default |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b1b70c008f4a11efa11a525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b1b706af8f4a11efa11a525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b1b7002f8f4a11efa11a525400a9236a.png) |


---
*Source: [https://trtc.io/document/65367](https://trtc.io/document/65367)*
