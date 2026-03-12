# Using Beauty Special Effects to Process Images

This tutorial guides you on how to use the SDK to beautify images, apply effects, download processed images, and perform other operations in a browser.

## Before You Start

- Please read the [Activate the Service](https://trtc.io/document/60218?platform=web&product=beautyar) to familiarize yourself with the license application and usage, and prepare the license.
- Please read the [Start Integration](https://trtc.io/document/68777?platform=web&product=beautyar) guide to understand the basic usage of the SDK.

## Directions

### Step 1. Import the Beauty AR Web SDK

Create an ar-demo.html file and include the following dependency JavaScript files.

```
<script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/latest/webar-sdk.umd.js"></script><script src="https://webar-static.tencent-cloud.com/docs/examples/js-sha256/0.9.0/sha256.min.js"></script>
```

> **Noteï¼**Demo use the script tag method for inclusion. You can also refer to the methods in the integration guide to include it [Start Integration](https://trtc.io/document/68777?platform=web&product=beautyar).webar-sdk.umd.js is the main package and is required.sha256.min.js is the package used for obtaining the Signature signature, and it is included here only for demonstration purposes in the demo project.

### Step 2. Initialize the Beauty AR Web SDK

Fill in the APPID, LICENSE_KEY, and token obtained from the [preparation work](https://www.tencentcloud.com/document/product/1143/68964#.E5.87.86.E5.A4.87.E5.B7.A5.E4.BD.9C) into the example code below:

```
<img id="inputImageElement" src="https://webar-static.tencent-cloud.com/docs/test/m4-1080.jpg"><canvas id="arOutputElement" style="width: 400px;display: inline-block;margin-left: 20px;"></canvas>
```

```
/** ----- Authentication configuration ----- *//** * Tencent Cloud account's APPID *  * You can view your APPID in the [Account Center](https://console.tencentcloud.com/developer). */const APPID = ''; // Set it to your Tencent Cloud account APPID./** * Web LicenseKey *  * obtained from Before You Start */const LICENSE_KEY = ''; // Set it to your license key./** * The token used to calculate the signature. *  * Note: This method is only suitable for debugging. In a production environment, you should store the token and calculate the signature on your server. The front end can get the signature by calling an API. For details, see * https://trtc.io/zh/document/68777?platform=web&product=beautyar#cf3401f9-e22e-4f54-9e2d-942c08be0f93 */const token = ''; // Set it to your token./** ----------------------- *//** * Get the signature * * Note: This method is only suitable for debugging. In a production environment, you should store the token and calculate the signature on your server. The front end can get the signature by calling an API. For details, see * https://trtc.io/zh/document/68777?platform=web&product=beautyar#e4ce3483-41f7-4391-83ae-f4b61e221ea0 */const getSignature = function () {    const timestamp = Math.round(new Date().getTime() / 1000);    const signature = sha256(timestamp + token + APPID + timestamp).toUpperCase();    return { signature, timestamp };};const inputImageElement = document.getElementById('inputImageElement');const arOutputElement = document.getElementById('arOutputElement');// ar sdk configconst config = {    module: {        beautify: true,    },    auth: {        licenseKey: LICENSE_KEY,        appId: APPID,        authFunc: getSignature    },    input: inputImageElement, // input image element    output: arOutputElement, // output canvas element    beautify: { // default Beautify config        "eye": 0.5,        "whiten": 0.4,        "dermabrasion": 0.6,        "lift": 0.1,        "shave": 0.2,    },}// init ArSdkconst { ArSdk } = window.AR;const arSdk = new ArSdk(config);arSdk.on('error', (e) => {    console.log(e);});
```

## Step 3. Update Input Image

you can select an image file using the input tag and call the `updateInputImage` interface to update the image.

```
<input type="file" id="imageInput" accept="image/*" style="display: none;">
```

```
const imageInput = document.getElementById('imageInput');imageInput.addEventListener('change', function () {    const file = this.files[0];    if (file) {        const reader = new FileReader();        reader.onload = function (event) {            inputImageElement.src = event.target.result;            inputImageElement.onload = function () {                arSdk.updateInputImage({                    width: inputImageElement.width,                    height: inputImageElement.height,                    input: inputImageElement,                })            };        };        reader.readAsDataURL(file);    }});
```

## Step 4. Set BeautifyãMakeupãEffect

Use the `setBeautify` interface to apply beauty effects, and the `setEffect` interface to apply makeup, face stickers, and other effect.

```
// set effectfunction setMakeUp() {    if (!arSdk) return    arSdk.setEffect([{        id: 'CE82819618A6CDA3', // makeupãeffect id        intensity: 0.8    }])}// clear effectfunction clearMakeUp() {    if (!arSdk) return    arSdk.setEffect(null)}// set beautifyfunction setBeautify() {    if (!arSdk) return    arSdk.setBeautify({        "eye": Math.random() * 1,        "whiten": Math.random() * 1,        "dermabrasion": Math.random() * 1,        "lift": Math.random() * 1,        "shave": Math.random() * 1,    })}// clear beautifyfunction clearBeautify() {    if (!arSdk) return    arSdk.setBeautify({        "eye": 0,        "whiten": 0,        "dermabrasion": 0,        "lift": 0,        "shave": 0,    })}
```

## Step 5. Download Image

Use the `takePhoto` interface to obtain the processed image ImageData, render it to the canvas, and download it.

```
<canvas id="photoCanvas" style="display: none;"></canvas><button id="downloadImage">Download Image</button>
```

```
const downloadImage = document.getElementById('downloadImage');downloadImage.addEventListener('click', async () => {    if (!arSdk) {        alert('Please initAR firstï½')        return    }    const imageData = await arSdk.takePhoto();    photoCanvas.width = imageData.width;    photoCanvas.height = imageData.height;    const context = photoCanvas.getContext("2d");    context.putImageData(imageData, 0, 0);    const base64Image = photoCanvas.toDataURL("image/png");    const a = document.createElement("a");    a.href = base64Image;    a.download = "downloadedImage.png";    document.body.appendChild(a);    a.click();    document.body.removeChild(a);})
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
<!DOCTYPE html><html lang="en"><head>    <meta charset="UTF-8">    <meta name="viewport" content="width=device-width, initial-scale=1.0">    <title>Image Upload and Display</title></head><body>    <div>        step1: <button id="initAR">Init AR SDK</button>        </br>        step2: <button id="selectAndProcess">Update Input Image</button>    </div>    <div>        step3: <button onclick="setMakeUp()">Set Makeup</button>        <button onclick="clearMakeUp()">Clear Makeup</button>        <button onclick="setBeautify()">Set Beautify</button>        <button onclick="clearBeautify()">Clear Beautify</button>    </div>    <div>        step4: <button id="downloadImage">Download Image</button>    </div>    <input type="file" id="imageInput" accept="image/*" style="display: none;">    <br>    <img id="inputImageElement" src="https://webar-static.tencent-cloud.com/docs/test/m4-1080.jpg">    <canvas id="arOutputElement" style="display: inline-block;"></canvas>    <canvas id="photoCanvas" style="display: none;"></canvas>    <script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/latest/webar-sdk.umd.js">    </script>    <script src="https://webar-static.tencent-cloud.com/docs/examples/js-sha256/0.9.0/sha256.min.js"></script>    <script>        let arSdk;        // todoï¼Enter the license information        const APPID = "";        const LICENSE_KEY = "";        const token = "";        const getSignature = function () {            const timestamp = Math.round(new Date().getTime() / 1000);            const signature = sha256(timestamp + token + APPID + timestamp).toUpperCase();            return {                signature,                timestamp            };        };        const selectAndProcess = document.getElementById('selectAndProcess');        const imageInput = document.getElementById('imageInput');        const downloadImage = document.getElementById('downloadImage');        const inputImageElement = document.getElementById('inputImageElement');        const initArBtn = document.getElementById('initAR');        const arOutputElement = document.getElementById('arOutputElement');        const photoCanvas = document.getElementById('photoCanvas');        initArBtn.addEventListener('click', async () => {            arSdk = await getInstance();            alert('Init AR SDK Success!!!')        })        selectAndProcess.addEventListener('click', () => {            if (!arSdk) {                alert('Please click initAR to init AR SDK')                return            }            imageInput.click();        })        downloadImage.addEventListener('click', async () => {            if (!arSdk) {                alert('Please click initAR to init AR SDK')                return            }            const imageData = await arSdk.takePhoto();            photoCanvas.width = imageData.width;            photoCanvas.height = imageData.height;            const context = photoCanvas.getContext("2d");            context.putImageData(imageData, 0, 0);            const base64Image = photoCanvas.toDataURL("image/png");            const a = document.createElement("a");            a.href = base64Image;            a.download = "downloadedImage.png";            document.body.appendChild(a);            a.click();            document.body.removeChild(a);        })        imageInput.addEventListener('change', function () {            const file = this.files[0];            if (file) {                const reader = new FileReader();                reader.onload = function (event) {                    inputImageElement.src = event.target.result;                    inputImageElement.onload = function () {                        arSdk.updateInputImage({                            width: inputImageElement.width,                            height: inputImageElement.height,                            input: inputImageElement,                        })                    };                };                reader.readAsDataURL(file);            }        });        function setMakeUp() {            if (!arSdk) return            arSdk.setEffect([{                id: 'CE82819618A6CDA3', // makeupãeffect id                intensity: 0.8            }])        }        function clearMakeUp() {            if (!arSdk) return            arSdk.setEffect(null)        }        function clearBeautify() {            if (!arSdk) return            arSdk.setBeautify({                "eye": 0,                "whiten": 0,                "dermabrasion": 0,                "lift": 0,                "shave": 0,            })        }        function setBeautify() {            if (!arSdk) return            arSdk.setBeautify({                "eye": Math.random() * 1,                "whiten": Math.random() * 1,                "dermabrasion": Math.random() * 1,                "lift": Math.random() * 1,                "shave": Math.random() * 1,            })        }        async function getInstance() {            if (arSdk) {                return Promise.resolve(arSdk)            }            const config = {                module: {                    beautify: true,                    segmentation: false                },                auth: {                    licenseKey: LICENSE_KEY,                    appId: APPID,                    authFunc: getSignature                },                input: inputImageElement,                output: arOutputElement,                beautify: {                    "eye": Math.random() * 1,                    "whiten": Math.random() * 1,                    "dermabrasion": Math.random() * 1,                    "lift": Math.random() * 1,                    "shave": Math.random() * 1,                },            }            return new Promise((resolve) => {                const sdk = new window.AR.ArSdk(config)                sdk.on('resourceReady', async () => {                    // get makeuplist                     sdk.getEffectList({                        Type: 'Preset',                        Label: 'Makeup',                    }).then((res) => {                        const list = res.map(item => ({                            name: item.Name,                            id: item.EffectId,                            cover: item.CoverUrl,                            url: item.Url,                            label: item.Label,                            type: item.PresetType,                        }));                        console.log('makeuplist', list)                    })                    resolve(sdk)                })                sdk.on('ready', () => {                })                sdk.on('error', (e) => {                    console.log(e);                });            })        }    </script></body></html>
```


---
*Source: [https://trtc.io/document/69310](https://trtc.io/document/69310)*
