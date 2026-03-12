# Live Stream Management Interface (Vue)

## Overview

This document provides a detailed introduction to the **Monitoring Webpage** in the TUILiveKit Demo. You can directly integrate our developed viewing page into your existing project as specified in this document, or customize the webpage style, layout, and feature items according to your needs.

## Feature Overview

| **Feature Category** | **Specific Abilities** |
| --- | --- |
| **Multi-stream live room monitoring** | Supports showing 8+ live streams simultaneously (actual quantity customizable). |
| **Low-latency playback** | Pull live stream in real time with â¤3s delay. |
| **Standalone audio control** | Enable/disable sound for any live streaming room individually to avoid interference. |
| **View details via a click** | Click any live streaming room window to quickly enter the details page and view anchor information and key details. |
| **Dismiss rule-violating live streaming room with one click** | Operate directly on the details page or monitoring panel to quickly shut down live streaming rooms with rule violations and enhance handling efficiency. |

## **Feature Demonstration**

The monitoring page provides default behavior and style. However, if the default behavior and style cannot fully meet your requirements, you can also customize the UI. It mainly includes **multi-stream live room monitoring on the same screen, low-delay playback, standalone audio control, one-click view detail, and one-click dismiss rule-violating live streaming rooms.**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2fec997ae4611f0b08552540044a08e.png)

## Quick Run-Through

### Step 1: Configuring the Environment and Activating the Service

Before performing quick integration, you need to refer to [preparations](https://www.tencentcloud.com/document/product/647/73735) to meet the environment configuration and activate the corresponding service.

### Step 2: Downloading Demo

```
git clone https://github.com/Tencent-RTC/TUIKit_Vue3.git
```

### Step 3: Dependency Installation

```
cd TUIKit_Vue3/demos/live-monitor-vue3 && npm install && cd server && npm install
```

### Step 4: Starting the Server Project

```
SDKAppID
```

```
http://localhost:9000/api
```

### Step 5: Starting the Front-End Project

```
SDKAppID
```

```
SDKAppID
```

```
npm run dev
```

## Tailor-Made

You have successfully run the Demo of the monitoring page. If you need UI customization, you can refer to the following methods. Custom content includes but is not limited to `color theme, font, rounded corners, buttons, icons, input boxes, pop-ups` in the source code, which can be **added, deleted, or modified**. Below are examples of color theme, button, and icon customization. You can refer to the implementation approach and apply it to other components to meet your UI customization needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bd2809a1ae4611f096c2525400454e06.png)

### Color Theme

For example, in [Step 5](#step5), you can use the example code to manipulate the theme value to switch color themes.

```
<UIKitProvider theme="dark">  // When the theme input is dark, the overall interface color theme is black  xxx                         // When the theme input is light, the overall interface color theme is white-theme</UIKitProvider>
```

### Button

If you need to add or replace buttons for UI customization, it can be obtained as follows, using the three buttons for page operation in the live list as an example.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a34a1e85ae2f11f096c2525400454e06.png)

Refer to the image above to find the source code for the corresponding Button in the specified position, and perform UI customization operations such as **adding, deleting, or replacing** the current Button.

### Icons

If you need to perform UI customization such as adding or replacing icons, you can implement it as follows, using the Icon in the live list as an example. Follow the guide below to find the corresponding Icon position and perform UI customization operations such as adding, deleting, or replacing.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a35b4c54ae2f11f096c2525400454e06.png)


---
*Source: [https://trtc.io/document/74097](https://trtc.io/document/74097)*
