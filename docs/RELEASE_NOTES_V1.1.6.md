## RT-950/950Pro Editor v1.1.6

Version 1.1.6 makes large channel configurations faster to edit, safer to write, and easier to troubleshoot on both factory-firmware and nicFW950 radios.

### Highlights

- Multi-channel bulk editing for power, bandwidth, mode, RX/TX tones, busy lockout, scan membership, transmit enable, and up to four nicFW group memberships.
- Undo, redo, and timestamped change history for individual edits, bulk edits, moves, copies, drag-and-drop operations, and zone/group clearing.
- A Configuration Validation Center that identifies invalid frequencies, malformed tones, unsupported values, firmware-specific errors, incomplete RX/TX data, and likely duplicate channels before a write.
- A complete post-write verification report containing write status, programmed-channel count, every expected-versus-actual byte difference, warnings, and paths to the safety backup, verification capture, and diagnostic transcript.
- Removal of the former 20-item verification-difference limit.
- A compact responsive Dashboard toolbar that keeps Search, Copy selected, Move selected, and other controls visible at narrower window sizes.

Version 1.1.6 retains the complete v1.1.5 feature set, including factory USB/COM and Bluetooth/BLE support, full nicFW950 support, firmware-aware menus, exact storage preservation, startup-image tools, Remote control, firmware maintenance, RadioReference, RepeaterBook, stock configurations, Backup Manager, and multilingual UI support.

### Installation

1. Download `RT950_950Pro_Editor_Setup_v1.1.6_x64.exe` below.
2. Close RT-950/950Pro Editor if it is running.
3. Run the installer over the existing installation.

The installer is self-contained for 64-bit Windows and does not require Python or the retired backend executable.

### Integrity

SHA-256: `2D569AF7EF1D7CE803175158E983F8F82519B349D3ADB7A86E170FE6DDD81461`

The installer is Authenticode-signed by `KK4OXN / RT-950 950Pro Editor`.

### Important safety notes

- Keep a known-good backup before writing or changing firmware-specific settings.
- Verify frequencies, tones, offsets, modulation, groups, power, and transmit permissions before transmitting.
- Do not disconnect or power off the radio during a read, write, verification, startup-image transfer, or firmware operation.

Thank you to the Patreon members and testers whose field reports and radio testing shaped this release.
