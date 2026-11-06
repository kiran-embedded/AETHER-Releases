# AETHER Kernel Releases

Official pre-compiled flashable release packages and companion tools for **Xiaomi Redmi Note 10** (`mojito` / `sunny`) running **Android 16 and Android 17**.

---

## 📱 Device Specifications & Target
* **Device**: Xiaomi Redmi Note 10 (`mojito` / `sunny`)
* **SoC**: Qualcomm Snapdragon 678 (SM6150)
* **Kernel Version**: Linux 4.14.357-AETHER-CORE
* **Compiler**: Clang 18 + ThinLTO + Performance Optimizations (-O2)
* **Android Compatibility**: Android 16 (A16) & Android 17 (A17)

---

## ⚡ Key Architectural Features

### 1. CPU & Memory Subsystem
* **BORE CPU Scheduler**: Burst-Oriented Response Enhancer (v5.1.0) paired with Energy-Aware Scheduling (EAS) to eliminate interactive UI frame drops during background multi-tasking.
* **MGLRU (Multi-Gen LRU)**: High-performance generational page reclamation backport (sysfs enabled at `0x0003`) yielding up to 40% less CPU utilization under severe memory pressure.
* **High-Efficiency ZRAM**: 3 GB ZRAM pool utilizing the LZ4 compression algorithm (~3.15x compression ratio).

### 2. Hardware Drivers & Battery Protection
* **Hardware Bypass Charging**: True PMIC power-path isolation using Qualcomm PM6150 / SMB5 NVDC votables. Powers motherboard system rails directly from the charger with 0 mA battery draw during gaming sessions.
* **180 Hz Touch Digitizer**: FocalTech FT3418 active register tuning configured for 5.5 ms scan period (~180 Hz sampling rate) for lower touch input latency.
* **Hi-Fi Class-H Audio**: Qualcomm WCD937x codec enhancements with direct headphone gain staging sysfs controls.

### 3. Security & Root Cloaking
* **USB Data Shield**: In-kernel controller-level protection (`/proc/sys/kernel/deny_new_usb`) that pulls down the D+ pullup resistor in the Qualcomm DWC3 PHY, blocking untrusted data transfers while allowing full charging power.
* **KernelSU & SuSFS v2.3.0**: Native in-kernel stealth filesystem cloaking to pass strict safety and banking application integrity checks.
* **Re-Kernel v11.7**: Integrated Binder transaction protection, signal shielding, and Netfilter firewall mitigation against port scans.

---

## 📦 Package Overview

| Package Name | Purpose | How to Install |
| :--- | :--- | :--- |
| **`AETHER-Kernel-mojito-v*.zip`** | Main Kernel Boot Image (AnyKernel3) | Flash in Recovery (TWRP / OrangeFox) |
| **`AETHER-Kernel-Control-WebUI-v*.zip`** | WebUI Control Dashboard + APK Service | Flash in KernelSU / Magisk Manager |
| **`AETHER-SuSFS-Stock-Spoofer-v*.zip`** | Root & Mount Cloaking Module | Flash in KernelSU / Magisk Manager |

---

## 🚀 Installation Instructions

### First Time Installation (Clean Flash Recommended):
1. Download the latest **`AETHER-Kernel-mojito-v*.zip`** from [Releases](https://github.com/kiran-embedded/AETHER-Releases/releases).
2. Reboot into custom recovery (**TWRP** or **OrangeFox**).
3. *(Optional but recommended)*: Take a backup of your existing `boot` and `dtbo` partitions.
4. Flash `AETHER-Kernel-mojito-v*.zip`.
5. *(Optional for Root Cloaking)*: Flash `AETHER-SuSFS-Stock-Spoofer-v2.3.0.zip`.
6. Reboot to system.
7. *(Optional for In-Tree WebUI)*: Open KernelSU or Magisk and install `AETHER-Kernel-Control-WebUI-v*.zip`. Access the dashboard at `http://localhost:8080` in any web browser.

---

## 🤝 Credits & Acknowledgements
* **Lead Developer**: Kiran Embedded (`@kiran-embedded`)
* **Contributors & Testers**: `@Whiteduck07`, `@ham1do`, `@saxo06`
* Upstream Linux Kernel & Android Open Source Project (AOSP) communities.
