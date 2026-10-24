# Changelog

## v17

- **`SharedOwner.Order` no longer lists `MindAttic.GTFO.CrashTestDummies`.** That mod dropped its
  Insert/Delete feature (and this submodule entirely) in its own v17, so the entry could never match
  again; removed rather than left dead. `GTFO.CrashTestDummies` and `GTFO.SkipDrop` both join the
  `vN` scheme at v17 too, so every GTFO.* mod now shares one version number.

## v16

- **Insert and Delete swapped: Insert is now infinite health, Delete is now infinite ammo.**
- **`InfiniteToggles.cs` always logs its on/off announcements to the console too**, not just as a
  fallback for when the event-log message fails.
- Joins the GTFO.EZ family's `vN` versioning scheme, starting here at v16 to match its current
  release.
