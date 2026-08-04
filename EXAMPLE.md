# A worked example, receipt-style

One forecast from this record, next to the aviation-authority declaration
that covered the same area. Every element below is checkable.

## 1. The forecast (in this repository)

File: [`reports/forecast/2026-08-02/10_h3.parquet`](reports/forecast/2026-08-02/10_h3.parquet) — 18 high-confidence
cell(s):

| lat | lng | probability | target (UTC) | distance from NOTAM center |
|---|---|---|---|---|
| 54.121 | 19.428 | 0.89 | 2026-08-02 13:00 UTC | 144 nm |
| 54.121 | 19.465 | 0.90 | 2026-08-02 13:00 UTC | 144 nm |
| 54.137 | 19.410 | 0.91 | 2026-08-02 13:00 UTC | 144 nm |
| 54.138 | 19.447 | 0.91 | 2026-08-02 13:00 UTC | 143 nm |
| 54.120 | 19.391 | 0.89 | 2026-08-02 13:00 UTC | 145 nm |
| 54.103 | 19.372 | 0.87 | 2026-08-02 13:00 UTC | 147 nm |
| 54.089 | 19.686 | 0.85 | 2026-08-02 13:00 UTC | 140 nm |
| 54.153 | 19.281 | 0.83 | 2026-08-02 13:00 UTC | 147 nm |
| 54.136 | 19.336 | 0.82 | 2026-08-02 13:00 UTC | 146 nm |
| 54.137 | 19.373 | 0.90 | 2026-08-02 13:00 UTC | 145 nm |
| 54.120 | 19.354 | 0.89 | 2026-08-02 13:00 UTC | 146 nm |
| 54.153 | 19.318 | 0.89 | 2026-08-02 13:00 UTC | 146 nm |
| 54.186 | 19.207 | 0.70 | 2026-08-02 13:00 UTC | 148 nm |
| 54.186 | 19.244 | 0.83 | 2026-08-02 13:00 UTC | 146 nm |
| 54.173 | 19.669 | 0.85 | 2026-08-02 13:00 UTC | 136 nm |
| 54.190 | 19.651 | 0.82 | 2026-08-02 13:00 UTC | 136 nm |
| 54.138 | 19.484 | 0.89 | 2026-08-02 13:00 UTC | 142 nm |
| 54.207 | 19.669 | 0.84 | 2026-08-02 13:00 UTC | 135 nm |

Committed at **2026-08-02 11:40 UTC** (commit
`8701a5968495` in the primary record; this mirror carries the same
bytes — compare them yourself). The forecast was committed **1.3 h before its target hour**.

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

All 18 cell(s) sit 135–148 nm from the NOTAM center — inside its
155 nm radius. Great-circle math; any calculator confirms it.

## What this example shows — and what it does not

- **Shows:** one high-confidence forecast was committed hours before its target window; at that window the same area was covered by an independent authority GPS-interference declaration.
- **Does not show:** prediction of the declaration itself (it was standing), or per-event skill.

> **Scope note:** the authority declaration was ALREADY ACTIVE at commit time (standing NOTAM) — stated up front, not discovered. It is a blanket area warning with no end date; it cannot say which cells or which hour. The model never reads NOTAMs (they are used only to grade it). This receipt shows the model's own call — specific cells, a specific hour, committed before the window — inside an area the authority had flagged. It does NOT claim the declaration was predicted.

Timing for rows dated before 2026-08-02 is anchored by the primary record
(daily HEAD stamps in [`proofs/primary/`](proofs/primary/) — see
[`VERIFY.md`](VERIFY.md)); from 2026-08-02 onward, this repository's own
commits are the anchored, commit-before-window record.

*Generated 2026-08-04 13:09 UTC from the
live receipt pipeline; a single example illustrates the mechanics — the
statistical evidence is the aggregate record.*
