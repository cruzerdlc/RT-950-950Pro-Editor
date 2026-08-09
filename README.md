<p align="center">
  <img src="rt950_950pro_icon.png" alt="RT-950/950Pro Editor icon" width="128">
</p>

<h1 align="center">RT-950/950Pro Editor</h1>

<p align="center">
  <img src="https://img.shields.io/badge/version-v0.8.40-blue" alt="Version v0.8.40">
  <img src="https://img.shields.io/badge/platform-Windows-0078D4" alt="Windows">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License"></a>
</p>

<p align="center">
  A community-developed Windows programming application for the Radtel RT-950 and RT-950Pro radios.
</p>

<p align="center">
  <strong>Current stable release: v0.8.40</strong><br>
  Created by <strong>KK4OXN</strong>
</p>

---

## About the project

RT-950/950Pro Editor is an alternative to the original Radtel CPS software. It provides a larger, easier-to-use interface for managing memory channels, zones, radio settings, APRS information, DTMF data, modulation memories, and other supported radio options.

The editor can work directly with the radio through a USB programming cable or Bluetooth Low Energy, and it can also open and save compatible Radtel CPS `.dat` files.

This project is independent community software and is not produced, sponsored,
endorsed, or supported by Radtel.

## Main features

- Read the radio through a USB/COM programming cable.
- Write edited data back to the radio with automatic backup and optional verification.
- Experimental Bluetooth/BLE reading and writing.
- Edit memory channels in a large spreadsheet-style table.
- View and edit channels by zone.
- Rename radio zones.
- Edit receive and transmit frequencies independently.
- Configure CTCSS and DCS tones.
- Set bandwidth, power, scan inclusion, scrambler, encryption, and other channel options.
- Enable or inhibit transmission on individual channels.
- Preserve AM modulation on supported non-airband frequencies.
- Edit VFO settings.
- Edit optional radio features.
- Edit DTMF codes.
- Edit FM, AM, and SSB modulation-memory data.
- Edit APRS settings, including callsign and supported beacon options.
- Import and export CSV channel lists.
- Open CHIRP-compatible CSV files as editable tabs.
- Import included stock configurations for common services and calling frequencies.
- Open, edit, and save compatible OEM `.dat` files.
- Upload a custom boot picture through the USB/COM cable.
- Light and dark interface themes.
- Multilingual application shell.
- Built-in update checking.
- Detailed logs and write transcripts for troubleshooting.

## What's new in v0.8.40

- Persistent rotating logs in `%APPDATA%\RT950ProEditor\logs`.
- **Help > Enable Detailed Logging** and **Help > Open Log Folder**.
- Startup and update-check diagnostics, with clearer update-failure reporting.
- Automatic redaction of personal RepeaterBook tokens in logs.

## Supported workflows

### Direct USB/COM programming

The recommended and most thoroughly tested method is a compatible USB programming cable that appears in Windows as a COM port.

The editor uses the recovered factory CPS communication protocol to:

1. Identify the connected radio.
2. Read the radio into a new editor tab.
3. Create a fresh pre-write backup.
4. Build a complete write image from the edited data.
5. Write the data to the radio.
6. Optionally read the radio back and verify the result.

### Bluetooth/BLE programming

Bluetooth/BLE read and write support is available for compatible RT-950/950Pro radios.

BLE writing uses the stable full-payload method. Because wireless programming can be interrupted by range, battery, or operating-system Bluetooth behavior, keep the radio close to the computer and do not power it off during a write.

Experimental BLE boot-picture upload is disabled.

### OEM `.dat` file editing

The editor can open and save compatible Radtel CPS `.dat` files. This is useful when you want to:

- Prepare a codeplug without connecting a radio.
- Exchange data with the OEM CPS.
- Keep dated configuration backups.
- Edit channel and settings data before writing with either application.

Legacy `.dat` channel records are automatically upgraded in memory when newer fields are required.

### CSV import and export

CSV support makes it easier to create, review, and exchange channel lists in spreadsheet applications.

The released application includes channel, modulation, and zone CSV templates, plus
stock configuration imports for common services and calling frequencies. Always
verify local laws and frequency assignments before transmitting.

## System requirements

### To run the released application

- Windows 10 or Windows 11 recommended.
- A Radtel RT-950 or RT-950Pro radio.
- A compatible USB programming cable for COM/USB programming, or a Bluetooth-capable PC for BLE programming.
- The correct USB serial driver for the cable. Many cables use a CH340-compatible driver.

End users running the released `.exe` do not need Python.

## Installation

1. Open the repository's [Releases page](https://github.com/cruzerdlc/RT-950-950Pro-Editor/releases).
2. Download the newest `RT950_vX.X.XX.zip` release.
3. Extract the entire ZIP file to a normal folder.
4. Run:

```text
RT-950_950Pro_Editor.exe
```

Do not run the executable directly from inside the ZIP archive.

Every release includes a SHA-256 checksum. Verify the downloaded archive against
the checksum published with that release before opening it.

Windows Defender or another antivirus program may warn about an unsigned community-built executable. Download releases only from the official project repository. See `DEFENDER_FALSE_POSITIVE_NOTES.md` and `docs/ANTIVIRUS_FALSE_POSITIVES.md` for more information.

## Quick start: read, edit, and write a radio

### 1. Connect the radio

1. Connect the programming cable to the radio and computer.
2. Turn the radio on.
3. Close the OEM Radtel CPS, CHIRP, serial terminals, and any other application that may be using the COM port.
4. In the editor, open **COM Port Connection** or choose **Radio > COM Port Settings**.
5. Select the radio's real COM port, such as `COM3` or `COM5`.

You can find the assigned port in Windows Device Manager under **Ports (COM & LPT)**.

### 2. Read the radio

Choose:

```text
Radio > Read Radio
```

The editor reads the radio and opens the result in a new tab. Keep the automatic backup created by the application.

### 3. Edit the configuration

Use the left navigation or the **Edit** menu to open the section you need:

- Memory Channels
- VFO Mode
- Optional Features
- DTMF Codes
- FM/AM/SSB Modulation
- Zones
- APRS Info
- Encryption Presets

For channel editing, select one or more rows and change the required fields. Review receive frequency, transmit frequency, tones, modulation, bandwidth, power, and TX Enable before writing.

### 4. Write the radio

Choose:

```text
Radio > Write Radio
```

For normal use, leave both of these options enabled:

- Create/read a fresh backup before writing.
- Verify the radio after writing.

Do not disconnect the cable, close the program, or power off the radio during a write.

## Bluetooth/BLE use

1. Turn on Bluetooth on the Windows computer.
2. Enable Bluetooth on the radio.
3. Disconnect the radio from the Radtel phone application so the radio can advertise.
4. Open **Read Radio** or **Write Radio**.
5. Choose **Bluetooth / BLE**.
6. Click **Scan BLE**.
7. Select the detected radio.
8. Start the read or write operation.

Keep a known-good backup and keep the radio near the computer throughout the operation.

## RadioReference import

The RadioReference/RadioRef importer supports ZIP, city/state, and county/state
searches, result preview and selection, mode filtering, CHIRP CSV and text export,
and direct import into the open radio file. Select a destination zone, choose append
or overwrite behavior, and set the starting channel as needed.

DMR, P25, NXDN, D-STAR, C4FM, and other unsupported digital modes may appear in
imported results, but the radio does not decode digital voice. Those entries are
treated as receive-only where appropriate.

## RepeaterBook import

RepeaterBook import uses each user's own personal `rbuapp_` application token; the
program does not include a shared embedded token. Tokens can be remembered using
Windows protection when available. Searches support relevant combinations of state,
city, ZIP, county, callsign, frequency, landmark, region, country, and mode.

Preview and selectively import results into a destination zone with append or
overwrite behavior. Digital-only repeaters can be imported as receive-only or
skipped. When published, valid analog input frequencies and tones are retained.
The application does not redistribute the RepeaterBook database.

## Working with stock configurations

The released application includes prepared stock configurations for common services
and frequency groups. To use one:

1. Open **File > Open Stock Config**.
2. Select the desired configuration.
3. Choose the destination zone or import behavior when prompted.
4. Review every imported channel before writing.

Stock lists are provided as a convenience. Frequencies, channel plans, licensing requirements, and transmit permissions can change and may differ by location.

## TX Enable and receive-only channels

The **TX Enable** field controls the radio's per-channel transmit-enable flag.

- Set **TX Enable** to ON for channels where transmission is intended and permitted.
- Set **TX Enable** to OFF for receive-only channels.
- Leaving the transmit-frequency field blank is also appropriate for many receive-only configurations.

After writing important receive-only channels, use verification or read the radio again to confirm the setting remained disabled. When testing, use a suitable 50-ohm dummy load and test equipment rather than transmitting over the air.

## AM channel support

AM can be selected on supported memory channels, including supported frequencies outside the normal aviation band. Version v0.8.35 and later preserve the AM flag when building the radio upload image.

The radio's actual receive capabilities still depend on its firmware and hardware.

## Custom boot picture

COM/USB boot-picture upload is supported.

1. Connect the radio through the real programming-cable COM port.
2. Open **Tools > Boot Picture**.
3. Load an image from the computer.
4. Adjust or preview it as needed.
5. Start the upload.
6. Wait until all 150 image pages have been acknowledged.
7. Power-cycle the radio to display the new boot image.

The factory-compatible completion sequence sends the final `Over` frame without expecting another response from the radio. A successful upload is determined by acknowledgment of all 150 image pages.

Boot-image readback is not enabled because tested radio firmware did not reliably return the existing image.

## Backups and recovery

The editor performs a fresh radio read before normal writes and stores backup captures in the application-data folder.

Typical location:

```text
C:\Users\<your-name>\AppData\Roaming\RT950ProEditor
```

Recommended backup routine:

1. Read and save the original radio configuration before making changes.
2. Keep at least one known-good OEM CPS `.dat` file.
3. Keep the editor's automatic pre-write captures.
4. Export important channel lists to CSV.
5. After a successful write and verification, keep a dated copy as a recovery point.

Do not publicly upload private codeplugs that contain personal callsigns, APRS coordinates, private frequencies, names, or other sensitive information.

## Troubleshooting

### The COM port is missing

- Reconnect the USB cable.
- Check Windows Device Manager under **Ports (COM & LPT)**.
- Install the correct USB serial driver.
- Close any other software using the port.
- Try another USB port.

### Radio read fails

- Confirm that the radio is powered on.
- Confirm that the correct COM port is selected.
- Close the OEM CPS and other serial applications.
- Reconnect the cable and power-cycle the radio.

### Radio write fails

- Do not immediately disconnect the radio.
- Save the displayed log.
- Power-cycle the radio and try reading it again.
- Restore a known-good backup when necessary.

### Verify reports differences

- Read the radio again and inspect the affected fields.
- Confirm that the radio firmware supports the edited option.
- Restore the pre-write backup if the result is incorrect.

### Boot picture does not appear

Power the radio completely off and back on after the upload.

### Antivirus warning

Unsigned PyInstaller applications can trigger reputation-based or heuristic antivirus warnings. Download only from the official repository and review the included antivirus documentation.

## Logs and bug reports

For bugs, feature requests, and questions, open an issue:

https://github.com/cruzerdlc/RT-950-950Pro-Editor/issues

Use the issue form that best fits the request. For support questions, include
the information below so maintainers can reproduce the problem.

Please include:

- App version.
- Windows version.
- Radio model.
- Connection type: USB/COM or BLE.
- USB serial adapter/cable type and COM port, when relevant.
- What you were trying to do and exact reproduction steps.
- Expected and actual results.
- Relevant log text or transcript. In v0.8.40, use **Help > Open Log Folder**.
- Whether the radio was read back after the write.

Do not post a private radio backup or codeplug publicly unless you have removed
callsigns, APRS coordinates, private frequencies, names, API tokens, and other
sensitive information.

## Documentation

Additional documentation is available in the `docs` folder:

- `USER_GUIDE.md`
- `BACKUP_AND_RESTORE.md`
- `TROUBLESHOOTING.md`
- `LEGAL_AND_RADIO_COMPLIANCE.md`
- `ANTIVIRUS_FALSE_POSITIVES.md`
- `RADIOREF_IMPORT.md`
- `REPEATERBOOK_IMPORT.md`

## Safety and legal notice

You are responsible for operating the radio legally and safely.

- Verify frequency allocations and license requirements in your country.
- Do not transmit on receive-only, aviation, public-safety, marine, government, or other restricted frequencies unless specifically authorized.
- Confirm tones, offsets, bandwidth, and transmit power before writing.
- Keep a backup before every write.
- Do not interrupt a radio write or boot-picture upload.

Users are responsible for confirming applicable licensing, frequency allocations,
and operating rules in their jurisdiction. This software is provided without
warranty. Use it at your own risk.

## Credits and licensing

RT-950/950Pro Editor was created by **KK4OXN**.

Bluetooth/BLE support uses adapted MIT-licensed reference work by **Nivin Goonesekera (VK3NWG)**, with portions based on work by **Nathan G. Barguss (2E0NBS)**. See `THIRD_PARTY_NOTICES.md` for attribution and license details.

This project is licensed under the [MIT License](LICENSE).

Project repository:

https://github.com/cruzerdlc/RT-950-950Pro-Editor

## Support the project

This project is developed and maintained for the radio community. Support is
optional and helps with testing equipment, development time, and future improvements.

### [Support on Patreon](https://www.patreon.com/KK4OXN)

**Support the project through Cash App:**

### [Donate with Cash App — $cruzerdlc](https://cash.app/$cruzerdlc)

<p align="center">
  <a href="https://cash.app/$cruzerdlc">
    <img src="cashapp_qr.png" alt="Donate to $cruzerdlc with Cash App" width="220">
  </a>
</p>
