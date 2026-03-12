# Beauty Effects

TUILiveKit provides two kinds of beauty effects: basic beauty filter and advanced beauty effect. If you are not satisfied with the effect of the basic beauty filter, you can choose to integrate the advanced beauty effect to satisfy more advanced beauty needs.

## Basic Beauty Filter

TUILiveKit seamlessly integrates basic beauty filter functionality by default. The basic beauty filter includes whitening, skin smoothing, and rosy effect features, and the intensity of beauty effects can be adjusted to satisfy different needs. These functionalities are already built into TUILiveKit, with no additional configuration or integration required.

### Panel Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d3a82aa24d811f0a62e525400454e06.png)

## Advanced Beauty Effect

TUILiveKit Advanced Beauty Effect uses [Tencent Special Effect Beauty](https://www.tencentcloud.com/zh/document/product/1143/53942).

### Effect Display

| **V-Face** | **Eye Distance** | **Slim Nose** | **3D Stickers** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3e0602ab24d811f0a62e525400454e06.gif) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/38b9a8ba24d811f09e67525400bf7822.gif) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3af308ba24d811f0b47352540044a08e.gif) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3a3d8d9224d811f091625254001c06ec.gif) |

> **Notes:**Advanced beauty effect requires separate payment. For details, see [Tencent Effect SDK](https://www.tencentcloud.com/document/product/1143/45372?lang=en&pg=).

### Start Integration

#### Step 1: Seamless Integration of `Tebeautykit`

Android

iOS

1. Download and decompress [TUILiveKit](https://github.com/Tencent-RTC/TUILiveKit/archive/refs/heads/main.zip), and copy the `Android/tebeautykit` folder into your project at the same directory level as the app.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2cd24e4624d811f0b44b5254007c27c5.png)

2. Edit your own project's `settings.gradle` file and add the following code:

```
  include ':tebeautykit'
```

1. Download and decompress [TUILiveKit](https://github.com/Tencent-RTC/TUILiveKit/archive/refs/heads/main.zip), and copy the `iOS/TEBeautyKit` folder into your project at the same directory level as the `Podfile`.

``

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2ca1266f24d811f0a62e525400454e06.png)

2. Edit the `podfile` and add the following code:

```
  pod 'TEBeautyKit',:podspec => './TEBeautyKit/TEBeautyKit.podspec'
```

3. Execute the `pod install` command in the terminal.

#### Step Two: Authenticate & Set Beauty Resource

1. Apply for authorization, obtain `LicenseUrl` and `LicenseKey`. Please refer to [license guide](https://www.tencentcloud.com/document/product/1143/50266?lang=en&pg=).
2. In the place where your business is initialized (by default, at the same position as [log in](https://www.tencentcloud.com/document/product/647/60037#step4)), add the following authentication code and replace the `beauty package number`, `LicenseUrl`, and `LicenseKey` you applied for:

Android

iOS

```
LicenseUrl
```

iOS can set relevant content in the `didFinishLaunchingWithOptions` method of `AppDelegate`.

```
LicenseURL
```

> **Notes:**If you are unclear about the Beauty Number, click [overview of beauty package numbers](https://www.tencentcloud.com/document/product/1143/45371).**Complete the above steps to integrate the advanced beauty effect.**


---
*Source: [https://trtc.io/document/69851](https://trtc.io/document/69851)*
