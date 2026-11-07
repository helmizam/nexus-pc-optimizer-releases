# Compatibility matrix

NEXUS PC OPTIMIZER 1.1 targets **.NET Framework 4.8.1** (WPF). This was chosen over .NET 10 for the desktop app
because Microsoft's .NET 10 support matrix covers Windows 10 only in its Enterprise/LTSC editions, while .NET
Framework 4.8.1 is a Windows component supported on Windows 10 22H2 Home/Pro, Enterprise/LTSC 2021 and Windows 11.
The backend (Railway) stays on ASP.NET Core / .NET 10.

| Operating system (x64) | Build | Installs & runs | .NET Framework 4.8.1 | Microsoft security support for the OS* |
|---|---|---|---|---|
| Windows 11 24H2 / 25H2 / later | 26100+ | ✅ Yes | Built in | ✅ Supported |
| Windows 11 23H2 | 22631 | ✅ Yes | Built in | Check Microsoft lifecycle (Home/Pro 23H2 ended Nov 2025) |
| Windows 10 22H2 Home / Pro | 19045 | ✅ Yes | Via Windows Update / offline installer | ⚠️ **Ended 14 Oct 2025.** Consumer ESU ended Oct 2026. |
| Windows 10 22H2 Enterprise / Education | 19045 | ✅ Yes | Via Windows Update | ⚠️ Only with a paid Extended Security Updates subscription |
| Windows 10 Enterprise LTSC 2021 | 19044 | ✅ Yes | Via Windows Update | ✅ Until Jan 2027 (IoT LTSC 2021: Jan 2032) |
| Windows 10 Enterprise LTSC 2019 and older | ≤ 17763 | ❌ Blocked by installer | — | — |
| Windows 10 32-bit, ARM64 | — | ❌ Not supported (x64 build only) | — | — |

\* NEXUS **running** on an OS is not the same as that OS being **secure**. NEXUS never claims that Windows 10
Home/Pro is security-supported by Microsoft; the installer and documentation state this plainly. Dates follow
Microsoft's published lifecycle and should be re-checked at https://learn.microsoft.com/lifecycle.

## Feature notes per OS

| Feature | Windows 11 | Windows 10 22H2 / LTSC 2021 |
|---|---|---|
| All maintenance modules | ✅ | ✅ (same Windows APIs: WMI Storage, Optimize-Volume, Task Scheduler, StartupApproved) |
| WinGet updater | ✅ (App Installer built in) | ✅ if *App Installer* is installed from the Microsoft Store (LTSC: install manually) |
| Delivery Optimization cleanup | ✅ | ✅ (1903+) |
| Icons | Segoe Fluent Icons | Falls back to Segoe MDL2 Assets — a few glyphs may look slightly different |
| Rounded window corners / Mica | ✅ | Square corners (ignored silently) |
| Dark title bar | ✅ | ✅ (20H1+) |

## Verification status

| Check | Status |
|---|---|
| Build & all automated tests on Windows 11 (build 26300, x64) | ✅ Done (233 tests) |
| Installer: install, run all 14 pages from `C:\Program Files`, uninstall | ✅ Done on Windows 11 |
| Installer blocks unsupported Windows versions / missing .NET 4.8.1 | ✅ Implemented (MinVersion 10.0.19044, registry Release ≥ 533320) |
| Hands-on run on a physical/virtual Windows 10 22H2 Home/Pro machine | ⏳ **Not yet performed** — no Windows 10 machine was available. Use the checklist below before announcing Windows 10 support. |

### Windows 10 acceptance checklist
1. Fresh Windows 10 22H2 Home VM, fully updated, .NET Framework 4.8.1 installed (`Release` ≥ 533320).
2. Run the installer; confirm it installs and the app starts in Bahasa Melayu, dark theme.
3. `NexusPCOptimizer.exe --ui-selftest C:\temp\ui` → `selftest.log` all `OK`.
4. Storage Cleaner scan, Disk detection (SSD/HDD correct), RAM, Startup list, Health page show real data.
5. Account: register → e-mail → activate; Notification Centre shows announcements; Settings → Check for updates.
6. Uninstall from Settings > Apps; confirm scheduled tasks removed.
