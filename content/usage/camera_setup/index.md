+++
title = "Scene setup"
weight = 2
+++

ProPixelizer will work as soon as you have [added the Render Feature](/getting_started/quickstart/#3-configure-your-render-pipeline-asset-s) to your Render Pipeline Asset. If you want to improve your scenes further:

- Add the [ProPixelizer Camera](/technical/propixelizer-camera) monobehaviour to your camera game objects. This is required for snapping to remove pixel creep, and gives extra options for changing the pixelization method, scene-wide color grading, pixel size constraints, etc.
- Add the [ObjectRenderSnapable](/technical/objectrendersnapable/) to any moving objects using the ProPixelizer shaders. This will register them for snapping/unsnapping during rendering to remove pixel creep.

...and that's it! Dive into the [examples](/getting_started/examples/) for specific implementation details and ideas.