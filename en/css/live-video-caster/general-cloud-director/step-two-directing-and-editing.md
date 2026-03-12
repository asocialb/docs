# Step Two: Directing and Editing

LVC lets you direct and edit video layouts, audio, watermarks, and standby videos and images, as well as create program schedules. These features can enrich your live stream content.

## Step 1: Setting a Directed Video Frame Size

After you finish [adding video input sources](https://www.tencentcloud.com/document/product/267/58532) for your caster in Live Video Caster, you can set the frame size for each video output.

The size settings will affect the output size of input sources, template layouts, and custom layouts.

LVC comes with built-in landscape and portrait mode output size templates for live streaming on Weixin Channels. It also supports custom output sizes.

1. In the [Live Video Caster](https://console.tencentcloud.com/live/caster?rid=5) list, find the caster you want to edit and click its **ID** or click **Open** on the right to enter the caster editing page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ca9aa185dc8511f0a6e3525400e889b2.png)

2. On the caster editing page, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/fa4b4181230f11efa0b8525400db4520.png) in the upper-right corner.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0a149ae5dc8611f0a6e3525400e889b2.png)

3. Click **Publish** to enter the settings page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/88194a751e8b11f099e05254005ef0f7.png)

4. Configure the following items in the **Output video** section:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a82cff091e8b11f091155254007c27c5.png)

| Configuration Item | Description |
| --- | --- |
| Video width | Value range: The long side and short side of the video must not exceed 4096 x 2160 pixels. If you need to customize the width and height, both are required. |
| Video height | Value range: The long side and short side of the video must not exceed 4096 x 2160 pixels. If you need to customize the width and height, both are required. |
| Frame rate | Value range: Less than or equal to 60fps. |
| Video bitrate | Value range: Less than or equal to 10,000kbps. |
| Audio bitrate | Options: 128kbps, 192kbps, and 256kbps. |

> **Note:**If only one stream is published and the parameters above are not specified or are 0, the parameters of the original stream will be used. If more than one stream is published and the parameters above are not specified or are 0, the output resolution will be 720p.

## Step 2: Configuring a Layout

1. Click **Add layout** in the layout component of the function area to enter the layout creation page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/20845e92dc8611f08d525254001c06ec.png)

2. Select a layout style and create the corresponding layout:
  - Select a [template layout](https://www.tencentcloud.com/document/product/267/58531#.5B.5D(id.3Atemplate).E6.A8.A1.E6.9D.BF.E5.B8.83.E5.B1.80).
  - Select a [custom layout](https://www.tencentcloud.com/document/product/267/58531#.5B.5D(id.3Acustomize).E8.87.AA.E5.AE.9A.E4.B9.89.E5.B8.83.E5.B1.80).
3. The layout you created is displayed in the layout component area.
4. Click the successfully added layout to push it to the preview (PVW) window.

> **Note:**LVC comes with five layout templates. Select an appropriate template based on your needs or customize a layout.The layout that is currently in use in PVW is marked by a green frame. The layout currently in use in PGM is marked by a red frame. Layouts in use cannot be edited or deleted.To edit a layout template, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/aab28150b11011eeae9a525400c26da5.png) in the lower-right corner of the layout.To delete a layout template, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/9f3b7340b11111eeae9a525400c26da5.png) in the upper-right corner of the layout.![](https://staticintl.cloudcachetci.com/cms/backend-cms/c7ce3f32231011efa62352540003d080.png)

### Layout Guide

LVC supports multiple layout modes in different output sizes.

- Landscape mode:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b338bd966cef11f09f3d52540099c741.png)

- **Portrait mode**: To use the portrait layout for output, click **Set** in the upper-right corner of the main page to enter the page for changing the [output size](https://www.tencentcloud.com/document/product/267/58531#output_size).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d3174e816cef11f0b9a25254007c27c5.png)

### Template Layout

LVC comes with five built-in templates. You may select a template based on your needs, as detailed below:

1. Click to select the layout template you want to use.
2. Click the **Select an input** drop-down list to select input sources.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/50a487ea6cf011f084fc525400bf7822.png)

3. After selecting input sources, you can preview your video in the preview box.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7ea128e66cf011f0b9a25254007c27c5.png)

4. Click **Confirm** to complete the creation of the layout.

### Custom Layout

LVC allows you to customize the arrangement, stacking order, and sizes of input sources and drag and drop them as needed.

1. Click **Custom layout** and click **Add** to add input sources.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9bd33c146cf011f087e15254005ef0f7.png)

> **Note:**You can add a maximum of four input sources; to remove an input source, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/b8b44cb2a46211eeb0fd525400170219.png).

2. Adjust the layout of the input sources:
  - Click and hold the mouse button while dragging to adjust the sizes and positions of input sources.
  - Click **Front** or **Back** to adjust the stacking order of the input sources.
3. Click the **Select an input** drop-down list to select input sources. After selecting input sources, you can verify the video effect in the preview window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bf6dfd9f6cf011f0bcac525400e889b2.png)

4. Click **Confirm** to complete the creation of the layout.

## Step 3: Starting Preview

View the video input source area and click an added input source or a created layout template to start preview (PVW).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fd6928f46d1e11f09f3d52540099c741.png)

> **Note:**The layout currently in use in PVW is marked by a green frame. An input source or layout in use cannot be deleted directly. To delete a layout in use, manually close PVW or PGM or stop the caster first.

## Step 4: Setting Audio

- LVC allows you to adjust the volume of each input stream in the output stream. When the **Switch audio and video together** box is checked, the audio and video in the PVW playback are from the same input source. For example:
  - If PVW is playing the video from input source 1, the audio being played is also from input source 1. If PVW is playing a mixed stream of video from input sources 1 and 3, the audio being played is also a mix of audio from input sources 1 and 3.
- When the **Switch audio and video together** box is unchecked, audio and video can be selected separately. For example:
  - If the video from input source 1 is being played, you can choose to play the audio from input source 3. If a mixed stream of video from input sources 1 and 3 is being played, you can choose to play the audio from input source 1 only.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0e6ac3cc6d1f11f084fc525400bf7822.png)

## Step 5: Adding a Component

### Watermarking

#### Creating a Watermark Template

LVC supports multiple watermark overlays. To add a watermark in your directed footage, follow these steps:

1. Select the Watermark tag and click **Add** to enter the watermark creation page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/68ec3ea26cf111f096685254001c06ec.png)

2. Click **Upload** to upload your watermark image.

> **Note:**The watermark image can be in PNG, JPG, JPEG or GIF format, with a maximum size of 2M and a width and height not exceeding 1024px. Dynamic watermarks are supported.After the upload, you can position the watermark by dragging it or specifying its coordinates for a higher positioning precision.

3. Adjust the position and size of the watermark image by dragging the image on the editing screen or clicking ![](https://staticintl.cloudcachetci.com/cms/backend-cms/b8c05b9ea46211eeb0fd525400170219.png) to **enter coordinates manually** and entering the precise pixel values.
4. Customize a name for the watermark.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b352d45b6cf211f081ce52540044a08e.png)

> **Note:**To enter coordinates manually, you must start preview (PVW) first.

5. After the adjustment, you can click **Preview** to view the watermark effect.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ddfbfa1c6cf211f087e15254005ef0f7.png)

6. When you are finished, click **Confirm**to save the watermark template.
7. Select the watermark template you want to enable, and click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/b8ca1301a46211eebf3d525400bb593a.png) to turn on the **PVW window**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/025073136cf311f096685254001c06ec.png)

8. The watermark is displayed in the PVW window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1f25421a6d1f11f0bcac525400e889b2.png)

#### Editing a Watermark Template

1. Select a watermark template you created and click **Edit** on the right to modify the template data.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3bfe653f6cf311f0b9a25254007c27c5.png)

2. Adjust the watermark template based on your business requirements. After the adjustment, click **Confirm**.

#### Deleting a Watermark Template

> **Note:**If a watermark template is in use, it cannot be deleted.

1. Select a watermark template you created and click **Delete** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/572c6bc26cf311f09e39525400454e06.png)

2. Click **Confirm**to delete the template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/55289ba8231111ef860b52540049c929.png)

#### Close a Watermark Template

Select a watermark template you created and click **Close** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7e83ec226cf311f09f3d52540099c741.png)

### Adding Text

#### Creating a Text Template

LVC supports multiple text overlays, as well as text and watermark overlays. To add text in your directed footage, follow these steps:

1. Select the Text tab and click **Add** to enter the text creation page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/02a9f2a66cf611f0bcac525400e889b2.png)

2. Configure the following items based on your business requirements:

Text

Time

![](https://staticintl.cloudcachetci.com/cms/backend-cms/52cc2e846cf611f087e15254005ef0f7.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/77fa8f816cf611f084fc525400bf7822.png)

| Configuration Item | Description |
| --- | --- |
| Type | The default is **Text,**  and you can also select **Time**.Text:Enter the text to be displayed.Time:Set the type to either Time or Date + Time. |
| Font | Options: Songti and Heiti. |
| Size | Value range: 16 to 60. |
| Font color | Customize the font color according to your preference. |
| Position | Drag and drop the text to adjust its position. |
| Display | Options:  **Fixed position**, **Scroll** and **Single Scroll**. |

3. After the editing, click **Confirm** to save the text template.
4. Select the text template you want to enable, and click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/b8f663dca46211eebf3d525400bb593a.png) to turn on the **PVW window**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8ffe8fde6cf611f0b9a25254007c27c5.png)

5. After the PVW window is turned on,The text is displayed in the PVW window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/301cb18c6d1f11f0bcac525400e889b2.png)

#### Editing a Text Template

1. Select a text template you created and click **Edit** on the right to modify the template data.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c7b8338b6cf611f096685254001c06ec.png)

2. Adjust the text template based on your business requirements. After the adjustment, click **Confirm**.

#### Deleting a Text Template

> **Note:**If a text template is in use, it cannot be deleted.

1. Select a text template you created and click **Delete** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e186e5486cf611f09e39525400454e06.png)

2. Confirm whether to delete the text template. Click **Confirm** to delete it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a76d40ce231111ef90c35254006d3582.png)

#### Close a Text Template

Select a text template you created and click **Close** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ffb71c266cf611f084fc525400bf7822.png)

### Adding Subtitles

#### Adding a Subtitle Template

1. Select the subtitle tag, and then click  **Add**  to enter the subtitle adding page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1947b0066cf711f09f3d52540099c741.png)

2. Based on your business requirements, proceed with the following configurations:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4da843266cf711f09e39525400454e06.png)

| Configuration Item | Description |
| --- | --- |
| Subtitle Remarks | You can customize the subtitle remarks according to your needs. |
| Title Content | You can customize the title content according to your needs, which contains up to 20 characters.The title bar is displayed by default. You can manually uncheck it to hide the title bar. |
| Title Font | The default title font is  **Songti** . You can also select **Heiti**. |
| Title Font Size | The font size range is from 12 to 60.You can select a font color according to your preference. |
| Title Background | The default style is  **Modern Minimalist** . You can also select the  **Youthful and Lively**  style.You can select a title background color according to your preference. |
| Subtitle Content | You can customize the subtitle content according to your needs, which contains up to 512 characters.After the subtitle content is entered, the preview page will show the effect. |
| Subtitle Font | The default subtitle font is  **Songti** . You can also select **Heiti**. |
| Subtitle Font Size | The font size range is from 12 to 60.You can select a font color according to your preference. |
| Subtitle Background | The default style is  **Modern Minimalist** . You can also select the  **Youthful and Lively**  style.You can select a subtitle background color according to your preference. |
| Display | The default is **Fixed position**. You can also select **Scroll** or **Single Scroll**.The **Scroll** and **Single Scroll** modes both support setting the scrolling speed.The default speed is 5 seconds/line, namely the time for a character to scroll from right to left.The adjustable speed range is 5-600 seconds/line. |
| Position | On the preview page, you can drag and drop the text to adjust its position. |

3. After editing is completed, click  **Confirm**  to save the subtitle template.
4. Select the subtitle template you want to enable, and click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/c0d2b142231411efb2cb5254006568c0.png) to turn on the  **PVW window** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6d5a1d6b6cf711f096685254001c06ec.png)

5. After the PVW window is turned on, subtitles will be displayed in the left PVW.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4379420f6d1f11f084fc525400bf7822.png)

#### Modifying a Subtitle Template

1. Select the subtitle template you created, and click  **Edit**  on the right to modify the template information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9ca128726cf711f09f3d52540099c741.png)

2. Adjust the subtitle template according to your actual business needs. After the adjustment is completed, click  **Confirm** .

#### Deleting a Subtitle Template

> **Note:**If a subtitle template is in use, it cannot be deleted.

1. Select the subtitle template you created and click  **Delete**  on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b20085566cf711f09f3d52540099c741.png)

2. To confirm the deletion of the current subtitle template, click  **Confirm**  to delete it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c0e763e0231411ef90c35254006d3582.png)

#### Close a Subtitle Template

Select the subtitle template you created and click **Close**on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d58c41e16cf711f09e39525400454e06.png)

### Adding a Transition

LVC offers a variety of transition effects. Click any transition template to use it. Once selected, the transition effect will appear the next time video sources are switched.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ee9cf3916cf711f0bcac525400e889b2.png)

## Step 6: Adding a Standby Video or Image

### Adding a Standby Video

A standby video serves as an auxiliary input source. LVC automatically switches to the auxiliary input source when your live stream is interrupted unexpectedly.

> **Note:**If the standby video function is enabled, when the input source or pulled stream for the PGM (primary stream) fails or is interrupted, LVC automatically switches to the standby video. Once the primary stream recovers, LVC switches back to the primary stream.

Set this function by following these steps:

1. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/51e0dab1a48311eebf3d525400bb593a.png) in the upper-right corner, select **Standby Settings**to enter the configuration page, and click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/b901b50ca46211eeb76e525400461a83.png) to enable standby video.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dc9fe7a51fef11f0b2bc525400454e06.png)

2. Set the input type and fill in the corresponding URL. **On demand URL** and **Live URL** are supported.
3. After the configuration, click **Confirm** to save the settings.

> **Note:**If added successfully, the video can be previewed in this window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fd2da8201fef11f08ca05254005ef0f7.png)

### Adding a Standby Image

A standby image serves as an auxiliary image input source. LVC automatically switches to the auxiliary input source when your live stream is interrupted unexpectedly.

> **Note:**If the standby video function is not enabled, when the input source or pulled stream for the PGM (primary stream) fails or is interrupted, LVC automatically switches to the standby image. Once the primary stream recovers, LVC switches back to the primary stream.If a standby video and standby image are both enabled, LVC switches to the standby video first. If the standby video also fails, LVS switches to the standby image.

Enable the standby image function by following these steps:

1. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/e911b0a2a48311eebf3d525400bb593a.png) in the upper-right corner, select **Standby Settings** to enter the configuration page, and click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/b91959d3a46211eebd03525400c26da5.png) to enable standby image.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/41a867c01ff011f0b2bc525400454e06.png)

2. Click **Upload** and select and upload a local image.

> **Note:**The maximum image size is 5MB. The PNG, JPG, and JPEG formats are supported.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/94e984f06cf811f084fc525400bf7822.png)

3. Click **Confirm** to save the settings.


---
*Source: [https://www.tencentcloud.com/document/product/267/58531](https://www.tencentcloud.com/document/product/267/58531)*
