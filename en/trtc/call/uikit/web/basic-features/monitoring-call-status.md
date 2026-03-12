# Monitoring Call Status

This article describes how to use call status callbacks with the TUICallKit component.

## Call State Monitoring

If your business requires **monitoring the call status**, such as events during the call process ( [TUICallEvent](https://www.tencentcloud.com/document/product/647/51017) for details), you can refer to the following code:

```
import { TUICallEvent } from '@trtc/call-engine-lite-js';let handleUserEnter = function(event) {    console.log('TUICallEvent.USER_ENTER: ', event);};TUICallKitAPI.getTUICallEngineInstance().on(TUICallEvent.USER_ENTER, handleUserEnter);TUICallKitAPI.getTUICallEngineInstance().off(TUICallEvent.USER_ENTER, handleUserEnter);
```

## Component Callback Event

The TUICallKit component offers call status callbacks, which can be used to implement more interaction logic on the business side. Please refer to the [TUICallKit Attribute Overview](https://www.tencentcloud.com/document/product/647/51015#e57a5c34-b984-4372-af01-abaa5cd44ffe) for more details.

- `beforeCalling`: Executed prior to the commencement of the call.
- `afterCalling`: Executed upon the completion of the call.

React

Vue

```
function App() {  const handleBeforeCalling = () => {    console.log("[TUICallKit Demo] beforeCalling");  };  const handleAfterCalling = () => {    console.log("[TUICallKit Demo] afterCalling");  };  return (    <TUICallKit       beforeCalling={handleBeforeCalling}       afterCalling={handleAfterCalling} />  )}
```

```
<template>  <TUICallKit     :beforeCalling="handleBeforeCalling"     :afterCalling="handleAfterCalling" /></template><script setup>function handleBeforeCalling() {  console.log("[TUICallKit Demo] beforeCalling");}function handleAfterCalling() {  console.log("[TUICallKit Demo] afterCalling");}</script>
```


---
*Source: [https://trtc.io/document/59852](https://trtc.io/document/59852)*
