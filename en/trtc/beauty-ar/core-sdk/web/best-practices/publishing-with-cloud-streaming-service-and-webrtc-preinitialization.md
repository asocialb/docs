# Publishing with Cloud Streaming Service and WebRTCï»¿ (Preinitialization)

## Preparations

- Read [Overview](https://www.tencentcloud.com/document/product/1143/50099) to learn about how to use the Beauty AR Web SDK.
- For more information on WebRTC publishing, see [Publishing over WebRTC](https://www.tencentcloud.com/document/product/1143/53886). This document describes the differences in the code and process when the preinitialization scheme is used.
- For more information on the preinitialization scheme, see [Loading Optimization](https://www.tencentcloud.com/document/product/1143/50103).

## Getting Started

The preinitialization scheme differs from the general loading scheme mainly in that you don't need to specify the `input` or `camera` attribute when initializing the SDK; that is, instead of specifying the input data for the SDK during initialization, you later call the `initCore` API to specify the data at an appropriate location based on your needs. In this way, the resources depended on by the SDK are loaded in advance, and the `ready` event of the SDK will be triggered more quickly after `initCore` is later called, making it easier to get and display the output stream. Below is the key sample code:

### Initializing SDK

```
...let resourceReady = false// Basic configuration parameters of the Beauty AR SDKconst config = {    // input: stream, // Do not specify `input`.    auth: {        licenseKey: LICENSE_KEY,        appId: APPID,        authFunc: getSignature    },    // Initial beauty effects (optional parameters)    beautify: {        whiten: 0.1, // The brightening effect. Value range: 0â1.        dermabrasion: 0.5, // The smooth skin effect. Value range: 0â1.        lift: 0.3, // The slim face effect. Value range: 0â1.        shave: 0, // The V shape effect. Value range: 0â1.        eye: 0, // The big eyes effect. Value range: 0â1.        chin: 0, // The chin shaping effect. Value range: 0â1.        â¦â¦    },    language: 'en'}// Pass in `ar sdk` for `config`.const ar = new ArSdk(config);// If the `resourceReady` callback event is triggered, the resources have been completely loaded, and you need to wait for `initCore` to provide input.ar.on('resourceReady', () => {    resourceReady = true})// The `ready` event will be triggered after `initCore` is called.ar.on('ready', () => {    // Get the output stream data of the Beauty AR SDK    const arStream = await ar.getOutput();    // Process the output stream    ...})...
```

### Triggering the `initCore` event with a user operation

```
// The following describes how to set the input stream for the preinitialization scheme with an example in which the user turns on the camera.function onClickStartCamera(){    let w = 1280;    let h = 720;    // Get the device's input stream    const arInputStream = await navigator.mediaDevices.getUserMedia({        audio: true,        video: {            width: w,            height: h        }    });    if(!resourceReady){ // In this mode, calling `initCore` will have no effect if `resourceReady` is not triggered, and you can do some customization.        return    }    // Set the input stream data of the Beauty AR SDK    ar.initCore({        input: arInputStream    })}
```

## Sample Code

You can download the [sample code](https://github.com/tencentcloud-webar/web-demo-en), decompress it, and view the `AR_and_LEB_Preload.html` file in the `AR_LEB_WEB` code directory.


---
*Source: [https://trtc.io/document/53940](https://trtc.io/document/53940)*
