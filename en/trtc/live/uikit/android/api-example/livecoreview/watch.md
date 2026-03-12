# Watch

This document mainly introduces how to use the `LiveStreamCore` module's `LiveCoreView` to view the host's live stream.

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
public class WatchActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        LiveCoreView liveCoreView = new LiveCoreView(this);        addContentView(liveCoreView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));    }}
```

### Step 2: Viewing

Call `joinLiveStream` to enter a host's live room for viewing.

iOS

Android

```
let roomId = "live_100001"    // Please replace it with the room ID of the host you want to viewself.liveCoreView.joinLiveStream(roomId: roomId) { roomInfo in    // Successfully joined the live streaming room} onError: { code, message in    // Failed to join the live streaming room}
```

```
String roomId = "live_100001";    // Please replace it with the room ID of the host you want to viewliveCoreView.joinLiveStream(roomId, new TUIRoomDefine.GetRoomInfoCallback() {    @Override    public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {        // Successfully joined the live streaming room    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed to join the live streaming room    }});
```

When the host dismisses the room, you will receive the `onRoomDismissed` callback.

iOS

Android

```
func onRoomDismissed(roomId: String) {    // The room has been dissolved}
```

```
void onRoomDismissed(String roomId) {    // The room has been dissolved}
```


---
*Source: [https://trtc.io/document/67473](https://trtc.io/document/67473)*
