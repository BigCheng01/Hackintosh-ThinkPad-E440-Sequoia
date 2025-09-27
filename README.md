# Hackintosh-ThinkPad-E440-Sequoia
OpenCore (Version 1.0.5) EFI for Lenovo ThinkPad E440, tested on macOS Sequoia 15.7.  This repository provides a working EFI configuration for Hackintosh users.
## Hardware Specs

- **Model**: Lenovo ThinkPad E440 (20C5006UTW) — HM87 chipset
- **CPU**: Intel Core i7-4702MQ (Haswell, 4C/8T)
- **iGPU**: Intel HD Graphics 4600 ✅ (used in macOS)
- **dGPU**: NVIDIA GeForce 740M (Kepler GK208) ❌ disabled in macOS
- **Memory**: 8 GB DDR3 1600 (2×4 GB, Hynix)
- **Storage**:
  - NT-512 512 GB SSD (SATA)
  - Samsung 870 EVO 2 TB (SATA)
- **Ethernet**: Realtek PCIe GBE Family Controller ✅ (via `RealtekRTL8111.kext`)
- **Wi-Fi**: **Intel Dual Band Wireless-AC 7260** ✅ (supported via OpenIntelWireless)
- **Audio**: Conexant CX20751/20755 ✅ (via AppleALC)
- **BIOS**: Secure Boot **Disabled** (recommended), CSM **Enabled** (works), Resizable BAR **Disabled**, Above 4G Decoding **Disabled**, AHCI **Enabled**
 ### Wi-Fi (Intel 7260) Notes
- The **Intel Dual Band Wireless-AC 7260** works on macOS via the [**OpenIntelWireless** project](https://github.com/OpenIntelWireless).
- On the E440, Lenovo's **BIOS whitelist** effectively allows only this Intel card among the factory options.  
  If your unit already has **AC 7260**, **no hardware change is needed**.  
  If it ships with a different WLAN module, you **must replace it with Intel AC 7260** to pass the whitelist and work in macOS.
## OCLP-Mod Support Requirement
In addition to using this EFI, to fully enable **integrated graphics**, **Wi-Fi**, and **Bluetooth**, you must run **OCLP-Mod** (a modified version of OpenCore Legacy Patcher).  
Project link: [laobamac/OCLP-Mod](https://github.com/laobamac/OCLP-Mod)
## Tested macOS Versions
- ✅ macOS Sequoia 15.7 — fully tested and confirmed working with this EFI  
- 🟡 macOS Sequoia (any 15.x within same major version) — theoretically supported  
- ❌ Other major macOS versions (e.g. macOS 14 Sonoma, macOS 26 Tahoe) — **not supported** due to GPU and Wi-Fi driver incompatibility  
## What Works ✅
- Display output (integrated GPU)  
- Internal speaker & microphone  
- Bluetooth audio (via Bluetooth)  
- Wireless (Intel AC 7260)  
- Bluetooth functionality (basic)  
- USB ports  
- Built-in camera  
- Sleep & Wake  
## Partial / Untested ⚠️
- Internal optical drive — identified by system, but **not tested**  
- HDMI output — **no testing conditions available**  
- AirDrop, Sidecar, Continuity features — **very likely unsupported**  
- 3.5 mm headphone jack — **not tested**
- Power management - **Partial supported**
## What Doesn’t Work ❌
- Brightness adjustment  
- Discrete GPU (dGPU)  
- SD card reader
## Usage Instructions
1. Download or clone this repository, and copy the **EFI** folder to the EFI partition of your macOS installer USB (or internal drive).  
2. Boot into macOS installer using OpenCore.  
3. Install macOS Sequoia as usual.  
4. After installation and first boot, run **OCLP‑Mod** to apply post‑install patches.  
   - This step unlocks full functionality for iGPU, Wi-Fi, and Bluetooth beyond what the EFI provides alone.  
5. Reboot, and you should have a working system with all supported features active.
## Important Notes
1. **Hardware / BIOS Preparation**  
   Before installing, make sure the **Intel AC 7260 Wi-Fi card** is correctly installed (or, for other models, a compatible Intel card supported by OpenIntelWireless). Also ensure all BIOS settings are configured properly (Secure Boot disabled, AHCI mode, etc.).

2. **config.plist Customization**  
   If your hardware differs or you have special needs, you may edit `config.plist` with a suitable editor. This EFI is built for **OpenCore version 1.0.5**.

3. **OCLP‑Mod Requires Network**  
   OCLP‑Mod needs internet to fetch patches, but at this stage Wi-Fi and Bluetooth may not work. Use a wired connection or a USB-connected cellular hotspot. Expected data usage: ~200 MB or more.

4. **Platform (SMBIOS) Configuration Warning**  
   For security, the provided `config.plist` does **not** include a full machine‑specific platform setup (i.e. no “three codes” / serials). You need to configure them yourself using the appropriate editor—but **ensure you set the platform to MacBookPro16,1**, otherwise USBMap.kext and internal devices may malfunction.

5. **Boot Arguments / Verbose Mode**  
   This EFI preserves `-v` in `boot-args`, so macOS boots in verbose (debug) mode by default. If you don’t need that, you can remove `-v`—but **do not remove the entire `boot-args` entry**, only the `-v` flag.
## Acknowledgements
- [Acidanthera](https://github.com/acidanthera) — for **OpenCorePkg** and a suite of kexts, drivers, tools that underpin the Hackintosh ecosystem.  
- [Dortania](https://github.com/dortania) — for their detailed OpenCore installation guides, troubleshooting docs, and community support.  
- [OpenIntelWireless / itlwm](https://github.com/OpenIntelWireless/itlwm) — for enabling Intel wireless support on macOS via **itlwm.kext** and related tools. 
- [zxystd](https://github.com/zxystd) — principal developer behind itlwm and IntelBluetoothFirmware, whose work makes Intel Wi-Fi/Bluetooth on macOS possible.
- [laobamac / OCLP-Mod](https://github.com/laobamac/OCLP-Mod) — for the patched version of OpenCore Legacy Patcher used to unlock full GPU, Wi-Fi, Bluetooth support beyond EFI.  
- All contributors, testers, and community members whose shared knowledge, issues, and code made this project feasible.
