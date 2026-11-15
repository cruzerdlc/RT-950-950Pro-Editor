## RT-950/950Pro Editor v1.1.8

Version 1.1.8 focuses on safer radio writes, clearer imports, stronger nicFW compatibility checks, and byte-level reliability across factory and nicFW configurations.

### Safer writes and recovery

- Added a persistent interrupted-write recovery journal. If a write does not finish cleanly, the next launch can offer the exact pre-write or Radio Read baseline for recovery.
- Added a **Restore previous configuration** action after a write. It loads the captured pre-write baseline and returns to the normal confirmed Write Radio workflow, including another safety backup.
- Added nicFW firmware-family capability checks. Validated v6 firmware retains the complete editor and write toolset; unvalidated major versions are restricted to Console and Firmware recovery tools.

### Import improvements

- Replaced the summary-only RadioReference and RepeaterBook import confirmation with a row-by-row comparison.
- Exact duplicates are unchecked automatically.
- Occupied destinations and frequency conflicts are identified before import.
- Every incoming channel can be included or skipped independently.
- Source names remain intact during preview and are truncated only when placed into the selected factory or nicFW destination format.

### Format and reliability corrections

- Fixed factory GBK channel, zone, and Broadcast FM names so multibyte characters cannot be split into garbled bytes.
- Corrected Broadcast FM names to the radio's actual 12-byte text payload.
- Fixed erased `0xFF` padding appearing as question marks in nicFW DTMF, scan, band-plan, and GPS names.
- Prevented unsupported non-ASCII text from being silently replaced in RMS ASCII-only fields.
- Corrected nicFW group-name storage and signaling group 16 encoding and decoding.
- Centralized the factory CTCSS/DCS catalog and reject unsupported factory DCS values before a write begins.
- Fixed the Dashboard connection indicator after successful writes.
- Removed stale hard-coded version identifiers from network clients.

### Validation

- All six native C# regression executables passed, including all 22 native write tests.
- All 51 legacy/native Python regression tests passed.
- The final .NET 10 x64 Release build completed with zero warnings and zero errors.

### Installation

1. Download `RT950_950Pro_Editor_Setup_v1.1.8_x64.exe` below.
2. Close RT-950/950Pro Editor if it is running.
3. Run the installer over the existing installation.
4. Confirm the correct connection type, COM port, and nicFW operating baud rate before reading or writing.

The installer is self-contained for 64-bit Windows and does not require Python or the retired backend executable.

### Integrity

SHA-256: `B8400F204FA63E3DFC028CD034F68F99AC259FA55F5783123DE1B0787D4843E4`

The installer is Authenticode-signed by `KK4OXN / RT-950 950Pro Editor` and timestamped by DigiCert.

### Important safety notes

- Keep a known-good backup before writing or changing firmware-specific settings.
- Verify frequencies, tones, offsets, modulation, groups, power, and transmit permissions before transmitting.
- Do not disconnect or power off the radio during a read, write, verification, startup-image transfer, or firmware operation.

Thank you to the Patreon members and testers whose field reports and radio testing shaped this release.
