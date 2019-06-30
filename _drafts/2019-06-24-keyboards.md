---
layout: post
title: "Custom Mechanical Keyboard, pt 1"
author: "Landon"
tags:
- engineering
---

At work, I've just been using my Macbook's built-in keyboard, while at home I have a [Ducky Shine Zero]() with [Cherry MX Blue]() switches. The mechanical keyboard is way more pleasant to use, but it has a Windows key layout, which is confusing to use with a Mac, since they have the ridiculous Command key instead of following the same keyboard shortcuts as Windows and most Linux distros. So, I decided I wanted a mechanical keyboard at work. There are a few [available]() mechanical keyboards with Mac key layouts, but most of them actually just have some substitute modifier keys and a little dip switch to remap the layout slightly. While certainly an option, my lead had also recently gotten a [Kinesis split keyboard](), which looked pretty interesting. Looking further into [non-mainstream keyboards](), I decided to just build my own from scratch.

Keyboards are very simple devices - you need a PCB of the right shape, switches, keycaps, diodes, some sort of microcontroller, and probably a case. I found a design that I liked open-source on Github, called the [Redox keyboard](https://github.com/mattdibi/redox-keyboard/) - it's mostly based on the [Ergodox]() keyboard, which is also open-source but has a more dedicated following and official manufacturers. Unfortunately, the Redox keyboard called for a very strange set of keycaps, including 10 1.25u keys. Those are fairly unusual to find, especially in a sculpted profile. Generally a keyboard will have at most 7 1.25u keys for the various modifiers. Therefore, I modified the design to use more 1.5u keys so that a keycap set supporting the Ergodox would almost perfectly cover my modified Redox layout, with just a few spare caps. I also chose to use the [wireless version](https://github.com/mattdibi/redox-keyboard/tree/master/redox-w), which uses BLE to communicate - I don't particularly like wireless accessories usually, but with a split keyboard, there's usually an extra wire that runs between the two that would lead to a more cluttered setup.

Image: original redox
Image: modified redox

After modifying the PCB layout, I ordered a set from [JLC PCB](), which had the best deal on 2-layer boards of this size. I ordered a set of [Cherry MX Brown]() switches, as well as a set of [Cherry MX Blue ]() switches, with the intention of using mostly browns, with some of the modifiers replaced by blues for a clackier feel. It'll be interesting to compare them directly. I also ordered a handful of other switches for comparison, which I might use for the modifiers anyway. I ordered the rest of the necessary electronic components from a mix of Digikey and Amazon. The main Redox Wireless Github page has a better list - aside from the slight layout modification, my keyboard will be unmodified. To round out the required parts, I also picked up a set of [SA Vilebloom]() keycaps, which look awesome and very helpfully come in an Ergodox layout (which is cheaper than the base kit!).

That's where things stand for now - some of the parts are still shipping in the mail, and a case and stabilizer plate need to be designed. I convinced Rebecca to also build a keyboard using some of my spare boards and components, so she's been helping with the case design. We'll probably 3D print the case, and design another pcb with cutouts for the switches to act as the stabilizer plate, though there was also discussion of sending out for waterjetting/lasercutting from a sheet of aluminum.

Part 2 will be coming soon™, which should cover the case design, plate design, assembly, and final thoughts.

Thanks for reading :)