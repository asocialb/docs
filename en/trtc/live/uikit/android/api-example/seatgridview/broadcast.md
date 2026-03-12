# Broadcast

This document mainly introduces how to use `SeatGridView` to go live. Only after going live can other audience members enter the voice chat room to listen to the host's broadcast.

## Prerequisites

Before using `SeatGridView`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67506#) to SeatGridView to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding SeatGridView to the View

You need to import the `SeatGridView` module first, then create a SeatGridView object and add it to your view.

iOS

Android

```
import RTCRoomEngineimport SeatGridView class BroadcastController: UIViewController {    private let seatGridView: SeatGridView = {         let view = SeatGridView()      return view    }()        override func viewDidLoad() {        super.viewDidLoad()        // Add seatGridView to the view and set layout constraints    }}
```

```
import com.trtc.uikit.livekit.seatGridView.SeatGridView;public class BroadcastActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        SeatGridView seatGridView = new SeatGridView(this);        addContentView(seatGridView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));    }}
```

### Step 2: Preparing Live Streaming Parameters

When calling the `startVoiceRoom` API, you need to fill in the key parameters `TUIRoomInfo`. The following is a detailed introduction:

#### Parameters: TUIRoomInfo

`TUIRoomInfo` consists of many fields, but usually, you only need to focus on filling in the following fields:

| Parameter Name | Field Description | Additional Notes | Data Type | Example |
| --- | --- | --- | --- | --- |
| roomId | Room ID | Only letters (a-z, A-Z), digits (0-9), underscores, and hyphens are allowed. | New Character String | "room_100001" |
| name | Room Name | Room name of string type. | New Character String | "denny`s room" |
| seatMode |  Microphone Mode | This field is effective only when microphone control is enabled.It is divided into "freeToTake" and "applyToTake" modes. In freeToTake mode, audience members can take the microphone freely without applying. In applyToTake mode, audience members need the room owner's approval to take the microphone. | Enumeration Value | TUISeatMode.applyToTake |
| maxSeatCount | Maximum Number of Microphones | The maximum number of mic positions of numeric type, referring to the maximum number of people on mic simultaneously, maxSeatCount.The maximum number of mic positions is consistent with the upper limit of the number of 'Multi-guests' in the purchased [package](https://trtc.io/document/59407). | Digits | 10 |
| isSeatEnabled | Whether to enable microphone position control | Boolean type mic control enable flag. | Boolean value | true |
| roomType | Room type | Divided into two room types: "conference" and "live". Voice chat belongs to live, so use live here. | Enumeration Value | TUIRoomType.live |

#### Step 3: Starting Live Streaming

After preparing the parameters in Step 2 `TUIRoomInfo`, you can call the `startVoiceRoom` API function to start live streaming.

After starting the live stream, you also need to call the `startMicrophone` API to enable the local microphone, ensuring that the audience can hear your voice.

iOS

Android

```
// Assemble TRTC room entry parameters. Replace the field values in `TRTCParams` with your own parameter valueslet roomInfo = TUIRoomInfo()roomInfo.roomId = "voice_100001"   // Please replace it with your own room ID.roomInfo.name = "denny`s room"    // Please replace it with your own room name.roomInfo.seatMode = .applyToTake  // In typical video live streaming scenarios, the apply-to-take mode is used for joining the mic. If in your case, the audience doesn't need to apply to join the mic, you can change this to freeToTake.roomInfo.maxSeatCount = 10        // Please replace it with the maximum number of seats in the Live package you purchased.roomInfo.isSeatEnabled = true     // If you do not need seat control, you can set isSeatEnabled to falseroomInfo.roomType = .live         // Ensure the room type is live.self.seatGridView.startVoiceRoom(roomInfo: roomInfo) { [weak self] roomInfo in    // Going live successfully    guard let self = self else { return }    self.seatGridView.startMicrophone {      // Successfully turned the local mic on    } onError: { code, message in      // Failed to turn the local mic on    }} onError: { code, message in     // Failed to go live}
```

```
TUIRoomDefine.RoomInfo roomInfo = new TUIRoomDefine.RoomInfo();roomInfo.roomId = "voice_100001"; // Please replace it with your own room IDroomInfo.name = "denny's room"; // Please replace it with your own room nameroomInfo.maxSeatCount = 10; // Please replace it with the maximum number of seats in the Live package you purchasedroomInfo.isSeatEnabled = true; // If you do not need seat control, you can set isSeatEnabled to falseroomInfo.roomType = TUIRoomDefine.RoomType.LIVE;   // Ensure the room type is live.roomInfo.seatMode = TUIRoomDefine.SeatMode.APPLY_TO_TAKE;  // If you don't need to apply to take the mic, you can set this to FREE_TO_TAKE.seatGridView.startVoiceRoom(roomInfo, new TUIRoomDefine.GetRoomInfoCallback() {    @Override    public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {        // Going live successfully        seatGridView.startMicrophone( new TUIRoomDefine.ActionCallback() {            @Override            public void onSuccess() {                // Successfully turned the local mic on            }            @Override            public void onError(TUICommonDefine.Error error, String message) {                // Failed to turn the local mic on            }        });    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed to go live    }});
```


---
*Source: [https://trtc.io/document/67505](https://trtc.io/document/67505)*
