# OpenCore
OpenCore 1.0.4

# Adapted For
ASUS NUC 13 Pro (Arena Canyon)

# OS Version Being Tested
macOS Sequoia 15.x (Wi-Fi may require OCLP-mod by @laobamac for newer Intel cards)

# BIOS Configuration
⚠️ Use BIOS version with Thunderbolt enabled and CFG Lock unlocked.

How to update and configure BIOS:
1. Ensure **Thunderbolt Security is Disabled** and **PCIe tunneling is Enabled**.
2. Enable `Above 4G Decoding`.
3. Set CFG Lock to **0 (Unlocked)** using CFGLock.efi if needed before updating to latest BIOS.
4. Recommended BIOS version: **0061** (confirmed CFG unlocked if previously set in earlier versions).
5. Set Primary Display to iGPU (for macOS to boot) if using eGPU for output.

## Advanced BIOS Settings

### Storage
- SATA Mode Selection: **AHCI**

### Video
- IGD Minimum Memory: **64MB**
- IGD Aperture Size: **512MB**
- IGD Primary Video Port: **Thunderbolt or HDMI** (depending on connected monitor)
- IGD Secondary Video Port: **None**

### Boot
- Secure Boot: **Disabled**
- UEFI Boot: ✅ Enabled
- Legacy Boot: ❌ Disabled
- Fast Boot: ❌ Disabled

### Power
- Deep S4/S5: ✅ On
- Wake on LAN from S4/S5: **Power On - Normal Boot**
- Wake System from S5: ❌ Off
- Wake from Thunderbolt Device: ❌ Off

> All other settings can remain default unless stated otherwise.

## CFG Unlock (Optional if locked in BIOS)
If installing macOS for the first time and CFG is locked:
- Format USB as FAT32
- Copy `CFGLock.efi` to `/EFI/BOOT/`
- Boot into USB via F10 and select `CFGLock Shell.efi`
- Set CFG Lock to `0`

---

# Known Issues
- Thunderbolt 4 device (OneXGPU) currently **does not support hotplug**.
- Continuity features may not fully work (Handoff & Universal Clipboard are confirmed working).
- AirDrop, Universal Control may not function due to unsupported Wi-Fi/Bluetooth stack.

---

## Screenshots
- macOS Sequoia 15.x Desktop
- Thunderbolt & eGPU recognized in System Info
- Geekbench 6 (Metal) showing RX 7600MXT performance

---

## Kexts Used
- `Lilu.kext`
- `WhateverGreen.kext`
- `VirtualSMC.kext`
- `SMCProcessor.kext`
- `SMCSuperIO.kext`
- `AppleALC.kext`
- `IntelMausi.kext`
- `AirportItlwm.kext` (for Wi-Fi, Sequoia patched)
- `BlueToolFixup.kext`
- `IntelBluetoothFirmware.kext`
- `IntelBluetoothInjector.kext`
- `IntelBTPatcher.kext`
- `FakePCIID.kext`
- `FakePCIID_AMD_GFX.kext`

---

## Tools Recommended
- Hackintool
- OpenCore Configurator (OCC)
- OCAuxiliaryTools (OCAT)
- ProperTree
- GenSMBIOS (generate serials for iMac19,1)
- MountEFI / EFI Agent
- gibMacOS (create install media)

---

## ACPI Patches
- `SSDT-TB3-NUC13.aml`: Custom SSDT for Thunderbolt 4 routing (required for OneXGPU eGPU support)

---

## Drive Setup
- macOS Sequoia installed on NVMe SSD transplanted from NUC10
- EFI partition uses OpenCore 1.0.4, iMac19,1 SMBIOS

---

## EFI Theme
- `BsxM1` used for OpenCore UI

---

## Credits
- Used the https://github.com/hackintosh-club/intel-nuc10 EFI as a baseline so most of the credit goes to those developers
- Built and refined by [Farooq Ali] aka mac_assassin @ https://github.com/apollohackintosh

---

## Status
✅ Boots macOS Sequoia 15.x  
✅ Thunderbolt 4 recognized  
✅ eGPU (RX 7600MXT in OneXGPU) functioning  
🔧 USB mapping and Thunderbolt SSDTs refined for Arena Canyon
