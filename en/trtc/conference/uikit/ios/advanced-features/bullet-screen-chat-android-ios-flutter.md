# Bullet Screen Chat (Android & IOS & Flutter)

## Feature Introduction

The interactive Danmaku function supports the following features: sending barrage messages, inserting custom messages, customizing message styles, etc. Danmaku messages support emoji input, adding fun to the messages and making the interaction more pleasant.

## Usage Instructions

After you successfully [integrate TUIRoomKit](https://www.tencentcloud.com/document/product/647/54843) and successfully log in, you can use this feature. TUIRoomKit bullet screen supports the following features:

- Send/receive text or emoji messages.
- Hide the danmaku button.
- Bullet screen automatically disappears after 5 seconds.

| Danmaku Chat | Send emoji | Hide the danmaku (bottom bar: settings) |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5ca781620eab11f09ecc52540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/596c906b0eab11f09d28525400bf7822.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/832cc7960eaa11f0b3015254001c06ec.png) |

## Feature Customization

If the current UI does not meet your requirements, you can modify it by changing the source code to achieve the UI effect you are satisfied with. For different platforms, please refer to:

Android

iOS

Flutter

You can achieve the UI effect you are satisfied with by modifying the source code in the directory [Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/main/floatchat](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/main/floatchat). For easier UI customization, an introduction to the bullet screen file is provided here.

```
// Position: Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/main/floatchatFloatChat         âââ View   â   âââ MessageBarrageView.java       // Interface for each barrage message  â   âââ FloatChatSendView.java        // Input box interface for barrage sending  âââ TUIFloatChatButton.java           // Send button for barrage  âââ TUIFloatChatDisplayView.java      // Area for showing barrage messages
```

You can achieve the UI effect you are satisfied with by modifying the source code under the Source/Common/Components/FloatChat directory. For easier UI customization, an introduction to the bullet screen file is provided here.

```
FloatChat         âââ FloatChatButton.swift          // Barrage sending button  âââ FloatChatDisplayView.swift      // Area for showing barrage messages  âââ FloatChatInputController.swift      // Input box interface for barrage sending
```

The barrage chat component of Flutter is located in the [tencent_float_chat_widget](https://pub.dev/packages/tencent_float_chat_widget) plug-in. You can achieve the UI effect you are satisfied with by modifying the source code in the directory `tencent_float_chat_widget/lib/float_chat`. For easier UI customization, an introduction to the barrage file is provided here.

```
// File location: tencent_float_chat_widget/lib/float_chat
```

## Critical Code

Android

iOS

Flutter

### Core API

The Danmaku Chat component mainly provides two APIs:

[`TUIFloatChatButton`](https://github.com/Tencent-RTC/TUIRoomKit/blob/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/main/floatchat/TUIFloatChatButton.java): Pull up the barrage sending interface after clicking.

[`TUIFloatChatDisplayView`](https://github.com/Tencent-RTC/TUIRoomKit/blob/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/main/floatchat/TUIFloatChatDisplayView.java): Area for showing barrage messages.

In scenarios where you need to send danmaku, create a TUIFloatChatButton. Click to bring up the input interface.

```
TUIFloatChatButton button = new TUIFloatChatButton(mContext, roomId);mButtonContainer.addView(button);
```

In scenarios where you need to display danmu messages, use TUIFloatChatDisplayView to display danmu messages.

```
TUIFloatChatDisplayView view = new TUIFloatChatDisplayView(mContext, roomId);mLayoutDisplayViewContainer.addView(view);
```

The Danmaku Chat component is mainly divided into two parts:

**FloatChatButton**: Pull up the barrage sending interface after clicking.

**FloatChatDisplayView**: Area for showing barrage messages.

You can create these two components by yourself and place them in any position of the view.

```
let floatchatButton = FloatChatButton()floatchatButton.updateRoomId(roomId:"your room Id") // Set roomIdself.view.addSubView(floatchatButton)
```

```
let displayView = FloatChatDisplayView()self.view.addSubView(displayView)
```

In the bullet screen chat component ([tencent_float_chat_widget](https://pub.dev/packages/tencent_float_chat_widget)), the following classes are externally exposed:

- **FloatChatWidget**: Contains the bullet screen chat button and the bullet screen message display area. You can perform layout in the following ways where needed:

```
import 'package:tencent_float_chat_widget/tencent_float_chat_widget.dart';                       FloatChatWidget(roomId: yourRoomId)  // Layout where you need, input the roomId of the room for sending and receiving messages.
```

- **InputWidget**: The input box for sending bullet screen chat messages. You need to lay it out on the topmost layer of the `Stack` in the page you are laying out to prevent it from being covered by other components. Once the layout is completed, it is not shown by default. Once you click the bullet screen chat button in **FloatChatWidget**, the input box and keyboard will pop up automatically **.**

```
import 'package:tencent_float_chat_widget/tencent_float_chat_widget.dart';Stack(    children: [      ...yourWidget,        // Another one of your widgets, here as an example      const InputWidget(),  // Input box for sending bullet screen chat messages    ],)
```

- **FloatChatManager**: The class provides a deleteStatus() method. When you log out of the current room, this method must be called to clear the bullet screen chat status.

```
import 'package:tencent_float_chat_widget/tencent_float_chat_widget.dart';FloatChatManager().deleteStatus();
```

> **Note:**If you have any requirements or feedback during the integration and use process, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/68975](https://trtc.io/document/68975)*
