### Instructions

Inside the kext folder you will find the necessary kexts for the card to work, place them into your *EFI/CLOVER/Kexts/Other* folder.

Finally add the following Lines to your Clover file:
(I have included screenshots for convenience)
(Remember to replace the Question *(?)* marks with your actual PCI ID)


Under /Devices/Properties key
***



			<key>PciRoot(0x?)/Pci(0x?,0x0?)/Pci(0x0)</key>
			<dict>
				<key>AAPL,slot-name</key>
				<string>WLAN</string>
				<key>compatible</key>
				<string>pci14e4,4353</string>
				<key>device_type</key>
				<string>Airport Extreme</string>
				<key>model</key>
				<string>Dell DW1820 (BCM4350) 802.11ac wireless</string>
				<key>name</key>
				<string>Airport</string>
			</dict>
		</dict>

***


Under force Kext to load:

		<key>ForceKextsToLoad</key>
		<array>
			<string>\System\Library\Extensions\IONetworkingFamily.kext</string>
		</array>
		
* Notes: If you find the DW1820A not working properly you may try the pin-masking trick. Same pins should be masked for any computer. The following picture shows the pins-to-mask in red color.

![Imgur](https://i.imgur.com/kof6tzz.png)
		
###Credits

* the-darkvoid: Original BrcmPatchRAM and BrcmPatchRAM2 with the firmware injector
* RehabMan: Improvements to kexts
* acidanthera: Further improvements of bluetooth kexts, introduction of BrcmPatchRAM3 and AirportBrcmFixup
* Hervé: Properties injection from OSXLatitude