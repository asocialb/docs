# Stream Mix

CSS provides live stream mix feature, which can synchronously mix multiple streams of input sources into a new stream based on the configured stream mix layout for interactive live streaming. In addition, the stream mix feature has been connected to TencentCloud API 3.0. For more information, please see [CreateCommonMixStream](https://intl.cloud.tencent.com/document/product/267/35997). This document uses examples to describe how to implement live stream mix in different scenarios.

## Notes

- Using stream mix will incur transcoding fees. For details, please see [Live Transcoding (Watermarking, Stream Mixing)](https://intl.cloud.tencent.com/document/product/267/39604).
- To use the mixing and cropping feature, the value of the cropping parameter cannot exceed the value of input stream parameter.

## Supported Features

- Up to **16** concurrent streams can be mixed.
- Up to **5** types of input sources (audio and video, pure audio, pure video, image, and canvas) can be mixed.
- Mixed streams can be output as a new stream.
- Cropping and watermarking are supported.
- Template configuration is supported.
- Recording based on stream mix is supported.
- Stream mix types and positions can be switched in real time.
- Stream mix can be started/canceled seamlessly.

## Common Layout Templates

Common templates include 10, 30, 40, 310,410, 510, and 610. When using them, you do not need to enter the position and length/width parameters of the input stream, and **the original image will be auto-scaled.** You only need to pass in the template ID.

**Figures of common layout templates:**

| Template 10 Preview Image | Template 30 Preview Image |
| --- | --- |
| ![](https://staticintl.cloudcachetci.com/cms/backend-cms/9ac65e4e507911ee974d5254005f490f.jpeg) | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/a231b195507911ee94c3525400d793d0.jpeg) |
| Template 40 Preview Image | Template 310 Preview Image |
| ![](https://staticintl.cloudcachetci.com/cms/backend-cms/34989b9c507911ee84f2525400494e51.jpeg) | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/3a74ad7f507911ee84f2525400494e51.jpeg) |
| Template 410 Preview Image | Template 510 Preview Image |
| ![](https://staticintl.cloudcachetci.com/cms/backend-cms/b2f66b48507911ee974d5254005f490f.jpeg) | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/b6b119b2507911ee974d5254005f490f.jpeg) |
| Template 610 Preview Image |  |
| ![](https://staticintl.cloudcachetci.com/cms/backend-cms/ba64aaac507911ee84f2525400494e51.jpeg) |  |

## Creating Stream Mix Session

### Parameters

For more information, please see [CreateCommonMixStream](https://intl.cloud.tencent.com/document/product/267/35997).

### Scenario 1. Applying for stream mix - using template 20

This example shows you how to use a preset stream mix template to mix streams.

#### Sample input code

```
https://live.tencentcloudapi.com/?Action=CreateCommonMixStream&MixStreamSessionId=test_room&MixStreamTemplateId=20&OutputParams.OutputStreamName=test_stream1&InputStreamList.0.InputStreamName=test_stream1&InputStreamList.0.LayoutParams.ImageLayer=1&InputStreamList.1.InputStreamName=test_stream2&InputStreamList.1.LayoutParams.ImageLayer=2&<Common request parameters>
```

#### Sample output code

```
{  "Response": {    "RequestId": "e8fa8015-0892-40d5-95c4-12a4bc06ed31"  }}
```

#### Stream mix effect for mic connect

![img](https://staticintl.cloudcachetci.com/cms/backend-cms/f1de0933507911ee94c3525400d793d0.jpeg)

### Scenario 2. Applying for stream mix - using template 390

This example shows you how to use a preset stream mix template to mix streams.

#### Sample input code

```
https://live.tencentcloudapi.com/?Action=CreateCommonMixStream&MixStreamSessionId=test_room&MixStreamTemplateId=390&OutputParams.OutputStreamName=test_stream2&InputStreamList.0.InputStreamName=test_stream1&InputStreamList.0.LayoutParams.ImageLayer=1&InputStreamList.0.LayoutParams.InputType=3&InputStreamList.0.LayoutParams.ImageWidth=1920 (canvas width)&InputStreamList.0.LayoutParams.ImageHeight=1080 (canvas height)&InputStreamList.0.LayoutParams.Color=0x000000&InputStreamList.1.InputStreamName=test_stream2&InputStreamList.1.LayoutParams.ImageLayer=2&InputStreamList.2.InputStreamName=test_stream3&InputStreamList.2.LayoutParams.ImageLayer=3&<Common request parameters>
```

#### Sample output code

```
{  "Response": {    "RequestId": "9d8d5837-2273-4936-8661-781aeab9bc9c"  }}
```

#### Stream mix effect for host competition

![img](https://staticintl.cloudcachetci.com/cms/backend-cms/f1df3c8f507911eeabd75254005810a4.jpeg)

### Scenario 3. Custom stream mix

Use the custom layout, where the position parameters `LocationX` and `LocationY` represent the absolute pixel distance between the top-left corner of the small image and that of the background image.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f1bceb81507911ee974d5254005f490f.png)

#### Sample input code

```
https://live.tencentcloudapi.com/?Action=CreateCommonMixStream&MixStreamSessionId=test_room&OutputParams.OutputStreamName=test_stream2&InputStreamList.0.InputStreamName=test_stream1&InputStreamList.0.LayoutParams.ImageLayer=1&InputStreamList.0.LayoutParams.InputType=3&InputStreamList.0.LayoutParams.ImageWidth = 1920&InputStreamList.0.LayoutParams.ImageHeight= 1080&InputStreamList.0.LayoutParams.Color=0x000000&InputStreamList.1.InputStreamName=test_stream2&InputStreamList.1.LayoutParams.ImageLayer=2&InputStreamList.1.LayoutParams.ImageWidth = 640&InputStreamList.1.LayoutParams.ImageHeight= 360&InputStreamList.1.LayoutParams.LocationX= 50&InputStreamList.1.LayoutParams.LocationY= 720&InputStreamList.2.InputStreamName=test_stream3&InputStreamList.2.LayoutParams.ImageLayer=3&InputStreamList.2.LayoutParams.ImageWidth = 640&InputStreamList.2.LayoutParams.ImageHeight= 360&InputStreamList.2.LayoutParams.LocationX= 740&InputStreamList.2.LayoutParams.LocationY= 720&<Common request parameters>
```

#### Sample output code

```
{  "Response": {    "RequestId": "8c443359-ba07-4b81-add8-a6ff54f9bf54"  }}
```

#### Custom stream mix effect

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f1de8b50507911ee94c3525400d793d0.png)

## Canceling Stream Mix

### Parameters

For more information, please see [CancelCommonMixStream](https://intl.cloud.tencent.com/document/product/267/35998).

### Examples

This example shows you how to cancel a stream mix by session ID.

#### Sample input code

```
https://live.tencentcloudapi.com/?Action=CancelCommonMixStream&MixStreamSessionId=test_room
```

#### Sample output code

```
{  "Response": {    "RequestId": "3c140219-cfe9-470e-b241-907877d6fb03"  }}
```

> **Note:**After applying for canceling stream mix, wait at least for 5s before canceling it.After canceling the stream mix, wait at least for half a minute before you can apply for stream mix using the same session ID.

## Error Codes

For stream mix API 3.0, most common error codes have been transformed into the style of [API 3.0 error code](https://www.tencentcloud.com/en/document/product/267/35997#6.-error-code). However, some error codes remain unchanged, which will be provided in the format of `err_code [ $code ],msg [ $message ]` in `Message` and prompted as an `InvalidParameter` error. The causes of specific codes are as detailed below:

| Error Code | Reason | Troubleshooting |
| --- | --- | --- |
| -1 | An error occurred while parsing the input parameters | Check whether the JSON format of the request body is correct.Check whether `InputStreamList` is empty. |
| -2 | Incorrect input parameter | Check whether the image parameter is too large. |
| -3 | The number of streams is incorrect | Check whether the number of input streams is within the range of [1,16]. |
| -4 | Incorrect stream parameter | Check whether the length/width of the input/output stream are within the range of (0,3000).Check whether the number of input streams is within the range of (0,16].Check whether the input stream carries `LayoutParams`.Check whether `InputType` is supported (valid values: 0, 2, 3, 4, 5).Check whether the stream ID length is within the range of (1,80). |
| -11 | Layer error | Check whether the number of layers is the same as the number of input streams.Check whether the layer ID is duplicate.Check whether the layer ID is within the range of (0,16]. |
| -20 | The input parameter does not match the API | Check whether the number of input streams matches the template ID.Check whether the color parameter is correct. |
| -21 | The number of input streams for stream mix is incorrect | Check whether there are at least two input streams. |
| -28 | Failed to get the background length/width | Check whether the canvas length and width are set when setting the canvas.Check whether the background stream exists (stream mix needs to start 5 seconds after push starts). |
| -29 | Incorrect cropping parameter | Check whether the cropping position is out of the stream length/width range. |
| -33 | Incorrect watermark image ID | Check whether the input image ID is set. |
| -34 | Failed to get the URL of the watermark image | Check whether the image has been successfully uploaded and whether the URL has been generated. |
| -111 | The `OutputStreamName` parameter does not match `OutputStreamType` | If `OutputStreamType` is set to `0`, `OutputStreamName` should be in `InputStreamList`.If `OutputStreamType` is set to `1`, `OutputStreamName` should not be in `InputStreamList`. |
| -300 | The output stream ID has already been used | Check whether the current output stream belongs to another stream mix task. |
| -505 | Failed to find the input stream in `upload` | Check whether stream mix is initiated 5 seconds after the push and whether the stream can be played back. |
| -507 | Failed to query the stream length/width parameters | Check whether the canvas length and width are set.Check whether the push succeeds. We recommend you start stream mix 5 seconds after push starts. |
| -508 | Incorrect output stream ID | Check whether different output stream IDs are used by the same `MixStreamSessionId`. |
| -10031 | Failed to trigger stream mix | We recommend you start stream mix 5 seconds after push starts. |
| -30300-31001-31002 | The `sessionid` does not exist when stream mix is canceled | Check whether the `MixStreamSessionId` exists. |
| -31003 | The output stream ID does not match that in `session` | Check the output stream ID entered when stream mix is canceled. |
| -31004 | The output stream bitrate is invalid | Check whether the output stream bitrate is within the range of [1,50000]. |
| Others | For other errors, please [contact customer service](https://www.tencentcloud.com/contact-us) for assistance. | - |

## FAQs

- [How do I ensure that the input streams can be auto scaled with no black bars in the video image during stream mix?](https://intl.cloud.tencent.com/document/product/267/38255)
- [What should I do if error code -505 is returned for stream mix after push?](https://intl.cloud.tencent.com/document/product/267/38255)
- [What will happen if stream mix is not canceled after it is applied for?](https://intl.cloud.tencent.com/document/product/267/38255)
- [Why is the assistant host's video image in the mixed stream not in the expected position?](https://intl.cloud.tencent.com/document/product/267/38255)

> **Note:**For more FAQs about stream mix, please see [On-cloud Stream Mix](https://intl.cloud.tencent.com/document/product/267/38255).


---
*Source: [https://www.tencentcloud.com/document/product/267/37665](https://www.tencentcloud.com/document/product/267/37665)*
