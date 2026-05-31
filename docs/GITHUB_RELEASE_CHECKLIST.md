# GitHub Release Checklist

## Before publishing

- [ ] Confirm the packaged Windows EXE launches.
- [ ] Run the EXE on a clean Windows machine or VM.
- [ ] Confirm the About dialog shows the correct version.
- [ ] Confirm the icon appears in the taskbar/window.
- [ ] Confirm Radio → Read Radio works.
- [ ] Confirm Radio → Write Radio works with a harmless edit.
- [ ] Confirm Boot Picture → Upload to Radio works with a test image.
- [ ] Confirm `README.md`, `CHANGELOG.md`, and docs are updated.
- [ ] Package the tested EXE into the release ZIP or installer.

## Suggested GitHub release title

```text
RT-950/950Pro Editor v0.7.0-pre1
```

## Suggested release notes

```markdown
## RT-950/950Pro Editor v0.7.0-pre1

Pre-production release package.

### Highlights

- Direct radio read/write over COM port.
- Automatic backup before write.
- Automatic verify after write.
- Multi-tab channel editor with zones.
- In-app VFO, Optional Features, DTMF, FM/AM/SSB, APRS, and Encryption editors.
- Built-in stock presets.
- Boot picture editor and confirmed boot picture upload.
- Custom app icon.
- GitHub-ready documentation.

### Downloads

- Portable Windows EXE ZIP

### Safety

Always read/backup before writing. Do not unplug power or USB during write or boot-picture upload.
```


## Upload with PowerShell script

```powershell
.\scripts\Upload-BuildToGitHub.ps1 -ReleaseZip ".\release\RT950_950Pro_Editor_v0.7.0-pre4_Windows_Portable.zip"
```
