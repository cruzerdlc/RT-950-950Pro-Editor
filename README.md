# RT-950/950Pro Editor

**RT-950/950Pro Editor** is a Windows application for programming and managing the Radtel RT-950 / RT-950Pro radio.

Made by **KK4OXN**.

Project: https://github.com/cruzerdlc/RT-950-950Pro-Editor  
Donate: https://cash.app/$cruzerdlc

> **Pre-production status:** read, write, settings edit, stock presets, and boot image upload have been tested during development. Keep backups and verify your own radio before depending on it.
>
> **Binary packaging note:** public builds are distributed as a clean portable Windows folder/ZIP instead of a one-file self-extracting EXE to reduce antivirus false positives.

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


## v0.7.0-pre45 Zone Write Save Fix

- Radio Read **Save As .dat** now uses a bundled internal RT-950PRO template and only asks where to save.
- **Write Radio** now applies edited zone names to the radio zone block.
- Zone names match the radio style: `ZoneOne`, `ZoneTwo`, `ZoneThree`, etc.

## v0.7.0-pre45 Modulation CSV + Zones

- Added **File > Download CSV templates...** to save channel and zone CSV templates plus a detailed field guide.
- Added **Edit > Zones...** so each zone name can be edited from inside the app.
- Added zone-name CSV import/export from the Zones editor.
- Kept the v0.7.0-pre45 GitHub update-checker fix that reads prerelease releases as well as `/releases/latest`.


v0.7.0-pre45 notes:
- Fixed Zone editor Apply Name crash.
- Moved modulation CSV import/export/template workflow to Edit > FM/AM/SSB Modulation.
- Removed zone import/export buttons from the Zone editor.
