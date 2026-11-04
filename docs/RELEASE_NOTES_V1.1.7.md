## RT-950/950Pro Editor v1.1.7

Version 1.1.7 is a focused reliability release that makes the saved radio connection behave consistently in both Read Radio and Write Radio.

### Highlights

- A saved **USB / Serial COM Port (nicFW950 custom firmware)** profile now remains selected after returning from Settings to the Dashboard.
- Write Radio honors the saved connection profile for factory `.dat` files and startup channel workspaces.
- The selected COM port and nicFW operating baud rate remain available in the Write Radio dialog.
- Loaded nicFW codeplugs still force the nicFW protocol, preventing them from being sent through incompatible factory USB or Bluetooth/BLE workflows.
- Invalid saved profile values safely fall back to factory USB.

Version 1.1.7 retains the complete v1.1.6 feature set, including multi-channel bulk editing, undo/redo and change history, the Configuration Validation Center, complete post-write verification reports, the responsive Dashboard, and full factory-firmware and nicFW950 support.

### Installation

1. Download `RT950_950Pro_Editor_Setup_v1.1.7_x64.exe` below.
2. Close RT-950/950Pro Editor if it is running.
3. Run the installer over the existing installation.
4. Confirm the correct connection type, COM port, and nicFW operating baud rate before reading or writing.

The installer is self-contained for 64-bit Windows and does not require Python or the retired backend executable.

### Integrity

SHA-256: `D138A4285BA23C60F0071F221F52275B23B23BEA4A881E121DFCFE8883897D6A`

The installer is Authenticode-signed by `KK4OXN / RT-950 950Pro Editor` and timestamped by DigiCert.

### Important safety notes

- Keep a known-good backup before writing or changing firmware-specific settings.
- Verify frequencies, tones, offsets, modulation, groups, power, and transmit permissions before transmitting.
- Do not disconnect or power off the radio during a read, write, verification, startup-image transfer, or firmware operation.

Thank you to the users and Patreon members whose field reports helped identify and verify this correction.
