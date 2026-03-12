# Create Group Chat

This article will guide you through creating a group on TUIKit.

## Display Effect

After creating the group chat, you can start sending messages and interacting in the group. If you go back to the Conversation List at this time, you will find the group chat you just created:

| Created group successfully | Conversation List is updated |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f8bbe2442c7811ef9130525400bf8054.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f8c62d782c7811efa4f552540077de32.png) |

## Environment Requirements

- Xcode 10 or later
- iOS 9.0 or later

## Preconditions

Before building the interface, please ensure that you have completed the following 4 things:

1. Created an application in the console.
2. Created some user accounts in the console.
3. Integrated `TUIKit`.
4. Called the `TUILogin` `login` API to log in to the component.

> **Note:**All components use this API to log in. You can log in once every time you start the application.Please make sure that the login is successful, and we recommend that you do the following in the callback of successful login.

If you haven't completed the above 4 steps, please refer to the corresponding steps in [Getting Started](https://www.tencentcloud.com/document/product/1047/60521) first, otherwise you may encounter obstacles when implementing the following features.

If you have already completed them, please continue reading below.

## Creates a group

There are two prerequisites for manually creating a group on TUIKit:

1. Loading the conversation list. Please refer to the document: [Build Conversation List](https://www.tencentcloud.com/document/product/1047/61217#).
2. Added some contacts. Please refer to the document: [Add Contacts](https://www.tencentcloud.com/document/product/1047/61221#).

There are 3 more steps to follow:

1. On the loaded conversation list interface, click the `+` icon in the upper right corner to pop up a submenu and select `Create Group Chat`.
2. Select several group members. These members are the contacts you have added. If you have not added any contacts before, nobody will be available to select on this screen.
3. Set the group chat name, type, avatar, etc.

The effect is shown below:

| Click Create Group Chat | Select group members | Group Settings |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d3c32c1e2c7411efb0275254006c0558.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d3b398b42c7411ef97da5254007d9c55.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d3bbe0ac2c7411ef9130525400bf8054.png) |

## More practices

You can locally [run the TUIKitDemo source code](https://www.tencentcloud.com/document/product/1047/45913) to explore more interface implementations.

## Contact Us

If you have any questions about this article, feel free to join the [Telegram Technical Group](https://t.me/+EPk6TMZEZMM5OGY1), where you will receive reliable technical support.


---
*Source: [https://trtc.io/document/61223](https://trtc.io/document/61223)*
