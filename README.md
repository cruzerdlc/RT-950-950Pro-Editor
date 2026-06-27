# RT-950/950Pro Editor

**RT-950/950Pro Editor** is a Windows application for programming and managing the Radtel RT-950 / RT-950Pro radio.

Made by **KK4OXN**.

Project: https://github.com/cruzerdlc/RT-950-950Pro-Editor  
Donate: https://cash.app/$cruzerdlc

## Download and run

This app is intended to be delivered as a ready-to-run Windows executable. End users do **not** need Python, build scripts, or developer tools.

1. Download the latest release package.
2. Extract the ZIP if needed.
3. Run:

```text
RT-950_950Pro_Editor.exe
```

4. Connect the RT-950 / RT-950Pro programming cable.
5. Use **Radio > Read Radio** to read the radio.
6. Edit channels or settings.
7. Use **Radio > Write Radio** to write changes back to the radio.

## First-time setup

Most users only need the radio programming cable driver installed. Many RT-950 / RT-950Pro programming cables appear in Windows as a CH340 / CH341 USB serial device.

Before using the app:

- Install the USB serial driver for your programming cable if Windows does not detect it automatically.
- Confirm the cable appears in Windows Device Manager under **Ports (COM & LPT)**.
- Note the COM port number, such as `COM5`.
- Keep the radio powered on and connected during read/write operations.

## Main features

- Direct radio **Read Radio** and **Write Radio** over COM port.
- Automatic pre-write backup option.
- Optional read-back verification after write.
- Multi-tab channel editor.
- Channel view selector for **All Channels** or a specific zone.
- Bulk channel edit with checkbox selection.
- Zone editor.
- VFO / CAT control settings editor.
- Optional Features editor.
- DTMF editor.
- APRS editor.
- FM/AM/SSB Modulation editor.
- Encryption Presets / Defaults editor.
- Boot Picture tool.
- CSV import/export and templates.
- Light mode and dark mode.
- Startup splash screen with project links.

## v0.8.10 changes

- Refined COM/USB cable read/write sizing for the channel block.
- Changed COM/USB full-write channel span from `0x8000` to `0x7C00`.
- Changed COM/USB read channel span to the matching `0x7C00` size.
- The editor still exposes 990 real USB/factory channel slots; the final 64 bytes are preserved/padded alignment bytes.
- Bluetooth/BLE read and write behavior is unchanged from the confirmed-good v0.8.8/v0.8.9 path.

## v0.8.9 changes

- UI-only update on top of v0.8.8.
- Enlarged the startup splash screen so the Close button is visible again.
- Increased the Write Radio window height so the bottom progress/log/status area is no longer clipped.
- Kept v0.8.8 Bluetooth/BLE read/write behavior unchanged.

## v0.8.8 changes

- Reworked Bluetooth/BLE clone operations toward the working CHIRP driver model.
- Added a CHIRP-style BLE clone map with a 0x7800 / 960-channel segment and preserved 64-byte channel gap.
- BLE writes from a Radio Read tab now skip the extra pre-write safety read and write only full full CHIRP-compatible clone payload.
- USB serial read/write behavior is unchanged.

## v0.8.6 changes

- Changed Bluetooth/BLE reads to use fast reference-style timing.
- Removed the extra slow BLE pacing that could let the radio drop out of programming mode during long reads.
- Reduced BLE empty-read retries to short, quick retries instead of long waits.
- Reduced BLE per-block timeout so a missed notify burst retries faster.
- Kept BLE dynamic SEND challenge/key negotiation from v0.8.5.
## v0.8.1 changes

- Added visible Bluetooth/BLE attribution in the startup splash screen.
- Added Bluetooth/BLE attribution to the About screen.
- Added Bluetooth/BLE attribution in the Read Radio and Write Radio windows.
- Kept experimental BLE read/write logic from v0.8.0 intact.

## v0.8.0 changes

- Increased the default main app window size so the full left navigation rail fits better.
- Increased the minimum app window size to reduce clipped sidebar actions.
- Widened the left navigation rail so the dark/light mode button text fits cleanly.

## v0.7.4 changes

- Fixed Read Radio and Write Radio popup header/banner areas so they follow dark mode.
- Fixed Write Radio option checkboxes so they no longer highlight white in dark mode.
- Maintainer Windows build files remain included in the source package, while end-user documentation remains focused on running the executable.

## v0.7.1 changes

- Switched release numbering from prerelease-style tags to normal version tags starting at **v0.7.1**.
- Cleaned end-user documentation so it no longer tells normal users to run build scripts.
- Replaced the native top menu with a themed in-app command bar so **File / Radio / Edit / View / Tools / Help** follow light/dark mode instead of staying white.
- Fixed channel/grid alternating row colors so dark mode no longer shows white rows.
- Kept the backend radio protocol, read/write logic, CAT/VFO handling, DAT/CSV processing, and validation logic intact.

## Recommended workflow

1. Start the app.
2. Read the radio with **Radio > Read Radio**.
3. Save or keep the automatic backup.
4. Edit channels/settings.
5. Write the radio with **Radio > Write Radio**.
6. Use verification when you want the app to read back and compare the write.

## Antivirus note

This is a free community project. The app may be flagged by Microsoft Defender or other antivirus tools because the executable is currently unsigned and has limited reputation. This does not automatically mean the app is malicious, but users should only download it from the official project release page and should not run copies from unknown sources.

Source is available for review. If an antivirus product incorrectly flags the app, the file can be submitted to that vendor as a false positive.

## Safety and legal note

Always verify frequencies, tones, offsets, and transmit permissions before writing to the radio. Follow your local radio regulations.


## Bluetooth/BLE read and write

Version v0.8.0 added experimental Bluetooth/BLE read and write. Version v0.8.1 adds visible attribution for the BLE reference work.  In **Read Radio** or **Write Radio**, choose **Bluetooth / BLE**, click **Scan BLE**, select the RT-950/950Pro radio, and then read or write.

Bluetooth write is experimental. Keep a known-good backup, keep the radio powered on, and do not interrupt the write. The app still uses the same RT-950/950Pro read/write backend; Bluetooth only replaces the USB serial byte transport.

The BLE transport includes MIT-licensed reference work by Nivin Goonesekera (VK3NWG), with portions by Nathan G. Barguss (2E0NBS). See `THIRD_PARTY_NOTICES.md`.
