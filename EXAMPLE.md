# A worked example, receipt-style

One forecast from this record, next to the aviation-authority declaration
that covered the same area. Every element below is checkable.

## 1. The forecast (in this repository)

File: [`reports/forecast/2026-08-03/10_h12.parquet`](reports/forecast/2026-08-03/10_h12.parquet) — 6 high-confidence
cell(s):

| lat | lng | probability | target (UTC) | distance from NOTAM center |
|---|---|---|---|---|
| 54.457 | 23.056 | 0.94 | 2026-08-03 22:00 UTC | 81 nm |
| 54.291 | 22.933 | 0.94 | 2026-08-03 22:00 UTC | 90 nm |
| 54.338 | 23.141 | 0.94 | 2026-08-03 22:00 UTC | 89 nm |
| 54.456 | 23.094 | 0.95 | 2026-08-03 22:00 UTC | 81 nm |
| 54.573 | 23.121 | 0.94 | 2026-08-03 22:00 UTC | 75 nm |
| 54.591 | 23.066 | 0.94 | 2026-08-03 22:00 UTC | 73 nm |

Committed at **2026-08-03 10:07 UTC** (commit
`a129e6f23911` in the primary record; this mirror carries the same
bytes — compare them yourself). The forecast was committed **11.9 h before its target hour**.

## 2. The authority declaration (context, stated up front)

**NOTAM A5014/26** (EYVL, issued by EYVN),
in effect **since 2026-07-29 05:10 UTC**, radius 155 nm:

> PRECAUTION-GNSS SIGNAL JAMMING AND SPOOFING CAN BE  EXPECTED IN
VILNIUS FIR  MOSTLY IN WESTERN AND SOUTHERN PARTS. CONVENTIONAL
NAV AIDS AVAILABLE  AND MAY BE USED AS RECOMENDED  IN EASA  SIB
2022-02R4. AIR  CREW  ARE AS

This is a blanket area warning — 155 nautical miles, open-ended.
It cannot say which cells or which hour. **The model never reads NOTAMs**; they
are used only to grade it. The forecast above is the model's own call — specific
cells, a specific hour, committed before the window — inside an area the
authority had flagged.

Look it up yourself on any public NOTAM service (e.g. FAA NOTAM Search,
notams.aim.faa.gov — free): search location EYVL, NOTAM A5014/26.

## 3. The overlap

All 6 cell(s) sit 73–90 nm from the NOTAM center — inside its
155 nm radius. Great-circle math; any calculator confirms it.

## What this example shows — and what it does not

- **Shows:** one high-confidence forecast was committed hours before its target window; at that window the same area was covered by an independent authority GPS-interference declaration.
- **Does not show:** prediction of the declaration itself (it was standing), or per-event skill.

> **Scope note:** the authority declaration was ALREADY ACTIVE at commit time (standing NOTAM) — stated up front, not discovered. It is a blanket area warning with no end date; it cannot say which cells or which hour. The model never reads NOTAMs (they are used only to grade it). This receipt shows the model's own call — specific cells, a specific hour, committed before the window — inside an area the authority had flagged. It does NOT claim the declaration was predicted.

Timing for rows dated before 2026-08-02 is anchored by the primary record
(daily HEAD stamps in [`proofs/primary/`](proofs/primary/) — see
[`VERIFY.md`](VERIFY.md)); from 2026-08-02 onward, this repository's own
commits are the anchored, commit-before-window record.

*Generated 2026-08-03 23:55 UTC from the
live receipt pipeline; a single example illustrates the mechanics — the
statistical evidence is the aggregate record.*
