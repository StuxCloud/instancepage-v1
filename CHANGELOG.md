# Changelog

All notable changes to instancepage-v1 are documented here.

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
