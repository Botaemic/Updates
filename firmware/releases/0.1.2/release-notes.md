# SoundController USB Firmware 0.1.2

## Changes

- Fixes the app-to-bootloader jump address so firmware updates enter the LUFA HID bootloader at `0x7000`.
- Keeps the mock update artifact aligned with the fixed firmware image.

## Artifact

```text
SoundController.hex
```
