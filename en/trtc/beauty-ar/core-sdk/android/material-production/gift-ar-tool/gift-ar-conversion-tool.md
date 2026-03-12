# Gift AR Conversion Tool

This document mainly introduces the Tencent Gift AR and the method of use of the corresponding Gift AR Conversion Tool. Through this document, you will learn how to use this tool.

## Introduction

The Gift AR Conversion Tool (TEP Tools) is a material generation and conversion tool created specifically for Gift AR. It supports converting PNG frame sequences, SVGA, WebP animations, PAG animation files, and Lottie into.mp4 or.tcmp4 formats supported by the effect player.

> **Note:**The Gift AR Conversion Tool currently only supports MacOS 14 and above systems, and supports x86 and arm64 architectures. Please use the corresponding system to proceed with subsequent installation and use.

## Download

You can download the Gift AR Conversion Tool to your local system from [TEP Tools](https://mediacloud-76607.gzc.vod.tencent-cloud.com/MediaX/TEP/download/TEP_Tool_Latest.zip). After download completion:

1. Decompress the TEP_Tool_Latest.zip package to get the Gift AR Conversion Tool. After decompressing it, as shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/33154cf2d15a11ef82a5525400e889b2.png)

2. If your Mac's processor is Intel architecture, double-click `x86_app/teptool` to open; if your Mac's processor is Apple Silicon architecture, double-click `arm64_app/teptool` to open.

You can confirm the processor architecture of your Mac by running `uname -m` in the terminal.

3. On first run, computer authorization is required (a pop-up prompt will indicate that it cannot be opened). Authorization steps: System Preferences > Security & Privacy > General tab > click "Open Anyway".
4. Once authorized, reopen it to operate normally.

> **Note:**When opening the teptool, a prompt appears: "teptool" is damaged and cannot be opened. You should move it to the Trash.At this point, execute the init.sh file under the folder after decompression. When the console output shows: `Init executed successfully!`, reopen it to operate normally.

## Main Interface of the Tool

The main interface can be divided into a feature operation area and a log output area, as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3084dabdfe2611efbf88525400e889b2.png)

Before using the effect player, you will obtain an issued effect player License from Tencent Cloud. Therefore, at this point, you can fill in the obtained appId and LicenseKey information into the corresponding columns in the tool. This information will be used to encrypt and generate the effect file, enhancing the security of the effect file.

> **Note:**If you have multiple packageNames or bundleIds, please use English commas to concatenate them, for example: `com.packagName1,com.packagName2,com.packagName3`.

## Basic Configuration Item Description

- **fps:** Define the frame rate for material playback.
- **alpha scale:** Whether to scale the video alpha area (default scaling is 0.5). Currently, options are: scale 0.5; no scaling 1. Scaling the video can eventually reduce the video resolution and improve compatibility.
- **resource:** source file format.

## Convert PNG Frame Sequence to TEP Mp4

We have provided a batch of test materials. You can download them and perform conversion tests. [Click to download materials](https://mediacloud-76607.gzc.vod.tencent-cloud.com/MediaX/TEP/material/TepToolTestMaterial.zip).

### Ordinary Animation

Video frame naming method: 000.png, 001.png... 099.png increase successively. For frame image naming, see as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/59d4c9e7d17511ef8c8a525400454e06.png)

> **Note:**The first frame must be **000.png**; otherwise, it will be unable to generate normally.

**frames path:**location of video frames; click "choose" to select the folder path where the video frames are located.

If there is any audio, perform the next operation:

Click "audio(mp3)" to add the audio file of effects. Currently supports mp3 files.

After completing the above configuration, click the create TEP button at the bottom to start generation of TEP materials.

### Fusion Animation

click **add** to add the mask information of the fusion animation. The meanings of the configurations are as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2cdd063efe2711ef8c825254001c06ec.png)

- id: Flag of the fusion animation, equivalent to an integer flag of the current resource. When playing the fusion animation, different bitmap or text can be returned for display based on different id values. This value does not support customization and is auto-incremented internally.
- source tag: Flag of the fusion animation, equivalent to a string flag of the current resource. When playing the fusion animation, different bitmaps are returned for display based on different tags.
- source type: Refers to the attribute type of the fusion animation. Currently, two methods are supported. Image indicates a fusion animation of the image type; text indicates a fusion animation of the text type.
- fit type: The way of image display. Currently, two methods are supported: fitXY (tiling the image, default) and centerCrop (proportional scaling). These concepts are the same as those of the image alignment mode in Android.
- text color: If it is a text type, this attribute configuration exists. It indicates the text color. The format is: #RRGGBB.
- alignment: If it is a text type, this attribute configuration exists. It indicates the centering method of the text. Valid values: NONE (use the SDK default centering method, that is, finally displayed in the center); LEFT (displayed on the left); CENTER (displayed in the center); RIGHT (displayed on the right).
- font size (px): If it is a text type, this attribute configuration exists. It indicates the text size, and the unit is pixel px. If 0 is filled in, it means allowing the SDK to adaptively calculate the text size; if a value larger than 0 is filled in, the text will be displayed based on the filled text size value.
- text Bold: If it is a text type, this attribute configuration exists. Set whether the text is bold.
- mask path: path to the mask image. Click the choose button to select the corresponding mask image path.

#### Mask Image Description

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/090aaef9d17911ef82a5525400e889b2.png)

(1) in figure indicates a group of image masks. The black frame area is used to indicate the area where the fusion animation is displayed. (2) represents the content of the corresponding video frame.

> **Note:**Naming rules for mask files, which are the same as those for video frames, such as: 000.png, 001.png... 099.png. The file name indicates which frame the current mask belongs to.The size of the mask frame must match that of the video frame.Mask content: The black area indicates the position where the image (text) needs to be displayed. The transparency of other areas must be 0 (the red in the black area indicates the obstruction area).Use a rectangle for the mask area. It is recommended that the width and height of the mask area do not exceed 1/2 of the width and height of the mask frame.

Rendering

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/42739304d17911ef82a5525400e889b2.png)

## SVGA to TEP Mp4 Conversion

Support converting SVGA into TEP mp4 files individually and in batch. For batch conversion, please select a folder.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/36a1623afe2711efbf88525400e889b2.png)

- **resource: Select svga.**
- **svga file: Click "choose" to select the folder path where it is located. When there are many svga files, batch conversion can be adopted; check "patch convert" to indicate batch conversion.**
- dynamic item: Fusion animation material addition, which can be dynamically replaced at runtime and supports two formats: image and text.

You can preview and extract the imageKey from the Svga fusion animation through [online Web Svga Tools](https://www.nangonghan.com/svga/). The extraction method is as follows:

### Procedure 1: Drag the Svga Fusion to the Preview Area

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1b6932504d8611f0a6ac525400bf7822.png)

### Procedure 2: Copy ImageKey

Click "Download Image Resources & Copy ImageKey", and Click "Copy ImageKey" in the Image Resource Asset.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8dc17d4e4d8611f0a6ac525400bf7822.png)

## Convert WebP to TEP Mp4

Support converting WebP animated images into TEP mp4 files. Support individual and batch conversion.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3f6955ddfe2711ef8c825254001c06ec.png)

## PAG to TEP Mp4 Conversion

Support converting PAG into TEP mp4 files. Support individual and batch conversion.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/47715504fe2711efa49152540044a08e.png)

## Lottie to TEP Mp4 Conversion

Support converting Lottie into TEP mp4 files. Support individual and batch conversion.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d52a64afe2711ef8c825254001c06ec.png)

## Preview Animation

You can use [Gift AR Preview Tool](https://www.tencentcloud.com/document/product/1143/70542#) to quickly preview/accept the animation effect. Ensure the animation effect is correct before configuring and distributing it, and then play it in the Mobile SDK.

## FAQ

### Note: Video Resolution Exceeds 1504. What Should Be Done?

During the switching process, in logs, the following may be printed: `[Warning] Output video width: xxx or height: xxx is over 1504. Some devices will display exception. For example green screen!`

A prompt is given that the final video resolution (width or height) exceeds 1504, and it is not recommended to exceed 1504. Screen glitches and mosaic screen effects may occur when it exceeds 1504. This is an empirical value, and this value can run normally on most models. This is just a reminder and does not affect the normal generation of videos.

This tool supports a compatible mode for generating video files, that is, controlling the output mp4 dimension to no more than 1080p. As follows:

When you check Compatibility mode, toggle on the compatible mode. Enabled by default.

When you close it, the output size may exceed 1080p, which can meet the demand for high resolution. But there may be problems when some low-end devices play it.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/90f600f7fe2611efa21c525400bf7822.png)


---
*Source: [https://trtc.io/document/70541](https://trtc.io/document/70541)*
