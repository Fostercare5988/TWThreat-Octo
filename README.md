# TWThreat

[![Version](https://img.shields.io/badge/Version-1.2.0-blue.svg)](https://github.com/Fostercare5988/TWThreat/releases)
[![Interface](https://img.shields.io/badge/Interface-1.12.1%20(Build%205875)-orange.svg)](https://github.com/Fostercare5988/TWThreat)
[![Engine](https://img.shields.io/badge/Engine-ClassicAPI%20%7C%20SuperWoW%20%7C%20NamPower%20%7C%20UnitXP%20%7C%20DXVK-green.svg)](https://github.com/Fostercare5988/TWThreat)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/Fostercare5988/TWThreat)

A high-performance, real-time threat meter engineered natively for **World of Warcraft 1.12.1** on the **Enhanced Client Extension Stack** (**ClassicAPI**, **SuperWoW 2.2+**, **NamPower 4.6.2+**, **UnitXP SP3**, and **DXVK**) created and maintained by **Fostercare5988**.

TWThreat provides instantaneous server-authoritative threat tracking, eliminates combat garbage collection stutter, delivers 144Hz/240Hz+ smooth bar animations, and provides direct SuperWoW GUID targeting.

---

## ⚡ Quick Start & Slash Commands

You can use `/twt` or `/twtshow`:

* `/twt` or `/twt show` — Shows / hides the main threat window.
* `/twtshow` — Toggles visibility of the threat window.
* `/twt tankmode` — Toggles the Tank Mode companion window.
* `/twt who` — Inspects addon versions across party and raid members.
* `/twt debug` — Toggles debug traffic monitor.

### Key Shortcuts & Interactions:
* **Settings**: Click the **Gear Icon** at the top right of the threat window to configure bar height, scale, font, alpha, columns, and thresholds.
* **Lock Window**: Click the **Padlock Icon** to lock or unlock frame movement.
* **Tank Mode Target Lock**: In Tank Mode, click any creature bar to lock target via **SuperWoW direct GUID targeting** (`TargetUnit(guid)`).

---

## ✨ Core Features

* **Server-Authoritative Threat Tracking**: Direct integration with the server-side threat protocol (`TWT_UDTSv4` / `TWTv4=`), providing 100% accurate threat values without legacy KTM combat log desync.
* **Target Frame Threat Integration**:
  * **Threat Glow**: Visual threat border aura on your target frame (Green -> Yellow -> Red).
  * **Numeric Percentage Badge**: Real-time numerical threat percentage displayed directly on the target frame.
* **Threat Alerts & Warnings**:
  * **Full Screen Glow**: Fullscreen vignette pulse when nearing or exceeding threat threshold.
  * **Audio Warnings**: Configurable audio alarm when reaching critical aggro transition percentages.
* **Multi-Target Tank Mode**: Companion HUD displaying real-time threat status across all active tanked mobs, with direct GUID targeting.
* **Deep Customization**: Selectable fonts, bar heights, custom TPS / Threat / Percent columns, OOC transparency, and combat auto-show/hide.

---

## 💻 Technical Architecture & Zero-Bloat Optimizations

* **Strict Engine Dependency Guard**: Declares an active runtime check for `CLASSIC_API_VERSION` and `SUPERWOW_VERSION` at initialization, preventing silent failures.
* **Zero Combat GC Churn**: Eradicated all dynamic table allocations during combat. Uses pre-allocated recycling pools (`threatPool`, `tankModePool`, `sortList`) and single-pass string parsing, eliminating frame drops in 40-man raids.
* **Delta-Time Decoupled 144Hz+ Smoothing**: Bar animations and glow transitions use normalized delta-time (`dt`) exponential smoothing, guaranteeing stutter-free rendering at 60Hz, 144Hz, and 240Hz+ under DXVK and Vulkan.
* **SuperWoW Direct GUID Targeting**: Tank Mode utilizes SuperWoW's `TargetUnit(guid)` API for instant, 100% reliable targeting of specific mobs in multi-mob packs without fuzzy targeting errors.
* **Zero pfUI Bloat & Clean XML**: Completely eliminated legacy pfUI dependencies, unresolved frame anchors (`pfTarget`), and dead texture assets, resulting in clean `FrameXML.log` output.
* **No Network Spam**: Removed all automated update spam and broadcast prompts across raid and guild channels.

---

## 📦 Installation & Requirements

1. **Requirements**:
   - **World of Warcraft 1.12.1** (Build 5875).
   - [**ClassicAPI**](https://github.com/brues-code/ClassicAPI) (`ClassicAPI.dll`).
   - [**SuperWoW**](https://github.com/balakethelock/SuperWoW) (`SuperWoW.dll` v2.2+).
   - [**NamPower**](https://github.com/Emyrk/nampower) (`nampower.dll` v4.6.2+).
   - [**UnitXP SP3**](https://codeberg.org/konaka/UnitXP_SP3) (`UnitXP_SP3.dll`).
   - [**DXVK**](https://github.com/doitsujin/dxvk) & [**VanillaFixes**](https://github.com/hannesmann/vanillafixes).
2. **Installation**:
   - Place the `TWThreat` folder into:
     ```text
     World of Warcraft/Interface/AddOns/TWThreat/
     ```
   - Ensure `TWThreat.toc` is directly inside `Interface/AddOns/TWThreat/`.
   - Enable **TWThreat** in your AddOn list at character selection.

---

## 👥 Credits & Attribution

* **Xerron / Er / CosminPOP** — Original author of TWThreat.
* **Fostercare5988** — Modernization, Enhanced 1.12.1 Engine Stack refactoring, Zero-GC recycling pools, FrameXML fixes, and repository maintenance.

---

## 📜 Changelog

### v1.2.0
* Upgraded startup dependency guard to inspect `CLASSIC_API_VERSION` and `SUPERWOW_VERSION` globals directly.
* Normalized TOC metadata and title to clean standard naming (`TWThreat`).
* Updated documentation with DXVK engine badge and direct repository hyperlinks for all DLL prerequisites.

### v1.1.0
* Verified zero-GC threat recycling pools and delta-time animation smoothing.
* Updated TOC metadata and published comprehensive technical README documentation.

### v1.0.0
* Initial release of the streamlined single-folder edition.
* Complete removal of pfUI bloat and broken frame references.
* SuperWoW direct GUID targeting integration in Tank Mode.
* Zero-GC combat parsing and 144Hz+ DXVK smoothing.
