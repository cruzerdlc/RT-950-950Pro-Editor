# RT-950/950Pro Editor v0.8.37

Stable maintenance release based on v0.8.36.

## Fixed in this release

- Corrected the COM/USB boot-picture completion step to match the OEM CPS capture exactly.
- After all 150 image pages are acknowledged, the app now sends the final A5 `Over` frame without waiting for a response. The radio and OEM CPS do not exchange a final A5 ACK at this point.
- Removed the misleading five-second timeout and warning that appeared after an otherwise successful boot-picture upload.
- Boot-upload logs now clearly report that no response is expected after the final `Over` frame.
- Retains the v0.8.36 stock-config import fix and all v0.8.35 AM, synchronized settings-tab, and TX-lockout fixes.

The stable full-payload BLE write method remains enabled. Experimental BLE boot-picture upload remains disabled.

Use the included Windows build scripts to create the portable executable. Keep a radio backup before writing. After a boot-picture upload, power-cycle the radio to view the new image.
