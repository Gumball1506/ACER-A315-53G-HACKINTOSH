# Acer A315-53G-5790
![Hackintosh Cover](https://tmp.phongvu.vn/wp-content/uploads/2019/03/Laptop-Acer-Aspire-A3-A315-53-30E7-NX.H2BSV.003-1-e1552533691136.jpg)

## Changelogs
```
  - Update to 10.14.6
  - Update kext to latest
  - Usb port limit patch
  - Fix Trackpad
  - Fix Brightness 
  - Change from FakeSMC to VirtualSMC 
```

## Specification
```
- Name: Acer A315-53G
- Processor: Intel Core i5-8250U ( 1.6 GHz - 3.4 GHz / 6MB / 4 nhân, 8 luồng )
- Wifi: Qualcomm Atheros QCA9377 Wireless
- Audio: Realtek ALC255
- Graphics: 
  * IGP: Intel UHD Graphics 620
  * Discrete: NVIDIA GeForce MX130 2GB GDDR5
- Display: 15.6" ( 1366 x 768 ) 
- Storage:
  * HDD: 500GB HDD 5400RPM 
  * SSD: Western Digital Green 120GB M.2 2280 SATA 3
- Dual Boot:
  * Windows 10 Pro
  * MacOS Mojave
```

## Known not work
```
1. Discrete Graphics: GeForce MX130 2 GB GDDR5 (Disabled - MacOS not supported optimus)
2. Built-in Wifi (Must be replaced)
```

## How to fix trackpad

https://www.reddit.com/r/hackintosh/comments/cs2pa2/catalina_update_problem/

https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/

For DSDT.dsl, wait for the file to load completely
1. Search and Replace all "GFX0" for "IGPU"
2. Search and Replace all "HDAS" for "HDEF"
3. Apply VoodooI2C GPIO Patch and Windows 10 Patch
4. Find your touchpad device (mine was TPL1), scroll to _INI section and replace 

```
If (LEqual (SDM1, Zero))
                {
                    SHPO (GPLI, One)
                }

```

to 

```
SHPO (GPLI, One)
```
5. Compile and if no errors, save the file as AML file
6. Copy edited file to EFI/CLOVER/ACPI/patched

* Copy ONLY EDITED (don't copy if you didn't replace anything)

Source: https://www.tonymacx86.com/threads/guide-acer-swift-3-i5-8250u-high-sierra.249160/
