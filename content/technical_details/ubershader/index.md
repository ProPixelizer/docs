+++
title = "The Uber Shader"
+++

The PixelizedWithOutline material adds all passes required to draw and outline the object. It uses a custom editor inspector and categorizes the shader properties as follows:

- Appearance: Properties for albedo maps, normals maps, emission maps, and whether to color grade the object using a palette.
    - The Albedo is the base color of the object, further tinted by the Color. The alpha values of these control dithered transparency.
    - Use Color Grading toggles color grading. The Palette texture property is a texture look-up table (LUT) used for the color grading. A number of LUTs to emulate well-known devices (eg NES, PAL, GameBoy) are shipped with ProPixelizer. 

            You can create your own palettes by using a palette asset (Right Click -> Create -> ProPixelizer -> Palette) which is used to generate the LUTs. The LUT can also include color dither patterns as demonstrated here. For more information, see the Color palettes and dither patterns section of the user guide below.

        Emission and Emission Color can be used to provide unlit colors for your material. Think of laser beams, red eyes on skeletons, etc.

        Diffuse and Emissive Vertex Color Weight control how the model's vertex coloring is included in the calculation. Unity's particle system uses vertex color for 'per particle' coloring. Some Synty models have black vertex colors on some mesh areas.

        Use Dithered Transparency toggles whether partial alpha (in the range 0 to 1) should be ignored or drawn as dithered transparency.

        Alpha Clip Threshold specifies a minimum alpha value required to draw parts of the mesh.

    Lighting: Shadow and lighting ramp.

        Lighting Ramp is a texture ramp used for cell shading, which helps give a pixel-art aesthetic. When rendering the object, the calculated color Value is used as to sample the lighting ramp.

        Ambient Light provides additional light to the object. You can control a blend between block color and scene ambient color/spherical harmonics. This can be helpful to tweak the appearance, in conjunction with the color grading. 

    Pixelize: Properties to pixelate the object.

        Pixel size in the range 1-5. This sets the size of one 'macropixel' in screen pixels.

    Outline: Outline related properties.

        ID: A number. Outlines are drawn when pixels have an ID different to those around them. If two objects should have outlines when they meet, give them different IDs (eg, two enemies). If they should not have outlines (eg, a character and their equipment), give them the same ID. The value should be an integer in the range (0, 255).

        Outline Color: The color to use for the outline. The alpha value controls blending with the scene color. Alpha values of 0 can be used for invisible outlines, 1.0 can be used for block color, and fractions to blend with the appearance material color.

        Edge Highlight: This property is used to lighten or darken edges detected by inspection of scene normals. To use it, make sure that 'Use Normals For Edge Detection' is enabled on the Pixelisation Feature of your Forward Renderer Asset. Color values less than 0.5 will darken edges, color values above 0.5 will lighten edges, and values of 0.5 will make no difference.