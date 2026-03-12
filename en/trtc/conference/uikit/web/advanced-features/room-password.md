# Room Password

## Description of the Feature

TUIRoomKit supports room encryption. You can use TUIRoomKit to schedule or create a password-protected room. **If the UI Interaction of TUIRoomKit does not meet your product requirements, you can use TUIRoomEngineSDK to custom the Room Password interaction features. For details, please refer to**[**Key Code**](https://www.tencentcloud.com/document/product/647/64893#eae2186f-0d0c-4a8b-acf5-497953e42854).

## **Use instructions**

### Creating password room

After successfully integrating TUIRoomKit and logging in, you can create a password room. For creating a password room on different platforms, please refer to:

Android

iOS

Web

Please ensure that you have successfully [connected to TUIRoomKit](https://www.tencentcloud.com/document/product/647/54843#087dff27-11d0-42ec-bb14-202b4b333452) and [logged in](https://www.tencentcloud.com/document/product/647/54843#05771e5e-e6ca-48f7-b99d-40b9a7c99cc4) successfully, then you can create a password-protected room by calling the following example code:

```
ConferenceDefine.StartConferenceParams params = new ConferenceDefine.StartConferenceParams("222222"); // Please replace "222222" with your own defined room number
params.passWord = "123456"; // Please replace "123456" with your set password (pure digits, up to 6 characters)
Intent intent = new Intent(this, ConferenceMainActivity.class);
intent.putExtra(KEY_START_CONFERENCE_PARAMS, params);
startActivity(intent);
```

> **Note:**The room can be entered only with a password of pure digits, up to 6 characters.

Please ensure you have successfully [connected to TUIRoomKit](https://www.tencentcloud.com/document/product/647/54842#.E6.AD.A5.E9.AA.A4.E4.B8.80.EF.BC.9A.E5.BC.80.E9.80.9A.E6.9C.8D.E5.8A.A1) and [logged in](https://www.tencentcloud.com/document/product/647/54842#.E6.AD.A5.E9.AA.A4.E5.9B.9B.EF.BC.9A.E7.99.BB.E5.BD.95-TUI-.E7.BB.84.E4.BB.B6), then you can create a password-protected room by using the following sample code:

Swift

OC

```
import TUIRoomKitfunc quickStartConference() {    let vc = ConferenceMainViewController()    let params = StartConferenceParams(roomId: "111111")  // Please replace "111111" with your defined room number    params.password = "123456"  // Please replace "123456" with your defined room password    vc.setStartConferenceParams(params: params)    navigationController?.pushViewController(vc, animated: true) }
```

```
#import "TUIRoomKit/TUIRoomKit-Swift.h"- (void)quickStartConference {    ConferenceMainViewController * vc = [[ConferenceMainViewController alloc]init];    StartConferenceParams * params = [[StartConferenceParams alloc]                                       initWithRoomId: @"111111" // Please replace "111111" with your custom room number                                    isOpenMicrophone:YES                                        isOpenCamera:NO                                       isOpenSpeaker:YES                       isMicrophoneDisableForAllUser:NO                           isCameraDisableForAllUser:NO                                       isSeatEnabled:NO                                                name:@"YourRoomName"                                            password:@"123456"]; // Please replace "123456" with your custom room password    [vc setStartConferenceParamsWithParams:params];    [self.navigationController pushViewController:vc animated:YES];}
```

> **Note:**The room can be entered only with a password of pure digits, up to 6 characters.

Please ensure you have successfully [connected to TUIRoomKit](https://www.tencentcloud.com/document/product/647/54845#.E6.AD.A5.E9.AA.A4.E4.B8.89.EF.BC.9A.E4.B8.8B.E8.BD.BD.E5.B9.B6.E5.BC.95.E7.94.A8-TUIRoom-.E7.BB.84.E4.BB.B6) and [logged in](https://www.tencentcloud.com/document/product/647/54845#a97bf81c-3780-41c6-bfbe-eab34c0d9909), then you can create a password-protected room by using the following sample code:

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-web-vue2.7import { conference } from '@tencentcloud/roomkit-web-vue3';conference.start('123456', { // Please replace "123456" with your own defined room number  roomName: 'TestRoom',  isSeatEnabled: false,  isOpenCamera: false,  isOpenMicrophone: false,  password: '123456', // Please replace "123456" with your set password (pure digits, up to 6 characters)});
```

> **Note:**The room can be entered only with a password of pure digits, up to 6 characters.

### Schedule password-protected room

To schedule a password-protected room, please refer to [Schedule conference (Android&iOS&Flutter)](https://www.tencentcloud.com/document/product/647/63139) or [Schedule conference (Web&Electron)](https://www.tencentcloud.com/document/product/647/63275)instructions to open the scheduling interface and set the password. The interaction scheme is as follows:

- **Invited Members Enter Room**: They can enter the room via the meeting list or room number, without needing a password.
- **Non-invited Members Enter Room**: They can only enter the room via the room number and must enter the correct password.

| Android & iOS |  |  |
| --- | --- | --- |
| Schedule password room | Non-invited members enter the room with password | Invited members can directly enter the room |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/617e6b538acb11ef80ff525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fae594457c0511ef82535254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/218308797c0611ef852f52540075b605.png) |

| Web |  |  |
| --- | --- | --- |
| Creating password room | Non-invited members enter the room with password | Invited members can directly enter the room |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d3da96007c8311efa87e52540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c0ec8a347c7611ef80ff525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c3fc838f7c7611ef82535254002693fd.png) |

> **Noteï¼**If the scheduled conference UI does not meet your needs, you need to implement the feature according to your own UI interaction design. For related API calls, please refer to [Key Code](https://www.tencentcloud.com/document/product/647/64893#eae2186f-0d0c-4a8b-acf5-497953e42854).

## Feature customization

If the current UI does not meet your needs, you can achieve the desired UI effect by modifying the source code. For different platforms, please refer to:

Android

iOS

Web

Electron

You can achieve the desired UI effect by modifying the source code under [Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/schedule/scheduleinfo](https://github.com/Tencent-RTC/TUIRoomKit/blob/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/schedule/scheduleinfo/EnterConferencePasswordView.java) directory. To facilitate your UI customization, here we introduce the files related to room password.

```
// Location: Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/schedule/scheduleinfo  âââ EnterConferencePasswordView.java  // Password Input Popup Interface  âââ SetConferenceEncryptView.java     // Schedule Conference Password Setting Interface
```

You can modify the source code in the [iOS/TUIRoomKit/Source/View](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/iOS/TUIRoomKit/Source/View) directory to achieve the desired UI Effect. To facilitate easier customization, this document provides an introduction to the room password files.

```
view         âââ ConferencePasswordView.swift           // Password Input Popup Interface  âââ ScheduleConferenceDataHelper.swift     // Schedule Conference Password Popup Style Interface
```

You can modify the source code in the following directories to achieve the desired UI Effect. To facilitate easier customization, this document provides an introduction to the room password files.

```
// Location: TUIRoomKit/Web/roomkit/vue3/src/TUIRoom/components/PreRoom         âââ PasswordDialog.vue  // Password Input Popup Interface  ScheduleConference/ScheduleConferencePanel  âââ ScheduleConferencePanelPC.vue     // Schedule Conference Password Setting Interface Web  âââ ScheduleConferencePanelH5.vue     // Schedule Conference Password Setting Interface H5
```

You can modify the source code in the following directories to achieve the desired UI Effect. To facilitate easier customization, this document provides an introduction to the room password files.

```
// Location: TUIRoomKit/Electron/roomkit/vue3/src/TUIRoom/components/PreRoom         âââ PasswordDialog.vue  // Password input popup interface  ScheduleConference/ScheduleConferencePanel  âââ ScheduleConferencePanelPC.vue     // Schedule Conference Password Setting Interface Web  âââ ScheduleConferencePanelH5.vue     // Schedule Conference Password Setting Interface H5
```

> **Note:**If you have any requirements or feedback, you can contact: info_rtc@tencent.com.

## Key code

- To create a password room, please refer to different platforms:

Android

iOS

Web/ Electron

```
public abstract void createRoom(TUIRoomDefine.RoomInfo roomInfo, TUIRoomDefine.ActionCallback callback);
```

You can set the room password by configuring the password field of the roomInfo parameter. For more details, please refer to [createRoom](https://www.tencentcloud.com/document/product/647/54864#911bbef4c82371be741fa4c6c0693907).

Below is the sample code:

```
TUIRoomDefine.RoomInfo roomInfo = new TUIRoomDefine.RoomInfo();roomInfo.roomId = "222222";  // Please replace "222222" with your own defined room numberroomInfo.password = "123456" // Please replace "123456" with your set password (pure digits, up to 6 characters)TUIRoomEngine.sharedInstance().createRoom(roomInfo, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Callback for successful room creation    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Callback for failed room creation    }});
```

```
- (void)createRoom:(TUIRoomInfo *)roomInfo onSuccess:(TUISuccessBlock)onSuccess onError:(TUIErrorBlock)onError NS_SWIFT_NAME(createRoom(_:onSuccess:onError:));
```

You can set the room password by configuring the password field of the roomInfo parameter. For more details, please refer to [createRoom](https://www.tencentcloud.com/document/product/647/54855#4d0e7ddf563f6245a1d812b0690a5eea).

Below is the sample code:

Swift

OC

```
import RTCRoomEnginefunc createRoom() {    let roomInfo = TUIRoomInfo()    roomInfo.roomId = "111111"     // Please replace "111111" with your custom room number    roomInfo.password = "123456"   // Please replace "123456" with your custom room password    TUIRoomEngine.sharedInstance().createRoom(roomInfo) {        print("CreateRoom success")    } onError: { code, message in        print("CreateRoom error, code:\\(code), message:\\(message)")    }}
```

```
#import "RTCRoomEngine/TUIRoomDefine.h"#import "RTCRoomEngine/TUIRoomEngine.h"- (void)createRoom {    TUIRoomInfo * roomInfo = [[TUIRoomInfo alloc] init];    roomInfo.roomId = @"111111";     // Please replace "111111" with your custom room number    roomInfo.password = @"123456";   // Please replace "123456" with your custom room password    [[TUIRoomEngine sharedInstance] createRoom:roomInfo onSuccess:^{        NSLog(@"CreateRoom success");    } onError:^(TUIError code, NSString * _Nonnull message) {        NSLog(@"CreateRoom error, code:%ld, message:%@", (long)code, message);    }];}
```

You can set the room password by configuring the password field. For more details, please refer to [start](https://www.tencentcloud.com/document/product/647/54880#b0bf2a3b-428c-474f-9a0e-271c7c3b6bfd).

Below is the sample code:

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-web-vue2.7import { conference } from '@tencentcloud/roomkit-web-vue3';conference.start('123456', { // Please replace "123456" with your own defined room number  roomName: 'TestRoom',  isSeatEnabled: false,  isOpenCamera: false,  isOpenMicrophone: false,  password: '123456', // Please replace "123456" with your set password (pure digits, up to 6 characters)});
```

- To schdedule a password room, please refer to different platforms:

Android

iOS

```
public abstract void scheduleConference(ConferenceInfo conferenceInfo, TUIRoomDefine.ActionCallback callback);
```

You can set the room password by configuring the password field of the conferenceInfo parameter. For more details, please refer to [scheduleConference](https://www.tencentcloud.com/document/product/647/64482#fe650b8a01a3be98f309a9d6770f6b31). Example code is as follows:

```
TUIConferenceListManager manager = TUIRoomEngine.sharedInstance().getExtension(CONFERENCE_LIST_MANAGER);TUIConferenceListManager.ConferenceInfo conferenceInfo = new TUIConferenceListManager.ConferenceInfo();conferenceInfo.basicRoomInfo.roomId = "222222";   // Please replace "222222" with your own defined room numberconferenceInfo.basicRoomInfo.password = "123456"; // Please replace "123456" with your set password (pure digits, up to 6 characters)manager.scheduleConference(conferenceInfo, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Successful callback for booking a room    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed callback for booking a room    }});
```

```
- (void)scheduleConference:(TUIConferenceInfo *)conferenceInfo onSuccess:(TUISuccessBlock)onSuccess onError:(TUIErrorBlock)onError NS_SWIFT_NAME(scheduleConference(_:onSuccess:onError:));
```

You can set the room password by configuring the password field of the conferenceInfo parameter. For more details, please refer to [scheduleConference](https://www.tencentcloud.com/document/product/647/64476#26abfce04dc32efb2e1dd56154d3c1ed). Example code is as follows:

Swift

OC

```
import RTCRoomEnginefunc scheduleConference() {    let manager = TUIRoomEngine.sharedInstance().getExtension(extensionType: .conferenceListManager) as? TUIConferenceListManager    let conferenceInfo = TUIConferenceInfo()    conferenceInfo.basicRoomInfo.roomId = "111111"    // Please replace "111111" with your custom room number    conferenceInfo.basicRoomInfo.password = "123456"  // Please replace "123456" with your custom room password    manager?.scheduleConference(conferenceInfo, onSuccess: {        print("ScheduleConference success")    }, onError: { code, message in        print("ScheduleConference failed, code:\\(code), message:\\(message)")    })}
```

```
#import "RTCRoomEngine/TUIRoomEngine.h"#import "RTCRoomEngine/TUIConferenceListManager.h"- (void)scheduleConference {    TUIConferenceListManager * manager = [[TUIRoomEngine sharedInstance] getExtension: TUIExtensionTypeConferenceListManager];    TUIConferenceInfo * conferenceInfo = [[TUIConferenceInfo alloc] init];    conferenceInfo.basicRoomInfo.roomId = @"111111";    // Please replace "111111" with your custom room number    conferenceInfo.basicRoomInfo.password = @"123456";  // Please replace "123456" with your custom room password    [manager scheduleConference:conferenceInfo onSuccess:^{        NSLog(@"ScheduleConference success");    } onError:^(TUIError code, NSString * _Nonnull message) {        NSLog(@"ScheduleConference failed, code:%ld, message:%@", (long)code, message);    }];}
```

- Enter password room

Android

iOS

Web/Electron

```
public abstract void enterRoom(String roomId, TUIRoomDefine.RoomType roomType, TUIRoomDefine.EnterRoomOptions options, TUIRoomDefine.GetRoomInfoCallback callback);
```

You can set the room password by setting the password field of the options parameter. For detailed API information, please refer to [enterRoom](https://www.tencentcloud.com/document/product/647/54864#7d887cfe0029482a872a8bef2c90b29a). Sample code is as follows:

```
String roomId = "222222";    // Please replace "222222" with the room number you are joiningTUIRoomDefine.EnterRoomOptions options = new TUIRoomDefine.EnterRoomOptions();options.password = "123456"; // Please replace "123456" with your set password (pure digits, up to 6 characters)TUIRoomEngine.sharedInstance().enterRoom(roomId, TUIRoomDefine.RoomType.CONFERENCE, options, new TUIRoomDefine.GetRoomInfoCallback() {    @Override    public void onSuccess(TUIRoomDefine.RoomInfo engineRoomInfo) {        // Successful room entry callback    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed room entry callback        if (error == TUICommonDefine.Error.WRONG_PASSWORD) {            // Wrong password, handle the incorrect entry password business here.        }    }});
```

```
- (void)enterRoom:(NSString *)roomId roomType:(TUIRoomType)roomType options:(TUIEnterRoomOptions *)options onSuccess:(TUIRoomInfoBlock)onSuccess onError:(TUIErrorBlock)onError NS_SWIFT_NAME(enterRoom(_:roomType:options:onSuccess:onError:));
```

You can set the room password by configuring the password field in the options parameter. For more details, please refer to [enterRoom](https://www.tencentcloud.com/document/product/647/54855#3e5f7fdc1c30135d17bd4464609d99e4). Sample code is as follows:

Swift

OC

```
import RTCRoomEnginefunc enterRoom() {    let roomId = "111111"        // Please replace "111111" with your custom room number    let options = TUIEnterRoomOptions()    options.password = "123456"  // Please replace "123456" with your custom room password    TUIRoomEngine.sharedInstance().enterRoom(roomId, roomType: .conference, options: options) { roomInfo in        print("EnterRoom success")    } onError: { code, message in        print("EnterRoom failed, code:\\(code), message:\\(message)")    }}
```

```
#import "RTCRoomEngine/TUIRoomEngine.h"- (void)enterRoom {    NSString * roomId = @"111111";   // Please replace "111111" with your custom room number    TUIEnterRoomOptions * options = [[TUIEnterRoomOptions alloc] init];    options.password = @"123456";    // Please replace "123456" with your custom room password    [[TUIRoomEngine sharedInstance] enterRoom:roomId roomType:TUIRoomTypeConference options:options onSuccess:^(TUIRoomInfo * _Nullable roomInfo) {        NSLog(@"EnterRoom success");    } onError:^(TUIError code, NSString * _Nonnull message) {        NSLog(@"EnterRoom failed, code:%ld, message:%@", (long)code, message);    }];}
```

You can enter the room by setting the password field. For more details, please refer to [join](https://www.tencentcloud.com/document/product/647/54880#b08d0951-c1f4-4db4-a84d-8414b853d0f1).

Below is the sample code:

```
// Note the package name. If you are using the vue2 version, please change the package name to @tencentcloud/roomkit-web-vue2.7import { conference } from '@tencentcloud/roomkit-web-vue3';conference.join('123456', { // Please replace "123456" with the room number you are joining  isOpenCamera: false,  isOpenMicrophone: false,  password: 'Set your room password', // Please replace "123456" with your set password (pure digits, up to 6 characters)});
```


---
*Source: [https://trtc.io/document/64893](https://trtc.io/document/64893)*
