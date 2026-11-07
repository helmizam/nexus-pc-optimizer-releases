# NEXUS PC OPTIMIZER

Free, safety-first maintenance utility for Windows 10 and Windows 11 (x64): software updates (WinGet), uninstaller,
RAM monitor, storage cleaner, SSD TRIM / HDD optimisation, startup manager, Smart Shutdown, system health,
scheduler and activity logs. Bahasa Melayu (default) and English.

This repository distributes **official releases only**. It contains no source code.

## Download

Get the latest installer from **[Releases](../../releases/latest)**: `NexusPCOptimizer-<version>-setup.exe`.

Requirements: Windows 10 22H2 / Enterprise LTSC 2021 or Windows 11, x64, with Microsoft .NET Framework 4.8.1
(see [COMPATIBILITY.md](COMPATIBILITY.md)).

## Verify your download

Every release includes `SHA256SUMS.txt`, `manifest.json` and its signature `manifest.json.sig`.

```powershell
Get-FileHash .\NexusPCOptimizer-1.2.0-setup.exe -Algorithm SHA256
```

The hash must equal the value in `SHA256SUMS.txt` and in `manifest.json`. NEXUS's built-in updater verifies the
manifest's ECDSA P-256 signature with a key compiled into the application and checks the SHA-256 automatically;
an update that fails either check is discarded. The public release key is listed in [KEYS.md](KEYS.md).

## Privacy

Registration is optional and free; all maintenance features work without it. No hidden telemetry. Optional
diagnostics are off by default. Full details: [PRIVACY.md](PRIVACY.md).

## Support (voluntary)

NEXUS PC OPTIMIZER is freeware. If you find it useful you can make a voluntary contribution (from RM1) via the
DuitNow QR code on the app's **About & Support** page. It is entirely optional: every feature stays free, nothing is
tracked, and there are no reminders or pop-ups. Terms: [TERMS_OF_USE.md](TERMS_OF_USE.md).

## Version history

See [versions.json](versions.json) and the [Releases](../../releases) page.

## Reporting security issues

See [SECURITY.md](SECURITY.md).

---

Developed & Maintained by **CHOKS**, Independent Software Developer. Copyright © 2026 CHOKS.
