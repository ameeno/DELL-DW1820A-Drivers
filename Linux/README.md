### Linux General Instructions

This is slightly vague, sorry as it is highly distribution dependent.

I Use Arch And i hope these instructions will translate to your Distro of choice, or perhaps you can build from source.


For linux, The WiFi portion of this card works well with the brcmfmac Kernel driver.

Normally this should load and autodetect, but if it does not, be sure to BLACKLIST other broadcom and iw drivers!!!!


Blacklisting drivers can be found here:

https://wiki.archlinux.org/index.php/Kernel_module#Using_files_in_/etc/modprobe.d/_2



so for example a 99_broadcom_blacklist.conf would look like this:
  blacklist b43
  blacklist b43legacy
  blacklist iwlwifi


For bluetooth however, The normal drivers are buggy.

For arch this patch is fantastic (Download/Install from AUR)

https://aur.archlinux.org/packages/bcm4350c5-firmware/



For your own distribution, you will need to find bcm4350c5-firmware
package, or you can take a look at the arch PKGBUILD:
https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=bcm20702a1-firmware
and apply the firmware modifications yourself.

In a nutshell, it downloads the windows zip file for bluetooth, extracts the firmware for bluetooth for this card, and patches it to work with linux.


This will enable fully working wifi/Bluetooth with the DW1820A on Linux.
