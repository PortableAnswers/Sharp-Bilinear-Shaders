Sharp-Bilinear Shaders for Retroarch
=================================

This is a collection of shaders for sharp pixels without pixel wobble and minimal blurring in RetroArch/Libretro.

There are twp shaders included.

- "2x-prescale-sharp-bilinear" does a fixed 2x integer prescale, resulting in a small amount of blur but no pixelwobble.

This is a simple two-pass shader configuration. First, an integer 2x prescale is applied, followed by a bilinear scaling to fullscreen. 

- "sharp-bilinear-simple" does a automatic integer prescale using the maximum integer depending on game resolution and screen resolution.

This is a bit more involved shader that results in even sharper images than the above.

Both shader configurations give sharp pixels with zero pixel wobble in all games. 

Compared to the "video smoothing=ON" setting with no shaders, pixels are less blurry. Compared to the "video smoothing=OFF" setting with no shaders, the pixels do not change shape/wobble as they move across the screen.

I tried TheMaister's autoscaling shader from the libretro repo, "retro/sharp-bilinear.glslp," but, for some reason, that shader did not work well with vertical games for me.

Installation
---------------
To install this shader in RetroPie:

- Copy the contents of the included "Copy_To_RetroPie" folder to /opt/retropie/emulators/retroarch/shader/
- open the RetroPie-Setup menu and choose "Edit RetroPie/RetroArch Configurations"-> "configure basic libretro emulator options"-> "configure default options for all libretro emulators"
- set "Video Shader Enable" to "True"
- set "Video Shader File" to "sharp-bilinear-simple.glslp," or "2x-prescale-sharp-bilinear.glslp" depending on your preference.

Example Images 
-------------------

shader "sharp-bilinear-simple" on:
![](https://image.ibb.co/hU4k95/with_shader.png)

shader off, smoothing on (too much blur):
![](https://image.ibb.co/jhzDwk/without_shader.png)

shader off, smoothing off:
![](https://image.ibb.co/nHzowk/no_shader_smoothing_off.png)

On first glance, the above looks sharp and good, but looking at a detail, we can see pixel wobble that happens if no shader is used. The pixels along the black diagonal should all be the same, square shape, but some of them appear rectangular:
![](https://image.ibb.co/htaxNQ/no_shader_smoothing_off_detail.png)

Compare the above detail to the result with the shader on:
![](https://image.ibb.co/hrRXp5/with_shader_detail.png)

Now all pixels have the same shape, at the cost of a slight reduction in sharpness. 
