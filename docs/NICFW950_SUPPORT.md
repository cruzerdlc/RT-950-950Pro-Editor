# nicFW950 custom-firmware support

RT-950/950Pro Editor v1.1.5 adds a separate compatibility profile for an
RT-950 Pro running [nicFW950](https://github.com/nicsure/RMS880). Factory
firmware and nicFW950 use incompatible baud rates, packet framing, storage
layouts, and channel records. Always select the profile that matches the
firmware installed on the connected radio.

The custom firmware is not included with this editor. Compatibility support was
developed with permission and technical assistance from the RMS880/nicFW950
developer.

## Reading a nicFW radio

1. Connect the RT-950 Pro with its USB programming cable.
2. Open **Read Radio**.
3. Choose **USB / Serial COM Port (nicFW950 custom firmware)**.
4. Select the COM port and operating baud rate. The app opens at nicFW's required
   38,400-baud bootstrap speed and then negotiates the selected operating speed;
   76,800 baud is the default.
5. Keep the radio connected until the automatic capture and read complete.

After the read, the sidebar automatically changes to the nicFW tool set. Loading
a factory `.dat` or reading a factory-firmware radio restores the normal pages.

## Supported workspace

- All 999 memory channels and preservation of the firmware VFO records.
- Channel names, RX/TX frequencies and tones, groups, clarifier/BFO, reverse,
  modulation, bandwidth, power, PTT ID, busy lockout, and documented flags.
- Settings, Groups, User Keys, Band Plan, Scanning, DTMF, GPS/APRS, Codeplug,
  Power, Calibration, Remote, Fonts, UI, Startup, Console, and Firmware sections.
- Exact firmware-storage block import and export.
- Automatic nicFW captures and Backup Manager restore support.
- 240 × 320 RGB565 startup-image preparation, radio-frame preview, formatting,
  read/write verification, and preservation of reserved bytes.
- Live radio display and keypad/PTT remote control.
- Firmware flashing plus complete flash-image backup and restore, shown only for
  an active nicFW configuration.

## Safe writing behavior

The active configuration carries its firmware profile. **Write Radio** forces
that profile so factory commands cannot accidentally be sent to a nicFW radio or
vice versa.

For nicFW writes, the editor reads the required live baseline, merges the visible
changes, preserves reserved and radio-managed data, writes changed pages,
finalizes and reboots the radio, and reads the affected pages back for
verification. Do not disconnect or power off the radio during any of these steps.

## Backups and firmware safety

Before changing channels, settings, calibration, power tables, startup images,
or firmware:

1. Read the radio and retain the automatic nicFW capture.
2. Use **Firmware** to save a complete flash image before flashing or recovery.
3. Confirm the selected COM port and firmware profile.
4. Verify frequencies, tones, groups, modulation, power, and transmit permissions.
5. Keep the radio powered and connected until verification finishes.

Firmware and calibration operations can make a radio unusable when interrupted
or supplied with an incompatible image. Restore only images made for the same
radio and firmware family.

## Protocol references

- [RMS880 technical information](https://github.com/nicsure/RMS880/wiki#technical-information)
- [Serial Protocol](https://github.com/nicsure/RMS880/wiki/Serial-Protocol)
- [Storage Layout](https://github.com/nicsure/RMS880/wiki/Storage-Layout)
- [Data Structures](https://github.com/nicsure/RMS880/wiki/Data-Structures)

nicFW support is isolated from the factory USB and Bluetooth/BLE services so a
change in one firmware profile does not alter the other protocol.
