# v0.8.40

- Added persistent rotating application logs under `%APPDATA%\RT950ProEditor\logs`.
- Added **Help > Enable Detailed Logging**, enabled by default, with a saved per-user preference.
- Added **Help > Open Log Folder** so users can immediately locate and send `rt950pro_editor.log` and its rotated backups.
- Added startup diagnostics covering app version, Python/runtime, operating system, executable location, working directory, settings path, and log path.
- Standardized the GitHub update-check User-Agent and instrumented the complete workflow: request URL, HTTP status, elapsed time, response size/type, rate-limit remainder, fallback source, raw/normalized version, version keys, chosen asset, and final comparison decision.
- Fixed the update-check error callback: the prior worker captured an exception variable in a delayed lambda, which Python clears after the `except` block and could cause update failures to disappear behind a callback `NameError`.
- Moved update results through a thread-safe queue polled by Tk instead of calling Tk methods directly from the network worker thread.
- Automatic update failures now appear in the status bar and point users to **Help > Open Log Folder**; manual failures also show the exact log path.
- Added logging for unexpected Tk callback, main-thread, and worker-thread exceptions.
- Added automatic redaction for personal `rbuapp_` and legacy shared `app_` RepeaterBook tokens in application logs.
- Added seven diagnostic logging/update-check regression tests; all previous RadioRef, RepeaterBook, boot-picture, AM/TX, stock-config, and settings fixes remain included.

# v0.8.39

- Added **File > RepeaterBook Import** using RepeaterBook's approved per-user app-token workflow.
- Each user enters their own `rbuapp_` token; shared `app_` tokens are rejected and none is embedded in the source or release package.
- Added links to the RepeaterBook API Apps dashboard and API instructions.
- Remembered tokens use Windows Data Protection when available and can be cleared from the importer.
- Corrected the User-Agent to preserve the exact RepeaterBook-approved project prefix while appending the current runtime version and contact email.
- Added United States searches by state, ZIP-resolved city, city, county, callsign, frequency, landmark, mode, emergency-service classification, and Amateur/GMRS service.
- Added rest-of-world searches by country, region, city, callsign, frequency, landmark, and mode.
- Added selectable result preview, operational-only filtering, result limits, duplicate detection, and direct import into the active file.
- Added destination zone, append/overwrite, and starting-channel controls.
- Digital-only repeaters can be imported receive-only or skipped; analog-capable repeaters retain input frequency and uplink/downlink tones when provided.
- Analog repeater results without a published input frequency default to receive-only instead of transmitting on the repeater output.
- Added RepeaterBook attribution and detail-page links without providing a bulk database, standalone export service, or website scraper.
- Added nine RepeaterBook token, query, header, parsing, conversion, and menu regression tests.
- Retains all v0.8.38 RadioRef, Patreon, v0.8.37 boot-picture, v0.8.36 stock-config, and v0.8.35 AM/TX/settings fixes.

# v0.8.38

- Added **File > RadioRef Import** with ZIP, City/State, and County/State searches.
- Added JavaScript-rendered RadioReference scraping through Playwright with standard HTML fallback; no RadioReference API key is required.
- Added result preview, multi-row selection, mode filters, CHIRP CSV export, human-readable TXT export, and direct import into the currently open radio file.
- Added destination zone, append/overwrite, and start-channel controls.
- RadioReference and unsupported digital-mode rows default to receive-only; DMR/P25/NXDN/D-STAR/C4FM can be listed but are not decoded by the radio.
- Added CHIRP CSV validation, existing-CSV mode filtering, CSV-to-TXT conversion, and county-cache build/refresh tools.
- Added bundled US county-ID seed cache and standard 22-channel GMRS/FRS plus 7-channel NOAA generators.
- Added Patreon links to the splash screen, left sidebar above GitHub, and About window: https://patreon.com/KK4OXN
- Retains all v0.8.37 boot-picture completion, v0.8.36 stock-config, and v0.8.35 AM/TX/settings fixes.

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

