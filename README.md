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
