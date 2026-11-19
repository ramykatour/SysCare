<p align="center">
  <img src="syscare.ico" width="96" alt="SysCare">
</p>

<h1 align="center">SysCare</h1>

<p align="center">
  A small maintenance toolkit for Windows 10 and 11.<br>
  Junk cleaner, RAM cleaner, duplicate finder, registry fixer, startup manager and a network monitor in one window.
</p>

<p align="center">
  <a href="https://github.com/ramykatour/SysCare/releases/latest"><b>Download SysCare.exe</b></a> ·
  <a href="https://github.com/ramykatour/SysCare/issues">Report a bug</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-2.1-22d3ee" alt="version 2.1">
  <img src="https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-0078D4" alt="Windows 10 | 11">
  <img src="https://img.shields.io/badge/price-free-green" alt="free">
</p>

<!-- Screenshots go in docs/screenshots/ -->
<p align="center">
  <img src="docs/screenshots/dashboard.png" width="720" alt="SysCare dashboard">
</p>

## What it does

**Junk Cleaner** clears temp files, the thumbnail cache, Windows error reports, the Windows Update download cache, Chrome / Edge / Firefox caches and the Recycle Bin. It shows the size of each category before you delete anything.

**RAM Cleaner** asks Windows to release idle memory from running processes and tells you how much came back. There is an option to flush the standby cache as well (needs Administrator). Below that is a list of the 40 biggest memory users, and you can end any of them from there.

**Duplicate Finder** matches files by size first, then a partial hash, then a full SHA-256. You pick which copy to keep (oldest, newest or shortest path). It will not let you delete every copy in a group.

**Large Files** lists the biggest files in a folder you choose.

**Registry Fixer** looks for broken startup entries, orphaned uninstall entries and dead App Paths. Before it touches anything it writes a `.reg` backup, and if the backup fails that item is skipped. Backups can be restored from inside the app. It can also create a restore point first.

**Startup Manager** enables or disables startup programs the same way Task Manager does, so nothing is deleted. Torrent clients are highlighted.

**Network Monitor** shows live download and upload speed and which processes hold the most connections. Torrent clients are flagged and can be ended from the list.

## How it handles your files

- Duplicate Finder and Large Files send files to the Recycle Bin instead of deleting them.
- Registry fixes are backed up to `Documents\SysCare\RegistryBackups` first.
- Only clear-cut registry problems are listed. There is no "optimize" button.
- The scanners skip `Windows`, `Program Files`, `ProgramData` and `AppData`.
- Anything destructive asks for confirmation.

Two things worth knowing. Cleaning the registry almost never speeds up a PC, so treat it as a way to remove leftovers. And the RAM Cleaner gives you free memory for a short while: Windows reloads pages as programs need them, so it is mainly useful when memory is close to full. If usage is always high, the list of top processes will tell you more than the cleaner will.

## Download and install

1. Go to the [Releases](https://github.com/ramykatour/SysCare/releases/latest) page and download `SysCare.exe`.
2. Run it. There is no installer and nothing is written outside your own folders, apart from the registry backups mentioned above.
3. Accept the Administrator prompt. It is needed for the Windows Temp folder, the Update cache, the standby cache and HKLM registry entries. Without it SysCare still runs, but those items are skipped.

Requirements: Windows 10 or 11, 64-bit.

VirusTotal report: [view scan](https://www.virustotal.com/gui/file/5af1ec346f68285d5130ac57b11d49e86503eb959073f5fb9316b5b46e932282/detection)

### Windows SmartScreen

On first launch Windows may show "Windows protected your PC", because the exe is not signed with a paid code-signing certificate. Click **More info**, then **Run anyway**.

### Antivirus warnings

A few engines flag programs that edit the registry, touch process memory and ask for admin rights, and SysCare does all three. In the VirusTotal scan of version 2.1, 3 of 71 engines (Bkav Pro, CrowdStrike Falcon and SecureAge) returned generic heuristic detections, and the major engines did not flag it. This is common for PyInstaller builds. You can [check the current report](https://www.virustotal.com/gui/file/5af1ec346f68285d5130ac57b11d49e86503eb959073f5fb9316b5b46e932282/detection) yourself. If you are not comfortable running it, don't.

## FAQ

**Can the RAM Cleaner make me lose unsaved work?**
No. It does not close anything. Only the "End checked processes" button does, and it asks first.

**It freed almost nothing.**
That usually means there was little idle memory to release. Look at the process list to see what is actually using it.

**How do I undo a registry fix?**
Registry Fixer, then "Restore from backup...", then pick the `.reg` file. Double-clicking the file in Explorer works too.

**My internet is slow.**
Open the Network page. A running torrent client shows up in red. End it there and disable it in Startup Manager so it stays off.

**Why do some items say they need Administrator?**
Windows Temp, the Update cache, the standby cache and HKLM entries are protected. Run SysCare as Administrator to include them.

**How do I uninstall it?**
Delete `SysCare.exe`. Registry backups stay in `Documents\SysCare` until you remove that folder.

## Feedback

Found a bug or want a feature? [Open an issue](https://github.com/ramykatour/SysCare/issues) and include your Windows version and what you clicked.

## License

SysCare is free to use for personal and commercial use. The software is provided as is, without warranty. Redistribution of modified copies or reverse engineering is not permitted without written permission.

© 2026 [DevoSoft](https://github.com/ramykatour). Keep backups of anything important.
