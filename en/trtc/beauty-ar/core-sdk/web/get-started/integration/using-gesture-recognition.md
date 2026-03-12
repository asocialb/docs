# Using Gesture Recognition

The Tencent Effect SDK supports Hand Gesture Recognize starting from v1.0.23.

## Enable Hand Gesture Module

Enable the hand gesture module when initializing the SDK.

```
import { ArSdk } from 'tencentcloud-webar';const sdk = new ArSdk( {   module: {     beautify: true, // Beauty, Makeup, Face Effects module     handGesture: true // Hand gesture recognition module   },   auth: { // The authentication information     licenseKey: 'xxxxxxxxx',     appId: 'xxx',     authFunc: authFunc   },   camera: { // Pass in the camera parameters        width: 1280,        height: 720   },   beautify: {      whiten: 0.1,      dermabrasion: 0.3,      eye: 0.2,      chin: 0,      lift: 0.1,      shave: 0.2   },   â¦â¦ // For more config settings, please refer to theãAPI Documentationã })
```

## Listen for Gesture Changes.

After enabling gesture recognition, trigger `handGesture` when a gesture change occurs.

```
// After enabling gesture recognition, it will trigger when a gesture change is detected.sdk.on('handGesture',(hands)=>{    console.log('handGesture', hands) // Refer to the following "Hand Object Structure" for hands.    â¦â¦ // Other business code, such as setting effects through the SDK's setEffect interface, etc.})
```

## Hand Object Structure

```
Hand: {    gesture: string // Gesture names, optional values include: None, Thumb_Up, Thumb_Down, Victory, Pointing_Up, Open_Palm, ILoveYou, Closed_Fist.    handedness: string // Recognized as left hand or right hand, values are Left, Right.}Hands: Array<Hand>
```

## List of supported Gestures.

| **Hand gesture value** | **Detail** |
| --- | --- |
| None | No valid gesture recognized |
| Thumb_Up | Thumbs up ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/91d39bd31b6d11f09240525400bf7822.png) |
| Thumb_Down | Thumb down ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a7d5509a1b6d11f0897952540099c741.png) |
| Victory | victory ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b5875ba41b6d11f091eb525400454e06.png) |
| Pointing_Up | pointing up ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c18c95fa1b6d11f091eb525400454e06.png) |
| Open_Palm | open palm ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cd0ae7aa1b6d11f091eb525400454e06.png) |
| ILoveYou | i love you ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/da52f8531b6d11f0abe05254005ef0f7.png) |
| Closed_Fist | close fist ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ece4471f1b6d11f09240525400bf7822.png) |


---
*Source: [https://trtc.io/document/69309](https://trtc.io/document/69309)*
