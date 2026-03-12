# Live Stream Mixing Error `InvalidParameter.OtherError`

## Error

`InvalidParameter.OtherError` error occurs when stream mixing is initiated.

## Possible Causes

- The width or height of an input stream image exceeds 2000 px.
- The concurrent channels of a stream exceed 20.
- An account of “Channel Mode” is using the `CreateCommonMixStream` API.

## Solutions

The following describes common troubleshooting methods for suberror codes.

#### Error 1: `"Message":"InnerErrCode : [ -10021 ],IrnerErrMsg: [ Params Error ]"`

1. Use FFplay to play back a live stream and view its resolution. The resolution below is `1920 x 1080`, which will not cause an error.
Command: `ffplay -i "playback URL"`.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/5568cc2ad44f11ee89c5525400170219.png)
2. [Use VLC](https://intl.cloud.tencent.com/document/product/267/32483) to play back the live stream:
  - Enable VLC, click **Media** > **Open Network Stream** > **Network**, and then enter a URL. After confirmation, you can pull the live stream.
  - You can view the live stream resolution in **Tools** > **Media Information** > **Codec**.

#### Error 2: `"Message":"InnerErrCode:[ -41 ],InnerErrMsg: [ ]"`

Suppose a host creates a stream mixing session, and then exits the session without canceling it. The same stream name will be used by multiple stream mixing sessions if the host enter other sessions, which will trigger this error.

When a stream mixing session is interrupted, the stream mixing screen will stop at the last frame if the background stream is not interrupted. You can call the `CancelCommonMixStream` API to make the last frame not to stay on the screen. If the background stream is interrupted, the entire screen will be stuck.

- If all input streams are successfully pushed with the same stream names within 15 minutes, the stream mixing session will be recovered.
- If all input streams are interrupted, the stream mixing session will be automatically canceled after 15 minutes.

#### Error 3: `"Message":"InnerErrCode:[ -4 ],InnerErrMsg: [ get liveconfig failed! ]"`

You can upgrade the CSS console to the latest version (live stream code mode) to fix this error.

#### Error 4: `"Message":"input stream num is not match the template id!"`

For details about parameters and directions, please see [CreateCommonMixStream API > MixStreamTemplateId](https://intl.cloud.tencent.com/document/product/267/35997).

#### Error 5: `"Message":"InnerErrCode:[ -300 ],InnerErrMsg: [ outputstreamid not avaliable, outputstreamid alread use as background in other sessionid ]"`

You can set a **different**`OutputStreamName` for session B to fix this error.

#### Error 6: `"Message": "InnerErrCode:[ -2 ],InnerErrMsg: [ small picture out of the background ]"`

- For how to set `LocationX`, please see [CommonMixLayoutParams > LocationX](https://intl.cloud.tencent.com/document/product/267/30767#CommonMixLayoutParams).
- For how to set `LocationY`, please see [CommonMixLayoutParams > LocationX](https://intl.cloud.tencent.com/document/product/267/30767#CommonMixLayoutParams).
- For more examples about using stream mixing templates, please see [Live Stream Mixing](https://intl.cloud.tencent.com/document/product/267/37665).

#### Error 7: `"Message": "InnerErrCode:[ -111 ],InnerErrMsg: [ output_stream_type is [0],but output_stream_id xxxxx is not in input stream list ]"`

- If you set `OutputStreamType` to `0` or leave it empty, you need to set `OutputStreamName` to one of the input stream names.
- If you want to use a new `OutputStreamName`, set `OutputStreamType` to `1`.
- When you set `OutputStreamType` to `1`, you cannot set `OutputStreamName` to any stream names in both `InputStreamList` and the live streaming backend.


---
*Source: [https://www.tencentcloud.com/document/product/267/40599](https://www.tencentcloud.com/document/product/267/40599)*
