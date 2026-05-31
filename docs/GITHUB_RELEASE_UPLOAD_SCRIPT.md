# Uploading a Windows build to GitHub Releases

This project includes a maintainer PowerShell script:

```powershell
.\scripts\Upload-BuildToGitHub.ps1
```

The script uploads the tested Windows release package to:

```text
https://github.com/cruzerdlc/RT-950-950Pro-Editor
```

## Requirements

Install GitHub CLI and sign in once:

```powershell
winget install --id GitHub.cli
gh auth login
```

## Upload an existing release ZIP

```powershell
.\scripts\Upload-BuildToGitHub.ps1 -ReleaseZip ".\release\RT950_950Pro_Editor_v0.7.0-pre4_Windows_Portable.zip"
```

## Upload from an EXE

If you only have the tested EXE, the script can package it into a portable ZIP first:

```powershell
.\scripts\Upload-BuildToGitHub.ps1 -ExePath ".\dist\RT-950_950Pro_Editor.exe"
```

## Draft release

```powershell
.\scripts\Upload-BuildToGitHub.ps1 -ReleaseZip ".\release\RT950_950Pro_Editor_v0.7.0-pre4_Windows_Portable.zip" -Draft $true
```

## Notes

- The script uses the `VERSION` file for the release tag.
- If a release already exists, it uploads assets with `--clobber` so the ZIP can be replaced.
- The script does not store a GitHub token. Authentication is handled by `gh auth login`.
