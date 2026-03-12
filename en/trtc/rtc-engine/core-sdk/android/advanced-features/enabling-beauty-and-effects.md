# Enabling Beauty and Effects

This tutorial mainly introduces how to realize the function of beauty effects in TRTC live broadcast. With beauty management, you can use the following features:

- Set up "skin smoothing", "whitening", "ruddy" and other beauty effects.
- Set up "enlarge eyes", "thin face", "V face", "adjust chin" and "shorten face", "shrink nose", "brighten eyes", "whiten teeth", "remove eye bags", "remove wrinkles", "remove wrinkles", etc to fix face special effects.
- Set the "hairline", "interorbital distance", "canthi", "mouth shape", "ala nasi", "nose position", "lip thickness" and "facial form", etc to fix face special effects.
- Set up "eyeshadow", "blush" and other beauty effects.
- Set up animated effects such as dynamic stickers and face pendants.

## Prerequisites

To use the beauty effect feature, you need an SDKAppID. Please ensure the RTC service status is normal. Alternatively, you can integrate **TEBeautyKit** for more beauty AR features. For details, refer to [Beauty AR](https://trtc.io/document/60216).

## Set the beauty algorithm and level

TRTC provides you with a variety of peeling algorithms, including **smooth**, **natural** and **optimal**, you can choose the most suitable solution according to your own product.

Different from the other three platforms to set the beauty effect through the beauty management class `TXBeautyManager`, **TRTC Windows** platform needs to call [setBeautyStyle](https://trtc.io/document/50770#b7be60907f35f85041714fcedcc34719) to set the beauty, whitening, ruddy and other special effects.

Android

iOS

Mac

Windows

```
// Declare the TRTCCloud variable and initializeprivate TRTCCloud mCloud;mCloud = TRTCCloud.sharedInstance(getApplicationContext());TXBeautyManager beautyManager = mCloud.getBeautyManager();beautyManager.setBeautyStyle(TXBeautyManager.TXBeautyStyleSmooth); // Beauty Style set to smoothbeautyManager.setBeautyLevel(9); // Beauty level set to 9
```

```
//  AppDelegate.h@property (nonatomic, strong) TRTCCloud *trtcCloud;//  AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance]; // Creating the TRTC instanceTXBeautyManager * beautyManager = [self.trtcCloud getBeautyManager];[beautyManager setBeautyStyle:TXBeautyStyleSmooth]; // Beauty Style set to smooth[beautyManager setBeautyLevel:9]; // Beauty level set to 9
```

```
//  AppDelegate.h@property (nonatomic, strong) TRTCCloud *trtcCloud;//  AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance]; // Creating the TRTC instanceTXBeautyManager * beautyManager = [self.trtcCloud getBeautyManager];[beautyManager setBeautyStyle:TXBeautyStyleSmooth]; // Beauty Style set to smooth[beautyManager setBeautyLevel:9]; // Beauty level set to 9
```

```
ITRTCCloud* trtc_cloud_;trtc_cloud_->setBeautyStyleSmooth(TRTCBeautyStyleSmooth, 5, 5, 5); // Set beauty, whitening, reddening and other special effects
```

> **Noteï¼**The value of beauty level ranges from 0 to 9, where 0 indicates off and 9 indicates the most obvious effect.When you set only the beauty style but not the beauty level, you will not be able to see the effect of the beauty style since the default beauty level is 0.

## Set the whitening level and ruddy level

Call `setWhitenessLevel` and `setRuddyLevel` to set the whitening level and rosy level respectively. The above two interface parameters are the same as `setBeautyLevel`.

Android

iOS

Mac

```
// Declare the TRTCCloud variable and initializeprivate TRTCCloud mCloud;mCloud = TRTCCloud.sharedInstance(getApplicationContext());TXBeautyManager beautyManager = mCloud.getBeautyManager();beautyManager.setWhitenessLevel(9); // Whitening level set to 9beautyManager.setRuddyLevel(9); // Set the redness level to 9
```

```
//  AppDelegate.h@property (nonatomic, strong) TRTCCloud *trtcCloud;//  AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance]; // Creating the TRTC instanceTXBeautyManager * beautyManager = [self.trtcCloud getBeautyManager];[beautyManager setWhitenessLevel:9]; // Whitening level set to 9[beautyManager setRuddyLevel:9]; // Set the redness level to 9
```

```
//  AppDelegate.h@property (nonatomic, strong) TRTCCloud *trtcCloud;//  AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance]; // Creating the TRTC instanceTXBeautyManager * beautyManager = [self.trtcCloud getBeautyManager];[beautyManager setWhitenessLevel:9]; // Whitening level set to 9[beautyManager setRuddyLevel:9]; // Set the redness level to 9
```

## Set the color filter effect and intensity

The color filter is a color lookup table image containing a color mapping relationship. According to the mapping relationship in the lookup table, the SDK will conduct secondary processing on the original video image captured by the camera to achieve the expected filter effect.

Android

iOS

Mac

```
// Declare the TRTCCloud variable and initializeprivate TRTCCloud mCloud;mCloud = TRTCCloud.sharedInstance(getApplicationContext());TXBeautyManager beautyManager = mCloud.getBeautyManager();Bitmap filterMap = BitmapFactory.decodeResource(getResources(), R.drawable.filterImage);
beautyManager.setFilter(filterMap); // Set the filter effectbeautyManager.setFilterStrength(1); // Set the color filter strength to 1
```

```
//  AppDelegate.h@property (nonatomic, strong) TRTCCloud *trtcCloud;//  AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance]; // Creating the TRTC instanceTXBeautyManager * beautyManager = [self.trtcCloud getBeautyManager];UIImage *filterImage = [UIImage imageNamed:@"filterImage"];[beautyManager setFilter:filterImage]; // Set the filter effect[beautyManager setFilterStrength:1]; // Set the color filter strength to 1
```

```
//  AppDelegate.h@property (nonatomic, strong) TRTCCloud *trtcCloud;//  AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance]; // Creating the TRTC instanceTXBeautyManager * beautyManager = [self.trtcCloud getBeautyManager];NSImage *filterImage = [NSImage imageNamed:@"filterImage"];[beautyManager setFilter:filterImage]; // Set the filter effect[beautyManager setFilterStrength:1]; // Set the color filter strength to 1
```

> **Noteï¼**The value range of filter color intensity is 0 - 1, the default value is 0.5, the larger the value, the more obvious the filter effect.

## Set the special effects

TRTC provides a variety of facial effects for Android and iOS platforms, including "enlarge eyes", "thin face", "V face", "adjust chin" and "shorten face", "shrink nose", "brighten eyes", "whiten teeth", "remove eye bags", "remove wrinkles", "remove wrinkles", and other effects, which need to be integrated with **TEBeautyKit** to use. See [Integrating TEBeautyKit on Android](https://trtc.io/document/60196?platform=android&product=beautyar) and [Integrating TEBeautyKit on iOS](https://trtc.io/document/60194?platform=ios&product=beautyar).

- Advanced beauty function reference on **Android platform**ï¼[Android Tencent beauty effects SDK](https://trtc.io/document/45391)
- **iOSiOS** **platform**ï¼[iOS Tencent beauty effects SDK](https://trtc.io/document/45390)

## Contact us

If you have any suggestions or feedback, please contact `info_rtc@tencent.com`.


---
*Source: [https://trtc.io/document/64698](https://trtc.io/document/64698)*
