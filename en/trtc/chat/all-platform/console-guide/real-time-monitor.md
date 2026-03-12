# Real-Time Monitor

## Real-Time Monitoring

> **Note:**The real-time monitoring feature is in beta testing and is still being updated in iteration mode. If you have any feedback or suggestions, [submit a ticket](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=0&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&level3_id=237&radio_title=%E7%99%BB%E5%BD%95%E5%8F%8A%E5%A4%9A%E7%AB%AF%E5%9C%A8%E7%BA%BF%E9%97%AE%E9%A2%98&queue=3235&scene_code=27293&step=2).

1. In the left sidebar, choose**Chat > >**[**Monitor**](https://console.trtc.io/chat/monitor), and **select the target application at the top**.
2. In the overview area, you can view **Current Online Users**, **One-to-One Messages Today**, **Ordinary Group Messages Today**, and **Audio-Video Group Messages Today**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fe2d311fcb5711f09e745254007c27c5.png)

3. In the detailed monitoring data area, data of the 24 hours of the natural day is displayed on the timestamp by default. When the mouse cursor points to the data chart area, you can use the scroll wheel to zoom in the timestamp to view details, drag the timestamp left and right to view the data before and after the time, and click the legend below the timestamp to hide or show the corresponding value in the chart.
  - In the login monitoring area, you can view the login times and login success rate of each client.

> **Note:**Currently, only the login data reported by 4.8.10 or later Chat SDKs for iOS, Android, Windows, and macOS will be displayed. You are advised to upgrade to the [latest version of SDK](https://intl.cloud.tencent.com/document/product/1047/33996).

  - In the message monitoring area, you can view the number of one-to-one or group messages sent by each client and the message sending success rate.

> **Note:**Currently, only the login data reported by 4.8.10 or later Chat SDKs for iOS, Android, Windows, and macOS will be displayed. You are advised to upgrade to the [latest version of SDK](https://intl.cloud.tencent.com/document/product/1047/33996). Currently, the web SDK does not support collecting message statistics by chat type.

  - In the callback monitoring area, you can view the number of callbacks and the callback success rate.
  - In the RESTful API monitoring area, you can view the number of RESTful API requests and the request success rate.
  - In the offline push monitoring area, you can view the number of offline push times and the push success rate.


---
*Source: [https://trtc.io/document/69873](https://trtc.io/document/69873)*
