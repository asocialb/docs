# Quick Integration

## Overview

TUIKaraoke is an open-source audio/video UI component that you can integrate into your project to bring online karaoke, seat management, gift giving/receiving, text chat, and other TRTC features to your application. TUIKaraoke requires only a few lines of code and also supports the Android platform. Its basic features are shown below:

> **Note**All TUIKit components are based on two basic PaaS services of Tencent Cloud, namely [TRTC](https://intl.cloud.tencent.com/document/product/647/35078) and [Chat](https://intl.cloud.tencent.com/document/product/1047/35448). When you activate TRTC, the Chat SDK Trial Edition (which supports up to 100 DAUs) will also be activated automatically. For Chat billing details, see [Pricing](https://intl.cloud.tencent.com/document/product/1047/34350).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/efa3bd2d38bd11edb1de525400c56988.png)

## Integration

### Step 1. Download and import the `TUIKaraoke` component

Go to [GitHub](https://github.com/tencentyun/TUIKaraoke), clone or download the code, copy the `Source`, `Resources`, and `TXAppBasic` folders and the `TUIKaraoke.podspec` file in the `iOS` directory to your project, and complete the following import operations:

- Add the following import commands to your `Podfile`:

```
pod 'TUIKaraoke', :path => "./", :subspecs => ["TRTC"]pod 'TXLiteAVSDK_TRTC'pod 'TXAppBasic', :path => "TXAppBasic/"
```

- Open Terminal and run the following installation command in the directory of the `Podfile`:

```
pod install
```

### Step 2. Configure permissions

Configure permission requests for your app in the `info.plist` file of your project. The SDKs need the following permissions (on iOS, the mic access must be requested at runtime):

```
 <key>NSMicrophoneUsageDescription</key>    <string>`TUIKaraoke` needs to access your mic.</string>
```

### Step 3. Initialize and log in to the component

For more information on relevant APIs, see [TRTCKaraoke (iOS)](https://intl.cloud.tencent.com/document/product/647/41942).

```
  // 1. Initialize  let karaokeRoom = TRTCKaraokeRoom.shared()  karaokeRoom.setDelegate(delegate: self)  // 2. Log in  karaokeRoom.login(SDKAppID: Int32(SDKAppID), UserId: UserId, UserSig: ProfileManager.shared.curUserSig()) { code, message in        if code == 0 {            // Logged in        }  }
```

**Parameter description:**

- **SDKAppID**: **TRTC application ID**. If you haven't activated TRTC, log in to the [TRTC console](https://console.tencentcloud.com/trtc/app), create a TRTC application, click **Application Info**, `SDKAppID` information is as shown in the figure below:
![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/415d3224b5d011eeb2a1525400170219.png)
- **SecretKey**: **TRTC application key**. Each secret key corresponds to an `SDKAppID`. You can view your applicationâs secret key on the [Application Management](https://console.tencentcloud.com/trtc/app) page of the TRTC console.
- **userId**: Current user ID, which is a custom string that can contain up to 32 bytes of letters and digits (special characters are not supported).
- **userSig**: The security protection signature calculated based on `SDKAppID`, `userId`, and `Secretkey`. You can click [here](https://console.trtc.io/usersig) to directly generate a debugging `userSig` online. For more information, see [UserSig](https://intl.cloud.tencent.com/document/product/647/35166).

### Step 4. Implement the online karaoke scenario

1. **The room owner creates a room through**[TUIKaraoke.createRoom](https://intl.cloud.tencent.com/document/product/647/41942).

```
int roomId = "Room ID";let param = RoomParam.init()param.roomName = "Room name";param.needRequest = false; // Whether permission is required for listeners to speak.param.seatCount = 8;       // Number of seats in the room. Set it to `8`.param.coverUrl = "URL of room cover image";karaokeRoom.createRoom(roomID: Int32(roomInfo.roomID), roomParam: param) { [weak self] (code, message) in guard let `self` = self else { return } if code == 0 {     // Room created successfully }}
```

2. **A listener enters the room through**[TUIKaraoke.enterRoom](https://intl.cloud.tencent.com/document/product/647/41942).

```
karaokeRoom.enterRoom(roomID: roomInfo.roomID) { [weak self] (code, message) in guard let `self` = self else { return } if code == 0 {     // Entered room successfully }}
```

3. **A listener turns their mic on through**[TUIKaraoke.enterSeat](https://intl.cloud.tencent.com/document/product/647/41942).

```
// 1. A listener calls an API to mic onint seatIndex = 1; karaokeRoom.enterSeat(seatIndex: seatIndex) { [weak self] (code, message) in guard let `self` = self else { return } if code == 0 {     // Mic turned on successfully }}// 2. The listener receives the `onSeatListChange` callback and refreshes the seat listfunc onSeatListChange(seatInfoList: [SeatInfo]) {}
```

> **Note** You can implement other seat management operations as instructed in [TRTCKaraoke (iOS)](https://intl.cloud.tencent.com/document/product/647/41942) or by referring to the [TUIKaraoke demo project](https://github.com/tencentyun/TUIKaraoke/).

4. **Play back songs and try out the karaoke scenario**
You can get the music ID and URL to play back a song. For more information, see [Music Playback APIs](https://www.tencentcloud.com/document/product/647/41942#music-playback-apis2).

```
// Play back the musickaraokeRoom.startPlayMusic(musicID: musicID, originalUrl: muscicLocalPath, accompanyUrl: accompanyLocalPath);// Stop the musickaraokeRoom.stopPlayMusic();
```

After completing the previous steps, you can implement the basic karaoke features. If your business needs more features such as chat and gift giving, you can integrate the following capabilities:

### Step 5. Add the text chat feature (optional)

If you want implement a text chat feature between speakers and listeners, implement message sending/receiving as follows:
For more information on relevant APIs, see [sendRoomTextMsg](https://intl.cloud.tencent.com/document/product/647/41942#sendroomtextmsg).

```
// Sender: Sends text chat messageskaraokeRoom.sendRoomTextMsg(message: message) { [weak self] (code, message) in    if code == 0 {        // Sent successfully    }}// Receiver: Listens for text chat messageskaraokeRoom.setDelegate(delegate: self)func onRecvRoomTextMsg(message: String, userInfo: UserInfo) {    debugPrint("Received a message from" + userInfo.userName + ": " + message)}
```

### Step 6. Add the gift giving feature (optional)

You can implement gift giving, receiving, and displaying as follows:

```
// Sender: Customize `IMCMD_GIFT` to distinguish between gift messageskaraokeRoom.sendRoomCustomMsg(cmd: kSendGiftCmd, message: message) { code, msg in    if (code == 0) {        // Sent successfully    }}// Receiver: Listens for gift messageskaraokeRoom.setDelegate(delegate: self)func onRecvRoomCustomMsg(cmd: String, message: String, userInfo: UserInfo) {    if cmd == kSendGiftCmd {        debugPrint("Received a gift from" + userInfo.userName + ": " + message)    }}
```

## FAQs

### Does the `TUIKaraoke` component support sound effect features such as voice change, tone change, and reverb?

Yes. For more information, see the [TUIKaraoke demo project](https://github.com/tencentyun/TUIKaraoke/blob/main/iOS/Source/ui/TRTCKTVViewController/SubViews/TRTCKaraokeSoundEffectAlert.swift).

> **Note** If you have any suggestions or feedback, please contact colleenyu@tencent.com.


---
*Source: [https://trtc.io/document/41940](https://trtc.io/document/41940)*
