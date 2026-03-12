# Step One: Incorporate Input Sources

The Cloud Streaming Services console provides the Live Video Caster (LVC) system. This document describes how to use LVC for online broadcasting after activating the LVC feature.

> **Note:**Billable items of LVC include broadcast output duration and third-party relay. Billing is based on usage duration. For more information, see [Live Video Caster Pricing Overview](https://www.tencentcloud.com/document/product/267/58538).To avoid incurring unnecessary charges when you are not using a caster, click **Stop**for the caster on the [Live Video Caster list page](https://console.tencentcloud.com/live/caster?rid=5). For detailed procedures, see [Managing Live Video Caster](https://www.tencentcloud.com/document/product/267/58533).LVC is incompatible with Internet Explorer and Firefox browsers. We recommend using Chrome.

## Use Limits

- Each account can create up to **five**LVC instances. If there are already five instances under your account, you must delete an existing instance before you can add a new one. To add more instances, please [submit a ticket](https://console.tencentcloud.com/workorder/category).
- You can add up to **five**VOD files to the VOD input playback list.
- Third-party relay supports up to three streams, one of which is relayed to the current CSS account by default, and the other two can be relayed to third-party vendors. For more information, see [Relay](https://www.tencentcloud.com/document/product/267/58530#.E6.AD.A5.E9.AA.A44.EF.BC.9A.E7.9B.B4.E6.92.AD.E8.BD.AC.E6.8E.A8).

## Preparations

1. Make sure you have already activated [CSS](https://console.tencentcloud.com/live/livestat).
2. Make sure you have added a **Push**domain and a **Playback**domain in [Domain Management](https://console.tencentcloud.com/live/domainmanage) and completed the CNAME configuration for both domains.
3. Go to the [Live Video Caster](https://console.tencentcloud.com/live/caster?rid=5) page in the CSS console to enter the LVC activation page. Check the box agreeing to the [Tencent Cloud Terms of Service](https://www.tencentcloud.com/document/product/301/9248?has_map=1) and [LVC Billing Overview](https://www.tencentcloud.com/document/product/267/58538?has_map=1). Click **Activate**to activate LVC.
4. Make sure you have [created a Live Video Caster](https://www.tencentcloud.com/document/product/267/58533#.E6.96.B0.E5.BB.BA.E5.AF.BC.E6.92.AD.E5.8F.B0) in the **Live Video Caster** page.

## Operation Steps

1. Log in to [Live Video Caster](https://console.tencentcloud.com/live/caster?rid=5) and view the Live Video Caster list.
2. Find the caster you want to edit and click its **ID** or click **Open** on the right to enter the caster editing page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c6d75097dc8211f08a7a52540099c741.png)

3. In the input source area, click **Add input** to add a video input.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a490ed47dc8511f09143525400bf7822.png)

4. In the window that pops up, set the input type and enter the URL of the source video. The following four input types are available:

Live

On demand（Support editing）

lmage

Publish local stream

Dynamic Overlays

![](https://staticintl.cloudcachetci.com/cms/backend-cms/92d83b0d94e811eea869525400c26cb9.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8004cfc419e311f09240525400bf7822.png)

**Add input**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/44935e806c4811f08eae52540044a08e.png)

**Edit input**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7323e9176c4911f088f3525400e889b2.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a88095f594e811eebd87525400c40977.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2bcb65041e7a11f0ac5352540044a08e.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f0b2839c854a11efaee3525400bdab9d.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/69d6d72320de11f0b21052540099c741.png)

| Input type | Description |
| --- | --- |
| Live | Input name: CustomInput type: **Live****Pull from URL**: The live stream is pulled from a URL to LVC. The RTMP, HLS, SRT, and HTTP-FLV protocols are supported.**Publish**: Media files are pushed to LVC using the RTMP protocol. |
| On demand | Input name: CustomInput type: **On demand URL**. Click **Add URL**.Supports media files stored in Tencent Cloud COS and media files stored by other providers.Supports the MP4, HLS, and FLV formats.You can enter multiple on-demand file URLs separated with semicolons (;). The console automatically cycles through the files in the list. |
| Image | Input name: CustomInput type: **Image****Image URL**: Supports JPEG, JPG, PNG, and BMP images not larger than 1920x1080 pixels.**Local image**: Supports uploading PNG, JPG, and JPEG images not larger than 5MB. |
| Publish local stream | Input name: CustomInput type: **Publish local stream****Screen Sharing**: The input can be a shared screen (an application window or desktop). Supported resolutions include 1920x1080, 1280x720, 640x480, and 640x360.**Publish from camera**: Supports using the local camera as an input source, supporting resolutions of 1920x1080, 1280x720, 640x480, and 640x360.In the local camera streaming scenario, the beauty effect feature is turned off by default. According to your business needs, you can choose to manually turn this feature on or off.Parameter adjustment: You can customize the beauty effect parameters to improve your personal appearance.Various personalized settings are provided to meet your special needs, including:Beauty Effects and Makeup: These can help to clear skin blemishes, enhance skin texture, and add various makeup effects.Filters and Stickers: You can add various fun filters and stickers.Background and Emoji: You can change the video background or add emojis.Virtual Avatars: You can transform your appearance into various virtual avatars. |
| Dynamic Overlays | Input name: CustomInput type: Dynamic OverlaysBased on your business needs, you can overlay Dynamic Overlays on the live stream from the broadcasting side. You can go to [Dynamic Overlays](https://console.tencentcloud.com/live/config/material) to create them to add a scoreboard, a caption or other effects. |

> **Note:**Ensure that each on-demand/live URL you input is accessible. Otherwise, the input will not be playable.If the input source is interrupted, the output will display a black screen.

5. Click **Confirm**to finish adding the input source. The system will automatically play the video.

> **Note:**To **modify an input source**, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/c332cbfba30b11eea869525400c26cb9.png) at the bottom of the input source to enter the input source editing page, fill in the information you need to modify, and click **Confirm** to save the modification.![](https://staticintl.cloudcachetci.com/cms/backend-cms/f97c39676ceb11f096685254001c06ec.png)After modification, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/c337a770a30b11ee8964525400321be2.png) in the lower-left corner of the video source to refresh. After refreshing, you can see the modified input source displayed.![](https://staticintl.cloudcachetci.com/cms/backend-cms/1092d7c66cec11f09e39525400454e06.png)To **delete an input source**, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/c33e921da30b11eeb6c6525400e46040.png) on the top of the input source. A dialog box pops up asking for confirmation. Click **Confirm** to delete the input source.![](https://staticintl.cloudcachetci.com/cms/backend-cms/2c8856ce6cec11f096685254001c06ec.png)When you modify or delete an input source, the input source cannot be used in a preview (PVW) or main monitor (PGM) layout.


---
*Source: [https://www.tencentcloud.com/document/product/267/58532](https://www.tencentcloud.com/document/product/267/58532)*
