# Voice Chat Room

This document guides developers through building a voice chat room application with host broadcasting and audience participation features using the **AtomicXCore** SDK's `LiveListStore` and `LiveSeatStore`.

## Core Concepts

| **Core Concept** | **Type** | **Core Responsibilities & Description** |
| --- | --- | --- |
| `LiveListStore` | `abstract class` | `createLive()`: Start live stream as host.`endLive()`: End live stream as host.`joinLive()`: Audience joins live room.`leaveLive()`: Leave live room. |
| `LiveInfo` | `data class` | `liveID`: Unique room identifier.`seatTemplate`: Layout template. |
| `LiveSeatStore` | `abstract class` | Core seat management class. Manages all seat information and seat-related operations in the room.Provides a real-time seat list data stream via liveSeatState.seatList. |
| `LiveSeatState` | `data class` | Represents the current state of all seats.`seatList`: a StateFlow containing the real-time seat list.`speakingUsers`: users currently speaking and their volume. |
| `SeatInfo` | `data class` | Data model for a single seat. The seat list (seatList) emitted by LiveSeatStore is a list of SeatInfo objects.Key fields:`index`: seat position.`isLocked`: whether the seat is locked.`userInfo`: user information for the seat. If the seat is empty, this field is empty. |
| `SeatUserInfo` | `data class` | Detailed data model for the user occupying a seat. When a user successfully takes a seat, the userInfo field in SeatInfo is populated.Key fields:`userID`: unique user ID.`userName`: user nickname.`avatarURL`: user avatar URL.`microphoneStatus`: microphone status (on/off).`cameraStatus`: camera status (on/off). |

## Prerequisites

### Step 1: Activate the Service

See [Activate Service](https://www.tencentcloud.com/document/product/647/60033) to obtain either the trial or paid version of the SDK.Then, go to [the Console](https://console.trtc.io/app) for application management, and get the following:

- `SDKAppID`: Application identifier (required). Tencent Cloud uses `SDKAppId` for billing and details.
- `SDKSecretKey`: Application secret key, used to initialize the configuration file with secret information.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/018c103bc9f411f09e745254007c27c5.png)

### Step 2: Import AtomicXCore into Your Project

**Install the component**: Add the dependency `implementation 'com.tencent.atomicx:atomicxcore:latest`' to your `build.gradle` file, then perform a **Gradle** **Sync**.

```
dependencies {    implementation 'io.trtc.uikit:atomicx-core:latest.release'    api "io.trtc.uikit:rtc_room_engine:3.4.0.1306"    api "io.trtc.uikit:atomicx-core:3.4.0.1307"    api "com.tencent.liteav:LiteAVSDK_Professional:12.8.0.19279"    api "com.tencent.imsdk:imsdk-plus:8.7.7201"    // Other dependencies...}
```

### Step 3: Implement Login Logic

Call `LoginStore.shared.login` in your project to complete authentication. **This is required before using any functionality of AtomicXCore**.

> **Noteï¼**We recommend calling `LoginStore.shared.login` after your app's own user authentication is successful to ensure clear and consistent login logic.

```
import android.os.Bundleimport androidx.appcompat.app.AppCompatActivityimport io.trtc.tuikit.atomicxcore.api.login.LoginStoreimport io.trtc.tuikit.atomicxcore.api.CompletionHandlerimport android.util.Logclass MainActivity : AppCompatActivity() {    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        LoginStore.shared.login(            this,              // context            1400000001,        // Replace with your SDKAppID            "test_001",        // Replace with your UserID            "xxxxxxxxxxx",     // Replace with your UserSig            object : CompletionHandler {                override fun onSuccess() {                    // Handle login success                    Log.d("Login", "login success")                }                override fun onFailure(code: Int, desc: String) {                    // Handle login failure                    Log.e("Login", "login failed, code: $code, error: $desc")                }            }        )    }}
```

**Login API Parameter Description**

| Parameter | Type | Description |
| --- | --- | --- |
| `sdkAppID` | `Int` | Get this from [TRTC console > Application management](https://console.trtc.io/app). |
| `userID` | `String` | The unique ID for the current user. Must contain only English letters, numbers, hyphens, and underscores. |
| `userSig` | `String` | A ticket for Tencent Cloud authentication. Please note:**Development Environment**: You can use the local `GenerateTestUserSig.genTestSig` function to generate a UserSig or generate a temporary UserSig via the [UserSig Generation Tool](https://console.trtc.io/usersig).**Production Environment**: To prevent key leakage, you must use a server-side method to generate UserSig. For details, see [Generating UserSig on the Server](https://www.tencentcloud.com/document/product/647/35166).For more information, see [How to Calculate and Use UserSig](https://www.tencentcloud.com/document/product/647/35166). |

## Building a Basic Voice Chat Room

### Step 1: Host Room Creation

Follow the steps below to quickly set up a voice chat room as the host.

#### **1. Initialize the Seat**`Store`

In your host `Activity`, create a `LiveSeatStore` instance. Observe changes in `liveSeatState.seatList` to get real-time mic seat data and update your UI.

```
import android.os.Bundleimport android.util.Logimport androidx.appcompat.app.AppCompatActivityimport io.trtc.tuikit.atomicxcore.api.device.DeviceStoreimport io.trtc.tuikit.atomicxcore.api.live.LiveListStoreimport io.trtc.tuikit.atomicxcore.api.live.LiveSeatStoreimport kotlinx.coroutines.CoroutineScopeimport kotlinx.coroutines.Dispatchersimport kotlinx.coroutines.launch// YourHostActivity represents your Host Activityclass YourHostActivity : AppCompatActivity() {    private lateinit var liveListStore: LiveListStore    private lateinit var liveSeatStore: LiveSeatStore    private lateinit var deviceStore: DeviceStore    private val liveID = "test_voice_room_001"    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        setContentView(R.layout.activity_host) // Assume you have your own layout        // 1. Initialize Stores        liveListStore = LiveListStore.shared()        liveSeatStore = LiveSeatStore.create(liveID)        deviceStore = DeviceStore.shared()        // 2. Listen for mic seat list changes        observeSeatList()    }    private fun observeSeatList() {         // Listen for seatList changes and update your mic seat UI         CoroutineScope(Dispatchers.Main).launch {             liveSeatStore.liveSeatState.seatList.collect { seatInfoList ->                 // Render your mic seat UI here based on seatInfoList                 // Example: updateMicSeatView(seatInfoList)                 Log.d("HostActivity", "Seat list updated: ${seatInfoList.size} seats")             }         }    }}
```

#### **2.**Turn On Microphone

Turn On Microphone by calling the `openLocalMicrophone` method from `DeviceStore`:

```
import androidx.appcompat.app.AppCompatActivityimport io.trtc.tuikit.atomicxcore.api.device.DeviceStoreclass YourHostActivity : AppCompatActivity() {    // ... Other code ...    private fun openDevices() {        // 1. Turn on the microphone        DeviceStore.shared().openLocalMicrophone(completion = null)    }}
```

#### **3. Start Voice Chat**

Start the live voice chat by calling the `createLive` method of `LiveListStore`:

```
import android.os.Bundleimport android.util.Logimport androidx.appcompat.app.AppCompatActivityimport io.trtc.tuikit.atomicxcore.api.live.LiveInfoimport io.trtc.tuikit.atomicxcore.api.live.LiveInfoCompletionHandlerimport io.trtc.tuikit.atomicxcore.api.live.TakeSeatModeclass YourHostActivity : AppCompatActivity() {    // ... Other code ...    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        // ... Other code ...        // Start voice chat        startLive()    }    private fun startLive() {        val liveInfo = LiveInfo().apply {            // 1. Set room id            liveID = this@YourHostActivity.liveID            // 2. Set room name            liveName = "test voice room"            // 3. Set the live streaming template to the voice chat room template, with 9 seat.            seatTemplate = SeatLayoutTemplate.AudioSalon(seatCount = 9)            // 4. Set mic-taking mode, e.g., apply to take mic            seatMode = TakeSeatMode.APPLY        }        // 8. Call createLive to start the stream        liveListStore.createLive(liveInfo, object : LiveInfoCompletionHandler {            override fun onFailure(code: Int, desc: String) {                Log.e("Live", "Response startLive onError: $desc")            }            override fun onSuccess(liveInfo: LiveInfo) {                Log.d("Live", "Response startLive onSuccess")                // After successful creation, the Host is on the mic by default, now you can call unmuteMicrophone                liveSeatStore.unmuteMicrophone(null)            }        })    }}
```

**LiveInfo Parameter Description**

| **Parameter Name** | **Type** | **Required** | **Description** |
| --- | --- | --- | --- |
| `liveID` | `String` | Required | Unique identifier for the live room |
| `liveName` | `String` | Optional | Title of the live room |
| `notice` | `String` | Optional | Announcement information for the live room |
| `isMessageDisable` | `Boolean` | Optional | Mute status (`true`: muted, `false`: not muted) |
| `isPublicVisible` | `Boolean` | Optional | Public visibility (`true`: visible, `false`: hidden) |
| `seatMode` | [TakeSeatMode](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-take-seat-mode/index.html) | Optional | Mic seat mode (`FREE`: free to take seat, `APPLY`: apply to take seat) |
| `seatTemplate` | `SeatLayoutTemplate` | Required | Mic seat layout template ID |
| `coverURL` | `String` | Optional | Cover image URL for the live room |
| `backgroundURL` | `String` | Optional | Background image URL for the live room |
| `categoryList` | `List<Int>` | Optional | Category tag list for the live room |
| `activityStatus` | `Int` | Optional | Live activity status |

#### **4. Build the Mic Seat UI**

> **Noteï¼**For the complete business logic of mic seat UI effects, refer to the open-source [SeatGridView.kt](https://github.com/Tencent-RTC/TUILiveKit/blob/main/Android/tuilivekit/src/main/java/com/trtc/uikit/livekit/voiceroomcore/SeatGridView.kt) in the TUILiveKit project.

Use the `LiveSeatStore` instance to observe changes in `liveSeatState.seatList` and update your UI in real time. In your Activity (such as `YourAnchorActivity` or `YourAudienceActivity`), observe the data as follows:

```
import android.os.Bundleimport android.util.Logimport androidx.appcompat.app.AppCompatActivityimport kotlinx.coroutines.CoroutineScopeimport kotlinx.coroutines.Dispatchersimport kotlinx.coroutines.launchclass YourHostActivity : AppCompatActivity() {    // ... Other code ...    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        // ... Other code ...        // Listen for seatList changes        observeSeatList()    }    private fun observeSeatList() {        // Listen for seatList changes and update your mic seat UI        CoroutineScope(Dispatchers.Main).launch {            liveSeatStore.liveSeatState.seatList.collect { seatInfoList ->                // seatInfoList is the latest mic seat list (List<SeatInfo>), render your mic seat UI here based on seatInfoList                Log.d("HostActivity", "Seat list updated: ${seatInfoList.size} seats")            }        }    }}
```

#### **5. End Voice Chat**

To end the voice chat, call the `endLive` method of `LiveListStore`. The SDK will handle stopping the stream and destroying the room.

```
import android.util.Logimport androidx.appcompat.app.AppCompatActivityimport com.tencent.cloud.tuikit.engine.extension.TUILiveListManagerimport io.trtc.tuikit.atomicxcore.api.live.StopLiveCompletionHandlerclass YourHostActivity : AppCompatActivity() {    // ... Other code ...    // End voice chat    private fun stopLive() {        liveListStore.endLive(object : StopLiveCompletionHandler {            override fun onSuccess(statisticsData: TUILiveListManager.LiveStatisticsData) {                Log.d("Live", "endLive success, duration: ${statisticsData.liveDuration}")            }            override fun onFailure(code: Int, desc: String) {                Log.e("Live", "endLive error: $desc")            }        })    }    // Ensure this is also called when the Activity is destroyed    override fun onDestroy() {        super.onDestroy()        stopLive()        Log.d("Live", "YourHostActivity onDestroy")    }}
```

### Step 2: Audience Joins the Voice Chat Room

Follow these steps to allow audience members to join the voice chat room.

#### **1. Initialize the Mic Seat Store**

In your audience `Activity`, create a `LiveSeatStore` instance and observe changes in `liveSeatState.seatList` to update the mic seat UI.

```
import io.trtc.tuikit.atomicxcore.api.live.LiveListStoreimport io.trtc.tuikit.atomicxcore.api.live.LiveSeatStoreimport android.os.Bundleimport androidx.appcompat.app.AppCompatActivityimport kotlinx.coroutines.CoroutineScopeimport kotlinx.coroutines.Dispatchersimport kotlinx.coroutines.launchimport android.util.Log// YourAudienceActivity represents your Audience Activityclass YourAudienceActivity : AppCompatActivity() {    private lateinit var liveListStore: LiveListStore    private lateinit var liveSeatStore: LiveSeatStore    private val liveID = "test_voice_room_001" // Ensure liveID matches the Host's    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        setContentView(R.layout.activity_audience) // Assume you have your own layout        // 1. Initialize Stores        liveListStore = LiveListStore.shared()        liveSeatStore = LiveSeatStore.create(liveID)        // 2. Listen for mic seat list changes        observeSeatList()    }    private fun observeSeatList() {         // 3. Listen for seatList changes and update your mic seat UI         CoroutineScope(Dispatchers.Main).launch {             liveSeatStore.liveSeatState.seatList.collect { seatInfoList ->                 // Render your mic seat UI here based on seatInfoList                 // Example: updateMicSeatView(seatInfoList)                 Log.d("AudienceActivity", "Seat list updated: ${seatInfoList.size} seats")             }         }    }}
```

#### **2. Join Voice Chat Room**

Join the voice chat room by calling the `joinLive` method of `LiveListStore`:

```
import android.os.Bundleimport androidx.appcompat.app.AppCompatActivityimport android.util.Logimport io.trtc.tuikit.atomicxcore.api.live.LiveInfoimport io.trtc.tuikit.atomicxcore.api.live.LiveInfoCompletionHandler// YourAudienceActivity represents your Audience Activityclass YourAudienceActivity : AppCompatActivity() {        // ... Other code ...    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        setContentView(R.layout.activity_audience) // Assume you have your own layout        // ... Other code ...                // Enter voice chat room        joinLive()    }    private fun joinLive() {        // 1. Call joinLive to enter the voice chat room        liveListStore.joinLive(liveID, object : LiveInfoCompletionHandler {            override fun onSuccess(liveInfo: LiveInfo) {                Log.d("Live", "joinLive success")            }            override fun onFailure(code: Int, desc: String) {                Log.e("Live", "joinLive error: $desc")            }        })    }}
```

#### **3. Build the Mic Seat UI**

The process for building the mic seat UI as an audience member is the same as for the host. Refer to the host [Build the Mic Seat UI](#9a917c47-816f-4930-81b1-d35ee01c519d).

#### **4. Leave the Voice Chat Room**

When an audience member leaves the voice chat room, call the `leaveLive` method of `LiveListStore`:

```
import android.util.Logimport androidx.appcompat.app.AppCompatActivityimport io.trtc.tuikit.atomicxcore.api.CompletionHandler// YourAudienceActivity represents your Audience Activityclass YourAudienceActivity : AppCompatActivity() {    // ... Other code ...    private fun leaveLive() {        liveListStore.leaveLive(object : CompletionHandler {            override fun onSuccess() {                Log.d("Live", "leaveLive success")            }            override fun onFailure(code: Int, desc: String) {                Log.e("Live", "leaveLive error: $desc")            }        })    }    // Ensure this is also called when the Activity is destroyed    override fun onDestroy() {        super.onDestroy()        leaveLive()        Log.d("Live", "YourAudienceActivity onDestroy")    }}
```

### Run and Test

After completing the steps above, you will have a basic voice chat live streaming setup. For more advanced features, see the "Enrich Voice Chat Room Scenarios" section.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/159d41cdc9f411f0b011525400bf7822.png)

## Advanced Features

### **Implementing Speaking Wave Animation for Mic Seat Users**

In voice chat rooms, it is common to show a wave animation on the avatar of users who are speaking, so everyone can see who is currently talking. `LiveSeatStore` provides a `speakingUsers` data stream for this purpose.

#### Example

#### ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/159f07ffc9f411f09e745254007c27c5.gif)

#### Implementation

> **Noteï¼**For a complete implementation of the speaking wave animation, refer to [SeatGridView.kt](https://github.com/Tencent-RTC/TUILiveKit/blob/main/Android/tuilivekit/src/main/java/com/trtc/uikit/livekit/voiceroomcore/SeatGridView.kt) in the open-source TUILiveKit project.

In `YourAnchorActivity`, observe changes in `speakingUsers` and update the UI to reflect the speaking status:

```
import android.os.Bundleimport android.util.Logimport androidx.appcompat.app.AppCompatActivityimport kotlinx.coroutines.CoroutineScopeimport kotlinx.coroutines.Dispatchersimport kotlinx.coroutines.launch// In YourHostActivity or YourAudienceActivityclass YourHostActivity : AppCompatActivity() {    // ... (omitting other code) ...    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        // ... (omitting other code) ...        // Listen for speakingUsers changes        observeSpeakingUsersState()    }    private fun observeSpeakingUsersState() {        // Listen for speakingUsers changes and update the "currently speaking" status        CoroutineScope(Dispatchers.Main).launch {            liveSeatStore.liveSeatState.speakingUsers.collect { speakingUserSet ->                // Pass the set of "currently speaking" user IDs to the UI, update UI state                Log.d("HostActivity", "Speaking users updated: ${speakingUserSet.size} users")            }        }    }}
```

### Synchronizing Custom State in Live Streaming Room

In Live Streaming Room, hosts may need to synchronize custom information with all participants, such as the current room topic or background music. The `metaData` feature of `LiveListStore` supports this use case.

#### Implementation

1. On the host side, set custom information using the `updateLiveMetaData` API. `AtomicXCore` synchronizes these changes in real time to all participants.
2. On the audience side, subscribe to `LiveListState.currentLive` and listen for changes in `metaData`. When a relevant key is updated, parse its value and update your business logic.

#### Code Example

```
import io.trtc.tuikit.atomicxcore.api.LiveListStoreimport io.trtc.tuikit.atomicxcore.api.CompletionHandlerimport com.google.gson.Gsonimport io.trtc.tuikit.atomicxcore.api.MetaDataCompletionHandlerimport io.trtc.tuikit.atomicxcore.api.LiveListStore// 1. Define a background music model (using data class)data class MusicModel(    val musicId: String,    val musicName: String)// 2. Host side: Add a method to push background music in your Host business logicfun updateBackgroundMusic(music: MusicModel) {    val gson = Gson()    val jsonString = gson.toJson(music) ?: ""    // The metaData to be updated    val metaData = hashMapOf("music_info" to jsonString)    // Update metaData    LiveListStore.shared()        .updateLiveMetaData(            metaData,            object : CompletionHandler {                override fun onSuccess() {                    print("Background music ${music.musicName} pushed successfully")                }                override fun onFailure(code: Int, desc: String) {                    print("Failed to push background music: $desc")                }            }        )}// 3. Audience side: Add a method to listen for background music changes in your Audience business logicprivate fun subscribeToDataUpdates() {    CoroutineScope(Dispatchers.Main).launch {        LiveListStore.shared()            .liveState            .currentLive            .map { it.metaData }            .collect {                val musicInfo = it["music_info"]                // Refresh business state, e.g., play new background music            }    }}
```

## Enrich Voice Chat Room Scenarios

After implementing the basic voice chat room, you can add more interactive features by referring to the following guides:

| **Feature** | **Feature Description** | **Feature Stores** | **Implementation Guide** |
| --- | --- | --- | --- |
| **Enable Audience to Take Mic Seat** | Audience can apply to take a mic seat and interact with the host in real time. | [CoGuestStore](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/index.html) | [Implementation](https://www.tencentcloud.com/document/product/647/74683) |
| **Host Cross-Room Connection & PK** | Hosts from different rooms can connect for interaction or PK. | [CoHostStore](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/index.html)[BattleStore](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-battle-store/index.html) | [Implementation](https://www.tencentcloud.com/document/product/647/74689) |
| **Add Barrage Chat** | Members in the room can send and receive real-time text messages. | [BarrageStore](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.barrage/-barrage-store/index.html) | [Implementation](https://www.tencentcloud.com/document/product/647/74693) |
| **Build Gift System** | Audience can send virtual gifts to hosts to increase engagement and fun. | [GiftStore](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.gift/-gift-store/index.html) | [Implementation](https://www.tencentcloud.com/document/product/647/74691) |

## API Documentation

| **Store/Component** | **Feature Description** | **API Documentation** |
| --- | --- | --- |
| `LiveListStore` | Manages the full lifecycle of live rooms: create, join, leave, destroy rooms; query room list; modify live info (name, announcement, etc.); listen to live status (such as being kicked out, ended). | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/index.html) |
| `LiveSeatStore` | Core mic seat management: manage mic seat list, user status, seat operations (take seat, leave seat, kick, lock, toggle microphone/camera, etc.), listen to mic seat events. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/index.html) |
| `DeviceStore` | Audio/video device control: microphone (toggle/volume), camera (toggle/switch/quality), screen sharing, real-time device status monitoring. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/index.html) |
| `CoGuestStore` | Audience co-host management: co-host application/invitation/approval/rejection, member permission control (microphone/camera), status synchronization. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/index.html) |
| `CoHostStore` | Host cross-room connection: supports multiple layout templates (dynamic grid, etc.), initiate/accept/reject connection, manage co-host interaction. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/index.html) |
| `BattleStore` | Host PK battle: initiate PK (set duration/opponent), manage PK status (start/end), synchronize scores, listen to battle results. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-battle-store/index.html) |
| `GiftStore` | Gift interaction: get gift list, send/receive gifts, listen to gift events (including sender and gift details). | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.gift/-gift-store/index.html) |
| `BarrageStore` | Bullet chat feature: send text/custom barrage, maintain barrage list, real-time barrage status monitoring. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.barrage/-barrage-store/index.html) |
| `LikeStore` | Like interaction: send likes, listen to like events, synchronize total like count. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-like-store/index.html) |
| `LiveAudienceStore` | Audience management: get real-time audience list (ID/name/avatar), count audience number, listen to audience join/leave events. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-store/index.html) |
| `AudioEffectStore` | Audio effects: voice changer (child/male), reverb (KTV, etc.), ear monitor adjustment, real-time effect switching. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-store/index.html) |

## FAQs

### Why is there no sound after the audience calls joinLive?

- **Check device permissions:** Ensure the app has system permission to use the microphone.
- **Check the host:** Confirm the host has called `DeviceStore.shared().openLocalMicrophone(null)` to enable the microphone.
- **Check the network:** Ensure the device's network connection is stable.

### Why is the mic seat list not displayed or not updating?

- **Check store initialization:** Make sure you have created the `LiveSeatStore` instance with the same `liveID` before calling `createLive` or `joinLive` (`LiveSeatStore.create(liveID)`).
- **Check data observation:** Ensure you are observing the `liveSeatStore.liveSeatState.seatList` data stream.
- **Check API calls:** Confirm that `createLive` (host) or `joinLive` (audience) was successfully called (check the `onSuccess` callback).


---
*Source: [https://trtc.io/document/74681](https://trtc.io/document/74681)*
