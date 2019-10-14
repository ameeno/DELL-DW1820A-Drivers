### Instructions

Inside the kext/* folder you will find 4 kexts,

All of these kexts are credited to Rehabman and his hard work.
The patch for clover.config was originally from Herve from OSXLatitude

place the 4 kexts into your *EFI/CLOVER/Kexts/Other*

Folder.


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
