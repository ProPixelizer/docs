+++
title = "ProPixelizer Camera MonoBehaviour"
+++

The Pixelization Filter controls what objects should be pixelated.
- Full Scene allows you to pixelate the entire render.
- Only ProPixelizer will only pixelate ProPixelizer materials.
- Layers will pixelate any objects on the given layer mask. When using Layers, ProPixelizer materials must be on the pixelated layers to draw properly.


Fullscreen Options allow you to apply Color Grading or dithering to the entire scene by specifying a color palette (you can use ProPixelizer to create your own). These can also be overriden for individual cameras. Note: It's still my firm belief that dithering looks better when applied at the object level, so that the dither pattern can move with the object. ProPixelizer now supports both of these approaches, so don't take my word for it - decide for yourself what you like best!