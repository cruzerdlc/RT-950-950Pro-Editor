RT-950/950Pro Editor v0.7.0-pre33
=================================

Pre-production Windows application
----------------------------------
This project is intended to be delivered to users as a ready-to-run Windows EXE.
End users do not need Python or build tools.

Quick start
-----------
1. Download the latest Windows release package from GitHub Releases.
2. Extract the ZIP if needed.
3. Run RT-950_950Pro_Editor.exe.
4. Connect the radio programming cable.
5. Use Radio > Read Radio.
6. Edit channels/settings.
7. Use Radio > Write Radio.

Project
-------
GitHub: https://github.com/cruzerdlc/RT-950-950Pro-Editor
Donate: https://cash.app/$cruzerdlc
Made by: KK4OXN

Read README.md and docs\USER_GUIDE.md for full documentation.


Clean portable packaging
------------------------
Windows release builds should be distributed as a portable folder ZIP, not as a one-file self-extracting EXE. This reduces antivirus false positives.


## Developer build note

For building the clean portable Windows release, run `BUILD_CLEAN_PORTABLE_WINDOWS.bat`. If Python is not installed, the build script now offers to install Python 3.12 with `winget`. End users of the finished portable ZIP do not need Python.


v0.7.0-pre33 notes:
- Radio Read Save As .dat now uses a bundled internal RT-950PRO template and only asks where to save.
- Write Radio now applies edited zone names to the radio zone block.
- Zone names match the radio style: ZoneOne, ZoneTwo, ZoneThree, etc.

v0.7.0-pre12 notes:
- Fixed Zone editor Apply Name crash.
- Moved modulation CSV import/export/template workflow to Edit > FM/AM/SSB Modulation.
- Removed zone import/export buttons from the Zone editor.
