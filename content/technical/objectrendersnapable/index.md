+++
title = "Object Render Snapable"
weight = 21
+++

The `Object Render Snapable` MonoBehavior allows the position of objects to be snapped before rendering the frame. Coupled with a [ProPixelizer Camera](@/technical/propixelizer_camera/index.md) this can be used to [eliminate pixel creep](@/usage/eliminate_pixel_creep/index.md). Snapping of object view angles is also supported, allowing you to easily create the look of hand drawn pixel art which typically restricts the number of view directions. The original positions and angles are restored after camera rendering is complete.

![Object Render Snapable preview](ors.png)

### Snapping

- `Snap Position`: enables or disables snapping of the object's position.
- `Snap Euler Angles`: enables or disables snapping of the object's rotation. A number of different strategies are available:
    - `World Space Rotation`: the euler angles describing the rotation of the object in world space are snapped to the desired `Angle Resolution`.
    - `Camera Space Y`: the euler angles describing the rotation of the object are snapped in world space for x and z, and camera space for the Y-axis. For a camera that rotates freely around the y-axis, this will allow objects to appear with a restricted number of view directions, as shown in the gif below.

<img src="anglesnap.gif">

### Pixel Alignment

