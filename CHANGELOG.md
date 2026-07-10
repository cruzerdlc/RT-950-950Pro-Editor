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

