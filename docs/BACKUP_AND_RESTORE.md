# Backup and Restore

## Automatic backups

The editor performs a fresh radio read before normal writes. These backups are stored in the app data folder and can be used to recover from a bad edit.

Typical location:

```text
C:\Users\<you>\AppData\Roaming\RT950ProEditor
```

## Recommended backup routine

1. Read the radio before editing.
2. Save/export your channel list if you are making large changes.
3. Keep at least one known-good backup from the factory CPS and one from this editor.
4. After a successful write/verify, keep that backup as a recovery point.

## Restore note

A dedicated Backup Manager / Restore UI is planned as the next polish item. Until then, keep backup capture files and source `.dat` files organized by date.
