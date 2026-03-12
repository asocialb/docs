# Custom Seat View

This document mainly introduces how to customize a `SeatGridView`.

## Prerequisites

Before using `SeatGridView`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67506#) to SeatGridView to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding SeatGridView to the View

You need to import the `SeatGridView` module first, then create a SeatGridView object and add it to your view.

iOS

Android

```
import UIKitimport RTCRoomEngineimport SeatGridView class CustomizeSeatViewController: UIViewController {    private let seatGridView: SeatGridView = {         let view = SeatGridView()      self.seatGridView.setSeatViewDelegate(self)      return view    }        override func viewDidLoad() {        super.viewDidLoad()        self.seatGridView.setSeatViewDelegate(self)        // Add seatGridView to the view and set layout constraints    }}
```

```
import com.trtc.uikit.livekit.seatGridView.SeatGridView;public class CustomizeSeatViewActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        SeatGridView seatGridView = new SeatGridView(this);        addContentView(seatGridView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));    }}
```

### Step 2: Customizing a Seat

iOS

Android

If you want to customize the seat view, you need to implement the `SeatGridView` delegate `SGSeatViewDelegate`.

```
SGSeatViewDelegate
```

The following is a usage example:

```
SGSeatViewDelegate
```

If you want to customize the seat view, you need to implement the `SeatGridView` adapter `SeatViewAdapter`.

```
public interface SeatViewAdapter {    View createSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo);    void updateSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo, View seatView);    void updateUserVolume(SeatGridView seatGridView, int volume, View seatView);}
```

The following is a usage example:

```
seatGridView.setSeatViewAdapter(new VoiceRoomDefine.SeatViewAdapter() {    @Override    View createSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo) {        TextView seatUserName = new TextView(CustomizeSeatViewActivity.this);        seatUserName.setText(seatInfo.userName);        return seatUserName;    }        @Override    void updateSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo, View seatView) {    }        @Override    void updateUserVolume(SeatGridView seatGridView, int volume, View seatView) {    }});
```


---
*Source: [https://trtc.io/document/67499](https://trtc.io/document/67499)*
