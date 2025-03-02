+++
title = "Updating from previous versions"
weight = 3
date= 2024-10-19
+++

## Updating to v2.0

- Please delete the old install from your projects `Assets` folder before importing the new version. A modal window will warn you that import failed if you do not. ProPixelizer has now moved to the Packages folder.
- Version 2.0 adds a lot of new features, and much of the package has been rewritten. Despite this, you shouldn't need to make any changes to your project! I have maintained asset GUIDs, so Unity will automatically incorporate the new versions of any files into your project, even if they have been renamed.
- If you were using the ProPixelizer Render Pipeline Asset, you will find it is now included in the package samples, and so you'll need to import the samples into your project to continue using it.
- There are _many_ new features. The sample scenes give different examples of these; they all contain `readme`s in the scene heirachy with detailed further information. I strongly recommend that you import these scenes and look through them to understand what ProPixelizer can now do.
- PixelizedWithOutline is now deprecated and you should use the **UberShader** as a replacement; it does all the same things, but supports additional functionality like the DOTS renderer and GPU instancing. If you want to update your materials, you can do this easily using a button on the material inspector.
- Given the changes to the rendering API in Unity 6 (RenderGraph), I had to drop support for some of the legacy editors to focus efforts on newer features. This version drops support for 2020 and 2021, but maintains support for 2022 LTS. _All previous versions of ProPixelizer are available on the ProPixelizer git repository, contact me if you would like access and I will gladly assist._

## Updating to v1.8

- Dithered transparency is now disabled by default, but can be enabled through a material keyword via the inspector.

## Updating to v1.7

- You must now use the single Appearance+Outline material (PixelizedWithOutline) - Appearance will no longer work.
- Source Buffer option has been removed - pixelization is now determined only using the ProPixelizer Metadata buffer for better support across the different platforms. The appearance material does not have the passes required to render to the ProPixelizer Metadata buffer (these are added by the PixelizedWithOutline shader).
- Some material properties have been named from randomized ShaderGraph strings into more meaningful names.
- An automatic material updater has been added to fix both of the above issues. If your materials need to be updated, an update button will appear in inspector which will migrate your materials and properties to the PixelizedWithOutline shader.
- You no longer need to add things to 'Always Included Shaders'.
- 2019 is no longer supported, but both 2020 and 2021 now have LTS versions you can use instead. There is early support for 2022, but please bear in mind the URP API for this version is currently still changing frequently.
- Many of the updates can be automatically applied to your materials using the tool at Window/ProPixelizer/Update and Verify Materials. Please back up your project before using it, it will search through all materials looking for ProPixelizer materials to update.

## Updating to v1.6

- There are now some features of ProPixelizer which require the Outline pass to run. Use the Appearance+Outline material (which includes this pass), not the Appearance material. If you want to remove the outline, just set the outline alpha to zero.
- There is now another material to add to the Always Include Shaders under Project Settings > Graphics: Hidden/ProPixelizer/SRP/OutlineDetection. You can see the full list in the 'setting up the project' part of this guide.

## Updating to v1.4

- I changed the name of some shader keywords to be consistent between outline and appearance materials. After you update, run the tool Window/ProPixelizer/Verify Materials to fix any broken materials in your project (this will update all materials to use the new keywords).






