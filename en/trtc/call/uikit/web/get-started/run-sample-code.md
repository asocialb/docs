# Run Sample Code

This article will introduce how to quickly implement an audio and video call demo. You will complete the following key steps within 10 minutes and ultimately obtain a video call feature with a full user interface.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/be8d9e591bd211efa1975254005ac0ca.png)

## Environment preparations

- [Node.js](https://nodejs.org/en/) version 16+.
- Modern browser, supporting WebRTC API.

## Step 1: Download the demo

1. Open the terminal and clone the repository.

```
git clone https://github.com/Tencent-RTC/TUICallKit.git
```

2. Install dependencies.

React

Vue3

```
 cd ./TUICallKit/Web/basic-react
```

```
 cd ./TUICallKit/Web/basic-vue3
```

```
 npm install
```

## Step 2: Configure the demo

[Go to the Activate Service page](https://trtc.io/document/59832?platform=web&product=call&menulabel=web) and get the `SDKAppID and SDKSecretKey`**, then fill them in the**`GenerateTestUserSig-es.js` file.

React

Vue3

File path: `TUICallKit/Web/basic-react/src/debug/GenerateTestUserSig-es.js`

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0cf5a502668411ef97015254002693fd.png)

File path: `TUICallKit/Web/basic-vue3/src/debug/GenerateTestUserSig-es.js`

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2846515e668411efb0e2525400a9236a.png)

## Step 3: Run the demo

Open the terminal, copy the sample command to run the demo.

TUICallKit/Web/basic-react

TUICallKit/Web/basic-vue3

```
npm run dev
```

```
npm run dev
```

> **Warning:****For local environments, access under the localhost protocol. For public network experience, access under the HTTPS protocol. For details, refer to**[Network Access Protocol Instructions](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-05-info-browser.html#h2-3)**.**

## Step 4: Make your first call

1. Open the browser page, enter the project run address, and log in to userID (defined by you).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ca8e7485668311ef86bb525400fdb830.png)

2. Input the callee's userID and click all to experience your first call.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f06fe362668311efa32852540075b605.png)


---
*Source: [https://trtc.io/document/60415](https://trtc.io/document/60415)*
