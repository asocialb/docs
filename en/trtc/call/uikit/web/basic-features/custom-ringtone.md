# Custom Ringtone

This article introduces how to use the custom ringtone and silent incoming call ringtone feature from the definition.

## Setting incoming call ringtone

- Only local MP3 format file addresses can be used, ensuring that the file is accessible.
- To reset the ringtone, pass in an empty string for filePath.
- Use the ES6 import method to import the ringtone file.

```
import
```

## Silent incoming call ringtone

- Enable/Disable incoming call ringtone.
- After enabling, the incoming call ringtone will not be played when a call request is received.

```
try {  await TUICallKitAPI.enableMuteMode(enable: boolean);} catch (error: any) {  alert(`[TUICallKit] enableMuteMode API failed. Reason: ${error}`);}
```


---
*Source: [https://trtc.io/document/59847](https://trtc.io/document/59847)*
