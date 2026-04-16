# Release v2026.04.16

Date: 2026-04-16

## Added
- Pause / Resume / Cancel controls for download tasks in extension popup.
- Admin login page at `/admin` with `x-admin-token` workflow.
- Bilingual (ZH/EN) announcement fields with newline rendering support.

## Changed
- License API base switched to:
  - `https://extension.hepingan.top/webdown-license`
- Runtime config continues via:
  - `GET /config/public`
- Removed runtime permission prompt on download click; host permissions are declared in manifest.
- Improved download capture pipeline with:
  - `webRequest` merge support
  - `<noscript>` parsing
  - root-relative URL rewrite in orchestrator

## Fixed
- CORS preflight issue for config fetch path by avoiding unnecessary GET content-type header.
- Admin routing mismatch caused by reverse proxy port inconsistency.

## Notes
- This is a **new release** and should be published as a separate GitHub Release.
- Do **not** edit or replace previous releases.
