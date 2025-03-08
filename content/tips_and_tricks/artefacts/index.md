+++
title = "Common artefacts"
description = "Avoiding artefacts in 3D pixel art"
weight = 50
+++

Pixel art is a popular art style, but also highly perfectionist! Even a few small errors can greatly degrade the appearance of good pixel art. Here, I describe some common artefacts that occur when using 3d objects to create pixel art, and what you can do to fix them.

## Creep

Creep is the most well-known 3D pixel art artefact. Visually, the object appears to change shape and form as it moves relative to the camera. This can occur due to object movement, or for stationary objects because the camera is moving. The underlying cause is because the object is rasterized differently to the screen each time, resulting in an inconsistent set of pixels being drawn, which is most commonly due to sub-pixel motion of the object. The result is a visually distracting artefact, which is particularly noticeable in outlines.

{% article_image(image="creep.gif", gif=true, title="Pixel creep") %}
The object's pixel composition appears to change, creating a visually distracting artefact.
{% end %}

### How to fix it?

ProPixelizer provides functionality for correctly handling sub-pixel relative object motion as described in [this section](@/usage/eliminate_pixel_creep/index.md).

{% article_image(image="no_creep.gif", gif=true, title="No creep") %}
Pixel creep removed through snapping of relative object motion.
{% end %}

## Jaggies

A hallmark of pixel art is clean edges, with straight lines parallel to the horizontal axes creating perfect 'staircases' of 2x1 pixels. An interrupted staircase is usually called a _jaggie_.

{% article_image(image="jaggies.png", title="Jaggies") %}
An otherwise perfect 2x1 edge staircase is interrupted by the presence of a 1x1 pixel.
{% end %}

### How to fix it?

{% article_image(image="staircase.png", title="Fixed") %}
Fixing the camera rotation aligns the edges of the object correctly to allow perfect staircases to be rendered. <i>ProPixelizer's edge detection kernels are optimised to give you correct staircases.</i>
{% end %}

Check that you are using the correct projection for your orthographic camera. The easiest way to debug this is to place a cube in the scene directly in front of your camera. The camera should be first rotated 45 degrees about the vertical, and then tilted 30 degrees below horizontal (for example, use a rotation value in the transform of `(30, 45, 0)`, as in the ProPixelizer example scenes). The edges of your cube will then be pointing in a direction with a ratio of 2 pixels up/down for every one pixel across.

Jaggies can also result when pixelating by rendering to a low-resolution target. If the target is upscaled onto the screen by a non-integer multiple, aliasing of the low-resolution target will occur, causing rows and columns of pixels to be of different sizes and interrupting the staircase. ProPixelizer provides a pixel art antialiasing filter to mitigate this effect. It also provides useful functions to set your low-res target resolution to an integer ratio of the screen resolution.

## Moire pattern

A [Moiré pattern](https://en.wikipedia.org/wiki/Moir%C3%A9_pattern) is an optical illusion that is formed when two repeating patterns of different scale overlap. The mixture of these two patterns produces a third pattern, which is often unintended and can be visually distracting. These patterns are the reasons why pinstripe clothes and other textiles are not worn on television!

The general concept is shown below. In the first row we see a pattern consisting of bars, 6 pixels wide and repeating every 12 pixels. In the second row, we see bars 7 pixels wide and repeating every 14 pixels. The third row shows what happens when these patterns are overlaid; a new periodic pattern can be seen, with the repeating element shown by the red bar. The periodicity is equal to the lowest common multiple of the two original patterns, which in this case is 84 pixels.

{% article_image(image="moire_example.png", title="Moire patterns") %}
The periodic patterns in the top two rows combine to produce a Moiré pattern shown in the third row.
{% end %}

So what is the issue? Well, periodic patterns appear in pixel art more often than you may at first realise! [Ordered dithering](https://en.wikipedia.org/wiki/Dither) - in which two different colors are interleaved to approximate a third - is a popular technique and a hallmark of certain pixel art styles.
A Moiré pattern can occur when dithered objects are drawn one on texture, which is then scaled and displayed on the screen at non-integer zoom. For 3D pixel art, this situation can occur when the pixelated, low resolution target is rescaled and presented on the screen. Movement of the objects or camera can cause these patterns to shimmer in a very distracting manner.

{% article_image(image="moire_cubes.png", title="Moire patterns in a pixel art scene") %}
Rescaling the low-resolution render to match the screen has resulted in a visually distracting Moiré pattern. The red box highlights one element of the repeating pattern.
{% end %}

### How to fix it?

There are two different approaches you can take to fix this:

**Option 1: Make sure your pixels are large** and take up a large number of screen pixels. This doesn't technically fix the pattern, but it makes it less perceptible. However, this fix is not appropriate for all styles. In ProPixelizer you can do this by either increasing the `Pixel Size` on the `ProPixelizer Camera` monobehavior when using `World Space Pixel Size` mode, or by reducing the camera's `orthographic size` to reduce the camera field of view. However, this approach is only appropriate for certain pixel art styles.


{% article_image(image="moire_cubes_large_pixels.png") %}
Moire patterns are less visible when the pixel sizes are large.
{% end %}

**Option 2: Make sure your pixels are an integer number of screen pixels.** This approach completely eradicates the Moiré pattern by allowing the low resolution texture to perfectly scale into the screen texture without any interpolation or aliasing artefacts.




## Shimmer
