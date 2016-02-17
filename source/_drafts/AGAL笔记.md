---
title: AGAL笔记
id: 1727
categories:
  - 3D
  - Flash
  - 三维时代
tags:
---

Each register is 128 bits wide, which means that it contains 4 floating point values. Each of these values is called a component of the register.

Register components can be accessed both through the coordinate accessors (xyzw), and through the color accessors (rgba).

Attribute registers: va&lt;n&gt; only available in Vertex Shaders.
Constant registers: vc&lt;n&gt; 128 available to Vertex Shaders, and 28 for Pixel Shaders.
Temporary registers: vt&lt;n&gt; (Vertex Shaders) and ft&lt;n&gt; (Pixel Shaders) 8 temporary registers available
Output registers: op for Vertex Shaders, and oc for Pixel Shaders. only one output register
Varying Registers: v&lt;n&gt; 8 varying registers available.
Texture sampler registers: fs&lt;n&gt; &lt;flags&gt;

`&lt;flags&gt;` is a comma separated set of strings, that defines:

*   texture dimension. Options: `2d, cube`
*   mip mapping. Options: `nomip` (or `mipnone` , they are the same) `, mipnearest, miplinear`
*   texture filtering. Options: `nearest, linear`
*   texture repeat. Options: `repeat, wrap, clamp`