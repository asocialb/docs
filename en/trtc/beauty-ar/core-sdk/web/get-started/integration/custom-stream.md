# Custom Stream

You can use this integration mode if you want to apply effects to your own streams or want greater flexibility and control.

### Step 1. Import the SDK

- use npm package:

```
npm install tencentcloud-webar
```

```
import { ArSdk } from 'tencentcloud-webar';
```

- you can also import the SDK using the following method:

```
<script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/latest/webar-sdk.umd.js"></script><script>    // Receive T ArSdk class from window.AR    const { ArSdk } = window.AR;    ......</script>
```

### Step 2. Initialize an instance

```
// Get the authentication informationconst authData = { licenseKey: 'xxxxxxxxx', appId: 'xxx', authFunc: authFunc // For details, see âConfiguring and Using a License - Signatureâ};// The input streamconst stream = await navigator.mediaDevices.getUserMedia({ audio: true, video: { width: w, height: h }})const config = { module: {     beautify: true, // Whether to enable the effect module, which offers beautification and makeup effects as well as stickers     segmentation: true, // Whether to enable the keying module, which allows you to change the background     segmentationLevel: 0 // Optional values: 0 | 1 | 2. The higher the value, the better the segmentation effect, but this also increases resource usage and hardware requirements for the device. }, auth: authData, // The authentication information input: stream, // The input stream beautify: { // The effect parameters for initialization (optional)     whiten: 0.1,     dermabrasion: 0.3,     eye: 0.2,     chin: 0,     lift: 0.1,     shave: 0.2,     // For more beauty parameter settings, please refer to theãAPI Documentationã } // For more config settings, please refer to theãAPI Documentationã}const sdk = new ArSdk( // Pass in a config object to initialize the SDK config)
```

> **Note:**The loading of the effect and segmentation modules takes time and consumes resources. You can enable only the module you need during initialization. A module not enabled will not be loaded or initialized.

2. For `input`, you can also pass in `string|HTMLImageElement` to process image, and `HTMLVideoElement` to process video.

```
const config = { auth: authData, // The authentication information input: 'https://xxx.png', // The input stream, also support image and video element}const sdk = new ArSdk( // Pass in a config object to initialize the SDK config)// You can display the effect and filter list in the `created` callback. For details, see âSDK Integration - Parameters and APIsâ.sdk.on('created', () => { // Get the built-in makeup effects sdk.getEffectList({     Type: 'Preset',     Label: 'Makeup', }).then(res => {     effectList = res }); // Get the built-in filters sdk.getCommonFilter().then(res => {     filterList = res })})// Call `setBeautify`, `setEffect`, or `setFilter` in the `ready` callback// For details, see âSDK Integration - Configuring Effectsâsdk.on('ready', () => { // Configure beautification effects sdk.setBeautify({     whiten: 0.2 }); // Configure special effects sdk.setEffect({     id: effectList[0].EffectId,     intensity: 0.7 }); // Configure filters sdk.setFilter(filterList[0].EffectId, 0.5)})
```

### Step 3. Play the stream

- If you want to display a video image as quickly as possible, get and play the stream in the `cameraReady` callback. Because the SDK hasnât loaded the resources or completed initialization at this point, the original video will be played, The effect will be automatically applied once the SDK initialization is complete.

```
sdk.on('cameraReady', async () => {  // By getting the output stream in the `cameraReady` callback, you can display a video image sooner. However, because the initialization parameters have not taken effect at this point, the output stream obtained will be the same as the original stream.  // You can choose this method if you want to display a video image as soon as possible but do not need to apply effects to the video the moment it is displayed.  // You donât need to update the stream after the effects start to work.  const output = await ar.getOutput();  // Use `video` to preview the output stream  const video = document.createElement('video')  video.setAttribute('playsinline', '');  video.setAttribute('autoplay', '');  video.srcObject = output  document.body.appendChild(video)  video.play()})
```

- If you want to play the video after the SDK is initialized and effects are applied, get and play the output stream in the `ready` playback.

```
sdk.on('ready', async () => {  // If you get the output stream in the `ready` callback, because the initialization parameters have taken effect at this point, the output stream obtained will show effects.  // The `ready` callback occurs later than `cameraReady`. You can get the output stream in `ready` if you want your video to show effects the moment it is displayed but do not expect it to be displayed as soon as possible.  const output = await ar.getOutput();  // Use `video` to preview the output stream  const video = document.createElement('video')  video.setAttribute('playsinline', '');  video.setAttribute('autoplay', '');  video.srcObject = output  document.body.appendChild(video)  video.play()})
```

### Step 4. Get the output

```
const output = await sdk.getOutput()
```

To learn more about how to publish the processed streams, see [Publishing Using TRTC](https://www.tencentcloud.com/document/product/1143/53885) and [Publishing over WebRTC](https://www.tencentcloud.com/document/product/1143/53886).

> **Note:**If the input passed in is an image, a string-type data URL will be returned by default. You can set getOutput(OUTPUT_TYPES.MEDIA_STREAM) to force the return type to be MediaStream;  other input scenarios will always return the MediaStream type.The video track of the output stream is processed in real time by the Tencent Effect SDK. The audio track (if any) is kept.`getOutput` is an async API. The output will be returned only after the SDK is initialized and has generated a stream.You can pass an `FPS` parameter to `getOutput` to specify the output frame rate (for example, 15). If you do not pass this parameter, the original frame rate will be kept.You can call `getOutput` multiple times to generate streams of different frame rates for different scenarios (for example, you can use a high frame rate for preview and a low frame rate for stream publishing).

### Step 5. Configuring effects

For detailed directions, see [Configuring Effects](https://www.tencentcloud.com/document/product/1143/54291).

## Updating the Input Stream

If you want to feed a new input stream to the SDK after changing the device or enabling/disabling the camera, you donât need to initialize the SDK again. Just call `sdk.updateInputStream` to update the input stream.
The following code shows you how to use `updateInputStream` to update the input stream after switching from the computerâs default camera to an external camera.

```
async function getVideoDeviceList(){    const devices = await navigator.mediaDevices.enumerateDevices()    const videoDevices = []    devices.forEach((device)=>{        if(device.kind === 'videoinput'){            videoDevices.push({                label: device.label,                id: device.deviceId            })        }    })    return videoDevices}async function initDom(){    const videoDeviceList = await getVideoDeviceList()    let dom = ''    videoDeviceList.forEach(device=>{        dom = `${dom}        <button id=${device.id} onclick='toggleVideo("${device.id}")'>${device.label}<nbutton>        `    })    const div = document.createElement('div');    div.id = 'container';    div.innerHTML = dom;    document.body.appendChild(div);}async function toggleVideo(deviceId){    const stream = await navigator.mediaDevices.getUserMedia({        video: {            deviceId,            width: 1280,            height: 720,          }    })    // Call an API provided by the SDK to change the input stream.     // After the input stream is updated, you donât need to call `getOutput` again. The SDK will get the output.    sdk.updateInputStream(stream, true) // The second parameter defaults to true, indicating that the old mediaTrack will be stopped; if you need to retain it, then set to false. }initDom()
```

## Pausing and Resuming Detection

You can call `disable` and `enable` to manually pause and resume detection. Pausing detection can reduce CPU usage.

```
<button id="disable">Disable detection</button><button id="enable">Enable detection</button>
```

```
// Disable detection and output the original streamdisableButton.onClick = () => {    sdk.disable()}// Enable detection and output a processed streamenableButton.onClick = () => {    sdk.enable()}
```

## Play and Pause output screen

You can use the `stop` and `resume` methods to pause and play the output screen. In the paused state, the screen remains static and playback is halted.

```
<button id="stop">stop</button><button id="resume">resume</button>
```

```
// stop outputstopButton.onClick = () => {    sdk.stop()}// resume outputresumeButton.onClick = () => {    sdk.resume()}
```


---
*Source: [https://trtc.io/document/50102](https://trtc.io/document/50102)*
