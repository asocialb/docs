# Floating Window

## Feature Introduction

TUIRoomKit supports the floating window feature, allowing users to create a freely draggable floating window for displaying and managing the TUIRoomKit video conferencing interface. This makes it easier for users to handle other tasks while participating in a video conference.

## ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/56e36f3d128b11efa09b525400762795.png)

## Use Instructions

1. During the meeting, click on the **More** > **Floating** button in the bottom toolbar to enable the floating window.
2. When enabling the "Floating Window" feature for the first time, Android devices will be redirected to the relevant system settings page. You need to enable the appropriate permissions for the app, such as **Floating Window**, **Background Pop-up Interface**, **Allow display over other Apps** etc. The names of the relevant system settings may vary slightly between different device models.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc250e5e128b11efa09b525400762795.png)

3. After enabling the relevant system permissions, Android devices support both in-app and out-of-app floating windows, while iOS devices only support in-app floating windows.
4. In the floating window state, click on the floating window to return to the conference.

## Key code

You can enable/disable the Floating Window feature using the following methods, refer to different platforms:

Android

You can delete the code [Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/main/bottomnavigationbar/BottomViewModel.java](https://github.com/Tencent-RTC/TUIRoomKit/blob/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/main/bottomnavigationbar/BottomViewModel.java) in the createItemList function `addFloatItemIfNeeded(itemDataList)` to disable the Floating Window.

```
private List<BottomItemData> createItemList() {
    List<BottomItemData> itemDataList = new ArrayList<>();
    addUserListItemIfNeeded(itemDataList);
    addMicItemIfNeeded(itemDataList);
    addCameraItemIfNeeded(itemDataList);
    addRaiseHandItemIfNeeded(itemDataList);
    addApplyListItemIfNeeded(itemDataList);
    addScreenItemIfNeeded(itemDataList);
    addChatItemIfNeeded(itemDataList);
    addInviteItemIfNeeded(itemDataList);    // Delete this line of code to disable the Floating Window feature 
    // addFloatItemIfNeeded(itemDataList);
    addSettingsItemIfNeeded(itemDataList);
    return itemDataList;
}
```

> **Note:**If you have any requirements or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/60484](https://trtc.io/document/60484)*
