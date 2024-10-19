+++
title = "Updating from previous versions"
weight = 3
date= 2024-10-19
+++

# Version update notes

## Updating to v2.0

- Version 2.0 adds a lot of new features, and much of the package has been rewritten. Despite this, you shouldn't need to make any changes to your project!
- PixelizedWithOutline is functional, but deprecated. I now recommend using the UberShader; it does all the same things but also supports more functionality like the DOTS renderer and GPU instancing.

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






