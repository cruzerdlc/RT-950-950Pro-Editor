## v0.7.0-pre63 - Delete/insert, editor delete button, tone OFF, panel fixes

Fixed (regressions)
- FM/AM/SSB Modulation tab was blank: the table grids were nested inside a
  scroll-frame canvas (canvas-in-canvas), which rendered empty. They now lay
  out directly and show again.
- Optional Features showed only one card: removed a width-tracking layout
  hack and uniform-column sizing; all six cards render again.

Added
- Right-click menu: "Delete row" (in addition to Insert blank above/below).
- Keyboard on the channel list: Delete removes the selected row(s) and shifts
  the list up; Insert adds a blank line below the selection.
- Channel editor popup: "Delete channel" button removes the current channel
  (list shifts up) and reloads the slot.

Changed
- RX Tone / TX Tone now show "OFF" instead of "None" everywhere (channel
  list, channel editor dropdowns, VFO).
- Settings fields sized to their values instead of stretching full width
  (APRS, DTMF, Optional, VFO) - cards hug the left with a trailing spacer.
- APRS Info scrolls fully (no more cut-off bottom row) and the custom message
  box is a sensible width.
- Zones tab restyled to match the app: section header, banded rows, accent
  Apply button.
- DTMF group/info fields resized to fit their values.

## v0.7.0-pre63 - Editor popup fix, insert-blank, default column order

Fixed
- Channel editor popup: the Close button and status line are now pinned to
  the bottom and always visible (they were getting cut off). The window is a
  bit taller and resizable, with a sensible minimum size.

Added
- Right-click menu: "Insert blank above" and "Insert blank below" the
  selected channel. Inserting shifts the rest of the list (or the current
  zone) down by one; the last slot in range is pushed out, with a status
  note if it held data.

Changed
- Default channel-list column order now matches the requested layout:
  CH, Name, TX Freq, RX Freq, RX Tone, TX Tone, Power, Wide, Busy Lock,
  Scan, TX Enable, RX Mod. Columns are still drag-to-reorder and your
  arrangement is remembered. Existing settings are migrated once to this
  default; after you drag a column, your order sticks. Use
  View > Reset channel-list column order to return to this default.

## v0.7.0-pre63 - Main screen redesign: inline editing, popup editor, frequency rules

Changed
- Removed the fixed side channel-editor panel. The channel list now fills the
  whole tab for a clearer, wider grid.
- Edit channels two ways:
  * Inline: click a row to select it, then click a cell again (or press F2 /
    Enter) to edit that cell directly in the table. Choice fields (tone,
    power, etc.) show a dropdown; text/frequency fields are typed.
  * Popup editor: double-click a row (or use the "Edit channel" toolbar
    button) to open a channel editor showing every field, with Previous /
    Next buttons (and PageUp/PageDown) to scroll through channels without
    closing it. The popup follows the table selection and vice-versa.
- Frequencies are shown exactly as entered - no trailing zeros are added in
  the display (132 stays "132", 146.52 stays "146.52"). The canonical padded
  form is still used internally when writing to the radio/.dat.

Added
- Frequency range validation for channel RX/TX. Entries must be within the
  radio's tunable range (0.1-1000 MHz); out-of-range or non-numeric values are
  rejected with a clear message. A TX frequency outside the radio's transmit
  bands (144-148, 420-450, and 27 MHz CB) is allowed but flagged with a note
  that the radio will receive but not transmit there. Limits are defined as
  named constants (RADIO_RX_MIN/MAX_MHZ, RADIO_TX_BANDS_MHZ) and are easy to
  adjust. (Sources: Radtel RT-950Pro product listings.)

## v0.7.0-pre63 - Wider channel editor, Read/Write dialog styling, progress bars

Changed
- Main window channel editor is now double-wide and lays its fields out in
  two columns, so the property list is shorter and easier to scan. The
  window opens with the editor pane pre-sized (~470 px) and the split is
  draggable.
- Read Radio and Write Radio dialogs restyled to the Fluent look: primary
  actions use the accent button, helper text uses the caption style, the
  log/console areas use a white card with a hairline border and Consolas,
  and consistent spacing throughout. Status/warning colors use Fluent tones
  (error #C42B1C, success #0F7B0F).
- COM Port settings dialog: caption helper text and accent Save button.

Fixed
- Read Radio and Write Radio now show a working progress bar while a
  read/write is running. Previously the code called `self.progress.start()`
  but no progress bar was ever created, so the busy indicator silently did
  nothing (the AttributeError was swallowed).

## v0.7.0-pre63 - Modulation layout fix, headless-import fix, code audit

Fixed
- FM/AM/SSB Modulation (Radio Read): rebuilt the layout with a scrollable
  grid. The AM/SSB "Step Freq / Rx Gain" footer cards no longer clip their
  second row, the Import/Export buttons now render correctly (were blank
  boxes), and the whole page scrolls instead of being pinned to a fixed
  size. Removed all absolute pixel placement from this editor.
- Headless / CLI-without-Tk: the module now imports on systems without
  Tkinter. Previously `class ClosableNotebook(ttk.Notebook)` referenced
  `ttk` at import time, so the documented command-line mode (check / export
  / import / convert-chirp) crashed on import where Tk was unavailable.
  Added a safe placeholder base used only when Tk is missing.

Changed
- Settings-panel subtitles use the Caption type-ramp style instead of a
  hardcoded gray, for consistent typography.

Verified
- Core data path exercised end-to-end via the CLI on the bundled template:
  .dat parse (990 slots), export to CSV, CSV import + re-save + reparse, and
  CHIRP CSV conversion all succeed with no errors.
- Module imports cleanly both with Tk present (GUI definitions) and absent
  (CLI mode); the Fluent theme applies without errors.

## v0.7.0-pre63 - Fluent UI overhaul and settings-panel layout fixes

UI redesigned to follow Microsoft's Windows app design guidance
(https://learn.microsoft.com/windows/apps/design/).

Fixed
- Optional Features (Radio Read): cards no longer clip the right-hand
  column. Replaced the fixed-size, absolutely-placed cards with a
  responsive, scrollable 3-column grid whose cards size to their content.
- APRS Info (Radio Read): cards no longer clip the last field (e.g. "APRS
  Tx Data Reporting"). Removed fixed card width/height; cards size to
  content and the value columns absorb slack so dropdowns render in full.
- FM/AM/SSB Modulation (Radio Read): table columns (including Name) are no
  longer clipped; panel widths are derived from the column widths plus the
  scrollbar. CSV action buttons now read as buttons instead of blank boxes.
- Section titles now show a single "&" (e.g. "Audio, Power & VOX") instead
  of a literal "&&".
- Main window: status bar is packed before the notebook so tab content is
  no longer hidden behind the bar.
- Channel-list columns widened so headers ("Busy Lock", "TX Enable",
  "RX Mod") and values are no longer clipped; short flag columns centered;
  the Name column stretches to fill.
- Channel editor side panel is now scrollable, so all 18 fields and the
  footer are always reachable on shorter windows.

Changed
- Typography follows the Windows type ramp: one font family (Segoe UI
  Variable, falling back to Segoe UI), Semibold (not Bold) for headings,
  sentence casing, left alignment.
- Built-in Fluent Light theme (neutral surfaces, #0078D4 system accent,
  flat controls with an accent focus ring, banded table rows, thin
  scrollbars). Uses sv-ttk (Sun Valley) automatically when installed.
- Standard buttons use a subtle neutral fill distinct from white entry
  fields; primary actions use the accent button style.

Notes
- Optional dependency: `pip install sv-ttk` for the most authentic Windows
  11 surface. The app runs and themes correctly without it.

## v0.7.0-pre63 - Zone Write Save Fix

- Fixed Radio Read **Save As .dat** so it only asks where to save the file; it no longer asks the user to open/select a template first.
- Added bundled `rt950pro_dat_template.dat` used internally for Radio Read Save As .dat.
- Fixed Radio > Write Radio so edited zone names are applied to the radio write image.
- Added Zone Names to the Write Radio scope/status text.
- Confirmed RT-950PRO .dat zone names use the radio-style names: `ZoneOne`, `ZoneTwo`, `ZoneThree`, etc.

## v0.7.0-pre63 - Modulation CSV Fix
- Fixed Zone editor Apply Name crash.
- Removed Import CSV / Export CSV from Edit > Zones.
- Added Import CSV, Export CSV, and Download CSV Template under Edit > FM/AM/SSB Modulation.
- Added detailed rt950_modulation_template.csv.


## v0.7.0-pre63 - Modulation CSV + Zones

- Added File > Download CSV templates... for channel template, zone template, and detailed field guide.
- Added Edit > Zones... editor for zone names.
- Added zone-name CSV import/export.
- Preserved v0.7.0-pre63 prerelease-aware GitHub update checker fix.

## v0.7.0-pre63 - Update checker prerelease fix

- Fixed GitHub update checks when the latest published build is a GitHub prerelease.
- The updater now checks the normal latest release endpoint, then the releases list including prereleases, then the VERSION file.
- Improved the error message when GitHub data cannot be read.


## v0.7.0-pre63 - Auto update checker

- Added **Help → Check for Updates...**.
- Added automatic startup update check against the project GitHub repository.
- The app checks the latest GitHub Release first, then falls back to the raw `VERSION` file if no release is published yet.
- If a newer release is found, the app asks whether to open the GitHub download/release page.
- Updated build metadata to v0.7.0-pre63.


## v0.7.0-pre63

- Fixed the clean portable Windows build script for PyInstaller 6.x.
- Removed the invalid `--noupx` command-line option when building from the `.spec` file.
- UPX remains disabled in `RT950_950Pro_Editor.spec` using `upx=False`.
- Build command remains `BUILD_CLEAN_PORTABLE_WINDOWS.bat`.


## 0.7.0-pre63

- Fixed clean portable build bootstrap when Windows only has the Microsoft Store `python` alias.
- Build script now searches for `py.exe`, Python 3.13/3.12/3.11, `python`, and `python3`.
- If Python is missing, the build script can install Python 3.12 using `winget`.
- Added `INSTALL_PYTHON_FOR_BUILD_WINDOWS.bat` helper.
- Kept the release packaging as PyInstaller onedir + `--noupx` to reduce antivirus false positives.

# Changelog

## v0.7.0-pre63

- Added `scripts/Upload-BuildToGitHub.ps1` for uploading tested Windows builds to GitHub Releases.
- Added `docs/GITHUB_RELEASE_UPLOAD_SCRIPT.md` with maintainer upload instructions.
- The upload script supports existing portable ZIP files, EXE-to-ZIP packaging, draft releases, prerelease releases, and replacing existing release assets.

## v0.7.0-pre63

Documentation cleanup for EXE-only distribution.

- Removed `docs/BUILDING_WINDOWS_EXE.md`.
- Removed `docs/DEVELOPER_NOTES.md`.
- Removed the source/Python first-time setup section from the user guide.
- User-facing setup now points only to the Windows executable workflow.


## v0.7.0-pre63

- Updated README for EXE-only distribution.
- Removed end-user build instructions from README.
- README now tells users to download and run the Windows executable from GitHub Releases.

All notable changes to **RT-950/950Pro Editor** are tracked here.

## v0.7.0-pre63

Pre-production packaging release.

- Added Windows EXE build scripts.
- Added PyInstaller spec file.
- Added optional Inno Setup installer script.
- Added GitHub-ready `README.md`.
- Added user guide, build guide, release checklist, developer notes, protocol notes, troubleshooting, backup notes, and radio-compliance notes.
- Added contributing, support, security, license, requirements, and `.gitignore` files.
- Updated app version to `v0.7.0-pre63`.

## v0.7.0-pre63

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
