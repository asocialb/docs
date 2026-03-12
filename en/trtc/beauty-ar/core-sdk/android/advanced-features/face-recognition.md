# Face Recognition

Detects when a face is partially captured or concealed or when there are multiple faces; recognizes 256 facial keypoints.

## Index Image for 256 Facial Keypoints

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d9b5b0d1f54811ed95155254007e6a5b.png)

## Integration guide for Android

For directions on how to integrate the Beauty AR SDK for Android, see the integration guide for [Integrating SDK  (Android)](https://www.tencentcloud.com/document/product/1143/60195).

## Registering an Xmagic listener

This API is used to configure the callback of facial keypoints and other data.

**Version 2.6.0** and earlier versions use the following method.

```
void setYTDataListener(XmagicApi.XmagicYTDataListener ytDataListener)public interface XmagicYTDataListener {    void onYTDataUpdate(String data)}
```

**Version 3.0.0**uses the following method.

```
void setAIDataListener(XmagicApi.OnAIDataListener aiDataListener)public interface OnAIDataListener {    void onFaceDataUpdated(List<TEFaceData> faceDataList);    void onHandDataUpdated(List<TEHandData> handDataList);    void onBodyDataUpdated(List<TEBodyData> bodyDataList);    void onAIDataUpdated(String data); //This method is a new method added in version 3.0.0, and the data structure is consistent with the XmagicYTDataListener interface used in previous versions.}
```

`onYTDataUpdate and onAIDataUpdated` returns a JSON string structure that contains the information of up to 5 faces:

```
{ "face_info":[{  "trace_id":5,  "face_256_point":[    180.0,    112.2,    ...  ],  "face_256_visible":[    0.85,    ...  ],  "out_of_screen":true,  "left_eye_high_vis_ratio:1.0,  "right_eye_high_vis_ratio":1.0,  "left_eyebrow_high_vis_ratio":1.0,  "right_eyebrow_high_vis_ratio":1.0,  "mouth_high_vis_ratio":1.0 }, ... ]}
```

### Fields

| Field | Type | Value Range | Description |
| --- | --- | --- | --- |
| trace_id | int | [1,INF) | The face ID. If the faces obtained continuously from a video stream have the same face ID, they belong to the same person. |
| face_256_point | float | [0,screenWidth] or [0,screenHeight] | 512 values in total for 256 facial keypoints. (0,0) is the top-left corner of the screen. |
| face_256_visible | float | [0,1] | Visibility of the 256 facial keypoints. |
| out_of_screen | bool | true/false | Whether the face is outside of the screen view. |
| left_eye_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the left eye. |
| right_eye_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the right eye. |
| left_eyebrow_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the left eyebrow. |
| right_eyebrow_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the right eyebrow. |
| mouth_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the mouth. |

#### Parameters

| Parameters | Description |
| --- | --- |
| XmagicApi.XmagicYTDataListener ytDataListener | Callback function implementation class. |


---
*Source: [https://trtc.io/document/60310](https://trtc.io/document/60310)*
