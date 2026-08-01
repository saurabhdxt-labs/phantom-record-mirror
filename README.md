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

Each row is a calibrated probability that the given cell experiences GNSS
degradation at the target hour. Rows with `probability >= 0.7` are the
record's graded high-confidence level.

## Why a mirror

This repository mirrors the primary anchored record from 2026-08-01 onward and
carries its own independent verification history from its first commit. The
pre-2026-08-01 record is maintained in the primary record repository and is
available for inspection during evaluation; its daily HEAD stamps are
published here under `proofs/primary/`.

## Honesty rules this record lives by

- **Committed before the window.** The binding time bound is a Bitcoin block,
  not a git timestamp — see `VERIFY.md`.
- **Gaps are real and never back-filled.** A re-run would be timestamped
  after the event; a gapless record would be less believable, not more.
- **Files are first-write-final.** Nothing here is ever revised.
- **Misses stay in the record.** The replay shows them.

## Contact

Evaluation, verification walk-through, or data questions:
**saurabh@saurabhdxt.com**

*All rights reserved. The record is published for verification; the
forecasting method is proprietary (patent pending).*
