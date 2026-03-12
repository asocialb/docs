# Basic Beauty

TUIRoomKit introduces a basic beauty feature that enables users to optimise their peeling, whitening and rosy effects when conducting multi-person conferences, enhancing the visual experience of video conferences and adding interest to them. This article will detail how to use this feature in TUIRoomKit components.

## Integration effects

After integrating the basic beauty feature in the TUIRoomKit component, the display looks as follows:

| **Close**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/14aa8e517c7811ef82535254002693fd.png) | **Smoother**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5b998c627c7811efb9d8525400f69702.png) |
| --- | --- |
| **Whitening**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/91ae28f97c7811efa87e52540055f650.png) | **ruddy**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9f5d03ce7c7811ef852f52540075b605.png) |

## Terms of preparation

Before you can use the basic beauty features provided by Tencent Cloud, you need to go to the console and enable the multiplayer conferencing service for the app. See [Enabling the service](https://www.tencentcloud.com/document/product/647/59973#da1ae48d-e664-4486-bb5c-ed5aa89a8180) for specific steps.

## Turn on basic beauty

> **Note:****H5 is not supported at this time, only for Web PC.****Requires TUIRoomKit v2.6.2 and above.**

TUIRoomKit's UI scheme supports setting basic beauty by default. If you don't need to show the basic beauty function, you can hide the basic beauty UI with the following code:

Vue3

Vue2

```
import { conference, FeatureButton } from '@tencentcloud/roomkit-web-vue3';conference.hideFeatureButton(FeatureButton.BasicBeauty);
```

```
import { conference, FeatureButton } from '@tencentcloud/roomkit-web-vue2.7';conference.hideFeatureButton(FeatureButton.BasicBeauty);
```

## Common problems

### No response or delay in turning on basic beauty?

When the network is poor, the basic beauty model file may not finish downloading, which may cause failure to open the basic beauty.

### Can I turn off the camera and be able to turn on basic beauty?

Can't.


---
*Source: [https://trtc.io/document/64689](https://trtc.io/document/64689)*
