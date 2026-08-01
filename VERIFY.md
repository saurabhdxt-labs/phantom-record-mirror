# Verify this record yourself

Nothing here asks for trust. Two independent checks, both runnable by anyone.

## 1. Timing — the Bitcoin bound

Every forecast file was committed BEFORE the window it predicts. Git commit
times alone are self-settable, so the binding bound is Bitcoin:

- `proofs/mirror/` — an OpenTimestamps stamp of each of this repository's own
  sync commits. Verify with the open-source `ots` client:
  `ots verify proofs/mirror/<commit>.sha.ots proofs/mirror/<commit>.sha`
  A verified proof names a Bitcoin block; the block's time is a hard upper
  bound on when that commit (and every file in it) existed.
- `proofs/primary/` — the daily HEAD stamps of the primary record repository
  (maintained since 2026-06; this mirror starts 2026-08-01). Each HEAD stamp
  anchors the primary record's entire commit ancestry via git's parent-hash
  chain. The primary repository is available for inspection during evaluation.
- Freshly created stamps are *pending* until Bitcoin aggregation completes
  (typically hours); `ots upgrade` completes them. Pending is a queue state,
  not a weaker claim.

## 2. Outcomes — aviation-authority NOTAMs

Forecast rows with `probability >= 0.7` are the record's graded high-
confidence level. To check outcomes against an independent authority source:

1. Pick a date and area from `reports/forecast/`.
2. Pull that day's GPS-interference NOTAMs for the area from any public
   NOTAM service (e.g. FAA NOTAM Search, notams.aim.faa.gov — free), or from
   your own aviation-data provider.
3. Compare where the high-confidence rows fall against the areas the
   authorities declared. NOTAMs are declarations, not per-hour ground truth —
   the aggregate comparison methodology and its results are part of the
   evaluation materials.

## Honesty notes

- Gaps in the record are real and never back-filled: a re-run would be
  timestamped after the event, which would defeat the record's purpose.
- Files are first-write-final. Nothing in this repository is ever revised.
