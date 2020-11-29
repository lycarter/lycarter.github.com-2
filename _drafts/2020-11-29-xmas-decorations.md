---
layout: post
title: "Sierpinski Christmas Tree"
author: "Landon"
tags:
- art
- engineering
gallery: true
---

Due to COVID, I'll be spending the holidays in my NYC apartment for the first time instead of traveling home. While unfortunate, that means I get to come up with some creative ideas for Christmas decorations. Resources for making things in a 400 sf studio apartment are essentially limited to [3D printing]({% post_url 2020-10-08-3d-printing %}) and soldering - luckily, [PCBs from China](https://jlcpcb.com/) are absurdly cheap and ship quickly, so I decided to make an apartment-sized tech-y Christmas tree. One of the critical requirements is that whatever I made needed to be compact enough to reasonably store and travel with later, so making something modular seemed like a good approach. The idea struck me to design a PCB that would represent a single unit of a [Sierpinski Triangle](https://en.wikipedia.org/wiki/Sierpi%C5%84ski_triangle) so that I could tesselate together many identical boards to make a tree of any size.

<div class="gallery">
<figure name="1" alt="Design in EasyEDA" caption="Design previewed in EasyEDA"></figure>
<figure name="2" alt="Single module (front)" caption="Single module, assembled (front)"></figure>
<figure name="3" alt="Single module (back)" caption="Single module, assembled (back)"></figure>
<figure name="4" alt="Solder Bridge" caption="Closeup of the solder bridge used to select in/out for each of the 3 corners"></figure>
<figure name="5" alt="9-module assembly" caption="9-module assembly"></figure>
</div>

I started by drawing a snow-covered Christmas Tree in [Inkscape](https://inkscape.org/), then imported that SVG into [EasyEDA](https://easyeda.com/). I've used both [Eagle](https://www.autodesk.com/products/eagle/overview) and [KiCad](https://kicad.org/) in the past, but EasyEDA's approach to user-driven libraries, and integration with [LCSC](https://lcsc.com/) has made it my go-to for simple projects like this. I elected to use 3 [WS2812b-mini](https://lcsc.com/product-detail/Light-Emitting-Diodes-LED_Worldsemi-WS2812B-Mini_C527089.html) addressable RGB LEDs per board, and connect each board at the corners with 3-position pin headers. When diagramming out the path the signal would take, I determined that each of the 3 corners of my tree would need to act as either an input or output depending on the position in the overall arrangement, given that I was planning to power the tree from a bottom corner and didn't want any "horizontal" connections, only "vertical" connections (ie, the signal had to go up and down the tree rather than across). To accomplish this, I put a small solder bridge connection on each corner which could select between input and output. I've gotten into the habit of putting solder bridges into my PCBs for customizations like this, or to change functionality by bypassing certain components. It's given me a higher success rate on rev 1.0 boards rather than requiring multiple iterations. I planned to drive the whole assembly from an external Arduino, which I knew could drive WS2812 chains of a pretty reasonable length without any issue. For the first pass, I ordered 10 boards with the goal of making a 9-member Sierpinski triangle. The next logical step up is 27 members, which was a bit more than I planned to commit to, and might be a bit too large for my apartment. As a final touch, I added a small hole to the top so that the board could be hung like an ornament, in the event that I send these boards to friends and family.

Overall, it worked great! I had trouble soldering the WS2812b-minis by hand because the leads go under the component, and so I wound up with a few bad modules on my first attempt. After resoldering the LEDs on the bad modules, it worked flawlessly! I plan on pinning this to a sheet of foamcore and mounting it to the wall. Once the holidays are over, I can unmount it from the foamcore, toss the old sheet, and just store a small pile of PCBs. I was planning on writing some firmware myself, but found that the [FastLED TwinkleFOX example](https://github.com/FastLED/FastLED/blob/master/examples/TwinkleFox/TwinkleFox.ino) worked perfectly out of the box!

All design files are available on [Github](https://github.com/lycarter/sierpinski-tree). If you decide to make any yourself, drop me a note! Thanks for reading :)

todo:
- github
    - email contest