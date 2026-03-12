# Audience Listening

`TUILiveKit` Voice Chat Room provides a comprehensive, ready-to-use interface for pure audio live streaming scenarios. It allows you to quickly implement essential features such as audience listening and mic interaction, eliminating the need to manage complex UI or seat management logic yourself.

## Feature Overview

- **Listen to Live Streams**: Hear the hostâs real-time audio stream with clarity and low latency.
- **Co-guest**: Request to join the mic and interact with the host via audio.
- **Live Information**: View room announcements and see the list of online audience members.
- **Live Interaction**: Engage with features such as bullet comments, gifts, and likes.

| **Listen to Live Streams** | **Co-guest** | **Live Information** | **Live Interaction** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7ab1ceefc07111f09c26525400bf7822.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/07055d1ac07411f0b35752540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f90d662ec07311f0aa02525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b26d5a28c06411f08863525400e889b2.png) |

## Quick Integration

### Integrate the Component

Follow the [Preparation](https://www.tencentcloud.com/document/product/647/60335) guide to integrate `TUILiveKit` into your project.

### Launch the Voice Chat Room Activity

The `VoiceRoomActivity` component provides a complete audience-side UI and business logic for the voice chat room. Simply launch this `Activity` to allow users to join a live room. Typically, when a user selects a room from the [Live Stream List](https://www.tencentcloud.com/document/product/647/74325), you should navigate to the audience view. See the example below:

```
import android.content.Intentimport android.os.Bundleimport androidx.appcompat.app.AppCompatActivityimport com.trtc.uikit.livekit.voiceroom.VoiceRoomActivityimport com.trtc.uikit.livekit.voiceroom.VoiceRoomDefine// YourLiveListActivity represents your live room list pageclass YourLiveListActivity : AppCompatActivity() {    // Handle "click live room" event    fun onJoinVoiceRoomClicked(roomId: String) {        // 1. Prepare the Intent and pass the required parameters        //    - roomId: The ID of the live room you want to join        //    - behavior: VoiceRoomDefine.RoomBehavior.JOIN means joining the room as an "audience"        val intent = Intent(this, VoiceRoomActivity::class.java).apply {            putExtra(VoiceRoomActivity.INTENT_KEY_ROOM_ID, roomId)            putExtra(VoiceRoomActivity.INTENT_KEY_ROOM_BEHAVIOR, JOIN.ordinal)        }        // 2. Navigate to the voice chat room page        startActivity(intent)    }}
```

- **Intent Extra Parameter Description:**

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| `VoiceRoomActivity.INTENT_KEY_ROOM_ID` | `string` | Globally unique live room ID. |
| `VoiceRoomActivity.INTENT_KEY_ROOM_BEHAVIOR` | `Int` | Room entry behavior:- `AUTO_CREATE`: Automatically create and enter a live room.- `PREPARE_CREATE`: Enter the pre-live preview page first, then create and enter the live room after the user clicks "Start Live".- `JOIN`: Join the room as an audience member. |

## Customize UI

`TUILiveKit` supports UI customization to meet a variety of business needs. You can easily modify interface text and icons.

### Text Customization (String Resources)

`TUILiveKit` uses standard **Android XML resource files** to manage the text displayed in the UI. You can directly modify the strings that need adjustment via the XML file:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6d9d2af2c07211f0a0935254007c27c5.png)

### Icon Customization (Drawable Resources)

`TUILiveKit` uses the standard **Android drawable resource** folder to manage the image resources for the UI. You can quickly change the custom icons by replacing the resource files. When replacing, ensure that the new file names are consistent with the original file names.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6d94ebddc07211f0b4a7525400454e06.png)

## Next Steps

You have successfully integrated **Audience Viewing**. Next, implement additional features such as **host broadcasting**, **live stream list** and **gift system**. See the table below for details:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Broadcasting** | Complete host live streaming workflow, including pre-live preparation and interactive features after going live. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74323) |
| **Live Stream List** | Display the live room list UI and features, including room list and room information display. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74325) |
| **Gift System** | Support custom gift asset configuration, billing system integration, and gift-sending in PK scenarios. | [Integration Guide](https://www.tencentcloud.com/document/product/647/69849) |

## FAQs

### No sound when an audience member after co-guest?

Ensure the app has microphone permission. Go to your deviceâs `App Info > Permissions > Microphone` and verify that microphone access is enabled.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/839f1b75c07311f0b4a7525400454e06.png)

### Bullet comments sent by an audience member are not visible to others in the room?

There are 3 reasons you can refer to:

- Check the network connection to ensure the audience memberâs device is online.
- The audience member has been muted by the host and cannot send bullet comments.
- The bullet comment contains blocked keywords. Confirm that the comment complies with room rules.


---
*Source: [https://trtc.io/document/74327](https://trtc.io/document/74327)*
