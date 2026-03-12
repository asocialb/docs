# Listen

This document mainly introduces how to use `SeatGridView` to listen to a certain host's live broadcast.

## Prerequisites

Before using `SeatGridView`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67506#) to SeatGridView to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding SeatGridView to the View

You need to import the `SeatGridView` module first, then create a SeatGridView object and add it to your view.

iOS

Android

```
import SeatGridView import RTCRoomEngineclass ListenController: UIViewController {    private let seatGridView: SeatGridView = {         let view = SeatGridView()      return view    }()        override func viewDidLoad() {        super.viewDidLoad()        self.seatGridView.addObserver(observer: self)        // Add seatGridView to the view and set layout constraints    }        deinit {        self.seatGridView.removeObserver(observer: self)    }}
```

```
import com.trtc.uikit.livekit.seatGridView.SeatGridView;public class ListenActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        SeatGridView seatGridView = new SeatGridView(this);        addContentView(seatGridView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));    }}
```

### Step 2: Listening

Call `joinVoiceRoom` to enter a host's live room for listening.

iOS

Android

```
let roomId = "voice_100001"    // Please replace it with the room ID of the host you want to listen toself.seatGridView.joinVoiceRoom(roomId: roomId) { roomInfo in    // Listening succeeded} onError: { code, message in    // Listening failed}
```

```
String roomId = "live_100001";    // Please replace it with the room ID of the host you want to listen toseatGridView.joinVoiceRoom(roomId, new TUIRoomDefine.GetRoomInfoCallback() {    @Override    public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {        // Successfully joined the live streaming room    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed to join the live streaming room    }});
```

When you want to leave the live room, you can call the leaveVoiceRoom API.

iOS

Android

```
self.seatGridView.leaveVoiceRoom {   // Successfully exited the live streaming room} onError: { code, message in     // Failed to exit the live streaming room}
```

```
seatGridView.leaveVoiceRoom( new , new TUIRoomDefine.GetRoomInfoCallback() {    @Override    public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {        // Successfully exited the live streaming room    }    @Override    public void onError(TUICommonDefine.Error error, String message) {         // Failed to exit the live streaming room    }});
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
*Source: [https://trtc.io/document/67504](https://trtc.io/document/67504)*
