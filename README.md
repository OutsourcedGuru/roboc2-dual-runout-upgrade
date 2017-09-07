# roboc2-dual-runout-upgrade
Step-by-step instructions for upgrading the Robo C2 to support dual filament run-out detection.

# Skills
You'll need soldering skills for this project. There will be small wires and tiny connectors on those switches.

# Order Parts
For this project, you'll need two microswitches and an optional two-pin JST connector. You'll also need some small-gauge wire of any color. The printed part requires tight tolerances for the switches so it's important to get the exact same part for this to fit. (The lever must swing unhindered through an arc which is only interrupted by the existence of filament for it to accurately close.)

If you don't want to purchase the two-pin JST connector, it's your option to de-solder the one from your existing run-out sensor's assembly from the small circuit board it's on.

Additionally, you'll need to print a replacement filament run-out switch box for the back of the printer. I used standard black PLA for this and it resulted in a nice-looking part.

# Software
My own Robo C2 arrived with an inoperative filament run-out switch. It didn't detect when the filament was inserted nor when it ran out, resulting in some aborted jobs. Reviewing the OctoPrint -> Settings -> Plugins, I did see that the stock [Filament Sensor plugin](http://plugins.octoprint.org/plugins/filament_sensor/) was supposed to be running. Checking the cabling, the connection from the run-out sensor was securely plugged into the Raspberry Pi 3's GPIO pins. And yet, it didn't work.

I think I'd like to replace the original plugin with something else that allows more options.

# Design Criteria
* I wanted to be able to detect a run-out of either filament rolls in anticipation of a dual-extruder upgrade which comes next
* I didn't want to have to re-wire the Raspberry side of things so I've tried to keep the upgrade in the localized area of the replace run-out switch assembly with respect to changes
* It's possible to use this with only a single filament in play; just cut a spare bit of 1.75mm filament at 5", bend an L-shape (or full circle) at the top and then insert it into the second filament hole to close that switch as a "dummy" marker
* In this single-filament mode, note that the spare filament "dummy" may be pulled from the sensor to pause a print job as if you'd pressed the Pause button from the LCD screen


