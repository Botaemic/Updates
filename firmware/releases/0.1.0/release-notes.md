# SoundController USB Firmware 0.1.0

## Changes

- Base HID firmware with OLED display, app slots, encoder events, firmware version reporting, and bootloader entry support.
- Handles the Windows app disconnect command and returns to the waiting/not-connected OLED state.

## Artifact

The future online server should place the firmware HEX here:

```text
SoundController.hex
```

The `manifest.json` entry should include the real `sha256` and `sizeBytes` values before this is used for real updates.
