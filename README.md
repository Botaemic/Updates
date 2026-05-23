# SoundController Update Feed

This folder is the publish-ready update feed for the SoundController Windows app.

The app reads:

```text
manifest.json
```

The manifest then points to release notes and update artifacts with relative paths, for example:

```text
firmware/releases/0.1.2/SoundController.hex
```

## Recommended GitHub Setup

For a simple static update source, publish the contents of this folder to a small GitHub repository and enable GitHub Pages.

Recommended repository shape:

```text
soundcontroller-updates/
  manifest.json
  app/
  firmware/
```

Then the app can use a manifest URL like:

```text
https://<github-user>.github.io/soundcontroller-updates/manifest.json
```

You can also use the raw GitHub URL:

```text
https://raw.githubusercontent.com/<github-user>/soundcontroller-updates/main/manifest.json
```

GitHub Pages is nicer for this because the URLs are shorter and intended for static file hosting.

## GitHub Releases

GitHub Releases are useful for larger downloadable files like `setup.exe`.

If an artifact is uploaded to a GitHub Release, put its full download URL in `manifest.json` instead of a relative path:

```json
"url": "https://github.com/<github-user>/<repo>/releases/download/v0.1.8/setup.exe"
```

The update manager already supports both relative URLs and full HTTPS URLs.

## Update Rules

- `Check Now` only reads `manifest.json`.
- No update artifact is downloaded until the user presses `Update` and confirms.
- `sha256` should be filled in for every real artifact.
- `sizeBytes` should match the published file size.
- Keep versions in `x.x.x` format.

## Current Published Firmware

```text
Firmware: 0.1.2
File:     firmware/releases/0.1.2/SoundController.hex
SHA-256:  71ebb328700c255de8a3d4cf6f8f01863e649321ad39c1ffc355efc7980e0f2b
Size:     24743 bytes
```
