+++
title = "Edges and Outlines"
weight = 4
+++

Good edges and outlines are a key ingredient of pixel art; they help accentuate small details and can be used to bring depth to areas of otherwise featureless 'flat' shading.ProPixelizer supports three different types of lines as described here.

{% article_image(image="outlines_and_edges.png", title="Outline and edge types") %}
The three line types are (<i>left</i>) outlines, (<i>middle</i>) edge highlights, and (<i>right</i>) bevels.
{% end %}

## Silhouette Outlines

In ProPixelizer, outlines are drawn around the silhouette of objects where the material has the same `ID` and (for [pixel expansion](@/usage/pixelization/index.md)) where the pixels are [aligned](@/usage/eliminate_pixel_creep/index.md). If you have an object with multiple mesh components - for example a character with equipment - then you may wish to assign the same `ID` to each material and align the meshes to ensure a silhouette is drawn around the entire character.

When two objects overlap, ProPixelizer performs additional depth testing of the ID-based outlines to make sure that outlines are only drawn for foreground objects; this prevents incorrect outlines from appearing on visible edge of the background object.

{% article_image(image="overlap.png", title="Depth tested outlines") %}
ProPixelizer performs depth-testing of silhouette outlines to ensure correct outlines when objects overlap.
{% end %}

The [Uber Shader](@/technical/ubershader/index.md) contains an `OutlineColor` property for silhouette outline control, where the alpha value controls the silhouette outline strength (and can be set to 0 to disable the outline entirely). The [ProPixelizer SubTarget](@/usage/shadergraph/index.md) for shader graph provides the `ProPixelizer Outline` color input node, which grants per-pixel outline control and can be used to create custom outline styles and animated outline effects. 

## Edges

ProPixelizer provides two methods for drawing edge lines on your models.
These methods work by analysing the normals rendered to the screen to identify ridges and folds in the mesh.
The `Normal Edge Detection Threshold` on the [ProPixelizer Render Feature](@/technical/render_feature/index.md) adjusts how sensitive the edge detection algorithm is, and the value can be tuned to detect more or less edges across the scene.

Additionally, ProPixelizer can perform edge detection by testing the scene depth in addition to screen normals, as shown in the image, when `Use Depth Testing For Edge Outlines` is enabled on the Render Feature.

{% article_image(image="depth_edges.png", title="Depth tested edges") %}
Edges are detected through analysis of both scene normals and depth. For example, the edges within the circle on the top surface all have the same surface normals (directly up), but edges are detected due to changes in the scene depth.
{% end %}

{% article_image(image="bevel_v_edge.png") %}
A comparison of bevel and edge highlights.
{% end %}

### Bevel Edges

_Bevel edges_ create 1 pixel wide edges where the normals are the average of the faces surrounding the edge. The result is a line which is light reactive, responding to illumination as if the edge were bevelled. For edges on the rear side of an object, ProPixelizer will also fold the edge normals away from the camera, allowing the rear edges to interact with light sources behind the object to create a rim light effect.

In the [Uber Shader](@/technical/ubershader/index.md) the normal blending for edge bevelling is controlled by the `Edge Bevel Weight` property, while in the [ProPixelizer SubTarget](@/usage/shadergraph/index.md) for ShaderGraph the corresponding input node is `ProPixelizer Bevel Weight`.

### Edge Highlights

The edge highlight adds or subtracts a constant color to an object's detected edges to brighten or darken them.
In the [Uber Shader](@/technical/ubershader/index.md) the color is controlled by the `Edge Highlight Color` property, and in the [ProPixelizer SubTarget](@/usage/shadergraph/index.md) for ShaderGraph the corresponding input node is `ProPixelizer Edge Highlight`.
Color values less than 0.5 will darken edges, color values above 0.5 will lighten edges, and values of 0.5 will make no difference.
The alpha value can be used to control the edge highlight strength.