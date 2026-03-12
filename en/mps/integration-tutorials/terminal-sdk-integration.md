# Terminal SDK integration

The terminal SDK is a suite of audio and video terminal product capabilities launched by Tencent Cloud. It encompasses three types of SDKs for video encoding, audio enhancement, and video enhancement. Tailored to meet diverse customer needs, it supports access from multiple terminals such as mobile, web, and PC.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/27a550c42ed011efa01d5254005235d8.png)

## Terminal Video Codec SDK

Tencent's Top Speed Codec (TSC) terminal video encoder is designed for scenarios requiring low computational power, low latency, and high-quality image on the terminal side. Compared with hardware encoding, its advantages include:

1. Stable, reliable, and quick to start.
2. At the same quality level, it saves bitrate, enhances transmission stability, reduces downlink distribution bandwidth, and saves on storage costs.
3. At the same bitrate, it improves image quality and enhances user experience.
4. A rich set of features meets diverse business needs, such as using Regions of Interest (ROI) encoding to improve the image quality in the face region and dynamically adjusting encoding configuration to adapt to network fluctuations.

For details, see [TSC Terminal Video Codec SDK](#294b81fb-0ba2-420c-99fc-40805708d0e2).

## Terminal Audio SDK

The client audio SDK provides audio encoding and enhancement capabilities. It achieves effects including adaptive noise suppression, acoustic echo cancellation, and automatic gain control, significantly improving audio quality by eliminating echo and noise.

For details, see [TSC Terminal Audio SDK](#47de165a-7753-4985-9415-539b9f772a74).

## Terminal Enhancement SDK

The client enhancement SDK, based on efficient image processing algorithms and AI model inference capabilities, achieves terminal video super-resolution, image quality enhancement, frame interpolation, and other features.

For details, see [TSC Terminal Enhancement SDK](#84157eba-650d-42ea-a51e-4d6541bab97a).

## TSC Terminal Video Codec SDK

### Product Overview

Compared with Video on Demand (VOD) and Cloud Streaming Services (CSS) encoding, terminal-side encoding requires different solutions.

| Encoding Mode | VOD | CSS | Terminal-side Codec |
| --- | --- | --- | --- |
| Typical Business | WeTV, video account, and other mainstream on-demand services | Video account live streaming, Tencent sports live streaming, and other mainstream live streaming services | VooV Meeting, WeChat video call, and 5G remote control services |
| Latency Requirements | Pursues an extreme compression rate, with no latency requirements. | Pursues a high compression rate, allowing second-level latency. | Pursues a high compression rate while requiring zero latency. |
| Real-Time Requirements | Pursues an extreme compression rate, with no real-time requirements. | Allows multi-frame average real-time under multi-threading. | Requires real-time encoding under single-threading. |
| Network Condition Constraints | Encoding process is unrelated to network status, with fixed encoding configuration. | Encoding process is unrelated to network status, with fixed encoding configuration. | Encoding process is strongly related to network status, requiring dynamic adjustment of encoding configuration based on network status. |
| Scenario Characteristics | 1 -> N, no interaction | 1 -> N, no interaction | N <-> N, strong interaction |
| Solution | Server-side encoding | Server-side encoding | Terminal-side encoding |

Tencent's Top Speed Codec (TSC) terminal video encoder is designed for scenarios requiring low computational power, low latency, and high-quality image on the terminal side. Compared with hardware encoding, its advantages include:

1. Stable, reliable, and quick to start.
2. At the same quality level, it saves bitrate, enhances transmission stability, reduces downlink distribution bandwidth, and saves on storage costs.
3. At the same bitrate, it improves image quality and enhances user experience.
4. A rich set of features meets diverse business needs, such as using Regions of Interest (ROI) encoding to improve the image quality in the face region and dynamically adjusting encoding configuration to adapt to network fluctuations.

### SDK Access Process

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0f29395e2d4711efb0275254006c0558.png)

1. **Evaluation and Trial: Customers provide system platform and demand information, and**[apply for product trial](https://console.tencentcloud.com/workorder/category)**.**
  - System platform: Android, iOS, Windows, macOS, etc.
  - Use cases: live streaming, VOD
  - Encoding specification: encoding format, resolution, frame rate, bitrate, latency requirements, etc.
  - Optimization objectives: bitrate savings, image quality enhancement, CPU savings, and respective assessment metrics (PSNR, SSIM, VMAF, etc)
2. **Development and Integration: Integrate the beta version of the SDK into the app, for performance evaluation and custom optimization.**
  - Based on customer effect evaluation results and specific business scenario needs, provide in-depth optimization support.
3. **Launch and Release: Apply for a license, integrate the official version of the SDK with license authorization, and test and launch the app.**
  - If the license is about to expire or has expired, you can apply for a license renewal.

### SDK Integration

The video codec SDK is implemented in C/C++/Assembly, providing a unified C interface for various system platforms.

#### Android

● Provides ARMv7 and ARMv8 version dynamic libraries, and the application is integrated via NDK.

● Provides Java interface encapsulation. The interface is basically consistent with Android's hardware encoding MediaCodec, facilitating parallel replacement of MediaCodec.

#### iOS

Provides ARMv8 and x86_64 version XCFramework.

#### macOS

Provides ARMv8 and x86_64 version framework.

#### Windows

Provides x86 and x86_64 version dynamic libraries.

#### Basic Video Encoding Process

![](https://staticintl.cloudcachetci.com/cms/backend-cms/faf17f932d4611efa4f552540077de32.png)

## TSC Terminal Audio SDK

### Product Overview

The client audio SDK provides audio encoding and enhancement capabilities, significantly improving audio quality by eliminating echo and noise.

Details of features for each edition are as follows:

| Feature Point | Standard Edition | Professional Edition | Premium Edition |
| --- | --- | --- | --- |
| Acoustic Echo Cancellation | Supported | Supported | Supported |
| Automatic Gain Control | Supported | Supported | Supported |
| Adaptive Noise Suppression | Supported | Supported | Supported |
| Echo Cancellation Music Mode | - | Supported | Supported |
| Volume Equalization | - | Supported | Supported |
| AI Intelligent Noise Reduction | - | Supported | Supported |
| Audio Encoding | - | - | Supported |
| AI Codec | - | - | Supported |

### Real-Time Communication Audio 3A

Audio 3A technology is a set of basic features in sound signal processing, commonly used in real-time communication systems such as video conferencing, calls, and live microphone connections, to ensure high-quality audio signal transmission, and provide better communication quality and audio listening experience. 3A stands for Adaptive Noise Suppression (ANS), Acoustic Echo Cancellation (AEC), and Automatic Gain Control (AGC).

![Real-time communication audio link](https://staticintl.cloudcachetci.com/cms/backend-cms/4ebbddc72d4711efa01d5254005235d8.png)

- ANS

The main feature of ANS is to eliminate the background noise components in the voice signal, reduce interference, and therefore improve speech intelligibility and perceptual quality. Based on the additive noise model assumption, the audio signal captured by the microphone can be considered as a superposition of the pure voice signal and noise interference. By tracking and estimating noise in non-voice segments of the audio, and then subtracting the noise component energy in the voice segments, a clearer voice signal can be obtained.

- AEC

AEC mainly addresses the echo problem in audio communication. During a call, the sound played by the speaker is directly captured by the microphone or captured after reflection, causing the remote user to hear their own voice. This can seriously affect call quality. AEC technology can process the near-end signal based on the remote reference signal, effectively eliminating or reducing this echo phenomenon, thereby enhancing the call experience.

- AGC

AGC is responsible for adjusting the volume during the transmission of audio signals. When the volume of the sound source is too low or too high, it can significantly affect the call experience. AGC can automatically detect the loudness of the audio stream and dynamically adjust the volume level to keep it within a comfortable range. AGC can alleviate the volume instability caused by factors such as differences in recording device collection, speaker volume, and distance.

### Use Cases

The SDK can be applied in the preprocessing of audio encoding in uplink push and the post-processing of audio decoding in downlink pull, to enhance sound quality. Currently, it supports Android, iOS, Windows, and macOS clients.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5a9a6e942d4711ef97da5254007d9c55.png)

- Online teaching scenario: Eliminating noise and echo enhances the clarity of sound during the teaching process.
- In-game voice scenario: Equalizing loud and soft voices improves player listening experience and game experience.
- Live streaming scenario: Anchor voice noise reduction and voice gain control improve the overall live streaming quality in voice chat, song rooms, and similar scenarios.

### SDK API Calling Process

![](https://staticintl.cloudcachetci.com/cms/backend-cms/75d842da2d4711efa01d5254005235d8.png)

## TSC Terminal Enhancement SDK

### Product Overview

The client enhancement SDK, based on efficient image processing algorithms and AI model inference capabilities, achieves terminal video super-resolution, image quality enhancement, frame interpolation, and other features.

Details of features for each edition are as follows:

| Feature Point | Standard Edition | Professional Edition | Premium Edition |
| --- | --- | --- | --- |
| Standard super-resolution | Supported | Supported | Supported |
| Standard super-resolution+Enhancement parameters(Contrast/Color/Brightness) | Supported | Supported | Supported |
| Professional super-resolution | - | Supported | Supported |
| AI image quality enhancement | - | Supported | Supported |
| AI frame interpolation enhancement | - | - | Supported |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/acf9c1a27a1b11ef852f52540075b605.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/13bdeda07a1c11efa87e52540055f650.png)

- The advantage of the Standard Edition is the performance, with our algorithms achieving good super-resolution effects at minimal time and energy consumption. It is compatible with almost all mobile phones of different performances.
- Additionally, the Standard Edition offers image enhancement features, which can adjust image brightness, color saturation, and contrast.
- The advantage of the Professional Edition is the effect. Using AI model inference, it can regenerate missing texture details in the original image, achieving the best image enhancement and super-resolution effects. The Professional Edition requires computational power of the device and is recommended for use on mid to high-end mobile phones.

### Performance

- Standard super-resolution

| System | Device Model | Device Configuration | Basic Super-Resolution Parameter | CPU(%) | Memory(MB) | Frame Rate | GPU(%) | Power Consumption(mAh) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Android | HUAWEI Mate50 (2022) | Chip: Snapdragon 8+ Gen1 CPU: 3.0 GHz GPU: Adreno 730 Battery: 4272.8 mAh | 720P - Off | 2.8 | 48 | 59.9 | 5 | 138.01 |
|  |  |  | 720P x 1.5 | 3 | 64 | 60.4 | 10 | 196.55 |
|  |  |  | 576P x 1.25 | 3 | 60.1 | 59.9 | 7 | / |
|  |  |  | 4K x 1.25 | 3 | 163.2 | 59.9 | 46.4 | / |
| Android | Sony Xperia 5 II (2020) | Chip: Snapdragon 865 CPU: 2.84 GHz GPU: Adreno 650 Battery: 3104 mAh | 720P - Off | 1 | 135.9 | 59.1 | 4 | 133.78 |
|  |  |  | 720P x 1.5 | 2 | 146.8 | 59.2 | 10 | 152.41 |
|  |  |  | 576P x 1.25 | 2 | 139.2 | 59.2 | 6 | / |
|  |  |  | 4K x 1.25 | 2 | 311.2 | 59.2 | 46.7 | / |
| Android | Xiaomi 6 (2017) | Chip: Snapdragon 835 CPU: 2.45 GHz GPU: Adreno 540 | 720P x 1.5 | 2.9 | 119 | 60 | 18.9 | / |
| Android | Redmi Note 4 (2016) | Chip: MediaTek MT6797 Helio X20 CPU: MT6797 2.0 GHz GPU: ARM Mali-T880 | 720P x 1.5 | 9.4 | 137.9 | 60.6 | 74.5 | / |
| Android | Honor 8 Youth Edition (2016, budget phone) | Chip: HiSilicon Kirin 655 CPU: HI6250 2.3 GHz GPU: ARM Mali-T830 | 720P - Off | 2 | 77 | 58.8 | Not supported | / |
|  |  |  | 720P x 1.5 | 2 | 83.4 | 58.1 | Not supported | / |
| iOS | iPhone 13 (2021) | CPU: 3.23 GHz GPU: quad-core Battery: 3065.65 mAh | 720P - Off | 5.9 | 54.4 | 59.5 | 15.9 | 64.99 |
|  |  |  | 720P x 1.5 | 6 | 63.8 | 59.5 | 24 | 88.29 |
|  |  |  | 576P x 1.25 | 4.7 | 57.3 | 59.5 | 18.9 | / |
|  |  |  | 4K x 1.25 | 9.2 | 162.2 | 59.5 | 60.6 | / |
| iOS | iPhone 6P (2014) | CPU: Apple A9 GPU: PowerVR GT7600 | 720P - Off | 13 | 40.5 | 59.5 | 22.8 | / |
|  |  |  | 720P x 1.5 | 18.8 | 49.4 | 59.6 | 50.2 | / |

- Professional super-resolution

| System | Device Model | Device Configuration | Professional Super-Resolution Parameter | CPU(%) | Memory(MB) | Frame Rate | GPU(%) | Power Consumption(mAh) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Android | HUAWEI Mate50 (2022) | Chip: Snapdragon 8+ Gen1 CPU: 3.0 GHz GPU: Adreno 730 Battery: 4272.8 mAh | 720P - Off | 3 | 66 | 60 | 3 | 138.01 |
|  |  |  | 720P x 1.5 | 13 | 123 | 48 | 10 | 342.9 |
|  |  |  | 576P x 1.25 | 13 | 105 | 60 | 7 | 333.13 |
|  |  |  | 540P x 2 | 13 | 105 | 60 | 11 | 322.73 |
| Android | Sony Xperia 5 II (2020) | Chip: Snapdragon 865 CPU: 2.84 GHz GPU: Adreno 650 Battery: 3104 mAh | 720P - Off | 1 | 142 | 59.1 | 3 | 133.78 |
|  |  |  | 720P x 1.5 | 13 | 196 | 39 | 8 | 294.06 |
|  |  |  | 576P x 1.25 | 13 | 148 | 58 | 8 | / |
|  |  |  | 540P x 2 | 13 | 159 | 40 | 7 | / |
| iOS | iPhone 13 (2021) | CPU: 3.23 GHz GPU: quad-core Battery: 3065.65 mAh | 720P - Off | 6 | 73 | 60 | 14 | 64.99 |
|  |  |  | 720P x 1.5 | 15 | 94 | 40 | 14 | / |
|  |  |  | 576P x 1.25 | 10 | 84 | 60 | 16 | / |
|  |  |  | 540P x 2 | 9 | 76 | 60 | 21 | / |

- AI image quality enhancement

| System | Device Model | Device Configuration | Professional Enhancement Resolution | CPU(%) | Memory(MB) | Frame Rate | GPU(%) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Android | HUAWEI Mate50 (2022) | Chip: Snapdragon 8+ Gen1 CPU: 3.0 GHz GPU: Adreno 730 Battery: 4272.8 mAh | 720P | 13 | 140 | 55 | 7 |
|  |  |  | 576P | 13 | 126 | 74 | 5 |
|  |  |  | 540P | 13 | 130 | 78 | 7 |
| Android | Sony Xperia 5 II (2020) | Chip: Snapdragon 865 CPU: 2.84 GHz GPU: Adreno 650 Battery: 3104 mAh | 720P | 13 | 184 | 41 | 5 |
|  |  |  | 576P | 13 | 174 | 59 | 5 |
|  |  |  | 540P | 13 | 142 | 43 | 4 |
| iOS | iPhone 13 (2021) | CPU: 3.23 GHz GPU: quad-core Battery: 3065.65 mAh | 720P | 17 | 91 | 40 | 11 |
|  |  |  | 576P | 12 | 70 | 60 | 11 |
|  |  |  | 540P | 9 | 68 | 60 | 11 |

### Use Cases

1. Enhance terminal players to improve video playback quality and smoothness.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/589e97802d5111ef9130525400bf8054.png)

2. Save costs by reducing the resolution and bitrate of video distribution, and then minimize experience loss through terminal playback enhancement.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3d8040652ed411ef97da5254007d9c55.png)

For example, in cloud gaming scenarios, the capability of real-time video super-resolution on the terminal can reduce the computational power of cloud rendering and encoding, save transmission bandwidth, and save costs. In the following example, a game scene transmitted from the cloud at 720P (5.6Mbps) is up-scaled to 1080P in real-time on the terminal. The viewing effect is close to a scene transmitted directly at 1080P (8.2Mbps) from the cloud, saving 30% of bandwidth.

### SDK Integration

#### Compatibility

- Android platform: Applicable to Android 5.0 and later (API 21, OpenGL ES 3.1).
- iOS platform: Applicable to iPhone 5s and later versions of devices, with the minimum system version being iOS 12.

#### Package Size

- Standard Edition: Android AAR is approximately 0.3 MB (arm64-v8a), and iOS Framework is approximately 0.4 MB.
- Professional Edition: Android AAR is approximately 2.1 MB (Single arm64-v8a architecture), and iOS Framework is approximately 1.9 MB.

#### Integration Guide

Please refer to the [Android](https://github.com/tencentyun/TSR/blob/main/Android%20Quick%20Start.md) and [iOS](https://github.com/tencentyun/TSR/blob/main/iOS%20Quick%20Start.md) integration guides.


---
*Source: [https://www.tencentcloud.com/document/product/1041/60831](https://www.tencentcloud.com/document/product/1041/60831)*
