# Virtual Background

TUIRoomKit has launched a Virtual Background feature, allowing users to set a blurry background during group meetings, hide the actual meeting environment, protect privacy, and add fun to the meeting. This article will introduce in detail how to use this feature in the TUIRoomKit component.

## Integration effect

After integrating the Virtual Background feature in the TUIRoomKit component, the display effect is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4cb971201bf411ef8bfe5254002fd0a8.png)

## Preparation Requirements

Before using Tencent Cloud's Virtual Background feature, you need to go to the Console to activate the group meeting service for your application, and purchase the **Advanced Interactive Version/Large Room Interactive Version** package. For specific steps, please refer to [Activate Service](https://www.tencentcloud.com/document/product/647/59973#).

## Enable Blurry Background

> **Note:****H5 is not supported, only applicable to Web PC.****You need TUIRoomKit v2.3.3 or later.**

TUIRoomKit's UI solution supports setting a virtual background. You can display the Virtual Background feature button on the UI by calling the [enableVirtualBackground](https://www.tencentcloud.com/document/product/647/54880#ac620717-1b58-42ed-b8a3-589bf0ad545e) interface. Clicking this button will enable the Virtual Background feature.

Vue3

Vue2

```
import { conference } from '@tencentcloud/roomkit-web-vue3';conference.enableVirtualBackground();
```

```
import { conference } from '@tencentcloud/roomkit-web-vue2.7';conference.enableVirtualBackground();
```

## FAQs

### No response or delay when activating virtual background?

- Make sure you have purchased the group meeting **Advanced Interactive Version/Large Room Interactive Version** package, see [Activate Service](https://www.tencentcloud.com/document/product/647/59973#) for details.
- When the network connection is poor, the virtual background model file may not have been completely downloaded, leading to the failure of activating the virtual background.

### Can I activate the virtual background with the camera off?

No.


---
*Source: [https://trtc.io/document/60533](https://trtc.io/document/60533)*
