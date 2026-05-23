# SoundController Companion App 0.1.6

## Changes

- Keeps the update-check UI under a single menu item.
- Shows versions in `x.x.x` format.
- Keeps update installation manual; auto update means auto check only.

## Artifact

The future online server should place the companion app installer here:

```text
setup.exe
```

The `manifest.json` entry should include the real `sha256` and `sizeBytes` values before this is used for real updates.
