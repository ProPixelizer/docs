+++
title = "Version History"
weight = 10
+++

## Version 2.0

- **Added** Low-res render target mode.
- **Added** Hybrid low-res render target mode.
- **Added** Full screen pixelisation mode.
- **Added** Full screen color grading option.
- **Added** Full screen dither option.
- **Added** depth testing to normal-derived edges (e.g. to reveal steps)
- **Added** Automatic rescaling to preserve world-space pixel size when zooming.
- **Added** Automatic rescaling to preserve world-space pixel size when changing screen resolution.
- **Added** ProPixelizer SubTarget for ShaderGraph - use it like a lit shadergraph, all pixelisation/dithering/color grading/cel shading/outlines are handled for you. Provides per-pixel control over outlines.
- **Added** Support for Forward+ rendering path.
- **Added** Support for Baked lighting.
- **Added** Support for Mixed lighting.
- **Added** Support for GPU Instancing.
- **Added** Support for Hybrid renderer.
- **Added** HDR Support for emissive lighting.
- **Added** 'Bevel' edge highlight option (where edges use average surrounding normal for lighting).
- **Added** Automatic world-space pixel alignment of static and unmoving objects.
- **Added** Screen resolution movement for low res targets ('camera subpixel motion').
- **Added** Lots of new example content and notes, showing you how to get the most out of ProPixelizer!
- **New Documentation** rewritten from scratch using Zola.
- Reduced the number of material keywords and changed some to shader_feature_local, which should give faster compile times.
- **Fixed** Depth buffer post-processing effects in 2022.
- **Fixed** greatly improved the edge detection kernels to give 1px edges more reliably.
- Renamed ProPixelizer material properties to match Universal Lit convention (run Window > ProPixelizer > Update and Verify Materials)

_Version 1.9 gradually evolved into a large enough update to warrant skipping to 2.0._

## Version 1.8.1

- **Added** ObjectRenderSnapable no longer required for static objects - snapping will occur automatically!
- **Added** Warning when MSAA is enabled (this is a common cause of confusion).
- **Fixed** Line artefact on iOS and some mobile targets (caused by numerical imprecision).
- **Fixed** Support null render pipeline in quality settings/graphics settings.
- **Fixed** WebGL: error on some browsers for 'Active draw buffers with missing fragment shader outputs'.
- **Fixed** WebGL: depth output/transparents not working on some browsers.
- **Fixed** ProPixelizer namespace used for everything.
- **Fixed** _ProPixelizer_Pixel_Scale affects outline buffer (thanks gridmaniac for report!).
- **Fixed** unsubscribe from camera events when camera disabled (thanks GamingLee for report!).
- **Fixed** 'cannot implicitly convert from 'Texture2D<float4>' error.
- **Fixed** Scene tab camera depth in 2021 and 2022 (affects Gizmos and grids).
- **Fixed** Preview cameras for ProPixelizer materials.

## Version 1.8

- **Added** support for Unity 2022.2. This required significant work to get things running in URP14, which contained a number of breaking API changes.
- **Added** support for scene ambient light and SH probes. The AmbientLight property now has an alpha channel - use this to control blending between scene ambient light or the color specified by the AmbientLight property.
- **Added** weights to control how vertex colors should be used (e.g. emissive, diffusive, or not at all). Vertex colors are used to store per-particle color by unity's particle system.
- **Added** an example scene with randomized materials to give an idea of how to achieve different looks.
- **Added** a global shader variable (float) _ProPixelizer_Pixel_Scale, which can be used to change scale of all ProPixelizer materials.
- **Added** a keyword toggle to enable/disable the use of dithered transparency when alpha < 1.
- Reintroduced alpha clip threshold property.
- **Fixed** depthAttachment error on Mac/Metal
- **Fixed** inconsistent dither pattern over large objects.
- **Fixed** line artifacts on extremely high resolution screens.
- **Fixed** artifacts when URP RenderScale is not 1.
- **Fixed** Preview window not working in some versions.
- Known bug (2021.3/2022): Crash or invisibility when SRPBatcher is enabled. The SRPBatcher remains broken with any USEPASS shaders in recent versions of Unity. I have reported this to Unity, and given minimal examples (see here), but all I can do is wait for them to fix. Does not affect builds.
- Known bug (2022.2): Dots in preview window. The preview window is bugged in this Unity version, see here and here for more details.

## Version 1.7

- **Added** `[MainColor]` property attribute for PixelizedWithOutline shader.
- **Added** option to snap object angles in camera space, to help create a 'billboard' effect.
- **Added** alpha support for Edge Highlight Color - set alpha to zero to disable edge highlights.
- **Added** an example showing camera stacking setup, and how to avoid creep on moving cameras.
- **Added** tool to the shader GUI to detect if materials need to be upgraded, and to handle upgrade.
- **Added** _EmissionColor property. _EmissionColor is multiplied by the emission texture to determine unlit appearance. It's great for damage flashes!
- **Added** additional messages to warn users when they haven't set the RenderPipelineAsset in the Graphics or Quality settings.
- **Added** Palette option HSV_Weighted_SquareDistance.
- **Added** Larger selection of preset dither patterns.
- **Fixed** Mac M1 soft crash bug (caused by index out of bounds exception when sampling the 4x4 dithered order array for transparency).
- **Fixed** no longer required to add shaders to the always included list when setting up the project.
- **Fixed** support for vertex colors, so that particles are now colored.
- **Fixed** Incorrect blending with transparent materials on some platforms/engine versions.
- **Fixed** Some bugs in the RenderSnapable system, added new features. 
- **Fixed** annoying console error messages from incorrect PostProcessPass format.
- **Fixed** unpixelized objects appear pixelated when occluding a pixelated object.
- **Fixed** objects dithered using _BaseColor.alpha < 1 will now no longer prevent objects behind them from being seen.
- **Fixed** Null reference exception if user has render pipeline set in GraphicsSettings but not in QualitySettings.
- **Fixed** material properties have been given more sensible names (e.g. _Albedo instead of Texture2D_FBC26130). Examples have been tidied, with example separate appearance and outline materials removed. I've added migration tools to enable material properties to be automatically upgraded through the inspector.
- **Fixed** Saturation/Value weights in Palette.
- **Fixed** Disappearing materials when opening Unity (caused by UsePass in PixelizedWithOutline failing to import forward rendered passes from the shader graph if imported before the shader graph).
- **Fixed** RTHandle support required for 2022b (URP 13.1 and higher).
- **Removed** the Object outline shader, added OutlinePass.hlsl.
- **Removed** Option to choose source buffer used for pixelisation. ProPixelizer now always uses the ProPixelizer buffer.
- **Renamed** Pixelized to ProPixelizerBase and changed the shader GUI to redirect users to use the PixelizedWithOutline material instead.
- **Dropped** support for 2019 LTS, remade all example assets (e.g. Render pipeline, post process data, shadergraph) in 2020 LTS.

## Version 1.6

v1.6 adds significant new functionality to outlining. You are strongly recommended to use the Appearance+Outline material.

- **Added** outlines now respect color palette, per-object control.
- **Added** outline appearance now controlled via shadergraph (add your own dashed patterns, blinking outlines, etc!).
- **Added** interior outlines using normal/depth post processing, per-object control.
- **Added** color property to the ProPixelizer shader.
- **Added** ability to define curve for mapping when using palette style V_Nearest (for monochrome palettes).
- **Added** Support for HDR.
- **Added** Fixed time delay mode to stepped animation tool.
- **Added** Ordered-dither transparency (e.g. for fading objects in/out)
- **Added** Option for camera snap to use orthographic size defined on camera, rather than just pixel size in world space units.
- **Fixed** Post-process does not flatten depth buffer, works with transparent again.
- **Fixed** Specular highlights no longer appear for very bright light sources.
- **Fixed** Shadows work for multiple cascades.
- **Fixed** Stepped animation tool doesn't create a new UUID when regenerating clips.
- **Fixed** SRPBatcher now works properly with ProPixelizer Appearance+Outline material. You should see a performance improvement!
- **Fixed** Additional light shadows (for URP 11+, thanks to Cyanilux's excellent repo.)
- **Fixed** Incorrect color grading on linear color space.
- **Fixed** Color grading bug, color grading is now 1-1 and limited only by 16-color/channel bit depth.
- **Fixed** Pixelization post-process for overlay cameras (requires Pixelisation source to be set to 'ProPixelizer Metadata', URP 10.5+).
- **Fixed** Camera snap supported for multiple cameras.
- **Fixed** Camera snap for moving cameras.
- Tidied up the example ShaderGraph, added more useful subgraphs.

## Version 1.5

- **Added** improved workflow for palettes. Individual palettes are now assets, so the values used for generating LUTs are saved.
- **Added** editor tool for user-defined 4x4 dither patterns.
- **Added** editor tool for creating stepped animations, to help replicate a flipbook/spritesheet feel.
- **Fixed** Bug for game view on Metal.
- **Fixed** Bug when RenderScale != 1.
- **Fixed** Correct pixelation for material preview, material icons and shader graph preview (fix for 2020+ only, URP on 2019 LTS doesn't expose required properties).
- **Fixed** editor warning when selecting in inspector (fix for 2020+ only, URP on 2019 LTS doesn't expose required properties).

## Version 1.4

- **Added** dither pattern support.
- **Added** single material to produce both outlines and appearance.
- **Added** example scene (Floating) to show new shader and a no-creep setup.
- **Fixed** occasional 'tearing' due to numerical precision error.
- **Fixed** creep in rare cases.
- **Improved** Palette Builder tool.
- Made shader keywords consistent - run Window/ProPixelizer/Verify Materials to fix broken materials.

## Version 1.3

- **Added** option for depth-tested outlines, to prevent outlines when objects overlap (see option in render feature).
- **Added** alpha cutout support.
- **Added** custom GUI for Appearance materials (for ShaderGraph versions that support it, 2020+).
- **Fixed** Object flashing bug for Orthographic projections when near plane was negative.
- **Fixed** gaps at screen edge.
- **Fixed** various truncation warnings.
- **Fixed** support for Unity 2020.2 and URP 10.2
- **Performance improvement:** Large performance improvement on all platforms (3 pixelation passes for color/outline/depth now reduced to a single 'Pixelization Map' pass). 

## Version 1.2

- **Fixed** creep/malformation at some resolutions.
- **Fixed** tearing in perspective projection.
- **Fixed** 3x3 pixelation on AMD+openGL targets.
- **Quality of life:** the '_ID' property in the ObjectOutline shader is now specified as integer in the range (0,255). No change is required if using the OutlineControl MonoBehaviour. 