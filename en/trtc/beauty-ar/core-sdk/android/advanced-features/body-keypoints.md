# Body Keypoints

## Overview

This capability processes the OpenGL textures of the camera and outputs 3D body data. You can pass the data to Unity to drive your model or use the data to implement other features.

## Integration (Android)

Follow the directions in [Integrating Tencent Effect SDK](https://www.tencentcloud.com/document/product/1143/60195) to integrate the Tencent Effect SDK.

### API calls

1. Enable the feature (XmagicApi.java).

```
public void setFeatureEnableDisable(String featureName, boolean enable);
```

Set `featureName` to `XmagicConstant.FeatureName.BODY_3D_POINT`.

2. Configure the data callback (XmagicApi.java).

**Version 2.6.0** and earlier versions use the following method.

```
void setYTDataListener(XmagicApi.XmagicYTDataListener ytDataListener)public interface XmagicYTDataListener { void onYTDataUpdate(String data)}
```

`onYTDataUpdate` returns a JSON string. You can find an example below.

  - `face_info` is facial data, which is not used by this capability.
  - For the meanings of fields in `body_3d_info`, see below.

**Version 3.0.0**uses the following method.

```
void setAIDataListener(XmagicApi.OnAIDataListener aiDataListener)public interface OnAIDataListener {    void onFaceDataUpdated(List<TEFaceData> faceDataList);    void onHandDataUpdated(List<TEHandData> handDataList);    void onBodyDataUpdated(List<TEBodyData> bodyDataList);    void onAIDataUpdated(String data); //This method is a new method added in version 3.0.0, and the data structure is consistent with the XmagicYTDataListener interface used in previous versions.}
```

`onAIDataUpdated` returns a JSON string. You can find an example below.

  - `face_info` is facial data, which is not used by this capability.
  - For the meanings of fields in `body_3d_info`, see below.

## Body Keypoints and Descriptions

- SMPL keypoints.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6cce97fd865e11eda61e525400463ef7.png)

- SMPL-X hand keypoints

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/601c5987866411eda151525400c56988.png)

Here is an example of the JSON string output by the SDK:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6cd1e5fe865e11eda61e525400463ef7.png)

The following section details the fields in `body_3d_info`:

- `imageWidth` and `imageHeight`: The width and height of images sent to the SDK.
- `items`: An array. Currently, it contains only one element.
- `index`: A reserved field. You can ignore it.
- `pose`:
  - Location [0,2]. The 3D location (xyz) of the body root bone with the camera at the center.
  - Location [3,12]. The body shape. It includes 10 floating numbers, which are based on 10 meshes of SMPL.
  - Location [13]. The focal length, which is 5000.
  - Location [14,29]. The OpenGL projection matrix in a 3D space, which is generated based on the focal length. A 4 x 4 projection matrix is calculated as follows in the algorithm:

```
matrix={    2 * focal_length / img_wid, 0, 0, 0,    0, 2 * focal_length / img_hei, 0,0,    0,0, (zf + zn) / (zn - zf), -1,    0, 0, (2.0f * zf * zn) / (zn - zf), 0};}
```

  - Location [30,33]. Whether the left toe, left heel, right toe, and right heel are on the ground.
- position_x,position_y,position_zï¼
  - Location [0,23]. 2D body keypoints (figure 1 above). The value of `position_z` for all 2D keypoints is `0`.
  - Location [24,47]. 3D body keypoints (figure 1 above).
- rotation
  - Location [0,23]. The body bone rotation quaternions (wxyz).
  - Location [25,54]. The hand bone rotation quaternions (wxyz). There are 15 quaternions for each hand.

## Bone Names

| No. | Bone Name | Bone Name 2 |
| --- | --- | --- |
| 01234567891011121314151617181920212223 | "pelvis","left_hip","right_hip","spine1","left_knee","right_knee","spine2","left_ankle","right_ankle","spine3","left_foot","right_foot","neck","left_collar","right_collar","head","left_shoulder","right_shoulder","left_elbow","right_elbow","left_wrist","right_wrist","left_hand""right_hand" | "Hips""LeftUpLeg""RightUpLeg""Spine""LeftLeg""RightLeg""Spine1""LeftFoot""RightFoot""Spine2""""""Neck""LeftShoulder""RightShoulder""Head""LeftArm""RightArm""LeftForeArm""RightForeArm""LeftHand""RightHand""""" |
| 252627282930313233343536373839 | "left_index1""left_index2""left_index3""left_middle1""left_middle2""left_middle3""left_pinky1""left_pinky2""left_pinky3""left_ring1""left_ring2""left_ring3""left_thumb1""left_thumb2""left_thumb3 | IndexFinger1_LIndexFinger2_LIndexFinger3_LMiddleFinger1_LMiddleFinger2_LMiddleFinger3_LPinkyFinger1_LPinkyFinger2_LPinkyFinger3_LRingFinger1_LRingFinger2_LRingFinger3_LThumbFinger1_LThumbFinger2_LThumbFinger3_L |
| 404142434445464748495051525354 | "right_index1""right_index2""right_index3""right_middle1""right_middle2""right_middle3""right_pinky1""right_pinky2""right_pinky3""right_ring1""right_ring2""right_ring3""right_thumb1""right_thumb2""right_thumb3" | IndexFinger1_RIndexFinger2_RIndexFinger3_RMiddleFinger1_RMiddleFinger2_RMiddleFinger3_RPinkyFinger1_RPinkyFinger2_RPinkyFinger3_RRingFinger1_RRingFinger2_RRingFinger3_RThumbFinger1_RThumbFinger2_RThumbFinger3_R |


---
*Source: [https://trtc.io/document/74184](https://trtc.io/document/74184)*
