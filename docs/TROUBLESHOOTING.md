# Troubleshooting

## COM port does not show

- Unplug/replug the programming cable.
- Check Device Manager → Ports (COM & LPT).
- Install the correct USB serial driver, commonly CH340 for many programming cables.
- Close the factory CPS or any other app that may be using the port.

## Read Radio fails

- Confirm the radio is powered on.
- Confirm the correct COM port.
- Close other serial tools.
- Try unplugging/replugging the USB cable.
- Try power-cycling the radio.

## Write Radio fails

- Do not unplug the cable.
- Read the radio back to confirm what changed.
- Restore from a known-good backup if needed.
- Try again after power-cycling the radio.

## Verify after write reports differences

- Read the radio again.
- Check whether the edited fields actually changed.
- If the radio is correct, save a fresh backup.
- If the radio is wrong, restore from backup.

## Boot image upload does not show immediately

Power-cycle the radio. Some boot image changes only display after restart.

## Boot image load/readback

The RT-950Pro tested during development did not return current boot-image bytes through the tested boot-image read command. For safety, production builds only support opening an image from disk and uploading it.

## Antivirus warns about EXE

Windows or antivirus software may warn on new unsigned community executables. Download only from the official project release page and scan the file before running.

## Automatic or manual update detection does not work

1. Run **Help > Check for Updates...** manually.
2. Open **Help > Open Log Folder**.
3. Send `rt950pro_editor.log` to the developer.
4. Include the app version, Windows version, approximate time of the failed check, and whether a VPN, proxy, firewall, antivirus HTTPS inspection, or filtered network was active.

The log records GitHub HTTP status codes, timeouts, SSL/DNS errors, API rate-limit information, parsed versions, and the final comparison decision. Personal RepeaterBook tokens are redacted automatically.

