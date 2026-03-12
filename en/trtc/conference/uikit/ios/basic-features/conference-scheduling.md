# Conference Scheduling

**If the UI interaction of conference(TUIRoomKit) does not meet your product requirements, and you have your own interaction and business logic needs for custom implementation of scheduled conference-related interaction features, you can integrate TUIRoomEngineSDK and refer to**[key code](https://www.tencentcloud.com/document/product/647/63139#14dd6ab2-f191-4934-9447-a24cfb8d1a25) related calls to meet your needs.

## Description of the Feature

TUIRoomKit supports schedule conference, allowing users to book a room and schedule conference. This article will detail the features of this functionality and explain how to use it within the TUIRoomKit component.

| Schedule Conference | Conference List | Configure Conference | Invite Members |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3217e0227b1411ef8829525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4649c9477b1411ef8631525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/63b0da5f7b1411ef8631525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7f5f98d47b1411efb9d8525400f69702.png) |

## Feature Integration

Before using the schedule conference feature, you need to complete the relevant configuration for TUIRoomKit and **log in to**. For details, please refer to [Quick Access](https://www.tencentcloud.com/document/product/647/54843#087dff27-11d0-42ec-bb14-202b4b333452).

> **Note:****The scheduled conference feature requires Conference v2.5.0 and above.**

### How to Schedule a Conference

To utilize the scheduled conference feature, you need to access the conference scheduling page provided by TUIRoomKit:

Android

iOS

Flutter

According to your business, simply call the following code in the corresponding Activity to schedule a conference.

java

kotlin

```
Intent intent = new Intent(this, ScheduleConferenceActivity.class);
startActivity(intent);
```

```
val intent = Intent(this, ScheduleConferenceActivity::class.java)startActivity(intent)
```

```
class YourViewController: UIViewContrller {    func jumpToScheduleViewController {        let scheduleViewController = ScheduleConferenceViewController()        navigationController?.pushViewController(scheduleViewController, animated: true)  }}
```

According to your business, navigate to `ScheduleRoomPage` when needed to access the conference scheduling page.

```
import 'package:tencent_conference_uikit/tencent_conference_uikit.dartNavigator.push(  context,  MaterialPageRoute(    builder: (context) => ScheduleRoomPage(),  ),);
```

- Configure Conference Details: Room Name, Room Type, Start Time, Room Duration, Timezone, Invite Members (Member List needs to be imported), Room Encryption, and Member Management (Mute All, Disable Drawing for All).
- How to invite members: Click "Add" to invite members. By default, you need to input the user list. To facilitate a quick experience, we provide a demo user list. Please refer to [How to invite members](https://www.tencentcloud.com/document/product/647/63139#ca6f6f6b-ca47-4bf0-aedd-ca817ae3401d).

| Enter the schedule conference interface | Configure conference details | Scheduled successful |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1a2c2857b1411ef80ff525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dc187b477b1411ef8631525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fecf7f357b1411ef80ff525400d5f8ef.png) |

### View scheduled conferences

TUIRoomKit provides UI components for the conference list. By arranging the conference list component on your page, you can view and manage all conferences by the current user:

Android

iOS

Flutter

1. Based on your business, add the conference list layout to your layout:

```
<!-- For example, if your parent layout is ConstraintLayout, add the following code --><FrameLayout
    android:id="@+id/tuiroomkit_fl_conference_list_container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintBottom_toBottomOf="parent"/>
```

2. Add the following code in the corresponding Activity to pull up the conference list:

java

kotlin

```
ConferenceListFragment fragment = new ConferenceListFragment();
FragmentTransaction transaction = this.getSupportFragmentManager().beginTransaction();
transaction.add(R.id.tuiroomkit_fl_conference_list_container, fragment);
transaction.commitAllowingStateLoss();
```

```
val fragment = ConferenceListFragment()val transaction = supportFragmentManager.beginTransaction()transaction.add(R.id.tuiroomkit_fl_conference_list_container, fragment)transaction.commitAllowingStateLoss()
```

```
class YourViewController: UIView {        // ConferenceListView initialization requires two parameters:        // @param viewController, the viewController to which the conference list page is added        func showConferenceList {             let listView = ConferenceListView(viewController: self)             view.addSubview(listView)        }}
```

```
import 'package:flutter/material.dart';import 'package:tencent_conference_uikit/tencent_conference_uikit.dart';// In your own page, add ConferenceListWidgetclass YourPage extends StatelessWidget {  const YourPage({Key? key}) : super(key: key);  @override  Widget build(BuildContext context) {    return Scaffold(      appBar: AppBar(title: const Text("Your Page")),      body: Column(        children: [          ...YourWidgets(),              // Your other widgets, this is just an exam          const ConferenceListWidget(),  // Conference list component        ],      ),    );  }}
```

The conference list provides the following features:

- View the conferences list: The list includes conference you created and conference you were invited to.
- View conference details: You can click on a specific conference to view its details.
- Modify conference information: Click on a conference in the conference list, **if the conference has not started yet, and you are the organizer**, you can edit the information for that conference.

| Click on the conference list | View conference details | Modify conference Information |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4811e33b7b1511ef8631525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5d9a3ce57b1511efb9d8525400f69702.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c7c0a357b1511ef82535254002693fd.png) |

### How to Invite Members

In the schedule conference or modify conference interface, you can click the **Participating Members** button to pop up the member selection interface. **By default, TUIRoomKit uses the Chat relationship chain. We also support you to set the**contacts**list**. For different platforms, please refer to:

Android

iOS

Flutter

#### Set contacts data

You can set your contacts user list through the setParticipants method.

java

kotlin

```
List<ConferenceDefine.User> participants = new ArrayList<>();ConferenceDefine.User user = new ConferenceDefine.User();user.id = "Jack";participants.add(user);ConferenceSession.sharedInstance().setParticipants(participants);
```

```
// Get the selected user listval participants = bundle.getSerializable(CONFERENCE_PARTICIPANTS) as ConferenceParticipantsval selectedList: ArrayList<User> = participants.selectedList
```

> **Note:**If the contacts UI of TUIRoomKit does not meet your business needs, we support you to associate your own contacts UI with TUIRoomKit. Please refer to: [How to set up a custom contacts](https://www.tencentcloud.com/document/product/647/63139#2599316c-d14b-4288-99b4-e9cd0aa963ef).

### How to experience the invite members feature

First, refer to [Run Sample Code](https://www.tencentcloud.com/document/product/647/60442), and complete the demo. In the `members.json` file of the demo project, some test user information has been pre-configured. You can choose two accounts, log in with the configured userId on two different phones, and then select the other user when scheduling or editing a conference. This way, the scheduled conference will appear in the other user's schedule list.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1ba7dada7bdd11efbe435254000bb03d.png)

### Code Implementation for Member List Page

Considering the complexity of the user list data on the invite members page, we have designed a solution that allows you to customize the Member Selection Interface. Next, we will guide you on how to integrate your own member selection page (of course, you can also directly use the UI provided in the demo, which will be introduced later).

1. Prepare your Friend Selection Page viewController, implementing the `SelectMemberControllerProtocol` protocol.

```
// Sample Codeclass SelectMemberViewController: UIViewController, ContactViewProtocol {    weak var delegate: ContactViewSelectDelegate?    var selectedUsers: [User]        func didSelectFinished() {    // Through the delegate, call back the selected members to Conference in the method where the selection i        delegate?.onMemberSelected(self, invitees: selectedMembers)    }}
```

> **Note:**The in-conference call feature also requires using your custom-defined contacts component. If you still need to use the in-conference call feature, it is recommended to place a `ConferenceParticipants` object in your contacts page's constructor parameter. The data source will be mentioned in the code in step two.The `ConferenceParticipants` class has two members:selectedList: the selected members;unSelectableList: Non-selectable members. You can set the corresponding members as non-selectable on the UI. The schedule conference feature does not use this field.

2. **Return the selected user list from the custom**contacts**to TUIRoomKit:** After completing user selection in the contacts, you need to return the selected user list to TUIRoomKit. You can return the data to TUIRoomKit using the following method.

```
// Sample CodeConferenceSession.sharedInstance.setContactsViewProvider { participants in    return SelectMemberViewController(participants: participants)}
```

3. With the above two steps, you can display your own member selection page. We also provide the page code in the demo as shown in the image above. You can directly copy the following files into your project to get our example page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1b90193a7bdd11ef8631525400a9236a.png)

In the `loadMembers` method of `SelectMembersViewModel`, you can load your own member list data (you can also directly obtain Chat Relationship Chain Data).

When you need to use the member invitation  feature  to invite members into the conference, we provide the following two solutions for you to add the members you need to invite:

### Solution 1: Using json to configure user information

You can refer to our  [Example Project](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/Flutter/tencent_conference_uikit/example). In the example/assets directory, `members.json` stores the user information required for invitations. Follow these steps:

1. In the `assets` directory of your project, create a new `members.json` file listing all the user information you need. The file format should be the same as the `members.json` mentioned above.
2. In the `pubspec.yaml` file of your project, complete the following configuration:

```
assets:  - assets/members.json
```

After completing the above configuration, you can select the members listed in `members.json` in the member invitation interface.

### Solution 2: Using Chat Buddy Information

If you have not configured the `members.json` mentioned above, the invite friends interface will default to pulling your Chat Buddy Information. When you need to invite other members to the conference, you can add the members you want to invite as friends according to your business needs.

- Prerequisites: log in to Chat SDK, the login process is the same as the [log in to Floating Chat](https://www.tencentcloud.com/document/product/647/57508#69f9a5eb-0191-4af4-9294-2a7dde5b4615) process. If you have already completed the login process or are using [In-Conference Chat](https://www.tencentcloud.com/document/product/647/61632), you can skip this step.
- The code for adding friends is as follows:

```
import 'package:tencent_cloud_chat_sdk/manager/v2_tim_manager.dart';// In Flutter Conference, there is already a dependency on tencent_cloud_chat_sdk, so there is no need to configure it separately// Replace the userID in the code with the UserID of the user you want to add to complete the friend additV2TIMManager().getFriendshipManager().addFriend(       userID: 'userID', addType: FriendTypeEnum.V2TIM_FRIEND_TYPE_BOTH);
```

After adding friends, you can choose to invite the added users **each time** you make a reservation.

If you need more related friend operations, please refer to: [Friend Management](https://trtc.io/document/48157). If you need to use REST API to batch add friends, please refer to: [Adding Friends RestAPI](https://trtc.io/document/34902).

After completing the steps above, by clicking the **Add** button, a member selection interface will pop up. Here, you can invite or remove members. Once modified, the conference you have booked will **appear in the other party's conference list**.

| Schedule conference interface click **Add** | Add or delete members from the user list |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a325dc8f7b1511ef8631525400a9236a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aee6b2107b1511ef80ff525400d5f8ef.png) |

### Notes

- After successfully scheduling a conference, you can get the conference id and reservation information.
- To batch schedule conferences at different dates/times, select the times and submit in batches.
- The start time for scheduling a conference cannot be earlier than the current time, but there is no limit on the number of days in advance.
- After the scheduled conference reaches the end time, if the conference has not been dissolved and there are no users in the conference, the conference will be retained for 6 hours from the scheduled end time. During this period, you can still enter the conference at any time.

## Feature customization

If the current UI does not meet your needs, you can achieve the desired UI effect by modifying the source code. For different platforms, please refer to:

Android

iOS

Flutter

You can achieve the desired UI effect by modifying the source code in the [Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/schedule](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/view/schedule) directory. To make it easier for you to customize the UI, here is an introduction to the Room Password file.

```
SchdeuleConference   âââ ConferenceDetails          // Conference details interface   âââ ConferenceList             // Conference list interface   âââ ModifyConference           // Modify conference interface   âââ SelectScheduleParticipant  // Calling the contacts list transmitted from outside   âââ TimeZone                   // Configure timezone interface   âââ View                       // Schedule conference interface
```

### How to set up a custom contacts

1. Pass in your Contacts UI:

You can use the following methods to import your contacts before [scheduling a conference](https://www.tencentcloud.com/document/product/647/63139#8be0d151-7bb2-4b84-a462-5fa7ff8fe037) and [opening the conference list](https://www.tencentcloud.com/document/product/647/63139#c1574ffd-812a-49ff-8826-74791e61f8ff)

java

kotlin

```
// Replace SelectParticipantActivity.class with your contacts activityConferenceSession.sharedInstance().setContactsViewProvider(SelectParticipantActivity.class);
```

```
// Replace SelectParticipantActivity.class with your contacts activityConferenceSession.sharedInstance().setContactsViewProvider(SelectParticipantActivity::class.java)
```

2. Your contacts returns the selected user list to TUIRoomKit:

After the contacts completes the user selection, you need to return the selected user list to TUIRoomKit. You can return data to TUIRoomKit in the following way.

java

kotlin

```
Intent intent = new Intent();// participants is the selected user list and must be of ArrayList<User> type.intent.putExtra(SELECTED_PARTICIPANTS, participants);setResult(3, intent);finish();
```

```
val intent = Intent()// participants is the selected user list and must be of ArrayList<User> type.intent.putExtra(SELECTED_PARTICIPANTS, participants)setResult(3, intent)finish()
```

3. TUIRoomKit passes the selected user list to your contacts:

You can obtain the list of users selected for the conference by the following method.

java

kotlin

```
// Get the selected user listConferenceParticipants participants = (ConferenceParticipants) bundle.getSerializable(CONFERENCE_PARTICIPANTS);ArrayList<User> selectedList = participants.selectedList;
```

```
// Get the selected user listval participants = bundle.getSerializable(CONFERENCE_PARTICIPANTS) as ConferenceParticipantsval selectedList: ArrayList<User> = participants.selectedList
```

You can achieve a satisfactory UI by modifying the source code in the [iOS/TUIRoomKit/Source](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/iOS/TUIRoomKit/Source) directory. To make it easier for you to customize the UI, here is an introduction to the files related to the room password.

```
Source    âââ ConferenceListView.swift                  // Conference listâââ ScheduleConferenceViewController.swift    // Schedule conference interfaceâââ View    âââ ConferenceOptions     Â Â  âââ ConferenceInvitation              // Conference invitation     Â Â  âââ MemberSelect                      // Invite members     Â Â  âââ ModifySchedule                    // Modify conference     Â Â  âââ ScheduleConference             âââ View                âââ ScheduleConference        // Schedule conference                 âââ ScheduleDetails           // Schedule conference details                âââ Widget                    // Conference pop view
```

You can modify the source code under the [tencent_conference_uikit/lib/pages](https://github.com/Tencent-RTC/TUIRoomKit/tree/main/Flutter/tencent_conference_uikit/lib/pages) directory to achieve your desired UI results. To make UI customization easier for you, here is an introduction to the files for scheduled conference.

```
pages      âââ conferenceList                            // Folder for scheduled conference list  |       âââ view.dart                         // Scheduled conference list page  |       âââ widget.dart                           |             âââ conference_date_item.dart   // Single date widget in the conference list  |             âââ conference_item.dart        // Single conference widget in the conference list  |             âââ no_schedule_widget.dart     // Widget displayed when there are no conference in the conference list  âââ schedule_conference                       // Folder for scheduled conference page  â       âââ view.dart                         // Scheduled conference page  â       âââ widgets  â             âââ attendee_selector           // Folder for attendee selection page  â             â      âââ view.dart            // Attendee selection page  â             â      âââ widgets  â             â             âââ selected_attendees.dart  // Pop-up page of selected attendees  â             âââ duration_selector.dart      // Widget for selecting conference duration  â             âââ room_control.dart           // Widget for muting/unmuting all attendees or disabling/enabling video during the conference  â             âââ room_info.dart              // Widget for overall room information of the scheduled conference  â             âââ room_type.dart              // Widget for selecting room type  â             âââ start_time_selector.dart    // Widget for selecting conference start time  â             âââ time_zone_selector.dart     // Page for selecting conference time zone  âââ schedule_details                          // Folder for conference details  â       âââ view.dart                         // conference details page   â       âââ widgets  â           âââ details_button_item.dart      // Single button widget in the conference details page  âââ         âââ room_info.dart                // Meeting information widget
```

> **Note:**If you have any suggestions or feedback, contact us at info_rtc@tencent.com.

## Key code

If you want to implement the schedule conference feature from Definition, please refer to TUIConferenceListManager: [Android](https://www.tencentcloud.com/document/product/647/64482#d5eaa3d13b4939e42a645d2c10016fcc), [iOS&Mac](https://www.tencentcloud.com/document/product/647/64476).


---
*Source: [https://trtc.io/document/63139](https://trtc.io/document/63139)*
