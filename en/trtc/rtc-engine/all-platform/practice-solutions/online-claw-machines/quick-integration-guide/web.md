# Web

## Implementation Workflow

This section summarizes some common business processes in online claw machines to help you better understand the implementation of the entire scenario.

Online Claw Machine TRTC Streaming

Online Claw Machine RTMP Streaming

The diagram below illustrates the sequence of RTC Engine streaming for an online claw machine, including processes such as RTC Engine streaming from a network camera and user-side stream pulling.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c807677b412b11f0912c52540044a08e.png)

The diagram below illustrates the sequence of RTMP streaming for an online claw machine, including processes such as RTMP streaming from a network camera and user streaming pull.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cf16416f412b11f0be2052540099c741.png)

## Integration Preparation

### Step 1: Activate the Service

The online claw machine scenario typically relies on the paid PaaS service of [RTC Engine](https://trtc.io/document/rtc-engine-overview?product=rtcengine&menulabel=core%20) for implementation. RTC Engine provides real-time audio and video interaction capabilities. You can choose to activate the service based on your specific business requirements.

1. Log in to the [RTC Engine console](https://console.trtc.io/app), then click **Create application** on the **Applications** page. You can choose to upgrade the RTC Engine application edition as needed. For example, upgrading to the Pro Edition unlocks more value-added feature services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2c933cc7412c11f0be2052540099c741.jpg)

> **Note:**It is recommended to create two separate applications for the test environment and the production environment, respectively. The first activation of RTC Engine includes a free 10,000-minute trial package.The RTC Engine monthly packages (Free Trial, Lite, Standard, and Pro packages) offer different value-added feature services. For details, see [RTC Engine Monthly Packages](https://trtc.io/document/56025?product=pricing#f10b65d1-6e8d-41e3-8686-84909b00a1a2).

2. After creating the application, you can view its basic information in [Application Management](https://console.trtc.io/app) > **Application Overview**. Keep your **SDKAppID** and **SDKSecretKey** secure for future use, and take precautions to prevent key leakage that may result in unauthorized traffic usage.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ddf574f6412b11f0be2052540099c741.png)

### Step 2: Import the SDK

#### NPM Integration

1. Install [trtc-sdk-v5](https://www.npmjs.com/package/trtc-sdk-v5) in your project using [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).

```
npm install trtc-sdk-v5 --save
```

2. Import a module in the project script.

```
import RTC Engine from 'trtc-sdk-v5';
```

#### Script Integration

Add the following code to your web page:

```
<script src="trtc.js"></script>
```

> **Note:**The trtc.js needs to be downloaded to your local project for integration. For the corresponding SDK, see [download link and demo address](https://github.com/Tencent-RTC/TRTC_Web?tab=readme-ov-file).

### Step 3: Perform Authentication and Authorization

UserSig is a security protection signature designed by TRTC to prevent malicious attackers from misappropriating your cloud service usage rights. RTC Engine validates this authentication credential when entering a room.

- Debugging phase: You can generate the UserSig using either the [Client Sample Code](https://trtc.io/document/35166?product=conference&menulabel=uikit&platform=web) or the [Console Access](https://console.trtc.io/usersig). This method is intended solely for debugging and testing purposes.
- Production stage: It is recommended to use the server-side computation scheme for UserSig with a higher security level to prevent client-side reverse engineering and key leakage.

Implementation process:

1. Before calling the initialization API of the SDK, have your app request UserSig from your server first.
2. Your server generates the UserSig based on the SDKAppID and UserID.
3. The server returns the generated UserSig to your app.
4. Your app sends the obtained UserSig to the SDK through a specific API.
5. The SDK submits the SDKAppID + UserID + UserSig to the cloud server for verification.
6. The cloud platform verifies the validity of the UserSig.
7. After the verification is passed, the RTC Engine SDK will be provided with real-time audio and video services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f10db379412b11f0be2052540099c741.jpeg)

> **Note:**The method of generating UserSig locally during the debugging and testing stage is not recommended for the production environment because it may be easily decompiled and reversed, causing key leakage.We provide the source code for server-side UserSig calculation in multiple languages (Java/Go/PHP/Node.js/Python/C#/C++). For details, see [UserSig Calculation Source Code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk).

### Step 4:  SDK Initialization and Event Listening

Create an RTC Engine SDK instance and set an event listener.

```
const trtc = TRTC.create();trtc.on('error', err => {  console.error(err);});
```

> **Note:**It is recommended to listen to SDK event notifications. Perform log printing and handling for some common errors. For details, see [Error Code Table](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.INVALID_PARAMETER).

### Step 5: Generate RTMP Streaming Address (RTMP Streaming)

Generate an RTMP streaming address.

```
rtmp://rtmp.rtc.qq.com/push/roomID?sdkappid=application&userid=username&usersig=signature
```

- push: The RTMP appName.
- The room ID, application, username, and signature in the address need to be replaced with your business-specific values.
- To simplify parameters, only string room IDs are supported,up to 64 characters, including numbers, letters, or underscores.

> **Note:**If other RTC Engine endpoints need to watch the RTMP stream, use a **string room ID for room entry**.

- For UserSig generation rules, see [UserSig](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk) (**The signature is valid**).

**Example:**

```
rtmp://rtmp.rtc.qq.com/push/hello-string-room?sdkappid=140*****66&userid=******rtmp2&usersig=eJw1jdE********RBZ8qKGRj8Yp-wVbv*mGMVZqS7w-mMDQL
```

## Integration Process

### API Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fcfd0be4412b11f09bbe525400454e06.jpg)

### Step 1: Claw Machine Streaming

#### RTC Engine Streaming

1. Calculate and generate UserSig using either the [client sample code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk) or the [console](https://console.trtc.io/usersig).
2. Configure the SdkAppid, UserId, UserSig, RoomId, and other information on the RTC Engine network camera or streaming box to start streaming.

> **Note:**RTC Engine room IDs are divided into numeric type `roomId` and string type `strRoomId`. The rooms of these two types are not interconnected. It is recommended to unify the room ID type.RTC Engine user roles are divided into anchors and audiences. Only hosts have streaming permissions. The user role should be specified upon room entry. If the user role is not specified, the default role is anchor.In the online claw machine scenario, it is recommended to use the `rtc` mode for entering a room, as this ensures lower latency.

#### **RTMP Streaming**

1. Use the [RTMP Address Generator](https://console.trtc.io/rtmptool) to generate an RTMP streaming address.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fb85bb932fd211f091625254001c06ec.png)

2. Configure the RTMP streaming address to the RTMP network camera or streaming box to start streaming.

### Step 2: Enter a Room and Play Streams

1. User enters RTC Engine room.

```
const trtc = TRTC.create();// Enter a roomtry {  await trtc.enterRoom({ strRoomId, scene:'rtc', sdkAppId, userId, userSig});  console.log('Room entry successful. ');} catch (error) {  console.error('Room entry failed. ' + error);}
```

2. User subscribes to hostâs audio and video stream.

```
${userId}_${streamType}
```

### Step 3: Exit Room

1. User exits the room.

```
await trtc.exitRoom(); // After a successful room exit, if the RTC engine instance is no longer needed, you can call the trtc.destroy method to terminate the instance and promptly release related resources.// Once terminated, the RTC engine instance can no longer be used, and a new instance needs to be created.trtc.destroy();
```

2. Dissolve room.
  - **Server-side Dissolve Room.**

RTC Engine provides the server-side API [`DismissRoom`](https://trtc.io/document/34269?product=rtcengine&menulabel=core%20) for dissolving rooms with numeric types and the API [`DismissRoomByStrRoomId`](https://trtc.io/document/39631?product=rtcengine&menulabel=core%20sdk) for dissolving rooms with string types. You can use these server-side APIs to remove all users from the room and dissolve the room.

  - **Client-side Dissolve Room.**

The client does not provide an API for directly dissolving a room. Each client should call [`exitRoom`](https://trtc.io/document/50762?platform=android&product=rtcengine&menulabel=core%20sdk#4651ae2c9ff5aa99442102e0d77a8606) to exit the room. Once all anchors and audiences have exited the room, the room will be automatically dissolved according to the RTC Engine room lifecycle rules. For details, see [RTC Engine Exit the Room](https://trtc.io/document/62045?product=rtcengine&menulabel=core%20sdk&platform=android#5055ad66-53b1-4539-88ec-6992d45bb0fd).

## Exception Handling

### Autoplay Policy Restriction

In the scenario of web-based stream pulling, to enhance the experience of users entering the room, autoplay is set by default upon entering the room. However, in Android and iOS WebViews, the default autoplay policy may be different from that in browsers. You can refer to the following documentation to disable the autoplay restriction in your app.

- Disable autoplay restriction in Android WebView: Call [setMediaPlaybackRequiresUserGesture(false)](https://developer.android.com/reference/android/webkit/WebSettings#setMediaPlaybackRequiresUserGesture(boolean)) to disable autoplay restriction.
- Disable autoplay restriction in iOS WebView: [Set mediaTypesRequiringUserActionForPlayback to WKAudiovisualMediaTypeNone](https://developer.apple.com/documentation/webkit/wkwebviewconfiguration/1851524-mediatypesrequiringuseractionfor).

> **Note:**For suggestions for handling complete autoplay policy restrictions, see [Tutorial: Handle Autoplay Restriction](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/tutorial-21-advanced-auto-play-policy.html).RTC Engine on iOS may not autoplay in the WeChat Browser using the above methods. If you need to enable autoplay, please [contact us](https://trtc.io/contact).


---
*Source: [https://trtc.io/document/77218](https://trtc.io/document/77218)*
