# Android

## Business Process

This section summarizes some common business processes in voice chat rooms to help you better understand the entire scenario implementation process.

Room Management Process

Room Owner Seat Management Process

Audience Seat Management Process

The following figure shows the room management process, including the creation, joining, exiting, and dissolvement of rooms.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c65f2bab8f0411f088af5254005ef0f7.png)

The following figure shows the room owner seat management process, including inviting a listener to speak, removing a speaker, and muting a seat.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c66640e98f0411f0ae9d5254001c06ec.png)

The following figure shows the audience seat management process, including becoming a speaker, become a listener, and moving a seat.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c66a069d8f0411f0ae9d5254001c06ec.png)

## Integration Preparation

### Step 1. Activating the Services

The voice chat room scenario typically depends on 2 paid PaaS services for construction, [Chat](https://trtc.io/products/chat) and [RTC Engine](https://trtc.io/products/rtc).

1. First, log in to the [Console](https://console.trtc.io/) to create applications, wherein one is an RTC Engine application, and the other one is a Chat application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c683dcba8f0411f0ae9d5254001c06ec.png)

> **Note:**It is recommended to create 2 separate applications for testing environment and production environment respectively. Each account (UIN) is given 10,000 free minutes monthly for one year.RTC Engine monthly packages are divided into Trial Edition (default), Lite Edition, Standard Edition, and Professional Edition, unlocking different value-added features and services. For details, see [Version Features and Monthly Package Description](https://trtc.io/document/67650?product=pricing).

2. After an application is created, you can see the basic information of the application in the **Application Management - Application Overview** section. It is important to keep the **SDKAppID** and **SDKSecretKey** safe for later use and to avoid key leakage that could lead to traffic theft.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c677c40d8f0411f088af5254005ef0f7.png)

### Step 2: Importing the SDK

The RTC Engine SDK and the Chat SDK have been published to the **mavenCentral** repository. You can configure gradle to download updates automatically.

1. Add the dependency for the appropriate version of the SDK in dependencies.

```
dependencies {    // TRTC Lite Edition SDK, including 2 features, TRTC and live streaming playback.    implementation 'com.tencent.liteav:LiteAVSDK_TRTC:latest.release'        // Add the Chat SDK. It's recommended to enter the latest version number.    implementation 'com.tencent.imsdk:imsdk-plus:Version number'    // If you need to add the Quic plugin, uncomment the next line (Note: the plugin version number should be identical to the Chat SDK version number).    // implementation 'com.tencent.imsdk:timquic-plugin:Version number'}
```

> **Note:**Except the recommended automatic loading method, you can also choose to download SDK and manually import it. For details, see [Manual Integration of the RTC Engine SDK](https://trtc.io/document/62045?product=rtcengine&menulabel=core%20sdk&platform=android#31b6b3f0-5363-44b1-95a0-dbabe648e9df) and[Manual Integration of the Chat SDK](https://trtc.io/document/34306?product=chat&menulabel=core%20sdk&platform=android#96b656a2-61f9-4b6b-9240-38b28a86057a).Quic plugin, offering axp-Quic multiplexing protocol with better resistance to poor networks, can still offer services under 70% packet loss rate. It's only applicable to Professional Edition, Professional Edition plus, and Enterprise Edition users. Purchase[Pro Edition, Pro plus Edition ,or Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use. To ensure normal usage of features, update the Chat SDK to version 7.7.5282 or later.

2. Specify the CPU architecture used by the app in defaultConfig.

```
defaultConfig {     ndk {             abiFilters "armeabi-v7a", "arm64-v8a"     }}
```

> **Note:**The RTC Engine SDK supports armeabi/armeabi-v7a/arm64-v8a architectures, and additionally supports x86/x86_64 architecture dedicated to simulators.The Chat SDK supports armeabi-v7a/arm64-v8a/x86/x86_64 architectures. To reduce installation package size, you can choose to package SO files of some architecture.

### Step 3: Project Configuration

1. Configure App permissions in AndroidManifest.xml. In voice chat scenarios, the RTC Engine SDK and the Chat SDK require the following permissions.

```
<uses-permission android:name="android.permission.INTERNET" /><uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /><uses-permission android:name="android.permission.ACCESS_WIFI_STATE" /><uses-permission android:name="android.permission.RECORD_AUDIO" /><uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" /><uses-permission android:name="android.permission.BLUETOOTH" />
```

> **Note:**The RTC Engine SDK has no built-in permission request logic. You need to declare corresponding permissions and features. Some permissions (such as storage and recording) require dynamic requests during running.If the Android project's `targetSdkVersion` is 31 or higher, or if the target device runs Android 12 or a newer version, the official requirement is to dynamically request `android.permission.BLUETOOTH_CONNECT` permission in the code to use the Bluetooth feature properly. For more information, see [Bluetooth Permissions](https://developer.android.google.cn/develop/connectivity/bluetooth/bt-permissions).

2. Since we use Java's reflection feature in the SDK, you should add relevant RTC Engine SDK classes to the non-obfuscation list in the proguard-rules.pro file.

```
-keep class com.tencent.** { *; }
```

## Integration Process

### Step 1: Generate Authentication Credentials

UserSig is a security protection signature designed by Tencent for real-time communication services to prevent attackers from stealing your right of using cloud services. RTC Engine and Chat services adopt this security protection mechanism, with RTC Engine performing authentication during room entry and Chat performing authentication during login.

- Debugging Stage: UserSig can be generated through two methods for debugging and testing purposes only: [client sample code](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk&platform=android) and [console access](https://trtc.io/document/35166?product=rtcengine&menulabel=core%20sdk&platform=android#console).
- Formal Operation Stage: It is recommended to use a higher security level server computation for generating UserSig. This is to prevent key leakage due to client reverse engineering.

The specific implementation process is as follows:

1. Before calling the SDK's initialization function, your app must first request UserSig from your server.
2. Your server computes the UserSig based on the SDKAppID and UserID.
3. The server returns the computed UserSig to your app.
4. Your app passes the obtained UserSig into the SDK through a specific API.
5. The SDK submits the SDKAppID + UserID + UserSig to Tencent Cloud CVM for verification.
6. Tencent Cloud verifies the UserSig and confirms its validity.
7. After the verification passes, the Chat SDK will be provided with instant messaging services, and the RTC Engine SDK will be provided with Tencent Real-Time Communication (TRTC) services.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c66a697c8f0411f0b321525400e889b2.jpeg)

> **Note:**The local computation method of UserSig during the debugging stage is not recommended for application in an online environment. It is prone to reverse engineering, leading to key leakage.We provide UserSig server-side computation source code in multiple languages (Java/Go/PHP/Node.js/Python/C#/C++). For details, see [Server-Side Calculation of UserSig](https://trtc.io/document/34580?product=chat&menulabel=uikit&platform=react#.E7.AD.BE.E5.90.8D.EF.BC.88usersig.EF.BC.89.E7.94.9F.E6.88.90.E5.B7.A5.E5.85.B7).

### Step 2: Initialization and Listening

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c65f03578f0411f0974b52540044a08e.svg)

1. Initialize the Chat SDK and add an event listener.

```
// Add event listener.V2TIMManager.getInstance().addIMSDKListener(imSdkListener);// Initialize the Chat SDK. After calling this API, you can immediately call the login API.V2TIMManager.getInstance().initSDK(context, sdkAppID, null);// After the SDK is initialized, it will trigger various events, such as connection status and expiration of log-in credentials.private V2TIMSDKListener imSdkListener = new V2TIMSDKListener() {    @Override    public void onConnecting() {        Log.d(TAG,"Chat SDK is connecting to Tencent Cloud Virtual Machine (CVM)");    }    @Override    public void onConnectSuccess() {        Log.d(TAG, "Chat SDK has successfully connected to Tencent CVM");    }};// Remove event listener.V2TIMManager.getInstance().removeIMSDKListener(imSdkListener);// Deinitialize the Chat SDK.V2TIMManager.getInstance().unInitSDK();
```

> **Note:**If your application's lifecycle is consistent with the SDK's lifecycle, you do not need to deinitialize before exiting the application. If you only initialize the SDK after entering a specific interface and no longer use it after exiting, you may deinitialize the SDK.

2. Create an RTC Engine SDK instance and set an event listener.

```
// Create an RTC Engine SDK instance (singleton mode)TRTCCloud mTRTCCloud = TRTCCloud.sharedInstance(context);// Set event listeners.mTRTCCloud.setListener(trtcSdkListener);// Notifications from various SDK events (e.g., error codes, warning codes, audio and video status parameters, etc.).private TRTCCloudListener trtcSdkListener = new TRTCCloudListener() {    @Override    public void onError(int errCode, String errMsg, Bundle extraInfo) {        Log.d(TAG, errCode + errMsg);    }        @Override    public void onWarning(int warningCode, String warningMsg, Bundle extraInfo) {        Log.d(TAG, warningCode + warningMsg);    }};// Remove event listener.mTRTCCloud.setListener(null);// Terminate the RTC Engine SDK instance (singleton mode)TRTCCloud.destroySharedInstance();
```

> **Note:**It is recommended to listen to SDK event notifications. Perform log printing and handling for some common errors. For details, see [Error Code Table](https://trtc.io/document/35130?platform=android&product=rtcengine&menulabel=core%20sdk#336ef58d7636c75f9aa0c87753e08e7c).

### Step 3: Log In and Log Out

After initializing the Chat SDK, you need to call the SDK login API to authenticate account identity and obtain permissions to use features of the account. Therefore, before using other features, ensure successful login. Otherwise, feature malfunction or unavailability may occur. If you only need to use the RTC Engine audio and video service, you can skip this step.

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c66db3b58f0411f084bd5254007c27c5.svg)

1. Log in.

```
// Log in: userID can be defined by the user and userSig can be generated as per Step 1.V2TIMManager.getInstance().login(userID, userSig, new V2TIMCallback() {    @Override    public void onSuccess() {        Log.i("imsdk", "success");    }        @Override    public void onError(int code, String desc) {        // If the following error codes are returned, it means that an expired UserSig is in use. You need to generate a new one for login again.        // 1. ERR_USER_SIG_EXPIRED (6206)        // 2. ERR_SVR_ACCOUNT_USERSIG_EXPIRED (70001)        // Note: For other error codes, do not call the login API here to avoid the Chat SDK entering an infinite loop.        Log.i("imsdk", "failure, code:" + code + ", desc:" + desc);    }});
```

2. Log out.

```
// Log out.V2TIMManager.getInstance().logout(new V2TIMCallback() {    @Override    public void onSuccess() {        Log.i("imsdk", "success");    }        @Override    public void onError(int code, String desc) {        Log.i("imsdk", "failure, code:" + code + ", desc:" + desc);    }});
```

> **Note:**If your application's lifecycle matches the Chat SDK's lifecycle, you do not need to log out before exiting the application. If you only use the Chat SDK after entering a specific interface and no longer use it after exiting the interface, you can log out and deinitialize the Chat SDK.

### Step 4: Room Management

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c676893a8f0411f0814e525400bf7822.svg)

1. Create a room.

The anchor (room owner) needs to create a room when going live. Here, the concept of "room" corresponds to "group" in Chat. This example only shows the way to create a Chat group on the client side. It can also be done[via server-side group creation](https://trtc.io/document/34895?product=chat&menulabel=core%20sdk&platform=android).

```
V2TIMManager.getInstance().createGroup(V2TIMManager.GROUP_TYPE_AVCHATROOM, groupID, groupName, new V2TIMValueCallback<String>() {  @Override  public void onSuccess(String s) {      // Group created successfully.  }  @Override  public void onError(int code, String desc) {      // Group creation failed.  }});// Listen for group creation notifications.V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {  @Override  public void onGroupCreated(String groupID) {      // Group creation callback. GroupID is the ID of the newly created group.  }});
```

> **Note:**To create a Chat group for a voice chat room scenario, select the live streaming group type `GROUP_TYPE_AVCHATROOM`.The RTC Engine does not provide a room-creation API. When a user attempts to join a room that does not exist, the backend automatically creates a room.

2. Enter a room.
  - Join a Chat group.

```
V2TIMManager.getInstance().joinGroup(groupID, message, new V2TIMCallback() {  @Override  public void onSuccess() {      // Successfully joined the group.  }  @Override  public void onError(int code, String desc) {      // Failed to join the group.  }});// Listen for the event of joining a group.V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {  @Override  public void onMemberEnter(String groupID, List<V2TIMGroupMemberInfo> memberList) {      // Someone joined the group.  }});
```

  - Join an RTC Engine room.

```
private void enterRoom(String roomId, String userId) {    TRTCCloudDef.TRTCParams params = new TRTCCloudDef.TRTCParams();    // Using a string-type room ID for example, it is recommended to keep it consistent with the Chat group ID.    params.strRoomId = roomId;    params.userId = userId;    // UserSig obtained from the business backend.    params.userSig = getUserSig(userId);    // Replace with your SDKAppID.    params.sdkAppId = SDKAppID;    // For room entry in voice chat interaction scenarios, specify the user's role.    params.role = TRTCCloudDef.TRTCRoleAudience;    // Use room entry in voice chat interaction scenarios as an example.    mTRTCCloud.enterRoom(params, TRTCCloudDef.TRTC_APP_SCENE_VOICE_CHATROOM);}// Event callback for the result of entering the room.@Overridepublic void onEnterRoom(long result) {    if (result > 0) {        // Result indicates the time taken (in milliseconds) to join the room.        Log.d(TAG, "Enter room succeed");    } else {        // Result indicates the error code in the case of room entry failure.        Log.d(TAG, "Enter room failed");    }}
```

> **Note:**RTC Engine room IDs are divided into integer type `roomId` and string type `strRoomId`. Rooms of different types are not interconnected. It is advisable to unify the room ID type.When entering a room in voice chat interaction scenarios, it is necessary to specify the user's role (anchor/audience). Only anchors have permissions to push streams. If not specified, the default role is anchor.For voice chat interaction room-entering scenarios, it is recommended to use `TRTC_APP_SCENE_VOICE_CHATROOM`.

3. Exit the room.
  - Exit a Chat group.

```
V2TIMManager.getInstance().quitGroup(groupID, new V2TIMCallback() {  @Override  public void onSuccess() {      // Successfully exited the group.  }  @Override  public void onError(int code, String desc) {      // Failed to exit the group.  }});V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {  @Override  public void onMemberLeave(String groupID, V2TIMGroupMemberInfo member) {        // Group member leaving callback.  }});
```

> **Note:**In a live streaming group (AVChatRoom), the group owner cannot exit the group. The owner can only dissolve the group by calling `dismissGroup`.

  - Exit an RTC Engine room.

```
private void exitRoom() {    mTRTCCloud.stopLocalAudio();    mTRTCCloud.exitRoom();}// Event callback for exiting the room.@Overridepublic void onExitRoom(int reason) {    if (reason == 0) {        Log.d(TAG, "Actively call exitRoom to exit the room.");    } else if (reason == 1) {        Log.d(TAG, "Removed from the current room by the server.");    } else if (reason == 2) {        Log.d(TAG, "The current room has been dissolved.");    }}
```

> **Note:**After all resources occupied by the SDK are released, the SDK will throw the `onExitRoom` callback notification to inform you.If you want to call `enterRoom` again or switch to another audio/video SDK, wait for the `onExitRoom` callback before proceeding. Otherwise, you may encounter exceptions such as the camera or microphone being forcefully occupied.

4. Dissolve the room.
- Dissolve a Chat group.

This example only shows the way to dissolve a Chat group on the client side. It can also be done via [server-side group dissolving](https://trtc.io/zh/document/34896?product=chat&menulabel=core%20sdk&platform=android).

```
V2TIMManager.getInstance().dismissGroup(groupID, new V2TIMCallback() {  @Override  public void onSuccess() {      // Group dissolved successfully.  }  @Override  public void onError(int code, String desc) {      // Failed to dissolve the group.  }});V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {  @Override  public void onGroupDismissed(String groupID, V2TIMGroupMemberInfo opUser) {      // Group dissolving callback.  }});
```

- Dissolve an RTC Engine room.
  - **Server-side dissolving**: RTC Engine provides the [server-side room dissolving](https://trtc.io/zh/document/34269?product=rtcengine&menulabel=core%20sdk&platform=android) API `DismissRoom` (distinguish between numeric room ID and string room ID). You can call this API to remove all users from the room and dissolve the room.
  - **Client dissolving**: Complete room exit for all anchors and audiences in the room via the room exit API `exitRoom` of each client. After room exit, the room will be automatically dissolved according to RTC Engine room lifecycle rules. For details, see [Exit the Room](https://trtc.io/zh/document/62045?product=rtcengine&menulabel=core%20sdk&platform=android#5055ad66-53b1-4539-88ec-6992d45bb0fd).

> **Warning:**It is recommended that after the end of live streaming, you call the room dissolvement API to ensure the room is dissolved. This will prevent audiences from accidentally entering the room and incurring unexpected charges.

### Step 5: Seat Management

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c66d10428f0411f0b321525400e889b2.svg)

First, we can create a JavaBean to save seat information.

```
public class SeatInfo implements Serializable {    public static final transient int STATUS_UNUSED  = 0;    public static final transient int STATUS_USED    = 1;    public static final transient int STATUS_LOCKED  = 2;    // The status of seats. Three corresponding statuses are available.    public int status;    // Whether the seat is muted.    public boolean mute;    // When the seat is occupied, the user information is stored.    public String userId;    @Override    public String toString() {        return "TXSeatInfo{"                + "status=" + status                + ", mute=" + mute                + ", user='" + userId + '\\''                + '}';    }}
```

1. Join a voice chat actively.

Becoming a speaker refers to off-mic audience sending a request to speak to the room owner or administrator. The audience can speak once the approval signaling is received. In a free-speaking mode, the signaling request part can be skipped.

- Listener sends a request to become a speaker.

```
// Audience sends a request to speak. userId is the Anchor ID, and data can pass in a JSON identifying the signaling.private String sendInvitation(String userId, String data) {    return V2TIMManager.getSignalingManager().invite(userId, data, true, null, 0, new V2TIMCallback() {        @Override        public void onError(int i, String s) {            Log.e(TAG, "sendInvitation error " + i);        }        @Override        public void onSuccess() {            Log.i(TAG, "sendInvitation success ");        }    });}// Anchor receives the request to speak. inviteID is the request ID, and inviter is the requester ID.V2TIMManager.getSignalingManager().addSignalingListener(new V2TIMSignalingListener() {    @Override    public void onReceiveNewInvitation(String inviteID, String inviter,                                       String groupId, List<String> inviteeList, String data) {        Log.i(TAG, "received invitation: " + inviteID + " from " + inviter);    }});
```

- Anchor processes the request to become a speaker.

```
// Agree to the request to speak.private void acceptInvitation(String inviteID, String data) {    V2TIMManager.getSignalingManager().accept(inviteID, data, new V2TIMCallback() {        @Override        public void onError(int i, String s) {            Log.e(TAG, "acceptInvitation error " + i);        }        @Override        public void onSuccess() {            Log.i(TAG, "acceptInvitation success ");        }    });}// Reject the request to speak.private void rejectInvitation(String inviteID, String data) {    V2TIMManager.getSignalingManager().reject(inviteID, data, new V2TIMCallback() {        @Override        public void onError(int i, String s) {            Log.e(TAG, "rejectInvitation error " + i);        }        @Override        public void onSuccess() {            Log.i(TAG, "rejectInvitation success ");        }    });}
```

- Listeners become speakers.

If the anchor agrees to the audience's request to speak, the audience can add seat information by modifying group attributes. Other users will receive a callback for the change in group attributes. Update the local seat information.

```
// Locally saved full list of seats.private List<SeatInfo> mSeatInfoList;// Callback for agreeing to the request to speak.V2TIMManager.getSignalingManager().addSignalingListener(new V2TIMSignalingListener() {    @Override    public void onInviteeAccepted(String inviteID, String invitee, String data) {        Log.i(TAG, "received accept invitation: " + inviteID + " from " + invitee);        takeSeat(seatIndex);    }});// Audience begins to speak.private void takeSeat(int seatIndex) {    // Create a seat information instance. Store the modified seat information.    SeatInfo localInfo = mSeatInfoList.get(seatIndex);    SeatInfo seatInfo = new SeatInfo();    seatInfo.status = SeatInfo.STATUS_USED;    seatInfo.mute = localInfo.mute;    seatInfo.userId = mUserId;        // Serialize the seat information object into JSON format.    Gson gson = new Gson();    String json = gson.toJson(seatInfo, SeatInfo.class);    HashMap<String, String> map = new HashMap<>();    map.put("seat" + seatIndex, json);        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the group attribute is added.    V2TIMManager.getGroupManager().setGroupAttributes(groupId, map, new V2TIMCallback() {        @Override        public void onError(int code, String message) {            // Failed to modify group attributes. Failed to become a speaker.        }        @Override        public void onSuccess() {            // Group attributes modified successfully. Switch the TRTC role and start streaming.            mTRTCCloud.switchRole(TRTCCloudDef.TRTCRoleAnchor);            mTRTCCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_DEFAULT);        }    });}
```

2. Bring someone to a voice chat.

Anchor brings someone to a voice chat (with no listener consent required), directly modifies the seat information saved in group attributes. After matching the userId successfully upon receiving the group attribute change callback, the corresponding listener can switch the RTC Engine role and start streaming. In an invite-to-speak mode, refer to the implementation logic of becoming a speaker. Just switch the sender and recipient of the signaling.

```
// Locally saved full list of seats.private List<SeatInfo> mSeatInfoList;// Anchor calls this API to modify the seat information saved in group attributes.private void pickSeat(String userId, int seatIndex) {    // Create a seat information instance. Store the modified seat information.    SeatInfo localInfo = mSeatInfoList.get(seatIndex);    SeatInfo seatInfo = new SeatInfo();    seatInfo.status = SeatInfo.STATUS_USED;    seatInfo.mute = localInfo.mute;    seatInfo.userId = userId;        // Serialize the seat information object into JSON format.    Gson gson = new Gson();    String json = gson.toJson(seatInfo, SeatInfo.class);    HashMap<String, String> map = new HashMap<>();    map.put("seat" + seatIndex, json);        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the group attribute is added.    V2TIMManager.getGroupManager().setGroupAttributes(groupId, map, new V2TIMCallback() {        @Override        public void onError(int code, String message) {            // Failed to modify group attributes. Failed to invite a listener to speak.        }        @Override        public void onSuccess() {            // Group attributes modified successfully. Trigger onGroupAttributeChanged callback.        }    });}// Audience receives group attribute change callback. Audience starts streaming after successfully matching own information.V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {    @Override    public void onGroupAttributeChanged(String groupID, Map<String, String> groupAttributeMap) {        // Last locally saved full seat information list.        final List<SeatInfo> oldSeatInfoList = mSeatInfoList;        // The most recent full seat information list parsed in groupAttributeMap.        final List<SeatInfo> newSeatInfoList = getSeatListFromAttr(groupAttributeMap, seatSize);        // Iterate through the full seat information list. Compare old and new seat information.        for (int i = 0; i < seatSize; i++) {            SeatInfo oldInfo = oldSeatInfoList.get(i);            SeatInfo newInfo = newSeatInfoList.get(i);            if (oldInfo.status != newInfo.status && newInfo.status == SeatInfo.STATUS_USED) {                if (newInfo.userId.equals(mUserId)) {                    // Personal user information matched successfully. Switch the TRTC role and start streaming.                    mTRTCCloud.switchRole(TRTCCloudDef.TRTCRoleAnchor);                    mTRTCCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_DEFAULT);                } else {                    // Update the local seat list. Render local seat view.                }            }        }    }});
```

3. Leave a voice chat actively.

Mic-connecting audiences can reset seat information by modifying group attributes. Other users will receive a group attribute change callback. Update local seat information.

```
// Locally saved full list of seats.private List<SeatInfo> mSeatInfoList;private void leaveSeat(int seatIndex) {    // Create a seat information instance. Store the modified seat information.    SeatInfo localInfo = mSeatInfoList.get(seatIndex);    SeatInfo seatInfo = new SeatInfo();    seatInfo.status = SeatInfo.STATUS_UNUSED;    seatInfo.mute = localInfo.mute;    seatInfo.userId = "";        // Serialize the seat information object into JSON format.    Gson gson = new Gson();    String json = gson.toJson(seatInfo, SeatInfo.class);    HashMap<String, String> map = new HashMap<>();    map.put("seat" + seatIndex, json);        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the group attribute is added.    V2TIMManager.getGroupManager().setGroupAttributes(groupId, map, new V2TIMCallback() {        @Override        public void onError(int code, String message) {            // Failed to modify group attributes. Failed to leave the seat.        }        @Override        public void onSuccess() {            // Group attributes modified successfully. Switch the TRTC role and stop streaming.            mTRTCCloud.switchRole(TRTCCloudDef.TRTCRoleAudience);            mTRTCCloud.stopLocalAudio();        }    });}
```

4. Remove people from the voice chat.

Anchor removes a speaker. Directly modify the seat information saved in group attributes. After matching the userId successfully upon receiving the group attribute change callback, the corresponding listener can switch the RTC Engine role and stop streaming.

```
// Locally saved full list of seats.private List<SeatInfo> mSeatInfoList;// Anchor calls this API to modify the seat information saved in group attributes.private void kickSeat(int seatIndex) {    // Create a seat information instance. Store the modified seat information.    SeatInfo localInfo = mSeatInfoList.get(seatIndex);    SeatInfo seatInfo = new SeatInfo();    seatInfo.status = SeatInfo.STATUS_UNUSED;    seatInfo.mute = localInfo.mute;    seatInfo.userId = "";        // Serialize the seat information object into JSON format.    Gson gson = new Gson();    String json = gson.toJson(seatInfo, SeatInfo.class);    HashMap<String, String> map = new HashMap<>();    map.put("seat" + seatIndex, json);        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the group attribute is added.    V2TIMManager.getGroupManager().setGroupAttributes(groupId, map, new V2TIMCallback() {        @Override        public void onError(int code, String message) {            // Failed to modify group attributes. Failed to become a speaker.        }        @Override        public void onSuccess() {            // Group attributes modified successfully. Trigger onGroupAttributeChanged callback.        }    });}// Mic-connecting audience receives group attribute change callback. It stops streaming after successfully matching own information.V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {    @Override    public void onGroupAttributeChanged(String groupID, Map<String, String> groupAttributeMap) {        // Last locally saved full seat information list.        final List<SeatInfo> oldSeatInfoList = mSeatInfoList;        // The most recent full seat information list parsed in groupAttributeMap.        final List<SeatInfo> newSeatInfoList = getSeatListFromAttr(groupAttributeMap, seatSize);        // Iterate through the full seat information list. Compare old and new seat information.        for (int i = 0; i < seatSize; i++) {            SeatInfo oldInfo = oldSeatInfoList.get(i);            SeatInfo newInfo = newSeatInfoList.get(i);            if (oldInfo.status != newInfo.status && newInfo.status == SeatInfo.STATUS_UNUSED) {                if (oldInfo.userId.equals(mUserId)) {                    // Its own information matched successfully. Switch the TRTC role and stop streaming.                    mTRTCCloud.switchRole(TRTCCloudDef.TRTCRoleAudience);                    mTRTCCloud.stopLocalAudio();                } else {                    // Update the local seat list. Render local seat view.                }            }        }    }});
```

5. Mute the mic.

Anchor mutes/unmutes a specific seat. Directly modify the seat information saved in group attributes. Corresponding mic-connecting audience receives group attribute change callback. After successfully matching userId, they pause/resume local streaming.

```
// Locally saved full list of seats.private List<SeatInfo> mSeatInfoList;// Anchor calls this API to modify the seat information saved in group attributes.private void muteSeat(int seatIndex, boolean mute) {    // Create a seat information instance. Store the modified seat information.    SeatInfo localInfo = mSeatInfoList.get(seatIndex);    SeatInfo seatInfo = new SeatInfo();    seatInfo.status = localInfo.status;    seatInfo.mute = mute;    seatInfo.userId = localInfo.userId;        // Serialize the seat information object into JSON format.    Gson gson = new Gson();    String json = gson.toJson(seatInfo, SeatInfo.class);    HashMap<String, String> map = new HashMap<>();    map.put("seat" + seatIndex, json);        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the group attribute is added.    V2TIMManager.getGroupManager().setGroupAttributes(groupId, map, new V2TIMCallback() {        @Override        public void onError(int code, String message) {            // Failed to modify group attributes. Failed to mute seats.        }        @Override        public void onSuccess() {            // Group attributes modified successfully. Trigger onGroupAttributeChanged callback.        }    });}// The mic-connecting audience receives the group attribute change callback. The audience pauses/resumes streaming after successfully matching own information.V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {    @Override    public void onGroupAttributeChanged(String groupID, Map<String, String> groupAttributeMap) {        // Last locally saved full seat information list.        final List<SeatInfo> oldSeatInfoList = mSeatInfoList;        // The most recent full seat information list parsed in groupAttributeMap.        final List<SeatInfo> newSeatInfoList = getSeatListFromAttr(groupAttributeMap, seatSize);        // Iterate through the full seat information list. Compare old and new seat information.        for (int i = 0; i < seatSize; i++) {            SeatInfo oldInfo = oldSeatInfoList.get(i);            SeatInfo newInfo = newSeatInfoList.get(i);            if (oldInfo.mute != newInfo.mute) {                if (oldInfo.userId.equals(mUserId)) {                    // Its own information matched successfully. Pause/ restore local streaming.                    mTRTCCloud.muteLocalAudio(newInfo.mute);                } else {                    // Update the local seat list. Render local seat view.                }            }        }    }});
```

6. Lock the mic.

Anchor locks/unlocks a seat by directly modifying the seat information saved in group attributes. Audience updates the corresponding seat view after receiving the group attribute change callback.

```
// Locally saved full list of seats.private List<SeatInfo> mSeatInfoList;// Anchor calls this API to modify the seat information saved in group attributes.private void lockSeat(int seatIndex, boolean isLock) {    // Create a seat information instance. Store the modified seat information.    SeatInfo localInfo = mSeatInfoList.get(seatIndex);    SeatInfo seatInfo = new SeatInfo();    seatInfo.status = isLock ? SeatInfo.STATUS_LOCKED : SeatInfo.STATUS_UNUSED;    seatInfo.mute = localInfo.mute;    seatInfo.userId = "";        // Serialize the seat information object into JSON format.    Gson gson = new Gson();    String json = gson.toJson(seatInfo, SeatInfo.class);    HashMap<String, String> map = new HashMap<>();    map.put("seat" + seatIndex, json);        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the group attribute is added.    V2TIMManager.getGroupManager().setGroupAttributes(groupId, map, new V2TIMCallback() {        @Override        public void onError(int code, String message) {            // Failed to modify group attributes. Failed to lock seats.        }        @Override        public void onSuccess() {            // Group attributes modified successfully. Trigger onGroupAttributeChanged callback.        }    });}// The audience receives the group attribute change callback. Update the corresponding seat view.V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {    @Override    public void onGroupAttributeChanged(String groupID, Map<String, String> groupAttributeMap) {        // Last locally saved full seat information list.        final List<SeatInfo> oldSeatInfoList = mSeatInfoList;        // The most recent full seat information list parsed in groupAttributeMap.        final List<SeatInfo> newSeatInfoList = getSeatListFromAttr(groupAttributeMap, seatSize);        // Iterate through the full seat information list. Compare old and new seat information.        for (int i = 0; i < seatSize; i++) {            SeatInfo oldInfo = oldSeatInfoList.get(i);            SeatInfo newInfo = newSeatInfoList.get(i);            if (oldInfo.status == SeatInfo.STATUS_LOCKED && newInfo.status == SeatInfo.STATUS_UNUSED) {                // Unlock a seat.            } else if (oldInfo.status != newInfo.status && newInfo.status == SeatInfo.STATUS_LOCKED) {                // Lock a seat.            }        }    }});
```

7. Move the microphone position.

On-mic anchor moves a seat by necessarily and separately modifying the source and target seat information saved in group attributes. Audience updates the corresponding seat view after receiving the group attribute change callback.

```
// Locally saved full list of seats.private List<SeatInfo> mSeatInfoList;// On-mic anchor calls this API to modify the seat information saved in group attributes.private void moveSeat(int dstIndex) {    // Obtain the source seat ID by userId.    int srcIndex = -1;    for (int i = 0; i < mSeatInfoList.size(); i++) {        SeatInfo seatInfo = mSeatInfoList.get(i);        if (seatInfo != null && mUserId.equals(seatInfo.userId)) {            srcIndex = i;            break;        }    }        // Obtain the corresponding seat information by the seat ID.    SeatInfo srcSeatInfo = mSeatInfoList.get(srcIndex);    SeatInfo dstSeatInfo = mSeatInfoList.get(dstIndex);        // Create a seat information instance. Store the modified source seat information.    SeatInfo srcChangeInfo = new SeatInfo();    srcChangeInfo.status = SeatInfo.STATUS_UNUSED;    srcChangeInfo.mute = srcSeatInfo.mute;    srcChangeInfo.userId = "";        // Create a seat information instance. Store the modified target seat information.    SeatInfo dstChangeInfo = new SeatInfo();    dstChangeInfo.status = SeatInfo.STATUS_USED;    dstChangeInfo.mute = dstSeatInfo.mute;    dstChangeInfo.userId = mUserId;    // Serialize the seat information object into JSON format.    Gson gson = new Gson();    HashMap<String, String> map = new HashMap<>();    String json = gson.toJson(srcChangeInfo, SeatInfo.class);    map.put("seat" + srcIndex, json);    json = gson.toJson(dstChangeInfo, SeatInfo.class);    map.put("seat" + dstIndex, json);        // Set group attributes. If the group attribute already exists, its value is updated. Otherwise, the group attribute is added.    V2TIMManager.getGroupManager().setGroupAttributes(groupId, map, new V2TIMCallback() {        @Override        public void onError(int code, String message) {            // Failed to modify group attributes. Failed to move seats.        }        @Override        public void onSuccess() {            // Group attributes modified successfully. Seats moved successfully.        }    });}
```

### Step 6: Audio Management

#### Sequence Diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c6738e138f0411f0814e525400bf7822.svg)

1. Subscription mode.

The RTC Engine SDK defaults to automatic subscription of audio streams. Users automatically play remote users' voice when joining a room. For manual subscription to audio streams, calling` muteRemoteAudio(userId, mute) `additionally is required to subscribe and play remote users' audio streams.

```
// Automatic subscription mode (default).mTRTCCloud.setDefaultStreamRecvMode(true, true);// Manual subscription mode (custom).mTRTCCloud.setDefaultStreamRecvMode(false, false);
```

> **Note:**Set the subscription mode `setDefaultStreamRecvMode` before entering the room `enterRoom` to ensure to take effect.

2. Collect and publish.

```
// Enable local audio capture and publishing.mTRTCCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_DEFAULT)// Stop local audio capture and publishing.mTRTCCloud.stopLocalAudio();
```

> **Note:**`startLocalAudio` requests mic permissions, and `stopLocalAudio` releases them.

3. Mute and unmute.

```
// Pause publishing local audio streams (mute).mTRTCCloud.muteLocalAudio(true);// Resume publishing local audio streams (unmute).mTRTCCloud.muteLocalAudio(false);// Pause the subscription and playback of a specific remote user's audio streams.mTRTCCloud.muteRemoteAudio(userId, true);// Resume the subscription and playback of a specific remote user's audio streams.mTRTCCloud.muteRemoteAudio(userId, false);// Pause the subscription and playback of all remote users' audio streams.mTRTCCloud.muteAllRemoteAudio(true);// Resume the subscription and playback of all remote users' audio streams.mTRTCCloud.muteAllRemoteAudio(false);
```

> **Note:**In comparison, `muteLocalAudio` only requires a pause or release of the data stream at the software level, thus it is more efficient and smoother. And it is better suited for scenarios that require frequent muting and unmuting.

4. Audio quality and volume type.
- Audio quality setting

```
// Set audio quality during local audio capture and publishing.mTRTCCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_DEFAULT);// Dynamically set audio quality during audio streaming.mTRTCCloud.setAudioQuality(TRTCCloudDef.TRTC_AUDIO_QUALITY_DEFAULT);
```

> **Note:**The RTC Engine offers 3 preset audio quality levels (Speech/Default/Music), corresponding to different audio parameters. For details, see [TRTCAudioQuality](https://trtc.io/document/50768?platform=android&product=rtcengine&menulabel=core%20sdk#9ccda47c68c6d873c7938428e0f9fd5d).

- Volume type setting.

Each RTC Engine audio quality level corresponds to a default volume type. If you need to forcibly specify a volume type, you can use the following API.

```
// Set volume type.mTRTCCloud.setSystemVolumeType(TRTCCloudDef.TRTCSystemVolumeTypeAuto);
```

> **Note:**The RTC Engine offers 3 volume type levels (VOIP/Auto/Media), corresponding to different volume channels. For details, see [TRTCSystemVolumeType](https://trtc.io/document/50768?platform=android&product=rtcengine&menulabel=core%20sdk#18a27b2511b4dfe97f272b7b7d1f6a7e).

- Audio routing setting.

Mobile devices such as smartphones usually have two playback locations: the speaker and the earpiece. If you need to forcibly specify the audio routing, you can use the following API.

```
// Set audio routing.mTRTCCloud.setAudioRoute(TRTCCloudDef.TRTC_AUDIO_ROUTE_SPEAKER);
```

> **Note:**The RTC Engine offers two audio routes (Speaker/Earpiece), corresponding to different sound emission locations. For details, see [TRTCAudioRoute](https://trtc.io/document/50768?product=rtcengine&menulabel=core%20sdk&platform=android#2e9bec9e051396669cd0f820a9d6bfc3).

## Advanced Features

### Bullet Screen Message Interaction

Voice chat live streaming rooms usually provide text-based bullet screen message interactions, which can be achieved by sending and receiving group chat plain text messages through Chat.

```
// Send public screen bullet screen messages.V2TIMManager.getInstance().sendGroupTextMessage(text, groupID, V2TIMMessage.V2TIM_PRIORITY_NORMAL, new V2TIMValueCallback<V2TIMMessage>() {    @Override    public void onError(int i, String s) {        // Failed to send bullet screen messages.    }    @Override    public void onSuccess(V2TIMMessage v2TIMMessage) {        // Bullet screen messages sent successfully.    }});// Receive public screen bullet screen messages.V2TIMManager.getInstance().addSimpleMsgListener(new V2TIMSimpleMsgListener() {    @Override    public void onRecvGroupTextMessage(String msgID, String groupID, V2TIMGroupMemberInfo sender, String text) {        Log.i(TAG, sender.getNickName + ": " + text);    }});
```

### Volume Level Callback

RTC Engine can callback the volume levels of the on-mic anchor at a fixed frequency. It is usually used to display sound waves and indicate the speaking anchor.

```
// Enable volume level callback. It is recommended to be enabled immediately after successful room entry.// interval: Callback interval (ms). enable_vad: Whether to enable voice detection.mTRTCCloud.enableAudioVolumeEvaluation(int interval, boolean enable_vad);private class TRTCCloudImplListener extends TRTCCloudListener {    public void onUserVoiceVolume(ArrayList<TRTCCloudDef.TRTCVolumeInfo> userVolumes, int totalVolume) {        super.onUserVoiceVolume(userVolumes, totalVolume);        // userVolumes is used to handle the volume levels of all speaking users, including both local users and remote streaming users.        // totalVolume is used to report the maximum volume value among remote streaming users.        ...        // Display sound waves on the UI based on volume levels.        ...    }}
```

> **Note:**Voice detection only provides local voice detection results. The user's role must be an anchor to make it convenient to remind users to turn on their mics.`userVolumes` is an array. For each element in the array, when userId is oneself, it indicates the volume captured by the local microphone; when userId is others, it indicates the volume of remote users.

### Music and Sound Effect Playback

Playing background music and sound effects is a high-frequency demand in voice chat room scenarios. Below, we will explain the use of and precautions for commonly used background music APIs.

1. Start/stop/pause/resume playback.

```
// Obtain the management class for configuring background music, short sound effects, and voice special effects.TXAudioEffectManager mTXAudioEffectManager = mTRTCCloud.getAudioEffectManager();TXAudioEffectManager.AudioMusicParam param = new TXAudioEffectManager.AudioMusicParam(musicID, musicPath);// Whether to publish the music to remote (otherwise play locally only).param.publish = true;// Whether the playback is from a short sound effect file.param.isShortFile = false;// Start background music playback.mTXAudioEffectManager.startPlayMusic(param);// Stop background music playback.mTXAudioEffectManager.stopPlayMusic(musicID);// Pause background music playback.mTXAudioEffectManager.pausePlayMusic(musicID);// Resume background music playback.mTXAudioEffectManager.resumePlayMusic(musicID);
```

> **Note:**The RTC Engine supports playing multiple music tracks simultaneously, identified uniquely by musicID. To play only one piece of music at a time, stop other music before starting playback. Alternatively, use the same musicID to play different music. In this way, the SDK will stop the previous music first, then play the next music.The RTC Engine supports playing local and network audio files. Use musicPath to input a local absolute path or URL address. Supported formats include MP3/AAC/M4A/WAV.

2. Adjust the ratio of music and voice volume.

```
// Set the local playback volume of a piece of background music.mTXAudioEffectManager.setMusicPlayoutVolume(musicID, volume);// Set the remote playback volume of a specific background music.mTXAudioEffectManager.setMusicPublishVolume(musicID, volume);// Set the local and remote volume of all background music.mTXAudioEffectManager.setAllMusicVolume(volume);// Set the volume of voice capture.mTXAudioEffectManager.setVoiceCaptureVolume(volume);
```

> **Note:**Volume value's normal range is 0-100, with a default of 60 and a maximum setting of 150, but there is a risk of audio clipping.If background music is overwhelming vocals, consider lowering the music playback volume and increasing the voice capture volume.**Mute microphone without muting background music**: Use `setVoiceCaptureVolume(0)` to replace `muteLocalAudio(true)`.

3. Set event callback for music playback.

```
mTXAudioEffectManager.setMusicObserver(mCurPlayMusicId, new TXAudioEffectManager.TXMusicPlayObserver() {    @Override    // Background music starts playing.    public void onStart(int id, int errCode) {        // -4001: Path opening failed.        // -4002: Decoding failed.        // -4003: Invalid URL address.        // -4004: Playback not stopped.        if (errCode < 0) {            // Stop the current music first before replaying after playback failure.            mTXAudioEffectManager.stopPlayMusic(id);        }    }        @Override    // The playback progress of background music.    public void onPlayProgress(int id, long curPtsMs, long durationMs) {        // curPtsMS current playback duration (in milliseconds).        // durationMs: Total duration of the current music (in milliseconds).    }        @Override    // Background music has finished playing.    public void onComplete(int id, int errCode) {        // Playback failure due to weak network during playback will also throw this callback. In this case, errCode < 0.        // Pausing or stopping playback midway will not trigger the onComplete callback.    }});
```

> **Note:**Use this API to set the playback event callback before playing background music to monitor the progress of the music;If the MusicId does not need to be reused, you can execute `setMusicObserver(musicId, null)` after playback is finished to completely release the Observer.

4. Loop playback of background music and sound effects.
- Solution 1: Use the `AudioMusicParam`'s `loopCount` parameter to set the number of loop playbacks.

The value range is from 0 to any positive integer. The default value is 0. 0 means play the music once; 1 means play the music twice; and so on.

```
private void startPlayMusic(int id, String path, int loopCount) {    TXAudioEffectManager.AudioMusicParam param = new TXAudioEffectManager.AudioMusicParam(id, path);    // Whether to publish music to the remote.    param.publish = true;    // Whether the playback is from a short sound effect file.    param.isShortFile = true;    // Set the number of loop playbacks. A negative number means an infinite loop.    param.loopCount = loopCount < 0 ? Integer.MAX_VALUE : loopCount;    mTRTCCloud.getAudioEffectManager().startPlayMusic(param);}
```

> **Note:**Solution 1 will not trigger the `onComplete` callback after each loop playback. It will only be triggered after all the set loop counts have been played.

- Solution 2: Implement loop playback through the "Background music has finished playing" event callback `onComplete`. It is usually used for list loop or single track loop.

```
// The member variable used for indicating whether to loop playback.private boolean loopPlay;private void startPlayMusic(int id, String path) {    TXAudioEffectManager.AudioMusicParam param = new TXAudioEffectManager.AudioMusicParam(id, path);    mTXAudioEffectManager.setMusicObserver(id, new MusicPlayObserver(id, path));    mTXAudioEffectManager.startPlayMusic(param);}private class MusicPlayObserver implements TXAudioEffectManager.TXMusicPlayObserver {    private final int mId;    private final String mPath;        public MusicPlayObserver(int id, String path) {        mId = id;        mPath = path;    }    @Override    public void onStart(int i, int i1) {    }    @Override    public void onPlayProgress(int i, long l, long l1) {    }    @Override    public void onComplete(int i, int i1) {        mTXAudioEffectManager.stopPlayMusic(i);        if (i1 >= 0 && loopPlay) {            // Here, you can replace the ID and Path of the music in the loop playlist.            startPlayMusic(mId, mPath);        }    }}
```

### Mixed Stream Relay and Push Back

1. Send mixed streams to the RTC Engine room.

```
private void startPublishMediaToRoom(String roomId, String userId) {    // Create a TRTCPublishTarget object.    TRTCCloudDef.TRTCPublishTarget target = new TRTCCloudDef.TRTCPublishTarget();    // After mixing, the streams are relayed back to the room.    target.mode = TRTCCloudDef.TRTC_PublishMixStream_ToRoom;    target.mixStreamIdentity.strRoomId = roomId;    // Mixed-stream robot's user ID, which should not be a duplicate of the user ID of any other user in the room.    target.mixStreamIdentity.userId = userId + MIX_ROBOT;    // Set the encoding parameters of the transcoded audio streams (which can be customized).    TRTCCloudDef.TRTCStreamEncoderParam trtcStreamEncoderParam = new TRTCCloudDef.TRTCStreamEncoderParam();    trtcStreamEncoderParam.audioEncodedChannelNum = 2;    trtcStreamEncoderParam.audioEncodedKbps = 64;    trtcStreamEncoderParam.audioEncodedCodecType = 2;    trtcStreamEncoderParam.audioEncodedSampleRate = 48000;    // Set the encoding parameters of the transcoded video streams (which can be ignored for pure audio stream mixing).    trtcStreamEncoderParam.videoEncodedFPS = 15;    trtcStreamEncoderParam.videoEncodedGOP = 3;    trtcStreamEncoderParam.videoEncodedKbps = 30;    trtcStreamEncoderParam.videoEncodedWidth = 64;    trtcStreamEncoderParam.videoEncodedHeight = 64;    // Set audio stream mixing parameters.    TRTCCloudDef.TRTCStreamMixingConfig trtcStreamMixingConfig = new TRTCCloudDef.TRTCStreamMixingConfig();    // By default, leave this field empty. It indicates that all audio in the room will be mixed.    trtcStreamMixingConfig.audioMixUserList = null;    // Configure a video stream mixing template (which can be ignored for pure audio stream mixing).    TRTCCloudDef.TRTCVideoLayout videoLayout = new TRTCCloudDef.TRTCVideoLayout();    trtcStreamMixingConfig.videoLayoutList.add(videoLayout);    // Start pushing back mixed streams.    mTRTCCloud.startPublishMediaStream(target, trtcStreamEncoderParam, trtcStreamMixingConfig);}
```

2. Perform event callback and update, and stop the tasks.
- Task result event callback.

```
private class TRTCCloudImplListener extends TRTCCloudListener {    @Override    public void onStartPublishMediaStream(String taskId, int code, String message, Bundle extraInfo) {        // taskId: When the request is successful, TRTC backend will provide you the taskId of this task in the callback. You can later use this taskId with updatePublishMediaStream and stopPublishMediaStream to update and stop.        // code: Callback result. 0 means success and other values mean failure.    }    @Override    public void onUpdatePublishMediaStream(String taskId, int code, String message, Bundle extraInfo) {        // When you call the media stream publishing API (updatePublishMediaStream), the taskId you provide will be returned to you through this callback. It is used to identify which update request the callback belongs to.        // code: Callback result. 0 means success and other values mean failure.    }    @Override    public void onStopPublishMediaStream(String taskId, int code, String message, Bundle extraInfo) {        // When you call the media stream publishing stopping API (stopPublishMediaStream), the taskId you provide will be returned to you through this callback. It is used to identify which stop request the callback belongs to.        // code: Callback result. 0 means success and other values mean failure.    }}
```

- Update published media streams.

This API sends a command to the RTC Engine server to update the media stream initiated by startPublishMediaStream.

```
// taskId: Task ID returned by the onStartPublishMediaStream callback.// target: For example, add or remove the published CDN URLs.// params: It is recommended to maintain consistency in the encoding output parameters for the media stream to avoid interruptions during playback.// config: Update the list of users involved in mix stream transcoding, such as cross-room PK.mTRTCCloud.updatePublishMediaStream(taskId, target, trtcStreamEncoderParam, trtcStreamMixingConfig);
```

> **Note:**Switching between audio only, audio and video, and video only is not supported within the same task.

- Stop publishing media stream.

This API sends a command to the RTC Engine server to stop the media stream initiated by startPublishMediaStream.

```
// taskId: Task ID returned by the onStartPublishMediaStream callback.mTRTCCloud.stopPublishMediaStream(taskId);
```

> **Note:**If taskId is filled with an empty string, it will stop all media streams initiated by the user through `startPublishMediaStream`. If you have only initiated one media stream or want to stop all media streams initiated by you, this method is recommended.

### Real-Time Network Quality Callback

You can listen to `onNetworkQuality` to real-time monitor the network quality of both local and remote users. This callback is thrown every 2 seconds.

```
private class TRTCCloudImplListener extends TRTCCloudListener {    @Override    public void onNetworkQuality(TRTCCloudDef.TRTCQuality localQuality,                                 ArrayList<TRTCCloudDef.TRTCQuality> remoteQuality) {        // localQuality userId is empty. It represents the local user's network quality evaluation result.        // remoteQuality represents the remote user's network quality evaluation result. The result is affected by both remote and local factors.        switch (localQuality.quality) {            case TRTCCloudDef.TRTC_QUALITY_Excellent:                Log.i(TAG, "The current network is excellent.");                break;            case TRTCCloudDef.TRTC_QUALITY_Good:                Log.i(TAG, "The current network is good.");                break;            case TRTCCloudDef.TRTC_QUALITY_Poor:                Log.i(TAG, "The current network is moderate.");                break;            case TRTCCloudDef.TRTC_QUALITY_Bad:                Log.i(TAG, "The current network is poor.");                break;            case TRTCCloudDef.TRTC_QUALITY_Vbad:                Log.i(TAG, "The current network is very poor.");                break;            case TRTCCloudDef.TRTC_QUALITY_Down:                Log.i(TAG, "The current network does not meet the minimum requirements of TRTC.");                break;            default:                Log.i(TAG, "Undefined");                break;        }    }}
```

### Advanced Permission Control

RTC Engine advanced permission control can be used to set different entry permissions for different rooms, such as advanced VIP rooms. It can also control the permission for audience to speak, such as handling ganchor mics.

Step 1: Enable the advanced permission control switch on the feature configuration page of the application in the [RTC Engine Console](https://console.trtc.io/).

Step 2: Generate privateMapKey on the backend. For sample code, see [privateMapKey computation source code](https://trtc.io/document/35157?product=rtcengine&menulabel=core%20sdk&platform=android#.E6.AD.A5.E9.AA.A42.EF.BC.9A.E5.9C.A8.E6.82.A8.E7.9A.84.E6.9C.8D.E5.8A.A1.E7.AB.AF.E8.AE.A1.E7.AE.97-privatemapkey).

Step 3: Room entry verification & speaking permission verification with PrivateMapKey.

- Room entry verification

```
TRTCCloudDef.TRTCParams mTRTCParams = new TRTCCloudDef.TRTCParams();mTRTCParams.sdkAppId = SDKAPPID;mTRTCParams.userId = mUserId;mTRTCParams.strRoomId = mRoomId;// UserSig obtained from the business backend.mTRTCParams.userSig = getUserSig();// PrivateMapKey obtained from the backend.mTRTCParams.privateMapKey = getPrivateMapKey();mTRTCParams.role = TRTCCloudDef.TRTCRoleAudience;mTRTCCloud.enterRoom(mTRTCParams, TRTCCloudDef.TRTC_APP_SCENE_VOICE_CHATROOM);
```

- Speaking permission verification

```
// Pass in the latest PrivateMapKey obtained from the backend into the role switching API.mTRTCCloud.switchRole(TRTCCloudDef.TRTCRoleAnchor, getPrivateMapKey());
```

## Exception Handling

### Exception Error Handling

When the RTC Engine SDK encounters an unrecoverable error, the error is thrown in the `onError` callback. For details, see [Error Code Tabl](https://trtc.io/document/35130?product=rtcengine&menulabel=core%20sdk&platform=android#336ef58d7636c75f9aa0c87753e08e7c)e.

- UserSig related

UserSig verification failure will lead to room-entering failure. You can use the [UserSig tool](https://console.trtc.io/usersig) for verification.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_INVALID_USER_SIG | -3320 | Room entry parameter UserSig is incorrect. Check if `TRTCParams.userSig `is empty. |
| ERR_TRTC_USER_SIG_CHECK_FAILED | -100018 | UserSig verification failed. Check if the parameter `TRTCParams.userSig` is filled in correctly or has expired. |

- Room entry and exit related

If failed to enter the room, you should first verify the correctness of the room entry parameters. It is essential that the room entry and exit APIs are called in a paired manner. This means that, even in the event of a failed room entry, the room exit API must still be called.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_TRTC_CONNECT_SERVER_TIMEOUT | -3308 | Room entry request timed out. Check if your internet connection is lost or if a VPN is enabled. You may also attempt to switch to 4G for testing. |
| ERR_TRTC_INVALID_SDK_APPID | -3317 | Room entry parameter sdkAppId is incorrect. Check if `TRTCParams.sdkAppId` is empty. |
| ERR_TRTC_INVALID_ROOM_ID | -3318 | Room entry parameter roomId is incorrect. Check if `TRTCParams.roomId` or `TRTCParams.strRoomId` is empty. Note that roomId and strRoomId cannot be used interchangeably. |
| ERR_TRTC_INVALID_USER_ID | -3319 | Room entry parameter userId is incorrect. Check if `TRTCParams.userId` is empty. |
| ERR_TRTC_ENTER_ROOM_REFUSED | -3340 | Room entry request denied. Check if `enterRoom` is called consecutively to enter a room with the same ID. |

- Device related

Errors for relevant monitoring devices. Prompt the user via UI in case of relevant errors.

| Enumeration | Value | Description |
| --- | --- | --- |
| ERR_MIC_START_FAIL | -1302 | Failed to open the mic. For example, if there is an exception for the mic's configuration program (driver) on a Windows or macOS device, you should try disabling then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_SPEAKER_START_FAIL | -1321 | Failed to open the speaker. For example, if there is an exception for the speaker's configuration program (driver) on a Windows or macOS device, you should try disabling then re-enabling the device, restarting the machine, or updating the configuration program. |
| ERR_MIC_OCCUPY | -1319 | The mic is occupied. This occurs when, for example, the user is currently having a call on the mobile device. |

### Exception Exit Handling

1. Be aware of network disconnection and exit the room upon timeout.

You can monitor RTC Engine network disconnection and reconnection events through the following callback.

Upon receiving the `onConnectionLost` callback, display a network disconnection icon on the local seat UI to notify the user. Simultaneously, initiate a local timer. If the `onConnectionRecovery` callback is not received after exceeding the set time threshold, it means the network remains disconnected. Then, locally initiate leaving the seat and room exit process. Pop up a window to inform the user that they have exited the room and the page will be closed. If the disconnection exceeds 90 seconds (default), a timeout room-exit will be triggered, and the RTC Engine server side will remove the user from the room. If the user has an anchor role, other users in the room will receive the `onRemoteUserLeaveRoom` callback.

```
private class TRTCCloudImplListener extends TRTCCloudListener {    @Override    public void onConnectionLost() {        // The connection between the SDK and the cloud has been disconnected.    }    @Override    public void onTryToReconnect() {        // The SDK is attempting to reconnect to the cloud.    }    @Override    public void onConnectionRecovery() {        // The connection between the SDK and the cloud has been restored.    }}
```

2. Automatically leave the voice chat when offline.

Chat user status is divided into online (ONLINE), offline (OFFLINE), and not logged in (UNLOGGED). Among them, the offline status is usually caused by user force-stopping process or abnormal network disruption. You can detect offline mic-connecting audiences through the features of anchors subscribing to the connection status of mic-connecting audiences, thereby removing them.

```
// Anchor subscribes to the connection status of mic-connecting audiences.V2TIMManager.getInstance().subscribeUserStatus(userList, new V2TIMCallback() {    @Override    public void onSuccess() {        // Subscription of user status succeeded.    }    @Override    public void onError(int code, String message) {        // Subscription of user status failed.    }});// Anchor unsubscribes from the connection status of audiences leaving the seat.V2TIMManager.getInstance().unsubscribeUserStatus(userList, new V2TIMCallback() {    @Override    public void onSuccess() {        // Unsubscription of user status succeeded.    }    @Override    public void onError(int code, String message) {        // Unsubscription of user status failed.    }});// User status change notification and processing.V2TIMManager.getInstance().addIMSDKListener(new V2TIMSDKListener() {    @Override    public void onUserStatusChanged(List<V2TIMUserStatus> userStatusList) {        for (V2TIMUserStatus userStatus : userStatusList) {            final String userId = userStatus.getUserID();            int status = userStatus.getStatusType();            if (status == V2TIMUserStatus.V2TIM_USER_STATUS_OFFLINE) {                // Remove an offline-status user.                kickSeat(getSeatIndexFromUserId(userId));            }        }    }});
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c6604f158f0411f084bd5254007c27c5.png)

> **Note:**User status subscription needs to be upgraded to the Professional Edition package. For details, see [Basic Service Details](https://trtc.io/document/34349?product=chat&menulabel=core%20sdk&platform=android).User status subscription needs enabling **User Profile Change Subscription** in the [Chat Console](https://console.trtc.io/chat) in advance. Failure to enable it will result in an error when `subscribeUserStatus` is called.

### Server Removes Users From and Dissolve the Room

1. Remove someone through the server side.

First, call the RTC Engine server-side user removing API [RemoveUser](https://trtc.io/document/34268?product=rtcengine&menulabel=core%20sdk&platform=android) (for integer room IDs) or [RemoveUserByStrRoomId](https://trtc.io/document/39630?product=rtcengine&menulabel=core%20sdk&platform=android) (for string room IDs) to remove the target user from the RTC Engine room. The input example is as follows:

```
https://trtc.tencentcloudapi.com/?Action=RemoveUser&SdkAppId=1400000001&RoomId=1234&UserIds.0=test1&UserIds.1=test2&<Common request parameters>
```

After the user is removed successfully, the target user on the client will receive the `onExitRoom() `callback with `reason` set to 1. You can handle leaving the seat and exiting the Chat group in this callback.

```
// Exit TRTC room event callback.@Overridepublic void onExitRoom(int reason) {    if (reason == 0) {        Log.d(TAG, "Actively call exitRoom to exit the room.");    } else {        // reason 1: Removed from the current room by the server.        // reason 2: The current room is dissolved.        Log.d(TAG, "Being removed from the room by the server, or the current room having been dissolved.");        // Leave the seat.        leaveSeat(seatIndex);        // Exit the Chat group.        quitGroup(groupID, new V2TIMCallback() {});    }}
```

2. Dissolve the room on the server side.

First call the Chat server-side group dissolving API [destroy_group](https://trtc.io/zh/document/34896?product=chat&menulabel=core%20sdk&platform=android) to dissolve the target group. The request URL example is as follows:

```
https://xxxxxx/v4/group_open_http_svc/destroy_group?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

After the group is dissolved, all members within the target group will receive the `onGroupDismissed()` callback on clients. At this point, you can handle operations such as exiting the TRTC room in this callback.

```
// Group dissolved callback.V2TIMManager.getInstance().addGroupListener(new V2TIMGroupListener() {  @Override  public void onGroupDismissed(String groupID, V2TIMGroupMemberInfo opUser) {      // Exit the TRTC room.      mTRTCCloud.stopLocalAudio();      mTRTCCloud.exitRoom();  }});
```

> **Note:**When all users in the room call `exitRoom()` to complete room exit, the RTC Engine room will be automatically dissolved. Of course, you can also call the server-side API [DismissRoom](https://trtc.io/document/34269?product=rtcengine&menulabel=core%20sdk&platform=android) (room ID in integer type) or [DismissRoomByStrRoomId](https://trtc.io/document/39631?product=rtcengine&menulabel=core%20sdk&platform=android) (string room ID) to mandatorily dissolve the RTC Engine room.

### View Live Streaming Room'S Historical Messages Upon Room Entry

By default, using AVChatRoom does not store live streaming room's historical messages. Therefore, when new users enter the live streaming room, they can only see messages sent after their entry. To optimize the experience for new users joining the group, you can configure the number of messages new live streaming group users can pull before joining the group in the console, as shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c67a5bab8f0411f0b321525400e889b2.png)

Pulling historical messages before joining the live streaming group for live streaming group users is the same as pulling historical messages for other groups. The sample code is:

```
V2TIMMessageListGetOption option = new V2TIMMessageListGetOption();option.setGetType(V2TIMMessageListGetOption.V2TIM_GET_CLOUD_OLDER_MSG); // Pull earlier existing messages from the cloud.option.setGetTimeBegin(1640966400);         // Starting from 2022-01-01 00:00:00.option.setGetTimePeriod(1 * 24 * 60 * 60);  // Pull messages of a 24-hour period.option.setCount(Integer.MAX_VALUE);         // Return all messages within the time range.option.setGroupID(#your group id#);          // Pull messages for the group chat.V2TIMManager.getMessageManager().getHistoryMessageList(option, new V2TIMValueCallback<List<V2TIMMessage>>() {    @Override    public void onSuccess(List<V2TIMMessage> v2TIMMessages) {        Log.i("imsdk", "success");    }    @Override    public void onError(int code, String desc) {        Log.i("imsdk", "failure, code:" + code + ", desc:" + desc);    }});
```

> **Note:**This feature is only available to advanced users. It only supports pulling up to 20 historical messages within 24 hours from the group.

### Sense the Mute Status of Anchors When They Enter the Room

Solution 1: Mute all anchors by default when they enter the room, then unmute the corresponding anchor based on the `onUserAudioAvailable(userId, true)` callback.

```
private class TRTCCloudImplListener extends TRTCCloudListener {    @Override    public void onUserAudioAvailable(String userId, boolean available) {        if (available) {            // Unmute the corresponding anchors.        }    }}
```

Solution 2: Store the anchor's mute status in the RTC Engine group attribute. When the audience enters the room, obtain all group attributes and parse the mute status of on-mic anchors.

```
V2TIMManager.getGroupManager().getGroupAttributes(groupID, null, new V2TIMValueCallback<Map<String, String>>() {    @Override    public void onError(int i, String s) {        // Failed to obtain group attributes.    }    @Override    public void onSuccess(Map<String, String> attrMap) {        // Successfully obtained group attributes. Assume the key for storing anchor mute status is muteStatus.        String muteStatus = attrMap.get("muteStatus");        // Parse muteStatus, and obtain the mute status of each on-mic anchor.    }});
```

### Bluetooth Headphone Audio Input/Output Issues

The mobile phone has successfully connected to the Bluetooth headphones, but the audio input or output of the RTC-Engine application still uses the mobile phone's microphone or speaker.

1. If the audio output is working fine with the Bluetooth headphones, but only the audio input is still using the mobile phone's microphone, check the settings for the audio volume type. Only under the call volume mode does it support capturing audio through the microphone on the Bluetooth headphones. For details, see [Audio Management - Audio Quality and Volume Type](#Audio quality and volume type).

```
mTRTCCloud.setSystemVolumeType(TRTCCloudDef.TRTCSystemVolumeTypeVOIP);
```

2. If audio input and output fail to use Bluetooth headphones, check whether Bluetooth permissions are granted in the App permissions. For Android devices, systems earlier than Android 12 require at least the `BLUETOOTH` permission, and Android 12 or later systems require at least the `BLUETOOTH_CONNECT` permission and need to request permissions dynamically in the code.

To configure Bluetooth permissions in the AndroidManifest.xml for compatibility with systems below Android 12, it is recommended to declare permissions as follows:

```
<!--Normal Permission: basic Bluetooth connection permissions--><uses-permission android:name="android.permission.BLUETOOTH" android:maxSdkVersion="30"/><!--Normal Permission: Bluetooth management and scan permissions--><uses-permission android:name="android.permission.BLUETOOTH_ADMIN" android:maxSdkVersion="30" /><!--Runtime Permission: Android 12 Bluetooth permissions for discovering Bluetooth devices--><uses-permission android:name="android.permission.BLUETOOTH_SCAN" /><!--Runtime Permission: Android 12 Bluetooth permissions for making the current device discoverable by other Bluetooth devices--><uses-permission android:name="android.permission.BLUETOOTH_ADVERTISE" /><!--Runtime Permission: Android 12 Bluetooth permissions for communicating with paired Bluetooth devices or checking if Bluetooth is enabled on the current mobile phone--><uses-permission android:name="android.permission.BLUETOOTH_CONNECT" />
```

For Android 12 and above systems, the method to dynamically request the newly added fine-grained Bluetooth permissions, is as follows:

```
private List<String> permissionList = new ArrayList<>();protected void initPermission() {    // Check if the Android SDK version is Android 12 or later.    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.S) {        // Add the required permissions to be requested dynamically according to the needs.        permissionList.add(Manifest.permission.BLUETOOTH_SCAN);        permissionList.add(Manifest.permission.BLUETOOTH_ADVERTISE);        permissionList.add(Manifest.permission.BLUETOOTH_CONNECT);    }    if (permissionList.size() != 0) {        // Dynamically request permissions.        ActivityCompat.requestPermissions(this, permissionList.toArray(new String[0]), REQ_PERMISSION_CODE);    }}
```

### Resource Path Issue for Music Playing

When the RTC Engine SDK API `startPlayMusic` is used to play background music, the music resource `path` parameter path does not support the passing of the path of files in directories for storing application resource files such as assets/raw for Android development. This is because files in these directories are bundled into the APK and are not extracted to the mobile's file system after installation. Currently, only network resource URLs and absolute paths to resource files as external storage of Android devices, and resource files in the application's private directory are supported.

You can work around this issue by copying resource files from the assets directory to either the device external storage or the application private directory beforehand. Sample code is as follows:

```
public static void copyAssetsToFile(Context context, String name) {    // The files directory under the application's directory.    String savePath = ContextCompat.getExternalFilesDirs(context, null)[0].getAbsolutePath();    // The cache directory under the application's directory.    // String savePath = getApplication().getExternalCacheDir().getAbsolutePath();    // The files directory under the application's private storage directory.    // String savePath = getApplication().getFilesDir().getAbsolutePath();    String filename = savePath + "/" + name;    File dir = new File(savePath);    // Create the directory if it does not exist.    if (!dir.exists()) {        dir.mkdir();    }    try {        if (!(new File(filename)).exists()) {            InputStream is = context.getResources().getAssets().open(name);            FileOutputStream fos = new FileOutputStream(filename);            byte[] buffer = new byte[1024];            int count = 0;            while ((count = is.read(buffer)) > 0) {                fos.write(buffer, 0, count);            }            fos.close();            is.close();        }    } catch (Exception e) {        e.printStackTrace();    }}
```

- Application private storage files directory path:`/data/user/0/<package_name>/files/<file_name>`.
- Application external storage files directory path:`/storage/emulated/0/Android/data/<package_name>/files/<file_name>`.
- Application external storage cache directory path:`/storage/emulated/0/Android/data/<package_name>/cache/<file_name>`

> **Note:**If you provide a path that is an external storage path outside of the application's specific directories, on Android 10 and above devices, you may face denial of access to the resource. This is due to Google introducing Partition Storage, a new storage management system. You can temporarily bypass this by adding the following code inside the <application> tag in the AndroidManifest.xml file: `android:requestLegacyExternalStorage="true"`. This attribute only takes effect on applications with targetSdkVersion 29 (Android 10), and applications with a higher version targetSdkVersion are still recommended to use the application's private or external storage paths.RTC Engine SDK 11.5 or later use the Content URI of the Content Provider component to play local music resources on Android devices.On Android 11 and HarmonyOS 3.0 or later, if you cannot access resource files in the external storage directory, you need to request the `MANAGE_EXTERNAL_STORAGE` permission:First, you need to add the following entry in your application's AndroidManifest file.<manifest ...>    <!-- This is the permission itself -->    <uses-permission android:name="android.permission.MANAGE_EXTERNAL_STORAGE" />
>     <application ...>        ...    </application></manifest>Then, guide users to manually grant this permission at the point in your application where it is needed.if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.R) {    if (!Environment.isExternalStorageManager()) {        Intent intent = new Intent(Settings.ACTION_MANAGE_APP_ALL_FILES_ACCESS_PERMISSION);        Uri uri = Uri.fromParts("package", getPackageName(), null);        intent.setData(uri);        startActivity(intent);    }} else {    // For Android versions less than Android 11, you can use the old permissions model    ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE}, REQUEST_CODE);}


---
*Source: [https://trtc.io/document/73428](https://trtc.io/document/73428)*
