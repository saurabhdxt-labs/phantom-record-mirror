# A worked example, receipt-style

One forecast from this record, next to the aviation-authority declaration
that covered the same area. Every element below is checkable.

## 1. The forecast (in this repository)

File: [`reports/forecast/2026-07-31/09_h3.parquet`](reports/forecast/2026-07-31/09_h3.parquet) — 14 high-confidence
cell(s):

| lat | lng | probability | target (UTC) | distance from NOTAM center |
|---|---|---|---|---|
| 32.687 | 34.955 | 0.89 | 2026-07-31 12:00 UTC | 79 nm |
| 32.647 | 34.949 | 0.90 | 2026-07-31 12:00 UTC | 77 nm |
| 32.665 | 34.966 | 0.90 | 2026-07-31 12:00 UTC | 78 nm |
| 32.624 | 34.959 | 0.90 | 2026-07-31 12:00 UTC | 75 nm |
| 32.635 | 34.877 | 0.86 | 2026-07-31 12:00 UTC | 77 nm |
| 32.672 | 34.911 | 0.90 | 2026-07-31 12:00 UTC | 79 nm |
| 32.690 | 34.928 | 0.89 | 2026-07-31 12:00 UTC | 79 nm |
| 32.650 | 34.921 | 0.90 | 2026-07-31 12:00 UTC | 77 nm |
| 32.668 | 34.938 | 0.90 | 2026-07-31 12:00 UTC | 78 nm |
| 32.675 | 34.883 | 0.89 | 2026-07-31 12:00 UTC | 79 nm |
| 32.654 | 34.894 | 0.90 | 2026-07-31 12:00 UTC | 78 nm |
| 32.628 | 34.932 | 0.90 | 2026-07-31 12:00 UTC | 76 nm |
| 32.613 | 34.887 | 0.87 | 2026-07-31 12:00 UTC | 76 nm |
| 32.632 | 34.904 | 0.90 | 2026-07-31 12:00 UTC | 76 nm |

Committed at **2026-07-31 09:28 UTC** (commit
`fcd3fd835233` in the primary record; this mirror carries the same
bytes — compare them yourself). The forecast was committed **2.5 h before its target hour**.

## 2. The authority declaration (context, stated up front)

**NOTAM A0596/26** (LLLL, issued by LLAD),
in effect **since 2026-07-28 10:45 UTC**, radius 117 nm:

> POSS INTRP TO AIRBORNE GNSS EQPT WI TEL-AVIV FIR.

This is a blanket area warning — 117 nautical miles, open-ended.
It cannot say which cells or which hour. **The model never reads NOTAMs**; they
are used only to grade it. The forecast above is the model's own call — specific
cells, a specific hour, committed before the window — inside an area the
authority had flagged.

Look it up yourself on any public NOTAM service (e.g. FAA NOTAM Search,
notams.aim.faa.gov — free): search location LLLL, NOTAM A0596/26.

## 3. The overlap

All 14 cell(s) sit 75–79 nm from the NOTAM center — inside its
117 nm radius. Great-circle math; any calculator confirms it.

## What this example shows — and what it does not

- **Shows:** one high-confidence forecast was committed hours before its target window; at that window the same area was covered by an independent authority GPS-interference declaration.
- **Does not show:** prediction of the declaration itself (it was standing), or per-event skill.

> **Scope note:** the authority declaration was ALREADY ACTIVE at commit time (standing NOTAM) — stated up front, not discovered. It is a blanket area warning with no end date; it cannot say which cells or which hour. The model never reads NOTAMs (they are used only to grade it). This receipt shows the model's own call — specific cells, a specific hour, committed before the window — inside an area the authority had flagged. It does NOT claim the declaration was predicted.

Timing for rows dated before 2026-08-02 is anchored by the primary record
(daily HEAD stamps in [`proofs/primary/`](proofs/primary/) — see
[`VERIFY.md`](VERIFY.md)); from 2026-08-02 onward, this repository's own
commits are the anchored, commit-before-window record.

*Generated 2026-08-04 02:20 UTC from the
live receipt pipeline; a single example illustrates the mechanics — the
statistical evidence is the aggregate record.*
