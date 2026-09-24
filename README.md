# Nucleus

CSC VB6 inventory orchestrator suite. `Nucleus.exe` reads `Software\CSC\Nucleus\Applications` (or a command-line path), spawns each listed collector via `clsProcess`, waits on a timer, then zips `C:\Nucleus\*.*` with `CGZipFiles` / unzip32 and copies `<computername>.zip` to `\\CBDXAAI\Nucleus`. Companion `McInfo.exe` (form caption "Envy") gathers McAfee VirusScan registry/engine/defs, McShield service state, DrWatson log date, and NetShield scan results into `C:\Nucleus\AVReport.txt`. `DiskStats.exe` walks local drives and appends INSERT SQL for `tblDiskSpace` to `C:\Nucleus\DiskSpace.txt`, coordinating via the shared Nucleus Collecting registry counter.

**Source last updated:** 2026-08-27 · **Language:** VB6 · **Target:** VB6 Win32 · **Output:** WinForms exe

_Note: original OneDrive LastWriteTime values were wiped to 2026-08-27 by a zip transfer; date above uses best available evidence (headers/copyright where helpful)._

## Solution structure

| Project | Language | Type | Purpose |
|---------|----------|------|---------|
| `Nucleus` (`Nucleus/Nucleus.vbp`) | VB6 | WinForms exe | Spawn collectors, zip C:\Nucleus, copy zip to share |
| `McInfo` (`Mcinfo/Mcinfo.vbp`) | VB6 | WinForms exe | Collect McAfee AV / McShield / DrWatson inventory SQL |
| `DiskStats` (`DiskStats/DiskStats.vbp`) | VB6 | WinForms exe | Local disk free/used space SQL for tblDiskSpace |

## How to open

Open the `.vbp` in Visual Basic 6.0 IDE:
- `Nucleus/Nucleus.vbp`
- `Mcinfo/Mcinfo.vbp`
- `DiskStats/DiskStats.vbp`

## Requirements

- Visual Basic 6.0 IDE
- For DiskStats: ADO 2.6, Scripting Runtime, and optional DiskSpace COM (`diskspace.dll`) as referenced
- For Nucleus zip: `unzip32.dll` / zip32 helpers used by `CGZipFiles` / `CGUnzipFiles`
- Registry write access under `HKLM\Software\CSC\Nucleus` (and SOTD for alternate DiskStats module)

## Attribution and provenance

Working copy from my Historical Dev folder `VB/Old/Nucleus`.
Company names in project files: CSC.
Product names: Nucleus / DiskStats.

## License

MIT (c) 2026 VaderConsulting for Dave Robinson's code. See `LICENSE`.
