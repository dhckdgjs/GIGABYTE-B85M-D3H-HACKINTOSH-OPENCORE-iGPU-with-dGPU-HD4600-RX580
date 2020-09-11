# GIGABYTE-B85M-D3H-HACKINTOSH-OPENCORE-iGPU-with-dGPU-HD4600-RX580


## Components

- M/B: GIGABYTE GA-B85M-D3H
- CPU: Intel® Core™ i5-4690 Processor
- iGPU: Intel® HD Graphics 4600
- dGPU: SAPPHIRE NITRO AMD Radeon RX 580 4GB
- Lan: Realtek® GbE LAN 8111F
- WiFi/Bluetooth: Broadcom BCM94360CS2
- Audio: Realtek® ALC892 codec
- Bootloader: Opencore 0.6.0

## Comments

This Hackintosh build guide is NOT GUARANTEE 100% fully working in your conditions.

This guide has been tested on MacOS Catalina 10.15.6 and prefers the use of an AMD dGPU for ease of installation. This settings are considered using dGPU(RX580) and iGPU(HD 4600 with Quicksync) simultaneously in specifically the FCPX(10.14.9) and these dual GPUs can nearly full hardware accelerated.(a.k.a Headless setting)

There are no differences with WEG and without WEG in this settings.(I cannot sure but, in my workflow these are almost same)

And this guide can be used on the ASUS, MSI M/B with similar chipset also. (some settings different)

## Procedure

1. Change M/B Bios Primary display(ASUS) or Initial Display Output(Gigabyte) to PEG or PCIE(iGPU MUST be turn on) and apply other CMOS settings.
2. Apply this EFI.
3. Install MacOS 10.15.6 or newer(with Lilu.kext and Whatevergreen.kext )
4. Set the SMBIOS to iMac 14,2 with working SystemSerialNumber, SystemUUID and MLB in your config.plist(PlatformInfo → Generic)
( An idiot guide to iMessage - [https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/) )
5. Apply the Framebuffer patch(Headless) on your Devices setting in config.plist. (check settings as below but I recommend using the Hackintool)

```
AAPL,ig-platform-id: 04001204(BAASBA==)

device-id: 12040000(EgQAAA==)

Check some options(I don't think it's necessary):
	- General: DeviceProperties, Connectors, VRAM, Graphic Device
	- Advanced: Hotplug Reboot Fix(I’m not sure), Spoof Video Device ID, VRAM 2048 MB, GfxYTile Fix

```

Ref. Dortania's OpenCore Install Guide for Haswell (https://dortania.github.io/OpenCore-Install-Guide/config.plist/haswell.html)

Done

## Summary

### What Works

- Sleep/Wake works. Pressing the power button or single keypress wakes the system in one shot.
- Netflix HD playback in Safari(with shikigva=80, NOT yet 4K in Catalina Safari).
- Handoff, Continuity, AirDrop, Continuity Camera, Unlock with Apple Watch.
- iMessage, FaceTime, App Store, iTunes Store.
- Intel HD 4600 for both compute tasks and driving DP monitors.(Fully H.264 accelerated in FCPX)
- The macOS USB 15 port limit is already addressed.(add some internal ports with Hackintool if you need more USB 2.0 ports)

Thanks
