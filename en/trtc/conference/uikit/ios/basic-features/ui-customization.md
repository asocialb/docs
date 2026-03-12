# UI Customization

This article will introduce how to customize the user interface of TUIRoomKit. By reading this article, you will understand various schemes for UI customization in TUIRoomKit to meet your specific application needs. Through these schemes, you can flexibly adjust and optimize UI elements to better fit your requirements.

## Replace Icon

You can directly modify the Icon Components in the **TUIRoomKit/Resources/TUIRoomKit.xcassets** folder to ensure a consistent color scheme for icons throughout the App. Please keep the icon file names unchanged when replacing.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f281a7a1bdd11ef942e525400720cb5.png)

## Replace Copywriting

You can modify the string content of the video conferencing interface by modifying the `TUIRoomKitLocalized.xcstrings` file in the `TUIRoomKit/Resources/Localized` folder.

## Adjust Video Window Layout

In the Meeting Main Interface, the classes related to video footage are as shown:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f42357b1bdd11efa1975254005ac0ca.png)

The file directory structure for classes related to video footage is as follows. You can adjust the video footage by modifying the contents in the `TUIRoomKit/Source/View` file.

```
Viewâââ Page    âââ ConferenceMainView.swift                            // Meeting Main View    âââ Widget        âââ VideoSeat            âââ ScreenCaptureMaskView.swift                 // Panel displayed during Local Screen Sharing            âââ VideoSeatCell.swift                         // Video Image Cell            âââ VideoSeatLayout.swift                       // Video Screen Layout            âââ VideoSeatUserStatusView.swift               // User Information Below Video Screen            âââ VideoSeatView.swift                         // Overall Video Screen Panel
```

## Adjust Bottom Toolbar

In the bottom toolbar of the meeting interface, there are various buttons related to the meeting. Classes or objects related to the bottom bar and its UI are as shown:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f22bc2f1bdd11efa1975254005ac0ca.png)

The file directory structure of classes related to the bottom toolbar is as follows. You can adjust the bottom bar by modifying the content in the `TUIRoomKit/Source/View` file.

```
Viewâââ Page    âââ Widget        âââ BottomNavigationBar            âââ BottomItemView.swift                        // Bottom Bar Universal Button            âââ BottomView.swift                            // Bottom Toolbar
```

### Modification of Bottom Toolbar Button

To facilitate your custom Definition of bottom feature buttons, our BottomView automatically constructs by reading a list. For example, to switch the video button, the code is as follows. You can modify the content of the button to achieve your desired requirements.

```
func createBottomData() {        let muteVideoItem = ButtonItemData()        // Set the default button title        muteVideoItem.normalTitle = .unMuteVideoText        // Set the button title after clicking        muteVideoItem.selectedTitle = .muteVideoText        // Set the default button icon        muteVideoItem.normalIcon = "room_camera_on"        // Set the button icon after clicking        muteVideoItem.selectedIcon = "room_camera_off"        // Set the button background color        muteVideoItem.backgroundColor = UIColor(0xA3AEC7)        // Set Button Image Resource Acquisition Location        muteVideoItem.resourceBundle = tuiRoomKitBundle()        // Set Whether the Button is Clickable        muteVideoItem.isSelect = !(roomInfo.isOpenCamera)        // Set Button Type to Distinguish Different Buttons          muteVideoItem.buttonType = .muteVideoItemType        // Set Button Click Event        muteVideoItem.action = { [weak self] sender in            guard let self = self, let button = sender as? UIButton else { return }            self.muteVideoAction(sender: button)        }}
```

## Adjust Top Toolbar

In the meeting main interface, classes or objects related to the top toolbar are as shown:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/392ffff31bf511efa1975254005ac0ca.png)

The file directory structure of classes related to the top toolbar is as follows. You can adjust the top bar by modifying the content in the `TUIRoomKit/Source/View` file.

```
Viewâââ Page    âââ Widget        âââ TopNavigationBar            âââ TopItemView.swift                           // Top Bar Universal Button            âââ TopView.swift                               // Top Toolbar
```

## Adjust Other UI

When you need to adjust other UI elements, you can refer to the directory structure of other UIs under the `TUIRoomKit/Source/View` file. In the directory structure below, each file's corresponding UI has been marked. You can modify parts of the UI you wish to change according to your needs.

```
Viewâââ Componentâââ Page    âââ ConferenceMainView.swift                            // Meeting Main Page    âââ Widget        âââ Dialog        â   âââ ExitRoomView.swift                          // Exit Room Popup        â   âââ MemberInviteView.swift                      // Invite Member Popup        â   âââ RaiseHandNoticeView.swift                   // Raise Hand Notification Box        â   âââ RoomInfoView.swift                          // Room Information Popup        âââ FloatWindow        â   âââ RoomUserStatusView.swift                    // Floating Window User Information        â   âââ RoomVideoFloatView.swift                    // Floating Window        âââ LocalAudioIndicator        â   âââ LocalAudioView.swift                        // Bottom Microphone Button        âââ MediaSettings        â   âââ MediaSettingView.swift                      // Settings Interface        â   âââ QualityInfoPanel.swift                      // Quality Inspection Panel        â   âââ VideoChoicePanel.swift                      // Video Settings Panel        âââ PopUpControlPanel        â   âââ PopUpView.swift                             // General Bottom Popup        âââ RaiseHandControlPanel        â   âââ RaiseHandApplicationCell.swift              // Stage Application List Member Cell        â   âââ RaiseHandApplicationListView.swift          // Stage Application List        â   âââ RaiseHandApplicationNotificationView.swift  // Stage Application Notification Box        âââ TransferOwnerControlPanel        â   âââ TransferMasterView.swift                    // Transfer Master Panel when Host checks out        âââ UserControlPanel        â   âââ UserListCell.swift                          // User List Member Cell        â   âââ UserListManagerView.swift                   // Manage User Panel        â   âââ UserListView.swift                          // User List Panel        âââ WaterMark            âââ FeatureSwitch.swift                         // Watermark Toggle            âââ WaterMarkLayer.swift                        // Watermark View            âââ WaterMarkLineStyle.swift                    // Watermark Text Style
```

## Custom Definition UI Scheme

The overall feature of TUIRoomKit is based on the UI-less SDK, TUIRoomEngine. You can fully implement your own UI interface based on TUIRoomEngine. For more details, see [TUIRoomEngine API](https://www.tencentcloud.com/document/product/647/54856#).


---
*Source: [https://trtc.io/document/54849](https://trtc.io/document/54849)*
