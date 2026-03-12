# Enable Watermark

This article introduces how to use the watermark plugin to add image watermarks on camera streams.

## Demo

## Prerequisites

- TRTC Web SDK version â¥ 5.3.0.

## Implementation Steps

### Install Watermark Plugin

```
import { Watermark } from 'trtc-sdk-v5/plugins/video-effect/watermark';let trtc = TRTC.create({ plugins: [Watermark] });
```

### Open Camera

```
await trtc.startLocalVideo({  view: 'local-video'  option: {    mirror: false  }});
```

### Start Watermark Plugin

```
await trtc.startPlugin('Watermark', {  imageUrl: 'https://web.sdk.qcloud.com/trtc/webrtc/test/qer-test/watermark/trtc-watermark-test.png'});
```

After testing, you can replace the test image URL with your own watermark image. It is recommended to use a transparent PNG format.

### Stop Watermark Plugin

```
await trtc.stopPlugin('Watermark');
```

## API Description

### trtc.startPlugin('Watermark', options)

Start watermark plugin.

#### options

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| imageUrl | `string` | Required | Image watermark URL |
| x | `string` | Optional | Watermark left margin |
| y | `string` | Optional | Watermark top margin |
| size | `string` \|`number` \|`object` | Optional | **When passing a string:**`"cover"` scales the background image to fully cover the background area, which may cause parts of the background image to be invisible. `"contain"` scales the background image to fit entirely within the background area, possibly leaving some areas blank. **When passing a number:**`x` scales the background image by x times, e.g., 0.5, with a valid range of `(0,1]` **When passing an object:**You can specify manually by passing `{width: 200, height: 300}` **The default is**`cover` |

**Example:**

```
await trtc.startPlugin('Watermark', {  imageUrl: 'https://web.sdk.qcloud.com/trtc/webrtc/test/qer-test/watermark/tv2.png',  size: 'contain'});
```

```
await trtc.startPlugin('Watermark', {  imageUrl: 'https://web.sdk.qcloud.com/trtc/webrtc/test/qer-test/watermark/tv2.png',  size: 'cover'});
```

```
await trtc.startPlugin('Watermark', {  imageUrl: 'https://web.sdk.qcloud.com/trtc/webrtc/test/qer-test/watermark/tv2.png',  x: 0,  y: 0,  size: 0.5});
```

```
await trtc.startPlugin('Watermark', {  imageUrl: 'https://web.sdk.qcloud.com/trtc/webrtc/test/qer-test/watermark/tv2.png',  x: 0,  y: 0,  size: {    width: 100,    height: 200  }});
```

### trtc.stopPlugin('Watermark')

Stop watermark plugin.

**Example:**

```
await trtc.stopPlugin('Watermark');
```

## FAQs

1. **Is the watermark mirrored?**

The local preview image is enabled by default, so the watermark will also be mirrored. You can disable the local preview mirror image.

```
await trtc.updateLocalVideo({  option: {    mirror: false  }});
```


---
*Source: [https://trtc.io/document/59661](https://trtc.io/document/59661)*
