# A worked example, receipt-style

One forecast from this record, next to the aviation-authority declaration
that covered the same area. Every element below is checkable.

## 1. The forecast (in this repository)

File: [`reports/forecast/2026-07-31/01_h12.parquet`](reports/forecast/2026-07-31/01_h12.parquet) — 9 high-confidence
cell(s):

| lat | lng | probability | target (UTC) | distance from NOTAM center |
|---|---|---|---|---|
| 54.389 | 23.089 | 0.88 | 2026-07-31 13:00 UTC | 85 nm |
| 54.357 | 23.012 | 0.84 | 2026-07-31 13:00 UTC | 87 nm |
| 54.476 | 22.965 | 0.85 | 2026-07-31 13:00 UTC | 79 nm |
| 54.406 | 23.109 | 0.88 | 2026-07-31 13:00 UTC | 84 nm |
| 54.276 | 22.839 | 0.88 | 2026-07-31 13:00 UTC | 90 nm |
| 54.289 | 23.044 | 0.88 | 2026-07-31 13:00 UTC | 91 nm |
| 54.255 | 23.042 | 0.88 | 2026-07-31 13:00 UTC | 93 nm |
| 54.506 | 23.116 | 0.88 | 2026-07-31 13:00 UTC | 79 nm |
| 54.539 | 23.155 | 0.88 | 2026-07-31 13:00 UTC | 77 nm |

Committed at **2026-07-31 01:25 UTC** (commit
`c971b3d96070` in the primary record; this mirror carries the same
bytes — compare them yourself). The forecast was committed **11.6 h before its target hour**.

## 2. The authority declaration

**NOTAM A5014/26** (EYVL, issued by EYVN),
effective **2026-07-29 05:10 UTC**, radius 155 nm:

> PRECAUTION-GNSS SIGNAL JAMMING AND SPOOFING CAN BE  EXPECTED IN
VILNIUS FIR  MOSTLY IN WESTERN AND SOUTHERN PARTS. CONVENTIONAL
NAV AIDS AVAILABLE  AND MAY BE USED AS RECOMENDED  IN EASA  SIB
2022-02R4. AIR  CREW  ARE AS

Look it up yourself on any public NOTAM service (e.g. FAA NOTAM Search,
notams.aim.faa.gov — free): search location EYVL, NOTAM A5014/26.

## 3. The overlap

All 9 cell(s) sit 77–93 nm from the NOTAM center — inside its
155 nm radius. Great-circle math; any calculator confirms it.

## What this example shows — and what it does not

- **Shows:** one high-confidence forecast was committed hours before its target window; at that window the same area was covered by an independent authority GPS-interference declaration.
- **Does not show:** prediction of the declaration itself (it was standing), or per-event skill.

> **Scope note:** the authority declaration was ALREADY ACTIVE at commit time (standing NOTAM). This receipt proves the forecast was committed hours before its target window and that an independent authority declaration covered the same area at that window — it does NOT claim the declaration was predicted.

Timing for rows dated before 2026-08-02 is anchored by the primary record
(daily HEAD stamps in [`proofs/primary/`](proofs/primary/) — see
[`VERIFY.md`](VERIFY.md)); from 2026-08-02 onward, this repository's own
commits are the anchored, commit-before-window record.

*Generated 2026-08-01 16:45 UTC from the
live receipt pipeline; a single example illustrates the mechanics — the
statistical evidence is the aggregate record.*
