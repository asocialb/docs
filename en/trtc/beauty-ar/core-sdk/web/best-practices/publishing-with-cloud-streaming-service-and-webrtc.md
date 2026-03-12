# Publishing with Cloud Streaming Service and WebRTCï»¿

## Before You Start

- Please read the [integration guide](https://www.tencentcloud.com/document/product/1143/50099) for Beauty AR Web.
- Please read [Getting Started](https://www.tencentcloud.com/document/product/267/41030) and [WebRTC Push](https://www.tencentcloud.com/document/product/267/41620) to complete the basic settings and learn how to publish streams over WebRTC.

## Directions

### Step 1. Import the Beauty AR Web SDK

```
<script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/latest/webar-sdk.umd.js"></script>
```

> **Note:**The above example uses a script tag to import the SDK. You can also [import it using an npm package](https://www.tencentcloud.com/document/product/1143/50099).

### Step 2. Import the WebRTC publishing resources

```
<script src="https://video.sdk.qcloudecdn.com/web/TXLivePusher-2.0.0.min.js" charset="utf-8"></script>
```

> **Note:**Make sure you add the script to the body of the HTML. Adding it to the head may cause an error.

### Step 3. Initialize the Beauty AR Web SDK

```
const { ArSdk } = window.AR;/** ----- Authentication configuration ----- *//** Tencent Cloud account's APPID *  * You can view your APPID in the [Account Center](https://console.tencentcloud.com/developer). */const APPID = ''; // Set it to your Tencent Cloud account APPID./** * Web LicenseKey *  * Log in to the RT-Cube console and click [Web Licenses](https://console.tencentcloud.com/vcube/web) on the left sidebar. A license key will be automatically generated after you create a license. */const LICENSE_KEY = ''; // Set it to your license key./** * The token used to calculate the signature. *  * Note: This method is only suitable for debugging. In a production environment, you should store the token and calculate the signature on your server. The front end can get the signature by calling an API. For details, see * [Signature](https://cloud.tencent.com/document/product/616/71370#.E7.AD.BE.E5.90.8D.E6.96.B9.E6.B3.95) */const token = ''; // Set it to your token./** ----------------------- *//** * Get the signature * * Note: This method is only suitable for debugging. In a production environment, you should calculate the signature on your server. The front end can get the signature by calling an API. * Example: * async function () { *  return fetch('http://xxx.com/get-ar-sign').then(res => res.json()); * }; */const getSignature = function () {    const timestamp = Math.round(new Date().getTime() / 1000);    const signature = sha256(timestamp + token + APPID + timestamp).toUpperCase();    return { signature, timestamp };};let w = 720;let h = 480;// Get the input streamconst stream = await navigator.mediaDevices.getUserMedia({    audio: true,    video: { width: w, height: h }})// The basic settings for the Tencent Effect SDKconst config = {    input: stream,    auth: {        licenseKey: LICENSE_KEY,        appId: APPID,        authFunc: getSignature    },    // Configure the initial effects (optional)    beautify: {        whiten: 0.1, // The brightening effect. Value range: 0-1.        dermabrasion: 0.5, // The smooth skin effect. Value range: 0-1.        lift: 0.3, // The slim face effect. Value range: 0-1.        shave: 0, // The V shape effect. Value range: 0-1.        eye: 0, // The big eyes effect. Value range: 0-1.        chin: 0, // The chin effect. Value range: 0-1.        â¦â¦    },    language: 'en',    â¦â¦}// Pass `config` to the Tencent Effect SDKconst ar = new ArSdk(config);// You can display the effect and filter list in the `created` callback.ar.on('created', () => {    // Get the built-in makeup effects and stickers    ar.getEffectList({        Type: 'Preset'    }).then((res) => {        const list = res.map(item => ({            "name": *item.Name,            id: item.EffectId,            cover: item.CoverUrl,            url: item.Url,            label: item.Label,            type: item.PresetType,        }));        const makeupList = list.filter(item=>item.label.indexOf('Makeup')>=0)        const stickerList = list.filter(item=>item.label.indexOf('Sticker')>=0)        // Show the makeup and sticker lists        renderMakeupList(makeupList);        renderStickerList(stickerList);    }).catch((e) => {        console.log(e);    });    // Get the built-in filters    ar.getCommonFilter().then((res) => {        const list = res.map(item => ({            "name": *item.Name,            id: item.EffectId,            cover: item.CoverUrl,            url: item.Url,            label: item.Label,            type: item.PresetType,        }));        // Show the filter list        renderFilterList(list);    }).catch((e) => {        console.log(e);    });});ar.on('ready', async (e) => {    // After receiving the `ready` callback, you can call `setBeautify`, `setEffect`, or `setFilter` to configure effects.    // For example, you can use `range input` to set the smooth skin effect:    $('#dermabrasion_range_input').change((e) => {        ar.setBeautify({            dermabrasion: e.target.value, // The smooth skin effect. Value range: 0-1.        });    });    // In the `created` callback, apply the effects based on user interactions with the makeup effect and sticker lists. The `setEffect` API supports three types of request parameters. For details, see the SDK integration guide.    $('#makeup_list li').click(() => {        ar.setEffect([{id: effect.id, intensity: 1}]);    });    $('#sticker_list li').click(() => {        ar.setEffect([{id: effect.id, intensity: 1}]);    });    // In the `created` callback, apply the filter based on user interactions with the filter list. The value `1` for the second parameter of `setFilter` indicates the filter strength. For details, see the SDK integration guide.    ar.setFilter(filterList[0].id, 1);    $('#filter_list li').click(() => {        ar.setFilter(filter.id, 1);    });    // Get the output stream of the Tencent Effect SDK    const arStream = await ar.getOutput();});ar.on('error', (e) => {    console.log(e);});
```

To learn more about UI control, you can download our code package at the end of this document.

### Step 4. Publish the stream

```
let livePusher = new TXLivePusher()// Set the basic stream publishing parameters (begin)let DOMAIN = 'Your push domain'let AppName = 'Your app name' let StreamName = 'Your stream name'let txSecret = 'Your txSecret'let txTime = 'Your txTime'// Set the basic stream publishing parameters (end)let pushUrl = `webrtc://${DOMAIN}/${AppName}/${StreamName}?txSecret=${txSecret}&txTime=${txTime}`// Set the preview (optional)livePusher.setRenderView('id_local_video')// Capture the streamlivePusher.startCustomCapture(arStream).then(()=>{    // Publish the stream immediately (you can also use another API to control when to start publishing the stream)    livePusher.startPush(pushUrl)})
```

In the above code, both `txSecret` and `txTime` need to be calculated. You can use the [**address generator**](https://console.tencentcloud.com/live/addrgenerator/addrgenerator) of the **CSS console** to quickly generate the parameters and get the publishing URL. For detailed directions, see [Address Generator](https://www.tencentcloud.com/document/product/267/31084).
After the stream is successfully published (`startPush), you should be able to see the video with effects applied.

### Step 5. Play the stream

> **Note:**For the example project, you need to start the web service of your device and make sure that the HTML file can be accessed via the specified port.

- If you have an available playback domain, follow the steps in [Live Playback](https://www.tencentcloud.com/document/product/267/31559) to play the stream.
- If you donât have a playback domain, you can preview the stream in [Stream Management](https://console.tencentcloud.com/live/streammanage) of the **CSS console**.

## Sample Code Package

You can download our sample code package [here](https://github.com/tencentcloud-webar/web-demo-en). The code for publishing over WebRTC is in `AR_LEB_WEB`.


---
*Source: [https://trtc.io/document/53886](https://trtc.io/document/53886)*
