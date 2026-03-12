# Custom Video Layout

This document mainly introduces how to use the `LiveStreamCore` module's `LiveCoreView` to implement custom video layouts.

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
import com.trtc.uikit.livekit.livestreamcore.LiveCoreView;public class CustomizeVideoLayoutActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        LiveCoreView liveCoreView = new LiveCoreView(this);        addContentView(liveCoreView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));    }}
```

### Step 2: Preparing Video Layout Parameters

When calling the `setLayoutMode` API, you need to fill in the key parameters `layoutMode` and `layoutJson`. The details are as follows:

#### Parameter 1: LayoutMode

`layoutMode` is an enumeration of the `LayoutMode` type.

| Enumeration value types | Meaning | Additional Notes |
| --- | --- | --- |
| gridLayout | Grid Layout | Built-in layout styles (this is the default style) |
| floatLayout | Floating Window Layout | Built-in layout styles |
| freeLayout | Vertical layout | Custom layout styles |

#### Parameter 2: layoutJson

layoutJson is a layout JSON string.

JSON structure description is as follows:

```
{	"1": {                                 // Number of video views		"backgroundColor": "#000000",      // Background color of the canvas in RGB hexadecimal format		"viewInfoList": [{                 // Layout information and background color of each video view			"x": 0,                        // Horizontal offset as a proportion of screen width, range [0, 1]			"y": 0,                        // Vertical offset as a proportion of screen width, range [0, 1]			"width": 1,                    // Width of the video view as a proportion of screen width, range [0, 1]			"height": -1,                  // Height of the video view as a proportion of screen width, range [0, 1] or -1; -1 means the view height is the same as the screen height			"zOrder": 0,                   // Z-order of the video view, higher values mean the view is on top			"backgroundColor": "#000000"   // Background color of the current video view in RGB hexadecimal format		}]	}}
```

### Step 3: Custom Video Layout

With the parameters `layoutMode` and `layoutConfig` from Step 2 ready, you can call the `setLayoutMode` API function to set the mic position layout.

#### Built-In Layout

When using the built-in layout, you only need to pass the `layoutMode` parameter.

iOS

Android

```
// Grid Layoutself.liveCoreView.setLayoutMode(layoutMode: .gridLayout)// Floating Window Layoutself.liveCoreView.setLayoutMode(layoutMode: .floatLayout)
```

```
// Grid LayoutliveCoreView.setLayoutMode(LiveCoreViewDefine.LayoutMode.GRID_LAYOUT, "");// Floating Window LayoutliveCoreView.setLayoutMode(LiveCoreViewDefine.LayoutMode.FLOAT_LAYOUT, "");
```

#### Custom Layout

When using a custom layout, the value of `layoutMode` should be `freeLayout` and the corresponding mic position layout configuration parameter `layoutJson` needs to be passed.

For example, to achieve the following video layout:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a2118d2abdd811ef8d65525400fdb830.png)

LayoutJson should be:

```
{  "1": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.0,      "width": 1.0,      "height": -1.0,      "zOrder": 0,      "backgroundColor": "#000000"    }]  },  "2": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.384,      "width": 0.5,      "height": 0.89333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.5,      "y": 0.384,      "width": 0.5,      "height": 0.89333,      "zOrder": 0,      "backgroundColor": "#000000"    }]  },  "3": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.384,      "width": 0.666666666,      "height": 0.666666666,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }]  },  "4": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.384,      "width": 0.5,      "height": 0.5,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.5,      "y": 0.384,      "width": 0.5,      "height": 0.5,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 0.8826,      "width": 0.5,      "height": 0.5,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.5,      "y": 0.8826,      "width": 0.5,      "height": 0.5,      "zOrder": 0,      "backgroundColor": "#000000"    }]  },  "5": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }]  },  "6": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }]  },  "7": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 1.050666666,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }]  },  "8": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 1.050666666,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 1.050666666,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }]  },  "9": {    "backgroundColor": "#000000",    "viewInfoList": [{      "x": 0.0,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.384,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 0.717333333,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.0,      "y": 1.050666666,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.333333333,      "y": 1.050666666,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }, {      "x": 0.666666666,      "y": 1.050666666,      "width": 0.333333333,      "height": 0.333333333,      "zOrder": 0,      "backgroundColor": "#000000"    }]  }}
```

Call the `setLayoutMode` API to implement a custom layout:

iOS

Android

```
let freeLayoutJson = ""  // Please replace this with the previous JSON stringself.liveCoreView.setLayoutMode(layoutMode: .freeLayout, layoutJson: freeLayoutJson)
```

```
String freeLayoutJson = "";  // Please replace this with the previous JSON stringliveCoreVjiew.setLayoutMode(LiveCoreViewDefine.FREE_LAYOUT, freeLayoutJson);
```


---
*Source: [https://trtc.io/document/67470](https://trtc.io/document/67470)*
