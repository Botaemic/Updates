# SoundController Companion App 0.1.4

## Changes

- Sends a disconnect notification to the USB device before the tray app exits.
- Keeps installer metadata aligned with app version `0.1.4`.

## Artifact

The future online server should place the companion app installer here:

```text
setup.exe
```

The `manifest.json` entry should include the real `sha256` and `sizeBytes` values before this is used for real updates.
