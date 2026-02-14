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

### Setting up PORTFOLIO_REPO_TOKEN

1. **Create a Personal Access Token (PAT)**:
   - Go to GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
   - Click "Generate new token (classic)"
   - Give it a descriptive name (e.g., "Photo Gallery Workflow")
   - Set an appropriate expiration period
   - Select the following scopes:
     - ✅ `repo` (Full control of private repositories)

2. **Copy the token** immediately (you won't be able to see it again)

3. **Add the token as a repository secret**:
   - In this repository (`spurs-women-photo-gallery`), go to Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name: `PORTFOLIO_REPO_TOKEN`
   - Value: Paste the token you copied
   - Click "Add secret"

**Important**: The token must have write permissions to the `my-portfolio-website` repository. If the repositories are under different organizations, ensure the token has cross-repository access.
