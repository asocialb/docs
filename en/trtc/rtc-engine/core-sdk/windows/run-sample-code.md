# Run Sample Code

This document describes how to quickly run the demo for the TRTC Windows SDK.

## Prerequisites

- Install Visual Studio 2017 or later (v2019 is recommended).
- Install [Qt 5.14.x](https://download.qt.io/archive/qt/5.14/5.14.2/).
- Find the right version of Qt Add-in for your Visual Studio on the [Qt website](https://download.qt.io/development_releases/vsaddin/). Download and install it.
- Open Visual Studio, in the menu bar, select **Extension > QT VS Tools > Qt Options > Qt Versions**, and add a **MSVC compiler**.
- Copy all the DLL files in `SDK/CPlusPlus/Win64/lib` (for 64-bit Windows) to the `debug/release` folder of the project directory.

> **Noteï¼**`debug/release` is auto-generated after environment configuration in Visual Studio. For 32-bit Windows, copy all the DLL files in `SDK/CPlusPlus/Win32/lib to the debug/release` folder of the project directory.

## Steps To Run Demo

### Step 1. Download the Demo

Download the [TRTC_Windows-C++](https://github.com/Tencent-RTC/TRTC_Windows) sample demo code on github which SDK has been imported into, or run the following command in a terminal:

```
git clone https://github.com/Tencent-RTC/TRTC_Windows.git
```

### Step 2. Configure the Demo

1. Log in to the [TRTC Console](https://console.trtc.io/) and click **Create Application**. If you have already done so, you may skip this step.
2. And then, your own `SDKAppID` and `SDKSecretKey` of your created application can be obtained in the **Basic Information** section.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b861c20739ac11ef9b60525400bdab9d.png)

3. Replace the values of `SDKAPPID` and `SDKSECRETKEY`in `defs.h` file under `TRTC-API-Example-C++`/`TRTC-API-Example-Qt`/`src`/`Util` directory with the information obtained in **Step 2** .

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7d8671643ac111efb958525400f69702.png)

> **Noteï¼**In the demo above, we used **SDKSecretKey** to generate **UserSig** locally in order to help you go through the demo easier. However, in the production environment, you are not supposed to generate userSig in this way, which may lead to **SDKSecretKey** leakage, thereby creating a chance for attackers to steal your TRTC traffic. **The correct way to generate UserSig is to integrate**[**Server-Side Generation of UserSig**](https://trtc.io/document/35166)**on your server.** When an user enters the room:Send a http request to your server.Generate a UserSig on your server.Return it to the user to enter the room.When you deploy your page to a production environment, you need to have your page accessed through the HTTPS(e.g. `https://domain/xxx`). For the reason, please refer to the document [Page Access Protocol Restriction Description](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-05-info-browser.html#h2-3).

### Step 3. Run the Demo

Open `QTDemo.sln` in the TRTC-API-Example-Qt directory with Microsoft Visual Studio (v2019 is recommended), set up the Qt environment (Qt 5.14 is recommended), and run the project.

## FAQs

- If you encounter any problems with access and use, please refer to [FAQs](https://trtc.io/document/36058?platform=windows&product=rtcengine).
- If you have any requirements or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/46748](https://trtc.io/document/46748)*
