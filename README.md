# :computer: Laptop-AMD-Hackintosh


![MacOS Sequoia](https://github.com/Francesco010780/Laptop-AMD-Hackintosh/blob/main/Images/MacOS%20Sequoia.png?raw=true)


# 	:information_source: Specific

| Name      | Description                   |
| --------- | -----------                   |
| CPU       | AMD Ryzen 7 5700U             |
| Graphics  | AMD Radeon RX Vega 8 (Renoir) |
| Memory    | 16 GB DDR4-3200 MHz (2 x 8 GB)|
| SSD       | 512 GB PCIe® NVMe™ M.2 SSD    |
| Sound     | --          |
| Ethernet  | Tethering USB kext            |
| WiFi / Bluetooth  | Realtek RTL8821CE        |
| BIOS      | HP Laptop Bios          |

# :zap: ACPI
We will use [SSDTTime](https://github.com/corpnewt/SSDTTime) to create ACPIs

After extracting the archive, Windows users should run SSDTTime.bat
Linux users will have to open their terminal inside the extracted SSDTTime/SSDTTime-master directory then run python3 SSDTTime.py. Make sure you have Python 3 installed.
Upon launching the tool, it will automatically download iASL, which (de)compiles ACPI tables.

Select option P on the target system to dump the ACPI tables needed for SSDTTime’s operations.
If you’re not running SSDTTime on the target system, select D instead to pick the folder with the ACPI tables dumped from that target machine

Must choose the option below:
- [x] USBX, Choose the default option (B key).

- [x] RTCAWAC, If it says you don’t need it, skip this SSDT.

- [x] PluginType, and USB Reset.

- [x] FakeEC Laptop,
- [x] XOSI, Choose default (A key)

The Results folder will look similar to the below after you’re done.
Now, copy all the files that start with SSDT and end in .aml inside of the root of the Results folder to Drive/EFI/OC/ACPI.

Finally, merge patches_OC.plist by using the PatchMerge script included with SSDTTime. Run it the same way as SSDTTime.

Press 1 to select the Config.plist created in an earlier step, then drag and drop your Config.plist onto the window, and press enter.

Afterwards, press 2 to start the merging process.

The modified Config.plist with the patches merged in will appear in the Results folder.

Check that it’s okay, then replace your original Config.plist with the newly generated one.

# 	:toolbox: Kexts
- AMDRyzenCPUPowerManagement
- AppleALC
- AppleMCEReporterDisabler
- BlueToolFixup
- BrightnessKeys
- ECEnabler
- ForgedInvariant
- HoRNDIS
- Lilu
- NootedRed
- NullEthernet
- NVMeFix
- RestrictEvents
- SMCAMDProcessor
- SMCBatteryManager
- SMCLightSensor
- SMCRadeonSensors
- VirtualSMC
- VoodooI2C
- VoodooI2CHID
- VoodooPS2Controller

# :repeat: Supported macOS & OpenCore Versions

* macOS Catalina 10.15.x
* macOS Big Sur 11.x
* macOS Monterey 12.x
* macOS Ventura 13.x
* macOS Sonoma 14.x
* macOS Sequoia 15.x (Having problems currently)
* OpenCore r1.0.3

# :gear: BIOS Settings

1. Secure boot
   - Disabled
2. TPM Status
   - Disabled

# :white_check_mark: Working
- [x] AMD Integrated Graphics
- [x] Audio
- [x] Bluetooth
- [x] USB Port
- [x] USB-C Port
- [x] Battery Status
- [x] Night Shift
- [x] Hibernation
- [x] iCloud & App Store

# :x: Not Working
- [ ] WiFi (Incompatible card)
- [ ] Memoji
- [ ] Animated Wallpapers

# 	:sparkles: Boot GUI
Modern (GoldenGate)

![GUI](https://dortania.github.io/OpenCore-Post-Install/assets/img/gui-nouveau.8ad4a7b4.png)
Font: [Dortania](https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html#setting-up-opencore-s-gui) for GUI
