# roboc2-dual-runout-upgrade
Step-by-step instructions for upgrading the Robo C2 to support dual filament run-out detection.

# Overview
The Robo C2 is a great printer out-of-the-box with few exceptions. In my case, one of those exceptions was that the filament run-out sensor simply does not work. Even though the C2 includes two slots for hotends and two filament guides there at the back, there was no support added for that second guide slot. In these cases, it's time for an upgrade. This project will replace the stock filament run-out assembly completely with one that should work for two rolls of filament at the same time.

# Skills
You'll need soldering skills for this project. There will be small wires and tiny connectors on those switches.

# Order Parts
For this project, you'll need two microswitches and an optional two-pin JST connector. You'll also need some small-gauge wire of any color. The printed part requires tight tolerances for the switches so it's important to get the exact same part for this to fit. (The lever must swing unhindered through an arc which is only interrupted by the existence of filament for it to accurately close.)  The specified microswitches (quantity two) are the [Philmore Micro Snap Action Switch Short Lever UPC 0 38975 23401 4](http://www.frys.com/product/7824549) at $1.89 each. The [JST Sales CONN HEADER PH SIDE 2POS 2MM](https://www.digikey.com/product-detail/en/S2B-PH-K-S(LF)(SN)/455-1719-ND/926626?WT.mc_id=IQ_7595_G_pla926626&wt.srch=1&wt.medium=cpc&&gclid=EAIaIQobChMI0ZbGkdCR1gIVF5J-Ch2gRg_3EAQYAyABEgKh-vD_BwE) connector costs $0.17.  The project total cost (minus filament, wires, solder, shipping, tax and labor) then is $3.95.

![microswitch](https://user-images.githubusercontent.com/15971213/30178853-50445b2e-93bf-11e7-8a34-8e062834d6c6.jpg)

If you don't want to purchase the two-pin JST connector, it's your option to de-solder the one from your existing run-out sensor's assembly from the small circuit board that it's on. This puts your existing sensor at-risk so maybe you shouldn't do that to allow yourself an easy fall-back plan.

![jst-connector](https://user-images.githubusercontent.com/15971213/30178031-79f04760-93bc-11e7-97dd-9545d22b42e7.jpg)

# Software
My own Robo C2 arrived with an inoperative filament run-out switch. It didn't detect when the filament was inserted nor when it ran out, resulting in some aborted jobs. Reviewing the OctoPrint -> Settings -> Plugins, I did see that the [Filament Sensor plugin](http://plugins.octoprint.org/plugins/filament_sensor/) was supposed to be running. Checking the cabling, the connection from the run-out sensor was securely plugged into the Raspberry Pi 3's GPIO pins. And yet, it didn't work. The design of the stock blade-type microswitch just didn't work at all from a physical tolerance standpoint and it's likely that Robo 3D just disabled the feature somewhere.

I think I'd like to replace the original plugin with something else that allows more options.

# 3D Part
For this project, you'll need to print the sensor assembly box in PLA. I used the [Robo Black PLA](https://store.robo3d.com/collections/filament-pla/pla-jet-black-500g) for this but any standard PLA filament should work.

# Design Criteria
* I wanted to be able to detect a run-out of either filament roll (in anticipation of a dual-extruder upgrade which comes next)
* I didn't want to have to re-wire the Raspberry side of things so I've tried to keep the upgrade in the localized area of the replace run-out switch assembly with respect to changes
* It's possible to use this with only a single filament in play; just cut a spare bit of 1.75mm filament at 5", bend an L-shape (or full circle) at the top and then insert it into the second filament hole to close that switch as a "dummy" marker
* In this single-filament mode, note that the spare filament "dummy" may be pulled from the sensor to pause a print job as if you'd pressed the Pause button from the LCD screen


