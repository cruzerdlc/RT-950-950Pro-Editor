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
- [ ] Confirm `VERSION` contains the exact release tag (for example, `v0.8.40`).
- [ ] Package the tested EXE into the release ZIP or installer.
- [ ] Generate and publish the SHA-256 checksum for every downloadable asset.
- [ ] Create the Git tag from the tested commit and publish the GitHub Release.

## Suggested GitHub release title

```text
RT-950/950Pro Editor v0.8.40
```

## Suggested release notes

```markdown
## RT-950/950Pro Editor v0.8.40

Stable release package.

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
.\scripts\Upload-BuildToGitHub.ps1 -ReleaseZip ".\release\RT950_950Pro_Editor_v0.8.40_Windows_Portable.zip"
```
