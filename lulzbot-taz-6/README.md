# LulzBot TAZ 6

## Quickstart
_AKA HOW DO I PRINT WITH THIS THING??_

0. If you have local access to the printer computer (at the corner of Markku), skip to step 3.

1. Download remote desktop client (for Mac you can use [Microsoft Remote Desktop](https://apps.apple.com/us/app/microsoft-remote-desktop-10/id1295203466))

2. Connect to tre-iot-hub.futurice.com (works from office network and VPN)

3. Login to the computer. You can find login credentials from password.futurice.com with name "Tampere Simplify3D"

4. Open Simplify3D software from dock if not already open

5. Load your `.stl` or `.obj` model file in Simplify3D. You can find models from [thingiverse](https://www.thingiverse.com/).

6. Make sure your model is laying flat on the ground on the 3D view. You probably shouldn't touch scaling or rotation, unless you know what you are doing.

7. Check which filament the machine is currently equipped with from the label of the filament roll. _Currently this is usually 2,85mm PLA._

8. On the bottom of the left hand side menu click "Edit process settings". Select matching _Material_ from the "Auto-Configure for Material" menu.

9. Select your desired _print quality_ from the next menu. _Medium_ is probably good enough, unless you want to have a finer finish or faster print.

10. Determine if your piece needs supports to be printed. Pieces with overhangs often need support structures for the printing to succeed. Need of supports is also often specified in thingiverse description / comments. Enabled supports by ticking _Generate support_.

11. Click OK and create your print with "Prepare to Print" button.

12. Make sure the estimated print time & filament usage makes sense. 3D printing is quite slow by its nature. Please make sure that someone can stay at the office until the print is finished. __NOTE:__ The estimated time is often less than actual print time.

13. Export your print as `.gcode` file with some reasonable filename with the "Save toolpaths to Disk" button.

14. Open browser and go to octoprint.iot.tre.futurice.org

15. If Octoprint indicates that it is not connected to the printer, power up the printer and press "Connect".

16. Upload the GCode to the Octoprint server with "Upload" button.

17. Find your file and press the printer icon to start the print.

18. After the print is done, the part will first be cooled down. After the desired cooling temperature is reached (45 C° for PLA), the printer will move back to neutral position and the part can be removed. The knife with blue handle and mild violence can be used to separate the piece from heat bed.

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
