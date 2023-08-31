---
layout: default
title: How To Do A CMOS Reset
parent: Network
---
Written by @jheden

The following will explain how to do a CMOS reset on a PC or a Laptop. Note that not all laptops come with a CMOS battery.
* Disconnect the power cable from the PSU/The charger and the battery of your laptop
* Open the casing of your PC/Laptop
* Locate one of these 3 things:
  * CMOS Battery - A 20 mm wide silver coin shaped object, usually located around the 1st PCIe slot, under the GPU
  * CMOS Reset Button - a small button located somewhere on your motherboard, tends to be on one of the edges 
  * CMOS Reset Jumpers - not much to say, two pins next to each other
* Based on whichever of the 3 options you've located, do one of the following things
  * Remove the battery, then hold the power button for 20 seconds
  * Hold the button and the power button for 20 seconds
  * Bridge the two pins with something metal (fork, screwdriver, knife) and hold the power button for 20 seconds
* Put everything back together. Your BIOS should be reset to its default settings, about which it will likely warn you when you turn the PC on

You can see pictures of the battery, jumpers and button in this post too. If you still struggle to find at least one of the listed things, consult your motherboard's manual.
![CMOS Battery](https://cdn.discordapp.com/attachments/1120361954574340096/1120361955278983289/battery_1.png)
![CMOS Button](https://cdn.discordapp.com/attachments/1120361954574340096/1120361955002175538/cmos_button_1.png)
![CMOS Jumper](https://cdn.discordapp.com/attachments/1120361954574340096/1120361954700181565/cmos_pins_1.png)
