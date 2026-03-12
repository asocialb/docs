# Release Notes

### Version 4.1.0.13 @2025.12.22

- Added Chroma Key Segmentation capability.
- Enhanced Body Beautification: Improved accuracy and stability of human body recognition.
- Upgraded libpag library: From version 4.4.24-noffavc to 4.4.35-noffavc.
- Fixed known bugs.

### Version 4.0.0.13 @2025.10.22

- Add the "skin highlight" property.
- Add smile detection capability.
- Beauty effect optimization.
- Fix known bugs.
- Optimize package resource file size.

### Version 3.9.3.12 @2025.07.16

- Added multiple skin smoothing effects in EffectMode_Pro mode.
- Integrated GAN skin beautification functionality in EffectMode_Pro mode.
- Added new material resources.
- Optimized the beautification effects.
- Fixed known bugs.

### Version 3.9.2.7 @2025.04.24

- Added automatic noise reduction capability in backlit conditions.
- Updated and upgraded the libpag library, with compatibility for Android 15 16k pagesize.
- Performance optimization.
- Fixed known bugs.

### Version 3.9.1.6 @2025.04.02

- Introduced the "Forehead 2" capability.
- Fix known bugs.

### Version 3.9.0.8 @2024.11.19

- Added "Light Makeup" capability. For details, see Light Makeup Usage Guide.
- Added Eye Corner Adjustment feature; Whitening added "Brightening" effect; Whitening supports Custom Filter Path. For details, see [Effect Parameters](https://www.tencentcloud.com/document/product/1143/60207).
- High-Performance Mode adjusted to EffectMode. For details, see EffectMode (High-Performance Mode) Usage Guide.
- Known bugs have been rectified.

### Version 3.8.0.15 @2024.10.15

Fix known bugs.

### Version 3.8.0.9 @2024.08.29

- Added beauty/beauty makeup/body attributes: brightness adjustment, eye position, double eyelid, under-eye bags, slim arms.
- Optimized the issue of makeup display on occluded objects.
- Optimized makeup smudging issue on low-end devices.
- Added new makeup and sticker materials.
- Fix known bugs.
- Performance optimization.

### Version 3.7.0.5 @2024.05.29

- Added skin tanning capabilities.
- Added hair dyeing feature for single-point makeup.
- Added natural face slimming feature in the high-performance mode.
- Added new 2D animation materials.
- Added the  `getDeviceLevel`  API to obtain device level.
- Optimized the forehead (hairline) effect.
- Optimized the beauty effect panel.

### Version 3.6.0.4 @2024.03.21

- Add "Denoise" feature.
- Add "camera move" capability and user experience.
- Fix known bugs.

### Version 3.5.0.5 @2024.01.29

- Added color temperature and hue-conditioning capabilities.
- Added intelligent beauty features and gender detection capabilities, providing softened beauty makeup effects for males and babies.
- The SDK supports pag file settings when self-definition segmentation and green screen are used.
- Optimized background segmentation capabilities.
- Optimized skin smoothing and brightening effects, minimizing impacts on non-skin areas.
- Optimized face detection sensitivity.
- Optimized the interface for setting beauty effects and added a new setEffect interface.
- Bug fix: the clarity range from -100 to 100 before has been changed to 0 to 100. Breast enhancement has been optimized as chest adjustment, with range changed from 0 to 100 to -100 to 100.
- Added 2D/3D sticker materials and full-face makeup style materials.
- Upgraded the libpag library to 4.3.33. Clients can replace it with their own pag version as needed.
- Revamped the demo style, and added the fastly accessible TEBeautyKit library.

### Version 3.3.0.2 @2023.10.30

- Added new features such as colored contact lenses, nose bridge width, and nose root.
- The demo has introduced a new texture cropping feature.
- The demo facial keypoints uses different colors to draw keypoints based on their visibility.

### Version 3.2.0.5 @2023.09.20

- Added sharpness effect feature.
- A new level of skin whitening, whitening 3, has been added.
- Added exclusive ability for skin brightening.
- Optimized the background blurring effect.
- Optimized the makeup logic of a single area.
- Solved the head-lowering issue during avatar body drive.
- Optimized the logic of voice drive.
- Upgraded the lilbpag version.
- Optimized aliasing rules to avoid the occurrence of class `a.a.a.a.a`.
- Addressed issues of jagged edges and unclear peripheries in skin smoothing.

### Version 3.1.0.2 @2023.08.02

- Newly added single-point makeup: eye shadow, eyeliner, eyelashes, and eyebrows, available in the S series package.
- Added gesture recognition capability, which can recognize 14 gestures and hand positions. Please refer to the [gesture document](https://www.tencentcloud.com/document/product/1143/56174) for details.
- The beauty feature has added a high-performance mode, which is suitable for long-term use on low-end devices. Please refer to the Android API documentation.
- Avatar has added new animation materials.
- Avatar supports custom backgrounds.
- The beauty feature's custom background segmentation and green screen segmentation have added image orientation detection.
- Fixed known bugs.

### Version 3.0.1.2 @2023.07.18

- Added material overlay capability, please refer to the Android API documentation for details.
- Fixed several known bugs.

### Version 3.0.0.13 @2023.05.12

- New beauty features added, including eye width, eye height, eyebrow angle, eyebrow distance, eyebrow height, eyebrow length, eyebrow thickness, eyebrow peak, lip width, lip position, and smile lips.
- New breast enlargement feature added to the body-shaping tool.
- so Library changes include renaming libteffmpeg.so to libtecodec.so.
- Fixed user experience issues and bugs related to background segmentation.
- Upgraded the 3D engine in the SDK. Please verify that any existing animated stickers are functioning correctly after upgrading. If you experience any issues, please contact us.
- API changes:

Removed the setYTDataListener interface and moved the data previously called back in onYTDataUpdate to AIDataListener as onAIDataUpdated. The content of the callback remains unchanged.

- Material changes:

(1) Deleted the following materials: Duck cap, Flower fairy, Glasses 2, Magic bow. These materials are not compatible with the current version of the SDK.

(2) Upgraded the following materials: Helmet, Paws, Lamb, Glasses. If you have used any of these materials before, please contact us to obtain the upgraded files.

### Version 2.6.0.112 @2023.03.01

- Added the green screen keying feature.
- Redesigned the beauty filter demo.
- Added the chin tucking feature.
- Optimized the rosy skin filter to add a filter to only the skin color area.
- Added support for dynamically downloading the `benchmark` folder in `assets`.
- Upgraded the PAG version to v4.0.
- Optimized the avatar APIs and demo.
- Updated the avatar materials.
- Fixed several bugs.

### Version 2.5.1.135 @2022.12.08

- Optimized 52 facial expressions.
- Added the 3D body keypoint detection capability.
- Added the enhanced beautification mode.
- Optimized the avatar image loading mode.
- Optimized the speech mirroring performance.
- Optimized custom keying.

### Version 2.5.0.207 @2022.10.25

- Introduced avatar features.
- Added support for muting and unmuting audio effects.
- Added a callback API for `updateProperties`.
- Added the `setBundleToLightEngine` API, which is used to dynamically add AI model-based resources.
- Added support for code obfuscation.
- Deleted the `LogUtils` class in the SDK.

### Version 2.4.2.324 @2022.09.13

Fixed the issue where the blush, contour, and lipstick effects fail to work in some cases.

### Version 2.4.2.322 @2022.07.19

Fixed some effect errors.

### Version 2.4.2.317 @2022.07.13

Deleted `beacon.aar`. If you update from a version earlier than v2.4.2.317, the new version will not include `beacon.aar`.

### Version 2.4.2 @ 2022.07.07

- Optimized the face detection algorithm to fix unstable recognition and tracking performance in some scenarios.
- Added support for verification of the parameters of the `updateProperty` API. For details about the parameter requirements, see updateProperty.
- Fixed the issue where the value returned by `isDeviceSupport` is sometimes inaccurate.
- Added `beacon.aar` to the `libs` directory of the SDK. You need to copy it to your project. If your project already has a beacon, it may cause a conflict. To avoid this, do not import the AAR file.
- Added support for Unity. For details, see the `Unity` folder in the SDK package.


---
*Source: [https://trtc.io/document/60203](https://trtc.io/document/60203)*
