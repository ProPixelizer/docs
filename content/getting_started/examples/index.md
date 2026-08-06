+++
title = "See the examples"
weight = 3
date = 2024-10-19
+++

<div class="examples-page">
  <p class="examples-intro">Here you can explore the sample scenes included with ProPixelizer. Each one focuses on a practical technique you can inspect, adapt, and use in your own Unity project.</p>

  <aside class="examples-import-callout" aria-label="Import information">
    <p>These samples are <strong>included with ProPixelizer,</strong> you can import every scene from the Package Manager.</p>
    <a href="#import-samples">View import steps ↓</a>
  </aside>

  <div class="examples-grid">

{% example_showcase(name="Full Screen", image="fullscreen.gif", gif=true, featured=true, alt="Pixelated green scene demonstrating full-screen pixelization and color grading", link="usage/pixelization/") %}
Applies pixelization and color grading to the whole camera. URP's postprocessing is used to give a feeling of depth.
{% end %}

{% example_showcase(name="Simple", image="simple.png", alt="Two shaded pixel-art spheres from the Simple example scene", link="getting_started/quickstart/") %}
A quick example to confirm your installation is correct.
{% end %}

{% example_showcase(name="Edges and Outlines", image="edges.png", alt="Pixel-art cubes showing different edge and outline treatments", link="usage/outlines/") %}
Compare silhouette outlines, edge highlights and lit bevel edges.
{% end %}

{% example_showcase(name="No Creep", image="nocreep.gif", gif=true, alt="Animated pixel-art shapes moving without pixel creep", link="usage/eliminate-pixel-creep/") %}
Eliminate pixel creep from moving objects.
{% end %}

{% example_showcase(name="World Space Pixel Size", image="worldspacepixelsize.gif", gif=true, alt="Animated building maintaining a consistent world-space pixel size", link="technical/propixelizer-camera/") %}
Maintain a consistent pixel size across different camera zooms and screen resolutions.
{% end %}

{% example_showcase(name="Color Palettes", image="colorpalettes.png", alt="Pixel-art objects using several palettes and dither patterns", link="usage/palette-tools/") %}
Explore color palettes and dither patterns. ProPixelizer contains tools for creating your own dither patterns and palettes.
{% end %}

{% example_showcase(name="Pixel Alignment", image="pixelalignment.png", alt="Two connected pixel-art cubes demonstrating pixel alignment", link="technical/objectrendersnapable/") %}
Restrict sub-pixel motion between related objects, such as equipment attached to a character.
{% end %}

{% example_showcase(name="Camera Stacking", image="camerastacking.png", alt="Several outlined pixel-art spheres rendered with stacked cameras", link="usage/camera-setup/") %}
Apply ProPixelizer to different cameras within a URP camera stack.
{% end %}

{% example_showcase(name="Multiple Lights", image="multiplelights.gif", gif=true, alt="Animated night scene illuminated by several lights", link="technical/render-feature/") %}
ProPixelizer supports both Forward and Forward+ for virtually unlimited additional lights.
{% end %}

  </div>

  <section class="examples-install-guide" id="import-samples">
    <div>
      <h2>Import the sample scenes</h2>
      <p>In Unity's Package Manager, choose <code>Packages: In Project</code>, select <code>ProPixelizer</code>, open the <code>Samples</code> tab, and select <code>Import</code>. Each scene includes a readme in its hierarchy with setup notes and further suggestions.</p>
    </div>
    <figure>
      <img src="how_to_install.png" alt="Unity Package Manager with the ProPixelizer Samples tab open and the Import button highlighted" width="641" height="264" loading="lazy" decoding="async" />
      <figcaption>The Samples tab in Unity's Package Manager.</figcaption>
    </figure>
  </section>
</div>
