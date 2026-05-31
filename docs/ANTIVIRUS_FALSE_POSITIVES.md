# Antivirus false positives

RT-950/950Pro Editor is a Windows radio programming utility. It talks to USB serial/COM ports and writes data to a connected radio. Some antivirus engines may treat new unsigned hardware utilities as suspicious, especially when they are packaged as Python executables.

## What changed in v0.7.0-pre8

The pre-production build was changed to reduce false positives:

- Uses a **portable folder build** instead of a one-file self-extracting EXE.
- Uses PyInstaller **onedir**, not `--onefile`.
- Uses **`upx=False` in the PyInstaller spec**; no UPX packing/compression.
- Adds Windows version metadata to the EXE.
- Produces a `SHA256SUMS.txt` file in the release folder.
- Keeps the release transparent: the EXE sits beside its support files instead of unpacking itself at runtime.

## Before publishing a release

1. Build with `BUILD_CLEAN_PORTABLE_WINDOWS.bat`.
2. Scan the output ZIP and EXE with Microsoft Defender.
3. Upload the ZIP or EXE to VirusTotal.
4. If only a few vendors flag it, submit false-positive reports to those vendors.
5. If Microsoft Defender flags it, submit the file to Microsoft Security Intelligence for review before publishing.

## Best long-term fix

For public releases, sign the EXE with a code-signing certificate. Signing does not guarantee zero detections, but it improves reputation and shows users who published the binary.
