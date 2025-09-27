# Retro CRT Shader (for Universal RP)
A shader graph which replicates some retro tv/monitor effects.
```diff
+ Updated for Unity 2022+
(now uses Fullscreen Graph & FullscreenPassRendererFeature rather than a custom one)
- For older version see branches
```

![Retro](retro.gif)

Effects include :
- CRT (cathode-ray tube) monitor warping
- Scanlines
- Image Distortion
- Static
- Scrolling glitchy static
- Vertical RGB subpixel / phosphor stripes

Repo also includes a multi-camera example setup to render the scene to a low-resolution render texture, to achieve a pixelated look. The main camera's culling mask is set to nothing, so the scene isn't rendered twice, and it uses a different Universal Renderer asset which uses the Retro CRT Shader/material in an **Fullscreen Pass Render Feature** to apply the shader to the screen, before additional post processing (**Vignette, Film Grain, Chromatic Aberration**)

Usage Notes :
- If want to apply to a regular Mesh Renderer (e.g. for a TV monitor), would need to swap the Graph type to Lit or Unlit.
- If you want to apply to screen without the second camera setup / pixelated look, swap the texture sample out in the graph for a `URP Sample Buffer` node set to "Blit Source". Use the material with **Fullscreen Pass Renderer Feature** on the Universal Renderer asset used by your camera.
- Most effects as listed above can be toggled on/off in the material inspector as the graph uses `shader_feature` keywords to create multiple shader variants. Only used variants will be included in build. Note that if you want to be able to toggle effects at runtime (using material.EnableKeyword), you would need to switch the keywords to `multi_compile` instead to force both on/off variants to be included.

Graph Screenshot :

![RetroGraph](retro_graph.png)

Blog Post (on my old site) : https://cyangamedev.wordpress.com/2020/09/10/retro-crt-shader-breakdown/
