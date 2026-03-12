# Run Sample Code

**Beauty AR Web** allows you to implement AR beautification, filters, makeup, stickers, and other features on websites. This document describes how to quickly run a web application that supports real-time beautification locally. Based on this application, you can implement other features as instructed in relevant documents.

> **Note:**This project is a test project intended for local testing only. To officially launch your project with Beauty AR Web capabilities, you need to purchase an official license and configure the website domain in the product console. For more information, see [Official License](https://trtc.io/document/60213?platform=web&product=beautyar).

## Step 1. Create a license

### Applying for a trial license

Ensure you have created a web license as instructed in [Applying for a trial license](https://www.tencentcloud.com/document/product/1143/60218#).

Fill in the project name and enter the local development address for the domain, taking `test.webar.com` as an example. Click Confirm to complete the creation.

- The Web License is authorized for the domain name, so please fill in the actual domain of your projectâs business site (do not enter localhost:xxxx).
- When using the Web License, the domain information will be validated, so it is essential to ensure that the domain used during actual operation matches the one entered when applying for the license, **excluding localhost addresses**. Since the localhost address is automatically validated as successful, even if `test.webar.com` is filled in above, you can still use `localhost:xxxx` as the development address to run the Demo locally without issues.

> **Note:**The trial license is valid for only 14 days (it can be renewed once for an additional 14 days, totaling 28 days). Each account can create a maximum of one test license. For formal projects, please visit the [Official License](https://trtc.io/document/60213?platform=web&product=beautyar) page to buy as needed.

### Getting the App idãlicense key and token.

After the creation, you can see the information of the created test project in the project list and get the`License Token` for Beauty AR Web and the `License key` for the test project. you also can get the `App ID`.

> **Note:**The **license** **token** is used to calculate the authentication signature, so make sure to keep it secure and confidential. Here, the token is used to calculate the signature on the frontend just to help you run the demo locally. In a real production environment, you need to implement the signature algorithm on the server.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6cc438e20e0111f0a6d15254007c27c5.png)

## Step 2. Run locally

1. Pull [sample project](https://github.com/tencentcloud-webar/web-demo-en/tree/master/quick-start) code.

```
 git clone https://github.com/tencentcloud-webar/web-demo-en.git cd quick-start
```

2. replace the specified configuration items in `index.js` with the license key, token, and `APPID` obtained in [step 1](https://www.tencentcloud.com/document/product/1143/68963#.E6.AD.A5.E9.AA.A41.EF.BC.9A.E5.88.9B.E5.BB.BA-license.5B.5D(id.3Astep1)) as shown below:

```
/** ----- Authentication configuration ----- *//** * Tencent Cloud account's APPID *  * You can also view your APPID in the [Account Center](https://console.tencentcloud.com/developer). */const APPID = ''; // Set it to your Tencent Cloud account APPID./** * Web LicenseKey *  * obtained from Before You Start */const LICENSE_KEY = ''; // Set it to your license key./** * The token used to calculate the signature. *  * Note: This method is only suitable for debugging. In a production environment, you should store the token and calculate the signature on your server. The front end can get the signature by calling an API. For details, see * https://trtc.io/document/50099?platform=web&product=beautyar#e4ce3483-41f7-4391-83ae-f4b61e221ea0 */const token = ''; // Set it to your token./** ----------------------- */
```

3. Run the project in the local development environment.

> **Note:**Before running your project locally, make sure the `nodejs` environment is already installed on the device.

Run the following commands successively in the project directory and access `localhost:8090` in the browser to try out the capabilities of Beauty AR Web.

```
# Install dependenciesnpm i # Compile and run the codenpm run dev
```

After following the steps above, you can try out the filters and effects of the SDK for desktop browser. You can use the built-in materials to try out various makeup filters and effects as instructed in [Start Integration](https://www.tencentcloud.com/document/product/1143/68777), or use more capabilities of Beauty AR Web such as custom stickers, makeup, and filters. For detailed directions on how to customize effect materials, please [Material Customization Guide](https://trtc.io/document/53887?platform=web&product=beautyar).


---
*Source: [https://trtc.io/document/68963](https://trtc.io/document/68963)*
