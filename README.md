# roboc2-dual-runout-upgrade
Step-by-step instructions for upgrading the Robo C2 to support dual filament run-out detection.

# Overview
The Robo C2 is a great printer out-of-the-box with few exceptions. In my case, one of those exceptions was that the filament run-out sensor simply does not work. Even though the C2 includes two slots for hotends and two filament guides there at the back, there was no support added for that second guide slot. In these cases, it's time for an upgrade. This project will replace the stock filament run-out assembly completely with one that should work for two rolls of filament at the same time.

# Skills
You'll need soldering skills for this project. There will be small wires and tiny connectors on those switches. In my case, I'm adding a hot glue step so keep this in mind. Your two microswitches might just fall in place and not need to be tweaked a little to prevent an always-closed condition. Mine will both require this tweaking, to be explained in the Instructions section. You will definitely need a multimeter or rig up a circuit which will show electrical continuity. To pull off this feat of magic, you should own a [caliper](http://www.homedepot.com/p/General-Tools-Fraction-Plus-6-in-3-Mode-Digital-Caliper-147/100651811) and know how to measure things accurately in millimeters. Depending upon your printer settings, you might consider using a small drill bit to make the screw holes larger if necessary (mine seem perfect but "your mileage may vary").

# Order Parts
For this project, you'll need two microswitches, an optional two-pin JST connector and/or small alligator clip cables for your multimeter. You'll also need some small-gauge wire of any color. The printed part requires tight tolerances for the switches so it's important to get the exact same part for this to fit. (The lever must swing unhindered through an arc which is only interrupted by the existence of filament for it to accurately close.)  The specified microswitches (quantity two) are the [Philmore Micro Snap Action Switch Short Lever UPC 0 38975 23401 4](http://www.frys.com/product/7824549) at $1.89 each—I picked mine up at Fry's to save on the shipping. The [JST Sales CONN HEADER PH SIDE 2POS 2MM](https://www.digikey.com/product-detail/en/S2B-PH-K-S(LF)(SN)/455-1719-ND/926626?WT.mc_id=IQ_7595_G_pla926626&wt.srch=1&wt.medium=cpc&&gclid=EAIaIQobChMI0ZbGkdCR1gIVF5J-Ch2gRg_3EAQYAyABEgKh-vD_BwE) connector costs $0.17.  The project total cost (minus filament, wires, solder, shipping, tax and labor) then is $3.95. You should order a minimum of four of the microswitches; I've found them to be fragile and easily destroyed since they aren't formed together 100% and may split apart with too much force.

![microswitch](https://user-images.githubusercontent.com/15971213/30178853-50445b2e-93bf-11e7-8a34-8e062834d6c6.jpg)

If you don't want to purchase the two-pin JST connector, it's your option to de-solder the one from your existing run-out sensor's assembly from the small circuit board that it's on. This puts your existing sensor at-risk so maybe you shouldn't do that to allow yourself an easy fall-back plan.

![jst-connector](https://user-images.githubusercontent.com/15971213/30178031-79f04760-93bc-11e7-97dd-9545d22b42e7.jpg)

Unless you have four hands, you should probably have a pair of [small alligator clip cables](https://www.adafruit.com/product/1592?gclid=EAIaIQobChMIuPjBgrOl1gIVmrjACh0EswbPEAQYAiABEgJhVvD_BwE) to test each microswitch once installed.

![small-alligator-clips](https://user-images.githubusercontent.com/15971213/30451083-a0c03752-9947-11e7-84a0-e6cea71ed48b.jpg)

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

Examine the part closely. You're testing for the following criteria in order to move on to the installation of the microswitches.

## Filament path clearance
There should be two holes which run through the part vertically, as installed on the back of the printer. A 1.75mm section of filament should easily slide through each hole. If not, you might need to try re-printing the part since it's crucial for the success of your sensor block.

## Guide tube
Your existing filament guide tube (4mm OD) should fit snugly inside the top of each hole. It should not fall out if you move things around.

## Internal
The inside of the part shouldn't have any printing artifacts left over, especially in the somewhat-rectangular spaces reserved for each microswitch and the space which allows the lever to move throughout its travel.

## Screw holes
It took several versions of this part to finally get the correct hole sizing for the two screw holes. In this case, if your printed part's screw holes aren't large enough to accept the stock screws from the original sensor block, you might consider drilling them slightly larger as necessary.

## Microswitch fit
If you've passed all tests up to this point, you're probably at the point of committing the first microswitch to a fit attempt. Note that this is a difficult step.

### Installing a microswitch
It helps to have a pair of [hemostats](https://www.grainger.com/product/39P047?cm_mmc=PPC:+Google+PLA&s_kwcid=AL!2966!3!166587266386!!!!82166196597!&ef_id=WXYq2AAAAIwGuxob:20170914193946:s&kwid=productads-adid^166587266386-device^c-plaid^82166196597-sku^39P047-adType^PLA) or small needle-nosed pliers for this. Remember at all times that these microswitches like to break in half at the seam if you put too much pressure on them.

First, prepare the microswitch by orienting the switch in the direction that it will rest in the intended side of the block. You now need to bend completely the unnecessary contact against the microswitch's side.

Next, slightly bend the opposite contact toward the middle contact, about 30 degrees should work.

In order to get this into the slot, the trick is to gently align one end until it's a fraction of a millimeter into that slot, then push in/down on the opposing end. All the while, you must make sure that the lever is fully closing the switch. Go gently. There will be a satisfying moment when the far end has now entered the rectangular section but now stop and take a breather. Evaluate where you are:

1. the lever must be just inside the arc slot for it
2. both ends of the microswitch should now be just inside the rectangular slot
3. the entire microswitch should be flat with respect to the plane of the top
4. at this point, it doesn't look like that 30-degree-bent contact is going to clear the little point

Next, it's good to grab that contact with your hemostats or something small/pokey and while gently pushing it around that point in the part, try to convince it to move past that and into the clear section below this. (Believe it or not, there's a reason for this design.) Once you've cleared the point again, take a break and review:

1. the 30-degree-bent contact is now past the point
2. again, make sure that the entire microswitch is flat with respect to the plane of the top

You're in the final push now. The trick is to evenly push down on the top of the microswitch to guide it into the bottom of its receiving slot. You're trying not to abuse the lever. You're trying not to accidentally spin the microswitch in any axis. It should eventually rest at the bottom and without breaking it in two with too much force. When you're satisfied that it's now in place, use your hemostats to bend that 30-degree-bent contact back to its original straight position.

## Microswitch initial test
Now's a good time to attach the two alligator clip cables to each of the contacts on the microswitch and then to your multimeter, setting it for resistance. I adjust mine to make a tone when there's a closed circuit.

For proper operation, the switch should be open if no filament is running through that slot and closed when it is. Don't panic if it's already closed (mine was doing that, too). This is to be expected given the tight tolerances.

If your microswitch performs this test perfectly (on with filament inserted, off without) then move on to the opposite switch installation.

If your microswitch is closed regardless of filament, remove the filament. Next, use something like your hemostats or a small nail to move the microswitch away from the filament path. If this now results in an open circuit, this is good. It means that you can apply some hot glue, holding the switch until it cools, in order to adjust the exact positioning so that it will work.  After the glue has completely cooled, repeat the original test.  If it passes then move on to the opposite switch installation. If this test fails, you'll want to heat up the glue, move the switch again and repeat until it passes.

If your microswitch is open regardless of filament, add the filament into the slot. Use the instructions in the paragraph above, just move the microswitch closer to the filament path. Again, hot glue to hold it in place while testing. Continue as in the instructions above.

## Second microswitch
Repeat for the second microswitch.

## Solder
(work-in-progress)
