+++
title = "How to: Eliminate Pixel Creep"
description = "How to: Eliminate Pixel Creep"
weight = 1
+++

Pixel creep is a problem that occurs frequently when rendering 3D objects as pixel art - the object appears to shimmer as it moves across the screen. An example can be seen in this video: https://www.youtube.com/watch?v=lO8O5tY-wZI . The creep occurs because both the number of pixels that an object occludes, and the alignment of the object with respect to the pixels, changes as it moves across the screen.

Pixel creep can be removed by aligning objects to the pixels of the screen before rendering them. Pixel creep can only ever be solved for orthographic projections; in a perspective projection, the object size changes as it moves on the screen.

For orthographic projections, ProPixelizer provides functionality to handle this for you, through two MonoBehaviours:

- The `ProPixelizer Camera` MonoBehaviour, which is attached to your camera.

- The `ObjectRenderSnapable` MonoBehaviour, attached to moving objects that you are rendering.

These MonoBehaviours will snap object positions before rendering and restore them afterwards. The implementation respects transform hierarchies.


## Snapping angles

The ObjectRenderSnapable MonoBehaviour can also snap the angles of objects being rendered. Set ShouldSnapAngles to true if object angles should also be snapped, by the desired Angle Resolution. If you have nested transformations (eg for equipment), I recommend you only do this on the root transform.


## Aligning pixel grids

The ObjectRenderSnapable MonoBehaviour also provides a way to align the pixel grids of child objects to their root transform. This is useful for things like equipment - you have different meshes but want the complete object to look like one sprite. Set the property Align Pixel Grid to true to cause the object's pixel grid to be aligned with the Pixel Grid Reference transform, or the root transform of the heirachy if this property is none.

An example is given in the picture on the left, showing how the blue/green shield looks when it is and is not aligned to the pixels of the root transform. Look closely within the circles - on the unaligned you should be able to see the slightly 1 pixel misalignment of the two objects with 3x3 pixelsizes.