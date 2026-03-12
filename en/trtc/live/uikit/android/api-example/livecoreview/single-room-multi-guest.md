# Single-room Multi-Guest

This document mainly introduces how to use the `LiveStreamCore` module's `LiveCoreView` to implement Mic Connect.

`LiveCoreView` supports the following capabilities for Mic Connect:

| [Request to connect](https://www.tencentcloud.com/document/product/647/67472#f1743fa3-3864-4085-a62e-892c86e8ab13) | [Audience terminate connection](https://www.tencentcloud.com/document/product/647/67472#b42d71d5-e940-469c-bdd8-6b23d2e685fd) | [Host terminate connection](https://www.tencentcloud.com/document/product/647/67472#1f8f55ea-0af7-4297-86a8-d8a208d38a89) |
| --- | --- | --- |

## Prerequisites

Before using `LiveStreamCore`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67475#) to LiveStreamCore to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding LiveCoreView to the View

You need to first import the `LiveStreamCore` module, then create a `LiveCoreView` view object and add it to your view.

iOS

Android

```
LiveStreamCore
```

```
public class AudienceConnectionActivity extends AppCompatActivity implements LiveCoreViewDefine.ConnectionObserver {    private LiveCoreView liveCoreView;    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        liveCoreView = new LiveCoreView(this);        addContentView(liveCoreView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));        liveCoreView.registerConnectionObserver(this);    }    @Override    protected void onDestroy() {        super.onDestroy();        liveCoreView.unregisterConnectionObserver(this);    }}
```

### Step 2: Audience Connection

#### Request to connect

When you want to connect with someone via mic, call the `requestIntraRoomConnection` API with three parameters: the userId of the person to connect with, the timeout duration, and whether to turn on the camera.

iOS

Android

```
let userId = "100012" // Please replace this with the userId of the user you want to initiate Mic Connect with. If you pass an empty string, it will default to connecting with the host.let timeout = 30     // Replace this with the timeout duration for requesting to speak, in seconds. If set to 0, the SDK will not perform timeout detection or trigger timeout callbackslet openCamera = true // When you want to initiate a video call, set openCamera to true. For an audio call, set it to false.self.liveCoreView.requestIntraRoomConnection(userId: userId, timeOut: timeout, openCamera: true) {    // Successfully sent request to connect via mic} onError: { code, message in    // Failed to send request to connect via mic}
```

```
String userId = "anchorUserId"; // Replace this with the userId of the person you want to connect with via micint timeout = 30; // Replace this with the timeout duration for requesting to speak, in seconds. If set to 0, the SDK will not perform timeout detection or trigger timeout callbacksboolean openCamera = true; // When you want to initiate a video call, set openCamera to true. For an audio call, set it to false.liveCoreView.requestIntraRoomConnection(userId, timeout, true, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Successfully sent request to connect via mic    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed to send request to connect via mic    }});
```

When you are the invitee for a connection, you will receive the `onUserConnectionRequest` callback. You can call the `respondIntraRoomConnection` API to accept or reject the connection.

iOS

Android

```
respondIntraRoomConnection
```

```
// Response succeeded
```

#### Audience terminate connection

If you do not want to connect with the host, call the `terminateIntraRoomConnection` API to disconnect.

iOS

Android

```
self.liveCoreView.terminateIntraRoomConnection()
```

```
liveCoreView.terminateIntraRoomConnection();
```

#### Host terminate connection

If you want to interrupt the connection with an audience member, call the `disconnectUser` API and pass in the corresponding user's userId.

iOS

Android

```
let targetUserId = "100010"  // Replace this with the userId of the audience member you want to disconnecself.liveCoreView.disconnectUser(userId: targetUserId) {    // Successfully disconnected} onError: { code, message in     // Failed to disconnect}
```

```
String targetUserId = "100010";  // Replace this with the userId of the audience member you want to disconnect fromliveCoreView.disconnectUser(targetUserId, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Successfully disconnected    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed to disconnect    }});
```


---
*Source: [https://trtc.io/document/67472](https://trtc.io/document/67472)*
