# API Document

This document describes the core parameters and methods of the Beauty AR Web SDK.

> **Note:**The Beauty AR Web SDK relies on hardware acceleration to achieve smooth rendering. The SDK allows you to check whether a browser supports hardware acceleration. You can block the browser if it does not support hardware acceleration.

```
import {ArSdk, isWebGLSupported} from 'tencentcloud-webar'if(isWebGLSupported()) {    const sdk = new ArSdk({    ...})} else {    // The browser blocking logic}
```

## Initialization Parameters

```
import { ArSdk } from 'tencentcloud-webar'// Initialize the SDKconst sdk = new ArSdk({... // Refer to the following Config definition})
```

`Config` of the SDK supports the following initialization parameters:

| Parameters | Description | Type | Required |
| --- | --- | --- | --- |
| module | The module configuration | type SegmentationLevel = 0 \| 1 \| 2 // since version 1.0.19 type ModuleConfig = {  beautify: boolean // The default is `true`.  segmentation: boolean // The default is `false`  segmentationLevel: SegmentationLevel // The default is 0.  handGesture: boolean // Whether to enable gesture recognition, default is false. Supported in versions after 1.0.23.  handLandmark: boolean // Whether to enable hand tracking, default is false. Supported in versions after 1.0.23. It is not recommended to enable this simultaneously with beautify.} | No. It is `{beautify: true, segmentation: false, segmentationLevel: 0,handLandmark: false}` by default. |
| auth | The authentication parameter | type AuthConfig = {  licenseKey: string // It can be obtained on the **Web licenses** page in the console.  appId: string // It can be viewed in **Account Info** > **Basic Info** in the console.  authFunc:() => Promise<{    signature:string,    timestamp:string  }> // Refer to the license configuration.} | Yes |
| input | Source | MediaStream \| HTMLImageElement \| String \| HTMLVideoElement | No |
| camera | Built-in Camera | type CameraConfig = {    width: number, // The video width.    height: number, // The video height.    mirror: boolean, // Whether to horizontally flip the video.    frameRate: number // The capturing frame rate.} | No |
| mirror | Mirrored or not, mirroring of input streams is supported.(supported since 1.0.19) | Boolean | No |
| beautify | The beauty filter parameter | type BeautifyOptions = {      whiten?: number, // The brightening effect. Value range: 0-1.       dermabrasion?: number // The smooth skin effect. Value range: 0-1.       lift?: number // The slim face effect. Value range: 0-1.       shave?: number // The face width. Value range: 0-1.       eye?: number // The big eyes effect. Value range: 0-1.       chin?: number // The chin effect. Value range: 0-1.    // The following parameters are only available since version 1.0.11       darkCircle?: number; // The dark circle effect. Value range: 0-1.       nasolabialFolds?: number; // The nasolabial folds effect. Value range: 0-1.       cheekbone?: number; // The cheek bone effect. Value range: 0-1.       head?: number; // The head effect. Value range: 0-1.       eyeBrightness?: number; // The eye brightness effect. Value range: 0-1.       lip?: number; // The lip effect. Value range: 0-1.       forehead?: number; // The forehead effect. Value range: 0-1.       nose?: number; // The nose effect. Value range: 0-1.       usm?: number; // The distinct effect. Value range: 0-1.} | No |
| background | The background parameter | type BackgroundOptions = {    type: 'image' \| 'blur' \| 'transparent' \| 'video',  // from version 1.0.23, support video-type dynamic background.    src?: string, // image \| video file address} | No |
| loading | The configuration of the built-in loading icon | type loadingConfig = {    enable: boolean,    size?: number    lineWidth?: number    strokeColor?: number} | No |
| language | i18n, 'jp' supported form 1.0.26 version | String: zh \| enï½jp | No, default is 'zh' |
| logLevel | Print console log level | 'OFF' \| 'ERROR' \| 'WARN' \| 'DEBUG' \| 'TRACE' \| 'INFO' | No, default is INFOï¼print all sdk log |
| initReport | Whether to initialize the log reporting module | Boolean | No, default is true |
| worker | Whether to disable the browser worker to optimize performance in specific scenarios. | String: auto \| disable | No, default is autoï¼The SDK determines whether to use workers based on the current browser environment. |
| proxyServer | Intranet Proxy Mode Utilization | type proxyServeConfig = {  webarProxy: string; // Intranet address of the interface proxy  staticProxy: string; // Intranet address of the resource proxy} | No |

## Callbacks

```
let effectList = [];let filterList = [];// Using the callbacks of the SDKsdk.on('created', () => {    // Pull and display the filter and effect list in the `created` callback    sdk.getEffectList({        Type: 'Preset',        Label: 'Makeup',    }).then(res => {        effectList = res    });    sdk.getCommonFilter().then(res => {        filterList = res    })})sdk.on('cameraReady', async () => {    // By getting the output stream in the `cameraReady` callback, you can display a video image sooner, but the initialization parameters have not taken effect at this point.    // You can choose this method if you want to display a video image as soon as possible but do not need to apply effects to the video the moment it is displayed.    // You donât need to update the stream after the effects start to work.    const arStream = await ar.getOutput();    // Play the stream locally    // localVideo.srcObject = arStream})sdk.on('ready', () => {    // Get the output stream in the `ready` callback. The initialization parameters have taken effect at this point.    // You can get the output stream in `ready` if you want your video to show effects the moment it is displayed but do not expect it to be displayed as soon as possible.    // Between the two methods, choose the one that fits your needs.    const arStream = await ar.getOutput();    // Play the stream locally    // localVideo.srcObject = arStream    // Call `setBeautify`, `setEffect`, or `setFilter` in the `ready` callback    sdk.setBeautify({        whiten: 0.3    });    sdk.setEffect({        id: effectList[0].EffectId,        intensity: 0.7    });    sdk.setEffect({        id: effectList[0].EffectId,        intensity: 0.7,        filterIntensity: 0.5 // In v0.1.18 and later, you can use this parameter to set the filter strength of a special effect. If you do not pass this parameter, the strength specified for the effect will be used.    });    sdk.setFilter(filterList[0].EffectId, 0.5)})// Triggered when a change in gesture is detected after enabling gesture recognitionsdk.on('handGesture',(hands)=>{    // none, thumb_up, thumb_down, victory, pointing_up, open_palm, iloveyou})// Error callback that affects the occurrence of errors during SDK usagesdk.on('error', (data)=>{    console.log('error', data.code, data.message)})// Warning callback, commonly triggered by the SDK when it detects an increase in time consumption.sdk.on('warning', (data)=>{    console.log('warning', data.code, data.message)})
```

| Events | Description | Callback Parameter |
| --- | --- | --- |
| created | The SDK authentication was completed and the instance was created successfully. | - |
| cameraReady | The SDK generated a video output (the video is not yet processed). | - |
| ready | Detection has been initialized. Effects are now applied to the output video. You can change the effect settings. | - |
| error | This callback is triggered when the SDK encounters an error. | The `error` object |
| warning | This callback is triggered when the SDK encounters a warning. | The `warning` object |
| handGesture | Triggered when a change in gesture is detected after enabling gesture recognition | Recognized gesture |
| detectStatusChange | Triggered when the face detection status changes. | Boolean, Whether a face is detected |

## APIs

| API | Parameters | Back | Description |
| --- | --- | --- | --- |
| setBeautify(options) | type BeautifyOptions = {  whiten?: number, // The brightening effect. Value range: 0-1.  dermabrasion?: number // The smooth skin effect. Value range: 0-1.  lift?: number // The slim face effect. Value range: 0-1.  shave?: number // The face width. Value range: 0-1.  eye?: number // The big eyes effect. Value range: 0-1.  chin?: number // The chin shaping effect. Value range: 0-1.  darkCircle?: number; // The dark circle effect. Value range: 0-1.  nasolabialFolds?: number; // The nasolabial folds effect. Value range: 0-1.  cheekbone?: number; // The cheek bone effect. Value range: 0-1.  head?: number; // The head effect. Value range: 0-1.  eyeBrightness?: number; // The eye brightness effect. Value range: 0-1.  lip?: number; // The lip effect. Value range: 0-1.  forehead?: number; // The forehead effect. Value range: 0-1.  nose?: number; // The nose effect. Value range: 0-1.  usm?: number; // The distinct effect. Value range: 0-1.} | - | This API is used to set the beauty filter parameter. You need to enable the beauty filter module. |
| setEffect(effects, callback) | effects: Effect ID \| Effect object \| (Effect ID \| Effect object) arraytype Effect = {    id: string,    intensity: number, // The effect strength. Value range: 0-1. Default: 1.    filterIntensity: number // The filter strength of an effect (supported in v0.1.18 and later). Value range: 0-1. By default, this parameter is the same as `intensity`.}callback: The callback for successful configuration | - | This API is used to set an effect. You need to enable the beauty filter module.**3D effects are supported by Advanced licenses only.** |
| setAvatar(params) | {    mode: 'AR' \| 'VR',    effectId?: string, // Pass through `effectId` to use the built-in model    url?: string, // Pass through `url` to use the custom model    backgroundUrl?: string, // Background image URL, which takes effect only in VR mode.} | - | This API is used to set an animoji or virtual avatar. You need to enable the beauty filter module.**Supported by Advanced licenses only** |
| setBackground(options) | {    type: 'image\|video\|blur\|transparent', // from version 1.0.23, support video-type dynamic background.    src: string, // This parameter is required only if `type` is `image` or `video`.} | - | To configure the background, it is necessary to activate the portrait segmentation module. |
| setForeground(options)**ï¼Since v1.0.23 ï¼** | {    type: 'image\|video',    src: string // Resource Path: Base64 or Online URL} | - | Set a fixed fullscreen foreground effect. |
| setSegmentationLevel(level) | level: 0 \| 1 \| 2 | - | Switch the background segmentation model |
| setFilter(id, intensity, callback) | id: The filter IDintensity: The filter strength. Value range: 0 - 1.callback: The callback for successful configuration. | - | This API is used to set a filter. |
| getEffectList(params) | {    PageNumber: number, // page number, default is 0    PageSize: number,// page size,default is 1000    Name: '', // effect name    Label: string \| Array, // effect label    Type: 'Custom' \| 'Preset' // Custom effect or Preset effect} |  | This API is used to pull the list of effects. |
| getAvatarList(type) | type = 'AR' \| 'VR' | The list of virtual avatars | Pull the list of Animoji/virtual avatars. |
| getEffect(effectId) | effectId: The effect ID | The information of a single effect | This API is used to pull the information of the specified effect. |
| getCommonFilter() | - | The list of built-in filters | This API is used to get the list of built-in filters. |
| async initCore() |  {  input?:MediaStream\|HTMLImageElement\|String; // The input source   camera?:CameraConfig; // Only for camera mode  mirror?:boolean;  // Mirror or not} | - | For pre-initialization scenarios only, it provides input information to the SDK. For details, see [Loading Optimization](https://www.tencentcloud.com/document/product/1143/50103) |
| async updateInputStream(src, stopOldTracks) | src: New input stream (`MediaStream`)stopOldTracks: stop the old MediaTrack or not, default is true | - | This API is used to update the input stream. |
| updateInputImage(options)**ï¼since v1.0.24ï¼** | {width: number;// image render widthheight: number; // image render heightinput: string;// image src} | - | Update input image |
| async getOutput(fps:number,type:OUTPUT_TYPES) | enum OUTPUT_TYPES {  IMAGE = 3,  MEDIA_STREAM = 4,}fps (optional): The output frame rate, default is consistent with the input media's FPS.type(optional):  3 \| 4 // 3 for image, 4 for media stream. The output defaults to 3 when the input is an image, and defaults to 4 when the input is not an image. | MediaStream\|String | - |
| disable() | - | - | This API is used to disable facial detection, which can reduce CPU usage. After it's disabled, the original stream will be returned. |
| enable() | - | - | This API is used to enable facial detection. After it's enabled, the stream returned will have been processed. |
| stop() | - | - | Pause the screen, the screen is frozen. |
| resume() | - | - | Resume the screen, the screen is playing. |
| async takePhoto() | - | {    data: Uint8Array,     width: number,     height: number} | This API is used to take a photo and return an object containing the buffer data. |
| async initLocalPlayer(id) | id: string // HTML DOM id for local preview. | - | Allowing the media stream output by the SDK to be played in a specified DOM container as a video. |
| async resetCore(input) | input: MediaStream\|HTMLImageElement\|String | - | Call this API to recover when a context lost error occurs. |
| destroy() | - | - | This API is used to terminate the current SDK instance and relevant texture resources. |

## Error Handling

The error object returned by the error callback includes the error code and error message, which facilitate troubleshooting.

```
sdk.on('error', (error) => {    // Handle an error in the error callback    const {code, message} = error    ...})
```

| Error Code | Description | Remarks |
| --- | --- | --- |
| 10000001 | The current browser environment is incompatible. | Recommend the user to use Chrome, Firefox, Safari, or the Weixin browser. |
| 10000002 | The render context is missing. | - |
| 10000003 | The rendering is slow. | Consider reducing the video resolution or disabling the feature. |
| 10000005 | An error occurred while parsing the input source. | - |
| 10000006 | Lag may occur due to insufficient browser support. | Recommend the user to use Chrome, Firefox, Safari, or the Weixin browser. |
| 10001101 | An error occurred while configuring the effect. | - |
| 10001102 | An error occurred while configuring the filter. | - |
| 10001103 | The effect strength parameter is incorrect. | - |
| 10001104 | sdk disabled, Cannot set effects | - |
| 10001105 | Invalid effect ID | - |
| 10001201 | Failed to turn on the camera. | - |
| 10001202 | The camera stopped. | - |
| 10001203 | Failed to get the camera permission. | The user needs to enable the camera permission by going to **Settings** > **Privacy** > **Camera**. |
| 10001204 | Cannot access media devices (despite being authorized). | Cannot find a media type that satisfies the request parameters, or a system error is preventing access to the device. |
| 10001205 | Microphone permission not allowed | The user needs to enable the microphone permission by going to **Settings** > **Privacy** > **Microphone**. |
| 10001206 | Some browsers may have discrepancies between the width and height returned by the getUserMedia interface and the user's settings. | - |
| 10004001 | Camera and microphone permission issues require a page refresh to continue using. | - |
| 20002001 | The authentication parameter is missing. | - |
| 20001001 | Authentication failed | Make sure you have created a license and the signature is correct. |
| 20001002 | The API request failed. | The error callback will return the data returned by the API. For details, see [API Error Codes](https://www.tencentcloud.com/document/product/1143/50107). |
| 20001003 | Failed to authenticate the effects setting interface | Access to this effect is denied; the Standard License cannot use features of the Advanced License. |
| 20001004 | Signature timeout | Signature timeout, and an error still occurs after retrying. |
| 20001005 | Authorize timeout | Authorize timeout, and an error still occurs after retrying. |
| 40000000 | An uncaught exception occurred. | - |
| 40000001 | As the current SDK version is too low, certain effects cannot be correctly displayed. Upgrade the SDK version. | - |
| 50000002 | The effect is lost due to the resolution change. | The effect needs to be reconfigured. |

### Warning Handling

The object returned in the warning callback contains a warning code and a warning message.

```
sdk.on('warning', (warning) => {    // Handle a warning in the warning callback    const {code, message} = warning    ...})
```

| Error Code | Description | Remarks |
| --- | --- | --- |
| 50005 | Detection took too long. | Dynamic monitoring: A warning is issued when the processing time for a single frame exceeds 150ms, indicating that the rendering frame rate drops below 10fps, resulting in stuttering. |

### Handling the missing render context error

On some computers, if the SDK is in the background for a long time, the `contextlost` error may occur. In such cases, you can call `ArSdk.prototype.resetCore(input: MediaStream)` to resume rendering.

```
sdk.on('error', async (error) => {    if (error.code === 10000002) {        const newInput = await navigator.mediaDevices.getUserMedia({...})        await sdk.resetCore(newInput)    }})
```


---
*Source: [https://trtc.io/document/50106](https://trtc.io/document/50106)*
