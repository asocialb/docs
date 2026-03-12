# Built-in Camera

You can choose this integration mode if you want to use the SDK with a deviceâs built-in camera or if your business scenario involves interaction with the built-in camera.

## Step 1. Import the SDK

- use npm package:

```
npm install tencentcloud-webar
```

```
import { ArSdk } from 'tencentcloud-webar';
```

- you can also import the SDK using the following method:

```
<script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/latest/webar-sdk.umd.js"></script><script>    // Receive ArSdk class from window.AR    const { ArSdk } = window.AR;    ......</script>
```

## Step 2. Initialize an Instance

```
// Get the authentication informationconst authData = {    licenseKey: 'xxxxxxxxx',    appId: 'xxx',    authFunc: authFunc // For details, see âConfiguring and Using a License - Signatureâ};const config = {    module: {        beautify: true, // Whether to enable the effect module, which offers beautification and makeup effects as well as stickers        segmentation: true, // Whether to enable the keying module, which allows you to change the background        segmentationLevel: 0 // Optional values: 0 | 1 | 2. The higher the value, the better the segmentation effect, but this also increases resource usage and hardware requirements for the device.    },    auth: authData, // The authentication information    camera: { // Pass in the camera parameters        width: 1280,        height: 720    },    beautify: { // The effect parameters for initialization (optional)        whiten: 0.1,        dermabrasion: 0.3,        eye: 0.2,        chin: 0,        lift: 0.1,        shave: 0.2,        // For more beauty parameter settings, please refer to theãAPI Documentationã    },    // For more config settings, please refer to theãAPI Documentationã}const sdk = new ArSdk(    // Pass in a config object to initialize the SDK    config)let effectList = [];let filterList = [];sdk.on('created', () => {    // You can display the effect and filter list in the `created` callback. For details, see âSDK Integration - Parameters and APIsâ.    sdk.getEffectList({        Type: 'Preset',        Label: 'Makeup',    }).then(res => {        effectList = res    });    sdk.getCommonFilter().then(res => {        filterList = res    })})// Call `setBeautify`, `setEffect`, or `setFilter` in the `ready` callback// For details, see âSDK Integration - Configuring Effectsâsdk.on('ready', () => {    // Configure beautification effects    sdk.setBeautify({        whiten: 0.2    });    // Configure special effects    sdk.setEffect({        id: effectList[0].EffectId,        intensity: 0.7    });    // Configure filters    sdk.setFilter(filterList[0].EffectId, 0.5)})
```

> **Note:**The loading of the effect and keying modules takes time and consumes resources. You can enable only the module you need during initialization. A module not enabled will not be loaded or initialized.If you specify the `camera` parameter of `config`, the video data the SDK captures from the deviceâs camera will be used as the input. We also offer some basic device management APIs. For details, see [Step 6. Control Devices](#step6).

## Step 3. Play the Stream

- If you want to display a video image as quickly as possible, get the player in the `cameraReady` callback. Because the SDK hasnât loaded the resources or completed initialization at this point, the player can only play the original video.

```
sdk.on('cameraReady', async () => {  // Initialize a player of the SDK. `my-dom-id` is the ID of the playerâs container.  const player = await sdk.initLocalPlayer('my-dom-id')  // Play the video  await player.play()})
```

- If you want to play the video after the SDK is initialized and effects are applied, get the player in the `ready` playback.

```
sdk.on('ready', async () => {  // Initialize a player of the SDK. `my-dom-id` is the ID of the playerâs container.  const player = await sdk.initLocalPlayer('my-dom-id')  // Play the video  await player.play()})
```

> **Note:**The player obtained by `initLocalPlayer` is muted by default. If you unmute it, there may be echoes.The player obtained is integrated with the `sdk.getOutput()` API.

The player object obtained by `initLocalPlayer` is integrated with the following APIs:

| API | Description | Request Parameter | Return Value |
| --- | --- | --- | --- |
| play | Plays the video. | - | Promise; |
| pause | Pauses the video. This does not stop the stream. You can resume the playback. | - | - |
| stop | Stops the video. This stops the stream. | - | - |
| mute | Mutes the video. | - | - |
| unmute | Unmutes the video. | - | - |
| setMirror | Sets whether to mirror the video. | true\|false | - |
| getVideoElement | Gets the built-in video object. | - | HTMLVideoElement |
| destroy | Terminates the player. | - | - |

> **Note:**The playerâs behaviors are affected by [camera settings](#step6). Camera settings prevail over the settings of `LocalPlayer`.For example, after you call `camera.muteVideo` to disable video, playback will not start even if you call `play`.After you call `camera.unmuteVideo` to enable video, the player will play the video automatically.
> Therefore, if you specify `camera`, you donât need to manually configure `localPlayer`.

## Step 4. Get the Output

```
const output = await sdk.getOutput()
```

> **Note:**If you use the built-in camera, the type of all media returned by `getOutput` is `MediaStream`.The video track of the output stream is processed in real time by the Tencent Effect SDK. The audio track (if any) is kept.`getOutput` is an async API. The output will be returned only after the SDK is initialized and has generated a stream.You can pass an `FPS` parameter to `getOutput` to specify the output frame rate (for example, 15). If you do not pass this parameter, the original frame rate will be kept.To learn more about how to publish the processed streams, see [Publishing Using TRTC](https://www.tencentcloud.com/document/product/1143/53885) and [Publishing over WebRTC](https://www.tencentcloud.com/document/product/1143/53886).

## Step 5. Configuring Effects

For detailed directions, see [Configuring Effects](https://www.tencentcloud.com/document/product/1143/54291).

## Step 6. Control Devices

```
const output = await sdk.getOutput()// Your business logic// ...// `sdk.camera` will have been initialized after `getOutput`. You can get an instance directly.const cameraApi = sdk.camera// Get the device listconst devices = await cameraApi.getDevices()console.log(devices)// Disable the video track// cameraApi.muteVideo()// Enable the video track// cameraApi.unmuteVideo()// Change to a different camera by specifying the device ID (if there are multiple cameras)// await cameraApi.switchDevice('video', 'your-device-id')
```

If you want to get an `sdk.camera` instance as soon as possible, you can get it in the `cameraReady` callback.

```
// Initialization parameters// ...const sdk = new ArSdk(    config)let cameraApi;sdk.on('cameraReady', async () => {    cameraApi = sdk.camera    // Get the device list    const devices = await cameraApi.getDevices()    console.log(devices)    // Disable the video track    // cameraApi.muteVideo()    // Enable the video track    // cameraApi.unmuteVideo()    // Change to a different camera by specifying the device ID (if there are multiple cameras)    // await cameraApi.switchDevice('video', 'your-device-id')})
```

You can use the following APIs of `camera` to control the built-in camera.

| API | Description | Request Parameter | Return Value |
| --- | --- | --- | --- |
| getDevices | Gets all devices. | - | Promise<Array<MediaDeviceInfo>> |
| switchDevice | Switches the device. | type:string, deviceId:string | Promise |
| muteAudio | Mutes the current stream. | - | - |
| unmuteAudio | Unmutes the current stream. | - | - |
| muteVideo | Disables the video track of the camera stream. This does not stop the stream. | - | - |
| unmuteVideo | Enables the video of the camera stream. | - | - |
| stopVideo | Disables the camera. This stops the video stream, but the audio stream is not affected. | - | - |
| restartVideo | Enables the camera. This API can only be called after `stopVideo`. | - | Promise |
| stop | Disables the current camera and audio device. | - | - |


---
*Source: [https://trtc.io/document/50101](https://trtc.io/document/50101)*
