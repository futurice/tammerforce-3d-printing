# LulzBot TAZ 6

## Quickstart
_AKA HOW DO I PRINT WITH THIS THING??_

1. Install [Cura](https://www.lulzbot.com/cura).

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
