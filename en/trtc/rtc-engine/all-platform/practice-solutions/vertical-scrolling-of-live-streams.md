# Vertical Scrolling of Live Streams

In live streaming scenarios where a large number of anchors offer a wide variety of video content, allowing users to quickly browse and select their favorite content by scrolling up or down can deliver an enhanced user experience. This document introduces the implementation solutions for Android and iOS, respectively.

## Vertical Scrolling Solution for Live Streams on iOS

In such scenarios, switching between live streaming rooms can cause discontinuity between the video streams of the current and next rooms, as entering a new room and pulling streams take time. To address this issue, 3 solutions are generally available. This document explains the 3 solutions in detail.

| **Implementation Method** | **User Experience** | **Resource Consumption** | **Implementation Logic** |
| --- | --- | --- | --- |
| [Black Screen](https://www.tencentcloud.com/document/product/1228/73993#9ed39c99-904e-499e-a06c-18be6397e1a1) | Good. When you switch between live streaming rooms, a black screen is displayed before the new video appears. | No additional resource consumption. | Simple. No additional logic. |
| [Placeholder Image](https://www.tencentcloud.com/document/product/1228/73993#66cb12f1-0c90-48e1-814b-5a327734042d) | Slightly better. When you switch between live streaming rooms, a fixed placeholder image of the corresponding anchor is displayed before the new video appears. | Slightly higher. A placeholder image needs to be additionally stored for each anchor and loaded on the client. | Slightly complex. Asynchronous loading of placeholder images is additionally required before switching. |
| [Dual Instances](https://www.tencentcloud.com/document/product/1228/73993#2ea458a4-4c26-489e-9994-35bbece92bcd) | Best. When you switch between live streaming rooms, the videos of the current and next anchors are smoothly displayed. | Higher. Two streams need to be pulled concurrently in the list. After you enter a live streaming room, only 1 stream needs to be pulled. | More complex. Multiple instances are required, and the audio and video pulling of each instance needs to be controlled. |

### Black Screen

By listening for system scrolling events, the code implementation of business personnel calls the room-switching API to switch between live streaming rooms. Before the new live streaming room is fully loaded, no content is displayed, resulting in a brief black screen. For convenience, the black screen duration here is about 1 second. The specific black screen duration is affected by network conditions and video bitrate. The rendering is as follows.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e4fe1d26c36d11f0a6dd5254005ef0f7.gif)

The code snippet for room switching is as follows:

```
let src = TRTCSwitchRoomConfig()// Generate the corresponding room ID and room entry credential according to business needs. In this example, generate the room entry credential on the client. For online businesses, obtain the information from the backend.src.strRoomId = strRoomIdsrc.userSig = GenerateTestUserSig.genTestUserSig(identifier: userId) as StringtrtcCloud.switchRoom(src)
```

### Placeholder Image

By listening for system scrolling events, the code implementation of business personnel calls the room-switching API to switch between live streaming rooms. Unlike the black screen solution, this solution requires loading a placeholder image for each live streaming room in advance. Before the video stream of a live streaming room appears, the placeholder image of the room is displayed. For convenience, the placeholder image duration here is about 1 second. The specific duration is affected by network conditions and video bitrate.

#### Rendering

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ff27dbedc36d11f0aa02525400e889b2.gif)

#### Implementation Steps

1. Set the background image for the first anchor.

```
bgView = UIImageView(frame: self.view.bounds)// The image should be the placeholder image for the corresponding live streaming room. Business personnel should obtain the image in advance.bgView.image = UIImage(named: "1.png")bgView.contentMode = .scaleAspectFillbgView.translatesAutoresizingMaskIntoConstraints = falseself.view.insertSubview(bgView, at: 0)NSLayoutConstraint.activate([    bgView.topAnchor.constraint(equalTo: view.topAnchor),    bgView.bottomAnchor.constraint(equalTo: view.bottomAnchor),    bgView.leadingAnchor.constraint(equalTo: view.leadingAnchor),    bgView.trailingAnchor.constraint(equalTo: view.trailingAnchor),])
```

2. Switch the background image before switching between live streaming rooms.

```
DispatchQueue.main.async {    UIView.transition(            with: self.bgView,            duration: 0,            options: .transitionCrossDissolve,            animations: {                // Business personnel switches the corresponding placeholder image.                self.bgView.image = UIImage(named: strRoomId)            }, completion: nil)}let src = TRTCSwitchRoomConfig()// Generate the corresponding room ID and room entry credential according to business needs. In this example, generate the room entry credential on the client. For online businesses, obtain the information from the backend.src.strRoomId = strRoomIdsrc.userSig = GenerateTestUserSig.genTestUserSig(identifier: userId) as StringtrtcCloud.switchRoom(src)
```

3. Switch the background image to the video when the first video frame starts rendering in the new live streaming room.

```
// Pull video streams.func onUserVideoAvailable(_ userId: String, available: Bool) {    if available {        trtcCloud.startRemoteView(userId, streamType: .big, view: view)    } else {        trtcCloud.stopRemoteView(userId, streamType: .big)    }}// When the first video frame starts rendering, switch the placeholder image to the background and display the video.func onFirstVideoFrame(_ userId: String, streamType: TRTCVideoStreamType, width: Int32, height: Int32) {    // Adjust the sequence of the background image and the video rendering control as needed.    self.view.exchangeSubview(at: 1, withSubviewAt: 0)}
```

### Dual Instances

> **Note:**Although this solution offers the best display effect and user experience, it requires pulling 2 streams simultaneously from the current and next live streaming rooms when a user is scrolling through the list. While the stream of the next live streaming room can stop preloading once the user enters the room, this solution results in higher overall traffic and fees.

#### Rendering

To achieve the smoothest vertical scrolling effect, 2 instances should be used at the same time. While you are viewing the current live streaming room, the video stream of the next live streaming room is preloaded. By leveraging UIPageViewController or manually adjusting the display positions of the current and next videos based on the scrolling position, a natural and smooth transition is achieved. The effect of scrolling to the next live streaming room is shown in the example on the left below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d58f8b6c36e11f0a6dd5254005ef0f7.gif)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/50e63d51c36e11f08c0e52540044a08e.gif)

The overall logic of this solution is as follows. Once you enter the current live streaming room, a sub-instance is immediately used to enter the next live streaming room, pull the video stream of the next room, and display the stream on the next page of UIPageViewController. Once you enter the new live streaming room, the audio stream of the new room is enabled. This loop repeats, ensuring the smoothest vertical scrolling effect. Meanwhile, to avoid excessive resource consumption, only the next live streaming room is preloaded, while the less frequently accessed previous live streaming room is not preloaded. As a result, when you switch back to the previous live streaming room, a brief black screen is still displayed. The effect of viewing the previous live streaming room is shown in the example on the right above.

#### Implementation Steps

1. Define a sub-instance utility class.

```
import Foundationimport ObjectiveCimport TXLiteAVSDK_Professional@objc protocol SubCloudHelperDelegate : NSObjectProtocol {    @objc optional func onUserVideoAvailableWithSubId(subId: Int, userId: String, available: Bool)}class SubCloudHelper:NSObject,TRTCCloudDelegate {    var trtcCloud: TRTCCloud!    var subId: Int!    weak var delegate : SubCloudHelperDelegate? = nil        func initWithSubId(subId: Int, trtcIns: TRTCCloud) {        self.subId = subId        self.trtcCloud = trtcIns        self.trtcCloud.addDelegate(self)    }    func getCloud()->TRTCCloud {        return trtcCloud    }    func onUserVideoAvailable(_ userId: String, available: Bool) {        if self.delegate?.onUserVideoAvailableWithSubId?(subId: subId, userId: userId, available: available) == nil {            return        }    }}
```

2. Use a sub-instance.

```
let trtcCloud = TRTCCloud()let subCloudHelper = SubCloudHelper()override func viewDidLoad() {    super.viewDidLoad()        subCloudHelper.initWithSubId(subId: 0, trtcIns: trtcCloud.createSub())    subCloudHelper.delegate = self}
```

3. Prepare UIPageViewController for switching.

```
private var atRoom: Bool = falsevar pageViewController: UIPageViewController!var pageZero: UIViewController!var pageOne: UIViewController!var pageTwo: UIViewController!var pages: [UIViewController] = []var curPageIdx = 0var curIsSub = falsefunc setupPages() {    pageViewController = UIPageViewController(        transitionStyle: .scroll,        navigationOrientation: .vertical    )    pageViewController.dataSource = self    pageViewController.delegate = self    addChild(pageViewController)    view.addSubview(pageViewController.view)    pageViewController.didMove(toParent: self)    // pages    pageZero = UIViewController()    pageZero.view.backgroundColor = .black    pageOne = UIViewController()    pageOne.view.backgroundColor = .black    pageTwo = UIViewController()    pageTwo.view.backgroundColor = .black    pages = [pageZero, pageOne, pageTwo]        pageViewController.setViewControllers([pages[curPageIdx]], direction: .forward, animated: false)}
```

4. Implement page switching in pageViewController.

```
// Obtain the next/previous page.func getShowPage(isNext: Bool) -> UIViewController {    var newPageIdx = 0    if isNext {        newPageIdx = curPageIdx + 1    } else {        newPageIdx = curPageIdx - 1    }    if newPageIdx >= pages.count {        newPageIdx = 0    } else if newPageIdx < 0 {        newPageIdx = pages.count - 1    }    return pages[newPageIdx]}extension RtcDuplexVC: UIPageViewControllerDataSource {    func pageViewController(_ pageViewController: UIPageViewController, viewControllerBefore viewController: UIViewController) -> UIViewController? {        return getShowPage(isNext: false)    }    func pageViewController(_ pageViewController: UIPageViewController, viewControllerAfter viewController: UIViewController) -> UIViewController? {        return getShowPage(isNext: true)    }}
```

5. The primary instance enters the live streaming room and the sub-instance preloads the next room.

```
// The primary instance enters the room.// Replace sdkAppId, roomID, strRoomId, userId, and userSig based on actual business needs.// In this example, generate userSig on the client. For online businesses, obtain the information from the backend.let params = TRTCParams()params.sdkAppId = UInt32(SDKAppID)params.roomId = 0params.strRoomId = strRoomIdLst.first ?? "1"params.userId = userIdparams.role = .anchorparams.userSig = GenerateTestUserSig.genTestUserSig(identifier: userId) as StringtrtcCloud.addDelegate(self)trtcCloud.enterRoom(params, appScene: .LIVE)// The sub-instance preloads and enters the next room.// Replace sdkAppId, roomID, strRoomId, userId, and userSig based on actual business needs.// In this example, generate userSig on the client. For online businesses, obtain the information from the backend.let subParams = TRTCParams()subParams.sdkAppId = UInt32(SDKAppID)subParams.roomId = 0subParams.strRoomId = strRoomIdLst[1]subParams.userId = userIdsubParams.role = .anchorsubParams.userSig = GenerateTestUserSig.genTestUserSig(identifier: userId) as StringsubCloudHelper.trtcCloud.enterRoom(subParams, appScene: .LIVE)subCloudHelper.trtcCloud.muteAllRemoteAudio(true)
```

6. Pull video streams based on callbacks and render the streams to the corresponding page.

```
func getPageByIdx(isNext: Bool) -> UIViewController {    var newPageIdx = curPageIdx    if isNext {        newPageIdx += 1    }    if newPageIdx >= pages.count {        newPageIdx = 0    }    return pages[newPageIdx]}extension RtcDuplexVC: TRTCCloudDelegate {    func onUserVideoAvailable(_ userId: String, available: Bool) {        if available {            trtcCloud.startRemoteView(userId, streamType: .big, view: getPageByIdx(isNext: curIsSub).view)        } else {            trtcCloud.stopRemoteView(userId, streamType: .big)        }    }}extension RtcDuplexVC: SubCloudHelperDelegate {    func onUserVideoAvailableWithSubId(subId: Int, userId: String, available: Bool) {        if available {            subCloudHelper.trtcCloud.startRemoteView(userId, streamType: .big, view: getPageByIdx(isNext: !curIsSub).view)        } else {            subCloudHelper.trtcCloud.stopRemoteView(userId, streamType: .big)        }    }}
```

7. Update the preloading room after switching to a new room, or update the currently displayed room while scrolling up.

```
func updateCurRoomIdx(isNext: Bool) {    if isNext {        curRoomIdx += 1        if curRoomIdx >= strRoomIdLst.count {            curRoomIdx = 0        }    } else {        curRoomIdx -= 1        if curRoomIdx < 0 {            curRoomIdx = strRoomIdLst.count - 1        }    }}// Here, you need to switch the room ID based on the actual business logic.func updateNewRoom(isNext: Bool) {    var newRoomIdx = 0    if isNext{        newRoomIdx = curRoomIdx + 1    } else {        newRoomIdx = curRoomIdx - 1    }    if newRoomIdx >= strRoomIdLst.count {        newRoomIdx = 0    } else if newRoomIdx < 0 {        newRoomIdx = strRoomIdLst.count - 1    }    let newRoomStrId = strRoomIdLst[newRoomIdx]        let src = TRTCSwitchRoomConfig()    src.strRoomId = newRoomStrId    src.userSig = GenerateTestUserSig.genTestUserSig(identifier: userId) as String    if curIsSub {        trtcCloud.switchRoom(src)        trtcCloud.muteAllRemoteAudio(true)    } else {        subCloudHelper.trtcCloud.switchRoom(src)        subCloudHelper.trtcCloud.muteAllRemoteAudio(true)    }}extension RtcDuplexVC: UIPageViewControllerDelegate {    func pageViewController(        _ pageViewController: UIPageViewController,        didFinishAnimating finished: Bool,        previousViewControllers: [UIViewController],        transitionCompleted completed: Bool    ) {        if completed {            guard let currentVC = pageViewController.viewControllers?.first else {return}            if let index = pages.firstIndex(of: currentVC) {                // Obtain the basis for determining whether the user scrolled up or down.                let iden = index - curPageIdx                // Update the index of the currently displayed page.                curPageIdx = index                // Scroll down.                if iden == 1 || iden == -2 {                    // Update the index of the current room.                    updateCurRoomIdx(isNext: true)                    // Update the instance of the currently displayed page.                    curIsSub.toggle()                    // Update the room.                    updateNewRoom(isNext: true)                }                // Scroll up.                if iden == -1 || iden == 2 {                    // Update the room.                    updateNewRoom(isNext: false)                    // Update the index of the current room.                    updateCurRoomIdx(isNext: false)                    // Update the instance of the currently displayed page.                    curIsSub.toggle()                    trtcCloud.muteAllRemoteAudio(true)                    subCloudHelper.trtcCloud.muteAllRemoteAudio(true)                }                // Unmute the current room.                if curIsSub {                    subCloudHelper.trtcCloud.muteAllRemoteAudio(false)                } else {                    trtcCloud.muteAllRemoteAudio(false)                }            }        }    }}
```

In addition, business personnel can distinguish between "scrolling through the list" and "in a live streaming room" statuses. When you scroll up or down, information, including room details and chats, is generally not needed. This information only needs to be displayed after you enter a live streaming room. This distinction can reduce the pressure on business personnel to record the live streaming room status during frequent vertical scrolling, while decreasing the resource consumption from preloading.

The specific approach is as follows. Only users who are scrolling through the list can switch between live streaming rooms by scrolling up or down. In this case, only the live streaming room visuals and a small amount of information are displayed. Once users enter a live streaming room, the full live streaming room, chats, and other information are displayed. At this point, the users are not allowed to switching between live streaming rooms by scrolling up or down. Meanwhile, the video stream preloading for the next live streaming room stops once users enter a live streaming room and resumes when the users return to the "scrolling through the listâ status. The effect is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7e6452e6c37c11f0aa02525400e889b2.gif)

The specific implementation is as follows:

```
// Handle the logic for entering a live streaming room.@objc func enterBtnClick() {    // Hide the UI component in the vertical scrolling list.    self.enterBtn.isHidden = true    // Display the UI component after the user enters a live streaming room.    self.exitBtn.isHidden = false    // ...        self.atRoom = true    // Forbid vertical scrolling once the user enters a live streaming room.    pageViewController.dataSource = nil        // Stop preloading.    if curIsSub{        trtcCloud.muteAllRemoteVideoStreams(true)    } else {        subCloudHelper.trtcCloud.muteAllRemoteAudio(true)    }}  // Handle the logic for exiting a live streaming room.@objc func exitBtnClick() {    // Hide the UI component in a live streaming room.    self.enterBtn.isHidden = false    // Display the UI component in the vertical scrolling list.    self.exitBtn.isHidden = true        self.atRoom = false    // Restore vertical scrolling once the user enters the vertical scrolling list.    pageViewController.dataSource = self    // Restore preloading.    if curIsSub{        trtcCloud.muteAllRemoteVideoStreams(false)    } else {        subCloudHelper.trtcCloud.muteAllRemoteAudio(false)    }}
```

## Vertical Scrolling Solution for Live Streams on Android

In the dual-instance and single-instance chapters below, the rendering and example code contain 3 pages. The order of the 3 pages is as follows: A > B > C. A corresponds to Room 1231, B to Room 1232, and C to Room 1233.

| **Implementation Method** | **User Experience** | **Resource Consumption** | **Implementation Logic** |
| --- | --- | --- | --- |
| [Single Instance](https://www.tencentcloud.com/document/product/1228/73993#03055b6b-0ecb-4e65-9843-2b8ba3ab4c28) | Typically, while scrolling through the list, you cannot view 2 live streaming rooms simultaneously. The corresponding live streaming room is displayed only after the page is fully switched. In this case, placeholder images can be used to enhance user experience. | Only 1 stream in the list consumes traffic, and 1 video playback object is being used. | Simple. Set placeholder images as needed. |
| [Dual Instances](https://www.tencentcloud.com/document/product/1228/73993#b91115f4-9b26-41f5-8f50-49a29c090772) | Better. You can enter 2 live streaming rooms simultaneously, and the next live streaming room is loaded in advance. While scrolling through the list, you can view both the current and next live streaming rooms simultaneously. | Two streams in the list consumes traffic, incurring 2 streams of fees, and 2 video playback objects are being used. | Complex. Multiple instances are required, and the audio and video pulling of each instance needs to be controlled. |

### Single Instance

While scrolling up or down the live stream list, you can view only 1 live stream (single instance), resulting in lower costs.

#### Rendering

When scrolling from Page A, you cannot view the live stream on Page B at the same time. After switching to Page B, you can view the live stream on Page B, but you will no longer be able to view the live stream on Page A.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2ec19a8ac36f11f0a0935254007c27c5.gif)

#### Solution Principle

While scrolling between pages, you can only view 1 live stream at any given time. After page switching, the previous live stream stops, and the next live stream is pulled.

When you scroll from Page A to Page B, the operations and status at each stage are as follows:

1. When Page A is displayed on the screen, TRTCCloud instance 1 is used to enter Room 1231, pull the stream, and play the audio and video on Page A.
2. During the process of scrolling from Page A to Page B, if the callback for switching to Page B has not yet been received, Page A continues playing the audio and video stream from Room 1231, while Page B shows a placeholder image or a black screen.
3. During the process of scrolling from Page A to Page B, if the callback for switching to Page B is received, TRTCCloud instance 1 is used to stop pulling the audio and video stream from Room 1231, exit the room, and then enter Room 1232 to pull and play the new audio and video stream on Page B, while Page A shows a placeholder image or a black screen.

#### Implementation Code

Use ViewPager2 and RecyclerView.Adapter to achieve a full-screen scrolling effect. In the onPageSelected callback of registerOnPageChangeCallback in ViewPager2, stop pulling the current stream, leave the current room, enter a new room, and start pulling the new stream. Below are the complete code of ScrollSwitchRoomActivity. The layout file is the same as the previous section.

The code of ScrollSwitchRoomActivity is as follows:

```
public class ScrollSwitchRoomActivity extends TRTCBaseActivity {    PageAdapter mAdapter;    public String[] mRoomIds;    private TRTCCloud mTRTCCloud;    private TXCloudVideoView mRemoteVideoView;    private int mCurPos = -1;    @Override    protected void onCreate(Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        setContentView(R.layout.activity_scroll_switch_room);        // Hide the title bar.        getSupportActionBar().hide();        mRoomIds = new String[]{"1231", "1232", "1233"};        if (checkPermission()) {            initView();        }    }    @Override    protected void onPermissionGranted() {        initView();    }    private void initView() {        mAdapter = new PageAdapter(this, mRoomIds);        ViewPager2 viewPager = findViewById(R.id.viewPager);        viewPager.setAdapter(mAdapter);        // Set the viewPager scrolling orientation.        viewPager.setOrientation(ViewPager2.ORIENTATION_VERTICAL);        // Set the viewPager preloading.        viewPager.setOffscreenPageLimit(1);        // Add a page switch listener.        viewPager.registerOnPageChangeCallback(new ViewPager2.OnPageChangeCallback() {            public void onPageSelected(int position) {                Log.d("ScrollSwitchRoom", "onPageSelected: " + position);                if (mCurPos == position) {                    return;                }                                RecyclerView recyclerViewImpl = (RecyclerView) viewPager.getChildAt(0);                // Exit the current room.                exitRoom();                // Enter the next room.                View itemView = recyclerViewImpl.getChildAt(position);                mRemoteVideoView = itemView.findViewById(R.id.txcvv_main_local);                enterRoom(position);                mCurPos = position;            }        });        // Initialize your views here        mTRTCCloud = TRTCCloud.sharedInstance(getApplicationContext());        mTRTCCloud.addListener(mTRTCCloudListener);    }    private void enterRoom(int roomIdIndex) {        TRTCCloudDef.TRTCParams mTRTCParams = new TRTCCloudDef.TRTCParams();        mTRTCParams.sdkAppId = GenerateTestUserSig.SDKAPPID;        mTRTCParams.userId = "123";        mTRTCParams.strRoomId = mRoomIds[roomIdIndex];        mTRTCParams.userSig = GenerateTestUserSig.genTestUserSig(mTRTCParams.userId);        mTRTCParams.role = TRTCCloudDef.TRTCRoleAudience;        mTRTCCloud.enterRoom(mTRTCParams, TRTCCloudDef.TRTC_APP_SCENE_LIVE);    }    private TRTCCloudListener mTRTCCloudListener = new TRTCCloudListener() {        public void onEnterRoom(long result) {            if (result == 0) {                // Enter room success            } else {                // Enter room failed            }        }        public void onExitRoom(int reason) {            // Exit room        }        @Override        public void onUserVideoAvailable(String userId, boolean available) {            super.onUserVideoAvailable(userId, available);            if (available) {                mTRTCCloud.startRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, mRemoteVideoView);            } else {                mTRTCCloud.stopRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);            }        }        public void onError(int errCode, String errMsg, Bundle extraInfo) {            // print Error            Log.e("ScrollSwitchRoom", "Error: " + errCode + " " + errMsg);        }    };    private void exitRoom() {        mTRTCCloud.stopAllRemoteView();        mTRTCCloud.exitRoom();//        mTRTCCloud.setListener(null);    }    public class PageAdapter extends RecyclerView.Adapter<PageAdapter.PageViewHolder> {                private Context context;        public String[] mRoomIds;                public PageAdapter(Context context, String[] roomIds) {            this.context = context;            this.mRoomIds = roomIds;        }        public PageViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {            View view = LayoutInflater.from(context).inflate(R.layout.item_scroll_page, parent, false);            return new PageViewHolder(view);        }        public void onBindViewHolder(@NonNull PageViewHolder holder, int position) {            TextView textView = holder.itemView.findViewById(R.id.tv_room_number);            textView.setText(getString(R.string.switchroom_roomid) + ":" + mRoomIds[position]);        }        public int getItemCount() {            return mRoomIds.length;        }        public int getItemViewType(int position) {            return position;        }        class PageViewHolder extends RecyclerView.ViewHolder {            PageViewHolder(@NonNull View itemView) {                super(itemView);            }        }    }        @Override    protected void onDestroy() {        super.onDestroy();        exitRoom();    }}
```

The activity_scroll_switch_room.xml content is as follows:

```
<?xml version="1.0" encoding="utf-8"?><androidx.viewpager2.widget.ViewPager2 xmlns:android="http://schemas.android.com/apk/res/android"    android:id="@+id/viewPager"    android:layout_width="match_parent"    android:layout_height="match_parent" />
```

The item_scroll_page.xml content is as follows:

```
<?xml version="1.0" encoding="utf-8"?><androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"    xmlns:app="http://schemas.android.com/apk/res-auto"    android:id="@+id/item_layout"    android:layout_width="match_parent"    android:layout_height="match_parent">    <ImageView        android:id="@+id/iv_placeholder"        android:scaleType="centerCrop"        android:background="@drawable/placeholder_img"        android:layout_width="match_parent"        android:layout_height="match_parent"/>    <com.tencent.rtmp.ui.TXCloudVideoView        android:id="@+id/txcvv_main_local"        android:layout_width="match_parent"        android:layout_height="match_parent" />    <TextView        android:id="@+id/tv_room_number"        android:layout_width="wrap_content"        android:layout_height="wrap_content"        app:layout_constraintEnd_toEndOf="@id/item_layout"        app:layout_constraintStart_toStartOf="@id/item_layout" /></androidx.constraintlayout.widget.ConstraintLayout>
```

### Dual Instances

When you scroll up or down the live stream list, 2 TRTCCloud instances enter 2 rooms (the current room and the next room) simultaneously. While scrolling, you can view live streams from both rooms. If you scroll down from the current room, you cannot view the live stream of the previous room until the page is fully switched. If necessary, you can use 3 TRTCCloud instances for implementation.

> **Note:**Using dual instances will pull streams from 2 rooms at the same time, resulting in the traffic consumption of 2 streams and incurring more fees. If 3 TRTCCloud instances are used, the traffic of 3 streams will be consumed.

#### Rendering

When scrolling from Page B, you can directly view the live stream on Page C.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4dac7dc4c36f11f08c0e52540044a08e.gif)

#### Solution Principle

While scrolling between pages, you can view up to 2 pages at the same time. Two TRTCCloud instances are used to enter 2 rooms and pull streams from both rooms simultaneously.

When you scroll from Page A to Page B, the operations and status at each stage are as follows:

1. When Page A is displayed on the screen, TRTCCloud instance 1 is used to enter Room 1231, pull the stream, and play the audio and video on Page A. Meanwhile, TRTCCloud instance 2 is used to enter Room 1232, pull the stream, play the video on Page B, and mute the audio.
2. During the process of scrolling from Page A to Page B, you can view both Page A and Page B playing videos simultaneously and hear the audio from Room 1231.
3. After Page B is fully displayed, TRTCCloud instance 2 is used to enable audio for Room 1232 while the video of this room continues playing. TRTCCloud instance 1 is used to leave Room 1231, enter Room 1233, pull the stream, play the video on page C, and mute the audio.
4. During the process of scrolling from Page B to Page A, you can only view the video of Room 1232, as TRTCCloud instance 2 is used on Page B and TRTCCloud instance 1 is used on Page C at this point. After Page A is fully displayed, TRTCCloud instance 1 is used on Page A to enter Room 1231, pull the stream, and play the audio and video, while Page B continues to use TRTCCloud instance 2 to pull the video stream and mute the audio.

#### Implementation Code

Use ViewPager2 and RecyclerView.Adapter to achieve a full-screen scrolling effect. The code for ScrollSwitchRoomActivity is as follows:

```
public class ScrollSwitchRoomDualActivity extends TRTCBaseActivity {    PageAdapter mAdapter;    public String[] mRoomIds;    private TRTCCloud mTRTCCloud;    private TRTCCloud mSubCloud;    private TXCloudVideoView mRemoteVideoView;    private TXCloudVideoView mSubRemoteVideoView;    private Boolean mIsInMainRoom = null;    private int mCurPos = 0;    @Override    protected void onCreate(Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        setContentView(R.layout.activity_scroll_switch_room);        // Hide the title bar.        getSupportActionBar().hide();        mRoomIds = new String[]{"1231", "1232", "1233"};        if (checkPermission()) {            initView();        }    }    @Override    protected void onPermissionGranted() {        initView();    }    private void initView() {        mAdapter = new PageAdapter(this,mRoomIds);        ViewPager2 viewPager = findViewById(R.id.viewPager);        viewPager.setAdapter(mAdapter);        // Set the viewPager scrolling orientation.        viewPager.setOrientation(ViewPager2.ORIENTATION_VERTICAL);        // Set the viewPager preloading.        viewPager.setOffscreenPageLimit(1);        // Add a page switch listener.        viewPager.registerOnPageChangeCallback(new ViewPager2.OnPageChangeCallback() {            public void onPageSelected(int position) {                Log.d("ScrollSwitchRoom", "onPageSelected: " + position);                RecyclerView recyclerViewImpl = (RecyclerView) viewPager.getChildAt(0);                if (mIsInMainRoom == null) {                    View itemView = recyclerViewImpl.getChildAt(position);                    mRemoteVideoView = itemView.findViewById(R.id.txcvv_main_local);                    View subItemView = recyclerViewImpl.getChildAt(position + 1);                    mSubRemoteVideoView = subItemView.findViewById(R.id.txcvv_main_local);                    enterRoom();                    mIsInMainRoom = true;                } else {                    if (mIsInMainRoom) {                        mTRTCCloud.muteAllRemoteAudio(true);                        mSubCloud.muteAllRemoteAudio(false);                    } else {                        mTRTCCloud.muteAllRemoteAudio(false);                        mSubCloud.muteAllRemoteAudio(true);                    }                    if (position != (mRoomIds.length - 1)) {                        String roomId;                        TRTCCloud trtcCloud;                        if (mCurPos < position) {                            // Scroll up the screen.                            roomId = mRoomIds[position + 1];                            trtcCloud = mIsInMainRoom ? mTRTCCloud : mSubCloud;                            View itemView = recyclerViewImpl.getChildAt(position + 1);                            if (mIsInMainRoom) {                                mRemoteVideoView = itemView.findViewById(R.id.txcvv_main_local);                            } else {                                mSubRemoteVideoView = itemView.findViewById(R.id.txcvv_main_local);                            }                        } else {                            // Scroll down the screen.                            roomId = mRoomIds[position];                            trtcCloud = mIsInMainRoom ? mSubCloud : mTRTCCloud;                            View itemView = recyclerViewImpl.getChildAt(position);                            if (mIsInMainRoom) {                                mSubRemoteVideoView = itemView.findViewById(R.id.txcvv_main_local);                            } else {                                mRemoteVideoView = itemView.findViewById(R.id.txcvv_main_local);                            }                        }                        switchRoom(roomId, trtcCloud);                    }                    mIsInMainRoom = !mIsInMainRoom;                }                mCurPos = position;            }        });        // Initialize your views here        mTRTCCloud = TRTCCloud.sharedInstance(getApplicationContext());        mSubCloud = mTRTCCloud.createSubCloud();    }    /**     * Call a room entry only during initialization. To switch to a different room later, call switchRoom.     */    private void enterRoom() {        mTRTCCloud.addListener(mTRTCCloudListener);        mSubCloud.addListener(mSubCloudListener);        TRTCCloudDef.TRTCParams mTRTCParams = new TRTCCloudDef.TRTCParams();        mTRTCParams.sdkAppId = GenerateTestUserSig.SDKAPPID;        mTRTCParams.userId = "123";//        mTRTCParams.roomId = Integer.parseInt(roomId);        mTRTCParams.strRoomId = mRoomIds[0];        mTRTCParams.userSig = GenerateTestUserSig.genTestUserSig(mTRTCParams.userId);        mTRTCParams.role = TRTCCloudDef.TRTCRoleAudience;        mTRTCCloud.enterRoom(mTRTCParams, TRTCCloudDef.TRTC_APP_SCENE_LIVE);        mTRTCParams.strRoomId = mRoomIds[1];        mSubCloud.muteAllRemoteAudio(true);        mSubCloud.enterRoom(mTRTCParams, TRTCCloudDef.TRTC_APP_SCENE_LIVE);    }    private TRTCCloudListener mTRTCCloudListener = new TRTCCloudListener() {        public void onEnterRoom(long result) {            if (result == 0) {                // Enter room success            } else {                // Enter room failed            }        }        public void onExitRoom(int reason) {            // Exit room        }        @Override        public void onUserVideoAvailable(String userId, boolean available) {            super.onUserVideoAvailable(userId, available);            if (available) {                mTRTCCloud.startRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, mRemoteVideoView);            } else {                mTRTCCloud.stopRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);            }        }        public void onError(int errCode, String errMsg, Bundle extraInfo) {            // print Error            Log.e("ScrollSwitchRoom", "Error: " + errCode + " " + errMsg);        }        public void onSwitchRoom(long err, String errMsg) {            // Switch room        }    };    private TRTCCloudListener mSubCloudListener = new TRTCCloudListener() {        public void onEnterRoom(long result) {            if (result == 0) {                // Enter room success            } else {                // Enter room failed            }        }        public void onExitRoom(int reason) {            // Exit room        }        @Override        public void onUserVideoAvailable(String userId, boolean available) {            super.onUserVideoAvailable(userId, available);            if (available) {                mSubCloud.startRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, mSubRemoteVideoView);            } else {                mSubCloud.stopRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG);            }        }    };    private void exitRoom() {        mTRTCCloud.stopAllRemoteView();        mTRTCCloud.exitRoom();        mTRTCCloud.setListener(null);        mSubCloud.stopAllRemoteView();        mSubCloud.exitRoom();        mSubCloud.setListener(null);    }    private void switchRoom(String roomId, TRTCCloud trtcCloud) {        TRTCCloudDef.TRTCSwitchRoomConfig config = new TRTCCloudDef.TRTCSwitchRoomConfig();//        config.roomId = Integer.parseInt(roomId);        config.strRoomId = roomId;        trtcCloud.switchRoom(config);    }    public class PageAdapter extends RecyclerView.Adapter<PageAdapter.PageViewHolder> {        private Context context;        public String[] mRoomIds;        public PageAdapter(Context context, String[] roomIds) {            this.context = context;            this.mRoomIds = roomIds;        }        public PageViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {            View view = LayoutInflater.from(context).inflate(R.layout.item_scroll_page, parent, false);            return new PageViewHolder(view);        }        public void onBindViewHolder(@NonNull PageViewHolder holder, int position) {            TextView textView = holder.itemView.findViewById(R.id.tv_room_number);            textView.setText(getString(R.string.switchroom_roomid) + ":" + mRoomIds[position]);        }        public int getItemCount() {            return mRoomIds.length;        }        public int getItemViewType(int position) {            return position;        }        class PageViewHolder extends RecyclerView.ViewHolder {            PageViewHolder(@NonNull View itemView) {                super(itemView);            }        }    }    @Override    protected void onDestroy() {        super.onDestroy();        exitRoom();    }}
```


---
*Source: [https://trtc.io/document/74578](https://trtc.io/document/74578)*
