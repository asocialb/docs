# Live FLV Encryption

Most private live streaming or live streaming that requires content security does not require hardware-level security and complex certificate distribution and verification processes. Moreover, in domestic live streaming, the FLV live streaming method is also popular. A secure live streaming solution for FLV is needed.

**Use case**: When using the FLV protocol for playback, it is desired to encrypt the stream content so that hackers cannot capture it through the network, and even if the stream is dumped locally, it cannot be played.

**Implementation plan**: Tencent Cloud CSS has developed its own stream encryption solution. Customers can request FLV encryption by submitting a ticket, specifying the encryption mode (video encryption, audio and video encryption), and Tencent Cloud will encrypt the live stream according to the specified module. When decrypting and playing, customers can obtain the TXEncryptionToken key field through the Tencent Cloud API interface DescribeDRMLicense request, add it to the playback URL parameters, and provide it to the playback SDK for decryption and playback.

**The self-developed encryption and decryption process is as follows:**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3c4e692e5da611ee9ff8525400d917da.png)

**Implementation Method:**For the specific implementation process, please contact Tencent Cloud sales or submit a ticket to contact Tencent Cloud CSS.

**Advantages of the solution:**The entire process is controllable, with product and tool support for keys and encryption/decryption. Tencent Cloud provides Player SDK, which is easy to integrate and has a mature solution.

**Existing issues:**The need to integrate the SDK, only supports custom-developed players. Web and browsers cannot play.

This solution provides two access methods for iOS and Android. Click[here](https://www.tencentcloud.com/document/product/1071/55454) to download the SDK.

## iOS Integration

```
/**Create a Player Instance. */V2TXLivePlayer *player = [[V2TXLivePlayer alloc] init];/** * Set the video rendering View for the player. This control is responsible for displaying the video content. * * @param view Player Rendering View * @return Return Value {@link V2TXLiveCode} *         - V2TXLIVE_OK：Success */[player setRenderView:view];/** * Set the player callback. * * By setting the callback, you can listen to some callback events of the V2TXLivePlayer player, * This includes player status, playback volume callback, audio and video first frame callback, statistical data, warnings, and error information, etc. * @param observer The target object for the player's callback. For more information, please check {@link V2TXLivePlayerObserver} */[player setObserver:self];/** * For key requests, please refer to License acquisition. * Set the Key * * @note The URL in the JSON must be the same as the URL in startLivePlay. The SDK performs a second validation through the URL to avoid incorrect decryption caused by a mismatch between the key and the URL. */NSString *url = @"http://5000.liveplay.myqcloud.com/live/flvtest100_1000.flv?request_type=STDFLV&TXEncryptionToken=ZW5jTW9kZT01JmVuY0tleT0yNmFjZWIxMjViNDczMWNjODRkZTAxZWEyNDA3ZDVmZCZlbmNJVj1iZmEwYmI0NDRhN2NhNDUyMDRjMmNhNzZhYWQyMWFjNA==";/** * Start playing the audio and video stream. * * @param url The playback address of the audio and video stream, supporting RTMP, HTTP-FLV, TRTC，HLS。 * @return Return Value {@link V2TXLiveCode} *         - V2TXLIVE_OK: Operation successful, start connecting and playing *         - V2TXLIVE_ERROR_INVALID_PARAMETER: Operation failed, the URL is not valid *         - V2TXLIVE_ERROR_REFUSED: RTC does not support pushing and pulling the same StreamId on the same device at the same time.[player startLivePlay:url];
```

## Android Integration

```
/** * Create a Player Instance. */V2TXLivePlayer player = new V2TXLivePlayer();/** * Set the video rendering View for the player. This control is responsible for displaying the video content. * * @param view Player rendering View * @return Return value {@link V2TXLiveCode} *         - V2TXLIVE_OK：Success */player.setRenderView(view);/** * Set the player callback.  * * By setting the callback, you can listen to some callback events of the V2TXLivePlayer player, * including player status, playback volume callback, audio and video first frame callback, statistical data, warnings, and error information, etc. * * @param observer the callback target object of the player,For more information, please refer to {@link V2TXLivePlayerObserver} */player.setObserver(this);/** * For key request, please refer to License acquisition * Set the key * * @note The URL in the JSON must be the same as the URL in startLivePlay. The SDK performs a secondary verification through the URL to avoid the situation where the key and URL do not match, causing incorrect decryption. */String url = "http://5000.liveplay.myqcloud.com/live/flvtest100_1000.flv?request_type=STDFLV&TXEncryptionToken=ZW5jTW9kZT01JmVuY0tleT0yNmFjZWIxMjViNDczMWNjODRkZTAxZWEyNDA3ZDVmZCZlbmNJVj1iZmEwYmI0NDRhN2NhNDUyMDRjMmNhNzZhYWQyMWFjNA==";/** * Start playing the audio and video stream.  * * @param url @param url The playback address of the audio and video stream, supporting RTMP, HTTP-FLV, TRTC, and HLS. * @return Return value {@link V2TXLiveCode} *         - V2TXLIVE_OK: Operation succeeded, start connecting and playing *         - V2TXLIVE_ERROR_INVALID_PARAMETER: Operation failed, the URL is not valid *         - V2TXLIVE_ERROR_REFUSED: RTC does not support pushing and pulling the same StreamId on the same device at the same time.。 */player.startLivePlay(url);
```

## License Acquisition

- Set the API interface name as DescribeDRMLicense.
- Interface request domain: drm.tencentcloudapi.com.
- Developers need to specify the DRM type value NORMALAES, and the Track type value SD for encryption, ContentType value LiveVideo, and ContentId as the user's stream id.
  - Example:
  - Test environment request:

```
POST / HTTP/1.1Host: drm.tencentcloudapi.comContent-Type: application/jsonX-TC-Action: DescribeDRMLicense<Public Request Parameters>{ "DrmType":"NORMALAES", "ContentId":"flvtest100", "Tracks":[  "SD" ], "ContentType":"LIVEVIDEO"}
```

  - Request Result:

```
{ "Response": {  "ContentId": "flvtest100",  "TXEncryptionToken": "ZW5jTW9kZT01JmVuY0tleT0yNmFjZWIxMjViNDczMWNjODRkZTAxZWEyNDA3ZDVmZCZlbmNJVj1iZmEwYmI0NDRhN2NhNDUyMDRjMmNhNzZhYWQyMWFjNA==",  "RequestId": "47f336fd-b05a-4192-b1f4-8f9d4c5f76f1" }}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/57047](https://www.tencentcloud.com/document/product/267/57047)*
