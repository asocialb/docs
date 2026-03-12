# API Overview

## TXLivePusher

Tencent Cloud CSS pusher is primarily used for browser-based web streaming. It captures the user's video and audio through the browser and utilizes WebRTC to transmit the video and audio streams to the Tencent Cloud CSS server.

| API | Description |
| --- | --- |
| [checkSupport](https://www.tencentcloud.com/document/product/267/58159#00edc968-000c-4592-b8f9-47490a4cf610) | Static function is used to check browser compatibility. |
| [setRenderView](https://www.tencentcloud.com/document/product/267/58159#3a841e44-2657-4d70-bc26-39a4d204a997) | Set the local video preview container. |
| [setVideoQuality](https://www.tencentcloud.com/document/product/267/58159#a7e0dec6-4760-48d1-8cee-2b2bcd6adbca) | Set Push Video Quality. |
| [setAudioQuality](https://www.tencentcloud.com/document/product/267/58159#3d0c9d81-90e5-44bf-b7c3-2cf0797672f2) | Set Push Audio Quality. |
| [setProperty](https://www.tencentcloud.com/document/product/267/58159#cfba56db-c7ee-46b5-8251-3756c5068265) | Invoke Advanced API Interface. |
| [startCamera](https://www.tencentcloud.com/document/product/267/58159#2f9ab3fe-314b-45bb-8145-b8a6cf2ef3ce) | Open Camera Device. |
| [stopCamera](https://www.tencentcloud.com/document/product/267/58159#492318ae-0965-4c25-aeee-474a15b36d5b) | Close Camera Device. |
| [startMicrophone](https://www.tencentcloud.com/document/product/267/58159#b9bdfb60-ead1-4942-806e-bbe5d9820d63) | Open Microphone Device. |
| [stopMicrophone](https://www.tencentcloud.com/document/product/267/58159#dc6393a1-ccfc-4fb3-be06-bf06e335aa37) | Close Microphone Device. |
| [startScreenCapture](https://www.tencentcloud.com/document/product/267/58159#e2b8835f-2aa3-40c6-bc9d-da41b64054df) | Enable Screen Capture. |
| [stopScreenCapture](https://www.tencentcloud.com/document/product/267/58159#a9b26ab7-13df-4116-bcc2-aba0740c4413) | Disable Screen Capture. |
| [startVirtualCamera](https://www.tencentcloud.com/document/product/267/58159#d9088dfe-3018-4e10-a462-2e990151b59b) | Start Capturing Local Media File Stream. |
| [stopVirtualCamera](https://www.tencentcloud.com/document/product/267/58159#7d851ea7-e5d6-42af-8e9b-ad77dab31079) | Stop Capturing Local Media File Stream. |
| [startCustomCapture](https://www.tencentcloud.com/document/product/267/58159#7582f298-b678-4723-947e-f2ae02410db7) | Use Custom Audio and Video Stream. |
| [stopCustomCapture](https://www.tencentcloud.com/document/product/267/58159#cfd776a7-5f17-439c-8fb7-68bc5e20fe08) | Close Custom Audio and Video Stream. |
| [startPush](https://www.tencentcloud.com/document/product/267/58159#96a7c9d1-4146-4432-9a22-c45acda3acba) | Start Pushing Stream. |
| [stopPush](https://www.tencentcloud.com/document/product/267/58159#d55657d7-0e7d-4b78-9f32-46a64522b496) | Stop Pushing Stream. |
| [isPushing](https://www.tencentcloud.com/document/product/267/58159#46fb1f2e-ccfe-4f76-abeb-64f99d765e59) | Check if Currently Pushing Stream. |
| [getMediaStream](https://www.tencentcloud.com/document/product/267/58159#3d0c318d-aae9-4e7b-a4b9-0409d375cb3a) | Get Audio and Video Stream by Stream ID. |
| [getDeviceManager](https://www.tencentcloud.com/document/product/267/58159#ead4a628-27fc-4382-bf03-597064cb663f) | Get Device Manager Object. |
| [getVideoEffectManager](https://www.tencentcloud.com/document/product/267/58159#18deefc9-bcf1-4293-9674-73d3316ac122) | Get Video Effect Manager Object. |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/267/58159#5a7db02d-b44f-4925-a57f-fe2411c53e11) | Get Audio Effect Manager Object. |
| [setVideoMute](https://www.tencentcloud.com/document/product/267/58159#aee0c1b4-65e0-4942-90ad-3002f3165b26) | Set whether to disable video stream. |
| [setAudioMute](https://www.tencentcloud.com/document/product/267/58159#c3a6e508-b70f-459a-b41f-788aaef7f9b4) | Set whether to disable audio stream. |
| [pauseVideo](https://www.tencentcloud.com/document/product/267/58159#e9c92230-ef64-426b-b73f-3e7ea6683851) | Disable video stream. |
| [pauseAudio](#cf9038d6-4a68-4926-8bdf-ef5b2a0a802f) | Disable audio stream. |
| [resumeVideo](https://www.tencentcloud.com/document/product/267/58159#e9c92230-ef64-426b-b73f-3e7ea6683851) | Restore video stream. |
| [resumeAudio](https://www.tencentcloud.com/document/product/267/58159#ee4e1065-d7bd-4f59-8bac-32c9aa052d86) | Restore audio stream. |
| [setVideoContentHint](https://www.tencentcloud.com/document/product/267/58159#821096b5-7a51-4cd7-8f08-3f068c7e9093) | Set video content hint to improve encoding quality in different content scenarios. |
| [setObserver](https://www.tencentcloud.com/document/product/267/58159#9e2fc6d2-8f2a-4823-a037-2d010ca030e9) | Set push stream event callback notification. |
| [destroy](https://www.tencentcloud.com/document/product/267/58159#dc8ae00e-a584-4588-aafe-00e3c71d2955) | When leaving the page or exiting, clean up the SDK instance. |

## TXDeviceManager

Device Management Interface, mainly used for managing camera and microphone devices, performing device acquisition and switching operations.

| API | Description |
| --- | --- |
| [getDevicesList](https://www.tencentcloud.com/document/product/267/58159#d0e3c8fa-6dfe-4bca-b593-77df628ea679) | Get Device List. |
| [getCurrentDevice](https://www.tencentcloud.com/document/product/267/58159#a9146828-700d-4d02-8d18-382cf3e473d4) | Get device information of the current stream. |
| [switchDevice](https://www.tencentcloud.com/document/product/267/58159#bea461c4-6d1f-4c39-87ad-20181290ae8b) | Switch the currently used device. |
| [switchCamera](https://www.tencentcloud.com/document/product/267/58159#9cfa23b1-7c92-45a9-8245-39094b4b847c) | Switch camera device. |
| [switchMicrophone](https://www.tencentcloud.com/document/product/267/58159#ecf2fdb1-bacc-4398-a9b6-888b179c7561) | Switch microphone device. |

## TXAudioEffectManager

Audio Effect Management Interface, mainly used for adjusting volume operations.

| API | Description |
| --- | --- |
| [setVolume](https://www.tencentcloud.com/document/product/267/58159#ca56b68f-09ba-4127-bca0-6480c5814f0f) | Set the volume level of the audio stream. |

## TXVideoEffectManager

Video Effect Management Interface, mainly used for setting Picture-in-Picture, mirror, filter, watermark, text, and other operations.

| API | Description |
| --- | --- |
| [enableMixing](https://www.tencentcloud.com/document/product/267/58159#04f540f5-f365-41b7-b950-7bbf65eda92c) | Enable local video screen mixing feature. |
| [setMixingConfig](https://www.tencentcloud.com/document/product/267/58159#02fcc095-76fc-4eb6-bedb-4bc8377fec4f) | Set mixing parameters. |
| [getMixingConfig](https://www.tencentcloud.com/document/product/267/58159#de7a0b9a-a3e3-4083-af1f-015f4c37f344) | Get the final adopted mixing parameters. |
| [setLayout](https://www.tencentcloud.com/document/product/267/58159#3b038734-ee73-43a0-bf75-5c4aab21a4c7) | Set Picture-in-Picture layout parameters for the video stream. |
| [getLayout](https://www.tencentcloud.com/document/product/267/58159#4f4c3989-ce3e-46fc-bc89-7753b12a9620) | Get Picture-in-Picture layout parameters for the specified stream. |
| [setMirror](https://www.tencentcloud.com/document/product/267/58159#27c8c4e4-2747-4811-9673-2fb6c06707db) | Set mirror effect for the video stream. |
| [setNormalFilter](https://www.tencentcloud.com/document/product/267/58159#636090bf-caf3-4563-9641-01da93a49b7e) | Set general filter effect for the video stream. |
| [setWatermark](https://www.tencentcloud.com/document/product/267/58159#60464509-da7d-4cfe-97d1-c5bf0bfa24be) | Set watermark. |
| [setText](https://www.tencentcloud.com/document/product/267/58159#6846bb5f-92d4-4ba7-ae49-990ec819c79e) | Set text. |

# TXLivePusher

Tencent Cloud CSS Pusher, mainly used for browser-based Web streaming. It captures the user's image and sound through the browser and pushes the video and audio streams to the Tencent Cloud server via WebRTC. If you need to enable the local mixing feature, call the TXVideoEffectManager method [enableMixing()](https://www.tencentcloud.com/document/product/267/58159#04f540f5-f365-41b7-b950-7bbf65eda92c) to enable it.

Please create an instance object first for all subsequent operations.

```
const livePusher = new TXLivePusher();
```

## checkSupport

Static function, check browser compatibility.

```
static checkSupport(): Promise<TXSupportResult>;
```

Return:

Return Promise object, where the result data structure is referred to as [TXSupportResult](https://www.tencentcloud.com/document/product/267/58159#726c01ad-7629-49ad-ab89-ad6ebe6fc0e4).

## setRenderView

Set the preview container for the local video screen, provide a div node, and the locally captured video will be rendered in the container. If the local mixing feature is enabled, the container will render the mixed audio and video after processing.

```
setRenderView(container: string | HTMLDivElement): void;
```

Parameter:

| Field | Type | Description |
| --- | --- | --- |
| container | string \| HTMLDivElement | Container ID or DOM node. |

## setVideoQuality

Set push video quality. The SDK has built-in video quality templates, allowing you to set the push video quality directly through predefined templates.

```
setVideoQuality(quality: string): void;
```

Parameter:

| Field | Type | Description |
| --- | --- | --- |
| quality | string | Predefined video quality template names. |

The built-in video quality templates are as follows:

| Template Name | Resolution (Width x Height) | Frame Rate (fps) | Bitrate (kbps) |
| --- | --- | --- | --- |
| 120p | 160 x 120 | 15 | 200 |
| 180p | 320 x 180 | 15 | 350 |
| 240p | 320 x 240 | 15 | 400 |
| 360p | 640 x 360 | 15 | 800 |
| 480p | 640 x 480 | 15 | 900 |
| 720p | 1280 x 720 | 15 | 1500 |
| 1080p | 1920 x 1080 | 15 | 2000 |
| 2K | 2560 x 1440 | 30 | 4860 |
| 4K | 3840 x 2160 | 30 | 9000 |

> **Note:**Due to device and browser limitations, the video resolution may not be perfectly matched. In this case, the browser will automatically adjust the resolution to be close to the corresponding resolution.If the video quality parameters (resolution, frame rate, and bitrate) do not meet your requirements, you can set custom values individually using [setProperty()](https://www.tencentcloud.com/document/product/267/58159#cfba56db-c7ee-46b5-8251-3756c5068265).The video resolution here mainly refers to the resolution of the locally captured video. The resolution during streaming may be lower than the captured resolution, and the browser will automatically adjust the streaming resolution based on network bandwidth and other factors.The default is 720p, i.e.`setVideoQuality('720p')`.

## setAudioQuality

Set the streaming audio quality. The SDK has an inbuilt audio quality template. The streaming audio quality can be set directly by using predefined templates.

```
setAudioQuality(quality: string): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| quality | string | The pre-defined name of the audio quality template. |

The built-in audio quality templates are as follows:

| Template Name | Sample rate | Bitrate (Kbps) |
| --- | --- | --- |
| standard | 48000 | 40 |
| high | 48000 | 128 |

> **Note:**If the audio quality parameters (sampling rate and bitrate) do not meet your requirements, you can individually set custom values through [setProperty()](https://www.tencentcloud.com/document/product/267/58159#cfba56db-c7ee-46b5-8251-3756c5068265).The default is to use 'standard', that is, `setAudioQuality('standard')`.

## setProperty

Primarily used for invoking advanced features, such as setting the resolution, frame rate and bitrate of the video, as well as setting the sampling rate and bitrate of the audio, among others.

```
setProperty(key: string, value: any): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| key | string | Key corresponding to the advanced API. |
| value | * | Parameters needed when invoking the key corresponding to the advanced API. |

The following advanced features are currently supported:

| Key | Value | Description | Sample code |
| --- | --- | --- | --- |
| setVideoResolution | { width: number; height:number; } | Establish the video resolution | setProperty('setVideoResolution', { width: 1920, height: 1080 }) |
| setVideoFPS | number | Configure the video frame rate | setProperty('setVideoFPS', 25) |
| setVideoBitrate | number | Set the video bitrate | setProperty('setVideoBitrate', 2000) |
| setAudioSampleRate | number | Configure the audio sample rate | setProperty('setAudioSampleRate', 44100) |
| setAudioBitrate | number | Establish the audio bitrate | setProperty('setAudioBitrate', 200) |
| setConnectRetryCount | number | Set the retry count for connections, default is: 3; range: 0 - 10. When the SDK unexpectedly disconnects with the server, it will attempt to reconnect. | setProperty('setConnectRetryCount', 5) |
| setConnectRetryDelay | number | Set the connection retry delay, the default value is: 1, in seconds; within the range: 0 - 10. When the SDK is anomalously disconnected from the server, it endeavors to reconnect. | setProperty('setConnectRetryDelay', 2) |
| enableAudioAEC | boolean | Enable echo cancellation | setProperty('enableAudioAEC', true) |
| enableAudioAGC | boolean | Enable automatic gain | setProperty('enableAudioAGC', true) |
| enableAudioANS | boolean | Enable noise suppression | setProperty('enableAudioANS', true) |
| enableLog | boolean | Should logs be printed in the console | setProperty('enableLog', true) |

> **Note:**Echo cancellation, automatic gain and noise suppression are enabled by default, their effectiveness ultimately depends on the device and browser. It is recommended that these three functions either be enabled or disabled collectively.Please set up before capturing and pushing the stream.

## startCamera

Initiate camera device. User authorization is required to allow the browser access to the camera. If authorization fails or device access fails, the returned Promise object will throw an error.

```
startCamera(deviceId?: string): Promise<string>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| deviceId | string | Camera device ID, an optional parameter, determines the camera device to open. The device ID can be obtained using the method [getDevicesList](https://www.tencentcloud.com/document/product/267/58159#d0e3c8fa-6dfe-4bca-b593-77df628ea679) in `TXDeviceManager`. On mobile devices, the front and rear cameras can be specified by entering 'user' and 'environment'. |

Return:

Yields a Promise object. Upon success, ID of the stream is returned, serving as the unique identification within SDK. In case of failure, the corresponding error message is thrown.

> **Note:**This interface does not support usage under the HTTP protocol; please deploy your website using the HTTPS protocol.Upon encountering a failure to open the camera, refer to the error message returned, consulting [getUserMedia Exception](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia#exceptions) as needed.

## stopCamera

The operation of shutting down the camera apparatus.

```
stopCamera(streamId?: string): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID, an optional parameter, signifies the specific camera stream to be deactivated. After the local stream mix is enabled, if multiple camera streams have been collected, you can turn off the specified camera stream through the stream ID; otherwise, it will close all camera streams. |

## startMicrophone

Activate microphone devices. It requires user authorization to access the microphone through the browser. If authorization fails, or the device is inaccessible, the returned Promise object will throw an error.

```
startMicrophone(deviceId?: string): Promise<string>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| deviceId | string | Microphone Device ID, an optional parameter designating the specific microphone equipment to be activated. The Device ID can be retrieved through the method [getDevicesList()](https://www.tencentcloud.com/document/product/267/58159#d0e3c8fa-6dfe-4bca-b593-77df628ea679) found in `TXDeviceManager`. |

Return:

Yields a Promise object. Upon success, ID of the stream is returned, serving as the unique identification within SDK. In case of failure, the corresponding error message is thrown.

> **Note:**This interface does not support usage under the HTTP protocol; please deploy your website using the HTTPS protocol.Error messages returned upon microphone activation failure; you may refer to [getUserMedia exceptions](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia#Exceptions) for further insights.In case an echo phenomenon occurs, you can mute the local video element video used for playing previews to prevent echo occurrences.livePusher.videoView.muted = true;

## stopMicrophone

Shut down the microphone device.

```
stopMicrophone(streamId?: string): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID is an optional parameter that indicates the specification of a microphone stream to be discontinued. Once local mix streaming has been activated, a specific microphone stream can be silenced by using Stream ID, if multiple microphone streams have been captured, otherwise, all microphone streams will be muted. |

## startScreenCapture

Screen capture is initiated, necessitating the user's permission for the browser to gain access to the screen. Should authorization or screen access be unsuccessful, the returned Promise object will project an error.

```
startScreenCapture(audio?: boolean): Promise<string>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| audio | boolean | Determines whether to collect system sound or Tag page sound: true - collection of sound, false - no sound collection, default is set to false. |

Return:

Yields a Promise object. Upon success, ID of the stream is returned, serving as the unique identification within SDK. In case of failure, the corresponding error message is thrown.

> **Note:**This interface does not support usage under the HTTP protocol; please deploy your website using the HTTPS protocol.When opening screen capturing fails, refer to the error information returned. For more details, refer to [getDisplayMedia exception](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getDisplayMedia#Exceptions).Currently, only Chrome 74+ and Edge 79+ support the collection of sound. In Windows systems, you can capture sound from the entire system, while on Linux and macOS, you can only capture sound from tab pages.If 'audio' is set to true, ensure that the option to capture sound at the bottom of the browser screen sharing pop-up window is checked, otherwise sound will not be captured. If 'audio' is set to false, the option to capture sound will not appear in the browser's screen sharing pop-up window.

## stopScreenCapture

Stops screen capturing.

```
stopScreenCapture(streamId?: string): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID, optional parameter, designates the shared screen stream to be closed. Once local stream mix is activated, if multiple screen share streams have been collected, a particular screen share stream can be turned off via the stream ID. If not specified, all screen share streams will be shut down. |

## startVirtualCamera

Commence the collection of local media file streams. At present, the supported file formats are video (mp4), audio (mp3), and images (jpg, png, bmp).

```
startVirtualCamera(file: File): Promise<string>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| file | File | Local media files are compulsory. The file format must be any of the following: mp4, mp3, jpg, png, bmp. |

Return:

Yields a Promise object. Upon success, ID of the stream is returned, serving as the unique identification within SDK. In case of failure, the corresponding error message is thrown.

> **Note:**Local files support video, audio, and image. Video files capture both video and audio streams, audio files only capture audio streams, and image files only capture video streams.A file object must be manually passed in, necessitating the prior use of `<input type="file">` to guide users in local file selection.

## stopVirtualCamera

Halting the collection of local media file streams.

```
stopVirtualCamera(streamId?: string): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID is an optional parameter used to specify the media file stream that needs to be shut off. After enabling local merged streaming, if multiple media file streams have been collected, you can close a specified media file stream through Stream ID, otherwise all media file streams will be shut off. |

## startCustomCapture

Utilize custom user audio-visual streams. Leverage user-generated streams for local merging and broadcasting.

```
startCustomCapture(stream: MediaStream): Promise<string>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| stream | MediaStream | User-defined stream. |

Return:

Yields a Promise object. Upon success, ID of the stream is returned, serving as the unique identification within SDK. In case of failure, the corresponding error message is thrown.

## stopCustomCapture

Shuts down the custom audio/video stream, only removes the custom stream, and does not terminate the custom stream.

```
stopCustomCapture(streamId?: string): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID, an optional parameter, refers to the custom stream that needs to be removed. After activating local mixed flow, if multiple custom streams are added, you can remove the specific custom stream through the stream ID, otherwise all custom streams will be purged. |

## startPush

Initiate streaming, establish a WebRTC connection, push audio and video streams to Tencent Cloud servers. If the local mixing function has been activated, the stream data being pushed will be the result of mixed processing.

```
startPush(pushUrl: string): Promise<void>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| pushUrl | string | WebRTC push address. |

Return:

Returns a Promise object.

> **Note:**Refer to the format of the push stream address [Assemble Push Stream URL](https://www.tencentcloud.com/en/document/product/267/57043#8a99c4e5-7eef-4a86-aa38-bb88b3701254).

## stopPush

Cease the propagation of audio and video streams, and terminate the WebRTC connection.

```
stopPush(): void;
```

## isPushing

Inquire whether the stream is currently being pushed.

```
isPushing(): boolean;
```

Return:

Boolean values, true - streaming in progress, false - streaming not in progress.

## getMediaStream

Acquire the audio and video streams based on the stream ID.

```
getMediaStream(streamId: string): MediaStream;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID is returned after the successful invocation of interfaces such as [startCamera()](https://www.tencentcloud.com/document/product/267/58159#2f9ab3fe-314b-45bb-8145-b8a6cf2ef3ce), [startMicrophone()](https://www.tencentcloud.com/document/product/267/58159#b9bdfb60-ead1-4942-806e-bbe5d9820d63), [startScreenCapture()](https://www.tencentcloud.com/document/product/267/58159#b9bdfb60-ead1-4942-806e-bbe5d9820d63), etc. |

Return:

The stream object captured can be played back by passing it to the [srcObject](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/srcObject) attribute of the video tag.

## getDeviceManager

Acquire the device management entity. Through device management, operations such as querying the device list and switching devices can be conducted.

```
getDeviceManager(): TXDeviceManager;
```

Return:

Device Management Object. For specific usage, please refer to [TXDeviceManager](https://www.tencentcloud.com/document/product/267/58159#47b240c3-db91-4bbf-b9a5-7f8dd03533ee).

## getVideoEffectManager

Acquire the video effect management object. Virtue of video effect management facilitates a myriad operations such as picture in picture, mirroring, filters, watermarks, text, and so forth.

```
getVideoEffectManager(): TXVideoEffectManager;
```

Return:

The video effect management object, for specific usage, please refer to [TXVideoEffectManager](https://www.tencentcloud.com/document/product/267/58159#4c733ac3-d491-4908-9c7f-fb69b859f8a1) .

## getAudioEffectManager

Acquire the audio effect management object. Through audio effect management, one can perform volume adjustment operations.

```
getAudioEffectManager(): TXAudioEffectManager;
```

Return:

The audio effect management object, for the specific method of use, please refer to [TXAudioEffectManager](https://www.tencentcloud.com/document/product/267/58159#12b7dd05-ec27-4b34-983c-5c1fcd308567).

## setVideoMute

Configure whether to disable the video stream. If the local stream mixing function is enabled, the stream that is disabled is the final produced video stream.

```
setVideoMute(mute: boolean): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| mute | boolean | true - disabled, false - enabled. |

> **Note:**The setting will take effect only when there is a current video stream.After disabling, each frame will be filled with black pixels, in reality still capturing the video stream.It is recommended to use [pauseVideo()](https://www.tencentcloud.com/document/product/267/58159#e9c92230-ef64-426b-b73f-3e7ea6683851) and [resumeVideo()](https://www.tencentcloud.com/document/product/267/58159#e9c92230-ef64-426b-b73f-3e7ea6683851) directly.

## setAudioMute

Configure whether to disable the audio stream. If the local stream mix feature is enabled, the audio stream that will be disabled corresponds to the final composite.

```
setAudioMute(mute: boolean): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| mute | boolean | true - disabled, false - enabled. |

> **Note:**The settings will take effect only when there is an ongoing audio stream.After being disabled, there is no sound, but in fact audio stream is still being gathered.It's advised to directly use [pauseAudio()](https://www.tencentcloud.com/document/product/267/58159#cf9038d6-4a68-4926-8bdf-ef5b2a0a802f) and [resumeAudio()](https://www.tencentcloud.com/document/product/267/58159#ee4e1065-d7bd-4f59-8bac-32c9aa052d86) .

## pauseVideo

Disabling video stream. Equivalent to `setVideoMute(true)`.

```
pauseVideo(): void;
```

## pauseAudio

Disable the audio stream. This is equivalent to `setAudioMute(true)`.

```
pauseAudio(): void;
```

## resumeVideo

Resuming the video stream is equivalent to `setVideoMute(false)` .

```
resumeVideo(): void;
```

## resumeAudio

Resume the audio stream. Equivalent to `setAudioMute(false)` .

```
resumeAudio(): void;
```

## setVideoContentHint

Set up video content prompts to enhance video encoding quality in various content scenarios.

```
setVideoContentHint(contentHint: string): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| contentHint | string | Content hint, refer to [MediaStreamTrack.contentHint](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/contentHint) . |

The suggested value range is as follows:

| Fetching Value | Description |
| --- | --- |
| '' | By default, the browser will automatically evaluate the video content and choose the appropriate prompt configuration for encoding. |
| 'motion' | This manifests as a preference for smoothness, applicable when the video content is obtained from camera captures, films, videos, or games. |
| 'detail' | Manifests as clarity precedence, suitable for video content that includes mixed images and text. When screen sharing, it's advisable to use this prompt. |
| 'text' | Manifests as clarity prioritized, applicable when the video content only contains copious amount of text. |

> **Note:**The setting will take effect only when there is a current video stream.

## setObserver

Setting up streaming event notification callbacks. By arranging these callbacks, one can monitor several streaming event notifications, including streaming states, statistical data, along with warnings and error messages, among others.

```
setObserver(observer: TXLivePusherObserver): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| observer | [TXLivePusherObserver](https://www.tencentcloud.com/document/product/267/58159#623509aa-c99d-4a5d-bfb1-213349b09cba) | The callback target object for the stream push. |

> **Note:**Currently, some callback event notifications, such as `onError`, `onWarning`, `onCaptureFirstAudioFrame`, `onCaptureFirstVideoFrame` can also be obtained through the Promise object returned by the corresponding interface. Users can opt for the method to receive the respective event notifications based on their usage preferences. `For instance:``startCamera().then()` is equivalent to `onCaptureFirstVideoFrame()` , the status of successful acquisition of the first frame of video can also be achieved.`startCamera().catch()` is equivalent to `onWarning()` , also it helps in obtaining the error when failing to turn on the camera.

## destroy

Upon departure from the page or exit, ensure to purge the SDK instance to avoid potential memory leaks. Execute the 'stop' method prior to invoking other functions.

```
destroy(): void;
```

# TXDeviceManager

Device Management Interface. Principally used for the administration of cameras and microphone devices. Should the local stream mix feature be toggled on, the corresponding stream IDs are necessitated for operation.

Obtain object instances through the `TXLivePusher` method [getDeviceManager()](https://www.tencentcloud.com/document/product/267/58159#ead4a628-27fc-4382-bf03-597064cb663f).

```
const deviceManager = livePusher.getDeviceManager();
```

## getDevicesList

Acquire the device list.

```
getDevicesList(type?: string): Promise<TXMediaDeviceInfo[]>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| type | string | Taking value **video** or **audio**, optional parameter. If not transmitted, return all device list, transmit video for camera device list, transmit audio for microphone device list. |

Return:

Returns a Promise object. For the structure of the device information, please refer to [TXMediaDeviceInfo](https://www.tencentcloud.com/document/product/267/58159#cb1eb617-3f88-4e39-82da-399b589998ec) .

> **Note:**This interface does not support usage under the HTTP protocol; please deploy your website using the HTTPS protocol.For security reasons, the browser may leave the 'deviceId' and 'deviceName' fields blank until the user grants access to the camera or microphone. Therefore, it is recommended to call this interface to get device details after the user has granted access.

## getCurrentDevice

Acquire the device information of the current stream. If local stream mix is activated, you must stipulate the stream ID.

```
getCurrentDevice(type: string, streamId?: string): Promise<TXMediaDeviceInfo>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| type | string | Device type: video - camera device, audio - microphone device. |
| streamId | string | Stream ID refers to the stream from which device information is to be fetched. This is a mandatory variable after enabling local stream mixing, corresponding to the stream collected by the camera or microphone devices. |

Return:

Returns a Promise object. For the structure of the device information, please refer to [TXMediaDeviceInfo](https://www.tencentcloud.com/document/product/267/58159#cb1eb617-3f88-4e39-82da-399b589998ec) .

## switchDevice

Switch the device currently in use. If local stream mix is enabled, a stream ID must be specified.

```
switchDevice(type: string, deviceId: string, streamId?: string): Promise<void>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| type | string | Device type: video - camera device, audio - microphone device. |
| deviceId | string | The device ID can be obtained by calling [getDevicesList()](https://www.tencentcloud.com/document/product/267/58159#d0e3c8fa-6dfe-4bca-b593-77df628ea679). |
| streamId | string | Stream ID, designates the stream of the device to be switched, it is required when local mix stream is enabled. The corresponding stream must be a stream collected by a camera or a microphone device. |

Return:

Returns a Promise object.

> **Note:**This method is only applicable for calls when collecting audio and video from a camera and microphone, streams collected in other ways do not support calling this API.If streaming has not yet commenced, the local stream alone is updated; but if streaming is already underway, the audio and video streams being pushed to the server are concurrently updated.When switching devices for a given stream, the corresponding stream ID remains constant.Upon specifying the stream ID, the corresponding stream type should align with the type, such as when type is video, the corresponding stream must be camera-captured video stream.It is advisable to directly employ [switchCamera()](https://www.tencentcloud.com/document/product/267/58159#9cfa23b1-7c92-45a9-8245-39094b4b847c) and [switchMicrophone()](https://www.tencentcloud.com/document/product/267/58159#ecf2fdb1-bacc-4398-a9b6-888b179c7561) .

## switchCamera

Transition camera equipment. Equivalent to `switchDevice('video', deviceId, streamId)` .

```
switchCamera(deviceId: string, streamId?: string): Promise<void>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| deviceId | string | The device ID can be acquired by invoking [getDevicesList()](https://www.tencentcloud.com/document/product/267/58159#d0e3c8fa-6dfe-4bca-b593-77df628ea679). On mobile devices, switching between the front and rear cameras can be facilitated by entering 'user' and 'environment'. |
| streamId | string | The stream ID specifies the stream of the camera device to be switched. Once local stream mix is activated, it's a mandatory field. The corresponding stream must be the one collected by the camera device. |

Return:

Returns a Promise object.

## switchMicrophone

Switching microphone device. This means `switchDevice('audio', deviceId, streamId)` .

```
switchMicrophone(deviceId: string, streamId?: string): Promise<void>;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| deviceId | string | The Device ID can be obtained by invoking the [getDevicesList()](https://www.tencentcloud.com/document/product/267/58159#d0e3c8fa-6dfe-4bca-b593-77df628ea679) function. |
| streamId | string | Stream ID, identifies the stream for which the microphone device will be changed, and must be supplied after enabling local mixed-flow. The corresponding stream must be a stream collected from the microphone device. |

Return:

Returns a Promise object.

# TXAudioEffectManager

An audio effect management interface, primarily employed for adjusting volume operations. If the local mixed-flow feature is activated, it is essential to pass in the corresponding stream ID for operation.

An object instance can be retrieved through the `TXLivePusher` method [getAudioEffectManager()](https://www.tencentcloud.com/document/product/267/58159#5a7db02d-b44f-4925-a57f-fe2411c53e11).

```
const audioEffectManager = livePusher.getAudioEffectManager();
```

## setVolume

Set the volume level of the audio stream. If local stream mixing is enabled, you must specify the stream ID.

```
setVolume(volume: number, streamId?: string): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| volume | number | The volume level, which ranges from 0 to 100, with the default value being 100. |
| streamId | string | Stream ID, designates the stream to be set, and must be transmitted after enabling local stream blending. |

> **Note:**If you feel the volume is still too low after setting the volume to 100, you can set the volume above 100, however, there's a risk of distortion with volumes exceeding 100, please handle with caution.

# TXVideoEffectManager

Video effect management interface. Principally employed for operations such as picture-in-picture, mirror, filters, watermarks, text and more. It's necessary to first invoke the [enableMixing()](https://www.tencentcloud.com/document/product/267/58159#04f540f5-f365-41b7-b950-7bbf65eda92c) interface to enable these features.

Acquire the object instance via the `TXLivePusher` method [getVideoEffectManager()](https://www.tencentcloud.com/document/product/267/58159#18deefc9-bcf1-4293-9674-73d3316ac122).

```
const videoEffectManager = livePusher.getVideoEffectManager();
```

## enableMixing

Initiate the function for local video frame mix.

```
enableMixing(enabled: boolean): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| enabled | boolean | Whether to activate local stream mix feature; it is deactivated by default. |

> **Note:**Prior to enabling the local stream mix, the previewed and pushed streams are purely raw captures. Upon activation, these streams undergo rendering through local browser mixing, incurring some performance overhead.It is requisite to enable local stream mixing by invoking `TXVideoEffectManager` before deploying other methods.Without the local stream mix activated, only a singular video stream and audio stream can be captured.After successfully activating local mix stream, various streams can be captured, such as executing two `startCamera` to capture two disparate camera visuals, or initially executing `startCamera` to capture the camera visual, followed by `startScreenCapture` to capture screen visual. The multi-stream captures, both visual and audio, appear in the final merged output.

## setMixingConfig

Set the stream mix parameters. When this interface is not invoked for settings, the default mix parameters are directly obtained from the methods `TXLivePusher` in [setVideoQuality()](https://www.tencentcloud.com/document/product/267/58159#a7e0dec6-4760-48d1-8cee-2b2bcd6adbca) and [setProperty()](https://www.tencentcloud.com/document/product/267/58159#cfba56db-c7ee-46b5-8251-3756c5068265).

```
setMixingConfig(config: TXMixingConfig): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| config | [TXMixingConfig](https://www.tencentcloud.com/document/product/267/58159#58e22fc8-4ce1-479c-a2b0-e3826e0e3800) | Configuration of mix streaming parameters. |

## getMixingConfig

Fetch the final adopted parameters of stream mixing. Primarily use the results set by [setMixingConfig()](https://www.tencentcloud.com/document/product/267/58159#02fcc095-76fc-4eb6-bedb-4bc8377fec4f), followed by the ones from the `TXLivePusher` methods in [setVideoQuality()](https://www.tencentcloud.com/document/product/267/58159#a7e0dec6-4760-48d1-8cee-2b2bcd6adbca) and [setProperty()](https://www.tencentcloud.com/document/product/267/58159#cfba56db-c7ee-46b5-8251-3756c5068265).

```
getMixingConfig(): TXMixingConfig;
```

Return:

The configuration setup for stream mix parameters, data structure please refer to [TXMixingConfig](https://www.tencentcloud.com/document/product/267/58159#58e22fc8-4ce1-479c-a2b0-e3826e0e3800).

## setLayout

Setting the Picture-in-Picture layout parameters for the video stream.

```
setLayout(config: TXLayoutConfig | TXLayoutConfig[]): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| config | [TXLayoutConfig](https://www.tencentcloud.com/document/product/267/58159#f7c9b067-b96e-4c93-a59f-92cde383f4b5) \| [TXLayoutConfig](https://www.tencentcloud.com/document/product/267/58159#f7c9b067-b96e-4c93-a59f-92cde383f4b5)[] | The configuration of the PiP layout supports the passage of an object or an array of objects. |

> **Note:**After enabling local stream mixing, all collected streams will automatically be added to the final output video stream. By default, the layout parameters ensure that the video stream image appears snugly in the upper left corner of the origin.Configuration parameters may be passed as an array of objects, for bulk setting of multiple stream's PiP layout effects, or you may simply pass an object to set a specific stream individually.If you do not wish to display the image of the collected stream, preferring only to retain the sound, you may set the layout width and height to 0.

## getLayout

Retrieve the PiP layout parameters for a specific stream.

```
getLayout(streamId: string): TXLayoutConfig | null;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID, signifies the stream from which you wish to acquire the Picture-in-Picture layout parameters. |

Return:

Returns the Picture-in-Picture layout parameters for the specified stream; for the data structure, please consult [TXLayoutConfig](https://www.tencentcloud.com/document/product/267/58159#f7c9b067-b96e-4c93-a59f-92cde383f4b5). If the stream does not exist, it returns null.

## setMirror

Specify the mirroring effect of the video stream, including horizontal and vertical mirrors.

```
setMirror(config: TXMirrorConfig | TXMirrorConfig[]): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| config | [TXMirrorConfig](https://www.tencentcloud.com/document/product/267/58159#e994af70-5de6-4178-a53d-9b4a34e26975) \| [TXMirrorConfig](https://www.tencentcloud.com/document/product/267/58159#e994af70-5de6-4178-a53d-9b4a34e26975)[] | Configuration for the mirror effect permits both individual and batch setting via object or object array. |

> **Note:**Configuration parameters can be passed as an array, allowing the batch setting of multiple streams' mirror effects, or as an individual object for a specific stream.

## setNormalFilter

Establish the general filter effect of the video stream, encompassing contrast, brightness, and saturation.

```
setNormalFilter(config: TXNormalFilterConfig | TXNormalFilterConfig[]): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| config | [TXNormalFilterConfig](https://www.tencentcloud.com/document/product/267/58159#f9a4326e-3c6d-4801-8961-f116683ec686) \| [TXNormalFilterConfig](https://www.tencentcloud.com/document/product/267/58159#f9a4326e-3c6d-4801-8961-f116683ec686)[] | The configuration for the general filter effect supports object or object array transmission. |

> **Note:**Configuration parameters can be transmitted as object arrays for the batch setting of general filter effects on multiple streams or as a solo object for specifically designated streams.

## setWatermark

Establish watermarks, with support for simultaneous multiple watermark settings.

```
setWatermark(config: TXWatermarkConfig | TXWatermarkConfig[] | null): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| config | [TXWatermarkConfig](https://www.tencentcloud.com/document/product/267/58159#89e3a4c4-0487-4f14-a148-4e1931473852) \| [TXWatermarkConfig](https://www.tencentcloud.com/document/product/267/58159#89e3a4c4-0487-4f14-a148-4e1931473852)[] \| null | Watermark configuration parameters allow for the transmission of objects, object arrays, or null. |

> **Note:**Configuration parameters can pass object arrays, simultaneously setting multiple watermarks, or can pass a single object to set an individual watermark.Passing null or an empty array as configuration parameters indicates the removal of existing watermarks.

## setText

Setting text, supporting the simultaneous setup of multiple texts.

```
setText(config: TXTextConfig | TXTextConfig[] | null): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| config | [TXTextConfig](https://www.tencentcloud.com/document/product/267/58159#b25c0058-bd60-4aac-951d-dead07f2e446) \| [TXTextConfig](https://www.tencentcloud.com/document/product/267/58159#b25c0058-bd60-4aac-951d-dead07f2e446)[] \| null | Text configuration parameters, supporting object passage, object arrays, or null. |

> **Note:**Configuration parameters can pass object arrays, simultaneously setting multiple texts, or can pass a single object to set an individual text.Passing null or an empty array for configuration parameters denotes deletion of existing text.

# Type Definition

## TXSupportResult

Browser Support Check Result.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| isWebRTCSupported | boolean | Whether WebRTC is supported |
| isH264EncodeSupported | boolean | Is H.264 encoding supported? |
| isH264DecodeSupported | boolean | Is H.264 decoding supported? |
| isMediaDevicesSupported | boolean | Is acquisition of media devices and media streams supported? |
| isScreenCaptureSupported | boolean | Is screen capture supported? |
| isMediaFileSupported | boolean | Is retrieval of local media file streams supported? |

## TXLivePusherObserver

Callback notifications for the stream, which include the status of the streamer, statistical information, warnings, and error messages.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| onError | [onError](https://www.tencentcloud.com/document/product/267/58159#d17a7173-54c1-490c-a97b-719f91230b55) | Notification of streaming errors. |
| onWarning | [onWarning](https://www.tencentcloud.com/document/product/267/58159#a3ef8c3d-654b-4590-8780-33d638cc2608) | Stream warning notification. |
| onCaptureFirstAudioFrame | [onCaptureFirstAudioFrame](https://www.tencentcloud.com/document/product/267/58159#e773103d-ed9d-4fac-8860-c6dbf380f137) | Callback notification completed for initial audio frame capture. |
| onCaptureFirstVideoFrame | [onCaptureFirstVideoFrame](https://www.tencentcloud.com/document/product/267/58159#c6625509-8e54-4c8c-902b-f6cc4d0b3d6a) | Callback notification upon completion of the first frame video collection. |
| onPushStatusUpdate | [onPushStatusUpdate](https://www.tencentcloud.com/document/product/267/58159#6606eb8d-badd-49fb-8437-8f22ce228101) | Live stream connection status callback notification. |
| onStatisticsUpdate | [onStatisticsUpdate](https://www.tencentcloud.com/document/product/267/58159#ce29d1ed-b397-428f-b447-10e61fc38558) | Callback notification of live stream statistical data. |

### onError

Callback for streaming errors. This callback is invoked when a streaming error occurs.

```
onError(code: number, message: string, extraInfo: object): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| code | number | Error Codes. |
| message | string | Error message. |
| extraInfo | object | Extension information. |

Please see the below references for error codes:

| Enumeration | Numerical Value | Description |
| --- | --- | --- |
| TXLIVE_ERROR_WEBRTC_FAILED | -1 | Failed to call the `WebRTC` API. |
| TXLIVE_ERROR_REQUEST_FAILED | -2 | Server stream request interface returned with an error. |

### onWarning

Stream warning notification.

```
onWarning(code: number, message: string, extraInfo: object): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| code | number | Error Codes. |
| message | string | Error message. |
| extraInfo | object | Extension information. |

Please see the below references for error codes:

| Enumeration | Numerical Value | Description |
| --- | --- | --- |
| TXLIVE_WARNING_CAMERA_START_FAILED | -1001 | Camera activation failure. |
| TXLIVE_WARNING_MICROPHONE_START_FAILED | -1002 | Failed to activate the microphone. |
| TXLIVE_WARNING_SCREEN_CAPTURE_START_FAILED | -1003 | Failed to initiate screen sharing. |
| TXLIVE_WARNING_VIRTUAL_CAMERA_START_FAILED | -1004 | Failed to open the local media file. |
| TXLIVE_WARNING_CAMERA_INTERRUPTED | -1005 | Camera was interrupted (device was detached or permission was revoked by user). |
| TXLIVE_WARNING_MICROPHONE_INTERRUPTED | -1006 | Microphone was interrupted (device was unplugged or permission was annulled by user). |
| TXLIVE_WARNING_SCREEN_CAPTURE_INTERRUPTED | -1007 | Screen sharing has been interrupted (clicking the stop sharing button in Chrome browser). |

> **Note:**Error message returned when attempting to activate the camera, microphone, or screen sharing, refer to [getUserMedia exception](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia#exceptions) and [getDisplayMedia exception](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getDisplayMedia#exceptions).The extended information returned when the camera, microphone, or screen sharing unexpectedly interrupts, will contain the stream ID of the corresponding stream.

### onCaptureFirstAudioFrame

The callback notification when the first frame of audio collection is completed. If the local mixing function is enabled, it will give a callback notification when the final mixed audio stream is generated.

```
onCaptureFirstAudioFrame(): void;
```

### onCaptureFirstVideoFrame

The callback notification when the first frame of video collection is completed. If the local mixing function is enabled, it will call back when the final mixed video stream is generated.

```
onCaptureFirstVideoFrame(): void;
```

### onPushStatusUpdate

Live stream connection status callback notification.

```
onPushStatusUpdate(status: number, message: string, extraInfo: object): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| status | number | Connection status code. |
| message | string | Connection status information. |
| extraInfo | object | Extension information. |

The reference for the connection status code is as follows:

| Enumeration | Numerical Value | Description |
| --- | --- | --- |
| TXLIVE_PUSH_STATUS_DISCONNECTED | 0 | Disconnect from server |
| TXLIVE_PUSH_STATUS_CONNECTING | 1 | Establishing server connection |
| TXLIVE_PUSH_STATUS_CONNECTED | 2 | Server connection established successfully |
| TXLIVE_PUSH_STATUS_RECONNECTING | 3 | Reconnecting to the server |

### onStatisticsUpdate

Callback of the push stream statistics, primarily encompassing WebRTC related statistical data.

```
onStatisticsUpdate(statistics: object): void;
```

The parameters are described as follows:

| Field | Type | Description |
| --- | --- | --- |
| statistics | object | Push stream statistics. |
| statistics.timestamp | number | The time for data sampling, counted as milliseconds elapsed since January 1, 1970 (UTC). |
| statistics.video | object | Data pertinent to the video stream. |
| statistics.video.bitrate | number | Video bitrate, unit: bit/s. |
| statistics.video.framesPerSecond | number | Video frame rate. |
| statistics.video.frameWidth | number | Video width. |
| statistics.video.frameHeight | number | Video height. |
| statistics.video.framesEncoded | number | Encoded frame count. |
| statistics.video.framesSent | number | Transmitted Frame Count. |
| statistics.video.packetsSent | number | Number of packets sent. |
| statistics.video.nackCount | number | NACK (Negative Acknowledgement) count. |
| statistics.video.firCount | number | FIR (Full Intra Request), the number of keyframe retransmission requests. |
| statistics.video.pliCount | number | PLI(Picture Loss Indication), the number of times video frames are retransmitted due to loss. |
| statistics.video.frameEncodeAvgTime | number | Average Encoding Time, measured in: ms. |
| statistics.video.packetSendDelay | number | Average duration of local caching prior to data packet transmission, unit: ms . |
| statistics.audio | object | Data related to the audio stream. |
| statistics.audio.bitrate | number | Audio bitrate, expressed in: bit/s . |
| statistics.audio.packetsSent | number | Number of packets sent. |

> **Note:**During the live streaming process, the SDK calculates the WebRTC related data at the frequency of once per second, and then calls this callback interface to return the data.If the returned field data is empty (undefined), it indicates that the current browser cannot obtain the corresponding data. At present, only the Chrome browser can access all the data.

## TXMediaDeviceInfo

Device information.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| type | string | Device type, video - camera, audio - microphone. |
| deviceId | string | Device ID. |
| deviceName | string | Device Name. |

## TXMixingConfig

Configuration of mix streaming parameters.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| videoWidth | number | The final width of the mixed video stream. |
| videoHeight | number | The ultimate height of the mixed video stream. |
| videoFramerate | number | Frame rate of the video after final mixing. |
| backgroundColor | number | The background color of the mixed screen, in hexadecimal format, defaults to black, i.e., 0x000000. |

## TXLayoutConfig

Picture-in-picture layout parameters.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID, denotes the stream to be configured. |
| x | number | Layout of the x-coordinate. |
| y | number | Layout y-axis. |
| width | number | Layout Width. |
| height | number | Layout Height. |
| zOrder | number | Layout Hierarchy. |

> **Note:**With the top left corner as the origin (0, 0), the coordinate attributes of the element describe its center. For instance, for a video stream with a resolution of 100*100, if it appears completely adjacent to the origin in the final generated video stream, then both its x and y coordinates would be 50.The greater the zOrder value, the more prominently the video stream will be displayed, overriding the visuals of other video streams.

## TXMirrorConfig

Mirror argument.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID, denotes the stream to be configured. |
| mirrorType | number | Mirror Type: 0 - No mirror effect, 1 - Horizontal mirror, 2 - Vertical mirror, 3 - Horizontal + Vertical mirror. |

## TXNormalFilterConfig

Parameters for standard filters.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| streamId | string | Stream ID, denotes the stream to be configured. |
| contrast | number | Contrast, value range [-100, 100], 0 denotes no processing. |
| brightness | number | Brightness, the value range [-100, 100], 0 indicates no processing. |
| saturation | number | Saturation, the value ranges from [-100, 100]. 0 indicates no processing. |

## TXWatermarkConfig

Parameters for Watermark Configuration.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| image | HTMLImageElement | Watermark image object. |
| x | number | Watermark's x-coordinate. |
| y | number | Watermark Y coordinate. |
| width | number | Watermark width. |
| height | number | Watermark height. |
| zOrder | number | Watermark hierarchy. |

> **Note:**With the upper left corner being the origin point (0, 0), the coordinate attributes of the element describe the center of the element. For instance, a watermark image with a resolution of 100*100, aligned closely with the origin, appearing perfectly within the resultant video stream, has its x and y coordinates respectively situated at 50.The larger the zOrder value, the more prominently the watermark image will appear, overlaying other video streams.

## TXTextConfig

Text Configuration Parameters.

Data Structure:

| Field | Type | Description |
| --- | --- | --- |
| text | string | Text content cannot be an empty string. |
| style | object | Refer to the corresponding CSS style settings for text styles. |
| style.font | string | Font Name. |
| style.font_size | number | Font size. |
| style.font_color | string | Font color represented in hexadecimal, such as #000000. |
| style.font_alpha | number | Font transparency, range [0, 100], default 100 (opaque). |
| style.bold | number | Text bolding, 0 - No bold, 1 - Bold, default 0 . |
| style.italic | number | Font slant, 0 - normal, 1 - italic, default 0. |
| style.shadow_color | string | Text shadow color, represented in hexadecimal, for instance #000000 . |
| style.shadow_alpha | number | Text shadow opacity, ranging from [0, 100], effective when shadow_color is present, default is 100 (opaque). |
| style.stroke_color | string | Text outline color, represented in hexadecimal, such as #000000 . |
| style.stroke_thickness | number | Stroke thickness of the text, default value is 0, that is, no stroke. |
| style.background_color | string | Background color, represented in hexadecimal form, such as #000000 . |
| style.background_alpha | number | Background transparency, ranging [0, 100]. It is effective when background_color exists, default value is 100 (Opaque). |
| x | number | Text x coordinate. |
| y | number | Text Y-Axes. |
| zOrder | number | Textual Hierarchy. |

> **Note:**The origin (0,0) is the top left corner, the coordinate properties of the element describe the center point of the element. Assuming the final width of the text is 100px, the height is 50px, if the text is to snugly fit the origin appearing in the finally generated video stream, its x-coordinate is 50, y-coordinate is 25.The greater the zOrder value, the higher the text appears, overlaying other video stream images.


---
*Source: [https://www.tencentcloud.com/document/product/267/58159](https://www.tencentcloud.com/document/product/267/58159)*
