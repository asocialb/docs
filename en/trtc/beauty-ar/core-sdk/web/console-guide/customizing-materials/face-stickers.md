# Face Stickers

You can upload a PNG file or PNG sequence frames to the console to create your own face-tracking stickers.

![ç´ æä¿¡æ¯](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/34af7606e01611edbd56525400088f3a.gif)

## Limits

| Requirement | Description |
| --- | --- |
| Format | For static stickers, upload a single PNG image. For animated stickers, upload a sequence of **numbered** PNG images, such as `001.PNG`, `002.PNG`. |
| Dimensions | 1000 x 1000 px or smaller is recommended. |
| Frame count | 100 frames or fewer. |
| Size | A single image should not exceed 1 MB. |

## Directions

### Step 1. Create your material

### Step 2. Import the material to the console

2. In the **Choose material** area of the **Parameter configuration** panel on the right, upload your material by either drag & drop or browse.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/37488b04e01611ed95af525400c56988.png)

### Step 3. Modify the parameters

- In the main panel, drag the sticker image to position it in relation to the face.
- In the parameter configuration panel on the right, change settings including the **blend mode**, **strength**, **playback speed** (for sequence frames), and **anchor point**.

> **Note**We do not recommend setting the playback speed higher than 30 fps.**Anchor point** is the reference point for the sticker, which is the center of the sticker image by default. X and Y indicate the horizontal and vertical distances (in percentage) of the anchor point from the top left corner of the sticker image. For example, the default anchor point is (0.5, 0.5). If you want to use the top left corner of the sticker as the anchor point, set the parameter to (0, 0). A well-chosen anchor point makes for better tracking effects. For example, for headdress stickers, an anchor point in the forehead is recommended, and for stickers such as glasses, an anchor point along the nose bridge is recommended. You can keep exploring to find the best anchor point for your sticker.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/49347317e01611edbd56525400088f3a.gif)

### Step 4. Preview the material

In the preview window on the right, you can preview your sticker on a built-in photo or on your device's camera.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/643d6585e01611edbd56525400088f3a.png)


---
*Source: [https://trtc.io/document/54299](https://trtc.io/document/54299)*
