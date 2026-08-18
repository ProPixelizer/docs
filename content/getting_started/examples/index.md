+++
title = "See the examples"
weight = 3
date = 2024-10-19
+++

<div class="examples-page">
  <p class="examples-intro">Here you can explore the sample scenes included with ProPixelizer. Each one focuses on a practical technique you can inspect, adapt, and use in your own Unity project.</p>

  <aside class="examples-import-callout" aria-label="Import information">
    <p>These examples are included with ProPixelizer in the <strong>ExampleAssets</strong> folder.
  </aside>

  <div class="examples-grid">

{% example_showcase(name="Full Screen", video="fullscreen", featured=true, alt="Pixelated green scene demonstrating full-screen pixelization and color grading", link="usage/pixelization/") %}
Applies pixelization and color grading to the whole camera. URP's postprocessing is used to give a feeling of depth.
{% end %}

{% example_showcase(name="Simple", image="simple.png", alt="Two shaded pixel-art spheres from the Simple example scene", link="getting_started/quickstart/") %}
A quick example to confirm your installation is correct.
{% end %}

{% example_showcase(name="Edges and Outlines", image="edges.png", alt="Pixel-art cubes showing different edge and outline treatments", link="usage/outlines/") %}
Compare silhouette outlines, edge highlights and lit bevel edges.
{% end %}

{% example_showcase(name="No Creep", video="nocreep", gif=true, alt="Animated pixel-art shapes moving without pixel creep", link="usage/eliminate-pixel-creep/") %}
Eliminate pixel creep from moving objects.
{% end %}

{% example_showcase(name="World Space Pixel Size", video="worldspacepixelsize", gif=true, alt="Animated building maintaining a consistent world-space pixel size", link="technical/propixelizer-camera/") %}
Maintain a consistent pixel size across different camera zooms and screen resolutions.
{% end %}

{% example_showcase(name="Color Palettes", image="colorpalettes.png", alt="Pixel-art objects using several palettes and dither patterns", link="usage/palette-tools/") %}
Explore color palettes and dither patterns. ProPixelizer contains tools for creating your own dither patterns and palettes.
{% end %}

{% example_showcase(name="ShaderGraph", video="shadergraph", alt="Custom shadergraphs in ProPixelizer", link="usage/shadergraph/") %}
Use ProPixelizer to create your own pixelart shaders.
{% end %}

{% example_showcase(name="Pixel Alignment", image="pixelalignment.png", alt="Two connected pixel-art cubes demonstrating pixel alignment", link="technical/objectrendersnapable/") %}
Restrict sub-pixel motion between related objects, such as equipment attached to a character.
{% end %}

{% example_showcase(name="Camera Stacking", image="camerastacking.png", alt="Several outlined pixel-art spheres rendered with stacked cameras", link="usage/camera-setup/") %}
Apply ProPixelizer to different cameras within a URP camera stack.
{% end %}

{% example_showcase(name="Multiple Lights", video="lights", gif=true, alt="Animated night scene illuminated by several lights", link="technical/render-feature/") %}
ProPixelizer supports both Forward and Forward+ for virtually unlimited additional lights.
{% end %}

{% example_showcase(name="DBuffer Decals", image="decals.png", alt="Example decal use with ProPixelizer", link="technical/render-feature/") %}
Use ProPixelizer with DBuffer decals.
{% end %}

  </div>
</div>
