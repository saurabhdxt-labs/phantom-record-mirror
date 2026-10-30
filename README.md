# PHANTOM — public GNSS-interference forecast record

**Live, hourly forecasts of GPS/GNSS interference — committed to this
repository BEFORE the window each forecast predicts, and timestamped into
Bitcoin so the record cannot be back-dated. By anyone, including us.**

Interference with satellite navigation is usually discovered reactively: a
receiver degrades mid-flight, a notice is filed afterward. PHANTOM forecasts
it up to 12 hours ahead, per ~5 km cell, refreshed hourly — and this record
exists so nobody has to take that claim on faith.

**Live replay of the graded record (hits AND misses):
https://phantom.saurabhdxt.com**

## What is in this repository

| Path | Content |
|---|---|
| `reports/forecast/<date>/<HH>_h<horizon>.parquet` | One file per observation hour and horizon (3/6/12 h). Exactly six columns: `h3_index, date, hour_observed, hour_target, horizon_h, probability`. |
| `proofs/mirror/` | OpenTimestamps proof of each of this repository's own commits — Bitcoin-verifiable timing. |
| `proofs/primary/` | Daily HEAD stamps of the primary record (maintained since June 2026), each anchoring its entire commit ancestry. |
| [`VERIFY.md`](VERIFY.md) | Step-by-step: verify the Bitcoin timing yourself, and check outcomes against aviation-authority NOTAMs. |
| [`EXAMPLE.md`](EXAMPLE.md) | A worked example: one forecast in this repo, next to the authority NOTAM that covered the same area, with the overlap arithmetic. |

Each row is a calibrated probability that the given cell experiences GNSS
degradation at the target hour. Rows with `probability >= 0.7` are the
record's graded high-confidence level.

## Machine-readable index

`index/<day>.json` lists, for one record day, every forecast file present,
the commit in THIS repository that first added it, that commit's time, the
lead in minutes before the hour the file forecasts, whether it was late
(committed at or after that hour), and whether a proof file exists for that
commit. `index/latest.json` names the newest day and lists every indexed day.
The commit times are this repository's own git times — self-reported, and
reproducible with `git log` — not the Bitcoin bound; the `proof` field is a
structural presence check of `proofs/mirror/<commit>.sha.ots`,
not a Bitcoin verification. Index updates land in their own `index:` commits, separate from
the forecast and `anchor:` commits, and are not themselves timestamped.

## Why a mirror

This repository mirrors the primary anchored record from 2026-07-31 onward and
carries its own independent verification history from its first commit. The
pre-2026-07-31 record is maintained in the primary record repository and is
available for inspection during evaluation; its daily HEAD stamps are
published here under `proofs/primary/`.

## Honesty rules this record lives by

- **Committed before the window, or it does not count.** The binding time
  bound is a Bitcoin block, not a git timestamp — see `VERIFY.md`, which also
  names the rows that were committed late.
- **Gaps are real.** A missing hour stays missing. Where an outage recovery
  committed a row at or after the hour it covers, the row is kept but does
  not count as a forecast of that hour; a gapless record would be less
  believable, not more.
- **Forecast records are first-write-final.** No file under
  `reports/forecast/` is ever revised; a re-run would be timestamped after the
  event, which would defeat the record's purpose.
- **Two things DO change, by design, and you can see both in `git log`:**
  the documentation pages (`README.md`, `VERIFY.md`, `EXAMPLE.md`) are
  regenerated from a versioned template when their wording improves; and
  timestamp proofs under `proofs/` are upgraded IN PLACE from *pending* to
  *confirmed* as Bitcoin aggregation completes. An upgrade appends the block
  attestation to an existing proof — it never alters what was stamped, and the
  original digest is unchanged. We state this because `git log --name-only`
  shows those files touched more than once, and we would rather explain it
  than have you find it and wonder.
- **Misses stay in the record.** The replay shows them.

## Contact

Evaluation, verification walk-through, or data questions:
**saurabh@saurabhdxt.com**

*All rights reserved. The record is published for verification; the
forecasting method is proprietary.*
