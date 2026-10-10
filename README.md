<p align="center">
  <img src="rt950_950pro_icon.png" alt="RT-950/950Pro Editor icon" width="128">
</p>

<h1 align="center">RT-950/950Pro Editor</h1>

<p align="center">
  A native Windows programming application for the Radtel RT-950 and RT-950Pro radios.
</p>

<p align="center">
  <img alt="Version 1.1.2" src="https://img.shields.io/badge/version-1.1.2-0078D4">
  <img alt="Windows 10 and 11" src="https://img.shields.io/badge/Windows-10%20%7C%2011-0078D4">
  <img alt="License MIT" src="https://img.shields.io/badge/license-MIT-green">
</p>

<p align="center">
  <strong>Current stable release: v1.1.2</strong><br>
  Created by <strong>KK4OXN</strong>
</p>

---

## About the project

RT-950/950Pro Editor is a community-developed alternative to the original Radtel CPS software. It provides a larger, modern interface for editing memory channels, zones, radio settings, APRS information, DTMF data, modulation memories, boot pictures, and other supported radio options.

The application is written in native C# with WinUI 3. It communicates directly with the radio through USB/serial or Bluetooth Low Energy and can open, edit, save, and write compatible Radtel CPS `.dat` files. The installed application does not require Python or a separate backend executable.

This project is independent community software and is not produced, sponsored, endorsed, or supported by Radtel.

## What's new in v1.1.2

- Added all 40 standard United States CB channels as a bundled stock configuration.
- Configured matching transmit and receive frequencies in AM mode.
- Preserved the correct historical frequency ordering for CB channels 23, 24, and 25.
- Added automated validation for the complete U.S. CB channel plan.
- Retains the native radio, `.dat`, selective stock-import, channel-editing, cloning, and installer improvements introduced in v1.1.1.

See [CHANGELOG.md](CHANGELOG.md) for earlier release history.

## Main features

### Radio programming

- Read and write through a USB programming cable and Windows COM port.
- Read and write through Bluetooth/BLE on compatible radios.
- Optional fresh backup before a write.
- Post-write readback and verification with clear diagnostic details.
- Native protocol handling with no Python backend.
- Detailed binary transcripts and application logs for troubleshooting.

### Channel and zone editing

- View all 990 memory slots in a searchable, spreadsheet-style table.
- Edit a field directly with a single click or open the full editor with a double-click.
- Automatically apply field edits to the active workspace.
- Select, move, copy, cut, paste, delete, and reorder channels.
- Move channels up or down while preserving valid slot numbering.
- Customize column order and width.
- View channels by zone and rename or clear zones.
- Edit RX/TX frequencies, CTCSS/DCS tones, power, bandwidth, scan behavior, busy lockout, PTT ID, scrambler, encryption, FHSS, modulation, and TX Enable.
- Validate frequency formatting and radio name-length limits.

### Radio settings

- VFO/CAT settings.
- Optional radio features.
- DTMF codes.
- FM, AM, and SSB modulation memories.
- APRS identity, SSID, position, beacon, and routing settings.
- Radio information and zone configuration.
- Custom 240 × 320 boot-picture preparation and USB/COM upload.

### Files and imports

- Open, edit, and save compatible OEM Radtel `.dat` files.
- Save a configuration read directly from the radio as a `.dat` file.
- Load a saved `.dat` file and write it to another radio without requiring a preliminary radio read.
- Import and export channel CSV files.
- Open CHIRP-compatible CSV files.
- Import selected entries—or all entries—from bundled stock configurations.
- Choose the destination zone and either a starting channel or the next available channel.
- Import selected RadioReference and RepeaterBook search results.
- Export channel lists and work with the included channel, zone, and modulation templates.

### Application experience

- Native WinUI 3 interface with system, light, and dark themes.
- Multilingual navigation and common controls.
- Built-in automatic update check that only prompts when a newer version is available.
- Manual update check from the navigation menu without leaving the current page.
- Persistent application settings and secure RepeaterBook token storage.
- Installer-created Start menu and optional desktop shortcuts.

## Installation

1. Open the repository's [Releases](https://github.com/cruzerdlc/RT-950-950Pro-Editor/releases) page.
2. Download the newest x64 installer, currently:

   ```text
   RT950_950Pro_Editor_Setup_v1.1.2_x64.exe
   ```

3. Close the editor if an older version is running.
4. Run the installer and select the installation location. The default is the standard 64-bit Program Files directory.
5. Choose whether to create a desktop shortcut.
6. The installer can optionally trust the included KK4OXN development signing certificate. Only select this option when the installer came from the official project release.

The installer includes the application, the self-contained .NET runtime, and the required Microsoft Windows App Runtime installer. End users do not need to install Python, .NET, or the retired `RT950Backend.exe` separately.

Installing over an older version removes retired Python/PyInstaller backend files while preserving normal user data stored under the user's application-data folder.

## System requirements

- Windows 10 or Windows 11, 64-bit.
- A Radtel RT-950 or RT-950Pro radio.
- A compatible USB programming cable for USB/COM programming, or a Bluetooth-capable Windows PC for BLE programming.
- The correct Windows serial driver for the cable. Many compatible cables use a CH340-family driver.

## Quick start

### Read a radio

1. Connect the programming cable and turn on the radio, or enable Bluetooth on the radio and PC.
2. Close the OEM CPS, CHIRP, phone app, serial terminals, and anything else that could be using the connection.
3. Open **Dashboard > Read Radio**.
4. Choose **USB / Serial COM Port** or **Bluetooth / BLE**.
5. Select the COM port or scan for the Bluetooth radio.
6. Start the read and keep the radio connected until it finishes.

### Edit channels and settings

- Use **Dashboard** for the complete radio workspace.
- Use **Memory Channels** for a full-height channel table.
- Single-click a supported cell to edit it directly.
- Double-click a row to open the complete channel editor.
- Use the other navigation pages to edit VFO, optional features, DTMF, modulation, APRS, and boot-picture data.

Edits are applied automatically to the active workspace. Use **Save .dat** to keep a portable backup before closing the application.

### Write a radio

1. Open **Dashboard > Write Radio**.
2. Choose USB/COM or Bluetooth/BLE and select the radio.
3. Optionally select **Create a fresh backup before writing**.
4. Confirm that the connected radio will be overwritten.
5. Start the write and do not disconnect or power off the radio.
6. Review the completion and verification result.

## Bluetooth/BLE notes

Bluetooth/BLE programming uses the Windows Bluetooth stack. Keep the radio near the computer, disconnect it from the Radtel phone application before scanning, and avoid powering it off during a read or write.

If Windows can see the radio but cannot open its notification channel, disconnect the radio from other devices, toggle Bluetooth off and on, power-cycle the radio, and scan again. Removing an old saved `walkie-talkie` device from Windows Bluetooth settings may also help.

Boot-picture upload is supported through USB/COM only.

## RadioReference and RepeaterBook

The integrated importers provide search progress, result previews, multi-row selection, zone targeting, duplicate handling, and starting-channel placement.

RadioReference searches support ZIP, city/state, and county/state workflows. Unsupported digital modes can be listed for monitoring but are not decoded by the radio.

RepeaterBook requires each user to generate a personal `rbuapp_` application token. The editor does not embed or redistribute a shared token. Remembered tokens are protected with Windows credential protection when available.

Review every imported frequency, tone, offset, mode, and transmit permission before writing it to a radio.

## Stock configurations

Open **Stock Configs** from the navigation menu, choose a configuration, review its contents, select the channels to import, and then choose the destination zone and starting location.

The included presets cover multiple countries and services, including:

- U.S. CB — all 40 AM channels with matching TX/RX frequencies.
- U.S. FRS/GMRS, GMRS repeaters, MURS, NOAA Weather Radio, calling frequencies, amateur simplex, aviation, marine, railroad, and interoperability channels.
- Additional Canadian, European, Australian, and New Zealand frequency groups.

Stock lists are provided as a convenience. Frequencies, channel plans, licensing requirements, equipment certification, transmit power, and operating permissions vary by location and can change. Confirm the applicable rules before transmitting.

## Backups and recovery

The application stores logs, diagnostic captures, and optional radio backups under:

```text
C:\Users\<your-name>\AppData\Roaming\RT950ProEditor
```

Recommended practice:

1. Read and save the original radio configuration before making changes.
2. Keep at least one known-good `.dat` file.
3. Enable the fresh-backup option before an important write.
4. Export important channel lists to CSV.
5. Read the radio after major changes and confirm the results.

Do not publicly upload a codeplug containing private callsigns, APRS coordinates, names, frequencies, API tokens, or other sensitive information.

## Troubleshooting and bug reports

For bugs, feature requests, and questions, [open a GitHub issue](https://github.com/cruzerdlc/RT-950-950Pro-Editor/issues).

Please include:

- Application version.
- Windows version.
- Radio model and firmware version, when known.
- USB/COM or Bluetooth/BLE connection type.
- Programming-cable or serial-adapter type and COM port, when relevant.
- Exact reproduction steps and the displayed error.
- Relevant log or diagnostic transcript.
- Whether a readback was performed after the write.

Logs are stored under `%APPDATA%\RT950ProEditor\logs`. Review files before posting them publicly.

## Building from source

The current application is native C# and WinUI 3. Python and PyInstaller are not part of the public application build.

Prerequisites include the .NET 8 SDK, a compatible Windows SDK, and the Windows App SDK dependencies restored through NuGet.

From the `RT950` directory:

```powershell
dotnet build .\WinUI3\RT950ProEditor.WinUI\RT950ProEditor.WinUI.csproj -c Debug -p:Platform=x64
```

For a native x64 release publish:

```powershell
dotnet publish .\WinUI3\RT950ProEditor.WinUI\RT950ProEditor.WinUI.csproj -c Release -r win-x64 --self-contained true -p:Platform=x64 -p:WindowsAppSDKSelfContained=false
```

See [WinUI3/DEPLOYMENT.md](WinUI3/DEPLOYMENT.md) for packaging details.

## Documentation

Additional documentation is available in the [`docs`](docs) folder:

- [User guide](docs/USER_GUIDE.md)
- [Backup and restore](docs/BACKUP_AND_RESTORE.md)
- [Troubleshooting](docs/TROUBLESHOOTING.md)
- [Protocol notes](docs/PROTOCOL_NOTES.md)
- [RadioReference import](docs/RADIOREF_IMPORT.md)
- [RepeaterBook import](docs/REPEATERBOOK_IMPORT.md)
- [Automatic updates](docs/AUTO_UPDATE.md)
- [Diagnostic logging](docs/DIAGNOSTIC_LOGGING.md)
- [Legal and radio compliance](docs/LEGAL_AND_RADIO_COMPLIANCE.md)
- [Antivirus and reputation warnings](docs/ANTIVIRUS_FALSE_POSITIVES.md)

## Safety and legal notice

You are responsible for operating the radio legally and safely.

- Verify frequency allocations, equipment requirements, and license conditions in your jurisdiction.
- Do not transmit on receive-only, aviation, public-safety, marine, government, or other restricted frequencies unless specifically authorized.
- Confirm frequencies, tones, offsets, modulation, bandwidth, TX Enable, and power before writing.
- Keep a backup before important writes.
- Do not interrupt a radio write or boot-picture upload.

This software is provided without warranty. Use it at your own risk.

## Credits and licensing

RT-950/950Pro Editor was created by **KK4OXN**.

Bluetooth/BLE support uses adapted MIT-licensed reference work by **Nivin Goonesekera (VK3NWG)**, with portions based on work by **Nathan G. Barguss (2E0NBS)**. See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for attribution and license details.

This project is licensed under the [MIT License](LICENSE.txt).

## Support the project

The editor is developed and maintained for the radio community. Optional support helps with testing equipment, development time, and future improvements.

- **Patreon:** [Become a supporter at patreon.com/KK4OXN](https://patreon.com/KK4OXN)
- **Cash App:** [Donate to $cruzerdlc](https://cash.app/$cruzerdlc)

<p align="center">
  <a href="https://cash.app/$cruzerdlc">
    <img src="cashapp_qr.png" alt="Donate to $cruzerdlc with Cash App" width="220">
  </a>
</p>
