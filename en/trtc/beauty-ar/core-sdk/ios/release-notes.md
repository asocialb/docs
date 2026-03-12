# Release Notes

### Version 4.1.0.7 @2025.12.15

- Added Chroma Key Segmentation capability.
- Enhanced Body Beautification: Improved accuracy and stability of human body recognition.
- Upgraded libpag library.
- Fixed known bugs.

### Version 4.0.0.13 @2025.10.22

- Add the "skin highlight" property.
- Add smile detection capability.
- Beauty effect optimization.
- Fix known bugs.
- Optimize package resource file size.

### Version 3.9.3.8 @2025.07.16

- Added multiple skin smoothing effects in EffectMode_Pro mode.
- Integrated GAN skin beautification functionality in EffectMode_Pro mode.
- Added new material resources.
- Optimized the beautification effects.
- Fixed known bugs.

### Version 3.9.2.6 @2025.04.24

- Added automatic noise reduction capability in backlit conditions.
- Performance optimization.
- Fix known bugs.

### Version 3.9.1.2 @2025.02.21

- Introduced the "Forehead 2" capability.
- Fix known bugs.

### Version 3.9.0.3 @2024.11.19

- Added "Light Makeup" capability. For details, see [Light Makeup Usage Guide](https://www.tencentcloud.com/document/product/1143/66152).
- Added Eye Corner Adjustment feature; Whitening added "Brightening" effect; Whitening supports Custom Filter Path. For details, see [Effect Parameters](https://www.tencentcloud.com/document/product/1143/60207).
- High-Performance Mode adjusted to EffectMode. For details, see EffectMode (High-Performance Mode) Usage Guide.
- Known bugs have been rectified.

### Version 3.8.0.9 @2024.10.16

Fix known bugs.

### Version 3.8.0.5 @2024.08.29

- Add beauty/makeup/body attributes: brightness adjustment, eye position, double eyelids, eye bags, slim arms.
- Optimize the issue of makeup display on obstructions when applying makeup.
- Optimize the makeup wear-off issue on low-end devices.
- Add new beauty and sticker materials.
- Update the PrivacyInfo privacy policy content.
- Fix the SDK upload failure to the App Store.
- Fix known bugs.
- Performance optimization.

### Version 3.7.0.1 @2024.05.30

- Added skin tanning capabilities.
- Added hair dyeing feature for single-point makeup.
- Added natural face slimming feature in the high-performance mode.
- Added new 2D animation materials.
- Added the  `getDeviceLevel`  API to obtain device level.
- Optimized the forehead (hairline) effect.
- Optimized the beauty effect panel.

### Version 3.6.0.3 @2024.04.11

Update PrivacyInfoã

### Version 3.6.0.1 @2024.03.21

- Add "Denoise" feature.
- Add "camera move" capability and user experience.
- Add PrivacyInfo.
- Fix known bugs.

### Version 3.5.0.2 @2024.01.29

- Added color temperature and hue-conditioning capabilities.
- Added intelligent beauty features and gender detection capabilities, providing softened beauty makeup effects for males and babies.
- The SDK supports pag file settings when self-definition segmentation and green screen are used.
- Optimized background segmentation capabilities.
- Optimized skin smoothing and brightening effects, minimizing impacts on non-skin areas.
- Optimized face detection sensitivity.
- Optimized the interface for setting beauty effects and added a new setEffect interface.
- Bug fix: the clarity range from -100 to 100 before has been changed to 0 to 100. Breast enhancement has been optimized as chest adjustment, with range changed from 0 to 100 to -100 to 100.
- Added 2D/3D sticker materials and full-face makeup style materials.
- Upgraded the libpag library to 4.3.33.
- Revamped the demo style, and added the fastly accessible TEBeautyKit library.

### Version 3.3.0.1 @2023.10.30

- Added new features such as colored contact lenses, nose bridge width, and nose root.
- The compilation of libpag.framework and TECodec.framework has introduced the simulator x86_64 architecture.
- The demo has introduced a new texture cropping feature.

### Version 3.2.0.2 @2023.10.11

Fixed known bugs.

### Version 3.2.0.1 @2023.09.20

- Optimized background blur.
- Added sharpness effect feature.
- A new level of skin whitening, whitening 2 and whitening 3 have been added.
- Optimized performance.
- Solved the head-lowering issue during avatar body drive.
- Added a feature only for skin whitening.
- Upgraded the libpag version.
- Optimized the logic of voice drive.
- Addressed issues of jagged edges and unclear peripheries in skin smoothing.

### Version 3.1.0.1 @2023.08.02

- Newly added single-point makeup: eye shadow, eyeliner, eyelashes, and eyebrows, available in the S series package.
- Added gesture recognition capability, which can recognize 14 gestures and hand positions. Please refer to the [gesture document for details](https://www.tencentcloud.com/document/product/1143/56174?lang=en&pg=).
- The beauty feature has added a high-performance mode, which is suitable for long-term use on low-end devices. Please refer to the iOS API documentation.
- Avatar has added new animation materials.
- Avatar supports custom backgrounds.
- Fixed known bugs.

### Version 3.0.1.5 @2023.07.18

- Added material overlay capability, please refer to the iOS API documentation for details.
- Fixed several known bugs.

### Version 3.0.0.4 @2023.06.06

Modify the naming of beauty parameters in XmagicConstant.hã

### Version 3.0.0.3 @2023.05.31

New interfaceï¼

ï¼1ï¼Added an interface for setting the path of the beauty modelã

ï¼2ï¼Added interface for obtaining avatar animation configurationã

ï¼3ï¼Added setting avatar animation interfaceã

### Version 3.0.0.1 @2023.5.12

- New beauty features added: eye width, eye height, eyebrow angle, eyebrow distance, eyebrow height, eyebrow length, eyebrow thickness, eyebrow peak, lip width, lip position, and smile lips.
- A breast enhancement feature has been added to the body beauty options.
- Experience issues and bugs related to background separation have been fixed.
- The 3D engine of the SDK has been upgraded, please verify if previous dynamic sticker effects are working properly after the SDK upgrade. If not, please contact us.
- API changes:

Delete the onYTDataEvent callback and move the data previously called back in onYTDataEvent to onAIEvent, which will now be accessed using event[@"ai_info"]. The content of the callback remains unchanged.

- Framework changes include renaming TEFFmpeg.framework to TECodec.framework.
- Material changes:

(1) Deleted the following materials: Duck cap, Flower fairy, Glasses 2, Magic bow. These materials are not compatible with the current version of the SDK.

(2) Upgraded the following materials: Helmet, Paws, Lamb, Glasses. If you have used any of these materials before, please contact us to obtain the upgraded files.

### Version 2.6.0.1 @2023.03.01

- Added green screen functionality to background segmentation.
- Revamped the beauty demo.
- Added chin slimming feature to beauty effect.
- Improved the blush effect by applying it only to the skin area.
- Optimized Avatar interface and demo.
- Updated Avatar assets.
- Fixed several bugs.

### Version 2.5.1.249 @2022.12.12

- Updated the `ffmpeg` and `Auth` dynamic libraries.
- Added the enhanced beautification mode.
- Added full-body avatars, body mirroring, cool boy, and speech mirroring.

### Version 2.5.0.250 @2022.10.31

- Added support for muting audio effects.
- Introduced Avatar features.
- Added support for compilation on an emulator.
- Fixed known memory leak issues.

### Version 2.4.2.114 @2022.07.19

- Fixed some effect errors.
- Reduced the package size.

### Version 2.4.2 @ 2022.07.07

- Optimized the face detection algorithm to fix unstable recognition and tracking performance in some scenarios.
- Added support for dynamically downloading effect resources for the demo.
- Fixed the failure to use custom filter images.
- Updated the API documentation.


---
*Source: [https://trtc.io/document/60204](https://trtc.io/document/60204)*
