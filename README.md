# DELL-OptiPlex-7040-Clover
Clover for OptiPlex 7040 with Skylake CPU & GPU

Only fix the Graphics by Bios hack, Ethernet, USB, and sound card with AppleALC, but, is enough! Less is more.

Test with OptiPlex 7040 which using i7-6700, Intel HD Graphics 530, Intel I219LM2 Ethernet, macOS 10.14.4

- I extract the BIOS.rom by AMI Flasher utility.
- I modity the DVMT to 64MB by [https://www.firewolf.science/2015/04/guide-intel-hd-graphics-5500-on-os-x-yosemite-10-10-3/]
- DVMT Pre-Allocated address is 0x350, so "setup_var 0x350 0x2" to set 64MB [中文教程](https://zhuanlan.zhihu.com/p/39798235)
- Note: the DVMT fixup will lose after set BOIS to factory default!
- DVMT fix is recommend, even though whatevergreen can do some path to fix it.

## DVMT fix step
1. unzip 'EFI-shell.zip' to a `FAT32` partition of a USB disk
   
   you will see some thing like this : "/Volumes/UDISK/EFI/BOOT/bootx64.efi" 
   
   or "E:/EFI/BOOT/bootx64.efi" 
2. reboot you machine using this this USB disk in `UEFI BOOT MODE`
   
   and you will see a cmd line
3. just run `setup_var 0x350 0x2` using this cmd line

4. fine, the graphics is ok to boot up macOS

### Know issue 
1. Just one DP port work
   
   you need to switch to an other DP port and reboot, if no DP signal after you see the "white apple" startup logo.

### FAQ
1. SIP enable default ?

   Yes. It way enabled by "config.plist/RtVariables/CsrActiveConfig=0x11".
2. What should we do before install macOS system upgrade ? eg.upgrade from 10.14.4 to 10.14.5
  
   Maybe you need to disable SIP before doing upgrade: Set "config.plist/RtVariables/CsrActiveConfig=0x67".
