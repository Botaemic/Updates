# SoundController USB Firmware 0.1.0

## Changes

- Base HID firmware with OLED display, app slots, encoder events, firmware version reporting, and bootloader entry support.
- Handles the Windows app disconnect command and returns to the waiting/not-connected OLED state.

## Artifact

The firmware HEX for this release is published here:

```text
SoundController.hex
```

The `manifest.json` entry must include the matching `sha256` and `sizeBytes` values before this is offered to users.
