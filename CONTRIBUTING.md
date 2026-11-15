# Contributing to instancepage-v1

Thank you for your interest in contributing! This repository is an archived, pinned snapshot of the original instancepage design, so its scope is intentionally narrow.

## Scope

This is **not** the actively developed template — that's [StuxCloud/instancepage](https://github.com/StuxCloud/instancepage). This repo preserves the pre-redesign `v1` look as-is. Contributions here should keep the existing design working, not change it:

- Fixing broken links, encoding issues, or browser-compatibility bugs
- Keeping the page renderable as browsers and standards evolve

New features, redesigns, or styling changes belong in the live `instancepage` repository instead.

## Getting Started

1. **Fork the repository** and clone your fork locally.
2. **Run it locally** with `./dev-server.sh` (or `dev-server.bat` on Windows) and open the printed URL. Add `--lan` to open it from a phone or another device on your network too.
3. **Make your changes** to `index.html` — it's a single self-contained file, no build step required.
4. **Submit a pull request** with a clear description of what you've changed and why.

## Reporting Bugs

- Check existing issues to avoid duplicates before opening a new one.
- Provide a clear title and description, steps to reproduce, and the expected vs. actual behaviour.
- Include your browser and OS where relevant — this is a purely client-side page, so most bugs are rendering issues.

## Style Guidelines

- Keep it a single static HTML file — no build tooling, no frameworks.
- Preserve the existing look and animation; this repo is about preservation, not iteration.
- Test both the light and dark themes, and the embedded (iframe) code path, before submitting.

## Questions

If you have any questions, feel free to reach out at [hello@stux.cloud](mailto:hello@stux.cloud) or open a discussion in this repository.

---

*Stux.Cloud is part of the [Stux.Group](https://github.com/StuxGroup) Brand of Companies.*

## Branches and going live

- **`main` is what's live.** Nothing is pushed to it directly: it only changes when a pull request from `staging` is merged. Merging into `main` deploys the site to GitHub Pages.
- **`staging` is the last check before live.** It only changes when a pull request from `test` is merged. There's no staging deployment, so this is where CI and a final review happen.
- **Work happens on `test`**, or on a feature branch off `test` that's merged back into it. Releases are made on `test` too; `commit.sh` / `commit.bat` refuse to run on `staging` or `main`.
- **Going live:** push `test` with its tag (`git push origin test --tags`), open a pull request into staging (`gh pr create --base staging --head test`), then once it's merged open one from staging into main (`gh pr create --base main --head staging`). Each needs CI to pass and is reviewed and merged by Leo.

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/version.sh` and `bash tests/site.sh`.
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.
5. Push `test` with its tag (`git push origin test --tags`) and open a pull request into `staging` (`gh pr create --base staging --head test`). Once it is merged, open one from `staging` into `main` (`gh pr create --base main --head staging`).
