# Publishing Guide

This repository is the public distribution repository for Carbon Element Video. It is separate from the private source repository and does not contain source code, signing files, backend credentials, or production secrets.

## Repository Roles

| Repository | Visibility | Purpose |
| --- | --- | --- |
| `520Girl/Self_developed_video` | Private | Flutter application, CoolAdmin backend, Vue operations console, database migrations, and content-ingestion code. |
| `520boys/carbon-element-video-release` | Public | Product documentation, public assets, release metadata, GitHub Pages, and APK assets published through Releases. |

## Automated Android Release

The private source repository uses GitHub Actions to publish Android APKs to this repository.

1. Update `pubspec.yaml`, for example `version: 2.0.1+3`.
2. Add user-facing notes at `docs/releases/v2.0.1.md` in the private source repository.
3. Deploy database migrations and backend/admin changes separately when required.
4. Commit and push source changes to `main`.
5. Create and push the matching tag:

```powershell
git tag v2.0.1+3
git push origin v2.0.1+3
```

The workflow builds a signed APK, calculates SHA-256, updates `app-info.json`, and creates or updates the matching GitHub Release in this repository.

## Public Repository Maintenance

- Keep the README, screenshots, privacy notice, and changelog accurate.
- Upload APK/AAB files only as GitHub Release assets, never as normal Git files.
- Keep `app-info.json` at the repository root for future in-app update checks.
- Configure GitHub Pages from the `main` branch root to publish `index.html`.
- Use a wide `1280 x 640` social image for Open Graph previews when available.
