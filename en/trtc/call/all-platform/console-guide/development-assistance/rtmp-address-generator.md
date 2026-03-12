# RTMP Address Generator

The TRTC console supports generating streaming addresses for the [RTMP streaming room entry feature](https://www.tencentcloud.com/document/product/647/62716#3b96cc52-90be-46ee-aec0-218dcf302119), which is only suitable for the testing phase. For official online business, please deploy the address generation logic to backend services to avoid traffic theft caused by encryption key leak.

## Generating Stream Address

1. Go to the [Tencent RTC console](https://console.trtc.io), select **Development Tools >**[**RTMP Address Generator**](https://console.trtc.io/rtmptool) in the left sidebar, and check the **Generating Stream Address** module.
2. Click the dropdown box to select your created application (SDKAppID).
3. Fill in **Push Roomname (RoomID)** and **Push Username (UserID)**.
4. Click **Generate** to immediately generate the corresponding RTMP streaming address.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/25046b34d23e11ef97675254007c27c5.png)


---
*Source: [https://trtc.io/document/67774](https://trtc.io/document/67774)*
