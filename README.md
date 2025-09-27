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
- **Ethernet**: Realtek PCIe GBE Family Controller ✅
- **Wi-Fi**: Intel Dual Band Wireless-AC 7260 ✅ (via OpenIntelWireless, BIOS whitelist requires this card)
- **Audio**: Conexant CX20751/20755 ✅
- **BIOS**: Secure Boot **Disabled** (recommended), CSM **Enabled** (works), Resizable BAR **Disabled**, Above 4G Decoding **Disabled**, AHCI **Enabled**
  ### Wi-Fi Notes

- The built-in **Intel Dual Band Wireless-AC 7260** is supported on macOS through the **OpenIntelWireless** project.  
- For ThinkPad E440, the **BIOS whitelist only accepts this Intel card** among factory options.  
- If your unit already has 7260, no change is needed.  
- If it ships with another card, you must replace it with Intel 7260 for compatibility.

