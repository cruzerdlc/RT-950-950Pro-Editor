# RT-950/950Pro Editor User Guide

## 1. What this app does

RT-950/950Pro Editor lets you read, edit, and write RT-950 / RT-950Pro radio programming from a Windows PC. It also includes a boot picture editor and stock channel presets.

## 2. First-time setup

1. Download the Windows release ZIP or installer.
2. Extract the ZIP or run the installer.
3. Run `RT-950_950Pro_Editor.exe`.

## 3. Reading the radio

1. Connect the USB programming cable.
2. Turn the radio on.
3. In the app, choose **Radio → Read Radio**.
4. Select the COM port, usually something like `COM5` or `USB-SERIAL CH340`.
5. Click **Read Radio**.
6. A new **Radio Read** tab opens when the read completes.

The app saves automatic capture backups in your Windows AppData folder.

## 4. Editing channels

1. Select a channel row.
2. Use the right-side **Channel editor** panel.
3. Changes save live inside the open tab.
4. Use the zone dropdown to switch between zones.
5. Right-click the channel list to cut/copy/paste rows.
6. Drag column headers to change column order.

## 5. Writing the radio

1. Select the Radio Read tab you want to write.
2. Choose **Radio → Write Radio**.
3. Select the COM port.
4. Click **Write Radio**.
5. The app automatically:
   - reads a fresh backup,
   - builds the write image,
   - writes the radio,
   - reads back and verifies.

Do not unplug the cable or power off the radio while writing.

## 6. Edit menu settings

The **Edit** menu opens in-app tabs for deeper radio settings:

- **VFO Mode**: VFO A/B/C frequency-mode settings.
- **Optional Features**: radio behavior, display, scan, work modes, zones, PF keys, and long-press key assignments.
- **DTMF Codes**: PTT-ID, DTMF side tone, speed, and code groups.
- **FM/AM/SSB Modulation**: broadcast and shortwave memory/settings.
- **APRS Info**: APRS switch, GPS, callsign, SSID, paths, beaconing, units, and symbol settings.
- **Encryption Presets / Defaults**: encryption/scrambler display defaults and presets used by the editor.

Most fields include an **ⓘ** information icon. Hover or click for descriptions.

## 7. Stock presets

Use **File → Open Stock Config** to import built-in preset channel lists.

When importing, choose whether to:

- **Overwrite** the selected zone starting at channel 1, or
- **Append** to the end of the used channels in the selected zone.

## 8. Boot picture editor

1. Choose **Tools → Boot Picture**.
2. Click **Open Image**.
3. Drag the image inside the dashed 240×320 frame.
4. Use the mouse wheel to zoom.
5. Click **Save BMP** to save a compatible 24-bit BMP.
6. Click **Upload to Radio** to write the boot image to the radio.

The boot image upload was confirmed using 150 acknowledged image pages. The radio does not support reliable boot-image readback through the tested command, so there is no “load from radio” workflow.

## 9. Backups

The app creates automatic backups before normal writes. Keep backups if you are testing new changes.

## 10. Best practices

- Read the radio before every major edit.
- Save/export CSVs for channel lists you care about.
- Write a small change first and verify before big updates.
- Keep a known-good backup from the factory CPS and from this editor.
- Program only frequencies you are authorized to use.
