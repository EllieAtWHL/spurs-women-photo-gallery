# Spurs Women Photo Gallery

This repository stores photos for the Spurs Women photo gallery system. Photos are automatically processed and made available through a CDN in the main portfolio website.

## How It Works

1. **Photo Upload**: Add photos to the appropriate date folders (e.g., `2025-26/20260208 WSL Spurs vs Chelsea/`)
2. **Automatic Manifest**: When photos are pushed to `main`, a GitHub Action automatically generates a manifest file
3. **CDN Integration**: The manifest enables CDN-based loading through jsdelivr.net
4. **Portfolio Integration**: The main portfolio website uses this manifest to display photos

## File Structure

```
2025-26/
├── 20260118 WFA Cup Spurs vs Leicester City/
├── 20260201 WSL West Ham vs Spurs/
└── 20260208 WSL Spurs vs Chelsea/
    ├── PXL_20260208_120555768.MP.webp
    ├── PXL_20260208_131354499.PANO.webp
    └── ...
```

## Supported Formats

- `.jpg`, `.jpeg`
- `.png` 
- `.webp`
- `.avif`

## Automation

- **Trigger**: Push to `main` branch with photo changes
- **Action**: Generates manifest and commits to portfolio repository
- **Validation**: Ensures manifest is valid before deployment

## Manual Manifest Generation

To manually regenerate the manifest:

```bash
# In the portfolio repository
npm run generate-external-manifest
```

## CDN URLs

Photos are served through: `https://cdn.jsdelivr.net/gh/EllieAtWHL/spurs-women-photo-gallery@main/`

## Repository Secrets

The workflow requires `PORTFOLIO_REPO_TOKEN` secret with write access to the portfolio repository.
