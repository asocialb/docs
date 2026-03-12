# Live Battles

`AtomicXCore` provides two core modules: `CoHostStore` for **cross-room connections** and `BattleStore` for **PK battles**. This guide explains how to integrate these modules to enable connection and PK features in a voice chat room application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b488f1dc9fc11f087ad52540099c741.png)

## Core Concepts

| **Core Concept** | **Type** | **Core Responsibilities & Description** |
| --- | --- | --- |
| **CoHostStore** | `abstract class` | Manages the lifecycle of host-to-host connections. Provides connection APIs such as `requestHostConnection` and `acceptHostConnection`. |
| **BattleStore** | `abstract class` | Handles PK battle signaling and state management across rooms, including PK status tracking. |
| **LiveListStore** | `abstract class` | Fetches the list of active live rooms (`fetchLiveList`). Use this to discover rooms available for connection. |
| **LiveSeatStore** | `abstract class` | Manages seat states within a room, including cross-room seats during connection. Tracks user join/leave events and microphone status. |
| **CoHostLayoutTemplate** | `enum` | Defines seat layout templates for cross-room connections, e.g., `HOST_STATIC_VOICE_6V6`. |
| **BattleConfig** | `data` | Configures PK battle details such as duration (`duration`) and whether a secondary response is required (`needResponse`). |

## Prerequisites

Integrate the [Quick Start](https://www.tencentcloud.com/document/product/647/74681) and ensure you have implemented both **Host Start Live** and **Audience Watch** features.

## Host Initiates a Connection

### Step 1: Fetch Active Streamers

To initiate a connection or PK, the host must retrieve the current list of live rooms and select a target host.

**Implementation:** Call `LiveListStore.shared().fetchLiveList`.

> **Noteï¼**If the target room is missing from the returned list, verify that isPublicVisible in TUILiveInfo is set to true when starting the stream.This API supports pagination. Use the cursor from the onSuccess callback for subsequent fetches. An empty cursor indicates all rooms have been fetched.For optimal performance, set pageCount to 20.

```
import io.trtc.tuikit.atomicxcore.api.live.LiveListStoreimport io.trtc.tuikit.atomicxcore.api.CompletionHandlerfun fetchLiveListForCoHost() {    val cursor = "" // Initial fetch    val pageCount = 20    LiveListStore.shared().fetchLiveList(cursor, pageCount, object : CompletionHandler {        override fun onSuccess() {            println("Live room list fetched successfully")            // Update your invitation panel with LiveListStore.liveState.liveList            // inviteAdapter.submitList(LiveListStore.liveState.liveList)        }        override fun onFailure(code: Int, desc: String) {            println("Failed to fetch live room list: $code")        }    })}
```

### Step 2: Send a Co-hosting Invitation

When a host selects another host, use `CoHostStore.requestHostConnection` to send a connection invitation.

> **Noteï¼**AtomicXCore supports up to **9** interconnected rooms, each with up to **50** users.This interface supports batch invitations, which you can use continuously; to check if an invitation to a single live room was successful, you need to listen for the `onSuccess` callback.The API supports extension fields. These are delivered to the target host via `onCoHostRequestReceived` in `CoHostListener`. Use this to pass business logic such as "start PK immediately".

```
import io.trtc.tuikit.atomicxcore.api.live.CoHostLayoutTemplateimport io.trtc.tuikit.atomicxcore.api.CompletionHandlerval targetHostLiveID = "target_host_room_id"val layoutTemplate = CoHostLayoutTemplate.HOST_STATIC_VOICE_6V6val timeout = 10 // secondsval extraInfo = "" // e.g., direct PK flagcoHostStore.requestHostConnection(    targetHostLiveID,    layoutTemplate,    timeout,    extraInfo,    object : CompletionHandler {        override fun onSuccess() {            println("Connection request sent. Awaiting response...")        }        override fun onFailure(code: Int, desc: String) {            println("Failed to send invitation: $desc")        }    })
```

### Step 3: Target Streamer Receives Invitation

The target host receives the invitation via `onCoHostRequestReceived` in `CoHostListener`. Display a UI prompt such as "Host invites you to join the connection".

```
private val coHostListener = object : CoHostListener() {    override fun onCoHostRequestReceived(        inviter: SeatUserInfo, extensionInfo: String    ){        // Show invitation dialog    }}
```

### Step 4: Target Host Accepts or Rejects Invitation

In the invitation UI, the target host can accept or reject. Call `acceptHostConnection` or `rejectHostConnection` as appropriate.

```
private val coHostStore = CoHostStore.create(liveID)private val coHostListener = object : CoHostListener() {    override fun onCoHostRequestReceived(        inviter: SeatUserInfo, extensionInfo: String    ){        // Accept connection        coHostStore.acceptHostConnection(fromHostLiveID, null)        // Or reject        // coHostStore.rejectHostConnection(fromHostLiveID, null)    }}
```

### Step 5: Render Co-hosting UI Layout

After connection is established, listen to `coHostStatus` in `CoHostStore.coHostState` and `seatList` in `LiveSeatStore.liveSeatState` to update the seat layout dynamically.

```
import io.trtc.tuikit.atomicxcore.api.live.CoHostStatusimport io.trtc.tuikit.atomicxcore.api.live.LiveSeatStoreimport io.trtc.tuikit.atomicxcore.api.live.SeatInfoimport kotlinx.coroutines.flow.collectprivate val liveSeatStore = LiveSeatStore.create(liveID)coHostStore.coHostState.coHostStatus.collect { status ->    if (status == CoHostStatus.CONNECTED) {        // Render connection layout (e.g., 6v6)    }}liveSeatStore.liveSeatState.seatList.collect { seatList: List<SeatInfo> ->    // Update avatars, mute status, etc.    // Use seatInfo.userInfo.liveID to distinguish local/remote users.    // Use seatInfo.userInfo.microphoneStatus for mute icon.}
```

### Step 6: Invite Additional Streamers During Co-hosting

You can invite more hosts even after a connection is established by calling `requestHostConnection` again.

```
import io.trtc.tuikit.atomicxcore.api.live.CoHostLayoutTemplateimport io.trtc.tuikit.atomicxcore.api.CompletionHandlerval targetHostLiveID = "target_host_room_id"val layoutTemplate = CoHostLayoutTemplate.HOST_STATIC_VOICE_6V6val timeout = 10val extraInfo = ""coHostStore.requestHostConnection(    targetHostLiveID,    layoutTemplate,    timeout,    extraInfo,    object : CompletionHandler {        override fun onSuccess() {            println("Connection request sent. Awaiting response...")        }        override fun onFailure(code: Int, desc: String) {            println("Failed to send invitation: $desc")        }    })
```

### Step 7: Exit Co-hosting

To disconnect, call `CoHostStore.exitHostConnection`. Remaining hosts should update their seat layout accordingly.

```
public void onExitButtonClicked() {    val coHostStore = CoHostStore.create(liveInfo.liveID)    coHostStore.exitHostConnection(object : CompletionHandler{        override fun onSuccess(){            // Handle successful exit        }        override fun onFailure(code: Int, desc: String){            // Handle error        }    })}
```

## PK Streamer Initiates a PK

BattleStreamers can start PK battles using two main flows, depending on the room state before PK begins:

| **PK Mode** | **Room State (Before PK)** | **Room State (After PK)** |
| --- | --- | --- |
| Scenario 1: PK after connection | Both sides connected | Returns to connection state |
| Scenario 2: Connection with PK mode | Both sides not connected | Returns to connection state |

### Scenario 1: PK After Connection

AtomicXCore enables hosts to start a timed PK battle once connected. Typical UI flow:

1. Send connection invitation; invited host accepts.
2. Hosts click PK to start a timed battle. Winner is determined by gifts received.
3. Target host receives a PK prompt and can accept.
4. UI enters PK mode and displays a progress bar (based on gifts, likes, etc.).
5. When PK ends, winner/loser is displayed and a punishment period begins.
6. After PK, state returns to connection mode.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b475a6ec9fc11f087ad52540099c741.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4ad26a5ec9fc11f0aedb525400454e06.png)

#### Step 1: Initiate PK Invitation

To start a PK battle among connected hosts, use `BattleStore.requestBattle`. Configure PK duration, whether a response is required, and any extension info.

> **Noteï¼**Default PK duration is 5 minutes if not set in `BattleConfig`.To start PK immediately, set `needResponse` to `false`.If `needResponse` is `false`, set `timeout` to 0.If the target host does not respond within the timeout, both hosts receive `onBattleRequestTimeout`. PK can be retried.

```
val targetUserID = "target_host_user_id"val config = BattleConfig(    duration = 30, // seconds    needResponse = true,    extensionInfo = "")battleStore.requestBattle(    config,    listOf(targetUserID),    timeout = 10, // seconds    completion = null)
```

#### Step 2: Target Streamer Receives PK Invitation

The target host receives the PK request via `onBattleRequestReceived` in `BattleListener`. Use `needResponse` in `battleInfo.config` to determine whether to prompt the user.

- If `needResponse` is false, enter PK state directly.
- If true, show a dialog and enter PK on acceptance.

```
private val mBattleListener: BattleListener = object : BattleListener() {    override fun onBattleRequestReceived(        battleId: String,        inviter: SeatUserInfo,        invitee: SeatUserInfo,    ) {        super.onBattleRequestReceived(battleInfo, inviter, invitee)        val userId = inviter.userId        val userName = inviter.userName        val needResponse = battleInfo.config.needResponse        // Show PK prompt if needed    }}
```

#### Step 3: Enter PK State

When `onBattleStarted` is triggered in `BattleListener`, render the PK progress bar in your UI.

- If `needResponse` is `false`, PK starts automatically.
- If `needResponse` is `true`, PK starts after all invited hosts call `acceptBattle`.
- Hosts joining PK receive `onUserJoinBattle`.
- All PK participants receive `onBattleStarted`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b859b66c9fc11f09e745254007c27c5.png)

#### Step 4: End PK State

PK ends either when the duration expires or when all hosts leave.

1. **PK Time Expires:** All hosts receive `onBattleEnded`.
2. **Manual Exit:** Any host can call `exitBattle`. Remaining hosts stay in PK and receive `onUserExitBattle`. If all hosts exit, PK ends early.

```
val battleStore: BattleStore = BattleStore.create(liveID)battleID = battleStore.battleState.currentBattleInfo.value?.battleIDbattleStore.exitBattle(battleID, null)
```

After PK ends, use `onBattleEnded` to display results and determine winner/loser.

> **Noteï¼**After PK ends, the session returns to cross-room co-hosting.To end co-hosting after PK, call `exitHostConnection`.

### Scenario 2: Co-hosting with PK Mode

**AtomicXCore** supports direct PK initiation during a live session, without prior co-hosting. After PK ends, the session returns to the live room state.

1. Streamer clicks `PK`, opens a panel with active streamers (see Step 1 above).
2. Selects a streamer and sends a PK invitation.
3. Target streamer receives the invitation and can accept or reject.
4. Upon acceptance, PK starts automatically. Points are accumulated via gifts or likes.
5. After PK ends, the winner is determined by points.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b47decec9fc11f0a4a55254001c06ec.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4ad25df0c9fc11f087ad52540099c741.png)

> **Noteï¼**This workflow requires both CoHostStore and BattleStore, with `needResponse` in BattleConfig set to `false`.

#### Step 1: Send Co-hosting Request

This step is similar to Steps 1 and 2 in "Host Initiates a Connection". Use the `extensionInfo` field in `requestHostConnection` to indicate PK mode for UI differentiation.

- If `extraInfo` is `{"withPK:true"}`, show "Host invites you to PK".
- If `extraInfo` is `{"withPK:false"}`, show "Host invites you to join a cross-room connection".

```
import io.trtc.tuikit.atomicxcore.api.live.CoHostLayoutTemplateimport io.trtc.tuikit.atomicxcore.api.CompletionHandlerval targetHostLiveID = "target_host_room_id"val layoutTemplate = CoHostLayoutTemplate.HOST_STATIC_VOICE_6V6val timeout = 10val extraInfo = "withPK:true"coHostStore.requestHostConnection(    targetHostLiveID,    layoutTemplate,    timeout,    extraInfo,    object : CompletionHandler {        override fun onSuccess() {            println("Connection request sent. Awaiting response...")        }        override fun onFailure(code: Int, desc: String) {            println("Failed to send invitation: $desc")        }    })
```

#### Step 2: Target Streamer Receives Request and Confirms

Target host receives `onCoHostRequestReceived` and can accept or reject.

```
private val coHostListener = object : CoHostListener() {    override fun onCoHostRequestReceived(        inviter: SeatUserInfo, extensionInfo: String    ){        // Show invitation dialog    }}
```

Accept or reject using:

```
private val coHostStore = CoHostStore.create(liveID)private val coHostListener = object : CoHostListener() {    override fun onCoHostRequestReceived(        inviter: SeatUserInfo, extensionInfo: String    ){        coHostStore.acceptHostConnection(fromHostLiveID, null)        // Or reject        // coHostStore.rejectHostConnection(fromHostLiveID, null)    }}
```

#### Step 3: Initiate PK Automatically

When the target streamer accepts, immediately call `BattleStore.requestBattle` with `needResponse: false` to start PK.

```
override fun onCoHostRequestAccepted(invitee: SeatUserInfo) {        coHostStore.acceptHostConnection(invitee.liveID, null)        val directPKConfig = BattleConfig(            duration = 30,             needResponse = false,             extensionInfo = ""        )        battleStore.requestBattle(            directPKConfig,            listOf(invitee.userID),             timeout = 0,            completion = null         )    }
```

#### Step 4: Enter PK State

This step is the same as [Enter PK State](#166c6a33-f068-4501-898a-6ef07c9b9b21).

## PK Score Update and Win/Loss Determination

### Updating PK Score via REST API

In typical**live host PK scenarios,** the value of gifts received by the host is linked to the PK score (for example, when a viewer sends a "Rocket" gift, the host's PK score increases by 500 points). You can implement real-time PK score updates using our REST API.

> **Noteï¼**The PK score system in the LiveKit backend uses pure numeric calculation and accumulation. You must calculate the PK score according to your own business logic before calling the update API. See the following PK score calculation examples:Gift TypeScore Calculation RuleExampleBasic GiftGift value Ã 510 RMB gift â 50 pointsIntermediate GiftGift value Ã 850 RMB gift â 400 pointsAdvanced GiftGift value Ã 12100 RMB gift â 1200 pointsSpecial Effect GiftFixed high score520 RMB gift â 1314 points

#### REST API Call Flow

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1cd5aeb2c9fd11f0a7775254005ef0f7.png)

#### Key Process Description

1. **Obtain PK Status:**
  - **Callback Configuration**: Configure [PK Status Callback](https://www.tencentcloud.com/document/product/647/68260) to have the LiveKit backend actively notify your system when PK starts or ends.
  - **Active Query**: Your backend can call the [PK Status Query](https://www.tencentcloud.com/document/product/647/68256) API at any time to check the current PK status.
2. **PK Score Calculation**: Your backend calculates the PK score increment based on your business rules.
3. **PK Score Update**: Your backend calls the [Update PK Score](https://www.tencentcloud.com/document/product/647/68255) API to update the PK score in the LiveKit backend.
4. **LiveKit Backend Syncs to Client**: The backend automatically synchronizes the updated PK score to all clients.

#### Involved REST API Endpoints

| **API** | **Function Description** | **Request Example** |
| --- | --- | --- |
| Active API - Query PK Status | Check whether the current room is in PK | [Example](https://www.tencentcloud.com/document/product/647/68256) |
| Active API - Update PK Score | Update the calculated PK score | [Example](https://www.tencentcloud.com/document/product/647/68255) |
| Callback Configuration - PK Start Callback | Receive real-time notification when PK starts | [Example](https://www.tencentcloud.com/document/product/647/68260) |
| Callback Configuration - PK End Callback | Receive real-time notification when PK ends | [Example](https://www.tencentcloud.com/document/product/647/68261) |

### Winner Determination

In PK scenarios, scores are typically based on gifts received, driving competition and engagement. The PK module in RoomEngine supports score updates and broadcasts. Link your gift logic to this system.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d50c20c9cc3d11f0afdc52540044a08e.png)

When your billing system confirms a gift transaction, call the [Modify PK Score](https://www.tencentcloud.com/document/product/647/68255) to update the host's PK score. All users in PK rooms see the updated `battleScore` in `BattleState`. Update your PK progress bar whenever `battleScore` changes.

```
private fun observeBattleScore() {    val job = lifecycleScope.launch {        battleStore?.battleState?.battleScore?.collect { battleScore ->            // Update PK progress bar here        }    }    collectJobs.add(job)}
```

## API Documentation

For details on all public interfaces, properties, and methods for CoHostStore, BattleStore, LiveListStore, LiveSeatStore, and related classes, see the [AtomicXCore API documentation](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore).

| **Store/Component** | **Function Description** | **API Documentation** |
| --- | --- | --- |
| CoHostStore | Host Connection Lifecycle Management: Responsible for managing and coordinating the lifecycle of anchor connections, including initiating connection invitations, handling acceptance/rejection, switching connection status, managing video streams during connections, and disconnecting connections. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/index.html) |
| BattleStore | Streamer PK Battle Lifecycle Management: Responsible for managing the entire lifecycle of timed PK battles between streamers, including initiating PK invitations, starting the battle, updating PK scores in real time, settling the winner at the end of the PK, and penalty time. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-battle-store/index.html) |
| LiveListStore | Manages live room lifecycle: query room list, modify live info, etc. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/index.html) |
| LiveSeatStore | Manages seat states within a room (including cross-room seats), tracks user seat changes, microphone status, and more. | [API Documentation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/index.html) |

## FAQs

#### What is the maximum number of rooms and users supported for connection or PK?

Up to 9 rooms can be connected simultaneously, with 50 users per room.

#### How do I implement a punishment period after PK loss?

After receiving the `onBattleEnded` callback, determine the winner using `battleScore` from `BattleState`. The connection remains active after PK. Implement a custom 30-second punishment period, then disconnect after the countdown.

#### Why did the connection invitation not reach the target host?

- Verify that **targetHostLiveId** is correct and the target room is actively live.
- Check network connectivity; invitation signaling has a default 30-second timeout.

#### What happens if a host disconnects or the app crashes during connection or PK?

CoHostStore and BattleStore have built-in heartbeat and timeout detection. If a participant exits unexpectedly, the other party is notified via events such as `onCoHostUserLeft` or `onUserExitBattle`. Use these events to update the UI (e.g., "The other party has disconnected") and end the interaction.

#### Why can PK scores only be updated via REST API?

REST API ensures PK score **security, real-time updates, and scalability**:

- **Tamper-proof and fair:** Requires authentication and data validation. Each update is traceable (e.g., gift action), preventing manual score changes or cheating.
- **Real-time sync:** Standardized formats (e.g., JSON) allow seamless integration with gifts, PK, and display systems, keeping scores consistent across hosts, viewers, and backend.
- **Flexible rule adaptation:** Backend configuration changes (e.g., adjusting gift score values) can be made without front-end changes, reducing iteration costs.


---
*Source: [https://trtc.io/document/74689](https://trtc.io/document/74689)*
