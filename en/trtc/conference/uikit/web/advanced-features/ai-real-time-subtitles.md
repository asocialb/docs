# AI Real-Time Subtitles

## Function Introduction

After accessing TUIRoomKit, you can turn on the AI real-time subtitle function by clicking âAI Assistantâ in the bottom bar:

- **AI real-time subtitles:**Display the discussion during the meeting in the form of subtitles.
- **AI real-time meeting recording:**Record in writing what was discussed during the course of the meeting.

> **Noteï¼**[TUIRoomKit monthly subscription](https://www.tencentcloud.com/document/product/647/59973) is required to use this feature.In addition to the normal call charges ([audio and video hourly billing instructions](https://www.tencentcloud.com/document/product/647/42734)); this feature will incur additional AI recognition charges for speech-to-text, please refer to the [AI recognition billing instructions for details](https://www.tencentcloud.com/document/product/647/67832).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cc736bbef12e11f09d62525400ecee81.png)

## Function Access

### Step 1: Start Local Backend Service

> **Noteï¼**Open AI transcription need to use the user's cloud id and key, high sensitivity, so do not integrate this interface in the client, you need to add your own business background StartAITranscription related code, here to Nodejs service as an example.

Open Nodejs backend service, the client listens for the user to enter the room and opens the AI transcription task via http request, sample code: [click to download](https://web.sdk.qcloud.com/trtc/AITask/server.zip).

```
require('dotenv').config();const express = require('express');const tencentcloud = require('tencentcloud-sdk-nodejs-trtc');const cors = require('cors')const TrtcClient = tencentcloud.trtc.v20190722.Client;// Get the Tencent Cloud account SecretId and SecretKey from the environment variable// You need to pass the Tencent Cloud account SecretId and SecretKey into the entry parameter, and you also need to pay attention to the confidentiality of the key pair here.// Code leaks can lead to SecretId and SecretKey leaks and threaten the security of all resources under the account.// The following code example is for reference only, a more secure way of using the key is recommended, see: https://cloud.tencent.com/document/product/1278/85305// The key can be obtained by going to the official console at https://console.cloud.tencent.com/cam/capi.const secretId = process.env.TENCENT_SECRET_ID || '';const secretKey = process.env.TENCENT_SECRET_KEY || '';const region = process.env.TENCENT_REGION || '';const clientConfig = {  credential: {    secretId: secretId,    secretKey: secretKey,  },  region: region,  profile: {    httpProfile: {      endpoint: 'trtc.tencentcloudapi.com',    },  },};const client = new TrtcClient(clientConfig);const app = express();app.use(express.json());app.use(cors());app.post('/start', async (req, res) => {  const { SdkAppId, RoomId, RoomIdType = 1, UserId, UserSig } = req.body;  const params = {    SdkAppId: SdkAppId,    RoomId: RoomId,    RoomIdType: RoomIdType,    TranscriptionParams: {      UserId: UserId,      UserSig: UserSig,    },  };  try {    const data = await client.StartAITranscription(params);    console.log('success',data)    res.status(200).json(data);  } catch (err) {    console.error('error', err);    res.status(500).json({ error: err.message });  }});app.post('/stop', async (req, res) => {  const { TaskId } = req.body;  try {    const data = await client.StopAITranscription({ TaskId: TaskId });    res.status(200).json(data);  } catch (err) {    console.error('error', err);    res.status(500).json({ error: err.message });  }});const port = process.env.PORT || 3000;app.listen(port, () => {  console.log(`Server is running on port ${port}`);});
```

### Step 2: Roomkit Enables AI Assistants

> **Noteï¼**Roomkit only processes data for AI captioning/meeting recording, the actual ASR is turned on when the client user enters the room, here you can adjust the timing according to your business needs.

```
<template>  <conference-main-view display-mode="permanent"></conference-main-view></template><script setup lang="ts">import { roomService } from '@tencentcloud/roomkit-web-vue3';// Called before the conference-main-view component is onmounted.roomService.setComponentConfig({ AIControl: { visible: true } });</script>
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f709ab3c0aeb11f0b3015254001c06ec.png)

### Step 3: Roomkit listens for the user to enter the room and calls the node service to enable AI transcription.

```
<template>  <conference-main-view display-mode="permanent"></conference-main-view></template><script setup lang="ts">import { conference } from '@tencentcloud/roomkit-web-vue3';import { startAITranscription } from '../http';const handleAITask = (data: {roomId: string}) => {  const { roomId } = data;  startAITranscription({    RoomId: roomId,    UserId: 'robot', // A robot user is required here, in the case of robot, this should not be the same as the userId of the user in the room, it is recommended to use robot.    UserSig: 'xxx', // The userSig of the robot    SdkAppId: sdkAppId,    RoomIdType: 1, // Room type is string room  });};conference.on(RoomEvent.ROOM_JOIN, handleAITask);conference.on(RoomEvent.ROOM_START, handleAITask);onUnmounted(() => {  conference.off(RoomEvent.ROOM_JOIN, handleAITask);  conference.off(RoomEvent.ROOM_START, handleAITask);});</script>
```

```
// http.tsimport axios from 'axios';const http = axios.create({  baseURL: 'http://localhost:3000', // Your Node.js service address.  timeout: 10000, // Request timeout});interface TranscriptionParams {    SdkAppId: number;    RoomId: string;    RoomIdType?: number;    UserId: string;    UserSig: string;  }  interface StopParams {    TaskId: string;  }// Start the AI transcription taskexport function startAITranscription(params: TranscriptionParams) {  return http.post('/start', params);}// Stop the AI transcription taskexport function stopAITranscription(params: StopParams) {  return http.post('/stop', params);}
```

> **Noteï¼**If you have any needs or feedback on the access and use process, you can contact info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/68951](https://trtc.io/document/68951)*
