# FAQs

### How to Handle Playback Failure Issues?

If the following logs appear during the playback process:

```
License checked failed! tceffect player license required!
```

Please check whether you have applied for the  Gift AR  player License and completed the initialization registration.

### How to Extract Running Logs?

By default, the  Gift AR  player SDK will store running logs. If problems occur during the test, you can extract the logs and give feedback to Tencent Cloud customer service.

#### Android Platform

The log of the  Gift AR  player is stored in the directory: `/sdcard/Android/data/${your_packagename}/files/TCMediaLog`. The log files are named by date. Export the TCMediaLog folder.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/43cf90164d9f11f09bf25254005ef0f7.png)

#### iOS Platform

The logs of the effect player are stored in the sandbox Documents/TCMedialog folder.

1. Export sandbox files. Operation: Open XCode > Window > Devices and Simulators.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ca9f84904d9f11f0ada05254007c27c5.png)

2. Extract the AppData/Documents/TCMedialog folder.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/14099f804da011f0a6ac525400bf7822.png)

### What Should Be Done If There Are No Log Files?

Check whether it is passed false to TCMediaXBase#setLogEnable to disable logs. The default file log is enabled.

### Support for Original Transparent MP4?

Supported. We provide a conversion tool that can easily convert formats such as MP4, image frame sequences, VAP, SVGA, PAG, WebP, and Lottie/PNG into formats supported by the  Gift AR  player, allowing for a seamless playback experience.

### How Does the  Gift AR  Player Achieve a Higher Compression Rate Compared with SVGA or Other Formats When Processing Gift Animations?

The file size of animation files in tcmp4 has an advantage. Evaluation shows that the file size of tcmp4 animation files is reduced by 81.5% compared with that of svga. We use a pure binary data structure, dynamically store bits with a very high compression rate, and adopt technologies such as concentrated compression of similar blocks to achieve a high compression rate.

### Relationship with Tencent Cloud Video Cube. Is It Planned to Be Integrated Into Tencent Cloud Video Cube to Address the Issue of Multiple Players Coexisting?

For versions 2.0 and earlier, the kernel of the  Gift AR  player depends on the Tencent Cloud Video on Demand player. For versions later than 3.0, all necessary SDK features are integrated into the  Gift AR  player. Just purchase the  Gift AR  player to enjoy the complete service without additional dependencies.

### Decoding Mode?

A5: The  Gift AR  player uses hardware decoding. There are mainly two reasons: First, app products generally need to process a large number of video streams simultaneously and transmit them to the audience in real-time. Hardware decoding can quickly decode video streams with high resolution and high bit rate; second, it can reduce the occupancy of CPU resources and improve the stability and efficiency of playback.

### File Too Large Causes Hardware Decoding Failure and Error. How to Resolve?

We provide a flexible sdk integration method. Following the customer's situation, there are the following response plans:

- If you have already connected to the RT-Cube player, after hardware decoding fails, playback is supported using the RT-Cube player's software decoding. Customers do not need to perform any additional processing, as the player sdk has already accommodated this internally.
- If you have not connected to the RT-Cube player, it is recommended to reduce the material resolution for low-end devices. The original material is recommended to be controlled within width Ã height < 1365 Ã 725. Based on the device information, high-end devices use high-resolution materials, while low-end devices use playable low-resolution materials (contact R&D for the source code of resolution judgment).

### What's the Highest Resolution Supported by the Player?

Currently, the player has no limit on the resolution of the picture. Combining image clarity and device performance, 1080p is generally selected.


---
*Source: [https://trtc.io/document/70544](https://trtc.io/document/70544)*
