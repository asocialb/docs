# Broadcast

This document mainly introduces how to use the core component of video live streaming, the `LiveStreamCore` module's `LiveCoreView` to start a live broadcast. Only after the broadcast starts can other viewers enter the live room to watch the host's live stream.

## Prerequisites

Before using `LiveStreamCore`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67475#) to LiveStreamCore to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding LiveCoreView to the View

You need to first import the `LiveStreamCore` module, then create a `LiveCoreView` view object and add it to your view.

iOS

Android

```
import RTCRoomEngineimport LiveStreamCore class BroadcastController: UIViewController {    private let liveCoreView: LiveCoreView = {         let view = LiveCoreView()      return view    }()        override func viewDidLoad() {        super.viewDidLoad()        // Add liveCoreView to the view and set layout constraints    }}
```

```
import com.trtc.uikit.livekit.livestreamcore.LiveCoreView;public class LiveActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        LiveCoreView liveCoreView = new LiveCoreView(this);        addContentView(liveCoreView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));    }}
```

### Step 2: Preparing Live Streaming Parameters

When calling the `startLiveStream` API, you need to fill in the key parameters `TUIRoomInfo`. The detailed introduction is as follows:

#### Parameters: TUIRoomInfo

`TUIRoomInfo` consists of many fields, but usually, you only need to focus on filling in the following fields:

| Parameter Name | Field Description | Additional Notes | Data Type | Example |
| --- | --- | --- | --- | --- |
| roomId | Room ID | Only letters (a-z, A-Z), digits (0-9), underscores, and hyphens are allowed. | New Character String | "room_100001" |
| name | Room Name | Room name of string type. | New Character String | "denny`s room" |
| seatMode |  Microphone Mode | This field is effective only when microphone control is enabled.It is divided into "freeToTake" and "applyToTake" modes. In freeToTake mode, audience members can take the microphone freely without applying. In applyToTake mode, audience members need the room owner's approval to take the microphone. | Enumeration Value | TUISeatMode.applyToTake |
| maxSeatCount | Maximum Number of Microphones | The maximum number of mic positions of numeric type, referring to the maximum number of people on mic simultaneously, maxSeatCount.The maximum number of seats is consistent with the maximum number of 'Multi-guests' in the [package](https://trtc.io/document/59407) you purchased. | Digits | 10 |
| isSeatEnabled | Whether to enable microphone position control | Boolean type mic control enable flag. | Boolean value | true |
| roomType | Room type | There are two types of rooms: "conference" and "live". For video live streaming, use live. | Enumeration Value | TUIRoomType.live |

### Step 3: Starting Live Streaming

After preparing the parameters `TUIRoomInfo` in step 2, you can call the `startLiveStream` API function to start the live stream.

After starting the live stream, you also need to call the `startCamera` and `startMicrophone` APIs to turn on the local camera and microphone, ensuring that the audience can see your video and hear your voice.

iOS

Android

```
// Assemble TRTC room entry parameters. Replace the field values in `TRTCParams` with your own parameter valueslet roomInfo = TUIRoomInfo()roomInfo.roomId = "voice_100001"  // Please replace it with your own room ID.roomInfo.name = "denny`s room"    // Please replace it with your own room name.roomInfo.maxSeatCount = 10        // Please replace it with the maximum number of seats in the Live package you purchased.roomInfo.isSeatEnabled = true     // If you do not need seat control, you can set isSeatEnabled to falseroomInfo.roomType = .live         // Ensure the room type is live.roomInfo.seatMode = .applyToTake  // The usual mode for video live streaming is applyToTake.self.liveCoreView.startLiveStream(roomInfo: roomInfo) { [weak self] roomInfo in    // Going live successfully    guard let self = self else { return }    // Turn the local camera on    self.liveCoreView.startCamera(useFrontCamera: true) { // This selects the front camera. You can also pass in false to select the rear camera.        // Successfully turned the local camera on    } onError: { code, message in         // Failed to turn the local camera on    }    // Turn the local mic on    self.liveCoreView.startMicrophone {       // Successfully turned the local mic on    } onError: { code, message in        // Failed to turn the local mic on    }} onError: { code, message in     // Failed to go live}
```

```
TUIRoomDefine.RoomInfo roomInfo = new TUIRoomDefine.RoomInfo();roomInfo.roomId = "voice_100001"; // Please replace it with your own room IDroomInfo.name = "denny's room"; // Please replace it with your own room nameroomInfo.maxSeatCount = 10; // Please replace it with the maximum number of seats in the Live package you purchasedroomInfo.isSeatEnabled = true; // If you do not need seat control, you can set isSeatEnabled to falseroomInfo.roomType = TUIRoomDefine.RoomType.LIVE; // Ensure the room type is live.roomInfo.seatMode = TUIRoomDefine.SeatMode.APPLY_TO_TAKE; // The usual mode for video live streaming is applyToTake.liveCoreView.startLiveStream(roomInfo, new TUIRoomDefine.GetRoomInfoCallback() {    @Override    public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {        // Going live successfully        liveCoreView.startCamera(true, new TUIRoomDefine.ActionCallback() {            @Override            public void onSuccess() {                // Successfully turned the local camera on            }            @Override            public void onError(TUICommonDefine.Error error, String message) {                 // Failed to turn the local camera on            }        });        liveCoreView.startMicrophone( new TUIRoomDefine.ActionCallback() {            @Override            public void onSuccess() {                // Successfully turned the local mic on            }            @Override            public void onError(TUICommonDefine.Error error, String message) {               // Failed to turn the local mic on            }        });    }    @Override    public void onError(TUICommonDefine.Error error, String message) {       // Failed to go live    }});
```


---
*Source: [https://trtc.io/document/67474](https://trtc.io/document/67474)*
