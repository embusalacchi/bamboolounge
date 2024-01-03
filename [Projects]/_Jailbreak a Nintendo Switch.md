Jailbreak a Nintendo Switch

Download the zips and binaries found on the [QuickStart Guide](https://yuzu-emu.org/help/quickstart/#yuzu-quickstart-guide)
Make sure you have the JCM Jig.
Shutdown the Switch completely.
Install TegraRcmGui and install the USB drivers.
Remove right joycon.
Insert Jig to the Bottom of the right joycon slot
Hold down Volume Up and hold the power button.  If nothing happens you are in debug mode.  If the Switch boots up then you need to try again.
Remove the jig and put the right joycon back on.
Connect the Switch to your computer using a USB-C Cable the handles data and not JUST POWER.
Using TegraRcmGUI find the file you downloaded name "TegraExplorer.bin" and inject the payload.
Using the Switch select format sd card and chose FAT32 + eMMC.
Once that is done select "Reboot to RCM".
Take out the SD Card and put it back in your computer.  
Move the files to the SD Card as found in the "Preparing the microSD Card" section of the [QuickStart Guide](https://yuzu-emu.org/help/quickstart/#yuzu-quickstart-guide)
Create emuMMC
Install [tinfoil](https://tinfoil.io/Download#download)
