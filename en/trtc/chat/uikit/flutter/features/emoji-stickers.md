# Emoji & Stickers

This document describe how to implement sticker module in Tencent Cloud Chat Flutter UIKIt.

Two types of stickers, are available in Message widget, shows in the following list:

| Sticker Type | MessageType | Integrate within Text | Sending Scheme | Rending Scheme | Usage | Default |
| --- | --- | --- | --- | --- | --- | --- |
| Small image | Text Message | Yes | Image name | The image is automatically matched against the local image assets by name. | **Enabled as default** , with one set of default packages, while adding new packages and cutmization are also support. | One set of default packages are provided, shown as the screenshots below. |
| Large image | Sticker Message | No | `baseURL` plus the image file name, which form the path of the emoji image asset | The asset resources are parsed based on the path. | Images are stored as assets, and are defined in `List` | - |

| **Name** | Small Image(Designed by us) | Tencent Large Image |
| --- | --- | --- |
| **Type** | Small image | Large image |
| **Description** | **Enabled as default**located at first | Not provided as default, this packages comes from customize configuration from our [Sample App](https://github.com/TencentCloud/chat-demo-flutter/tree/v2). |
| **Screenshots** | ![Figure 1](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/646d5566416511ee96d3525400088f3a.jpeg) | ![Figure 2](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/64a6dd21416511eeb231525400c56988.jpeg) |

## Usage

First, install the [tencent_cloud_chat_sticker](https://pub.dev/packages/tencent_cloud_chat_sticker) plugin:

```
flutter pub add tencent_cloud_chat_sticker
```

To enable the plugin, add the following code to the `plugins `list in `initUIKit`:

```
TencentCloudChatPluginItem(  name: "sticker",  initData: TencentCloudChatStickerInitData(    userID: TencentCloudChatLoginData.userID,  ).toJson(),  pluginInstance: TencentCloudChatStickerPlugin(    context: context,  ),)
```

In the `TencentCloudChatStickerInitData` object, you can select which default sticker sets to enable and add additional sticker sets to suit your needs.


---
*Source: [https://trtc.io/document/52227](https://trtc.io/document/52227)*
