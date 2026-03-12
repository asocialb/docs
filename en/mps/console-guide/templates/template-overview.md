# Template Overview

## Overview

Media Processing Service (MPS) supports transcoding, enhancement, and intelligent analysis, among other rich features. Each feature has corresponding detailed parameter settings. You can preset different processing parameters through configuring templates, facilitating subsequent reuse.

## Directions

Log in to the [MPS console](https://console.tencentcloud.com/mps) and click **Templates** on the left sidebar. Select the type of template you want to configure and click **Create template**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/062f9f27286311ef8b7b52540096e81f.png)

## Template Types

The table below lists the types of media processing templates you can create and add to an orchestration.

> **Note:**After [an orchestration is enabled](https://www.tencentcloud.com/document/product/1041/58242#e881ece6-8b7e-4b13-9f14-04858f1024dc), if the template used in the orchestration is edited, the orchestration will proceed with the edited template parameters.After [an orchestration is enabled](https://www.tencentcloud.com/document/product/1041/58242#e881ece6-8b7e-4b13-9f14-04858f1024dc), if the template used in the orchestration is deleted, the subtasks related to that template will fail.

| Template Type | Subtype | Description |
| --- | --- | --- |
| Audio/Video transcoding | TSC transcoding template | Compared to general transcoding, TSC transcoding template significantly reduces the file size of videos while maintaining their clarity. |
|  | General transcoding template | Basic video transcoding capabilities. |
|  | Video adaptive bitrate streaming template | The input source video files can be transcoded into multiple streams suitable for playback in various scenarios, allowing users to select the appropriate bitrate for video playback based on their network conditions, thereby enhancing the viewing experience. |
|  | General audio transcoding template | Supports basic transcoding processing for pure audio files. |
|  | TSC audio transcoding template | Compared to general audio transcoding, it achieves transcoding results with lower bit rates and superior sound quality. |
|  | Audio adaptive bitrate streaming template | Convert audio into adaptive bitrate streaming formats, allowing users to select the appropriate bitrate for audio playback based on their network conditions, thereby enhancing the listening experience. |
|  | Remuxing template | Transform the encapsulation format of the source video without re-encoding it. Currently, the conversion of source videos into MP4 and HLS formats is supported. |
| Audio/Video enhancement | Audio/Video enhancement | Our service supports the enhancement and repair of various quality issues in audio and video, comprehensively improving the visual experience. It is widely used in international major events such as the Olympic Games and the FIFA World Cup, as well as diverse scenarios such as the restoration of classic films and esports live streaming. |
| Intelligent auditing | Intelligent auditing | Audit images, voice, and text in videos for pornography, illegality, and regulation violations. |
| Intelligent identification | Intelligent identification | Identify faces, objects, text, and voice. Automatic Speech Recognition (ASR) also supports intelligent translation and converts it to subtitles. |
| Intelligent analysis | Intelligent analysis | Support tagging, classification, cover generation, frame-specific tagging, clipping, montage, intro and outro, game marking, and other intelligent analysis capabilities. |
| Screenshot | Time point screenshot | Take screenshots at specific time points. |
|  | Sampled screenshot | Take screenshots at a specified interval (seconds or percentage). |
|  | Image sprite screenshot | Take screenshots at specified time points and merge them into a sprite. |
|  | Animated screenshot | Cut out a video clip and make it into an animated screenshot. |
| Watermark | Watermark | Add a text or image watermark to a video. |
| Live recording | Live recording | Record live streaming content. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/48783](https://www.tencentcloud.com/document/product/1041/48783)*
