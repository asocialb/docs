# Cross-room Multi-Guest

This document mainly introduces how to use the `LiveStreamCore` module's `LiveCoreView` to achieve anchor connection.

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
import com.trtc.uikit.livekit.livestreamcore.LiveCoreView;import com.trtc.uikit.livekit.livestreamcore.LiveCoreViewDefine;public class AnchorConnectionActivity extends AppCompatActivity implements LiveCoreViewDefine.ConnectionObserver {    private LiveCoreView liveCoreView;    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        liveCoreView = new LiveCoreView(this);        addContentView(liveCoreView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));        liveCoreView.registerConnectionObserver(this);    }}
```

### Step 2: Anchor Connection

#### Initiating Connection

When you want to initiate a connection with an anchor in another room, you can call the `requestCrossRoomConnection` API, passing in two parameters: the room ID of the anchor's room and the timeout duration.

iOS

Android

```
let targetRoomId = "live_100011" // Please replace this with the room ID of the anchor you want to connect withlet timeout = 30 // Please replace this with the timeout duration for your speaking request, in seconds. If set to 0, the SDK will not perform timeout detection or trigger timeout callbacks.self.liveCoreView.requestCrossRoomConnection(roomId: targetRoomId, timeOut: timeout) {    // Successfully initiated connection request} onError: { code, message    // Failed to initiate connection request}
```

```
String targetRoomId = "live_100011"; // Please replace this with the room ID of the anchor you want to connect withint timeout = 30; // Replace this with the timeout duration for requesting to speak, in seconds. If set to 0, the SDK will not perform timeout detection or trigger timeout callbacksliveCoreView.requestCrossRoomConnection(targetRoomId, timeout, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Successfully initiated connection request    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed to initiate connection request    }});
```

When you receive a connection invitation, you will get the `onCrossRoomConnectionRequest` callback. You can accept or reject the connection request via the `respondToCrossRoomConnection` API.

iOS

Android

```
respondToCrossRoomConnection
```

```
// Response succeeded
```

#### Terminating the Connection

When you want to terminate the current connection, you can call the `terminateCrossRoomConnection` API.

iOS

Android

```
self.liveCoreView.terminateCrossRoomConnection()
```

```
liveCoreView.terminateCrossRoomConnection();
```


---
*Source: [https://trtc.io/document/67471](https://trtc.io/document/67471)*
