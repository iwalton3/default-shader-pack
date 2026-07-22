# default-shader-pack

MPV Shaders can greatly improve video quality, but they can be difficult to
configure. The goal of default-shader-pack and the shader pack integration in
the MPV Shim clients is to make shaders easier to use for more people. Video
enhancement should not be limited to HTPC enthusiasts who want to dig through
configuration guides and forum posts!

## Shader Profiles

This pack includes shader and configuration presets that work well for enhancing
both anime and live-action video content. You may want to adjust the settings if
the shader presets cause performance issues.

 - Defaults - This pack applies the following effects by default:
     - deband-default - This enabled debanding, which helps with dark scenes and gradients.
     - hwdec-default - Ensures hardware decoding is enabled.
     - static-grain-default - Adds a very small amount of static noise to help with debanding.
     - dither-fruit-default - Dithers colors to match the display color depth.
     - This may cause dropped frames if your graphics card is not powerful.
 - NVIDIA Image Scaling
 - AMD FidelityFX Super Resolution
 - AMD FidelityFX Contrast Adaptive Sharpening
 - Anime4K v4.0.1 - [Please read here](https://github.com/bloc97/Anime4K/blob/v4.0.1/GLSL_Instructions.md) for details.
 - NNEDI3 (64 Neurons) - Default profile for NNEDI3.
 - NNEDI3 High (128 Neurons) - NNEDI3 profile with higher processing requirements.
 - FSRCNNX
 - FSRCNNX x16
 - ArtCNN - Newer luma doubler aimed at anime, and the one to try first if
   FSRCNNX is disappointing. Three profiles: the default (C4F16), a denoising
   and sharpening variant, and a heavier C4F32 in the `hq` group.

## Included Shaders

 - [NVIDIA Image Scaling](https://gist.github.com/agyild/7e8951915b2bf24526a9343d951db214)
 - [AMD FidelityFX Super Resolution](https://gist.github.com/agyild/82219c545228d70c5604f865ce0b0ce5)
 - [AMD FidelityFX Contrast Adaptive Sharpening](https://gist.github.com/agyild/bbb4e58298b2f86aa24da3032a0d2ee6)
 - [Anime4K](https://github.com/bloc97/Anime4K)
 - [Static Grain](https://github.com/wopian/mpv-config)
 - [KrigBilateral](https://gist.github.com/igv/a015fc885d5c22e6891820ad89555637)
 - [SSimDownscaler](https://gist.github.com/igv/36508af3ffc84410fe39761d6969be10)
 - [NNEDI3](https://github.com/bjin/mpv-prescalers)
 - [FSRCNNX](https://github.com/igv/FSRCNN-TensorFlow)
 - [ArtCNN](https://github.com/Artoriuz/ArtCNN)

The configuration groups for some of these shaders are from the [MPV Configuration Guide](https://iamscum.wordpress.com/guides/videoplayback-guide/mpv-conf/).

## Notes on the graphics settings

Two settings this pack used to force are deliberately gone, and one that looks
outdated is deliberately kept:

 - **No `gpu-api`.** The pack used to force `opengl`. That was never about the
   shaders — MPV cross-compiles user GLSL to SPIR-V, and every profile here
   runs unmodified on Vulkan and compiles through the Direct3D 11 chain. It was
   there to make the `fbo-format` value below legal. Forcing OpenGL costs HDR
   output on Windows, where MPV would otherwise pick d3d11 or Vulkan.
 - **No `fbo-format`.** The pack used to ask for `rgba16f`, which is an
   OpenGL-backend format name; the Direct3D 11 backend calls the same format
   `rgba16hf`. On d3d11 the request failed, MPV fell back to *dumb mode*, and
   dumb mode silently disables every user shader. MPV's `auto` already tries
   16-bit float first on whichever backend is live, and has since MPV 0.29
   (2018) — which is the release that made asking by hand unnecessary.
 - **`profile=gpu-hq` stays**, even though MPV's `builtin.conf` now marks it a
   deprecated alias for `high-quality`. `high-quality` only exists in MPV 0.38
   and newer, so naming it would break every older MPV outright. Worth
   switching once the supported floor moves past 0.38.


# Improvements

This shader & settings pack makes a lot of decisions for the user. They tend towards
higher-end computers and may be processor intensive. They are also opinionated.
If you have any suggestions for how to improve this pack or if there are any
outright misconfigurations, please let me know.

Some upscalers, such as Anime4K, have been viewed as controversial. Please do not
use the issue tracker to debate the merits of certain upscalers. It is ultimately
the user's decision what upscalers they use and what they feel improves their viewing
experience.

If you would like to contribute additional profiles, please feel free to do so.
