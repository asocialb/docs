# Text Watermark

TUIRoomKit has launched the Text Watermark feature, allowing users to set text watermarks during group meetings. This article will detail how to use this feature within the TUIRoomKit component.

## Integration effect

After integrating the Text Watermark feature in the TUIRoomKit component, the display effect is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ddfb5b621bf211ef942e525400720cb5.png)

## Preparation Requirements

Before using Tencent Cloud's Text Watermark feature, you need to go to the Console and activate the Group Meeting service for your application. For specific steps, please refer to [Activate Service](https://www.tencentcloud.com/document/product/647/59973#).

## Enable Text Watermark

> **Note:****The Mini Program Platform does not support this feature yet, but both the Electron and Web versions are supported.****You need TUIRoomKit v2.3.3 or later.**

TUIRoomKit offers the Text Watermark feature. You can enable this feature by calling the [enableWatermark](https://www.tencentcloud.com/document/product/647/54880#daceee1b-175d-41a1-b495-d158fe01d63c) interface.

Web

Electron

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-web-vue2.7import { conference } from '@tencentcloud/roomkit-web-vue3';conference.enableWatermark();
```

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.enableWatermark();
```

## FAQs

### 1. Why does the page style appear abnormal after enabling Text Watermark?

Please check the parent element with **id 'roomContainer'**, and confirm its `style` is set to: `width: 100%; height: 100%; overflow: hidden;`.

Web

Electron

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-web-vue2.7import { conference } from '@tencentcloud/roomkit-web-vue3';conference.enableWatermark();
```

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-electron-vue2.7import { conference } from '@tencentcloud/roomkit-electron-vue3';conference.enableWatermark();
```


---
*Source: [https://trtc.io/document/60531](https://trtc.io/document/60531)*
