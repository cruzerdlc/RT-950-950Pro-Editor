
Startup default: this build opens the bundled RT-950PRO_CPS_Data20260626132407.dat save automatically when the app starts. Use File > Open startup default save to reopen it, or File > New blank channel list for a scratch tab.

# RT-950/950Pro Editor

**RT-950/950Pro Editor** is a Windows application for programming and managing the Radtel RT-950 / RT-950Pro radio.

Made by **KK4OXN**.

Project: https://github.com/cruzerdlc/RT-950-950Pro-Editor  
Donate: https://cash.app/$cruzerdlc

> **Pre-production status:** read, write, settings edit, stock presets, and boot image upload have been tested during development. Keep backups and verify your own radio before depending on it.
>
> **Binary packaging note:** public builds are distributed as a clean portable Windows folder/ZIP instead of a one-file self-extracting EXE to reduce antivirus false positives.


### v0.7.0-pre93 public-build cleanup

This build removes the hidden developer packet-capture tools from the public source package and executable build path. The normal **Tools > Boot Picture** feature remains.

Removed from public build:

- Virtual COM Setup
- Packet Capture Tool
- Boot Image Capture Lab
- Ctrl+T Dev Mode menu toggle

## Download and run

This project is intended to be delivered as a ready-to-run Windows executable. End users do **not** need Python, PyInstaller, or any build tools.

1. Go to the project **Releases** page.
2. Download the latest Windows release package.
3. Extract the ZIP if the release is packaged as a portable ZIP.
4. Run:

```text
RT-950_950Pro_Editor.exe
```

5. Connect the RT-950 / RT-950Pro programming cable.
6. Use **Radio → Read Radio** to read the radio.
7. Edit channels or settings.
8. Use **Radio → Write Radio** to write changes back to the radio.

## First-time setup

Most users only need the radio programming cable driver installed. Many RT-950 / RT-950Pro programming cables show up as a CH340 / CH341 USB serial device.

Before using the app:

- Install the USB serial driver for your programming cable if Windows does not detect it automatically.
- Confirm the cable appears in Windows Device Manager under **Ports (COM & LPT)**.
- Note the COM port number, such as `COM5`.
- Keep the radio powered on and connected during read/write operations.

## Main features

- Direct radio **Read Radio** and **Write Radio** over COM port.
- Automatic pre-write backup.
- Automatic read-back verification after write.
- Multi-tab editor similar to CHIRP.
- Zone selector for Zone 1 through Zone 10.
- Live channel editor panel.
- Right-click cut/copy/paste rows.
- Draggable/reorderable columns with remembered layout.
- Tone dropdowns with None, CTCSS, DCS Normal, and DCS Inverted.
- Edit tabs for:
  - VFO Mode
  - Optional Features
  - DTMF Codes
  - FM/AM/SSB Modulation
  - APRS Info
  - Encryption Presets / Defaults
- Info icons and setting descriptions based on the RT-950 PRO manual.
- Built-in stock preset browser/importer.
- Boot Picture editor with crop/preview/save/upload.
- Custom Windows app icon.
- Automatic update checker using GitHub Releases.

## Updates

The app checks GitHub for new versions on startup. You can also check manually from **Help → Check for Updates...**. If a newer version is available, the app asks whether to open the GitHub release/download page.

## Basic workflow

### Read the radio

1. Connect the programming cable.
2. Start **RT-950/950Pro Editor**.
3. Go to **Radio → Read Radio**.
4. Select the COM port.
5. Click **Read Radio**.

### Edit channels and settings

- Use the channel grid for channel memory.
- Use the right-side channel editor for the selected channel.
- Use the zone selector to switch between zones.
- Use the **Edit** menu for VFO, Optional Features, DTMF, APRS, modulation, and encryption defaults.
- Hover or click the **ⓘ** icons for field explanations.

### Write the radio

1. Select the radio tab you want to write.
2. Go to **Radio → Write Radio**.
3. Select the COM port.
4. Click **Write Radio**.
5. Wait for the backup, write, and verify steps to complete.

## Boot picture workflow

The boot picture editor prepares the correct image format and uploads it directly to the radio.

1. Go to **Tools → Boot Picture**.
2. Click **Open Image**.
3. Drag and zoom the image inside the 240 × 320 frame.
4. Click **Save BMP** to save the prepared image, or **Upload to Radio** to send it to the radio.
5. Power-cycle the radio if the new boot picture does not appear immediately.

## Documentation

- [User Guide](docs/USER_GUIDE.md)
- [Troubleshooting](docs/TROUBLESHOOTING.md)
- [Backup and Restore](docs/BACKUP_AND_RESTORE.md)
- [Release Checklist](docs/GITHUB_RELEASE_CHECKLIST.md)
- [Maintainer Release Upload Script](docs/GITHUB_RELEASE_UPLOAD_SCRIPT.md)
- [Legal / Radio Compliance Notes](docs/LEGAL_AND_RADIO_COMPLIANCE.md)
- [Antivirus False Positives](docs/ANTIVIRUS_FALSE_POSITIVES.md)
- [Changelog](CHANGELOG.md)

## Safety notes

- Always read/backup the radio before writing.
- Do not power off the radio during read/write or boot image upload.
- Make sure programmed frequencies comply with your license and local laws.
- This project is not affiliated with Radtel.

## Support

- GitHub issues: https://github.com/cruzerdlc/RT-950-950Pro-Editor/issues
- Project page: https://github.com/cruzerdlc/RT-950-950Pro-Editor
- Donate: https://cash.app/$cruzerdlc

## License

MIT License. See [LICENSE.txt](LICENSE.txt).


## Developer build note

For building the clean portable Windows release, run `BUILD_CLEAN_PORTABLE_WINDOWS.bat`. If Python is not installed, the build script now offers to install Python 3.12 with `winget`. End users of the finished portable ZIP do not need Python.


## v0.7.0-pre83 Optional Layout Height Fix

- Fixed Optional Features layout overlap in opened `.dat` tabs.
- Restored APRS Info editor for opened `.dat` files.
- RepeaterBook import is hidden until finished.

## v0.7.0-pre73 Zone Write Save Fix

- Radio Read **Save As .dat** now uses a bundled internal RT-950PRO template and only asks where to save.
- **Write Radio** now applies edited zone names to the radio zone block.
- Zone names match the radio style: `ZoneOne`, `ZoneTwo`, `ZoneThree`, etc.

## v0.7.0-pre73 Modulation CSV + Zones

- Added **File > Download CSV templates...** to save channel and zone CSV templates plus a detailed field guide.
- Added **Edit > Zones...** so each zone name can be edited from inside the app.
- Added zone-name CSV import/export from the Zones editor.
- Kept the v0.7.0-pre73 GitHub update-checker fix that reads prerelease releases as well as `/releases/latest`.


v0.7.0-pre73 notes:
- Fixed Zone editor Apply Name crash.
- Moved modulation CSV import/export/template workflow to Edit > FM/AM/SSB Modulation.
- Removed zone import/export buttons from the Zone editor.


### v0.7.0-pre83 notes
- The displayed app version now comes from the bundled VERSION file.
- Radio > Write Radio can use a Radio Read tab or an opened .dat tab as the source.
- Keypad Lock writes include diagnostics showing the requested value and outgoing optional_features byte.


### Factory CPS packet capture

Use `Tools > Virtual COM Setup` and `Tools > Packet Capture Tool` to capture the original factory CPS talking to the radio through a proxy bridge. This is useful when a radio behavior is not stored in the normal `.dat` or Radio Read backup data.


### v0.7.0-pre83 notes

- Keypad Lock radio offset corrected to `optional_features +0x1B` from clean factory CPS ON/OFF proxy captures.
- The old `+0x27` value was the `.dat` stream/logical position, not the radio write byte.


### v0.7.0-pre90 notes
- Write Radio screen cleanup: removed the duplicate Open Save Folder button from the options area and kept the existing action-row button.
- Verify after write and optional pre-write backup remain available.

### v0.7.0-pre89 notes

- Subaudio ScanSave and Cur Work Zone A/B/C radio write mapping fixes.
- Write Radio now includes a Save pre-write backup capture option and Open Save Folder button.

### v0.7.0-pre93 notes

- Channel rows now include a checkbox column for easier multi-select.
- Selecting multiple rows and pressing **Edit channel** opens the new bulk editor.
- The bulk editor fills in values that are the same across all selected channels and shows `<mixed>` where values differ.
- Only changed bulk-editor fields are applied to all selected channels.
- The single-channel editor now closes reliably with **Close**, **Esc**, or the window X.
- Microsoft Defender may flag unsigned PyInstaller builds with heuristic labels such as Wacatac. This release keeps the clean onedir build, UPX disabled, and source available for review. Submit suspected false positives to Microsoft Security Intelligence before distributing broadly.

See `DEFENDER_FALSE_POSITIVE_NOTES.md` for notes on Microsoft Defender heuristic false-positive handling.
