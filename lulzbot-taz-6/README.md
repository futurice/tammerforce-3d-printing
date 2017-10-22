# LulzBot TAZ 6

## Quickstart
_AKA HOW DO I PRINT WITH THIS THING??_

1. Install [Cura](https://www.lulzbot.com/cura). Notice that this is the Lulzbot version (there are several different Cura versions)! After installing, add the Taz 6 as a new machine (Machine->Add new machine->Taz 6).

2. Load your `.stl` or `.obj` model file in Cura. You can find models from [thingiverse](https://www.thingiverse.com/).

3. Check which filament the machine is currently equipped with from the label of the filament roll. _Currently this is usually 2,85mm PLA._

4. Select matching _Material_ from the left hand side menu. For PLA you can use e.g. _Material ease of use: Beginner - Material: PLA (Village Plastics)_, which has basic
205 C° Printing temeprature and 60 C° Bed Temperature settings.

5. Make sure your model is laying flat on the ground on the 3D view. You probably shouldn't touch scaling or rotation, unless you know what you are doing.

6. Select your desired _quickprint profile_ from the left hand side menu. _Standard_ is probably good enough, unless you want to have a finer finish or faster print.

7. Determine if your piece needs supports to be printed. Pieces with overhangs often need support structures for the printing to succeed. Need of supports is also often specified in thingiverse description / comments. Enabled supports by ticking _Print support structure_.

8. If you piece needs extra support to not fall / stick better to the surface, you can also select _Print brim_. For smaller pieces this is likely not required, but go ahead.

9. Make sure the estimated print time & filament usage makes sense. 3D printing is quite slow by its nature. Please make sure that someone can stay at the office until the print is finished. __NOTE:__ The estimated time is often less than actual print time.

10. Export your print as `.gcode` file with some reasonable filename. Transfer this file on the printers removable SD card. If you are using a 2016 MacBook, ~~cry yourself to sleep and~~ try to find a card reader.

11. Pop the SD card back into the printer, turn it on and select "Print from SD card" using the pushable knob on the device. Find your file, and start printing.

12. After the print is done, the part will first be cooled down. After the desired cooling temperature is reached (45 C° for PLA), the printer will move back to neutral position and the part can be removed. The knife with blue handle and mild violence can be used to separate the piece from heat bed.

For more in depth guide refer to the official [Operations guide](http://download.lulzbot.com/TAZ/6.02/documentation/guide/PDFs_for_web/TAZ_6_QSG_OPERATION_WEB.pdf
).

## Advanced

### Using custom printing profiles

Cura LulzBot Edition comes with bunch of custom profiles, but you can also create your own profiles by tweaking the settings and saving the profile as .ini file. If you come up with great settings, please give the files a nice logical name and commit them under `lulzbot-taz-6/profiles/<material>/` directory for others to use! If required, provide a small README file of the profiles usage.

To load a profile, load your model in Cura, change to full settings view from _Expert -> Switch to full settings_ and load the profile with _File -> Open profile_. Make sure that the settings match your printing material, and start printing!

### Printing using USB cable

You can also connect the Taz 6 printer to your computer using the USB type B connector behind the printer (this also worked with MacBook 2016 dongles).

Load your model in Cura, and select "Control" button which should now be visible on the top left of the 3D view. You can set the temperature manually and test that filament flows out of the printer by pressing "Extrude 10" button.

You can start printing by hitting Print. In this mode printing time only shown on your computer, and it seems like your computer needs to be connected to the printer until the print is complete. Don't crash your Cura during this time. :)

## Printing with OctoPi

In Futurice-Tampere network (or VPN) go to http://tre-octoprint.futurice.com/, and enter the credentials that can be found from password safe(search "Tampere Taz 6 OctoPrint"). Make sure the printer is turned on and hit "Connect" from the Connection menu.

Upload your files (already sliced .gcode files or .stl files that will be sliced on the device) and start printing.

Camera & DNS setup coming soon™

## Debugging

### PROBE FAIL CLEAN NOZZLE

This seems to occur when nozzle is too unclean to reliably conduct electricity. When autoleveling sequence is running, the printer lightly touches all corners until the nozzle contacts with the corner. If the nozzle head is not clean, this will fail and the printer will attempt to rewipe the head couple of times, until failing the print.

You should check Cura logs (if you are directly controlling the printer), every corner should register its coordinates:

```
Print started at 15:19:55
< Bed x: -9.00 y: -9.00 z: 1.868750
< Rewiping
< Bed x: -9.00 y: -9.00 z: 2.220625
< Bed x: 288.00 y: -9.00 z: 1.306875
< Bed x: 288.00 y: 289.00 z: 1.298125
< Bed x: -9.00 y: 289.00 z: 1.869375
< Eqn coefficients: a: -0.002500 b: -0.000604 d: 2.107064
< planeNormal x: 0.002500 y: 0.000604 z: 1.000000
< Probing done!
```

In this run the head was dirty, and rewiping happened once.

Try cleaning the head with some alcohol / rubbing the head without scratching it too badly.

This could also be caused by the frame not being square enough, refer to https://forum.lulzbot.com/viewtopic.php?f=36&t=4556&sid=d84f08e8bd061a2951cbe53aa686df41 and https://ohai.lulzbot.com/project/squaring-taz-6-frame/ (step 23).
