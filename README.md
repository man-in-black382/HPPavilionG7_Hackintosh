# HPPavilionG7_Hackintosh
Drivers and patched DSDT/SSDT files

Brightness slider enabled with IntelBacklight.kext and CLOVER DSTD fix “AddPNLF_1000000”

Brightness keys patch for DSDT:

into method label _Q10 replace_content
begin
// Brightness Down\n
    Notify(\_SB.PCI0.LPCB.PS2K, 0x0205)\n
    Notify(\_SB.PCI0.LPCB.PS2K, 0x0285)\n
end;
into method label _Q11 replace_content
begin
// Brightness Up\n
    Notify(\_SB.PCI0.LPCB.PS2K, 0x0206)\n
    Notify(\_SB.PCI0.LPCB.PS2K, 0x0286)\n
end;

VoodooHDA Volume Slider FIX

1. Set the volume to max both on System Volume settings and VoodooHDA preferences pane (the PCM output in particular).
2. Open the Terminal and go to /System/Library/Extensions/VoodooHDA.kext/Contents directory.
3. Type the command: sudo nano -w Info.plist.
4. Press CONTROL-W (^W for search) and search for the string "VoodooHDAEnableVolumeChangeFix" (without the quotes). Change the value from false to true. Save the file.
5. Fix your permitions and clear your caches.
6. Reboot the system. Volume controls now work 

TODO: make HDMI work
