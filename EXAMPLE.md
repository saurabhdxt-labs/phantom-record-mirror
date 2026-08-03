# A worked example, receipt-style

One forecast from this record, next to the aviation-authority declaration
that covered the same area. Every element below is checkable.

## 1. The forecast (in this repository)

File: [`reports/forecast/2026-07-31/04_h12.parquet`](reports/forecast/2026-07-31/04_h12.parquet) — 11 high-confidence
cell(s):

| lat | lng | probability | target (UTC) | distance from NOTAM center |
|---|---|---|---|---|
| 54.001 | 23.116 | 0.79 | 2026-07-31 16:00 UTC | 108 nm |
| 54.172 | 22.981 | 0.88 | 2026-07-31 16:00 UTC | 97 nm |
| 54.157 | 22.924 | 0.88 | 2026-07-31 16:00 UTC | 98 nm |
| 54.206 | 22.983 | 0.87 | 2026-07-31 16:00 UTC | 95 nm |
| 54.132 | 23.311 | 0.72 | 2026-07-31 16:00 UTC | 102 nm |
| 54.039 | 22.860 | 0.86 | 2026-07-31 16:00 UTC | 104 nm |
| 53.989 | 22.838 | 0.75 | 2026-07-31 16:00 UTC | 107 nm |
| 54.023 | 22.841 | 0.86 | 2026-07-31 16:00 UTC | 105 nm |
| 54.089 | 22.919 | 0.86 | 2026-07-31 16:00 UTC | 102 nm |
| 54.072 | 22.900 | 0.86 | 2026-07-31 16:00 UTC | 103 nm |
| 54.059 | 22.695 | 0.81 | 2026-07-31 16:00 UTC | 103 nm |

Committed at **2026-07-31 04:26 UTC** (commit
`5bbcf106ceea` in the primary record; this mirror carries the same
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

All 11 cell(s) sit 95–108 nm from the NOTAM center — inside its
155 nm radius. Great-circle math; any calculator confirms it.

## What this example shows — and what it does not

- **Shows:** one high-confidence forecast was committed hours before its target window; at that window the same area was covered by an independent authority GPS-interference declaration.
- **Does not show:** prediction of the declaration itself (it was standing), or per-event skill.

> **Scope note:** the authority declaration was ALREADY ACTIVE at commit time (standing NOTAM). This receipt proves the forecast was committed hours before its target window and that an independent authority declaration covered the same area at that window — it does NOT claim the declaration was predicted.

Timing for rows dated before 2026-08-02 is anchored by the primary record
(daily HEAD stamps in [`proofs/primary/`](proofs/primary/) — see
[`VERIFY.md`](VERIFY.md)); from 2026-08-02 onward, this repository's own
commits are the anchored, commit-before-window record.

*Generated 2026-08-03 15:56 UTC from the
live receipt pipeline; a single example illustrates the mechanics — the
statistical evidence is the aggregate record.*
