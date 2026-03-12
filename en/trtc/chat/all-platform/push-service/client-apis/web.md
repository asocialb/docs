# Web

## API Overview

| API | Description |
| --- | --- |
| `registerPush` | Register push service (must call this API to use push service only after obtaining user consent for the privacy policy). |
| `unRegisterPush` | Disable push service. |
| `addPushListener` | Add a Push Listener. |
| `removePushListener` | Remove a Push Listener. |

## API Detail

### Register Push Service

#### API

```
registerPush(options): Promise;
```

#### Parameter Options Description

| Parameter | Type | Description |
| --- | --- | --- |
| SDKAppID | Number | SDKAppID of the Push service. For reference: [Quick Integration > Prerequisites > Enabling a Service](https://www.tencentcloud.com/document/product/1047/75529#ef1e073e-23da-422d-b06b-f13fcda46734) to obtain SDKAppID. |
| appKey | String | Client key of the Push service. For reference: [Quick Integration > Prerequisites > Enabling a Service](https://www.tencentcloud.com/document/product/1047/75529#ef1e073e-23da-422d-b06b-f13fcda46734) to obtain AppKey |
| userID | String | Register the user's userID for push services. User's Unique Identifier, defined by you, can only include uppercase and lowercase letters (a-z, A-Z), digits (0-9), underscore, and hyphen. |

### Disabling Push Service

#### API

```
unRegisterPush(): Promise;
```

### Adding a Push Listener

#### API

```
addPushListener(eventName: string, listener: (data: any) => void);
```

#### Parameter description:

| Parameter | Type | Description |
| --- | --- | --- |
| eventName | String | Push event type.`WebPush.EVENT.MESSAGE_RECEIVED`: new notification arrival`WebPush.EVENT.MESSAGE_REVOKED`: notification recall`WebPush.EVENT.NOTIFICATION_CLICKED`: notification clicked |
| listener | Function | Push event handling method. |

### Removing a Push Listener

#### API

```
removePushListener(eventName: string, listener?: (data: any) => void);
```

#### Parameter description:

| Parameter | Type | Description |
| --- | --- | --- |
| eventName | String | Push event type.`WebPush.EVENT.MESSAGE_RECEIVED`: new notification arrival`WebPush.EVENT.MESSAGE_REVOKED`: notification recall`WebPush.EVENT.NOTIFICATION_CLICKED`: notification clicked |
| listener | Function \| undefined | Push event handling method. |


---
*Source: [https://trtc.io/document/75688](https://trtc.io/document/75688)*
