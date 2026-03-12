# Microphone Management

This document mainly introduces the microphone management capabilities of `SeatGridView`.

`SeatGridView` supports the following microphone management capabilities:

| [Start Microphone](https://www.tencentcloud.com/document/product/647/67501#b69cb2f6-d5bb-49c3-800a-61a654f28a39) | [Stop Microphone](https://www.tencentcloud.com/document/product/647/67501#8b6823f0-2ef9-400c-8f00-e7c40af1b431) |
| --- | --- |
| [Mute Microphone](https://www.tencentcloud.com/document/product/647/67501#2c9ff222-49c7-4b73-a0ef-93011b7464bc) | [Unmute Microphone](https://www.tencentcloud.com/document/product/647/67501#72a93aa9-24c8-4931-b1e6-10e617304cf9) |

## Prerequisites

Before using `SeatGridView`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67506#) to SeatGridView to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding SeatGridView to the View

You need to import the `SeatGridView` module first, then create a SeatGridView object and add it to your view.

iOS

Android

```
import UIKitimport RTCRoomEngineimport SeatGridView class SeatManagementController: UIViewController {    private let seatGridView: SeatGridView = {         let view = SeatGridView()      return view    }        override func viewDidLoad() {        super.viewDidLoad()        self.seatGridView.addObserver(observer: self)        // Add seatGridView to the view and set layout constraints    }        deinit {        self.seatGridView.removeObserver(observer: self)    }}
```

```
import com.trtc.uikit.livekit.seatGridView.SeatGridView;public class MicrophoneManagementActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        SeatGridView seatGridView = new SeatGridView(this);        addContentView(seatGridView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));        seatGridView.addObserver(this);    }    @Override    protected void onDestroy() {        super.onDestroy();        seatGridView.removeObserver(this);    }}
```

### Step 2: Managing the Microphone

#### Start Microphone

Call `startMicrophone` to turn on the microphone.

iOS

Android

```
self.seatGridView.startMicophone {    // Successfully turned on the mic} onError: { code, message in     // Failed to turn on the mic}
```

```
seatGridView.startMicrophone(new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess () {        // Successfully turned on the mic    }    @Override    public void onError (TUICommonDefine.Error error, String message) {        // Failed to turn on the mic    }});
```

#### Stop Microphone

Call `stopMicrophone` to turn off the microphone.

iOS

Android

```
self.seatGridView.stopMicophone()
```

```
seatGridView.stopMicophone();
```

#### Mute Microphone

Call `muteMicrophone` to mute.

iOS

Android

```
self.seatGridView.muteMicrophone()
```

```
seatGridView.muteMicrophone();
```

#### Unmute Microphone

Call `unmuteMicrophone` to unmute.

iOS

Android

```
self.seatGridView.unmuteMicrophone {    print("Unmuted successfully")} onError: { code, message in     print("Failed to unmute")}
```

```
seatGridView.unMuteLocalAudio(new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Successfully unmuted    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // // Failed to unmute    }});
```

When someone's microphone status changes, you will receive a callback `onUserAudioStateChanged`.

iOS

Android

```
func onUserAudioStateChanged(userInfo: TUIUserInfo, hasAudio: Bool, reason: TUIChangeReason) {    if hasAudio {       print("\\(userInfo.userId) has audio")    } else {       print("\\(userInfo.userId) has no audio")    }}
```

```
void onUserAudioStateChanged(TUIRoomDefine.UserInfo userInfo, boolean hasAudio,                             TUIRoomDefine.ChangeReason reason) {    // userInfo.userName's audio status changed}
```


---
*Source: [https://trtc.io/document/67501](https://trtc.io/document/67501)*
