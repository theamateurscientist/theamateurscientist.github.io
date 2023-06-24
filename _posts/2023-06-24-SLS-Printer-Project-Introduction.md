---
layout: post
category: powder_bed_printer
---

I've been planning on building a powder bed printer for a few years and finally started construction at the beginning of this year. This post will be an introduction to what this project is, my current progress, and my plans for it.
![Picture of laser system in action](/pictures/pbp/laser_example.jpg)

## Table of contents
- [Project Overview](#project-overview)
- [Current Progress](#current-progress)
- [Future Plans](#future-plans)

## [Project Overview](#project-overview)
### Simple Diagram of Powder Bed Printer (PBP) System
![Diagram of PBP](/pictures/pbp/printer_system_diagram.jpg)
A powder bed printer builds 3D objects by creating many 2D cross-sections, just like a typical plastic filament 3D printer. Here is an overview of the printing process:

1. The powder feed system pushes up unfused powder
2. The roller or powder spreader spreads fresh powder onto the build plate/area
3. A 2D pattern is fused by the laser
4. The build plate lowers to allow room for more fresh powder
5. Steps 1 through 4 repeats until a finished 3D object is created

I want to create a powder bed printer because of the possibilities for printing more strong or more desirable materials than plastic. A powder bed printer can potentially print ceramics and metals. However, due to the relatively low power of my laser compared to commercial units, I cannot melt metals or sinter ceramics directly. But, there is a way.

Instead of melting the build material directly, you first mix a low-melting temerature binder with the material you desire to build. Then, you fuse the material-binder combo together in the desired shape as you would normally with a powder bed printer. The resulting object that comes out is called a green body. To create the finished part, the binder must be burnt out and the desired final material will remain. This technique has been successfully used to create aluminum oxide parts using a laser in the same power range as mine[^1].

While this technique does allow for usage of a lower power, and therefore more affordable, laser, it does have some drawbacks. First, melting out the binder material results in the model shrinking. Second, this method requires extra equipment (a furnace/kiln) to burn out the powder and fuse the final material. Although, I have been wanting to make a lab furnace anyway. So, for me, needing to build a furnace is not too bothersome.

---
{: data-content="footnotes"}

[^1]: Z. H. Liu et al., “Selective laser sintering of high-density alumina ceramic parts,” Proceedings of the 35th International MATADOR Conference, pp. 351–354, 2007. doi:10.1007/978-1-84628-988-0_79
