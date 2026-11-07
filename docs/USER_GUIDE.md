# User Guide

The interface is in **Bahasa Melayu** by default. Switch to English in **Tetapan (Settings) → Bahasa**.
Names below are given as *Malay (English)*.

## The operation bar (global STOP / CANCEL)

Every long operation appears in the bar at the bottom of the window:

- **Current action** and live status line
- **Progress %** when measurable (an animated bar when the duration is unknown)
- **HENTI / BATAL (STOP / CANCEL)** — stops the operation at the next safe point
- When finished: success / warning / failure icon, a **Butiran (Details)** button with the full error text, and a
  **Cadangan (Recommended)** next step

Only one operation runs at a time, so maintenance tasks never conflict.

## 1. Papan Pemuka (Dashboard)

Live CPU and RAM gauges with 60-second charts, total / available RAM, per-drive storage use and free space,
installed-application count, available software updates (from the last scan), last maintenance date and
Windows uptime. The **overall status** badge lists the exact reasons (low disk space, high RAM, pending updates,
no recent maintenance, Windows restart pending). Quick buttons open Smart Shutdown, the Storage Cleaner or run an
update check.

## 2. Pengemas Kini Perisian (Software Updater)

1. Click **Imbas kemas kini (Scan for updates)**. WinGet lists apps with newer versions: name, ID, current and available versions, source.
2. Untick apps you do not want, or tick **Kecuali (Exclude)** to keep them out of bulk/scheduled updates permanently (manage the list in Settings).
3. Click **Kemas kini (Update)** on a row, **Kemas kini dipilih (Update selected)** or **Kemas kini semua (Update all)**. A preview dialog lists every change; bulk updates also require you to confirm you saved your work.
4. Progress and the final status are shown per row. Failures explain the reason (app running, hash mismatch, reboot required…).

- **Mod interaktif (Interactive mode)** shows each installer's own UI — use it for apps that need choices during installation.
- *Disemat (Pinned)* packages and packages that *require explicit targeting* are shown but not updated.
- Packages whose installed version Windows cannot determine are not included (WinGet `--include-unknown` is never used).
- **Aplikasi yang tidak boleh dikemas kini melalui WinGet** lists installed apps WinGet does not manage — update those with their own updater.
- The **Windows Update** card shows restart-pending status and last install / check times, with a shortcut to Windows Update settings. Nexus never changes Windows Update policies.

## 3. Penyahpasang Perisian (Software Uninstaller)

- Search by name or publisher, filter (all / ordinary / runtimes & drivers / system components) and sort by name, size, install date or publisher.
- Dot colours: green = ordinary app, orange = runtime or driver (other apps may depend on it), red = protected system component (cannot be uninstalled here).
- Select an app to see the details panel (publisher, version, date, size, scope, WinGet ID, install location).
- **Nyahpasang (Uninstall)** runs the app's own registered uninstaller (UAC appears for machine-wide apps). **Nyahpasang melalui WinGet** is offered when the app is a WinGet package.
- After the uninstaller closes, Nexus checks that the app is really gone and reports the result.
- Store apps: use **Tetapan Apl Windows (Windows Apps settings)**.

## 4. Pengurus RAM (RAM Manager)

- Total, used and available physical RAM, usage % and a live chart.
- Applications sorted by memory; **TINGGI (HIGH)** marks apps using > 10 % of RAM or > 1.5 GB.
- Tick apps → **Tutup dipilih (Close selected)** → confirm you saved your work. Apps are asked to close exactly like clicking **X**, so they can prompt you to save.
- The *force* option is off by default; enabling it requires a second, explicit confirmation.
- System processes and security software cannot be selected (toggle *Tunjuk proses sistem* only shows them).
- Nexus does **not** "clean" RAM, empty standby lists or trim working sets — Windows manages that memory better itself.

## 5. Pembersih Storan (Storage Cleaner)

1. Choose the **age threshold** (only files older than N days) and, if wanted, enable the opt-in categories (browser cache, Recycle Bin).
2. Click **Imbas (Scan)** — sizes and file counts appear per category; nothing is deleted.
3. Select categories and click **Bersihkan dipilih (Clean selected)**. Review the confirmation list, then confirm.
4. Each category shows what was recovered and how many files were skipped (in use / access denied). A text report is saved; open it with **Buka laporan (Open report)**.

Categories: user temp, Windows temp (admin), thumbnail cache, DirectX/NVIDIA/AMD/Intel shader caches, Windows error
reports & crash dumps, Delivery Optimization cache (admin, via `Delete-DeliveryOptimizationCache`), browser cache
folders only (opt-in; running browsers are skipped), Recycle Bin (opt-in, permanent).
For old Windows Update files use **Pembersihan Cakera (Disk Cleanup)** or **Storage Sense** — buttons provided.

## 6. Pengoptimum SSD/HDD (SSD/HDD Optimizer)

- **Kesan pemacu (Detect drives)** lists every volume: model, bus, file system, SSD/HDD/Unknown, capacity, used, free, TRIM support, Windows health.
- **Analisis (Analyze)** — read-only fragmentation/optimisation analysis (admin).
- **Optimumkan (Optimize)** — SSD: `Optimize-Volume -ReTrim`; HDD: `Optimize-Volume -Defrag`; Unknown media: shown with a warning and only the Windows default operation is offered after you tick an acknowledgement.
- The operation output and history are shown below; phases are labelled *Sedang menganalisis / Analisis selesai / Sedang mengoptimumkan / Pengoptimuman selesai*.
- **Optimumkan Pemacu (Windows)** opens Windows' own *Optimize Drives* tool.

## 7. Pengurus Permulaan (Startup Manager)

- Lists startup entries from HKCU/HKLM Run keys and the Startup folders with publisher, location and status.
- Labels: *Boleh dilumpuhkan (Can be disabled)* for common launchers/helpers; *Dilindungi (Protected)* for security, driver and hardware software (cannot be disabled here).
- Click the status button (or **Tukar status**) → read the explained effect → confirm. A backup is created before every change.
- **Sandaran & pemulihan (Backups & restore)** reverts any earlier change.
- **Cipta titik pemulihan (Create restore point)** — optional System Restore point (reports clearly if System Protection is off).
- Impact shows **T/B (N/A)**: Windows does not provide this measurement publicly, so Nexus does not invent one.

## 8. Penutupan Pintar (Smart Shutdown)

Choose the operations (disk space check, temp cleanup, Windows temp, caches, browser cache, Recycle Bin, SSD TRIM,
startup review) and the age threshold, then:

- **Mod 1 — Sediakan sekarang (Prepare now):** runs the steps, shows live per-step progress, saves a maintenance report and lists startup recommendations. The PC stays on.
- **Mod 2 — Optimumkan & tutup (Optimize & shut down):** runs the steps, shows the summary, then asks for **final confirmation** (you must tick "I have saved all my work"). After that a **10-second countdown with Cancel** appears. Windows then performs a normal shutdown (`shutdown /s /t 0`, no force) — apps with unsaved work can still stop it.

Honest note: temp cleanup and TRIM do not directly speed up boot. Startup time depends mostly on startup apps — review the recommendations.

## 9. Kesihatan Sistem (System Health)

Live CPU / RAM / disk-activity charts and a colour-coded overview: green good, yellow attention, red action
required, grey **no data** (never shown as healthy). **Baca suhu & haus pemacu** reads temperature, wear and
power-on hours (admin; only if the drive reports them).

## 10. Penjadual Penyelenggaraan (Maintenance Scheduler)

For each job — update check, temp cleanup, storage analysis, SSD optimisation — choose Manual / Daily / Weekly /
Monthly, the day and time (24 h `HH:mm`), then **Guna (Apply)**. Tasks appear in Windows Task Scheduler under
`\NexusPCOptimizer`.

- Update checks only check, unless you switch on **automatic installation consent** (excluded/pinned/unknown apps are still never updated).
- Scheduled cleanup uses the categories selected in the Storage Cleaner (admin categories excluded) and asks you to confirm when scheduling.
- SSD optimisation tasks run with highest privileges (one UAC prompt when created).
- **Lumpuhkan semua jadual (Disable all schedules)** removes every Nexus task.

## 11. Log Aktiviti (Activity Logs)

Every operation is recorded with date/time, operation, target, status, space recovered, error and whether it ran
with admin rights. Filter by category (maintenance, updates, uninstalls, cleanup, disk, startup, memory, scheduler,
system, errors), search, view details, **Eksport CSV / TXT**, open the logs or reports folder, or clear history.

## 12. Tetapan (Settings)

Language (Bahasa Melayu / English), theme (Dark / Light), default cleanup age, app-close timeout, run mode and
**Mula semula sebagai pentadbir (Restart as administrator)**, System Restore point, update exclusions and version info.

## 13. Pusat Notifikasi (Notification Centre)

Official announcements from the NEXUS owner — new versions, security updates, maintenance, new features, known
issues and service interruptions. A blue badge in the sidebar shows unread items. **Tandakan dibaca (Mark as read)**
per item or for all. Links open in your browser only if they are https and not a download of a program.
Announcements are fetched over HTTPS and accepted only if their digital signature verifies.
A yellow notice appears if your version is below the minimum supported version or there is service maintenance.

## 14. Akaun & Lesen (Account & License) — optional

NEXUS is free; registration is **optional** and does not unlock or lock any maintenance feature.

1. Enter your e-mail, tick the privacy consent, press **Hantar pautan pengesahan (Send verification link)**.
2. Open the e-mail, click the link and press the confirmation button. Your 22-character serial is shown once and e-mailed.
3. Paste the serial in **Nombor siri (Serial)** and press **Aktifkan (Activate)**. Dashes/spaces are ignored.

The serial is stored on your PC encrypted with Windows DPAPI. NEXUS re-checks it weekly in the background.
**Manage your account** (enter your registered e-mail first): replace a lost serial, request a copy of your data,
or delete your account — each confirmed by an e-mail link. **Buang lesen dari PC ini** removes the license from this PC.

## 15. Updating NEXUS itself

**Tetapan › Kemas kini NEXUS (Settings › NEXUS updates) › Semak kemas kini (Check for updates).** If a newer
version exists: **Muat turun & pasang (Download & install)**. NEXUS downloads the installer from the official GitHub
releases, verifies the digital signature and the SHA-256 checksum (a mismatching file is deleted), then asks you
before running the installer. Windows is never restarted automatically.

## 16. Privacy & optional diagnostics

**Tetapan › Privasi & diagnostik pilihan.** Off by default. When on, NEXUS sends once a week only the number of
failed operations per module and update results — never files, paths, software lists, browser data, usage or
hardware identifiers. See **Notis privasi (Privacy notice)** and `docs/PRIVACY.md`.
