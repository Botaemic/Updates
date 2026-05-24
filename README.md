# Botaemic Updates

This repository hosts static update feeds and release artifacts for Botaemic projects.

The current SoundController app should read the raw GitHub manifest URL:

```text
https://raw.githubusercontent.com/Botaemic/Updates/main/manifest.json
```

GitHub Pages currently publishes from `docs`, so the top-level manifest is not available at:

```text
https://botaemic.github.io/Updates/manifest.json
```

That Pages URL only works if Pages is later changed to publish from the repository root.

## Schema Version 2

`manifest.json` uses `schemaVersion` 2. Products are keyed by numeric product IDs instead of names like `companionApp` or `firmware`.

Product IDs use this 32-bit format:

```text
0xPPPPVVTT
```

- `PPPP` is the project ID.
- `VV` is the hardware or product variant. `00` means generic or all variants.
- `TT` is the target type.

Target types:

```text
0x01 Firmware
0x02 Windows companion app
0x03 Bootloader
0x04 Hardware definition/config package
0x05 Documentation package
0x06 Calibration/config data
```

Current SoundController product IDs:

```text
0x00010002 SoundController App
0x00010101 SoundController USB Firmware
```

The updater detects installed apps and connected USB devices first, then matches those detected product IDs against the manifest.

## Repository Shape

Recommended repository shape on GitHub:

```text
Botaemic/Updates
  README.md
  manifest.json
  app/
    soundcontroller/
      releases/
  firmware/
    soundcontroller/
      releases/
  docs/
    index.html
    schema-v2.md
```

GitHub Pages can publish the neutral landing page from the `docs` folder:

```text
https://botaemic.github.io/Updates/
```

## Relative And Absolute Artifacts

Artifacts can use paths relative to `baseUrl`:

```json
"url": "firmware/soundcontroller/releases/0.1.3/SoundController.hex"
```

They can also use full HTTPS URLs, for example GitHub Release assets:

```json
"url": "https://github.com/Botaemic/Updates/releases/download/v0.1.8/SoundController-App-0.1.8.msi"
```

The update manager supports both. It must verify SHA-256 before installing or flashing an artifact. Artifacts with an empty `sha256` are intentionally blocked until the hash is filled in.
