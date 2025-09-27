# Hackintosh-ThinkPad-E440-Sequoia
OpenCore EFI for Lenovo ThinkPad E440, tested on macOS Sequoia 15.7.  This repository provides a working EFI configuration for Hackintosh users.
## Hardware Specs

- **Model**: Lenovo ThinkPad E440 (20C5006UTW) — HM87 chipset
- **CPU**: Intel Core i5-4210M (Haswell, 2C/4T)
- **iGPU**: Intel HD Graphics 4600 ✅ (used in macOS)
- **dGPU**: NVIDIA GeForce 740M (Kepler GK208) ❌ disabled in macOS
- **Memory**: 8 GB DDR3 1600 (2×4 GB, Hynix)
- **Storage**:
  - NT-512 512 GB SSD (SATA)
  - Samsung 870 EVO 2 TB (SATA)
  - Lenovo SXI 64 GB (USB)
- **Ethernet**: Realtek PCIe GBE Family Controller ✅ (via `RealtekRTL8111.kext`)
- **Wi-Fi**: **Intel Dual Band Wireless-AC 7260** ✅ (supported via OpenIntelWireless)
- **Audio**: Conexant CX20751/20755 ✅ (via AppleALC)
- **BIOS**: Secure Boot **Disabled** (recommended), CSM **Enabled** (works), Resizable BAR **Disabled**, Above 4G Decoding **Disabled**, AHCI **Enabled**
 ### Wi-Fi (Intel 7260) Notes
- The **Intel Dual Band Wireless-AC 7260** works on macOS via the **OpenIntelWireless** project  
  (use **AirportItlwm.kext** for native Wi-Fi menu integration on macOS 15.x, or **itlwm.kext** + HeliPort).
- On the E440, Lenovo's **BIOS whitelist** effectively allows only this Intel card among the factory options.  
  If your unit already has **7260**, **no hardware change is needed**.  
  If it ships with a different WLAN module, you **must replace it with Intel 7260** to pass the whitelist and work in macOS.

