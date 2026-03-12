# ITRTCStatistics

Copyright (c) 2021 Tencent. All rights reserved.

Module: TRTC audio/video metrics (read-only)

Function: the TRTC SDK reports to you the current real-time audio/video metrics (frame rate, bitrate, lag, etc.) once every two seconds

**ITRTCStatistics**

## StructType

| FuncList | DESC |
| --- | --- |
| [TRTCLocalStatistics](https://www.tencentcloud.com/document/product/647/72272#a2e3e0ed7d189702c1f6466710efb14e) | Local audio/video metrics. |
| [TRTCRemoteStatistics](https://www.tencentcloud.com/document/product/647/72272#31083ca966a8ee092affeab44b65fe9a) | Remote audio/video metrics. |
| [TRTCStatistics](https://www.tencentcloud.com/document/product/647/72272#dc3354e15492d5bac4a773a6e230c9eb) | Network and performance metrics. |

## TRTCLocalStatistics

**TRTCLocalStatistics**

#### Local audio/video metrics.

| EnumType | DESC |
| --- | --- |
| audioBitrate | Field description: local audio bitrate in Kbps, i.e., how much audio data is generated per second |
| audioCaptureState | Field description:Audio equipment collection status(0ï¼Normalï¼1ï¼Long silence detectedï¼2ï¼Broken sound detectedï¼3ï¼Abnormal intermittent sound detected;) |
| audioSampleRate | Field description: local audio sample rate (Hz) |
| frameRate | Field description: local video frame rate in fps, i.e., how many video frames there are per second |
| height | Field description: local video height in px |
| streamType | Field description: video stream type (HD big image \| smooth small image \| substream image) |
| videoBitrate | Field description: local video bitrate in Kbps, i.e., how much video data is generated per second |
| width | Field description: local video width in px |

## TRTCRemoteStatistics

**TRTCRemoteStatistics**

#### Remote audio/video metrics.

| EnumType | DESC |
| --- | --- |
| audioBitrate | Field description: local audio bitrate (Kbps) |
| audioBlockRate | Field description: audio playback lag rate (%)Audio playback lag rate (audioBlockRate) = cumulative audio playback lag duration (audioTotalBlockTime)/total audio playback duration |
| audioPacketLoss | Field description: total packet loss rate (%) of the audio stream` audioPacketLoss ` represents the packet loss rate eventually calculated on the audience side after the audio/video stream goes through the complete transfer linkage of "anchor -> cloud -> audience".The smaller the ` audioPacketLoss `, the better. The packet loss rate of 0 indicates that all data of the audio stream has entirely reached the audience.If ` downLoss ` is ` 0 ` but ` audioPacketLoss ` isn't, there is no packet loss on the linkage of "cloud -> audience" for the audiostream, but there are unrecoverable packet losses on the linkage of "anchor -> cloud". |
| audioSampleRate | Field description: local audio sample rate (Hz) |
| audioTotalBlockTime | Field description: cumulative audio playback lag duration (ms) |
| finalLoss | Field description: total packet loss rate (%) of the audio/video streamDeprecated, please use audioPacketLoss and videoPacketLoss instead. |
| frameRate | Field description: remote video frame rate (fps) |
| height | Field description: remote video height in px |
| jitterBufferDelay | Field description: playback delay (ms)In order to avoid audio/video lags caused by network jitters and network packet disorders, TRTC maintains a playback buffer on the playback side to organize the received network data packets.The size of the buffer is adaptively adjusted according to the current network quality and converted to the length of time in milliseconds, i.e., ` jitterBufferDelay `. |
| point2PointDelay | Field description: end-to-end delay (ms)` point2PointDelay ` represents the delay of "anchor -> cloud -> audience". To be more precise, it represents the delay of the entire linkage of "collection -> encoding -> network transfer -> receiving -> buffering -> decoding -> playback".` point2PointDelay ` works only if both the local and remote SDKs are on version 8.5 or above. If the remote SDK is on a version below 8.5, this value will always be 0 and thus meaningless. |
| remoteNetworkRTT | Field description: round-trip delay (ms) from the SDK to cloudThis value represents the total time it takes to send a network packet from the SDK to the cloud and then send a network packet back from the cloud to the SDK, i.e., the total time it takes for a network packet to go through the linkage of "SDK -> cloud -> SDK".The smaller the value, the better. If ` remoteNetworkRTT ` is below 50 ms, it means a short audio/video call delay; if ` remoteNetworkRTT ` is above 200 ms, it means a long audio/video call delay.It should be explained that ` remoteNetworkRTT ` represents the total time spent on the linkage of "SDK -> cloud -> SDK"; therefore, there is no need to distinguish between ` remoteNetworkUpRTT ` and ` remoteNetworkDownRTT `. |
| remoteNetworkUplinkLoss | Field description: upstream packet loss rate (%) from the SDK to cloudThe smaller the value, the better. If ` remoteNetworkUplinkLoss ` is ` 0% `, the upstream network quality is very good, and the data packets uploaded to the cloud are basically not lost.If ` remoteNetworkUplinkLoss ` is ` 30% `, 30% of the audio/video data packets sent to the cloud by the SDK are lost on the transfer linkage. |
| streamType | Field description: video stream type (HD big image \| smooth small image \| substream image) |
| userId | Field description: user ID |
| videoBitrate | Field description: remote video bitrate (Kbps) |
| videoBlockRate | Field description: video playback lag rate (%)Video playback lag rate (videoBlockRate) = cumulative video playback lag duration (videoTotalBlockTime)/total video playback duration |
| videoPacketLoss | Field description: total packet loss rate (%) of the video stream` videoPacketLoss ` represents the packet loss rate eventually calculated on the audience side after the audio/video stream goes through the complete transfer linkage of "anchor -> cloud -> audience".The smaller the ` videoPacketLoss `, the better. The packet loss rate of 0 indicates that all data of the video stream has entirely reached the audience.If ` downLoss ` is ` 0 ` but ` videoPacketLoss ` isn't, there is no packet loss on the linkage of "cloud -> audience" for the video stream, but there are unrecoverable packet losses on the linkage of "anchor -> cloud". |
| videoTotalBlockTime | Field description: cumulative video playback lag duration (ms) |
| width | Field description: remote video width in px |

## TRTCStatistics

**TRTCStatistics**

#### Network and performance metrics.

| EnumType | DESC |
| --- | --- |
| appCpu | Field description: CPU utilization (%) of the current application, Android 8.0 and above systems are not supported |
| appMemoryUsageInMB | Field description: Memory usage size (MB) of current application |
| downLoss | Field description: downstream packet loss rate (%) from cloud to the SDKThe smaller the value, the better. If ` downLoss ` is ` 0% `, the downstream network quality is very good, and the data packets received from the cloud are basically not lost.If ` downLoss ` is ` 30% `, 30% of the audio/video data packets sent to the SDK by the cloud are lost on the transfer linkage. |
| gatewayRtt | Field description: round-trip delay (ms) from the SDK to gatewayThis value represents the total time it takes to send a network packet from the SDK to the gateway and then send a network packet back from the gateway to the SDK, i.e., the total time it takes for a network packet to go through the linkage of "SDK -> gateway -> SDK".The smaller the value, the better. If ` gatewayRtt ` is below 50 ms, it means a short audio/video call delay; if ` gatewayRtt ` is above 200 ms, it means a long audio/video call delay.It should be explained that ` gatewayRtt ` is invalid for cellular network. |
| localStatisticsArray | Field description: local audio/video statisticsAs there may be three local audio/video streams (i.e., HD big image, smooth small image, and substream image), the local audio/video statistics are an array. |
| localStatisticsArraySize | Field description: ` localStatisticsArray ` array size |
| receivedBytes | Field description: total number of received bytes (including signaling data and audio/video data) |
| remoteStatisticsArray | Field description: remote audio/video statisticsAs there may be multiple concurrent remote users, and each of them may have multiple concurrent audio/video streams (i.e., HD big image, smooth small image, and substream image), the remote audio/video statistics are an array. |
| remoteStatisticsArraySize | Field description: ` remoteStatisticsArray ` array size |
| rtt | Field description: round-trip delay (ms) from the SDK to cloudThis value represents the total time it takes to send a network packet from the SDK to the cloud and then send a network packet back from the cloud to the SDK, i.e., the total time it takes for a network packet to go through the linkage of "SDK -> cloud -> SDK".The smaller the value, the better. If ` rtt ` is below 50 ms, it means a short audio/video call delay; if ` rtt ` is above 200 ms, it means a long audio/video call delay.It should be explained that ` rtt ` represents the total time spent on the linkage of "SDK -> cloud -> SDK"; therefore, there is no need to distinguish between ` upRtt ` and ` downRtt `. |
| sentBytes | Field description: total number of sent bytes (including signaling data and audio/video data) |
| systemCpu | Field description: CPU utilization (%) of the current system, Android 8.0 and above systems are not supported |
| systemMemoryInMB | Field description: Memory size (MB) of current system |
| systemMemoryUsageInMB | Field description: Memory usage size (MB) of current system , iOS and MAC are not supported |
| upLoss | Field description: upstream packet loss rate (%) from the SDK to cloudThe smaller the value, the better. If ` upLoss ` is ` 0% `, the upstream network quality is very good, and the data packets uploaded to the cloud are basically not lost.If ` upLoss ` is ` 30% `, 30% of the audio/video data packets sent to the cloud by the SDK are lost on the transfer linkage. |


---
*Source: [https://trtc.io/document/72272](https://trtc.io/document/72272)*
