# Monitor Conference Status

This article introduces the use of TUIRoomKit component meeting status callback.

## Conference status monitoring

If your business needs to **monitor the status of a conference**, such as the start and end of a conference, you can refer to the following code:

Androidï¼Javaï¼

Androidï¼Kotlinï¼

iOS (Swift)

iOS (OC)

```
ConferenceDefine.ConferenceObserver observer = new ConferenceDefine.ConferenceObserver() {
    @Override
    public void onConferenceStarted(TUIRoomDefine.RoomInfo roomInfo, TUICommonDefine.Error error, String message) {
    }

    @Override
    public void onConferenceJoined(TUIRoomDefine.RoomInfo roomInfo, TUICommonDefine.Error error, String message) {
    }

    @Override
    public void onConferenceExisted(String roomId) {
    }

    @Override
    public void onConferenceFinished(String roomId) {
    }
};
ConferenceSession.sharedInstance().addObserver(observer);
```

```
val observer: ConferenceObserver = object : ConferenceObserver() {
    override fun onConferenceStarted(roomInfo: TUIRoomDefine.RoomInfo?, error: TUICommonDefine.Error?, message: String?) {
    }

    override fun onConferenceJoined(roomInfo: TUIRoomDefine.RoomInfo?, error: TUICommonDefine.Error?, message: String?) {
    }

    override fun onConferenceExisted(roomId: String?) {
    }

    override fun onConferenceFinished(roomId: String?) {
    }
}
ConferenceSession.sharedInstance().addObserver(observer)
```

```
class EnterRoomViewController: UIViewController {    override func viewDidLoad() {        super.viewDidLoad()        ConferenceSession.sharedInstance.addObserver(observer: self)    }}extension EnterRoomViewController: ConferenceObserver {    // start conference callback    func onConferenceStarted(roomInfo: TUIRoomInfo, error: TUIError, message: String) {        // Your code here     }    // join conference callback    func onConferenceJoined(roomInfo: TUIRoomInfo, error: TUIError, message: String) {        // Your code here    }    // conference has been disbanded callback    func onConferenceFinished(conferenceId: String) {        // Your code here    }    // exit conference callback    func onConferenceExited(conferenceId: String) {       // Your code here    }}
```

```
@interface EnterRoomViewController () <ConferenceObserver>@end@implementation EnterRoomViewController- (void)viewDidLoad {        [super viewDidLoad];       [[ConferenceSession sharedInstance] addObserver:self]; } #pragma mark - ConferenceObserver// start conference callback- (void)onConferenceStartedWithRoomInfo:(TUIRoomInfo *)roomInfo error:(TUIError *)error message:(NSString *)message {    // Your code here}// join conference callback- (void)onConferenceJoinedWithRoomInfo:(TUIRoomInfo *)roomInfo error:(TUIError *)error message:(NSString *)message {    // Your code here}// conference disbanded callback- (void)onConferenceFinishedWithConferenceId:(NSString *)conferenceId {    // Your code here}// exit conference callback- (void)onConferenceExitedWithConferenceId:(NSString *)conferenceId {    // Your code here}@end
```


---
*Source: [https://trtc.io/document/63272](https://trtc.io/document/63272)*
