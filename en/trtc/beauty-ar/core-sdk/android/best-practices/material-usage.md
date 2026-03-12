# Material Usage

## Filters

Each filter is an image in png format. When using it, you need to pass the image path to the SDK. See below for the operation steps.

### Scenario1: Using TEBeautyKit

TEBeautyKit is a UI panel library for BeautyAR. It is designed for users to use and manage beauty features quickly and conveniently.

See below for the operation steps.

1. **Refer to**[Integrating UIKit (Android)](https://www.tencentcloud.com/document/product/1143/60196)**.**
2. **Adding Filter Resources**

Place the newly added filter image in your project's `assets/lut` directory. Then, modify the panel configuration file `assets/beauty_panel/lut.json`, adding a new item based on the existing content in json. When the APP runs, calling the `TEBeautyKit``copyRes` method will copy the filter image from the assets directory to the downloadPath directory configured in `lut.json`.

3. **Configuring Filter Icons**

The icon field in `lut.json` represents the icon of the filter. Place the icon in the `assets/beauty_panel/panel_icon/lut_icon` directory. The value of the icon field can also be the URL of the icon, starting with `http` or `https`, and TEBeautyKit will fetch the icon from the internet.

4. **Configuring Filter Resources**

The resourceUri field in `lut.json` is the path where the filter image is saved in the app's private directory. Configure the resources based on the existing items and change the suffix of resourceUri from "xxx.png" to the file name of the newly added filter, avoiding conflicts with existing filters in `lut.json`. The resourceUri field can also be the URL of the filter image, starting with `http` or `https`. When the URL is clicked, the filter image will be downloaded from the internet and saved in the downloadPath directory configured in `lut.json`.

### Scenario 2: Integrating the BeautyAR SDK Directly

1. Place the newly added filter image in any directory of your project's assets. Then, upon app initialization, copy the image to the app's private directory or SD card to get the image path, marked as `/path/to/your/lut_xxx.png`. For simplicity, it is recommended to place the image in the assets/lut directory and then copy the copyRes code of TEBeautyKit from the demo project for use.
2. When using a filter, call the SDK's [setEffect](https://www.tencentcloud.com/document/product/1143/60201#32a345ed-73c4-4c60-bc7e-3f91b9a4755c) method and pass the filter image path to the SDK.

## Animation Stickers

Each animation is a folder. When using it, you need to pass the path of the folder to the SDK. See below for the operation steps.

### Scenario 1: Using TEBeautyKit

TEBeautyKit is a UI panel library for BeautyAR. It is designed for users to use and manage the beauty features quickly and conveniently.

See below for the operation steps.

1. **Refer to**[Integrating UIKit (Android)](https://www.tencentcloud.com/document/product/1143/60196)**.**
2. **Adding Animation Materials**

Place the newly added animation folder in the `assets/MotionRes` directory of your project. Then, modify the panel configuration file `assets/beauty_panel/motions.json`, adding a new item based on the existing content. When the APP runs, calling the `TEBeautyKit`'s `copyRes` method will copy the animation folder from the assets directory to the downloadPath directory configured in `motions.json`.

3. **Configuring Animation Icons**

The icon field in `motions.json` represents the icon of the animation. Place the icon in the `assets/beauty_panel/panel_icon/motions_icon` directory. The value of the icon field can also be the URL of the icon, starting with `http` or `https`, and TEBeautyKit will fetch the icon from the internet.

4. **Configuring Animation Materials**

The resourceUri field in `motions.json` is the path where the animation is saved in the app's private directory. Configure the materials based on the existing items, avoiding conflicts with existing animations in `motions.json`. The resourceUri field can also be the URL of the animation zip file, starting with `http` or `https`. When the URL is clicked, the zip file will be downloaded from the internet and saved in the downloadPath directory configured in `motions.json`.

### Scenario 2: Integrating the BeautyAR SDK Directly

Place the newly added animation folder in any directory of your project's assets. Then, upon app initialization, copy the folder to the app's private directory or SD card to get the animation folder, marked as `/path/to/your/motion`. When using the animation, call the SDK's [setEffect](https://www.tencentcloud.com/document/product/1143/60201#32a345ed-73c4-4c60-bc7e-3f91b9a4755c) method and pass the path to the SDK.

## Beauty Makeup and Background Segmentation

Their usage is the same as the Animation Sticker described above, with the corresponding json files being `makeup.json` and `segmentation.json`, respectively.


---
*Source: [https://trtc.io/document/73782](https://trtc.io/document/73782)*
