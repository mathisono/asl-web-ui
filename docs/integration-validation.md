# Current-release integration validation

This integration combines Hardware PR75 (`b987e35`) and backup PR76
(`0afdec9`) on the current WebUI 1.2 source. The companion ASL3 source is
PR218 (`a5a8f2d`), based on version 3.19.0. It is not a 1.1 backport.

Validation on Debian 13 ARM64:

- WebUI: 420 backend tests, frontend typecheck/build, isolated Hardware
  identity/board-swap and backup-warning/edit/readback browser checks passed.
- ASL3: 360 tests passed; package built natively for ARM64. Installed radio
  executables belong to the ASL3 package, not asl3-menu. Package ownership
  collisions and dependency changes were checked before installation.
- Full WebUI/ASL3 packages installed, installed payload hashes verified,
  authenticated live desktop Hardware/Backups pages checked, no browser
  exceptions. Existing application configuration, ownership, Allmon3 data,
  and the running Asterisk process were preserved.
- An idle backup of the older integrated Allmon3 storage layout was restored
  using the upgraded restore implementation into an isolated filesystem root.
  Original media, database integrity/rows/flags, file ownership and safe modes
  matched. No live production restore or post-restore package reconfiguration
  was performed.

The older Allmon3 application was deliberately retained; this is not a test
of migrating it to the optional announcements package. Its operator-owned
include list explicitly adds `/var/lib/allmon3/favorites.json`,
`/var/lib/allmon3/audio.sqlite3`, `/var/lib/allmon3/audio-originals`,
`/var/lib/allmon3-log-settings`, and the standalone time/weather INIs, in
addition to the upstream defaults. No data directories were migrated.
Allmon3 was stopped at idle for the backup, then restarted. The archive is
retained locally because original media exceeds the cloud upload limit.

Live radio discovery exercised the no-device path: no USB serial adapter was
enumerated, and no module answered. Hardware identity, alias handling and
board-swap behavior were verified with isolated fixtures; there was no live
radio programming, PTT, RF or power-cycle test. No recording architecture
change was made while the Logs placement proposal awaits direction.
