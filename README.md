# Botaemic Updates

This repository hosts update feeds and release artifacts for Botaemic projects.

The current SoundController app reads:

```text
manifest.json
```

The manifest then points to release notes and update artifacts with relative paths, for example:

```text
firmware/soundcontroller/releases/0.1.2/SoundController.hex
```

## Recommended GitHub Setup

Publish the contents of this folder to:

```text
https://github.com/Botaemic/Updates
```

Recommended repository shape on GitHub:

```text
Botaemic/Updates
  manifest.json
  app/
    soundcontroller/
      releases/
  firmware/
    soundcontroller/
      releases/
```

If GitHub Pages is enabled for the repository, SoundController should use:

```text
https://botaemic.github.io/Updates/manifest.json
```

If GitHub Pages is not enabled yet, SoundController can use the raw GitHub URL:

```text
https://raw.githubusercontent.com/Botaemic/Updates/main/manifest.json
```



## GitHub Releases

GitHub Releases are useful for larger downloadable files like `setup.exe`.

If an artifact is uploaded to a GitHub Release, put its full download URL in `manifest.json` instead of a relative path:

```json
"url": "https://github.com/Botaemic/Updates/releases/download/v0.1.8/setup.exe"
```

The update manager already supports both relative URLs and full HTTPS URLs.

## Update Rules


## Current Published Firmware
