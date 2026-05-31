# GitHub Upload Guide

Repository:

```text
https://github.com/cruzerdlc/RT-950-950Pro-Editor
```

## Upload a tested Windows release package

Use the included PowerShell script from the project folder:

```powershell
.\scripts\Upload-BuildToGitHub.ps1 -ReleaseZip ".\release\RT950_950Pro_Editor_v0.7.0-pre4_Windows_Portable.zip"
```

The script uses GitHub CLI authentication and does not store a token. Install/sign in once:

```powershell
winget install --id GitHub.cli
gh auth login
```

If you only have the tested EXE, the script can package it first:

```powershell
.\scripts\Upload-BuildToGitHub.ps1 -ExePath ".\dist\RT-950_950Pro_Editor.exe"
```

## Suggested repository description

```text
Windows editor for Radtel RT-950 / RT-950Pro radios with direct read/write, settings editing, stock presets, and boot picture upload.
```

## Suggested topics

```text
radtel, rt-950, rt-950pro, radio, ham-radio, gmrs, codeplug, cps, chirp, tkinter, pyserial
```
