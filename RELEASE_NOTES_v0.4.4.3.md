# v0.4.4.3 - Logo Import Package

Built for Teamfight Manager 2 v0.4.4.

This release keeps the mod versioning aligned with the game version: `0.4.4` for the current game build, plus `.3` for the third mod patch on top of it.

## Highlights

- Repacked the current verified logo database as a direct-import `.tfm2db` package for the in-game import flow.
- Preserved the validated v0.4.4.2 roster, player age, contract, and balance data.
- Verified all 120 team logo references after packaging.
- Verified all 120 embedded custom logo blocks after packaging.
- Fixed SillySilly Gaming's missing logo by routing it to custom logo slot 79.
- Kept stadium names unchanged; the experimental venue-name pass was rolled back and is not included in this release.

## Logo Changes

- The packaged file now uses the direct-import TFM2DB wrapper: `kind=1`, gzip offset `25`.
- The decompressed database core matches the known-good logo candidate exactly.
- Custom logo payloads were compared block-by-block against the source candidate with 0 differences.
- Team text/logo rows were re-exported and compared with 0 differences.
- SillySilly Gaming is present with logo reference `custom:custom_team_logo/79`.

## What Stayed The Same

- Team slots and roster structure remain from the validated v0.4.4.2 database.
- Player names, team ownership, contracts, ages, and balance data remain preserved.
- The Oracle's Elixir and Games of Legends based stat/balance pass from v0.4.4.2 remains intact.
- Stadium names remain game defaults unless already present in the base data.

## Validation

- Packaged asset: `tfm2_teams_and_rosters.tfm2db`
- SHA256: `fde02f2821d47be645316f3e8335d388b068070e0351f5a4f3939b1292e28cb4`
- File size: `32641244` bytes
- `tools/validate.go` passed on the packaged asset.
- Header verified as direct-import format: `kind=1`, gzip offset `25`.
- Decompressed DB core matches the active/source logo candidate exactly.
- 120 team logo references found.
- 120 custom logo blocks verified.
- 0 team text/logo diffs against the source candidate.
- 0 custom logo block diffs against the source candidate.
- `database_pack.info` parses as JSON and is versioned `0.4.4.3`.

## Install

Download `tfm2_teams_and_rosters.tfm2db` and import it through the game's custom database/import flow.

Manual AppData replacement is no longer the recommended verification path for this release. If you do edit AppData manually, back up your current database first.