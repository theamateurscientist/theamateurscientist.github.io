---
layout: post
category: powder_bed_printer
---
I've been planning on building a powder bed printer for a few years and finally started construction at the beginning of this year. This post will be an introduction to what this project is, my current progress, and my plans for it.
![Picture of laser system in action](/pictures/pbp/laser_example.jpg)

# CAUTION
High power lasers like the kind used in this project can blind you instantly. If you are going to attempt to recreate my work, please wear proper laser safety goggles. You have only one pair of eyes (for now)!

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

## [Current Progress](#current-progress)
### Laser System
So far, the laser power control and laser movement system are complete. For the laser diode, I am using a Nichia 7W+ NUBM44 450nm laser diode. To drive the laser diode, I assembled a laser diode driver circuit that features PWM control. Thanks to user OddOne on Candle Power Forums for creating the circuit (orignally for LEDs, but works for lasers)[^2].

![Laser Diode Driver Schematic](/pictures/pbp/MOSFET_Current_Regulator_web.png)
![Laser Diode Driver](/pictures/pbp/laser_diode_driver.jpg)
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/HtgSjghh45Y" title="YouTube video player" frameborder="0" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen>
</iframe>
### Hardware Control
To control all the stepper motors for my printer and control the laser diode driver, I utilized a RAMPS 1.4 which is an Arduino MEGA-based 3D printer hardware controller[^3]. I'm running Repetier firmware on the controller due to support for laser control[^4]. All the motors I am using were extracted from an old Printrbot Plus.

Before I put together the powder system, I used the printer as a laser engraver. I engraved the Windows "Bliss" background as well as my university's logo. I also used the laser to cut foam gaskets for the powder pistons.

![Windows Bliss Engraving](/pictures/pbp/bliss.jpg)
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/_btE86icDkA" title="YouTube video player" frameborder="0" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen>
</iframe>
### Custom Slicer
A 3D printer slicer is a program that takes a 3D model, "slices" it into 2D sections, then creates code for creating the right patterns for the printer to execute. I initially wanted to make the printer work with premade slicers (PrusaSlicer, Slic3r, Cura) but the gcode flavor/format they output was not suitable for my printer.
I will share the code once I finalize it, but I ended up using some external programs along with my own Python code to create a working slicer. Once the program is finalized, I will create a seperate post going into more detail about what it does and how it works.
### Manufacturing Usable Powder
Since I wanted to be able to print whatever material I desired, I experimented with creating my own powders. To get the fineness of powder I need (around 40 micron) I jerry-rigged a ball mill setup using an old vitamin bottle, a lathe, and some steel ball bearings. It works suprisingly well to smash the starting materials.

For my binder, I chose stearic acid since it was the binder used by the research paper I am basing my technique on[^1]. I messed around with aluminum powder and activated charcoal as base materials. The results have not been great.
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/ISAMmcf2i4o" title="YouTube video player" frameborder="0" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen>
</iframe>
## [Future Plans](#future-plans)
I'm away from home doing research for the summer, so I unfortunately have to put aside this project for a while.

The powder system definitely needs some work. I'm considering moving over to a roller system rather than a pusher system. I also want to change out the lead screws used for the powder pistons to something that can handle the force better.

For the slicer, I'm planning to implement different laser scanning patterns. I've seen some research papers discuss using alternating scan directions as well as a checkerboard scan pattern.

As for making the powders themselves, I just need to play around more with ball bearing sizes, mill speeds, and powder compositions. That portion of the project is the part I've spent the least time with. I'm also considering purchasing some black powder coating as it is a fine plastic powder that others have had success using in their laser powder bed printing systems[^5]. This would allow me to tune the printer's parameters with a generous supply of ready to use printing material.

Anyways, thanks for reading all that. I hope you stick around to see this project's progress. Take care.

---
{: data-content="footnotes"}

[^1]: Z. H. Liu et al., “Selective laser sintering of high-density alumina ceramic parts,” Proceedings of the 35th International MATADOR Conference, pp. 351–354, 2007. doi:10.1007/978-1-84628-988-0_79
[^2]: OddOne, "Super-Simple Power MOSFET Linear Current Regulator," https://www.candlepowerforums.com/threads/super-simple-power-mosfet-linear-current-regulator.236260/
[^3]: "RAMPS 1.4," RepRap Wiki, https://reprap.org/wiki/RAMPS_1.4
[^4]: "Laser Mode," Repetier, https://www.repetier.com/laser-mode/
[^5]: Vulcaman, "DIY-SLS-3D-Printer," https://www.instructables.com/DIY-SLS-3D-Printer/
