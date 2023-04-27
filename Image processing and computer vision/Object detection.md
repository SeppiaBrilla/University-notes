The object detection problem can be formulated in different ways:
- Simple object detection
- Instance-level Object Detection
For the first one, we can use the same principle used for [[Stereo vision]]: [[Local invariant feature]] or [[Convolutional neural networks]]. But for the second one, often, only a singular image of the object we want to find is present and, also we may want to find that specific object and not a similar one (so, not a common [[Classification]] problem).

## Instance-level Object Detection

Given a reference image (aka model image) of a specific object, determine whether the object is present or not in the image under analysis (aka target image) and, in case of detection, estimate the pose of the object.

Two main approaches:
- [[Template matching]]
