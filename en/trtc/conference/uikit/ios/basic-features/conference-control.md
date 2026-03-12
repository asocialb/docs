# Conference Control

This document will provide a detailed introduction to the pre-conference control, in-conference control, and other aspects of `TUIRoomKit` to help you better master the conference control features of `TUIRoomKit`. Through this document, you will be able to fully utilize the functions of `TUIRoomKit` to achieve high-quality audio and video conferences.

Upon creating and entering a room via `Android&iOS&Flutter` platforms, the room host or an administrator can access the participant management options by clicking the member button on the bottom toolbar. This action will prompt a member list to appear at the bottom of the screen. Within this list, the host or administrator can select any regular member to enforce actions such as **muting a user's messages** or **setting them as an administrator**, among other conference control operations. In addition, the host or administrator has the ability to perform conference-wide control actions, such as**muting audio for all participants** in the room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/265f34920c4311ef8d94525400f2c344.png)

## Pre-conference Control

Before entering the conference, you can use the pre-conference control features of `TUIRoomKit` to set the relevant parameters of the conference in advance, ensuring the smooth progress of the conference.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/30fb0eb80c4311efb74e525400b3b5af.png)

iOS (Swift)

Androidï¼Javaï¼

Flutter (Dart)

```
// CreateRoomViewController for your own ViewControllerclass CreateConferenceViewController: UIViewController {    private var conferenceViewController: ConferenceMainViewController?    func quickStartConferenceAction() {      conferenceViewController = ConferenceMainViewController()      // Implement the pre-conference control features by setting the parameters in ConferenceParams.      let params = ConferenceParams()      params.isMuteMicrophone = false      params.isOpenCamera = false      params.isSoundOnSpeaker = true      params.name = "your conference name"      params.enableMicrophoneForAllUser = true      params.enableCameraForAllUser = true      params.enableMessageForAllUser = true      params.enableSeatControl = false      conferenceViewController?.setConferenceParams(params: params)      conferenceViewController?.setConferenceObserver(observer: self)      // After completing the settings, call the interface to start or join a conference. Here, we take starting a conference as an example.      conferenceViewController?.quickStartConference(conferenceId: "your conferenceId")    }}extension CreateConferenceViewController: ConferenceObserver {    func onConferenceStarted(conferenceId: String, error: ConferenceError) {      if error == .success, let vc = conferenceViewController {        navigationController?.pushViewController(vc, animated: true)      }      conferenceViewController = nil    }}
```

```
public class ConferenceOwnerActivity extends AppCompatActivity {    private static final String TAG = "ConferenceOwnerActivity";
    private ConferenceObserver mConferenceObserver;    @Override    protected void onCreate(Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        setContentView(R.layout.app_activity_conference_main);
        // Implement the pre-conference control features by setting the parameters in ConferenceParams.        ConferenceParams params = new ConferenceParams();        params.setMuteMicrophone(false);        params.setOpenCamera(false);        params.setSoundOnSpeaker(true);
        params.setName("your conference name");        params.setEnableMicrophoneForAllUser(true);        params.setEnableCameraForAllUser(true);        params.setEnableMessageForAllUser(true);        params.setEnableSeatControl(false);        ConferenceMainFragment fragment = new ConferenceMainFragment();        fragment.setConferenceParams(params);        setConferenceObserver(fragment);        fragment.quickStartConference("your conferenceId");  // After completing the settings, call the interface to start or join a conference. Here, we take starting a conference as an example.    }

    private void setConferenceObserver(ConferenceMainFragment fragment) {        mConferenceObserver = new ConferenceObserver() {            @Override            public void onConferenceStarted(String conferenceId, ConferenceError error) {                super.onConferenceStarted(conferenceId, error);                if (error != ConferenceError.SUCCESS) {
                    Log.e(TAG, "Error : " + error);
                    return;
                }
                FragmentManager manager = getSupportFragmentManager();
                FragmentTransaction transaction = manager.beginTransaction();
                transaction.add(R.id.conference_owner_container, fragment);
                transaction.commitAllowingStateLoss();            }        };        fragment.setConferenceObserver(mConferenceObserver);    }}
```

```
var conferenceSession = ConferenceSession.newInstance("your conferenceId")        ..isMuteMicrophone = false      ..isOpenCamera = false      ..isSoundOnSpeaker = true      ..name = "your conference name"      ..enableMicrophoneForAllUser = true      ..enableCameraForAllUser = true      ..enableMessageForAllUser = true      ..enableSeatControl = false                ..onActionSuccess = () {    // Successful operation callback, you can navigate to the conference page here.        Navigator.push(          context,          MaterialPageRoute(          builder: (context) => ConferenceMainPage(),          ),        );      }                      ..onActionError = (ConferenceError error, String message) {}  // Failure operation callback      ..quickStart();         // After completing the settings, call the interface to start or join a conference. Here, we take starting a conference as an example.
```

Here is a detailed introduction to the parameters in the above code.

| Parameter | Type | Meaning |
| --- | --- | --- |
| isMuteMicrophone | bool | Whether to mute the microphone (default is false) |
| isOpenCamera | bool | Whether to open the camera (default is false) |
| isSoundOnSpeaker | bool | Whether to turn on the speakers (default is true) |
| name | String | conference name (default is your conferenceId) |
| enableMicrophoneForAllUser | bool | Whether to enable microphone permission for all members (default is true) |
| enableCameraForAllUser | bool | Whether to enable camera permission for all members (default is true) |
| enableMessageForAllUser | bool | Whether to enable message permission for all members (default is true) |
| enableSeatControl | bool | Whether to enable on-stage speaking mode (default is false) |

> **Note:**The above is an introduction to the parameters for creating and joining a conference in the aforementioned code. You can create either a free-speech room or a stage-speech room based on the different values passed to the isSeatEnable parameter. The control features available in these two types of rooms will also vary:**Free-Speech Room**: Regular users can freely speak and have the liberty to turn their microphones and cameras on or off.**Stage-Speech Room**: Only users on stage can freely turn their microphones and cameras on or off. Regular audience members can apply to become stage users by raising their hand.

## In-conference Control

### Managing a Free-Speech Room

When the room type is a free-speech room, the host or administrator can manage all members in the meeting through **Members** > Member List.

- The host or administrator can select any member for individual control: **unmute/mute**, **turn video on/off**, **set as an administrator**, **transfer host**, **disable/enable messaging**, or **kick out from the room**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/be8d6a2a0c4511ef89045254000ded98.png)

- The host or administrator can perform group control actions for all members within the room: **mute/unmute all** or **disable/enable video for all**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e85d99770c4511ef8d94525400f2c344.png)

### Managing a Stage-Speech Room

When the room type is a stage-speech room, the host or administrator can manage the members in the meeting through **Members** > Member List, as well as manage the on-stage status of selected members in the Stage Management section.

- The host or administrator can select any regular member for individual control: in addition to the actions available in the free-speech room, such as **unmute/mute**, **turn video on/off**, **disable/enable messaging**, **set as an administrator**, **transfer host,** and **kick out from the room**, stage-speech rooms also offer unique actions such as **inviting on stage** and **asking to leave the stage**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4995001d0c4611ef9ef35254002977b6.png)

- The host or administrator can manage the status of members who have applied to be on stage within the room: in the **Stage Management**section, they can **approve or reject** selected members, or **approve all members** who have applied to be on stage.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/836b54300ea111ef8c545254000781d8.png)


---
*Source: [https://trtc.io/document/59974](https://trtc.io/document/59974)*
