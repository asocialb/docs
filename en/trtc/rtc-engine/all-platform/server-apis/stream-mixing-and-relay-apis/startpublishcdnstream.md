# StartPublishCdnStream

## 1. API Description

Domain name for API request: trtc.intl.tencentcloudapi.com.

**API Description**

This API starts a stream mixing and relaying task. This API mixes multiple audio/video streams from a TRTC room into a single stream, encodes it, and then pushes it to CDN server or publishs it into the TRTC room. It also supports relaying a single stream from a TRTC room directly without transcoding.

After success, the API returns a globally unique TaskID. You will need this TaskId in later operations such as updating or stopping the task.

For more details, refer to the document:  [Feature Description](https://trtc.io/zh/document/47858?product=rtcengine) and [FAQs](https://trtc.io/zh/document/36058?product=rtcengine&menulabel=core%20sdk&platform=web) .

Note: You can enable the relay to CDN in the console to monitor events under the CDN relay status. For callback details, see: [Relay to CDN Callback Description](https://trtc.io/zh/document/54913?product=rtcengine&menulabel=core%20sdk&platform=web) .

Starting a relay task may incur the following fees:
MCU stream mixing and transcoding fees: [See Cloud Stream Mixing and Transcoding Pricing](https://trtc.io/zh/document/47631) .

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/647/34263).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: StartPublishCdnStream. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: 2019-07-22. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/647/34263#region-list) supported by the product. This API only supports: ap-guangzhou, ap-hongkong, ap-singapore. |
| SdkAppId | Yes | Integer | The [SDKAppID](https://intl.cloud.tencent.com/document/product/647/37714) of the TRTC room whose streams are relayed. |
| RoomId | Yes | String | The ID of the room whose streams are relayed (the main room). |
| RoomIdType | Yes | Integer | The type of the `RoomId` parameter, which must be the same as the ID type of the room whose streams are relayed. 0: integer; 1: string. |
| AgentParams | Yes | [AgentParams](https://www.tencentcloud.com/document/api/647/36760#AgentParams) | The information of the relaying robot in the room. |
| WithTranscoding | Yes | Integer | Whether to transcode the streams. `0`: No. `1`: Yes. This parameter determines whether transcoding fees are charged. If it is `0`, streams will only be relayed, and no transcoding fees will be incurred. If it is `1`, streams will be transcoded before being relayed, and transcoding fees will be incurred. |
| AudioParams | No | [McuAudioParams](https://www.tencentcloud.com/document/api/647/36760#McuAudioParams) | The audio encoding parameters. Because audio is always transcoded (no fees are incurred), this parameter is required when you start a relay task. |
| VideoParams | No | [McuVideoParams](https://www.tencentcloud.com/document/api/647/36760#McuVideoParams) | The video encoding parameters for relaying. If you do not pass this parameter, only audio will be relayed. |
| SingleSubscribeParams | No | [SingleSubscribeParams](https://www.tencentcloud.com/document/api/647/36760#SingleSubscribeParams) | The information of a single stream relayed. When you relay a single stream, set `WithTranscoding` to 0. |
| PublishCdnParams.N | No | Array of [McuPublishCdnParam](https://www.tencentcloud.com/document/api/647/36760#McuPublishCdnParam) | The information of the CDNs to relay to. You need to specify at least one between this parameter and `FeedBackRoomParams.N`. |
| SeiParams | No | [McuSeiParams](https://www.tencentcloud.com/document/api/647/36760#McuSeiParams) | The stream mixing SEI parameters. |
| FeedBackRoomParams.N | No | Array of [McuFeedBackRoomParams](https://www.tencentcloud.com/document/api/647/36760#McuFeedBackRoomParams) | The information of the room to which streams are relayed. Between this parameter and `PublishCdnParams`, you must specify at least one. Please note that relaying to a TRTC room is only supported in some SDK versions. For details, please contact technical support. |
| RecordParams | No | [McuRecordParams](https://www.tencentcloud.com/document/api/647/36760#McuRecordParams) | Relay Recording Parameters. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | The task ID, which is generated by the Tencent Cloud server. You need to pass in the task ID when making a request to update or stop a relaying task. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Mix AV & Relay

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: StartPublishCdnStream
<Common request parameters>

{
    "AgentParams": {
        "MaxIdleTime": 30,
        "UserSig": "eJw1zV8LgjAUBfCvInsO2dStGfQSQUb2pFJvsnLJJZW1LekPffdc6X08v8O5b5Snmd9LjRYeCnyMZt4vgUp2Fi7wB6vtuVRC207q0kpjSzIVTXUVSkE11EiEMeE8ZGw0*VCg5SCcDeRuBAutiwkLeRRwOo*nMajduy5O*gIaus9qel9vX*lJbHJmyDMxuKFFI27tsT*I1S6pl*jzBb*IOTE_",
        "UserId": "trtc_partner_test_1"
    },
    "AudioParams": {
        "AudioEncode": {
            "SampleRate": 48000,
            "Codec": 0,
            "BitRate": 64,
            "Channel": 2
        }
    },
    "VideoParams": {
        "VideoEncode": {
            "Height": 720,
            "Width": 1280,
            "Fps": 15,
            "BitRate": 1536,
            "Gop": 2
        },
        "LayoutParams": {
            "PureAudioHoldPlaceMode": 0,
            "MixLayoutMode": 4,
            "MixLayoutList": [
                {
                    "LocationX": 0,
                    "LocationY": 0,
                    "UserMediaStream": {
                        "StreamType": 0,
                        "UserInfo": {
                            "RoomIdType": 0,
                            "RoomId": "295066",
                            "UserId": "Trtc_User_0"
                        }
                    },
                    "ZOrder": 0,
                    "ImageHeight": 720,
                    "ImageWidth": 640,
                    "RenderMode": 0
                },
                {
                    "LocationX": 640,
                    "LocationY": 0,
                    "UserMediaStream": {
                        "StreamType": 0,
                        "UserInfo": {
                            "RoomIdType": 0,
                            "RoomId": "295066",
                            "UserId": "Trtc_User_1"
                        }
                    },
                    "ZOrder": 0,
                    "ImageHeight": 720,
                    "ImageWidth": 640,
                    "RenderMode": 0
                }
            ]
        },
        "BackGroundColor": "0xFF0000",
        "WaterMarkList": [
            {
                "WaterMarkType": 0,
                "WaterMarkImage": {
                    "LocationX": 64,
                    "LocationY": 64,
                    "WaterMarkHeight": 64,
                    "WaterMarkWidth": 64,
                    "WaterMarkUrl": "https://xkt-course-1304449343.cos.ap-beijing.myqcloud.com/test/mark/37f9eb62-ca72-430e-bfca-e700b59b20e0.png",
                    "ZOrder": 3
                }
            }
        ]
    },
    "PublishCdnParams": [
        {
            "PublishCdnUrl": "rtmp://3891.livepush.myqcloud.com/live/trtc_publishcdn_test1",
            "IsTencentCdn": 1
        }
    ],
    "RoomIdType": 0,
    "SdkAppId": 1400188366,
    "WithTranscoding": 1,
    "RoomId": "295066"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskId": "-m97l2ZU7vxyBSmXYsRx1Xy9Kf4bVVfbbhSKC4K-4pycoZWKv542xbi139uTvGt1zAHoAQ..",
        "RequestId": "b934c535-8d82-4f52-bd52-a1cbb043c4be"
    }
}
```

### Example2 Mix Audio & Relay

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: StartPublishCdnStream
<Common request parameters>

{
    "AgentParams": {
        "MaxIdleTime": 30,
        "UserSig": "eJw1zV8LgjAUBfCvInsO2dStGfQSQUb2pFJvsnLJJZW1LekPffdc6X08v8O5b5Snmd9LjRYeCnyMZt4vgUp2Fi7wB6vtuVRC207q0kpjSzIVTXUVSkE11EiEMeE8ZGw0*VCg5SCcDeRuBAutiwkLeRRwOo*nMajduy5O*gIaus9qel9vX*lJbHJmyDMxuKFFI27tsT*I1S6pl*jzBb*IOTE_",
        "UserId": "trtc_partner_test_1"
    },
    "AudioParams": {
        "AudioEncode": {
            "SampleRate": 48000,
            "Codec": 0,
            "BitRate": 64,
            "Channel": 2
        },
        "SubscribeAudioList": [
            {
                "UserInfo": {
                    "RoomIdType": 0,
                    "RoomId": "295066",
                    "UserId": "Trtc_User_0"
                }
            },
            {
                "UserInfo": {
                    "RoomIdType": 0,
                    "RoomId": "295066",
                    "UserId": "Trtc_User_1"
                }
            }
        ]
    },
    "PublishCdnParams": [
        {
            "PublishCdnUrl": "rtmp://3891.livepush.myqcloud.com/live/trtc_publishcdn_test1",
            "IsTencentCdn": 1
        }
    ],
    "RoomIdType": 0,
    "SdkAppId": 1400188366,
    "WithTranscoding": 1,
    "RoomId": "295066"
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "388014ec-a0b8-4b8f-86bc-1f467448f5f0",
        "TaskId": "-m9lnV5U7nj4rkLBWMXF9n8-EohONCXbalWuLYK-4pycoZWQndibcqSVnrlqKF5om7EIDVk4awE."
    }
}
```

### Example3 Relay AV

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: StartPublishCdnStream
<Common request parameters>

{
    "AgentParams": {
        "MaxIdleTime": 30,
        "UserSig": "eJw1zV8LgjAUBfCvInsO2dStGfQSQUb2pFJvsnLJJZW1LekPffdc6X08v8O5b5Snmd9LjRYeCnyMZt4vgUp2Fi7wB6vtuVRC207q0kpjSzIVTXUVSkE11EiEMeE8ZGw0*VCg5SCcDeRuBAutiwkLeRRwOo*nMajduy5O*gIaus9qel9vX*lJbHJmyDMxuKFFI27tsT*I1S6pl*jzBb*IOTE_",
        "UserId": "trtc_partner_test_1"
    },
    "AudioParams": {
        "AudioEncode": {
            "SampleRate": 48000,
            "Codec": 0,
            "BitRate": 64,
            "Channel": 2
        }
    },
    "VideoParams": {
        "VideoEncode": {
            "Height": 720,
            "Width": 1280,
            "Fps": 15,
            "BitRate": 1536,
            "Gop": 2
        }
    },
    "SingleSubscribeParams": {
        "UserMediaStream": {
            "StreamType": 0,
            "UserInfo": {
                "RoomIdType": 0,
                "RoomId": "295066",
                "UserId": "Trtc_User_0"
            }
        }
    },
    "PublishCdnParams": [
        {
            "PublishCdnUrl": "rtmp://3891.livepush.myqcloud.com/live/trtc_publishcdn_test1",
            "IsTencentCdn": 1
        }
    ],
    "RoomIdType": 0,
    "SdkAppId": 1400188366,
    "WithTranscoding": 0,
    "RoomId": "295066"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskId": "-m97l2ZU7tq6nEsHR89259B8aCDblqnbGhWKC4K-4pycoZWpyHnld1jC9aCD+EU7V8WRAQ..",
        "RequestId": "f23d95bf-ddaf-4d0c-86c0-6bf50c74c0a0"
    }
}
```

### Example4 Relay Audio

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: StartPublishCdnStream
<Common request parameters>

{
    "AgentParams": {
        "MaxIdleTime": 30,
        "UserSig": "eJw1zV8LgjAUBfCvInsO2dStGfQSQUb2pFJvsnLJJZW1LekPffdc6X08v8O5b5Snmd9LjRYeCnyMZt4vgUp2Fi7wB6vtuVRC207q0kpjSzIVTXUVSkE11EiEMeE8ZGw0*VCg5SCcDeRuBAutiwkLeRRwOo*nMajduy5O*gIaus9qel9vX*lJbHJmyDMxuKFFI27tsT*I1S6pl*jzBb*IOTE_",
        "UserId": "trtc_partner_test_1"
    },
    "AudioParams": {
        "AudioEncode": {
            "SampleRate": 48000,
            "Codec": 0,
            "BitRate": 64,
            "Channel": 2
        }
    },
    "SingleSubscribeParams": {
        "UserMediaStream": {
            "StreamType": 0,
            "UserInfo": {
                "RoomIdType": 0,
                "RoomId": "295066",
                "UserId": "Trtc_User_0"
            }
        }
    },
    "PublishCdnParams": [
        {
            "PublishCdnUrl": "rtmp://3891.livepush.myqcloud.com/live/trtc_publishcdn_test1",
            "IsTencentCdn": 1
        }
    ],
    "RoomIdType": 0,
    "SdkAppId": 1400188366,
    "WithTranscoding": 0,
    "RoomId": "295066"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskId": "-m97l2ZU7r57nZBesMa84KgzxhH0OBbbCRaKC4K-4pycoZW7yFPtusNuZOen1Ca0qtQQAQ..",
        "RequestId": "ef089f8b-d0d1-4131-894d-4edd68d61605"
    }
}
```

### Example5 Mix AV, then Feedback

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: StartPublishCdnStream
<Common request parameters>

{
    "AgentParams": {
        "MaxIdleTime": 30,
        "UserSig": "eJw1zV8LgjAUBfCvInsO2dStGfQSQUb2pFJvsnLJJZW1LekPffdc6X08v8O5b5Snmd9LjRYeCnyMZt4vgUp2Fi7wB6vtuVRC207q0kpjSzIVTXUVSkE11EiEMeE8ZGw0*VCg5SCcDeRuBAutiwkLeRRwOo*nMajduy5O*gIaus9qel9vX*lJbHJmyDMxuKFFI27tsT*I1S6pl*jzBb*IOTE_",
        "UserId": "trtc_partner_test_1"
    },
    "AudioParams": {
        "AudioEncode": {
            "SampleRate": 48000,
            "Codec": 0,
            "BitRate": 64,
            "Channel": 2
        }
    },
    "VideoParams": {
        "VideoEncode": {
            "Height": 720,
            "Width": 1280,
            "Fps": 15,
            "BitRate": 1536,
            "Gop": 2
        },
        "LayoutParams": {
            "PureAudioHoldPlaceMode": 0,
            "MixLayoutMode": 4,
            "MixLayoutList": [
                {
                    "LocationX": 0,
                    "LocationY": 0,
                    "UserMediaStream": {
                        "StreamType": 0,
                        "UserInfo": {
                            "RoomIdType": 0,
                            "RoomId": "295066",
                            "UserId": "Trtc_User_0"
                        }
                    },
                    "ZOrder": 0,
                    "ImageHeight": 720,
                    "ImageWidth": 640,
                    "RenderMode": 0
                },
                {
                    "LocationX": 640,
                    "LocationY": 0,
                    "UserMediaStream": {
                        "StreamType": 0,
                        "UserInfo": {
                            "RoomIdType": 0,
                            "RoomId": "295066",
                            "UserId": "Trtc_User_1"
                        }
                    },
                    "ZOrder": 0,
                    "ImageHeight": 720,
                    "ImageWidth": 640,
                    "RenderMode": 0
                }
            ]
        },
        "BackGroundColor": "0xFF0000",
        "WaterMarkList": [
            {
                "WaterMarkType": 0,
                "WaterMarkImage": {
                    "LocationX": 64,
                    "LocationY": 64,
                    "WaterMarkHeight": 64,
                    "WaterMarkWidth": 64,
                    "WaterMarkUrl": "https://xkt-course-1304449343.cos.ap-beijing.myqcloud.com/test/mark/37f9eb62-ca72-430e-bfca-e700b59b20e0.png",
                    "ZOrder": 3
                }
            }
        ]
    },
    "FeedBackRoomParams": [
        {
            "RoomId": "630777",
            "RoomIdType": 0,
            "UserId": "trtc_partner_test_2",
            "UserSig": "eJwtjEELgjAYhv-Ldy10m7mtQYcQOtklU6mLSFs1LVnzq4Tovwfa8Xmel-cD*zQLXsaDAhYQmI9stenQnu2o0eOpcrXHzvgKTY8V*8963dbOWQ2KLgihUkacTwXt3YCigpIlo0KyyZrBWW9ARZyQ-4O9gIJrYfK365M85PEw02HZPneNaJJbg4-1Nj6KQqZZacVhI1fw-QEkCzYe"
        }
    ],
    "RoomIdType": 0,
    "SdkAppId": 1400188366,
    "WithTranscoding": 1,
    "RoomId": "295066"
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "921e9cf6-b77c-4a7a-ab0e-c66a3e66fc59",
        "TaskId": "-m9lnV5U7n7TwoLKSsii1JivUn7DLDDbP16uLYK-4pycoZWQndib8GQJZEMMXFyOHe9Ds6WfxAE."
    }
}
```

### Example6 Mix AV & Relay with layout

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: StartPublishCdnStream
<Common request parameters>

{
    "AgentParams": {
        "MaxIdleTime": 30,
        "UserSig": "eJw1zV8LgjAUBfCvInsO2dStGfQSQUb2pFJvsnLJJZW1LekPffdc6X08v8O5b5Snmd9LjRYeCnyMZt4vgUp2Fi7wB6vtuVRC207q0kpjSzIVTXUVSkE11EiEMeE8ZGw0*VCg5SCcDeRuBAutiwkLeRRwOo*nMajduy5O*gIaus9qel9vX*lJbHJmyDMxuKFFI27tsT*I1S6pl*jzBb*IOTE_",
        "UserId": "trtc_partner_test_1"
    },
    "AudioParams": {
        "AudioEncode": {
            "SampleRate": 48000,
            "Codec": 0,
            "BitRate": 64,
            "Channel": 2
        }
    },
    "VideoParams": {
        "VideoEncode": {
            "Height": 720,
            "Width": 1280,
            "Fps": 15,
            "BitRate": 1536,
            "Gop": 2
        },
        "LayoutParams": {
            "PureAudioHoldPlaceMode": 0,
            "MixLayoutMode": 4,
            "MixLayoutList": [
                {
                    "LocationX": 0,
                    "LocationY": 0,
                    "UserMediaStream": {
                        "StreamType": 0,
                        "UserInfo": {
                            "RoomIdType": 0,
                            "RoomId": "295066",
                            "UserId": "Trtc_User_0"
                        }
                    },
                    "ZOrder": 0,
                    "ImageHeight": 720,
                    "ImageWidth": 640,
                    "RenderMode": 0
                },
                {
                    "LocationX": 640,
                    "LocationY": 0,
                    "UserMediaStream": {
                        "StreamType": 0,
                        "UserInfo": {
                            "RoomIdType": 0,
                            "RoomId": "295066",
                            "UserId": "Trtc_User_1"
                        }
                    },
                    "ZOrder": 0,
                    "ImageHeight": 720,
                    "ImageWidth": 640,
                    "RenderMode": 0
                }
            ]
        },
        "BackGroundColor": "0xFF0000",
        "WaterMarkList": [
            {
                "WaterMarkType": 0,
                "WaterMarkImage": {
                    "LocationX": 64,
                    "LocationY": 64,
                    "WaterMarkHeight": 64,
                    "WaterMarkWidth": 64,
                    "WaterMarkUrl": "https://xkt-course-1304449343.cos.ap-beijing.myqcloud.com/test/mark/37f9eb62-ca72-430e-bfca-e700b59b20e0.png",
                    "ZOrder": 3
                }
            }
        ]
    },
    "SeiParams": {
        "LayoutVolume": {
            "AppData": "layout_sei_test",
            "PayloadType": 100,
            "Interval": 1000,
            "FollowIdr": 1
        }
    },
    "PublishCdnParams": [
        {
            "PublishCdnUrl": "rtmp://3891.livepush.myqcloud.com/live/trtc_publishcdn_test1",
            "IsTencentCdn": 1
        }
    ],
    "RoomIdType": 0,
    "SdkAppId": 1400188366,
    "WithTranscoding": 1,
    "RoomId": "295066"
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "6dfc18cc-2123-4a11-9591-f1e873fbbd65",
        "TaskId": "-m9lnV5U7nzo2Xwh48Dc-YCDrR5Bk8DbJ1WrLYK-4pycoZWQndibrNig9cq-7ljX4SenbKWlZAE."
    }
}
```

### Example7 Cross-Room Stream Relaying

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: StartPublishCdnStream
<common request parameters>

{
    "AgentParams": {
        "MaxIdleTime": 30,
        "UserSig": "eJw1zV8LgjAUBfCvInsO2dStGfQSQUb2pFJvsnLJJZW1LekPffdc6X08v8O5b5Snmd9LjRYeCnyMZt4vgUp2Fi7wB6vtuVRC207q0kpjSzIVTXUVSkE11EiEMeE8ZGw0*VCg5SCcDeRuBAutiwkLeRRwOo*nMajduy5O*gIaus9qel9vX*lJbHJmyDMxuKFFI27tsT*I1S6pl*jzBb*IOTE_",
        "UserId": "trtc_partner_test_1"
    },
    "AudioParams": {
        "AudioEncode": {
            "SampleRate": 48000,
            "Codec": 0,
            "BitRate": 64,
            "Channel": 2
        },
        "SubscribeAudioList": [
            {
                "UserInfo": {
                    "RoomIdType": 0,
                    "RoomId": "295066",
                    "UserId": "Trtc_User_0"
                }
            },
            {
                "UserInfo": {
                    "RoomIdType": 0,
                    "RoomId": "295067",
                    "UserId": "Trtc_User_1"
                }
            }
        ]
    },
    "VideoParams": {
        "VideoEncode": {
            "Height": 720,
            "Width": 1280,
            "Fps": 15,
            "BitRate": 1536,
            "Gop": 2
        },
        "LayoutParams": {
            "PureAudioHoldPlaceMode": 0,
            "MixLayoutMode": 4,
            "MixLayoutList": [
                {
                    "LocationX": 0,
                    "LocationY": 0,
                    "UserMediaStream": {
                        "StreamType": 0,
                        "UserInfo": {
                            "RoomIdType": 0,
                            "RoomId": "295066",
                            "UserId": "Trtc_User_0"
                        }
                    },
                    "ZOrder": 0,
                    "ImageHeight": 720,
                    "ImageWidth": 640,
                    "RenderMode": 0
                },
                {
                    "LocationX": 640,
                    "LocationY": 0,
                    "UserMediaStream": {
                        "StreamType": 0,
                        "UserInfo": {
                            "RoomIdType": 0,
                            "RoomId": "295067",
                            "UserId": "Trtc_User_1"
                        }
                    },
                    "ZOrder": 0,
                    "ImageHeight": 720,
                    "ImageWidth": 640,
                    "RenderMode": 0
                }
            ]
        },
        "BackGroundColor": "0xFF0000",
        "WaterMarkList": [
            {
                "WaterMarkType": 0,
                "WaterMarkImage": {
                    "LocationX": 64,
                    "LocationY": 64,
                    "WaterMarkHeight": 64,
                    "WaterMarkWidth": 64,
                    "WaterMarkUrl": "https://xkt-course-1304449343.cos.ap-beijing.myqcloud.com/test/mark/37f9eb62-ca72-430e-bfca-e700b59b20e0.png",
                    "ZOrder": 3
                }
            }
        ]
    },
    "PublishCdnParams": [
        {
            "PublishCdnUrl": "rtmp://3891.livepush.myqcloud.com/live/trtc_publishcdn_test1",
            "IsTencentCdn": 1
        }
    ],
    "RoomIdType": 0,
    "SdkAppId": 1400188366,
    "WithTranscoding": 1,
    "RoomId": "295066"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskId": "-m97l2ZU7vxyBSmXYsRx1Xy9Kf4bVVfbbhSKC4K-4pycoZWKv542xbi139uTvGt1zAHoAQ..",
        "RequestId": "b934c535-8d82-4f52-bd52-a1cbb043c4be"
    }
}
```

## 5. Developer Resources

### SDK

TencentCloud API 3.0 integrates SDKs that support various programming languages to make it easier for you to call APIs.

Tencent Cloud SDK 3.0 for Python
Tencent Cloud SDK 3.0 for Java
Tencent Cloud SDK 3.0 for PHP
Tencent Cloud SDK 3.0 for Go
Tencent Cloud SDK 3.0 for Node.js
Tencent Cloud SDK 3.0 for .NET
Tencent Cloud SDK 3.0 for C++

### Command Line Interface

Tencent Cloud CLI 3.0

## 6. Error Code

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/647/34270#common-error-codes).

| Error Code | Description |
| --- | --- |
| AuthFailure | CAM signature/authentication error. |
| AuthFailure.UnRealNameAuthenticated | Identity verification has not been completed, so this operation is not allowed. |
| AuthFailure.UnauthorizedOperation | CAM authentication failed. |
| AuthFailure.UnsupportedOperation | Unsupported operation. |
| FailedOperation | Operation failed. |
| FailedOperation.RestrictedConcurrency | Maximum number of concurrent on-cloud recording tasks reached. Contact us to raise the limit. |
| InternalError | Internal error. |
| InvalidParameter | Parameter error. |
| InvalidParameter.SdkAppId | `SdkAppId` is incorrect. |
| MissingParameter | Missing parameter. |
| ResourceNotFound | The resource does not exist. |
| UnsupportedOperation | Unsupported operation. |


---
*Source: [https://trtc.io/document/48247](https://trtc.io/document/48247)*
