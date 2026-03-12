# FAQs

### Runtime error: "does not provide an export named 'createBlock' "?

If you encounter the following error after following the steps above, please make sure to lock the version of vite to below 3.0.0, and the version of vue to below 3.4.9.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f0a852d21bf911ef8a48525400762795.png)

The reason is that the electron project template provided supports vite versions specified below 3.0.0, but properties in vue version 3.4.9 and above require an upgrade of the vite version for support. An issue has been submitted to the official vue,[https://github.com/vuejs/core/issues/10177](https://github.com/vuejs/core/issues/10177).

### Is trtc-electron-sdk compatible with the official Electron v12.0.1 version?

Yes, trtc-electron-sdk does not depend on the electron's own SDK specifically, so there are no related version dependencies.


---
*Source: [https://trtc.io/document/57419](https://trtc.io/document/57419)*
