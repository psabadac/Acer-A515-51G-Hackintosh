

# Acer-A515-51G-51D3-Hackintosh

#### Tested with MacOS 10.15.6

<p align="center">
  <img src="https://i.imgur.com/OCJ0OE0.png" alt="Specs">
</p>


## What's Working...
 - [x] Audio & headphone jack
 - [x] CPU Speedstep (XCPM)
 - [x] iGPU with disabled dGPU
 - [x] Fully Functional QE/CI Enabled Graphics
 - [x] Battery Management
 - [x] ACPI Display brightness with hot keys / slider
 - [x] Ethernet
 - [x] Internal SD card Reader
 - [x] HDMI + Audio
 - [x] Sleep + Wake
 - [x] Smart Touchpad + Gestures (using I2C)
 - [x] WebCam
 - [x] Usb 3.0 + Type C
 - [x] Sleep From Lid
 - [x] WiFi by using HeliPort and itlwm.kext
 - [x] Native hotkey support with Fn keys

<p align="center">
  <img src="https://i.imgur.com/A0cKRrX.png" alt="Benchmarks">
</p>

  - Geekbench Score :
  - - Single-Core Score : 4219 [Link](https://browser.geekbench.com/v4/cpu/13793813).
  - - Multi-Core Score : 14837 [Link](https://browser.geekbench.com/v4/cpu/13793813).
  - - GPU OpenCL Score : 31191 [Link](https://browser.geekbench.com/v4/compute/4258348).

## Installation

###  Basic Installation

- Create a Bootable USB for MacOS by using [USB Installation Guide](https://www.tonymacx86.com/threads/unibeast-install-macos-catalina-on-any-supported-intel-based-pc.285366/) using Unibeast & UEFI
- Copy **ALL** the Contains of this Repo into **CLOVER** Folder inside the EFI partition of USB

### Post Installation

- Install Multibeast for UEFI
- - Copy **ALL** the Contains of this Repo into **CLOVER** Folder inside the EFI partition of Hard Drive where you installed the OS
---
### Laptop configuration


- **Audio** : The Sound Card is `Realtek ALC255`, which is driven by `AppleALC` on `layout-id 3`.

- **CPU** : The CPU model is `i5-8250U` and XCPM power management is natively supported.
 - - XCPM and HWP are recommended to work together to reach better power management, by injecting `plugin-type=1` with `SSDT-XCPM`, and using `CPUFriend.kext`.

- **Graphics** : The iGPU is `Intel UHD Graphics 620`, and its enabled using `Ig-Platform-id=0x191E0000`.
- - The discrete dGPU is `NVIDIA GeForce MX150`, and it is disabled because macOS doesn't support optimus technology. Plus battery life is much improved.
- - The colour branding or corrupted colour depth is fixed with Intel Skylake spoof and EDID fix.
- - Native brightness hotkey support using `DSDT.aml`.

- **Battery** : Battery Management using `SMCBatteryManager.kext`.

- **Backlight** : Native Brightness control using `SSDT-PNLF.aml`.

- **Ethernet** : Gigabit Ethernet using `RealtekRTL8111.kext`.

- **HDMI** : Intel Framebuffer patches to change the connector-type to match the physical connector, using `WhateverGreen.kext`.
- - **HDMI Audio** : Injecting property `"hda-gfx" = "onboard-1"` on HDAU, IGPU, HDEF objects & also injecting `layout-id 3` on HDAU to match layout-id on HDEF.

- **Touchpad** : Native I2C touchpad support using `VoodooI2C.kext`; Set touchpad Mode to `Advance` from `BIOS` & All gestures will work fine.

- **USB** : Custom `SSDT-UIAC.aml` SSDT for `USBInjectAll.kext` that configures USB ports on XHC such that the port limit patch is not needed, and each UsbConnnector value is correct for each port.
- - You can also find USB port mapping for `SSDT-UIAC` [Here](https://github.com/SiddheshNan/Acer-A515-51G-Hackintosh/blob/master/USB%20port%20mapping%20for%20SSDT-UIAC.md).

- **Wi-Fi** : Stock WiFi Card is `Intel Wireless AC 3168` 
- - It supported using **OpenIntelWireless** with [heliport](https://github.com/OpenIntelWireless/HeliPort) and [itlwm](https://github.com/OpenIntelWireless/itlwm)

- **Bluetooth** : Stock `Intel Wireless AC 3168` BT will work out-of-the box.
- **SD Card Reader** : Internal SD Card Support using Modified Sinetek's rtsx Driver.

## Credits

- **Special Thanks** to [Acidanthera](https://github.com/acidanthera) for most of the Kexts.
- **Special Thanks** to [RehabMan](https://github.com/RehabMan).
- Thanks to [Clover Bootloader](https://sourceforge.net/projects/cloverefiboot).
- Thanks to [goodwin](https://github.com/goodwin/) for [ALCPlugfix](https://github.com/goodwin/ALCPlugFix).
- Thanks to [alexandred](https://github.com/alexandred/) for [VoodooI2C](https://github.com/alexandred/VoodooI2C).
- Thanks to [Sinetek](https://github.com/sinetek) for [Sinetek-rtsx](https://github.com/sinetek/Sinetek-rtsx).
- Thanks to [al3xtjames](https://github.com/al3xtjames) for [NoTouchID](https://github.com/al3xtjames/NoTouchID).
- Thanks to [daliansky](https://github.com/daliansky/) for Some Patches which I used here from [XiaoMi-Pro](https://github.com/daliansky/XiaoMi-Pro/).
- Thanks to [OpenIntelWireess](https://github.com/OpenIntelWireless) working on wireless patches
