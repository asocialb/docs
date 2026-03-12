# FAQs

## An error occurs when running on iOS: Error (Xcode): Library not found for -ld64ï¼

`Xcode` 15 changed the compiled `linker`, and `RoomEngine Flutter` was adapted in 1.6.0. Old versions of Xcode cannot be compiled, so just use the latest `Xcode`.

## The project integrates `tencent_calls_uikit` and `rtc_room_engine` at the same time. There will be problems such as the two components interfering with each other when joining the room will interrupt the call. How to Resolveï¼

This is due to the exclusivity of the `RTC` service. We recommend that you use two flags, `callState` and `roomState`, to record whether you are currently on a call or in a conference. These two flags are used to isolate the two services. , to avoid this problem. For example, if you are currently on a call, entry into the room is prohibited.


---
*Source: [https://trtc.io/document/57598](https://trtc.io/document/57598)*
