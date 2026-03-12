# Web

This document primarily introduces How to quickly run through the AIConversationKit Demo project and experience high-quality conversational AI project. Follow this documentation, and you can run through the Demo within 20 minutes and eventually experience a conversational AI project with a complete UI interface.

| **AI Conversational Interface** |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cf3749c0139311f08c275254001c06ec.png) |

## Configuration Demo

First, go to [console](https://console.trtc.io/) to create an application, and then [activate the corresponding service](https://www.tencentcloud.com/document/product/647/69002#).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/33e61e9821a811f0a62e525400454e06.png)

## Run through the Demo

1. After creation, go to the application details page, select **RTC-Engine** **> Conversational AI**, refer to [No-Code Quick Integration Of Conversational AI Feature](https://www.tencentcloud.com/document/product/647/68137) configure conversational AI parameters, click **Quick Integration** in the lower right corner, switch to Web, and retrieve the SecretId, SecretKey and Config parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d656f3b212e511f0a9cd5254007c27c5.png)

2. When running server-side code, first install the related dependencies and replace the corresponding secretId and secretKey.

```
npm i express tencentcloud-sdk-nodejs-trtc
```

3. Run the frontend code.
4. Start your conversational AI project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8971a335137711f0a63e5254005ef0f7.png)


---
*Source: [https://trtc.io/document/68999](https://trtc.io/document/68999)*
