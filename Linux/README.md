## Linux General Instructions

***
This is slightly distribution dependent.
I use Arch and I hope these instructions will translate to your Distro of choice.

The Modprobe Blacklist instructions and BT Firmware instructions **SHOULD** be distribution agnostic.

***

##**WIFI**

For linux, The WiFi portion of this card works well with the brcmfmac Kernel driver.

Normally this should load and autodetect, but if it does not, be sure to BLACKLIST other broadcom and iw drivers.

Blacklisting drivers can be found here:

    https://wiki.archlinux.org/index.php/Kernel_module#Using_files_in_/etc/modprobe.d/_2

***

so for example a **/etc/modprobe.d/99_broadcom_blacklist.conf** would look like this:

    blacklist b43
    blacklist b43legacy
    blacklist iwlwifi

***

If you create the file with that contents, it will block other broadcom/intel wifi drivers loading at boot time, allowing brcmfmac to do its job.

This will make sure you have fully working wifi.
***

##**BLUETOOTH**

For bluetooth however, The normal drivers are buggy.
For arch this patch is fantastic (Download/Install from AUR)

    https://aur.archlinux.org/packages/bcm4350c5-firmware/

***

For your own distribution, you will need to find bcm4350c5-firmware
package, or you can take a look at the arch PKGBUILD:


    https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=bcm20702a1-firmware


Then apply the firmware modifications yourself.

**I gather the steps are as follows:**

List your usb devices

    lsusb

shows this on my laptop for Bluetooth

    Bus 002 Device 002: ID 0a5c:6414 Broadcom Corp. BCM4350C5 Bluetooth

Go to the following Github page and download the already converted driver that matches your ID: https://github.com/winterheart/broadcom-bt-firmware/tree/master/brcm (mine was BCM4350C5-0a5c-6414.hcd) Click on the file name, then click the Download button.

Copy your file to /lib/firmware/brcm, for example:

    sudo cp BCM4350C5-0a5c-6414.hcd /lib/firmware/brcm

Reboot.

This will enable fully working wifi/Bluetooth with the DW1820A on Linux.

Hope that helps!
