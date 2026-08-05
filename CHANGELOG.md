# v0.8.37

- Fixed a false boot-picture completion warning after all 150 image pages had been acknowledged.
- The OEM capture confirms that the radio does not return an A5 response to the final `Over` frame; the uploader now sends that frame without waiting for an ACK.
- The final `Over` packet remains byte-for-byte compatible with the factory CPS: `A5 06 00 00 00 04 4F 76 65 72 A9 5E`.
- Optional unexpected trailing bytes are recorded in the transcript without turning a successful upload into a failure.
- Retains all v0.8.36 stock-config import and v0.8.35 AM/TX/settings-tab fixes.

# v0.8.36

- Fixed stock-config import into legacy/startup `.dat` files that do not originally contain the `enableTx` channel member.
- Legacy 16-field channel records are upgraded in memory to the current 17-field layout with `enableTx` defaulting to ON.
- TX Enable changes now remain editable and saveable when starting from an older OEM `.dat` file.
- Retains all v0.8.35 AM upload, synchronized settings-tab, and TX-lockout fixes.

# v0.8.35

- Fixed channel flag encoding so `enableTx=0` clears the radio TX-enable bit instead of being forced back ON.
- Fixed radio-read decoding so the TX Enable column reflects bit 1 of the channel flag byte.
- Normalized channel flag values from raw numbers, display labels, and booleans; this preserves AM when a source exposes `AM`/`True` instead of numeric `1`.
- Opened `.dat` files now refresh their channel-row cache from the live BinaryFormatter object immediately before radio upload.
- Added upload logging that reports the number of AM and TX-inhibited channels in the generated write image.
- Settings panels are now unique and replace older copies instead of allowing duplicate APRS/VFO/etc. tabs to diverge.
- A new Radio Read closes and rebuilds open radio-settings panels against the newly read document, eliminating stale-data ambiguity.
- Stable full-payload BLE read/write behavior is unchanged; BLE boot-picture upload remains disabled.

# v0.8.33

- Fixed COM/USB Boot Picture upload to match the factory CPS boot-logo protocol captured with the standalone COM sniffer.
- The boot uploader now sends `PROGRAMBT9000U`, sends `D` without expecting a direct ACK, then uses the factory A5-framed setup/page/Over packets.
- Boot-image pages now use the captured 1024-byte page format and CRC-16/CCITT init-0 checksum.
- BLE boot-picture upload remains disabled; normal BLE codeplug read/write behavior is unchanged.

## v0.8.33

- Refined COM/USB boot-picture upload session entry.
- Boot image upload now uses PROGRAM/F/M identification only before the D boot-picture command.
- Removed the full SEND challenge from the boot-image entry path because real-radio testing showed D is not ACKed after the full challenge.
- BLE boot-picture upload remains disabled.
- Normal COM/USB and BLE codeplug read/write behavior is unchanged.

