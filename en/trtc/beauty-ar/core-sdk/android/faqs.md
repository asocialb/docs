# FAQs

### When I built my Android application for release, an error occurred saying that some methods were not found. What should I do?

- To fix the issue, add the following `keep` rules to prevent the code from being removed:

```
-keep class com.tencent.xmagic.** { *;}-keep class org.light.** { *;}-keep class org.libpag.** { *;}-keep class org.extra.** { *;}-keep class com.gyailib.**{ *;}-keep class com.tencent.cloud.iai.lib.** { *;}-keep class com.tencent.beacon.** { *;}-keep class com.tencent.qimei.** { *;}-keep class androidx.exifinterface.** { *;}
```

### What should I do if a GSON library conflict error occurs when I integrate the SDK into my host Android project?

```
Android{  configurations {    all*.exclude group: 'com.google.code.gson'  }}
```

### What should I do if the SO libraries fail to be loaded when `Android targetSdkVersion` is 31 or larger?

```
  <uses-native-library            android:name="libOpenCL.so"            android:required="true" />        //`true` indicates that the library is a must for the application to run. The application cannot be installed on a system without the library.        //`false` indicates that the application can use the library if it is available, but can also run without it. It can be installed on a system without the library. If you set the parameter to `false`, you need to deal with the issues that may arise due to the absence of the library.        //Android website introduction: %!s(<nil>)
```

For more information, see [<uses-native-library>](https://developer.android.google.cn/guide/topics/manifest/uses-native-library-element?hl=zh-cn).

### If the texture passed when using beauty filters is a horizontal texture, how to solve it?

You can use the 'convert' method in the TextureConverter.java utility class in the demo to rotate the texture and convert it to portrait mode, and then pass it to the beauty SDK.

```
    /**     * This method is used to rotate and mirror the RGBA texture. The process is to first rotate the texture Proceed in a clockwise direction. by 'rotation' degrees (which can take values of 0, 90, 180, 270), and then perform a horizontal flip (flipHorizontal) and a vertical flip (flipVertical)     * Use case: Some streaming SDKs return horizontal textures or the characters in the image are facing the wrong direction, while the SDK requires that the characters in the texture are facing forward. Therefore, this method can be used to convert the texture.     *      * @param srcID: The RGBA texture.     * @param width: The width of the texture.     * @param height: The height of the texture.     * @param rotation: The angle of rotation.     * @Returns: The rotated texture. Note: If rotated 90 or 270 degrees, the width needs to be swapped.     */    public int convert(int srcID, int width, int height, @RotationDegreesValue int rotation, boolean flipVertical, boolean flipHorizontal)
```

### If the texture passed when using beauty filters is an OES texture, how to solve it?

You can use the 'oes2Rgba' method in the TextureConverter.java utility class in the demo to convert the texture to an RGBA texture, and then pass it to the beauty SDK.

```
   /**     * This method is used to convert an OES texture to an RGBA texture     *     * @param srcID: The OES texture.     * @param width: The width of the texture.     * @param height: The height of the texture.     * @Returns: The ID of the RGBA texture.     */    public int oes2Rgba(int srcID, int width, int height)
```

### What if I want to use another version of PAG? Supported by V3.5.0

**When the client integrates the beauty filter SDK:**

If integrated through Maven, sdk can be introduced via implement. If you does not wish to use this version of pag, it can be excluded through:

```
implementation ('com.tencent.mediacloud:TencentEffect_S1-04:version'){               exclude group: "com.tencent.tav", module: "libpag"}
```

If manually integrated with the beautification SDK through download, the dependency on aar is without pag. you would still need to add a line in their app's build.gradle to implement pag for usage.

```
implementation 'com.tencent.tav:libpag:4.3.33-noffavc'
```

To dynamically download the .so libraries, you need to obtain them from the official download page and only integrate the `.aar`.

  1.1. 

### What are the relationships between different effect properties?

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2217f0785bb11eda61e525400463ef7.png)


---
*Source: [https://trtc.io/document/60312](https://trtc.io/document/60312)*
