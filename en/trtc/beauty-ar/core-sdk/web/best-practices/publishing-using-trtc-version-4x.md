# Publishing Using TRTC (Version 4.x)

> **Noteï¼**This tutorial is based on the 4.x TRTC Web SDK. If you are using the 5.x version of the SDK, please refer to [this tutorial](https://www.tencentcloud.com/document/product/1143/67329#).

## Before You Start

- Please read the [integration guide](https://www.tencentcloud.com/document/product/1143/50099) for Beauty AR Web.
- Follow the steps in [Integration (No UI)](https://www.tencentcloud.com/document/product/647/35096) to integrate the TRTC web SDK.
- Try [running a TRTC web demo](https://www.tencentcloud.com/document/product/647/35607) in your local project.

## Directions

### Step 1. Import the Beauty AR Web SDK

```
<script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/latest/webar-sdk.umd.js"></script>
```

> **Note:**The above example uses a script tag to import the SDK. You can also [import it using an npm package](https://www.tencentcloud.com/document/product/1143/50099).

### Step 2. Understand the stream initialization logic of TRTC

```
// Capture audio and video from the mic and camera for the local streamconst localStream = TRTC.createStream({ userId, audio: true, video: true });localStream.initialize().then(() => { console.log('initialize localStream success'); // The local stream was initialized successfully. You can call `Client.publish(localStream)` to publish the local stream..catch(error => { console.error('failed initialize localStream ' + error);});
```

This is the most common local stream initialization method.

2. `TRTC.createStream` also allows you to use an external audio/video source for the local stream so that you can use your own custom processing on the stream (such as applying beautification effects to the video). Below is an example:

```
// Get the custom streamconst stream = await this.ar.getOutput();// Use the audio/video source to create a local stream objectconst audioTrack = stream.getAudioTracks()[0];const videoTrack = stream.getVideoTracks()[0];const localStream = TRTC.createStream({ userId, audioSource: audioTrack, videoSource: videoTrack });localStream.initialize().then(() => { console.log('initialize localStream success'); // The local stream was initialized successfully. You can call `Client.publish(localStream)` to publish the local stream..catch(error => { console.error('failed initialize localStream ' + error);});
```

For detailed directions on how to use `createStream`, see [TRTC SDK documentation](https://web.sdk.qcloud.com/trtc/webrtc/doc/zh-cn/TRTC.html#createStream).

3. To process the local stream using Tencent Effect, you need to use the second method above. Before you call `getMyStream`, [initialize the Beauty AR Web SDK](#step3) first.

### Step 3. Initialize the Beauty AR Web SDK

```
const { ArSdk } = window.AR/** ----- Authentication configuration ----- *//** * The APPID of your Tencent Cloud account. *  * You can view your APPID in the [Account Center](https://console.cloud.tencent.com/developer). */const APPID = ''; // Set it to your Tencent Cloud account APPID./** * Web LicenseKey *  * Log in to the RT-Cube console and click [Web Licenses](https://console.cloud.tencent.com/vcube/web) on the left sidebar. A license key will be automatically generated after you create a license. */const LICENSE_KEY = ''; // Set it to your license key./** * The token used to calculate the signature. *  * Note: This method is only suitable for debugging. In a production environment, you should store the token and calculate the signature on your server. The front end can get the signature by calling an API. For details, see * [Signature](https://cloud.tencent.com/document/product/616/71370#.E7.AD.BE.E5.90.8D.E6.96.B9.E6.B3.95) */const token = ''; // Set it to your token./** ----------------------- *//** * Get the signature * * Note: This method is only suitable for debugging. In a production environment, you should calculate the signature on your server. The front end can get the signature by calling an API. ** Example: * async function () { *  return fetch('http://xxx.com/get-ar-sign').then(res => res.json()); * }; */const getSignature = function () {    const timestamp = Math.round(new Date().getTime() / 1000);    const signature = sha256(timestamp + token + APPID + timestamp).toUpperCase();    return { signature, timestamp };};let w = 1280;let h = 720;// The basic settings for the Tencent Effect SDKconst config = {    camera: { //This indicates that the SDK will capture streams from the camera.        width: 1280,        height:720    },    auth: {        licenseKey: LICENSE_KEY,        appId: APPID,        authFunc: getSignature    },    // Configure the initial effects (optional)    beautify: {        whiten: 0.1, // The brightening effect. Value range: 0-1.        dermabrasion: 0.5, // The smooth skin effect. Value range: 0-1.        lift: 0.3, // The slim face effect. Value range: 0-1.        shave: 0, // The V shape effect. Value range: 0-1.        eye: 0, // The big eyes effect. Value range: 0-1.        chin: 0, // The chin effect. Value range: 0-1.    },    language: 'en',    â¦â¦}// Pass `config` to the Tencent Effect SDKconst ar = new ArSdk(config);// You can display the effect and filter list in the `created` callback.ar.on('created', () => {    // Get the built-in makeup effects and stickers    ar.getEffectList({        Type: 'Preset'    }).then((res) => {        const list = res.map(item => ({            name: item.Name,            id: item.EffectId,            cover: item.CoverUrl,            url: item.Url,            label: item.Label,            type: item.PresetType,        }));        const makeupList = list.filter(item=>item.label.indexOf('Makeup')>=0)        const stickerList = list.filter(item=>item.label.indexOf('Sticker')>=0)        // Show the makeup and sticker lists        renderMakeupList(makeupList);        renderStickerList(stickerList);    }).catch((e) => {        console.log(e);    });    // Get the built-in filters    ar.getCommonFilter().then((res) => {        const list = res.map(item => ({            name: item.Name,            id: item.EffectId,            cover: item.CoverUrl,            url: item.Url,            label: item.Label,            type: item.PresetType,        }));        // Show the filter list        renderFilterList(list);    }).catch((e) => {        console.log(e);    });});ar.on('ready', (e) => {    // After receiving the `ready` callback, you can call `setBeautify`, `setEffect`, or `setFilter` to configure effects.    //  For example, you can use `range input` to set the smooth skin effect:    $('#dermabrasion_range_input').change((e) => {        ar.setBeautify({            dermabrasion: e.target.value, // The smooth skin effect. Value range: 0-1.        });    });    // In the `created` callback, apply the effects based on user interactions with the makeup effect and sticker lists. The `setEffect` API supports three types of request parameters. For details, see the SDK integration guide.    $('#makeup_list li').click(() => {        ar.setEffect([{id: effect.id, intensity: 1}]);    });    $('#sticker_list li').click(() => {        ar.setEffect([{id: effect.id, intensity: 1}]);    });    // In the `created` callback, apply the filter based on user interactions with the filter list. The value `1` for the second parameter of `setFilter` indicates the filter strength. For details, see the SDK integration guide.    ar.setFilter(filterList[0].id, 1);    $('#filter_list li').click(() => {        ar.setFilter(filter.id, 1);    });});ar.on('error', (e) => {    console.log(e);});
```

The code above shows you how to initialize the Beauty AR Web SDK, as well as how to respond to user interactions in the `ready` callback. To learn more about UI interactions, you can download the code package at the end of this document.

### Step 4. Initialize a TRTC stream

```
// Get the output stream of the Tencent Effect SDKconst arStream = await this.ar.getOutput();const audioSource = arStream.getAudioTracks()[0];const videoSource = arStream.getVideoTracks()[0];// create a local stream with audio/video from custom sourcethis.localStream_ = TRTC.createStream({    audioSource,    videoSource});
```

### Step 5. Play the stream

> **Note:**For the example project, you need to start the web service of your device and make sure that the HTML file can be accessed via the specified port.

After entering the room, you should be able to view the stream with effects applied (`index_AR.html` in the sample code). After that, you can open a new browser tab and enter the room to simulate the entry of a new user.

### Step 6. Control devices

```
const cameraApi = this.ar.camera;// Get the device listconst devices = await cameraApi.getDevices()console.log(devices)// Switch to a different camera// await cameraApi.switchDevice('video', 'your-video-device-id')// Disable the video track// cameraApi.muteVideo()// Enable the video track// cameraApi.unmuteVideo()// Disable the audio track// cameraApi.muteAudio()// Enable the audio track// cameraApi.unmuteAudio()// Stop the camera// cameraApi.stop()// Restart the camera// await cameraApi.restart()
```

### Step 7. Preview effects locally

```
// Use the built-in player of the SDK. `my-dom-id` is the ID of the playerâs container.const player = await sdk.initLocalPlayer('my-dom-id')// Play the videoawait player.play()// Pause the videoplayer.pause()
```

## Sample Code Package

You can download our sample code package [here](https://github.com/tencentcloud-webar/web-demo-en), Sample code is located in the **TRTC_Web(4.x)** folder, The main changes are in `index_AR.html` and `rtc-client-with-webar.js`. The code for the interaction logic of Tencent Effect is in `base-js/js/ar_interact.js`. The configuration of TRTC key information is in `base-js/js/debug/GenerateTestUserSig.js`.


---
*Source: [https://trtc.io/document/53885](https://trtc.io/document/53885)*
