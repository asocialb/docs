# Virtual Background

TUICallKit has launched a new feature for virtual backgrounds, allowing users to set a blurry or image background during video calls. This hides the real calling environment, protects privacy, and makes the call more interesting. Next, this article will detail how to use this feature in the TUICallKit component.

## Integration effect

The display effect of the TUICallKit component after integrating the virtual background feature is as follows:

| Original Camera | Blurry Background Effect | Image Background Effect |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/05d6304918ed11efac7f5254007bbd8c.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/06ae308e18ed11ef88ad5254002977b6.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/063e4ee718ed11ef8bfe5254002fd0a8.png) |

## Preparation Requirements

1. Before using the Virtual Background feature provided by Tencent Cloud, you need to visit the Console to activate Audio and Video Services for your application and purchase the `Group Call` package. For specific steps, please see [Activate Service.](https://www.tencentcloud.com/document/product/647/59832#)
2. Download the [Virtual Background Model](https://www.tencentcloud.com/document/product/647/60490#8e1c4015-d0f9-4b57-8f81-4c6c23820ca7) file, unzip it, and copy the `LiteavSegmentModel.zip` file to the `assets` directory of your project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/150f3ff6008611ef9125525400275b90.png)

3. In the `tuicallkit-kt` directory of the project, find the `build.gradle` file and replace the `TRTC SDK` version with the Professional Version.

```
api "com.tencent.liteav:LiteAVSDK_Professional:11.8.0.14176"
```

> **Note:**There is a corresponding relationship between the version of the TRTC SDK and the model file, please ensure the version number matches the model, see below: [Model File Matching with SDK](https://www.tencentcloud.com/document/product/647/60490#8e1c4015-d0f9-4b57-8f81-4c6c23820ca7).

## Enable Blurry Background

TUICallKit's UI design supports setting a blurry background. By calling the following interface, you can display a feature button for the blurry background on the UI. Clicking the button will directly enable the blurry background feature.

```
TUICallKit.createInstance(getApplicationContext()).enableVirtualBackground(true);
```

## Setting Image Background (Optional)

Implementing the image background requires users to save the image locally. After saving, call the following interface for setting (currently, only images with a local path are supported,  images of uri are not supported yet).

```
TUICallEngine.createInstance(context).setVirtualBackground("imagePath", null)
```

## FAQs

### Enabling blurry background has no response or is delayed?

- Ensure you have purchased the audio and video call `Group Call` package, see [Activate Service.](https://www.tencentcloud.com/document/product/647/59832#)
- Ensure the model file is downloaded to local.

If a model file is not added to the local path, when enabling the blurry background feature, the SDK will then download the model file. Under normal network conditions, the download takes 1~3s; the poorer the network, the longer it will take.

- Check if the model file and SDK are a match.

### Matching model files with SDK?

TUICallKit is based on the Chat SDK and TRTC SDK for audio and video call scenarios. Virtual background is a feature provided by TRTC SDK. There is a matching relationship between the virtual background model file and the TRTC SDK version. If they do not match, enabling the blurry background might be ineffective. The relationship between the model file and TRTC SDK is as below:

| SDK Version | Virtual background model file Download address |
| --- | --- |
| com.tencent.liteav:LiteAVSDK_Professional:11.7.0.12001 | [segmention_1.0](https://liteav.sdk.qcloud.com/sdkres/feature/virtual_background/model/versions/1.0/segmention_model_1.0.zip) |
| com.tencent.liteav:LiteAVSDK_Professional:11.8.0.14176 | [segmention_2.0](https://liteav.sdk.qcloud.com/sdkres/feature/virtual_background/model/versions/2.0/person_segmention_2.0.zip) |


---
*Source: [https://trtc.io/document/60490](https://trtc.io/document/60490)*
