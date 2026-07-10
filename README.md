# RT-950/950Pro Editor

A modern programming and maintenance tool for the Radtel RT-950 / RT-950Pro radio.

This project is intended to provide a cleaner, easier-to-use alternative to the factory CPS while preserving compatibility with the radio’s known programming behavior. It includes channel editing, zone management, settings tools, CSV import/export, Bluetooth/BLE support, COM/USB programming, and boot-picture upload support.

---

## Current Release

**Version:** v0.8.33  
**Status:** Stable build  
**Recommended for:** Normal COM/USB and Bluetooth/BLE codeplug editing

---

## Main Features

### Channel Editor

- Edit radio channels in a spreadsheet-style interface.
- Supports up to 990 channel slots for COM/USB workflow.
- Supports the stable 960-channel Bluetooth/BLE workflow.
- Edit RX frequency, TX frequency, tones, power, bandwidth, modulation-related fields, busy lockout, work modes, and other supported channel options.
- Copy, paste, reorder, and manage channel rows.
- Improved frequency precision for 6.25 kHz steps.

### Zone Management

- Supports zones 1 through 10.
- Rename zones.
- Assign and organize channels by zone.
- Bluetooth/BLE zone-name writing is supported using the separate C000 zone-name block.

### COM/USB Read and Write

- Read from the radio using a USB programming cable.
- Write edited codeplugs back to the radio.
- Verify radio data after write when applicable.
- Uses the known RT-950/950Pro programming handshake and memory layout.

### Bluetooth/BLE Read and Write

- Read and write the radio over Bluetooth/BLE.
- Uses the stable BLE programming path based on the known RT-950 BLE behavior.
- Supports channel and zone-name workflows.
- Normal BLE codeplug behavior is unchanged in this release.

### CSV Import and Export

- Export channel data to CSV.
- Import channel data from CSV.
- Useful for editing channels in spreadsheet software.
- Supports append/overwrite workflows where available.

### Boot Picture Tool

- Convert and upload boot pictures to the radio.
- Supports COM/USB boot-picture upload.
- Converts images to the radio’s required display format.
- Uses the factory-captured A5 boot-picture protocol in v0.8.33.

### Presets and Templates

- Includes preset/template support for easier setup.
- Useful for building repeatable radio configurations.

### User Interface

- Modernized Windows-style interface.
- Dark mode support.
- Multi-tab layout.
- Language menu support.
- Cleaner dialogs and improved workflow organization.

---

## Important Safety Notes

Writing to a radio always carries risk. Use this software carefully.

Before writing:

1. Read the radio first.
2. Save a backup of the original radio image.
3. Keep the radio powered during the full write process.
4. Do not disconnect the USB cable or power off the radio during programming.
5. Verify your frequencies and settings before transmitting.

The user is responsible for following local radio laws, frequency authorization, band limits, and licensing requirements.

---

## Frequency Range Behavior

The editor includes validation for known RT-950/950Pro operating ranges. Some fields may allow an override warning for out-of-range entries, but the radio may refuse the value, behave unpredictably, or fail to transmit/receive as expected.

Only enter frequencies you are authorized to use.

---

## Bluetooth/BLE Notes

Bluetooth/BLE channel and zone programming is supported.

BLE boot-picture upload is **not enabled in this stable release**. Experimental BLE boot-picture work exists separately and should not be treated as stable.

For normal use, v0.8.33 keeps the working BLE read/write path unchanged.

---

## Boot Picture Upload Notes

Boot-picture upload over COM/USB was fixed in v0.8.33 by matching the factory CPS behavior captured from a serial sniffer session.

The factory CPS does not wait for a normal ACK after the `D` boot-picture command. Instead, it enters a separate A5-framed boot-picture protocol.

This release follows that factory behavior.

---

## Recommended Workflow

### First-time use

1. Connect the radio using a known-good USB programming cable.
2. Open the editor.
3. Select the correct COM port.
4. Read from the radio.
5. Save a backup.
6. Make edits.
7. Write back to the radio.
8. Verify the result.

### Bluetooth/BLE use

1. Make sure the radio is in the correct Bluetooth/BLE programming mode.
2. Scan for the radio.
3. Connect.
4. Read from the radio first.
5. Save a backup.
6. Edit and write carefully.

---

## Project Status

This software is under active development.

Stable areas:

- COM/USB channel read/write
- Bluetooth/BLE channel read/write
- Zone-name read/write
- CSV import/export
- Frequency precision fixes
- COM/USB boot-picture upload as of v0.8.33

Experimental or disabled areas:

- BLE boot-picture upload
- Boot-picture readback from radio
- Unknown factory-only settings that have not yet been fully mapped

---

## Credits

Bluetooth/BLE protocol work is based in part on MIT-licensed research and code by:

- Nivin Goonesekera, VK3NWG
- Nathan G. Barguss, 2E0NBS

Additional RT-950/950Pro protocol behavior was validated through testing, CHIRP module review, and serial sniffer captures.

---

# Release Notes

## v0.8.33 - Factory Boot Picture Upload Protocol

This release fixes COM/USB boot-picture upload by matching the factory CPS protocol captured from a serial sniffer session.

### Fixed

- Fixed Boot Picture upload over COM/USB.
- The editor now follows the factory CPS boot-picture sequence:
  - `PROGRAMBT9000U`
  - radio ACK `06`
  - `D`
  - A5-framed boot-picture setup packets
  - A5-framed image page writes
  - final A5 `Over` frame
- Fixed the previous behavior where the app waited for a direct ACK after `D`.

The factory CPS does not wait for a direct ACK after `D`. It waits briefly, then starts the A5 boot-picture protocol.

### Notes

- Boot Picture upload is COM/USB only in this stable release.
- Bluetooth/BLE boot-picture upload remains disabled in the stable build.
- Normal Bluetooth/BLE channel, zone, and settings read/write behavior is unchanged.
- This build keeps the previously working BLE codeplug path untouched.

### Safety

Boot-picture writing changes a display image area of the radio. Do not power off or disconnect the radio during upload.

Recommended procedure:

1. Use a reliable USB programming cable.
2. Keep the radio powered during the entire upload.
3. Wait for the app to report completion before disconnecting.

---

## v0.8.32

- Tested an alternate boot-picture upload session entry method.
- Attempted factory-style identification before boot-picture upload.
- Superseded by v0.8.33 after serial sniffer protocol capture.

---

## v0.8.31

- Added another COM/USB boot-picture upload attempt using a fuller CPS-style session.
- Still expected behavior that did not match the factory CPS.
- Superseded by v0.8.33.

---

## v0.8.30

- Restored Boot Picture upload window functionality.
- Added image conversion for the radio boot-picture format.
- BLE boot-picture upload remained disabled.

---

## v0.8.29

- Fixed 6.25 kHz frequency precision display and write behavior.
- Improved handling of frequencies such as:
  - `462.56250`
  - `154.45625`
  - `151.00625`

---

## v0.8.28

- Added out-of-band warning and user override behavior.
- Invalid text and non-numeric frequency entries remain blocked.
- User must accept responsibility before allowing out-of-range values.

---

## v0.8.27

- Fixed Bluetooth/BLE zone-name writing.
- Added the correct C000 zone-name write behavior when Zones are enabled.
- Normal BLE channel writing remained unchanged.

---

## v0.8.24 - v0.8.26

- Removed unreliable Fast BLE write behavior.
- Returned BLE writing to the stable full-payload method.
- Improved BLE write reliability and pacing.
- Continued work on BLE zone-name write behavior.

---

## v0.8.21

- Added CB band support:
  - `26.965 - 27.405 MHz`

---

## v0.8.20

- Added 49 MHz range support:
  - `49 - 53 MHz`

---

## v0.8.19

- Split RX and TX frequency validation.
- RX allows broader receive ranges.
- TX is limited to known transmit-capable ranges unless overridden where supported.

---

## v0.8.18

- Added BLE zone-name read support.
- Added improved airband RX handling.

---

## v0.8.17

- Added language menu support:
  - English
  - Spanish
  - French
  - Portuguese
  - German
  - Italian
  - Chinese Simplified
  - Chinese Traditional
  - Japanese
  - Korean
  - Arabic
  - Hindi
  - Russian

---

## v0.8.10

- Fixed COM/USB channel memory span handling.
- Updated COM/USB workflow to support the 990-slot channel layout.
- Kept BLE workflow unchanged.

---

## Disclaimer

This project is not affiliated with Radtel.

Use at your own risk. Always keep a known-good backup of your radio before writing changes.