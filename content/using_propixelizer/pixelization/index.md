+++
title = "Pixelisation Controls"
weight = 2
+++

My goal with ProPixelizer is to provide you with ways to produce really good-looking, crisp pixel art. Pixel art comes in a variety of styles, hammered out through decades of changing hardware limitations and favored aesthetics. In practical terms, a good pixelart package must be flexible enough to render a whole range of different styles, because everyone wants something slightly different.

Starting from v2.0, ProPixelizer provides a number of different methods and options for controlling pixelization, as discussed below.

## Low-resolution Render Target

The most common technique used to pixelize 3D scenes is to render them at a resolution lower than the screen, then increase their scale using nearest/point filtering to retain 'crisp' pixels. There are numerous tutorials and assets that use this technique in Unity. In ProPixelizer v2.0, a low-resolution render target is used for some or all of the pixelation, depending on your settings.

ProPixelizer will automatically create and manage the low-resolution render target for you. The resolution of the low-resolution render target is controlled through the properties of the ProPixelizer Camera monobehavior. It can either be set to a fixed ratio of the screen resolution, a fixed resolution, or defined such that a single pixel has a specified size in world space units. In all cases the low-resolution render target's resolution cannot exceed the screen's resolution for performance reasons.

ProPixelizer will automatically handle sub-pixel camera motion for you: as your camera moves through the world, the low-resolution render target will move smoothly with respect to the screen resolution. 

## Low-resolution filter options

ProPixelizer lets you choose how much of your scene should be pixelated. You may choose to have either the full scene rendered to the low-resolution render target, or just ProPixelizer materials. This allows you to create everything from 100% pixel art scenes to 'hybrid' scenes that combine polygons and pixelart. 

This later 'hybrid' style is reminiscent of games from the 90s like Breath of Fire IV, Final Fantasy, and Populous: The Beginning where characters where often rendered as sprites and the background often rendered as low-poly 3d models.

{% article_image(image="ershin1.png") %}
A scene from the playstation game 'Breath of Fire IV' demonstrating a hybrid style.
{% end %}

{% article_image(image="bats.gif", gif=true) %}
A hybrid setup in ProPixelizer. The characters are drawn pixelated, while a low poly environment is used for the surroundings.
{% end %}

## Pixel Expansion

Despite being a popular method, using a low-resolution render target has a major drawback: In order to prevent pixel creep artefacts from occuring, objects must be snapped to the pixels of the low-resolution target. When the target is more pixelated, the object motion becomes more constrained. This has a negative effect on the 'user feel' in games that require precise feedback, such as action rpgs and arcade games - the motion becomes clunkier because small 'sub-pixel' increments are not possible.

{% article_image(image="full_screen_wo_pixel_expansion.gif", gif=true) %}
Creepless motion using a low-resolution render target. Individual objects must move in increments of the low-resolution render target.
{% end %}

ProPixelizer solves this problem using **Pixel Expansion**. I created this method specifically for ProPixelizer, and describe its implementation [here](https://medium.com/@elliotbentine/pixelizing-3d-objects-b55ec33328f1), under attempt 3. This technique works by drawing objects as a dithered pattern, and then expanding these dots into larger pixels through a post process. The result is that a given level of pixelization can be achieved using a smaller low-resolution target pixel size, and thus smooth movement can be retained. The method also supports per-object pixel sizes.

{% article_image(image="full_screen_w_pixel_expansion.gif", gif=true) %}
Creepless motion using a low-resolution render target and pixel expansion. Apparent sub-pixel motion between objects is possible because the low-resolution render target pixel size can be smaller while maintaining the same apparent level of pixelisation. Per-object pixel sizes are also supported.
{% end %}

You can enable or disable Pixel Expansion using the checkbox in the render feature. 

### Performance

Pixel Expansion requires an additional pass that is similar to an anti-aliasing pass; you can use it freely on PC and console, but be mindful on low-end mobile devices.
Some performance guidelines for different platforms can be found below. Note that you can specify different render pipeline assets for different quality settings, so you can automatically build e.g. mobile or webGL with different ProPixelizer settings than PC or console.

- **Highest performance** (android, iOS, webGL)
    - Full-screen pixelization filter, disable pixel expansion, use virtual camera.
- **Highest fidelity** (PC, consoles)
    - Use pixel expansion