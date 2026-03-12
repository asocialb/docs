# Switch Bluetooth Headset

## Feature Overview

When no Bluetooth headphones are connected, it supports only the selection of speaker and earpiece. If Bluetooth headphones are detected, switching between Bluetooth headphones, earpiece, and speaker is implemented by using the **Apple AVRoutePickerView** component.

> **Note:**Note: Currently, the switch function for Bluetooth headphones is only supported on the iOS platform.

## Usage

1. No Bluetooth headphones connected. Use the UI in TUICallKit to switch between speaker and earpiece. The UI adjustment is as follows.

| Earpiece | Speaker |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa9496c8662c11f09a9d52540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b59cb4a4662c11f0b5365254001c06ec.png) |

2. After connecting Bluetooth headphones, the style of the audio route selection button in TUICallKit changes. Click the button to awaken **AVRoutePickerView**, switch audio route from **AVRoutePickerView**, and the button name in TUICallKit will follow.

| Audio Route Toggle Button When Connecting Bluetooth Headphones | AVRoutePickerView |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7c77768662c11f088c4525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ef5ae3be662c11f088c4525400454e06.png) |


---
*Source: [https://trtc.io/document/72205](https://trtc.io/document/72205)*
