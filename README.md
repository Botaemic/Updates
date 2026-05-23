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
```

GitHub Pages can publish the neutral landing page from the `docs` folder:

```text
https://botaemic.github.io/Updates/
```

Because GitHub Pages is publishing from `docs`, top-level feed files are not served by that Pages URL. SoundController should use the raw GitHub manifest URL:

```text
https://raw.githubusercontent.com/Botaemic/Updates/main/manifest.json
```

If GitHub Pages is later changed to publish from the repository root, SoundController can use:

```text
https://botaemic.github.io/Updates/manifest.json
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
