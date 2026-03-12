# Custom Co-Guest and Co-Host View

This document mainly introduces how to use the `LiveStreamCore` module's `LiveCoreView` to implement a custom co-hosting and connection view.

## Prerequisites

Before using `LiveStreamCore`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67475#) to LiveStreamCore to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding LiveCoreView to the View

You need to first import the `LiveStreamCore` module, then create a `LiveCoreView` view object and add it to your view.

iOS

Android

```
LiveStreamCore
```

```
public class CustomizeConnectionActivity extends AppCompatActivity {    @Override    protected void onCreate(@Nullable Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        LiveCoreView liveCoreView = new LiveCoreView(this);        addContentView(liveCoreView,                new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT));    }}
```

### Step 2: Customizing Co-Hosting View

iOS

Android

If you want to customize the co-hosting and connection view, you need to implement the `LiveCoreView` delegate `VideoViewDelegate`.

```
protocol VideoViewDelegate {    func createCoGuestView(userInfo: TUIUserInfo) -> UIView?    func updateCoGuestView(userInfo: TUIUserInfo, modifyFlag: UserInfoModifyFlag, coGuestView: UIView)    func createCoHostView(coHostUser: TUIConnectionUser) -> UIView?    func updateCoHostView(coHostUser: TUIConnectionUser, modifyFlag: UserInfoModifyFlag, coHostView: UIView)}
```

The following is a usage example:

```
SGSeatViewDelegate
```

If you want to customize the co-hosting and connection view, you need to implement the `LiveCoreView` adapter VideoViewAdapter.

```
public interface VideoViewAdapter {    View createCoGuestView(TUIRoomDefine.UserInfo var1);    void updateCoGuestView(TUIRoomDefine.UserInfo var1, List<UserInfoModifyFlag> var2, View var3);    View createCoHostView(CoHostUser var1);    void updateCoHostView(CoHostUser var1, List<UserInfoModifyFlag> var2, View var3);}
```

The following is a usage example:

```
liveCoreView.setVideoViewAdapter(new LiveCoreViewDefine.VideoViewAdapter() {    @Override    public View createCoGuestView(TUIRoomDefine.UserInfo userInfo) {        TextView coGuestUserName = new TextView(CustomizeConnectionActivity.this);        coGuestUserName.setText(userInfo.userName);        return coGuestUserName;    }    @Override    public void updateCoGuestView(TUIRoomDefine.UserInfo userInfo, List<LiveCoreViewDefine.UserInfoModifyFlag> list, View view) {    }    @Override    public View createCoHostView(LiveCoreViewDefine.CoHostUser coHostUser) {        TextView coHostUserName = new TextView(CustomizeConnectionActivity.this);        coHostUserName.setText(coHostUser.connectionUser.userName);        return coHostUserName;    }    @Override    public void updateCoHostView(LiveCoreViewDefine.CoHostUser coHostUser, List<LiveCoreViewDefine.UserInfoModifyFlag> list, View view) {    }});
```


---
*Source: [https://trtc.io/document/67469](https://trtc.io/document/67469)*
