# Text Watermark

## Description of the Feature

Conference (TUIRoomKit) supports the Text Watermark feature, allowing users to add custom text watermarks to conference to protect content copyright or convey specific information. Through the Text Watermark feature, users can display personal information, company names, or conference topics on the conference screen, enhancing content security and professionalism. This article will provide a detailed introduction to this feature and explain how to use it in the TUIRoomKit component.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e98a071a798011efa87a525400bdab9d.png)

## Feature Integration

### Enable Watermark

In TUIRoomKit, the Watermark feature is disabled by default. If you want to enable the Text Watermark feature, you can do so with the following code.

Android

iOS

```
ConferenceSession.sharedInstance().enableWaterMark();
```

```
ConferenceSession.sharedInstance.enableWaterMark()
```

> **Note:**Once enabled, the default watermark text will be `Your userId (Your userName)`.

### Set Watermark Text

In TUIRoomKit, you can customize the watermark text to meet your specific business needs. You can set your watermark text using the following code.

Android

iOS

```
ConferenceSession.sharedInstance().setWaterMarkText("yourWaterMarkText");  // Replace the string with the watermark content you need to set
```

```
ConferenceSession.sharedInstance.setWaterMarkText(waterMarkText: "yourWaterMarkText")  // Replace the string with the watermark content you need to set
```

## Feature customization

If the current UI does not meet your needs, you can modify the source code to achieve a satisfactory UI effect. To make it easier for you to customize the UI, an introduction to the text watermark-related files is provided here.

Android

iOS

You can modify the source code in the [Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/page/widget/WaterMark](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/page/widget/WaterMark) directory to achieve a satisfactory UI effect. To make it easier for you to customize the UI, an introduction to the text watermark-related files is provided here.

```
// File Location: Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/page/widget/WaterMarkWaterMark                           // Directory related to text watermark views    âââ TextWaterMarkView.java      // Text watermark view    âââ WaterMarkLineStyle.java     // Text watermark style
```

You can modify the source code in the [iOS/TUIRoomKit/Source/View/Page/Widget/WaterMark](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/iOS/TUIRoomKit/Source/View/Page/Widget/WaterMark) directory to achieve a satisfactory UI effect. To make it easier for you to customize the UI, an introduction to the text watermark-related files is provided here.

```
// File Location: iOS/TUIRoomKit/Source/View/Page/Widget/WaterMarkWaterMark                           // Directory related to text watermark views    âââ WaterMarkLayer.swift        // Text watermark view    âââ WaterMarkLineStyle.swift    // Text watermark style
```


---
*Source: [https://trtc.io/document/64693](https://trtc.io/document/64693)*
