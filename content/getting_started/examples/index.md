+++
title = "Examples"
weight = 3
date= 2024-10-19
+++

ProPixelizer comes with a number of example scenes to showcase features and show you how to use the package, which can be found in the `ProPixelizer/ExampleAssets` folder.
Each example scene also contains a 'readme' in the scene heirachy, which you can inspect to find out more information or further suggestions.

{% example_showcase(name = "Simple", image="simple.png") %}
A simple scene showing a few different ProPixelizer materials. If you see this scene correctly, you've successfully installed ProPixelizer! 
{% end %}

{% example_showcase(name = "Edges and Outlines", image="edges.png") %} 
Shows off the different edge and outline options in ProPixelizer.
{% end %}

{% example_showcase(name = "World Space Pixel Size", image="worldspacepixelsize.gif", gif=true) %} 
A scene that configures a camera to use pixel sizes defined in world-space units. ProPixelizer automatically handles render target scaling and sub-pixel camera movement for you to smoothly maintan the desired pixel size across different camera ortho-sizes and screen resolutions.
{% end %}

{% example_showcase(name = "No Creep", image="nocreep.gif", gif=true) %} 
An example demonstrating how to use ProPixelizer to eliminate creep from moving objects.
{% end %}

{% example_showcase(name = "Color Palettes", image="colorpalettes.png") %} 
A scene that randomly changes material settings to show off a wide range of color palette and dither pattern styles. ProPixelizer contains tools for creating your own dither patterns and palettes.
{% end %}

{% example_showcase(name = "Pixel Alignment", image="pixelalignment.png") %} 
Shows you how to restrict sub-pixel relative motion between different objects - useful for aligning inventory items with characters, for example.
{% end %}

{% example_showcase(name = "Camera Stacking", image="camerastacking.png") %} 
An example scene where ProPixelizer is applied to different cameras in a URP camera stack.
{% end %}

{% example_showcase(name = "Multiple Lights", image="multiplelights.gif", gif=true) %} 
Demonstrates the use of additional lights in a scene.
_Note: you may need to enable additional lights and shadows in your Render Pipeline Asset._
{% end %}
