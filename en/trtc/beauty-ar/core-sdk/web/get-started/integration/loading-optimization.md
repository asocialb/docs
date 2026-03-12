# Loading Optimization

## Regular Mode

In contrast, if you call `getOutput` in the `ready` callback, the output stream obtained will have been processed. Because the `ready` callback occurs later than `cameraReady`, you can call `getOutput` in the `ready` callback if you want to apply effects to the video the moment it is displayed, but do not expect the video to be played as soon as possible.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4012eb46bf3e11ee9976525400c26da5.jpeg)

Sample code:

```
// Get the authentication informationconst authData = {    licenseKey: 'xxxxxxxxx',    appId: 'xxx',    authFunc: authFunc // For details, see âConfiguring and Using a License - Signatureâ};// When initializing the SDK in regular mode, pass in the input or camera parametersconst config = {    auth: authData, // The authentication information    beautify: { // The effect parameters        whiten: 0.1,        dermabrasion: 0.5,        lift: 0,        shave: 0,        eye: 0.2,        chin: 0,    },    input: inputStream // Prepare the stream data fed into the SDK as the input. For details, see âSDK Integration - Parameters and APIsâ.}const sdk = new ArSdk(    // Pass in a config object to initialize the SDK    config)// After authentication succeeds, the SDK will trigger the `created` callback immediatelysdk.on('created', () => {    // Pull and display the filter and effect list in the `created` callback    sdk.getEffectList({        Type: 'Preset',        Label: 'Makeup',    }).then(res => {        effectList = res    });    sdk.getCommonFilter().then(res => {        filterList = res    })})// The data you get by calling `getOutput` in different callbacks vary slightly. Choose the one that fits your needs.sdk.on('cameraReady', async () => {    const output = await sdk.getOutput() // The effect parameters have not taken effect    // Play the stream    ...})sdk.on('ready', async () => {    const output = await sdk.getOutput() // The effect parameters have taken effect    // Play the stream    ...    // Call `setBeautify`, `setEffect`, or `setFilter` in the `ready` callback})
```

## Pre-Initialization

When the SDK is loaded for the first time, it needs to download static resources in order to initialize the detection module. As a result, the loading of the SDK is affected by network conditions. Given that in some scenarios, you may want to display a video image as soon as possible, we offer a pre-initialization plan that loads static resources in advance.

**Use cases for pre-initialization**

- Case 1: The effect SDK is not needed when the webpage is initialized. A video is displayed only after the user performs certain operation.
- Case 2: Effects are needed for page B, and page B is directed from page A.
In such cases, you can load resources in advance (as early as possible), feed an input stream to the SDK when necessary, and then get a processed output stream.

For example, in case 1, you can load resources when the webpage is initialized; in case 2, you can get an SDK instance on page A and pass it to page B.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/626650740ce511efafb0525400493f3c.jpg)

**The code below works for case 1**

```
<button id="start">Enable the camera</button>
```

```
// Get the authentication informationconst authData = {    licenseKey: 'xxxxxxxxx',    appId: 'xxx',    authFunc: authFunc // For details, see âConfiguring and Using a License - Signatureâ};// Do not pass in the input or camera parameters when initializing the SDK. After an instance is obtained, the SDK will start loading the necessary resources.const config = {    auth: authData, // The authentication information    beautify: { // The effect parameters        whiten: 0.1,        dermabrasion: 0.5,        lift: 0,        shave: 0,        eye: 0.2,        chin: 0,    },}const sdk = new ArSdk(    // Pass in a config object to initialize the SDK    config)// After authentication succeeds, the SDK will trigger the `created` callback immediatelysdk.on('created', () => {    // Pull and display the filter and effect list in the `created` callback    sdk.getEffectList({        Type: 'Preset',        Label: 'Makeup',    }).then(res => {        effectList = res    });    sdk.getCommonFilter().then(res => {        filterList = res    })})// `resourceReady` indicates that the necessary resources are ready. After receiving this callback, you can call `initCore` to feed an input stream to the SDK.sdk.on('resourceReady', () => {})// In this mode, the SDK will trigger the `ready` callback only after `initCore` is called.sdk.on('ready', async () => {    const output = await sdk.getOutput() // The effects have been applied.    // Play the stream    ...    // Call `setBeautify`, `setEffect`, or `setFilter` in the `ready` callback})// Feed stream data to the SDK when the user turns the camera ondocument.getElementById('start').onclick = async function(){    const devices = await navigator.mediaDevices.enumerateDevices()    const cameraDevice = devices.find(d=>d.kind === 'videoinput')    navigator.mediaDevices.getUserMedia({        audio: false,        video: {            deviceId: cameraDevice.deviceId            ... // Other configuration        }    }).then(mediaStream => {        // In this mode, make sure you call `initCore` after the `resourceReady` callback.        sdk.initCore({            input: mediaStream // Prepare the stream data fed into the SDK as the input. For details, see âSDK Integration - Parameters and APIsâ.        })    })    }
```


---
*Source: [https://trtc.io/document/50103](https://trtc.io/document/50103)*
