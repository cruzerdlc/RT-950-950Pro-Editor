# Changelog

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
