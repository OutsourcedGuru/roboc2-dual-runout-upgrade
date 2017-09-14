# roboc2-dual-runout-upgrade
Step-by-step instructions for upgrading the Robo C2 to support dual filament run-out detection.

# Overview
The Robo C2 is a great printer out-of-the-box with few exceptions. In my case, one of those exceptions was that the filament run-out sensor simply does not work. Even though the C2 includes two slots for hotends and two filament guides there at the back, there was no support added for that second guide slot. In these cases, it's time for an upgrade. This project will replace the stock filament run-out assembly completely with one that should work for two rolls of filament at the same time.

# Skills
You'll need soldering skills for this project. There will be small wires and tiny connectors on those switches. In my case, I'm adding a hot glue step so keep this in mind. Your two microswitches might just fall in place and not need to be tweaked a little to prevent an always-closed condition. Mine will both require this tweaking, to be explained in the Instructions section. You will definitely need a multimeter or rig up a circuit which will show electrical continuity.

# Order Parts
For this project, you'll need two microswitches, an optional two-pin JST connector and/or small alligator clip cables for your multimeter. You'll also need some small-gauge wire of any color. The printed part requires tight tolerances for the switches so it's important to get the exact same part for this to fit. (The lever must swing unhindered through an arc which is only interrupted by the existence of filament for it to accurately close.)  The specified microswitches (quantity two) are the [Philmore Micro Snap Action Switch Short Lever UPC 0 38975 23401 4](http://www.frys.com/product/7824549) at $1.89 each—I picked mine up at Fry's to save on the shipping. The [JST Sales CONN HEADER PH SIDE 2POS 2MM](https://www.digikey.com/product-detail/en/S2B-PH-K-S(LF)(SN)/455-1719-ND/926626?WT.mc_id=IQ_7595_G_pla926626&wt.srch=1&wt.medium=cpc&&gclid=EAIaIQobChMI0ZbGkdCR1gIVF5J-Ch2gRg_3EAQYAyABEgKh-vD_BwE) connector costs $0.17.  The project total cost (minus filament, wires, solder, shipping, tax and labor) then is $3.95. You should order a minimum of four of the microswitches; I've found them to be fragile and easily destroyed since they aren't formed together 100% and may split apart with too much force.

![microswitch](https://user-images.githubusercontent.com/15971213/30178853-50445b2e-93bf-11e7-8a34-8e062834d6c6.jpg)

If you don't want to purchase the two-pin JST connector, it's your option to de-solder the one from your existing run-out sensor's assembly from the small circuit board that it's on. This puts your existing sensor at-risk so maybe you shouldn't do that to allow yourself an easy fall-back plan.

![jst-connector](https://user-images.githubusercontent.com/15971213/30178031-79f04760-93bc-11e7-97dd-9545d22b42e7.jpg)

Unless you have four hands, you should probably have a pair of [small alligator clip cables](https://www.adafruit.com/product/1592?gclid=EAIaIQobChMIuPjBgrOl1gIVmrjACh0EswbPEAQYAiABEgJhVvD_BwE) to test each microswitch once installed.

# Software
My own Robo C2 arrived with an inoperative filament run-out switch. It didn't detect when the filament was inserted nor when it ran out, resulting in some aborted jobs. Reviewing the OctoPrint -> Settings -> Plugins, I did see that the [Filament Sensor plugin](http://plugins.octoprint.org/plugins/filament_sensor/) was supposed to be running. Checking the cabling, the connection from the run-out sensor was securely plugged into the Raspberry Pi 3's GPIO pins. And yet, it didn't work. The design of the stock blade-type microswitch just didn't work at all from a physical tolerance standpoint and it's likely that Robo 3D just disabled the feature somewhere.

I think I'd like to replace the original plugin with something else that allows more options.

# 3D Part
For this project, you'll need to print the sensor assembly box in PLA. I used the [Robo Black PLA](https://store.robo3d.com/collections/filament-pla/pla-jet-black-500g) for this but any standard PLA filament should work. You can find both the STL and GCODE files here. If you choose to slice the STL yourself you should leave the part flat with its back oriented down. This part does not work well at all with internal supports if oriented differently. You should print on the highest quality setting available. The clearances on all sides of the microswitches are intentionally tight. You'll likely curse me later but this is necessary as you'll see later—the proximity forces the microswitch to be in exactly the right spot with respect to the filament path.

# Design Criteria
* I wanted to be able to detect a run-out of either filament roll (in anticipation of a dual-extruder upgrade which comes next)
* I didn't want to have to re-wire the Raspberry side of things so I've tried to keep the upgrade in the localized area of the replaced run-out switch assembly with respect to changes
* It's possible to use this with only a single filament in play; just cut a spare bit of 1.75mm filament at 5", bend an L-shape (or full circle) at the top and then insert it into the second filament hole to close that switch as a "dummy" marker
* In this single-filament mode, note that the spare filament "dummy" may be pulled from the sensor to pause a print job as if you'd pressed the Pause button from the LCD screen

# Instructions
(under construction)

This is still a work-in-progress. I've got the fifth revision of the part printed, it looks great and I'm now on my second set of microswitches. I've developed a (complicated) method of inserting the microswitches without damaging them. My JST connectors just arrived from Digikey.

I'm taking a series of photos to describe the process throughout. So far, this has been decidedly fussy.

adf
