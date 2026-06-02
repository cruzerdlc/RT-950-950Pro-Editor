## v0.7.0-pre33 - Zone Write Save Fix

- Fixed Radio Read **Save As .dat** so it only asks where to save the file; it no longer asks the user to open/select a template first.
- Added bundled `rt950pro_dat_template.dat` used internally for Radio Read Save As .dat.
- Fixed Radio > Write Radio so edited zone names are applied to the radio write image.
- Added Zone Names to the Write Radio scope/status text.
- Confirmed RT-950PRO .dat zone names use the radio-style names: `ZoneOne`, `ZoneTwo`, `ZoneThree`, etc.

## v0.7.0-pre12 - Modulation CSV Fix
- Fixed Zone editor Apply Name crash.
- Removed Import CSV / Export CSV from Edit > Zones.
- Added Import CSV, Export CSV, and Download CSV Template under Edit > FM/AM/SSB Modulation.
- Added detailed rt950_modulation_template.csv.


## v0.7.0-pre10 - Modulation CSV + Zones

- Added File > Download CSV templates... for channel template, zone template, and detailed field guide.
- Added Edit > Zones... editor for zone names.
- Added zone-name CSV import/export.
- Preserved v0.7.0-pre9 prerelease-aware GitHub update checker fix.

## v0.7.0-pre9 - Update checker prerelease fix

- Fixed GitHub update checks when the latest published build is a GitHub prerelease.
- The updater now checks the normal latest release endpoint, then the releases list including prereleases, then the VERSION file.
- Improved the error message when GitHub data cannot be read.


## v0.7.0-pre9 - Auto update checker

- Added **Help → Check for Updates...**.
- Added automatic startup update check against the project GitHub repository.
- The app checks the latest GitHub Release first, then falls back to the raw `VERSION` file if no release is published yet.
- If a newer release is found, the app asks whether to open the GitHub download/release page.
- Updated build metadata to v0.7.0-pre9.


## v0.7.0-pre9

- Fixed the clean portable Windows build script for PyInstaller 6.x.
- Removed the invalid `--noupx` command-line option when building from the `.spec` file.
- UPX remains disabled in `RT950_950Pro_Editor.spec` using `upx=False`.
- Build command remains `BUILD_CLEAN_PORTABLE_WINDOWS.bat`.


## 0.7.0-pre6

- Fixed clean portable build bootstrap when Windows only has the Microsoft Store `python` alias.
- Build script now searches for `py.exe`, Python 3.13/3.12/3.11, `python`, and `python3`.
- If Python is missing, the build script can install Python 3.12 using `winget`.
- Added `INSTALL_PYTHON_FOR_BUILD_WINDOWS.bat` helper.
- Kept the release packaging as PyInstaller onedir + `--noupx` to reduce antivirus false positives.

# Changelog

## v0.7.0-pre9

- Added `scripts/Upload-BuildToGitHub.ps1` for uploading tested Windows builds to GitHub Releases.
- Added `docs/GITHUB_RELEASE_UPLOAD_SCRIPT.md` with maintainer upload instructions.
- The upload script supports existing portable ZIP files, EXE-to-ZIP packaging, draft releases, prerelease releases, and replacing existing release assets.

## v0.7.0-pre9

Documentation cleanup for EXE-only distribution.

- Removed `docs/BUILDING_WINDOWS_EXE.md`.
- Removed `docs/DEVELOPER_NOTES.md`.
- Removed the source/Python first-time setup section from the user guide.
- User-facing setup now points only to the Windows executable workflow.


## v0.7.0-pre9

- Updated README for EXE-only distribution.
- Removed end-user build instructions from README.
- README now tells users to download and run the Windows executable from GitHub Releases.

All notable changes to **RT-950/950Pro Editor** are tracked here.

## v0.7.0-pre9

Pre-production packaging release.

- Added Windows EXE build scripts.
- Added PyInstaller spec file.
- Added optional Inno Setup installer script.
- Added GitHub-ready `README.md`.
- Added user guide, build guide, release checklist, developer notes, protocol notes, troubleshooting, backup notes, and radio-compliance notes.
- Added contributing, support, security, license, requirements, and `.gitignore` files.
- Updated app version to `v0.7.0-pre9`.

## v0.7.0-pre9

Production polish pass.

- Help menu now shows **About** instead of **About / workflow**.
- Removed internal developer/link-storage text from the About dialog.
- About dialog keeps public project information only.

## v0.6.4

- Updated Donate link to Cash App: `https://cash.app/$cruzerdlc`.

## v0.6.3

- Added custom app icon.
- Added **Made by KK4OXN** to About.
- Added GitHub and Donate links to About.

## v0.6.2

- Expanded setting descriptions across the Edit menu.
- Added descriptions informed by the RT-950 PRO manual for VFO, optional features, DTMF, FM/AM/SSB, APRS, and encryption-related fields.

## v0.6.1

- Renamed app to **RT-950/950Pro Editor**.
- Added info icons/tooltips next to many channel and settings fields.

## v0.6.0

- Cleaned boot picture workflow for production.
- Removed unsupported direct boot-image readback and local cached image workflow.
- Boot Picture now focuses on: Open Image, Fit, Reset, Save BMP, Upload to Radio.

## v0.5.9

- Removed direct boot-image readback from normal workflow after firmware returned unsupported status.
- Kept confirmed boot-image upload path.

## v0.5.8

- Recognized `A5 EE ... 04` boot-image readback refusal.
- Avoided scary timeout when the firmware refuses boot-image readback.

## v0.5.7

- Cleaned Pillow deprecation warning.
- Added local boot-image cache fallback after successful upload.

## v0.5.6

- Removed normal-menu lab/test tools.
- Cleaned Boot Picture into production workflow.
- Added first Load Current Image attempt before later removing it for production safety.

## v0.5.5

- Treated missing final `Over` ACK as OK if all 150 boot-image pages ACKed.
- Displayed cleaner boot-image upload success.

## v0.5.4

- Fixed missing `BootImageUploadDialog` class.
- Added Boot Image Upload dialog.

## v0.5.3

- Added first direct boot-picture upload test.
- Implemented `D` mode + `A5` setup packets + 150 RGB565 pages + `Over` packet.

## v0.5.2

- Fixed com0com setup helper so `setupc.exe` runs from its own folder.
- Improved validation for selected com0com tools.

## v0.5.1

- Added Virtual COM Setup Wizard.
- Added instructions for com0com / virtual null-modem pair workflow.

## v0.5.0

- Added Packet Capture Tool.
- Added direct capture and proxy bridge capture for factory CPS traffic.

## v0.4.9

- Added Boot Image Capture Lab.
- Added test BMP/raw payload generation.
- Added factory CPS boot-image capture analysis helpers.

## v0.4.8

- Grouped Optional Features into boxed sections.
- Ordered number-key long-press settings from Key [0] through Key [9].
- Added boot-image raw RGB payload export and process notes for protocol mapping.

## v0.4.7

- Added CHIRP-style built-in stock preset browser.
- Added stock preset CSVs and import-to-zone workflow.

## v0.4.6

- Added File → Import stock config / preset CSV to zone.
- Added overwrite vs append behavior for zone import.
- Improved Boot Picture radio-style preview.

## v0.4.5

- Boot Picture could load a current BMP from disk and remember the last exported BMP.
- Improved radio preview mockup.

## v0.4.4

- Cleaned Read Radio and Write Radio progress windows.
- Moved technical serial logs behind Show Details.
- Added Tools → Boot Picture.
- Added 240×320 24-bit BMP export workflow.

## v0.4.3

- Fixed write verify reconnect timing.
- If radio was slow to re-enter programming mode, write no longer falsely reported failure.

## v0.4.2

- Simplified production read/write workflow.
- Removed normal probe/test controls.
- Read Radio = choose COM port and read.
- Write Radio = choose COM port and write.
- Backup and verify happen automatically.

## v0.4.1

- Renamed normal radio menus to Read Radio and Write Radio.
- Added write scopes and verify after write.
- Added Open Backup Capture.

## v0.4.0

- Added full known-block write support:
  - channels
  - VFO
  - optional features
  - DTMF
  - FM/AM/SSB modulation
  - APRS
- Preserved unknown/unedited bytes from a fresh backup read.

## v0.3.9

- Fixed final channel write page by padding to factory-compatible 128-byte pages.
- Confirmed channel write and read-back.

## v0.3.8

- Added first experimental channel write workflow.
- Added fresh pre-write backup.

## v0.3.7

- Made Radio Read setting tabs editable.
- Added zones to Radio Read tabs.

## v0.3.6

- Fixed blank settings fields in in-app settings tabs.

## v0.3.5

- Moved VFO, Optional Features, DTMF, FM/AM/SSB, APRS, and Encryption editors into in-app tabs.

## v0.3.4

- Radio Read tabs now retain settings blocks instead of only channel rows.
- Settings viewers can open from Radio Read tabs.

## v0.3.3

- Fixed radio read channel-frame decoding.
- Confirmed 990 channel slots and populated channel data.

## v0.3.2

- Implemented original CPS radio read protocol discovery.
- Added RT-950 handshake and block read logic.

## v0.2.x

- Added CHIRP-like tabs and channel list behavior.
- Added closeable tabs.
- Added zone selector.
- Added tone dropdowns.
- Added live side editor changes.
- Added right-click cut/copy/paste.
- Added draggable column order persistence.

## v0.1.x

- Initial proof-of-concept codeplug editor.
- Imported/exported CSV.
- Opened RT-950Pro `.dat` files and displayed channel rows.
