# Virtual Try-On Integration Guide

## Before You Start

- Please read the [Activate the Service](https://trtc.io/document/60218?platform=web&product=beautyar) to familiarize yourself with the license application and usage, and prepare the license.
- Please read the [Start Integration](https://trtc.io/document/68777?platform=web&product=beautyar) guide to understand the basic usage of the SDK.

## Directions

### Step 1. Import the Beauty AR Web SDK

Create an ar-demo.html file and include the following dependency JavaScript files.

```
<script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/1.0.26-4/webar-sdk.umd.js"></script><script src="https://webar-static.tencent-cloud.com/docs/examples/js-sha256/0.9.0/sha256.min.js"></script>
```

> **Note:**Demo use the script tag method for inclusion. You can also refer to the methods in the integration guide to include it [Start Integration](https://trtc.io/document/68777?platform=web&product=beautyar).webar-sdk.umd.js is the main package and is required.sha256.min.js is the package used for obtaining the Signature signature, and it is included here only for demonstration purposes in the demo project.

### Step 2. Initialize the Beauty AR Web SDK

Fill in the APPID, LICENSE_KEY, and token obtained from the [preparation work](https://www.tencentcloud.com/document/product/1143/68965#.E5.87.86.E5.A4.87.E5.B7.A5.E4.BD.9C) into the example code below:

```
/** ----- Authentication configuration ----- *//** * Tencent Cloud account's APPID *  * You can view your APPID in the [Account Center](https://console.tencentcloud.com/developer). */const APPID = ''; // Set it to your Tencent Cloud account APPID./** * Web LicenseKey *  * obtained from Before You Start */const LICENSE_KEY = ''; // Set it to your license key./** * The token used to calculate the signature. *  * Note: This method is only suitable for debugging. In a production environment, you should store the token and calculate the signature on your server. The front end can get the signature by calling an API. For details, see * https://trtc.io/document/50099?platform=web&product=beautyar#e4ce3483-41f7-4391-83ae-f4b61e221ea0 */const token = ''; // Set it to your token./** ----------------------- *//** * Get the signature * * Note: This method is only suitable for debugging. In a production environment, you should calculate the signature on your server. The front end can get the signature by calling an API. * eg: * async function () { *  return fetch('http://xxx.com/get-ar-sign').then(res => res.json()); * }; */const getSignature = function () {    const timestamp = Math.round(new Date().getTime() / 1000);    const signature = sha256(timestamp + token + APPID + timestamp).toUpperCase();    return { signature, timestamp };};// ar sdk configconst config = {    module: {        beautify: true,        handLandmark: true // rings try on require handLandmark module    },    auth: {        licenseKey: LICENSE_KEY,        appId: APPID,        authFunc: getSignature    },    // Built-in Camera method is used to set the input;    // for Custom Stream methods, please refer to. https://trtc.io/document/50102?platform=web&product=beautyar    camera: {        width: 1080,        height: 720,        mirror: true,    },}// new ArSdkconst { ArSdk } = window.AR;const ar = new ArSdk(config);ar.on('error', (e) => {    console.log(e);});
```

### Step 3. Retrieve specified types of materials based on different labels.

In the SDK-created callback, you can obtain the list of built-in or custom effects. Built-in effects are distinguished by different tags, and common tag types include:

- Makeup: Face makeup effect
- Blush: Blush effect
- Eyes: Eyes effect
- Eyebrows: Eyebrows effect
- Lips: Lips effect
- Iris: Contact Lenses effect
- glasses: Glasses try-on
- rings: Rings try-on
- Headwear: Headwear try-on

We also recommend that clients manage materials using different tags when there is a demand for custom effects, referring to the production of [custom materials](https://trtc.io/zh/document/53887?platform=web&product=beautyar).

```
let makeupList, glassesList, contactLensesList,  headwearList, ringListlet customEffectListar.on('created', async () => {    makeupList = await ar.getEffectList({        Type: 'Preset',        Label: ['Makeup', 'Woman']    })    glassesList = await ar.getEffectList({        Type: 'Preset',        Label: ['glasses']    })    contactLensesList = await ar.getEffectList({        Type: 'Preset',        Label: ['Iris']    })    headwearList = await ar.getEffectList({        Type: 'Preset',        Label: ['Headwear']    })    ringList = await ar.getEffectList({        Type: 'Preset',        Label: ['rings']    })    // In scenarios with custom materials, set the Type to 'Custom' to retrieve the custom materials. See    // https://trtc.io/zh/document/53887?platform=web&product=beautyar    customEffectList = await ar.getEffectList({        Type: 'Custom'    })});
```

### Step 4. Set Effect

Use `setEffect` to apply various beauty, eyewear,ring, and headwear materials, as well as all custom effects. Please refer to the [API documentation](https://trtc.io/zh/document/50106?platform=web&product=beautyar) for the interface parameters.

```
function setMakeup() {    ar.setEffect({        id: makeupList[0].EffectId,    })}function setGlasses() {    ar.setEffect({        id: glassesList[0].EffectId,    })}function setContactLenses() {    ar.setEffect({        id: contactLensesList[0].EffectId,        intensity: 0.6    })}function setHeadwear() {    ar.setEffect({        id: headwearList[0].EffectId,    })}function setRings() {    ar.setEffect({        id: ringList[0].EffectId,    })}
```

> **Note:**When using rings try on, you need to enable the **handLandmark** module in the **module** **configuration** and ensure that the palm is fully visible in the camera's field of view during the preview.

### Step 5. Preview Effect

Obtain the processed mediaStream in the SDK ready state and preview the effect using the Video tag.

> **Note:**The output streams obtained at different lifecycle stages will have varying preview effects. For more details, please refer to the instructions in the [loading optimization](https://trtc.io/document/50103?platform=web&product=beautyar#.E6.99.AE.E9.80.9A.E6.A8.A1.E5.BC.8F) documentation. This example only uses the ready callback.

```
ar.on('ready', async (e) => {    // get output stream from ar sdk    const arOutputStream = await ar.getOutput();    // view with video element    const video = document.createElement("video");    video.setAttribute("id", "webar-output-video");    video.setAttribute("playsinline", "");    video.setAttribute("autoplay", "");    video.setAttribute("style", 'width:600px;height:auto;');    video.srcObject = arOutputStream;    document.body.appendChild(video);});
```

Also supports previewing through the initLocalPlayer method. This interface provides a convenient way to preview the SDK output effect by playing the media stream output from the SDK in a video format within a specified DOM container.

```
ar.on('ready', async (e) => {    // localplayerContainer is the ID of the specified DOM container.    // eg. <div style="display: inline-block;width: 1280px;height: auto;" id="localplayerContainer"></div>    const player = await arSdk.initLocalPlayer('localplayerContainer')    await player.play()});
```

### Step 6. Run Demo

Start a local server service and access the specified port.

Here, we use the [serve module](https://www.npmjs.com/package/serve) as an example. Run `serve .` in the directory where the demo is located.

Seeing the following output indicates that the local server service has started successfully.

```
    Serving!                                       â   â                                                  â   â   - Local:            http://localhost:57965     â   â   - On Your Network:  http://10.91.28.94:57965   â   â                                                  â   â   This port was picked because 5000 is in use.   â   â                                                  â   â   Copied local address to clipboard!
```

Access the specified port in Chrome to preview the effect.

> **Note:**The demo requires access to the browser's **camera** and **microphone** permissions. Please ensure that the page you are accessing has been granted these permissions.

The complete code snippet is as follows. Before running, please fill in the APPID, LICENSE_KEY, and token-related information in the code.

```
<!DOCTYPE html><html lang="en"><head>    <meta charset="UTF-8">    <meta http-equiv="X-UA-Compatible" content="IE=edge">    <meta name="viewport" content="width=device-width, initial-scale=1.0">    <title>webar virtual try on demo</title></head><body>    <div id="controls" style="margin-bottom: 20px;">        <button type="button" onclick="setMakeup()">set Makeup</button>        <button type="button" onclick="setGlasses()">set Glasses</button>        <button type="button" onclick="setContactLenses()">set Contact Lenses</button>        <button type="button" onclick="setHeadwear()">set Headwear</button>        <button type="button" onclick="setRings()">set Rings</button>    </div>    <script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/1.0.26-4/webar-sdk.umd.js"></script>    <script src="https://webar-static.tencent-cloud.com/docs/examples/js-sha256/0.9.0/sha256.min.js"></script>    <script>        const APPID = '';        const LICENSE_KEY = '';        const token = '';        const getSignature = function () {            const timestamp = Math.round(new Date().getTime() / 1000);            const signature = sha256(timestamp + token + APPID + timestamp).toUpperCase();            return {                signature,                timestamp            };        };        const config = {            module: {                beautify: true,                handLandmark: true // rings try on require handLandmark module            },            auth: {                licenseKey: LICENSE_KEY,                appId: APPID,                authFunc: getSignature            },            camera: {                width: 1080,                height: 720,                mirror: true,            },        }        // new ArSdk        const { ArSdk } = window.AR;        const ar = new ArSdk(config);        ar.on('error', (e) => {            console.log(e);            alert(e.message);        });        let makeupList, glassesList, contactLensesList,  headwearList, ringList        let customEffectList        // get effect list        ar.on('created', async () => {            makeupList = await ar.getEffectList({                Type: 'Preset',                Label: ['Makeup', 'Woman']            })            glassesList = await ar.getEffectList({                Type: 'Preset',                Label: ['glasses']            })            contactLensesList = await ar.getEffectList({                Type: 'Preset',                Label: ['Iris']            })            headwearList = await ar.getEffectList({                Type: 'Preset',                Label: ['Headwear']            })            ringList = await ar.getEffectList({                Type: 'Preset',                Label: ['rings']            })            // In scenarios with custom materials, set the Type to 'Custom' to retrieve the custom materials. See            // https://trtc.io/zh/document/53887?platform=web&product=beautyar            customEffectList = await ar.getEffectList({                Type: 'Custom'            })        });        function setMakeup() {            ar.setEffect({                id: makeupList[0].EffectId,            })        }        function setGlasses() {            ar.setEffect({                id: glassesList[0].EffectId,            })        }        function setContactLenses() {            ar.setEffect({                id: contactLensesList[0].EffectId,                intensity: 0.6            })        }        function setHeadwear() {            ar.setEffect({                id: headwearList[0].EffectId,            })        }        function setRings() {            ar.setEffect({                id: ringList[0].EffectId,            })        }                ar.on('ready', async (e) => {            // get output stream from ar sdk            const arOutputStream = await ar.getOutput();            // view with video element            const video = document.createElement("video");            video.setAttribute("id", "webar-output-video");            video.setAttribute("playsinline", "");            video.setAttribute("autoplay", "");            video.setAttribute("style", 'width:600px;height:auto;');            video.srcObject = arOutputStream;            document.body.appendChild(video);        });    </script></body></html>
```


---
*Source: [https://trtc.io/document/68965](https://trtc.io/document/68965)*
