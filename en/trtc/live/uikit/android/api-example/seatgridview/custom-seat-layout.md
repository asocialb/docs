# Custom Seat Layout

This document mainly introduces how to customize the seat layout for `SeatGridView`.

## Prerequisites

Before using `SeatGridView`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67506#) to SeatGridView to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding SeatGridView to the View

You need to import the `SeatGridView` module first, then create a SeatGridView object and add it to your view.

iOS

Android

```
import UIKitimport RTCRoomEngineimport SeatGridView class CustomizeSeatLayoutController: UIViewController {    private let seatGridView: SeatGridView = {         let view = SeatGridView()      return view    }        override func viewDidLoad() {        super.viewDidLoad()        // Add seatGridView to the view and set layout constraints    }}
```

```
import com.trtc.uikit.livekit.seatGridView.SeatGridView;public class CustomizeSeatLayoutActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        SeatGridView seatGridView = new SeatGridView(this);        addContentView(seatGridView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));    }}
```

### Step 2: Preparing Seat Layout Parameters

When calling the `setLayoutMode` API, you need to fill in the key parameters `layoutMode` and `layoutConfig`. The following is a detailed introduction:

#### Parameter 1: layoutMode

`ayoutMode` is an enumeration of type `SGLayoutMode`.

| Enumeration value types | Meaning | Additional Notes |
| --- | --- | --- |
| focus | Centralized layout(e.g., 1-3-3 layout, 1 element in the first row, 3 elements in the second and third rows) | Built-in layout styles |
| grid | Grid Layout | Built-in layout styles (this is the default style) |
| vertical | Vertical layout | Built-in layout styles |
| free | Free layout | Custom layout styles |

> **Notes:**When using the built-in layout styles of `seatGridView`, there is no need to provide additional `SGSeatViewLayoutConfig` parameters. You only need to pass the `SGLayoutMode` parameter to setLayoutMode.

#### Parameter Two: layoutConfig

`layoutConfig` is a structure of type `SGSeatViewLayoutConfig`, consisting of the fields `rowConfigs` and `rowSpacing`.

| Parameter Name | Field Description | Data Type |
| --- | --- | --- |
| rowConfigs | Used to store the configuration of each row's seat layout. | An array of SGSeatViewLayoutRowConfig type |
| rowSpacing | Used to store the row spacing of the seat layout | Floating point number |

`SGSeatViewLayoutRowConfig`  consists of four fields: `count`, `seatSpacing`, `seatSize`, and `alignment`.

| Parameter Name | Field Description | Data Type |
| --- | --- | --- |
| count | Number of seats per row | Integer |
| seatSpacing | Vertical spacing of seats in the same row | Floating point number |
| seatSize | Size of the seat | Size type |
| alignment | Arrangement of seats in the same row | SGSeatViewLayoutRowAlignment |

`SGSeatViewLayoutRowAlignment` is an enumeration.

| Enumeration value types | Meaning |
| --- | --- |
| spaceAround | Dispersed alignment, not against the container wall, with remaining space evenly distributed on both sides of each item |
| spaceBetween | Spaced alignment, with the leftmost and rightmost items against the left or right border, and equal spacing between items. |
| spaceEvenly | Average alignment, not against the container wall, with remaining space evenly distributed. |
| start | Left alignment |
| end | Right alignment |
| center | Center alignment |

### Step 3: Setting the Seat Layout

After preparing the parameters `layoutMode` and `layoutConfig` in Step 2, you can call the `setLayoutMode` API function to set the seat layout.

#### Built-In Layout

When using the built-in layout, you only need to pass the `layoutMode` parameter.

iOS

Android

```
// Centralized layoutself.seatGridView.setLayoutMode(layoutMode: .focus)// Grid Layoutself.seatGridView.setLayoutMode(layoutMode: .grid)// Verticalself.seatGridView.setLayoutMode(layoutMode: .vertical)
```

```
// Centralized layoutseatGridView.setLayoutMode(VoiceRoomDefine.LayoutMode.FOCUS, null);// Grid LayoutseatGridView.setLayoutMode(VoiceRoomDefine.LayoutMode.GRID, null);// Vertical layoutseatGridView.setLayoutMode(VoiceRoomDefine.LayoutMode.VERTICAL, null);
```

#### Custom Layout

When using a custom layout, the value of `layoutMode` should be `free` and the corresponding seat layout configuration parameter `layoutConfig` needs to be passed.

For example, to customize a 2, 1, 2 layout, with each row arranged as spaceBetween, center, and spaceBetween:

iOS

Android

```
// Create seat configuration for each rowlet firstRowConfig = SGSeatViewLayoutRowConfig(count: 2,     seatSpacing: 10.0, seatSize: CGSize(width: 50, height: 50), alignment: .spaceBetween)let secondRowConfig = SGSeatViewLayoutRowConfig(count: 1,    seatSpacing: 10.0, seatSize: CGSize(width: 72, height: 72), alignment: .center)let thirdRowConfig = SGSeatViewLayoutRowConfig(count: 2,     seatSpacing: 10.0, seatSize: CGSize(width: 50, height: 50), alignment: .spaceBetween)    let rowConfigs: [SGSeatViewLayoutRowConfig] = [firstRowConfig, secondRowConfig, thirdRowConfig]let layoutConfig = SGSeatViewLayoutConfig(rowConfigs: rowConfigs, rowSpacing: 20.0)// Set layout modeself.seatGridView.setLayoutMode(layoutMode: .free, layoutConfig: layoutConfig)
```

```
// Create seat configuration for each rowVoiceRoomDefine.SeatViewLayoutRowConfig firstRowConfig = new VoiceRoomDefine.SeatViewLayoutRowConfig();firstRowConfig.count = 2;firstRowConfig.seatSpacing = 10;firstRowConfig.seatSize = new VoiceRoomDefine.Size(50,50);firstRowConfig.alignment = SPACE_BETWEEN;VoiceRoomDefine.SeatViewLayoutRowConfig secondRowConfig = new VoiceRoomDefine.SeatViewLayoutRowConfig();secondRowConfig.count = 1;secondRowConfig.seatSpacing = 10;secondRowConfig.seatSize = new VoiceRoomDefine.Size(72,72);secondRowConfig.alignment = CENTER;VoiceRoomDefine.SeatViewLayoutRowConfig thirdRowConfig = new VoiceRoomDefine.SeatViewLayoutRowConfig();thirdRowConfig.count = 2;thirdRowConfig.seatSpacing = 10;thirdRowConfig.seatSize = new VoiceRoomDefine.Size(50,50);thirdRowConfig.alignment = SPACE_BETWEEN;List<VoiceRoomDefine.SeatViewLayoutRowConfig> rowConfigs = new ArrayList<>();rowConfigs.add(firstRowConfig);rowConfigs.add(secondRowConfig);rowConfigs.add(thirdRowConfig);VoiceRoomDefine.SeatViewLayoutConfig config = new VoiceRoomDefine.SeatViewLayoutConfig();config.rowConfigs = rowConfigs;config.rowSpacing = 20;// Set layout modeseatGridView.setLayoutMode(LayoutMode.FREE, config);
```


---
*Source: [https://trtc.io/document/67500](https://trtc.io/document/67500)*
