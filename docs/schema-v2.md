# Update Feed Schema Version 2

Schema v2 identifies each installable product with a numeric product ID. Apps and devices identify themselves locally first; the updater then matches those local product IDs against `manifest.json`.

## Product ID

Product IDs are 32-bit values:

```text
0xPPPPVVTT
```

- `PPPP`: project ID.
- `VV`: hardware or product variant. `00` means generic or all variants.
- `TT`: target type.

Target types:

```text
0x01 Firmware
0x02 Windows companion app
0x03 Bootloader
0x04 Hardware definition/config package
0x05 Documentation package
0x06 Calibration/config data
```

SoundController currently uses:

```text
0x00010002 SoundController App
0x00010101 SoundController USB Firmware
```

## Version Number

Human-readable versions stay in `latestVersion`, for example:

```json
"latestVersion": "0.1.2"
```

Numeric comparisons use:

```text
0x00MMmmpp
```

Examples:

```text
0.1.2  = 0x00000102
0.1.6  = 0x00000106
1.0.0  = 0x00010000
1.4.12 = 0x0001040C
```

## Product Fields

Each product entry includes:

- `productId`: the full numeric product ID.
- `projectId`: the parent project ID.
- `hardwareVariant`: the variant byte from the product ID.
- `targetType`: the target type byte from the product ID.
- `name`: display name.
- `category`: updater category such as `app` or `firmware`.
- `latestVersion` and `latestVersionNumber`: latest available version.
- `minimumSupportedVersion` and `minimumSupportedVersionNumber`: oldest version supported by this update path.
- `autoInstallDefault`: whether automatic install should be selected by default.
- `requiresAdmin`: whether installation needs elevation.
- `releaseNotes`: relative or absolute path to release notes.
- `artifacts`: downloadable files for this product.

## Artifact Fields

Common artifact fields:

- `type`: artifact type, for example `installer` or `intelHex`.
- `fileName`: local cache file name.
- `url`: relative path under `baseUrl` or a full `https://` URL.
- `sha256`: required hash for install or flash validation.
- `sizeBytes`: optional size check. `0` means no size check.

Installer artifacts can also include:

- `installerType`: installer format, for example `exe`.
- `installArguments`: normal install arguments.
- `silentInstallArguments`: unattended install arguments.

Artifacts with an empty `sha256` must not be installed or flashed.

## Example

```json
{
  "schemaVersion": 2,
  "baseUrl": "https://raw.githubusercontent.com/Botaemic/Updates/main/",
  "products": {
    "0x00010101": {
      "productId": "0x00010101",
      "projectId": "0x0001",
      "hardwareVariant": "0x01",
      "targetType": "0x01",
      "name": "SoundController USB Firmware",
      "category": "firmware",
      "latestVersion": "0.1.2",
      "latestVersionNumber": "0x00000102",
      "releaseNotes": "firmware/soundcontroller/releases/0.1.2/release-notes.md",
      "artifacts": [
        {
          "type": "intelHex",
          "fileName": "SoundController.hex",
          "url": "firmware/soundcontroller/releases/0.1.2/SoundController.hex",
          "sha256": "71ebb328700c255de8a3d4cf6f8f01863e649321ad39c1ffc355efc7980e0f2b",
          "sizeBytes": 24743
        }
      ]
    }
  }
}
```
