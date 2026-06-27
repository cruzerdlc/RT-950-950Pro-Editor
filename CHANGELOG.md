# Changelog

## v0.8.10

- COM/USB cable write refinement: changed channel write span from 0x8000 to 0x7C00 to avoid writing past the aligned channel area.
- COM/USB cable read now uses the matching 0x7C00 channel span.
- The editor continues to show 990 real channel slots for USB/factory mode; the final 64 bytes are kept as preserved/padded alignment bytes.
- Bluetooth/BLE read/write behavior is unchanged from the confirmed-good v0.8.8/v0.8.9 path.

## v0.8.9

- UI-only update on top of v0.8.8.
- Enlarged the startup splash window so the BLE attribution and Close button are visible again.
- Made the startup splash resizable and added a larger minimum size to prevent bottom clipping.
- Increased the Write Radio dialog height and minimum size so the progress bar, log, and bottom status text are visible.
- Reduced the Write Radio log's requested line height so the lower controls stay visible on smaller displays.
- Kept the v0.8.8 Bluetooth/BLE read/write protocol unchanged.

## v0.8.8

- Reworked Bluetooth/BLE mode to use the stable CHIRP-compatible 960-channel clone layout.
- BLE channel read/write segment now uses `0x7800` / 960 channels instead of the experimental 990-channel `0x7C00` layout.
- BLE Radio Read tabs now show 960 channels instead of padding phantom channels 961-990.
- BLE write now uses a full CHIRP-compatible clone payload write instead of changed-segment optimization.
- BLE write still skips the extra pre-write safety read when writing from a BLE Radio Read tab.
- BLE still skips the app-specific `C000` zone-name block to match the working CHIRP BLE behavior.
- USB serial read/write behavior remains unchanged.

## v0.8.6

- Changed Bluetooth/BLE reads to use fast reference-style timing.
- Removed the extra slow BLE pacing that could let the radio drop out of programming mode during long reads.
- Reduced BLE empty-read retries to short, quick retries instead of long waits.
- Reduced BLE per-block timeout to fail/retry faster when a notify burst is missed.
- Kept BLE dynamic SEND challenge/key negotiation from v0.8.5.
- Kept USB serial read/write behavior unchanged.

## v0.8.3

- Improved Bluetooth/BLE read stability during long channel reads.
- Added automatic BLE clone-session refresh every 4 KB during channel reads.
- Added BLE reconnect-and-resume when a block stalls with zero bytes returned.
- Increased BLE empty-read retries and pacing to reduce timeout crashes.
- Added BLE write ACK retry/reconnect handling for stalled write pages.
- Added extra BLE write pacing checkpoints during channel writes.
- Kept USB serial behavior unchanged.

## v0.8.2

- Improved Bluetooth/BLE read stability by adding automatic retry for empty BLE read blocks.
- Increased BLE per-read timeout to better match Windows BLE notification timing.
- Added BLE pacing between 20-byte BLE writes to reduce dropped bursts.
- Improved BLE write ACK handling with longer BLE ACK budgets and ACK-in-buffer detection.
- Added small BLE post-block delays, especially for settings/APRS commits.
- Added stray ACK cleanup before the radio ID block during BLE handshakes.

## v0.8.1

- Added Bluetooth/BLE attribution to the startup splash screen.
- Added Bluetooth/BLE attribution to the About screen.
- Added Bluetooth/BLE attribution to the Read Radio window.
- Added Bluetooth/BLE attribution to the Write Radio window.
- Kept the experimental BLE read/write transport from v0.8.0 intact.

## v0.8.0

- Added experimental Bluetooth/BLE read support.
- Added experimental Bluetooth/BLE write support.
- Added USB Serial / Bluetooth BLE connection type selector in Read Radio and Write Radio.
- Added Scan BLE button to detect nearby BLE devices and select the RT-950/950Pro radio.
- Added BLE transport using the radio ffe0/ffe1 UART service and ff31 unlock sequence while keeping the existing read/write backend intact.
- Added Bluetooth write safety confirmation because BLE writing is experimental.
- Added third-party attribution notice for the MIT-licensed BLE reference code by Nivin Goonesekera (VK3NWG), with portions by Nathan G. Barguss (2E0NBS).
- Added bleak to runtime/build requirements for Bluetooth/BLE support.


## v0.7.9

- Fixed dark-mode source tab highlighting so selected, pressed, hovered, and close-tab states no longer turn white with unreadable text.
- Applied the same theme-aware tab colors to normal notebooks and the custom closable notebook used for open files/radio reads.
- Updated the close-tab X icon colors for better dark-mode contrast.

## v0.7.7

- Fixed FM/AM/SSB Modulation editor custom table colors in dark mode.
- Replaced hardcoded white factory-grid rows with theme-aware dark/light colors.
- Updated modulation panel/footer label frames to follow the active theme.
- Refreshed the custom modulation grid after applying the current theme.
- Kept backend radio protocol, read/write, CAT/VFO, DAT/CSV, and validation logic unchanged.


## v0.7.6

- Fixed startup crash caused by the left sidebar VFO / CAT Control entry pointing to a missing method.
- Restored the left sidebar VFO / CAT Control navigation without changing the existing VFO editor/backend logic.
- Kept all radio read/write, DAT/CSV, CAT/VFO data, validation, and existing editor logic intact.

## v0.7.5

- Removed the left-sidebar **Menu Settings** hub button.
- Listed the radio settings directly in the left sidebar for one-click access.
- Added direct sidebar entries for Optional Features, DTMF Codes, FM/AM/SSB Modulation, Zones, APRS Info, Encryption Presets, and Boot Picture.
- Kept backend radio protocol, read/write logic, CAT/VFO handling, DAT/CSV processing, and validation logic intact.

## v0.7.4

- Fixed Read Radio and Write Radio popup header/banner areas so they follow dark mode instead of showing a white strip.
- Updated Read/Write dialog frames, headers, button rows, and status text to use the active Windows 11 Fluent theme.
- Fixed Write Radio option checkboxes so Save pre-write backup and Verify after write no longer highlight white in dark mode.
- Kept backend radio protocol, read/write logic, CAT/VFO handling, DAT/CSV processing, and validation logic intact.

## v0.7.3

- Removed the down-arrow indicator from the in-app File/Radio/Edit/View/Tools/Help command bar.
- Kept the dark-mode themed command bar and existing menu commands intact.
- Command-bar menus now open from clean Windows 11 style text buttons.


## v0.7.2

- Restored the maintainer-only Windows build BAT/script files so the app can be built again from the source package.
- Added an updated PyInstaller onedir spec with UPX disabled.
- Added `requirements-build.txt` for build-only dependencies.
- Kept end-user README/User Guide focused on running the executable, not building the app.

## v0.7.1

- Switched release numbering from prerelease-style tags to normal version tags starting with `v0.7.1`.
- Cleaned end-user documentation so normal users are only told how to run the executable and use the app.
- Removed user-facing build-script instructions from the release docs.
- Replaced the native top menubar with a themed in-app command bar so **File / Radio / Edit / View / Tools / Help** follow light/dark mode.
- Improved dark-mode Treeview banding so channel/editor grids no longer show white alternating rows.
- Kept backend radio protocol, read/write logic, CAT/VFO handling, DAT/CSV processing, and validation logic intact.

## v0.7.0-pre100

- Startup default tab closes automatically once real user data is opened, unless it has been edited.

## v0.7.0-pre99

- Added light/dark theme support.
- Updated popup/dialog windows to use the app icon.

## v0.7.0-pre98

- Added the first Windows 11 style app shell and navigation rail.

## Earlier prerelease history

Earlier prereleases added direct radio read/write, backup/verify workflow, channel editing, zone views, Optional Features fixes, Keypad Lock offset fixes, FM/AM/SSB modulation editing, APRS/DTMF/VFO editors, CSV import/export, startup default data, and the public-build cleanup that removed developer packet-capture tools.
