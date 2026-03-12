# Material Usage

## Filters

Each filter is an image in png format. When using it, you need to pass the image path to the SDK.

### Scenario 1: Using TEBeautyKit

`TEBeautyKit` is a UI panel library for BeautyAR. It is designed for users to use and manage beauty features quickly and conveniently. See below for the operation steps.

1. **Refer to**[Integrating UIKit (iOS)](https://www.tencentcloud.com/document/product/1143/60194)**.**
2. **Adding Filter Materials**

Place the newly added filter image in your project's `lut.bundle` directory. Then, modify the panel configuration file `TEBeautyKit/Assets/json/lut.json`, adding a new item based on the existing content in json.

3. **Configuring Filter Icons**

The icon field in `lut.json` represents the icon of the filter. Place the icon in the `TEBeautyKit/Assets/BeautyRes` directory. The value of the icon field can also be the URL of the icon, starting with http or https, and `TEBeautyKit` will fetch the icon from the internet.

4. **Configuring Filter Resources**

The `resourceUri` field in `lut.json` is the path where the filter image is saved in the app's private directory. Configure the resources based on the existing items in json and change the suffix of `resourceUri` from "xxx.png" to the file name of the newly added filter, avoiding conflicts with existing filters in lut.json. The `resourceUri` field can also be the URL of the filter image, starting with http or https. When the URL is clicked, the filter image will be downloaded from the internet and saved in the `downloadPath` directory configured in `lut.json`.

### Scenario 2: Integrating the BeautyAR SDK Directly

1. Place the newly added filter image in your project's `lut.bundle` directory. If using a dynamic download approach, download the filter image to the sandbox and record the path of the filter image.
2. When using a filter, call the SDK's `setEffect` method and pass the path of the filter image to the SDK. For the method of operation, refer to [Effect Parameters](https://www.tencentcloud.com/document/product/1143/60207).

## Animation Stickers

Each animation is a folder. When using it, you need to pass the path of this folder to the SDK. See below for the operation steps.

### Scenario 1: Using TEBeautyKit

TEBeautyKit is a UI panel library for BeautyAR. It is designed for users to use and manage the beauty features quickly and conveniently.

1. **Refer to**[Integrating UIKit (iOS)](https://www.tencentcloud.com/document/product/1143/60194)**.**
2. **Adding Animation Resources**

Place the newly added animation folder in the corresponding `resource bundle` directory of your project: in `2dMotionRes.bundle` for 2D animations, in `3dMotionRes.bundle` for 3D animations, in `ganMotionRes.bundle` for fun animations, or in `handMotionRes.bundle` for gesture animations. Then, modify the panel configuration file `TEBeautyKit/Assets/json/motions.json`, adding a new item based on the existing content.

3. **Configuring Animation Icons**

The `icon` field in `motions.json` represents the icon of the animation. Place the icon in the `TEBeautyKit/Assets/BeautyRes` directory. The value of the icon field can also be the URL of the icon, starting with `http or https`, and `TEBeautyKit` will fetch the icon from the internet.

4. **Configuring Animation Resources**

The `resourceUri` field in `motions.json` is the path where the animation is saved in the app's private directory. Configure the resources based on the existing items, avoiding conflicts with existing animations in `motions.json`. The `resourceUri` field can also be the URL of the animation zip file, starting with `http or https`. When the URL is clicked, the zip file will be downloaded from the internet and saved in the `downloadPath` directory configured in `motions.json`. The animation zip file needs to be unzipped before use.

### Scenario 2: Integrating the BeautyAR SDK Directly

Place the newly added animation folder in the corresponding `resource bundle` directory of your project, in `2dMotionRes.bundle` for 2D animations, in `3dMotionRes.bundle` for 3D animations, in `ganMotionRes.bundle` for fun animations, or in `handMotionRes.bundle` for gesture animations. In BeautyAR SDK of version 3.6.0 or earlier, if the animation file is encrypted, you need to copy it to the sandbox and record its path. If using a dynamic download approach, download the animation file to the sandbox and unzip it, and then record the path of the unzipped animation folder. When using the animation, call the SDK's setEffect method and pass the path to the SDK. Refer to [Effect Parameters](https://www.tencentcloud.com/document/product/1143/60207).

## Beauty Makeup and Background Segmentation

Their usage is the same as the Animation Sticker described above, with the corresponding json files being makeup.json and segmentation.json, respectively.


---
*Source: [https://trtc.io/document/73781](https://trtc.io/document/73781)*
