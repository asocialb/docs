# Enable Audio Mixer

This article will introduce how to add background music during a call.

## Demo

## Prerequisites

- TRTC version 5.1+
- The following platforms support adding background music during a call:

| Operating System | Browser Type | Minimum Browser Version |
| --- | --- | --- |
| Mac OS | Desktop Chrome | 56+ |
|  | Desktop Safari | 11+ |
|  | Desktop Firefox | 56+ |
|  | Desktop Edge | 80+ |
| Windows | Desktop Chrome | 56+ |
|  | Desktop QQ Browser | 10.4+ |
|  | Desktop Firefox | 56+ |
|  | Desktop Edge | 80+ |
| iOS | Mobile Safari | 14+ |
|  | WeChat Embedded Web | â |
| Android | Mobile Chrome | 81+ |
|  | WeChat Embedded Web | â |
|  | Mobile QQ Browser | â |

## Implementation Process

### Start Background Music

> - When playing online sound effect files, the sound effect files must support `CORS` and the access protocol must be `https`.
> - Supported formats include MP3, AAC (and other audio formats supported by browsers).
> - Before any user interaction, browsers prohibit web pages from playing media with sound. It is recommended to guide users to perform a click action before calling this interface.
> - Reference: [Autoplay_guide](https://developer.mozilla.org/en-US/docs/Web/Media/Autoplay_guide).

```
await trtc.startPlugin('AudioMixer', {  id: 'count',  url: '../assets/count.mp3',  loop: true,  volume: 0.2})
```

### Update Background Music

Perform operations on the background music.

```
// disable loop playbackawait trtc.updatePlugin('AudioMixer', {  id: 'count',  loop: false})// volume settingawait trtc.updatePlugin('AudioMixer', {  id: 'count',  volume: 1})// pause music `count`await trtc.updatePlugin('AudioMixer', {  id: 'count',  loop: true,  volume: 0.2,  operation: 'pause'})// resume music `count`await trtc.updatePlugin('AudioMixer', {  id: 'count',  operation: 'resume'})// play `count` from 5sawait trtc.updatePlugin('AudioMixer', {  id: 'count',  seekFrom: 5})
```

### Stop Background Music

Stop a background music that is not needed.

```
await trtc.stopPlugin('AudioMixer', {  id: 'count'})
```

## API

### trtc.startPlugin('AudioMixer', options)

Start background music.

#### options

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | `string` | Yes | Set a unique ID for each incoming music URL |
| url | `string` | Yes | Music file URL.  **One of url and track must be passed in**. If both are passed in, the url will be selected first. |
| track | `MediaStreamAudioTrack` | Yes | Music mediaStreamTrack. **One of url and track must be passed in**. You can pass in a track extracted from the `<audio/>` tag. If both are passed in, the url will be selected first. |
| loop | `boolean` | No | Whether to loop play, default is false |
| volume | `number` | No | Set the initial volume, default is 1 (0-1) |

```
await trtc.startPlugin('AudioMixer', {  id: 'count',  url: '../assets/count.mp3',  loop: true,  volume: 0.2})
```

### trtc.updatePlugin('AudioMixer', options)

Update background music.

#### options

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | `string` | Yes | The unique ID for each incoming music URL you set when call startPlugin |
| loop | `boolean` | No | Whether to loop play, default is false |
| volume | `number` | No | Set the initial volume, default is 1 (0-1) |
| seekFrom | `number` | No | Start seeking playback from which second, this parameter requires the music resource file to support [HTTP range requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Range_requests). |
| operation | `number` | No | Operation on the background music: 'pause' ï½ 'resume' ï½ 'stop' |

**Example:**

```
await trtc.updatePlugin('AudioMixer', {  id: 'count',  loop: true,  volume: 0.2,  operation: 'pause'})
```

### trtc.stopPlugin('AudioMixer', options)

Stop a background music that is not needed.

#### options

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | `string` | Yes | The unique ID for each incoming music URL you set when call startPlugin |

**Example:**

```
await trtc.stopPlugin('AudioMixer', {  id: 'count'})
```

## FAQs

1. **Cross-Origin Error?**

For example: Access to audio at XXX from origin XXX has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is
present on the requested resource.

Solution: You need to configure the CORS protocol for your online music files.

2. **Incorrect Audio Format, Unable to Play in Browser?**

For example: NotSupportedError: The operation is not supported.

Solution: You need to use an audio format supported by the browser.


---
*Source: [https://trtc.io/document/59660](https://trtc.io/document/59660)*
