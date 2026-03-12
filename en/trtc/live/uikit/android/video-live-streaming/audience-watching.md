# Audience Watching

**TUILiveKit**'s audience viewing page provides users with various and convenient live streaming and interaction features, enabling quick integration into your application to meet diverse audience needs.

## Feature Overview

- **Live streaming:** Clear and smooth viewing of the host's real-time live stream.
- **Interactive co-guest:** Apply for mic connection to interact with the host via audio and video.
- **Live information:** View the live streaming room title, description, and audience list, etc.
- **Live interactive:** Send a gift (with animation effects and host notification), like (with animation and real-time statistics), and interact via bullet screen.

| **Live Streaming** | **Interactive co-guest** | **Live Information** | **Live Interactive** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b45c4b1e992611f0aa4252540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bf2d9d5f992611f0aa4252540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a2d5c5ea992611f08bb25254005ef0f7.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c6f28472992611f0b7a5525400454e06.png) |

## Quick Start

### Step 1. Activate the Service

Refer to the [Activate Service](https://www.tencentcloud.com/document/product/647/60033) document to enable the Free trial or official package.

### Step 2. Code Integration

Refer to [Preparations](https://www.tencentcloud.com/document/product/647/72217) guide to integrate the TUILiveKit SDK.

### Step 3. Add an Audience Viewing view

In your viewer watching **Activity**, initialize and add the `AudienceContainerView` viewer watching view.

Kotlin

Java

```
import android.os.Bundleimport androidx.appcompat.app.AppCompatActivityimport com.trtc.uikit.livekit.features.audiencecontainer.AudienceContainerViewimport com.trtc.uikit.livekit.features.audiencecontainer.AudienceContainerViewDefine.AudienceContainerViewListenerclass YourAudienceActivity : AppCompatActivity() {    lateinit var audienceContainerView: AudienceContainerView    lateinit var listener: AudienceContainerViewListener    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        // 1. Create AudienceContainerView        audienceContainerView = AudienceContainerView(this)        val roomId = "1236666"        // 2. Initialize AudienceContainerView        audienceContainerView.init(this, roomId)        // 3. (Optional) Add AudienceContainerView event monitoring        listener = object : AudienceContainerViewListener {            override fun onLiveEnded(roomId: String?, ownerName: String?, ownerAvatarUrl: String?) {                // Live streaming end event, you can handle this event as your business need, here example code: end current page after live streaming ends                finish()            }            override fun onPictureInPictureClick() {                // Picture-in-Picture button click event, you can handle this event as your business need, here example code: click the Picture-in-Picture button to convert the current page to picture-in-picture mode                enterPictureInPictureMode()            }        }        audienceContainerView.addListener(listener)        // 4. Add AudienceContainerView to the interface        setContentView(audienceContainerView)    }    override fun onDestroy() {        // 5. (Optional) If you added an event listener, it needs to be removed on page termination        audienceContainerView.removeListener(listener)        super.onDestroy()    }}
```

```
import android.os.Bundle;import androidx.appcompat.app.AppCompatActivity;import com.trtc.uikit.livekit.features.audiencecontainer.AudienceContainerView;import com.trtc.uikit.livekit.features.audiencecontainer.AudienceContainerViewDefine;public class YourAudienceActivity extends AppCompatActivity {    private AudienceContainerView mAudienceContainerView;    private AudienceContainerViewDefine.AudienceContainerViewListener mListener;    @Override    protected void onCreate(Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        // 1. Create AudienceContainerView        mAudienceContainerView = new AudienceContainerView(this);        // 2. Initialize AudienceContainerView        String roomId = "1236666";        mAudienceContainerView.init(this, roomId);        // 3. (Optional) Add AudienceContainerView event monitoring        mListener = new AudienceContainerViewDefine.AudienceContainerViewListener() {            @Override            public void onLiveEnded(String roomId, String ownerName, String ownerAvatarUrl) {                // Live streaming end event, you can handle this event as your business need, here example code: end current page after live streaming ends                finish();            }            @Override            public void onPictureInPictureClick() {                // Picture-in-Picture button click event, you can handle this event as your business need, here example code: click the Picture-in-Picture button to convert the current page to picture-in-picture mode                enterPictureInPictureMode();            }        };        mAudienceContainerView.addListener(mListener);        // 4. Add AudienceContainerView to the interface        setContentView(mAudienceContainerView);    }    @Override    protected void onDestroy() {        // 5. (Optional) If you added an event listener, it needs to be removed on page termination        mAudienceContainerView.removeListener(mListener);        super.onDestroy();    }}
```

### Step 4. Navigate to the **Audience Viewing** view

Usually in the [live stream list](https://www.tencentcloud.com/document/product/647/72220), use the following code example when you need to jump to the viewer watching page:

Kotlin

Java

```
fun startActivity(context: Context) {    val intent = Intent(context, YourAudienceActivity::class.java)    intent.putExtra("roomId", "1236666")    context.startActivity(intent)}
```

```
private void startActivity(Context context){    Intent intent = new Intent(context, YourAudienceActivity.class);    intent.putExtra("roomId", "1236666");    context.startActivity(intent);}
```

## Customize Your UI Layout

### Customize the `AudienceContainerView` Feature Area

By calling the API of the `audienceView` created in [Step 3](https://www.google.com/search?q=%23step-3-add-the-viewer-watching-page), you can customize and disable (hide) the operation area or specific features on the viewer watching page:

Kotlin

Java

```
import android.os.Bundleimport androidx.appcompat.app.AppCompatActivityimport com.trtc.uikit.livekit.features.audiencecontainer.AudienceContainerViewclass YourAudienceActivity : AppCompatActivity() {    lateinit var audienceContainerView: AudienceContainerView    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        // 1. Create and initialize AudienceContainerView        audienceContainerView = AudienceContainerView(this)        val roomId = "1236666"        audienceContainerView.init(this, roomId)                // 2. Custom function example - forbid swiping to switch live rooms        audienceContainerView.disableSliding(true)                // 3. Add AudienceContainerView to the interface        setContentView(audienceContainerView)    }}
```

```
import android.os.Bundle;import androidx.appcompat.app.AppCompatActivity;import com.trtc.uikit.livekit.features.audiencecontainer.AudienceContainerView;public class YourAudienceActivity extends AppCompatActivity {    private AudienceContainerView mAudienceContainerView;    @Override    protected void onCreate(Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        // 1. Create and initialize AudienceContainerView        mAudienceContainerView = new AudienceContainerView(this);        String roomId = "1236666";        mAudienceContainerView.init(this, roomId);        // 2. Custom function example - forbid swiping to switch live rooms        mAudienceContainerView.disableSliding(true);        // 3. Add AudienceContainerView to the interface        setContentView(mAudienceContainerView);    }}
```

| **API** | **Description** |
| --- | --- |
| `disableHeaderLiveData(true)` | Hide Top Operation Section Live Information |
| `disableHeaderFloatWin(true)` | Hide Top Operation Section Floating Window Feature |
| `disableHeaderVisitorCnt(true)` | Hide Top Operation Section Audience List Function |
| `disableFooterCoGuest(true)` | Hide Bottom Operation Section Co-Anchoring Function |
| `disableSliding(true)` | Forbid Swiping to Switch Live Rooms |

### Text Customization (String Resources)

TUILiveKit uses standard **Android XML resource files** to manage the text displayed in the UI. You can directly modify the strings that need adjustment via the XML file:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7cd902e5991e11f0961e52540099c741.png)

### Icon Customization (Drawable Resources)

TUILiveKit uses the standard **Android drawable resource** folder to manage the image resources for the UI. You can quickly change the custom icons by replacing the resource files. When replacing, ensure that the new file names are consistent with the original file names.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7ce6a645991e11f0b38f5254001c06ec.png)

## Next Steps

Congratulations! You have successfully integrated **Audience Viewing**. Next, you can implement features such as **host streaming**, **live stream list** and **gift system**. Please refer to the table below:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Streaming** | The complete workflow for a host to start a stream, including pre-stream setup and various in-stream interactions. | [Host Streaming](https://www.tencentcloud.com/document/product/647/72219) |
| **Live Stream List** | Display the live stream list interface and features, including the live stream list and room information display. | [Live Stream List](https://www.tencentcloud.com/document/product/647/72220) |
| **Gift System** | Support custom gift asset configuration, billing system integration, and gift-sending in PK scenarios. | [Gift System](https://www.tencentcloud.com/document/product/647/69849) |

## FAQs

### Why is the video screen black when a viewer selects video co-hosting?

Please go to **App Info > Permissions > Camera** and check if the **camera permission** is enabled. Refer to the image below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f422e88991e11f0b7a5525400454e06.png)

### Why can't other viewers in the live room see the barrage content sent by a viewer?

- **Reason 1**: First check the network connection to ensure the viewer's device network is normal.
- **Reason 2**: The viewer has been **muted (banned)** by the host and cannot send barrage.
- **Reason 3**: The viewer's barrage content involves **keyword blocking**. Please confirm whether the content sent by the viewer complies with the live room rules.


---
*Source: [https://trtc.io/document/72221](https://trtc.io/document/72221)*
