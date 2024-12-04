+++
title = "Pixelisation Methods"
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


{% article_image(image="bats.gif") %}
A hybrid setup in ProPixelizer. The characters are drawn pixelated, while a low poly environment is used for the surroundings.
{% end %}

## Pixel Expansion

Despite being a popular method, using a low-resolution render target has a significant drawback. In order to prevent pixel creep artefacts from occuring, objects must be snapped to the pixels of the low-resolution target. As the target becomes more pixelated, the freedom to move objects becomes more and more constrained. This has a negative effect on the 'controller feel' for games that require precise feedback; motion becomes clunkier because small 'sub-pixel' increments are not possible.

To solve this problem, ProPixelizer provides a pixel expansion method. I created this method specifically for ProPixelizer, and describe its implementation here, under attempt 3. This technique works by drawing objects as a dithered pattern, and then expanding these dots into larger pixels through a post process. The result is that a given level of pixelization can be achieved using a smaller low-resolution target pixel size, and thus smooth movement can be retained. The method also supports per-object pixel sizes.

This image is taken from the Floating example scene, with world-space pixel size turned up, a material pixel size of 5, and pixel expansion enabled. The white lines show a grid aligned to the pixels of the sphere on the left. The cubes on the right are free to move at apparent 'sub-pixel' resolution, without exhibiting pixel creep.

If you want to use Pixel Expansion, simply tick the checkbox in the render feature to enable it.
Performance

Some performance guidelines for different platforms can be found below. Note that you can specify different render pipeline assets for different quality settings, so you can automatically build e.g. mobile or webGL with different ProPixelizer settings than PC or console.

    Highest performance (android, iOS, webGL)

        Full-screen pixelization filter, disable pixel expansion.

    Highest fidelity (PC, consoles)

        pixel expansion