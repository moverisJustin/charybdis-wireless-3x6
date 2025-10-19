# Charybdis Wireless (3x6 aka Mini) Guide
![wireless charybdis](./images/DSC08373.jpg "My build")

# Justin's Project Notes

I am relying on multiple existing guides to help with this work. They include:
1. This repo fork which originated here from @erenatas: https://github.com/erenatas/charybdis-wireless-3x6
2. This helpful guide from @280Zo: https://github.com/280Zo/charybdis-wireless-mini-3x6-build-guide/tree/main?tab=readme-ov-file
3. The official BastardKB guide which relies on several of these: https://docs.bastardkb.com/help/bluetooth.html#3d-prints
4. This Youtube video that got me started on this entire idea of a wireless, endgame Charybdis: https://www.youtube.com/watch?v=Mks7QDxFreY


#### Table of contents
* [Before we begin](#before-we-begin)
* [Disclaimer](#disclaimer)
* [Build Guide](#build-guide)
    * [1. Required Parts](#step-1-required-parts)
    * [2. Assembly](#step-2-assembly)
    * [3. Software](#step-3-software)
* [Thanks](#thanks)

# Before we begin

The Charybdis was created and designed by [Bastard Keyboards](https://bastardkb.com/) so I take no credit in the creation or design. To learn more about the Charybdis itself, read about it on [Charybdis Github](https://github.com/Bastardkb/Charybdis) repo. 

The purpose of this guide is mainly to take a note on what I have done to building a Wireless (Bluetooth) Charybdis, since there are only a few guides out there and many of them seem to be written by MUCH smarter people than me. I am going to build a 3x6 Charybdis Mini with the goal of having a Prospector dongle with it, therefore my guide will be specifically for that.

**Important notes:**

- The necessary files for PCBs and 3D files are scattered across Github, I will be referring to the each file specifically in this guide.

# Disclaimer 
**Follow at your own risk**, I am not liable for anything that does not work. If you are unsure of something I would suggest you stop by the Bastard Keyboards discord if you have questions. This is not really meant to be a complete step-by-step list. It is, however, meant as a way for me to document what was odd or hard for me as I followed a collection of other resources.

# Build Guide

## Step 1: Required Parts
### PCBs
I have ordered PCBs from JLCPCB.

For PCBs, most important part is, thumb parts needs to be thinner than usual. For building a nano or mini 0.8mm is enough, but for a full size, 0.6mm is recommended as flexibility is required. I did not change rest of the settings for other parts.

If possible, I would have preferred to have ordered thinner boards for the main parts as well. That would have made attaching the board to the switches much easier. It would have also have made it possible (maybe?) to use hot swap sockets.

#### PMW3610 Breakout
[Link to Void's repo](https://github.com/victorlucachi/charybdis-pmw3610-breakout/tree/nicenano/production)

For this PCB, you will need to solder PMW3610 later.

For the assembly, JLCPCB did not have `TCR2EF19`, which I replaced it with `TLV70018DDCR`:
```
#(Old) TCR2EF19:
73dB@(1kHz) 200mA Fixed 1.9V Positive 5.5V SOT-23-5 Linear Voltage Regulators (LDO) ROHS

#(New) TLV70018DDCR:
68dB@(1kHz) 200mA Fixed 1.8V Positive 5.5V SOT-23-5 Linear Voltage Regulators (LDO) ROHS
```

#### Nice!Nano Holder
[Link to olidacombe's repo](https://github.com/olidacombe/Elite-C-holder/tree/nicenano/adapter/production)

This PCB Design supports having a power switch that makes use of audio jack hole. Mine did not end up using the audio jack. Instead, the switch sits inside of the case and you reach in to use it. Frankly, it is not clear to me which direction is "on" and which is "off" between the two boards. I believe both of them have "on" when the switch is pulled to the center of the two boards (if they are on my desk). When I eventually get the prospector to work correclty, I think this will be easier. I also want to look into adding a small LED to the inside of the case that can indicate if it is on, if it is connected, etc.

#### PCB Thumbs
[Link to PCB thumbs](https://github.com/Bastardkb/Charybdis-PCB-thumbs/releases/tag/2.01)

Olidacombe also has a [fork](https://github.com/olidacombe/Charybdis-PCB-thumbs), in order to move wiring to left, but I personally did not use it.

### Flexible PCB Thumbs (for left)
[Link to repo](https://github.com/Bastardkb/TBK-Mini-PCB-thumb-cluster/releases/tag/2.1)

As I mentioned above, I think I ordered with 0.6mm thickness and did not change anything else.


### Flexible PCB for the plate (3x6)
[Link to repo](https://github.com/Bastardkb/TBK-Mini-PCB-plate/releases/tag/2.21)

Again, I ordered with 0.8mm thickness. Others dyed the boards black. I didn't think it would be that big of a deal. I was wrong. It wouldn't be a big deal if I was building one of the full size Charybdis. However, in the future I will probably re-order these with the boards dyed black so that they are less obvious. That is annoying since I had to order several of these already. I have enough to build 5 complete sets. Oops.

### 3D Prints
I printed everything for this build on my BambuLab P1S. I used Matte PLA for the blue and the orange and regular PLA for the black. I will add the link of each part have 3D printed for a 3x6 build.

I followed the BKB instructions for settings for my printer. That said, I don't know that it was completely necessary.

This is different from the official README, as it does not use bearings for trackball and uses ceramic bearing balls. Some of the designs require the 3D model to be mirrored, I will link my mirrored files in this repository (Please refer to [Disclaimer](#disclaimer)).

- [Right case 3MF](https://github.com/Bastardkb/Charybdis/blob/2dad0ca/files/3x6%20mini/CMini_v1_v11.3mf), [STEP file](https://github.com/Bastardkb/Charybdis/blob/9afdbc9/files/3x6%20mini/CMini_v1_v11.step)
- [Left case STL](./3d-prints/case_v3_v29_mirrorred.stl)
- [Right Plate STL](https://github.com/Bastardkb/Charybdis/blob/3908164/files/3x6%20mini/plate_v1_v11.stl)
- [Left Plate STL](./3d-prints/plate_v3_v29_mirrorred.stl)
- [Adapter - top STL](https://github.com/Bastardkb/Charybdis/blob/c818c76/files/3x5%20nano/adapter_v2_top_v75.stl)
- [Adapter BTU Bottom](https://github.com/Bastardkb/Charybdis/blob/d0e20cc/files/mods/btu/adapter_btu_bottom_v32.stl)
- [Printable 2.5mm BTU Ball](https://github.com/Bastardkb/Charybdis/blob/322faad/files/mods/printable-btu/printable_btu_2.5mm_ball.stl), You need 3 of these
- [Tent Left STL (Optional)](https://github.com/Bastardkb/Charybdis/blob/4924527/files/3x6%20mini/tent_v2_v57.3mf)
- [Tent Right STL (Optional)](./3d-prints/tent_v2_v57_mirrorred.stl)
- [Sensor Cover](https://github.com/Bastardkb/Charybdis/blob/9130a58/files/sensor_cover_v51.stl)
- [Travel Case](https://makerworld.com/en/models/1007550-charybdis-mini-travel-case)

#### Tips after build
- I would like to replace plates with metal ones to add more weight, and also less flexibility as ribbon wires add pressure.
- I added magnetic rings to the bottom of the plates so that I can tent th eboards with phone stands from Amazon.

### Required Components
In this section, I will go through each component I have bought, and also give example links. As of writing, I locate in Netherlands, therefore I tried to source some of the parts across European countries. 

| Name                         | Count | Link                                                                                                                         |
|------------------------------|-------|------------------------------------------------------------------------------------------------------------------------------|
| Trackball                    | 1     | I stole the ball from my MX Ergo                      |
| nice!nano microcontroller    | 2     | [Splitkb.com](https://splitkb.com/collections/keyboard-parts/products/nice-nano)                                             |
| (optional) mill max sockets  | 2     | [Splitkb.com](https://splitkb.com/collections/keyboard-parts/products/mill-max-low-profile-sockets?variant=31945995845709)   |
| SOD123 Diodes                | 41    | [Splitkb.com](https://splitkb.com/collections/keyboard-parts/products/smd-diodes)                                            |
| Button, 4x4x1.5              | 2     | [Aliexpress](https://www.aliexpress.com/item/4001046134819.html)                                                             |
| PMW3610 module               | 1     | [Aliexpress](https://www.aliexpress.com/item/1005006208592770.html)                                                          |
| Mini Toggle Switch TS-6 SPDT | 2     | [Aliexpress](https://www.aliexpress.com/item/1005003684819561.html)                                                          |
| Batteries                    | 2     | [Aliexpress](https://nl.aliexpress.com/item/1005005348368664.html)                                                           |
| Ceramic Bearing Balls 2.5mm  | 3     | [Aliexpress](https://www.aliexpress.com/item/1005004239319689.html)                                                          |
| Flexstrip Jumper Cables      | 2     | [Aliexpress](https://www.aliexpress.com/item/1005003498734969.html)                                                          |
| Key Switches                 | 41    | [Aliexpress](https://www.aliexpress.com/item/1005003761194503.html)                                                          |
| M3 5mm Brass Melt Nuts       |       | [Aliexpress](https://www.aliexpress.com/item/1005003582355741.html)                                                          |
| M4 5mm Brass Melt Nuts       |       | [Aliexpress](https://www.aliexpress.com/item/1005003582355741.html)                                                          |
| M3 8mm Torx Screws           |       | [Aliexpress](https://www.aliexpress.com/item/1005006115217679.html)                                                          |
| M4 8mm Torx Screws           |       | [Aliexpress](https://www.aliexpress.com/item/1005006115217679.html)                                                          |
| JST plug 2-pin               | 2     | [Aliexpress](https://www.aliexpress.com/item/1005006115217679.html)                                                          |


#### After Build Notes:
##### Ribbon Cables
BastardKb docs mention you require 30 wire ribbon cables, but its not specifically mentioned what type or length is required. From the link I sent above, I bought a 24 Pin 82MM Length and 12 Pin 70MM Length just to make sure. Frankly for future builds I need to measure these out much better. If they were shorter and more direct, then the internals of the case would be much cleaner. 

##### Batteries and JST Direction
One important part here is the battery. If you order a battery from Aliexpress to Europe, the order will be shipped with freight, meaning it will take ~2 months to arrive. Due to this reason, if you reside within EU, I would recommend to source a battery of your choice within EU. What needs to be considered before ordering any battery is to ensure that it is:
- 3.7V
- More than 80mAh
- If you want to squeeze the battery between nice!nano and and the holder PCB, then you need to be careful of its size. At [42keebs.eu](https://42keebs.eu/shop/parts/lithium-polymer-battery/?attribute_size=301230%20(80%20mAh)), it states that you can fit `350926`, `301230`, `401030` underneath the nice!nano microcontroller.
- Again, if you would like to fit a battery underneath nice!nano, you may want to buy [Mill Max Low Profile Sockets with Headers](https://splitkb.com/collections/keyboard-parts/products/mill-max-low-profile-sockets?variant=47060695646555) In order to create the gap in between.

The JST sockets to connect the batteries ended up being a giant PITA. I ended up not using them. Instead, I soldered the battery wire to the shield such that the JST plug to connect to the battery itself sits inside of the case and then then wires can be routed as needed. I'm not sure what would be cleaner/better, but this worked for now.

##### Nice!Nano Direction
Make sure you pay attention to which side of the Nice!Nano you are soldering the headers onto. That cost me a good penny by soldering up both sides of one board before I realized that I had messed up.

##### On/Off Switch
Also, the on/off switches I ordered are vertical from the shield they mount to. I wish I had sourced some that would sit on the shield so that the switch stuff off to the side. That would make it easier to operate the switches. 

##### Switch Soldering
Soldering the switches directly to the boards was not terribly difficult, but some of them did require an extra set of hands to help bend the board into the place while I tacked the switches on. Thankfully, thus far it would seem that all of our solder connections are solid.


## Step 2: Assembly
Most of the steps are similar to building a Charybdis Nano. I will try to explain what I have done differently.

1. Install screw inserts: [BastardKB Docs](http://docs.bastardkb.com/bg_cnano/04screw_inserts.html)
1. Solder diodes: [BastardKB Docs](http://docs.bastardkb.com/bg_cnano/05diodes.html)
1. Solder PMW3610 to sensor board
    - There is a single orientation to solder it, I don't think you will have any issues in this step. I would recommend to take out the sensor cap while doing any soldering to prevent touching it via solder iron. There is also kapon tape on the sensor, before starting to use it I would recommend to take them out.
1. Solder power switch to nice!nano holder
1. Solder button
1. Solder JST female plug
    - I soldered it in the same orientation with button where I can also reach to it from the side. Assembling nice!nano holder to case becomes a bit tight but it barely fits without pressure.
1. Solder nice!nano
    - [This video from Joe Scotto](https://youtu.be/l5kAx08Iom4) helped me a lot in this part. As it mentions, temperature on nice!nano is important, do not go above 300 degrees Celsius.
    - **Important** If you run into issues with wiring and in need to do desoldering, make sure to take out the nice!nano first!
1. Try connecting battery and see if nice!nano works
1. Install ribbon cables (including sensor board): [BastardKB Docs](http://docs.bastardkb.com/bg_cnano/07ribbon_cables.html)
    - I tried to pay attention to how BKB shows the ribbon cables being angled through the PCB. However, it would appear that almost all of them should have been angled the other direction.
    - I actually did this after I soldered the switches on. That was a mistake because I could have fixed some issues with the way in which the ribbon cables are tucked into the case.
1. Install and solder switches
    - I watched BastardKB build videos on Youtube for this part!
1. Install sensor board
    - During sensor assembly, I initially did not understand BTU prints were supposed to be installed angled, and needs to go all in. This is important otherwise ball will stay too high and sensor will not be able to read it. The bearings are press fit, so you can just mash them in.

## Step 3: Software
Connecting nice!nano for the first time is its reset mode, all you need to do is to drag and drop built image, which will flash itself. No need to change names or anything. Right hand is the main controller which you can connect to it via bluetooth and left hand automatically is connected to right hand.

When I first tried to set up the Prospector I managed to brick the board by deleting all of the files off the board to try to flash it. It would appear that was unnecessary and I will have to work on how to fix the issue (**10/19/2025**)

The software for the wireless version of the Charybis is getting a lot of ongoing development within the community. I, being relatively dumb when it comes to ZMK (and QMK for that matter), have had to rely heavily on the work of others.

My goal is to be able to edit the keymap/configuration of the keyboard using [ZMK Studio](https://zmk.studio/).

[Here is a repo](https://github.com/apetrovic6/zmk-charybdis) that uses Studio with a micro (so one less column than mine here). 

Similarly, [here is another repo](https://github.com/gukas/zmk-config-charybdis-4x6-prospector) that sets up a wireless 4x6 version (so the full sized version) with a prospector dongle.

This [repo](https://github.com/moverisJustin/charybdis-wireless-mini-zmk-firmware) presents an interesting approach to helping setup all of the necessary steps. It includes Github Actions to generate the necessary .uf2 files. You can do it with or without a dongle through this repo. However, the approach used in this repo makes it hard to translate the keymaps from other repo examples. It also does not allow you to use existing keymap editors like [this one] (https://nickcoutsos.github.io/keymap-editor/). Notably, I have not attempted to use this repo with Studio, so that could be a path forward.

You can find the zmk config from Erenatas (whose build guide I followed) here: [https://github.com/erenatas/zmk-config-charybdis-mini-wireless](https://github.com/erenatas/zmk-config-charybdis-mini-wireless), He added scroll support via forking [@grassfedreeve](https://github.com/grassfedreeve)'s config and adapted it to 3x6 mini. 

# Thanks
I would like to thank several specific folks who helped me make this dream keyboard a reality!
- [EIGA](https://www.youtube.com/watch?v=Mks7QDxFreY) with his Youtube.
- [BastardKB](http://bastardkb.com/)
- [VOID](https://github.com/victorlucachi)
- [olidacombe](https://github.com/olidacombe)
- My brother for his help teaching me to solder and letting me take up space in his office while I finished this build.

