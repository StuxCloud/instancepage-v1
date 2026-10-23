# Changelog

All notable changes to instancepage-v1 are documented here.

Since v26.10.23 this project uses [Date Versioning](https://datevers.ing) (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used Semantic Versioning.

## v26.10.23-1

### Added

- A Discord link preview: every page except the 404 page carries a `discord:component-embed` in its `<head>` (pre-built JSON, kept under Discord's 3,000-byte limit) showing what this server page is, in Stux.Cloud's colours with its icon. The Open Graph fallback is unchanged
- A full favicon set at the site root: `favicon.ico` (16, 32 and 48 px), `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` and `site.webmanifest`, all made from Stux.Cloud's own icon, and the matching tags in every page's `<head>`
- `tests/site.sh`, which checks every embed is valid JSON under 3,000 bytes with no stray `$1`, that the 404 page has none, that the favicon files exist at the right sizes, and that every `<head>` carries the tag set
- `.htmlvalidate.json` relaxes `valid-id` so the validator accepts the embed's required `discord:component-embed` id

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.0.4
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v1.0.4

### Changed

- The copyright line reads Stux.Group instead of Stux Group Ltd

## v1.0.3

### Added
- `404.html`: a custom not-found page matching this archive's legacy branding (blue gradient wordmark, monospace type, old logo/icon assets), instead of GitHub Pages' default error page.

## v1.0.2

### Fixed
- GitHub Pages was using the legacy branch-deploy build system, which can silently stop auto-deploying with no error recorded anywhere (discovered on SeasonalOverlaysLibrary — its live site served stale content for over an hour with no visible failure). Switched to GitHub Actions-based Pages deployment (`.github/workflows/pages.yml`), making every deploy an ordinary, observable CI run instead.

## v1.0.1

### Changed
- `index.html`'s logo, icon, and `README.md`'s logo now point at the `/old/` variants (`https://global.media.stux.cloud/old/logo.png` and `/old/icon.png`), matching this project's archived, pre-redesign branding rather than the current Stux.Cloud brand assets.
- Added a `favicon.ico` link (`https://global.media.stux.cloud/old/favicon.ico`) alongside the existing PNG icon for broader browser compatibility.

## v1.0.0

### Added
- Archived [StuxCloud/instancepage](https://github.com/StuxCloud/instancepage) at commit `0e2f1ba` (the last state before its modern redesign), preserving history up to that point as this repository's own `main` branch.
- `VERSION.md`, `CHANGELOG.md`, and `CONTRIBUTING.md`.
- A `commit.sh`/`commit.bat` pair that reads the version from `VERSION.md` and tags the release accordingly.
- A `dev-server.sh`/`dev-server.bat` pair to serve the page locally without hand-configuring a static server.
- A "Boring Legal Stuff" footer link on the instance page, pointing to `https://stux.cloud/legal`.

### Fixed
- `index.html`'s logo and favicon URLs, which pointed at the retired `media.stux.cloud/global/...` host, corrected to `https://global.media.stux.cloud/logo.png` and `/icon.png`.

### Removed
- `CNAME`, which pointed at the live template's production domain (`instancepage.stux.cloud`) — this archive isn't deployed there.
