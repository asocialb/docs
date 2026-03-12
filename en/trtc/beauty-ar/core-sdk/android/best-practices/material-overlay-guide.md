# Material Overlay Guide

Animation Material Overlay refers to the simultaneous activation of multiple animation materials.

## **Points to Note on Material Overlay**

1. Users shall manage the compatibility of their materials for overlaying. Here are two examples:

Example 1: Effect A turns a face into a royal visage, while Effect B turns a face into a fairytale visage. The overlay of these two effects may result in an unnaturally distorted image.

Example 2: Effect A represents rabbit ears, while Effect B represents pig ears. The overlay of these two effects presents two types of ears.

In Example 1 and Example 2, Material Overlay is not suitable. If Effect A is a pair of rabbit ears, and Effect B is blowing a kiss, these two effects won't conflict and are hence suitable for overlay.

2. Only the overlay of simple materials is supported. Simple materials refer to single animation effects, or single makeup effects, or single background, etc. Complex materials refer to those that contain multiple effects. There is no clear distinction between simple and complex materials. It is recommended that users thoroughly test and manage which materials can be overlaid and which cannot.
3. In Material Overlay, effects triggered by actions (such as stretching out a hand or smiling) are classified as complex effects and need to be placed first, with simple effects applied on top of them.
4. Example: The anchor uses Effect A, and then the audience gifts Effect B. Effect B is applied on top of Effect A. After a period of time, Effect B disappears and only Effect A is used. The setting process is as follows:
  4.1. Setting Effect A: Set mergeWithCurrentMotion to false.
  4.2. Setting Effect B: Set mergeWithCurrentMotion to true.
  4.3. After a brief period, proceed with setting Effect A by setting mergeWithCurrentMotion to false.

### **How to Configure for Simultaneous Activation**

v3.5.0 or later versions

v3.0.1 or later versions

1. If you are using the `setEffect` method to update Beauty Properties, to implement the Material Overlay feature, you can add the `mergeWithCurrentMotion` field in `extrainfo` and set it to `"true"`.
2. If you are using the `updateProperty` method, you can refer to the methods listed in [V3.0.1](#724581bc-eeca-4235-82bd-c3a5b8e4ff74).

### **Android**

If you want to overlay a certain animation, make-up, or segmentation material on the current material, then set 'mergeWithCurrentMotion' of the **XmagicProperty** object of the material to true. For other property settings, see [Beauty Parameter Settings](https://www.tencentcloud.com/document/product/1143/52514).

```
XmagicProperty xmagicProperty = new XmagicProperty(XmagicProperty.Category.MOTION,"video_keaituya",mResPath+"xmagic/MotionRes/2dMotionRes/video_keaituya",null,null);
xmagicProperty.mergeWithCurrentMotion = true;
mXMagicApi.updateProperty(xmagicProperty);
```

### **iOS**

If you want to overlay a certain animation, make-up, or segmentation material on the current material, then while setting the material, in the withExtraInfo dictionary, set mergeWithCurrentMotion to true. Here is an example:

```
NSString *key = _xmagicUIProperty.property.Id;NSString *value = [[NSBundle mainBundle] pathForResource:@"makeupMotionRes" ofType:@"bundle"];NSDictionary* extraInfo = @{@"mergeWithCurrentMotion":@(true)}; [self.beautyKitRef configPropertyWithType:@"motion" withName:key withData:[NSString stringWithFormat:@"%@",value] withExtraInfo:extraInfo];
```


---
*Source: [https://trtc.io/document/73783](https://trtc.io/document/73783)*
