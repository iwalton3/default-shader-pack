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
 - Generic (FSRCNNX) - Video profile with high quality upscaling and downscaling.
 - Generic High (FSRCNNX x16) - Video profile with very high quality upscaling and downscaling.
     - This may cause dropped frames if your graphics card is not powerful.
 - Anime4K x4 Faithful (For SD) - Upscale standard definition anime videos accurately.
 - Anime4K x4 Perceptual (For SD) - Includes above profile, but also makes lines darker and thinner.
 - Anime4K x4 Perceptual + Deblur (For SD) - Includes above profiles, but also reduces blur.
     - This may cause aliasing. You may want to turn it off depending on the video source.
 - Anime4K x2 Faithful (For HD) - Upscale high definition anime videos accurately.
 - Anime4K x2 Perceptual (For HD) - Includes above profile, but also makes lines darker and thinner.
 - Anime4K x2 Perceptual + Deblur (For HD) - Includes above profiles, but also reduces blur.
     - This may cause aliasing. You may want to turn it off depending on the video source.

## Included Shaders

 - [FSRCNNX](https://github.com/igv/FSRCNN-TensorFlow)
 - [Anime4K](https://github.com/bloc97/Anime4K)
 - [Static Grain](https://github.com/wopian/mpv-config)
 - [KrigBilateral](https://gist.github.com/igv/a015fc885d5c22e6891820ad89555637)
 - [SSimDownscaler](https://gist.github.com/igv/36508af3ffc84410fe39761d6969be10)
 - [NNEDI3](https://github.com/bjin/mpv-prescalers)

The configuration groups for some of these shaders are from the [MPV Configuration Guide](https://iamscum.wordpress.com/guides/videoplayback-guide/mpv-conf/).


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
