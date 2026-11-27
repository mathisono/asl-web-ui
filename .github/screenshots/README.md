# Desktop radio UI examples

Captured 2026-11-27 from this PR's built frontend in Chromium at a 1440-pixel desktop viewport. SR110U channel/advanced views and a separate SA818S V1.2 view demonstrate distinct identities on the neutral Radio programming page.

API responses, names and radio settings are example fixtures, not production data or hardware readback. No live backend, radio programming or RF action was used. Mobile screenshots are omitted. The advanced-controls image crops to its card.

2026-11-27 follow-up: channel/SA818S desktop captures refreshed after adding the always-available rescan action. All data is synthetic; no radio was programmed.
# Backup coverage desktop screenshots

Captured 2026-11-27 at 1440×1100 using `tests/browser/backup-coverage.cjs`, with
fabricated example data and a fully mocked API. No private host, operator,
credentials or real service operations. No mobile screenshots.

- `backup-coverage-desktop.png`: customized-list warning, preserving exclusions.
- `backup-idle-desktop.png`: backup/restore idle prerequisite and archive limits.
