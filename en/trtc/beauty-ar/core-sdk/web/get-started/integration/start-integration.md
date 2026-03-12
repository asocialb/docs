# Start Integration

This document describes how to quickly and securely connect to **Beauty AR Web** and use its features. If you have any questions, please [contact us](https://trtc.io/contact).

## Preparations

Before connecting to the SDK, make sure you have purchased a web license and created a project as instructed in [Activate the Service](https://trtc.io/document/60213#web).

### Getting parameter information

1. Getting the` App ID`, `License Key` and `License Token` from [License Management](https://console.trtc.io/beauty/license).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f4d320c0a2311f0b3015254001c06ec.png)

**Web Domain**: The domain information entered during project creation. The license can be used only under this domain.

> **Note:**Be sure to use the license key and license token that **match the developed domain**, otherwise authentication will fail, and the SDK cannot be properly initialized.

### Preparing signing information

In addition to the license key that is needed to authorize the SDK, you also need to use the token to sign the APIs called in the SDK.

#### Signature algorithm authentication process

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f4e32af0a2311f0ae6a525400454e06.jpeg)

- Token: Your unique ID, which is used to sign SDK APIs.
- App ID: The `APP ID` displayed in the Beauty AR console.
- Timestamp: The current time accurate to the second (10 digits).
- Signature: The signature used for signing, which expires after five minutes.

#### Deploying a signature service

Because the signature expires after a given time, and to prevent the token from being leaked, you need to deploy a signature generation service.

> **Note:**If the token is leaked, your identity will be stolen, which will lead to your resources also being leaked.If the signature generation method is implemented on the frontend, the token may be leaked. Therefore, to safeguard your security, we recommend that you do not implement signature generation on the frontend.

```
// Taking the `express` backend as an example,// Signature algorithm: sha256(timestamp+token+appid+timestamp)const { createHash } = require('crypto');const config = {    appid: 'Your Tencent Cloud `APPID`',    token: 'Your token',}const sha256 = function(str) {    return createHash('sha256')        .update(str)        .digest('hex');}const genSignature = function() {    const timestamp = Math.round(new Date().getTime() / 1000);    const signature = sha256(timestamp + config.token + config.appid + timestamp).toUpperCase(); // Use the token and APP ID obtained above to generate an encrypted string and return it    return { signature, timestamp };}app.get("/get-ar-sign", (req, res) => {    const sign = genSignature();    res.setHeader('Access-Control-Allow-Origin','*');    res.setHeader('Access-Control-Allow-Methods', 'GET, OPTIONS');    res.send(sign);})
```

#### Calling the signature service on the frontend

After deploying the signature service, add a signature acquisition method to your webpage for the SDK to connect to and call.

Web

```
async function getSignature() {    const res = await fetch('Your domain/get-ar-sign')    const authdata = await res.json()    console.log('authdata',authdata)    return authdata}
```

## SDK Integration

After completing the above preparations, follow the process below to connect to and use the SDK.

### Process description

The **Tencent Effect web SDK** offers simple and minimally invasive APIs. To integrate it and use its features, you only need to initialize an instance and add the render node to your webpage.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f4f63560a2311f0a6d15254007c27c5.png)

### Installing the SDK

The SDK is offered as an npm package.

```
npm install tencentcloud-webar
```

In addition, you can also use it for your project by importing JS.

```
<script charset="utf-8" src="https://webar-static.tencent-cloud.com/ar-sdk/resources/latest/webar-sdk.umd.js"></script>
```

### Initializing the SDK

For web integration, we offer two initialization modes for the SDK.

- [Built-in camera and player](https://trtc.io/document/50101?platform=web&product=beautyar): The device's built-in camera and player are used. API calls are easy and fast, with rich interactive features.
- [Custom streams](https://trtc.io/document/50102?platform=web&product=beautyar): You can use this mode if you want to apply effects to your own streams or want greater flexibility and control.

### Using the SDK

##### Configuring beauty filters and special effects

For more information, see [Configuring Filters and Effects](https://trtc.io/document/54291?platform=web&product=beautyar).

##### Segmentation

The keying feature allows you to segment and change the background in the image. For details, see [Configuring Segmentation](https://trtc.io/document/50105?platform=web&product=beautyar).

##### 3D effects

For more information, see [Configuring Filters and Effects](https://trtc.io/document/54291?platform=web&product=beautyar).

##### Animojis and virtual avatars

This capability relies on a WebGL2 environment. For more information, see [Configuring Animojis and Virtual Avatars](https://trtc.io/document/51231?platform=web&product=beautyar).

## Parameters and APIs

See [Parameters and APIs](https://trtc.io/document/50106?platform=web&product=beautyar).

## Sample Code

See [Quick Start](https://trtc.io/document/53939).


---
*Source: [https://trtc.io/document/68777](https://trtc.io/document/68777)*
