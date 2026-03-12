# Publishing Using TRTC (Version 5.x)

> **Note:**This tutorial is based on the 5.x TRTC Web SDK. If you are using the 4.x version of the SDK, please refer to [this tutorial](https://www.tencentcloud.com/document/product/1143/53885).

## Before You Start

- Please read the [integration guide](https://www.tencentcloud.com/document/product/1143/50099) for Beauty AR Web.
- Follow the steps in [Integration (No UI)](https://www.tencentcloud.com/document/product/647/35096) to integrate the TRTC web SDK.
- Try [running a TRTC web demo](https://www.tencentcloud.com/document/product/647/35607) in your local project.

## Directions

### Step 1. Import the Beauty AR Web SDK

**You can import the Beauty AR Web SDK by making some minor changes to the import method in the TRTC web demo.**

Add the following JavaScript script to your webpage (desktop):

```
<script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/latest/webar-sdk.umd.js"></script>
```

> **Note:**The above example uses a script tag to import the SDK. You can also [import it using an npm package](https://www.tencentcloud.com/document/product/1143/50099).

### Step 2. Understand the stream initialization logic of TRTC

1. In the TRTC demo project, you can observe the process of joining a TRTC room. After entering the room, TRTC captures local device input using the [startLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) and [startLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalAudio) methods, creating stream objects and publishing them to the roomï¼

```
const trtc = TRTC.create();await trtc.enterRoom({ roomId: 8888, sdkAppId, userId, userSig });// Collect the default microphone and publishawait trtc.startLocalAudio();// Collect the default camera and publishawait trtc.startLocalVideo({  view: document.getElementById("localVideo"), // Preview the video on the element with the DOM elementId of localVideo.});
```

The above code describes the most basic method of capturing local audio and video streams and publishing them to a specified room.

2. TRTC provides the [updateLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalVideo) interface for updating video streams. We can use custom capture methods to obtain beauty-enhanced streams and pass them to this interface for use.

```
// Get the custom streamconst stream = await ar.getOutput();// update trtc video trackawait trtc.updateLocalVideo({  option: { videoTrack: mediaStream.getVideoTracks()[0] },});
```

3. To process the local stream using Tencent Effect, you need to [initialize the Beauty AR Web SDK](#step3) first.

### Step 3. Initialize the Beauty AR Web SDK

Sample code:

```
const { ArSdk } = window.AR/** ----- Authentication configuration ----- *//** * The APPID of your Tencent Cloud account. *  * You can view your APPID in the [Account Center](https://console.cloud.tencent.com/developer). */const APPID = ''; // Set it to your Tencent Cloud account APPID./** * Web LicenseKey *  * Log in to the RT-Cube console and click [Web Licenses](https://console.cloud.tencent.com/vcube/web) on the left sidebar. A license key will be automatically generated after you create a license. */const LICENSE_KEY = ''; // Set it to your license key./** * The token used to calculate the signature. *  * Note: This method is only suitable for debugging. In a production environment, you should store the token and calculate the signature on your server. The front end can get the signature by calling an API. For details, see * [Signature](https://cloud.tencent.com/document/product/616/71370#.E7.AD.BE.E5.90.8D.E6.96.B9.E6.B3.95) */const token = ''; // Set it to your token./** ----------------------- *//** * Get the signature * * Note: This method is only suitable for debugging. In a production environment, you should calculate the signature on your server. The front end can get the signature by calling an API. ** Example: * async function () { *  return fetch('http://xxx.com/get-ar-sign').then(res => res.json()); * }; */const getSignature = function () {    const timestamp = Math.round(new Date().getTime() / 1000);    const signature = sha256(timestamp + token + APPID + timestamp).toUpperCase();    return { signature, timestamp };};// get trtc video track(original)const arInputStream = new MediaStream([trtc.getVideoTrack()]);// The basic settings for the Tencent Effect SDKconst config = {    input: arInputStream,    auth: {        licenseKey: LICENSE_KEY,        appId: APPID,        authFunc: getSignature    },    // Configure the initial effects (optional)    beautify: {        whiten: 0.1, // The brightening effect. Value range: 0-1.        dermabrasion: 0.5, // The smooth skin effect. Value range: 0-1.        lift: 0.3, // The slim face effect. Value range: 0-1.        shave: 0, // The V shape effect. Value range: 0-1.        eye: 0, // The big eyes effect. Value range: 0-1.        chin: 0, // The chin effect. Value range: 0-1.    },    language: 'en',    â¦â¦}// Pass `config` to the Tencent Effect SDKconst ar = new ArSdk(config);// You can display the effect and filter list in the `created` callback.ar.on('created', () => {    // Get the built-in makeup effects and stickers    ar.getEffectList({        Type: 'Preset'    }).then((res) => {        const list = res.map(item => ({            name: item.Name,            id: item.EffectId,            cover: item.CoverUrl,            url: item.Url,            label: item.Label,            type: item.PresetType,        }));        const makeupList = list.filter(item=>item.label.indexOf('Makeup')>=0)        const stickerList = list.filter(item=>item.label.indexOf('Sticker')>=0)        // Show the makeup and sticker lists    }).catch((e) => {        console.log(e);    });    // Get the built-in filters    ar.getCommonFilter().then((res) => {        const filterList = res.map(item => ({            name: item.Name,            id: item.EffectId,            cover: item.CoverUrl,            url: item.Url,            label: item.Label,            type: item.PresetType,        }));        // Show the filter list    }).catch((e) => {        console.log(e);    });});ar.on('ready', (e) => {    // After receiving the `ready` callback, you can call `setBeautify`, `setEffect`, or `setFilter` to configure effects.    // ar.setBeautify()    // ar.setEffect()    // ar.setFilter()        // update trtc video track (with AR effect)    const mediaStream = await ar.getOutput();    await trtc.updateLocalVideo({      option: { videoTrack: mediaStream.getVideoTracks()[0] },    });});ar.on('error', (e) => {    console.log(e);});
```

The above code initializes the configuration for the Web beauty effect SDK. The input for the beauty SDK is the unprocessed video stream obtained from the TRTC object's getVideoTrack interface.

### Step 4. Update the TRTC stream

Once the Web beauty effect SDK is initialized, you can use the getOutput method to obtain the output stream. Then, call the TRTC instance's updateLocalVideo interface to update the local stream and publish it to the room.

```
const mediaStream = await ar.getOutput();// update trtc video track (with AR effect)await trtc.updateLocalVideo({  option: { videoTrack: mediaStream.getVideoTracks()[0] },});
```

### Step 5: Run the demo to experience the effects

> **Note:**The example project requires you to start a local web server and ensure that the HTML file is accessible through the specified port number (the sample code is located in the **TRTC_Web(5.x)**folder, run quick-demo-js/index.html).

After entering the room, you will need to wait a short moment for the beauty effect to initialize. Once initialized, you can see the actual beauty effects in action. If successful, you can open a new browser tab and enter the room you just created to simulate the effect of other participants joining the room.

## Sample Code Package

You can download our sample code package [here](https://github.com/tencentcloud-webar/web-demo-en)ï¼Sample code is located in the **TRTC_Web(5.x)** folder, The main changes related to the beauty effects can be found in the **TRTC_Web(5.x)** folder, specifically in quick-demo-js/index.html and quick-demo-js/js/index.js. Please ensure you have applied for the TRTC key and the Web beauty effect license information in advance.


---
*Source: [https://trtc.io/document/67329](https://trtc.io/document/67329)*
