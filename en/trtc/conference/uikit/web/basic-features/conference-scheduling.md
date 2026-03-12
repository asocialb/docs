# Conference Scheduling

## Function Introduction

TUIRoomKit introduces a new feature for schedule rooms, which allows users to reserve a room and schedule a meeting on their schedule.

> **Noteï¼****Since v2.5.0, TUIRoomKit supports the ability to**schedule**rooms, view room list, modify room information, etc. Integrate with the latest version of TUIRoomKit to experience the room**schedule**process.**

## How to schedule a room

1. On the TUIRoomKit Preview screen, click **Schedule** > Fill in the room reservation information and set up related privileges > Complete the settings and click **Schedule**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6f3a165c584b11ef8357525400bdab9d.png)

2. The schedule result will be synchronized with the schedule result in the list of **schedule rooms** on the right side of the preview page, and it supports operations such as **viewing details, modifying rooms, canceling rooms, copying invitation information**, and so on. In addition, you can click **join** to enter the schedule room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ac7bf642584c11efb927525400fdb830.png)

## Terms of preparation

Before you can use the room schedule feature provided by Tencent Cloud, you need to go to the console and enable the multiplayer conferencing [service for the application](https://trtc.io/document/59973?platform=web&product=conference). See Turning on the service for more information on how to do this. Next, you need to bring in the TUIRoomKit component, as described in [Quick Run-Through](https://trtc.io/document/60441?platform=web&product=conference).

### Schedule Room example run-through

> **Noteï¼**You need to introduce **PreConferenceView (the pre-conference preview component)** and**ConferenceMainView (the main body of the TUIRoomkit UI component)**. In the example, the **v-if** and **v-else** directives are used to control the showing and hiding of the two components, and you can also use route jumping to switch between the components.In the **PreConferenceView** component, you control whether the scheduled room features are shown or hidden by setting the value of the **enable-scheduled-conference** property. In addition, the component listens to the on-enter-room event, so when the user clicks into the room, the [join](https://trtc.io/document/54880#b08d0951-c1f4-4db4-a84d-8414b853d0f1)interface is invoked by triggering the **handleEnterRoom** method.In the **ConferenceMainView** component, the **on-destroy-room** event is listened to and the **onDestroyRoom** method is triggered when the room is destroyed.

Web

Electron

```
<template>  <PreConferenceView    v-if="isShowPreConferenceView"    :enable-scheduled-conference="true" // Setting whether to enable the schedule room feature display    @on-enter-room="handleEnterRoom"  ></PreConferenceView>  <ConferenceMainView    v-else    display-mode="permanent"    @on-destroy-room="onDestroyRoom"  ></ConferenceMainView></template><script setup lang="ts">import { ref } from 'vue'; // Note the package name, if you are using the vue2 version change the package name to @tencentcloud/roomkit-web-vue2.7import { PreConferenceView, conference, ConferenceMainView } from '@tencentcloud/roomkit-web-vue3';const isShowPreConferenceView = ref(true);const init = async () => {  conference.login({          sdkAppId: 0,  // Replace with your sdkAppId      userId: '',  // Replace with your userId      userSig: '',  // Replace with your userSig  });}init();async function handleEnterRoom(roomOption: Record<string, any>) {  const { roomId } = roomOption;  await conference.join(roomId, {    isOpenCamera: false,    isOpenMicrophone: false,  });  isShowPreConferenceView.value = false;}function onDestroyRoom() {  isShowPreConferenceView.value = true;  init();}</script>
```

```
<template>  <PreConferenceView    v-if="isShowPreConferenceView"    :enable-scheduled-conference="true" // Setting whether to enable the schedule room feature display    @on-enter-room="handleEnterRoom"  ></PreConferenceView>  <ConferenceMainView    v-else    display-mode="permanent"    @on-destroy-room="onDestroyRoom"  ></ConferenceMainView></template><script setup lang="ts">import { ref } from 'vue';  // Note the package name, if you are using the vue2 version change the package name to @tencentcloud/roomkit-electron-vue2.7import { PreConferenceView, conference, ConferenceMainView } from '@tencentcloud/roomkit-electron-vue3';const isShowPreConferenceView = ref(true);const init = async () => {  conference.login({          sdkAppId: 0,  // Replace with your sdkAppId      userId: '',  // Replace with your userId      userSig: '',  // Replace with your userSig  });}init();async function handleEnterRoom(roomOption: Record<string, any>) {  const { roomId } = roomOption;  await conference.join(roomId, {    isOpenCamera: false,    isOpenMicrophone: false,  });  isShowPreConferenceView.value = false;}function onDestroyRoom() {  isShowPreConferenceView.value = true;  init();}</script>
```

## Schedule Room Control

## Schedule Room

After clicking **Schedule**on the Preview page, the schedule Room Setting box pops up, and users can set the room information according to their needs, which can be set to include: **room name, room type, start time, room duration, time zone, attendees, security (access code), management (all mute, all stop videa)**, and so on.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3ec1ac91584e11efb36952540075b605.png)

> **Noteï¼****TUIRoomKit's** invite members list is derived from **IM friends,** so you need to use **IM to add friends**. You can replace the user data by **adding IM friends**. In this case, you need to use the **IM** [REST API](https://trtc.io/document/34620?product=chat&menulabel=serverapis)  to get the **IM** friend chain data by adding a friend relationship. If you are importing data from an attendee's address book or adding users, see [Adding Friends](https://trtc.io/document/34902?product=chat&menulabel=serverapis). If you want to remove an attendee, you can delete the buddy relationship in the IM relationship chain, see [Deleting Buddies](https://trtc.io/document/34905?product=chat&menulabel=serverapis).

### View Details

Users can click **View Details** to view the details of the corresponding schedule room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/545eb527585011efb66652540055f650.png)

### Modify room information

The room owner can modify the information of the schedule room, after modification, click **Schedule** to adjust the information of the currently schedule room to the modified room information.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/72c3d1dd584f11efb927525400fdb830.png)

### Invitation to the room

Users can click

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7119856c585811ef81cf525400d5f8ef.png)

Invite to bring up the meeting information invitation box, and

**Copy the conference number and link**

to the pasteboard to share with other users by clicking Copy Meeting Number & Link.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f23d150e585011ef8357525400bdab9d.png)

## Caveat

- Room reservations cannot start earlier than the current time, but there is no limit to the number of days in advance.
- If you want to schedule rooms for different dates/times at the same time, just select the times and submit them at the same time.
- Once a room is schedule, the room number will be reserved for 6 hours from the start time of the schedule, if the room is not occupied, during which time you can return to the room at any time.
- The room number and reservation information will be available once the room is successfully schedule.

## Communication and feedback

If you have any needs or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/63275](https://trtc.io/document/63275)*
