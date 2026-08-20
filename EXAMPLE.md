# A worked example, receipt-style

One forecast from this record, next to the aviation-authority declaration
that covered the same area. Every element below is checkable.

## 1. The forecast (in this repository)

File: [`reports/forecast/2026-08-04/11_h6.parquet`](reports/forecast/2026-08-04/11_h6.parquet) — 19 high-confidence
cell(s):

| lat | lng | probability | target (UTC) | distance from NOTAM center |
|---|---|---|---|---|
| 55.428 | 21.107 | 0.88 | 2026-08-04 17:00 UTC | 96 nm |
| 55.330 | 20.575 | 0.90 | 2026-08-04 17:00 UTC | 114 nm |
| 55.346 | 20.557 | 0.91 | 2026-08-04 17:00 UTC | 114 nm |
| 55.379 | 20.558 | 0.91 | 2026-08-04 17:00 UTC | 113 nm |
| 55.363 | 20.538 | 0.90 | 2026-08-04 17:00 UTC | 114 nm |
| 55.396 | 20.539 | 0.91 | 2026-08-04 17:00 UTC | 113 nm |
| 55.330 | 20.952 | 0.87 | 2026-08-04 17:00 UTC | 104 nm |
| 55.561 | 20.545 | 0.91 | 2026-08-04 17:00 UTC | 108 nm |
| 55.594 | 20.546 | 0.89 | 2026-08-04 17:00 UTC | 107 nm |
| 55.627 | 20.547 | 0.84 | 2026-08-04 17:00 UTC | 106 nm |
| 55.610 | 20.528 | 0.83 | 2026-08-04 17:00 UTC | 107 nm |
| 55.478 | 20.561 | 0.90 | 2026-08-04 17:00 UTC | 110 nm |
| 55.495 | 20.543 | 0.91 | 2026-08-04 17:00 UTC | 110 nm |
| 55.429 | 20.541 | 0.91 | 2026-08-04 17:00 UTC | 112 nm |
| 55.429 | 20.578 | 0.90 | 2026-08-04 17:00 UTC | 111 nm |
| 55.412 | 20.559 | 0.91 | 2026-08-04 17:00 UTC | 112 nm |
| 55.445 | 20.522 | 0.90 | 2026-08-04 17:00 UTC | 112 nm |
| 55.445 | 20.560 | 0.91 | 2026-08-04 17:00 UTC | 111 nm |
| 55.528 | 20.544 | 0.91 | 2026-08-04 17:00 UTC | 109 nm |

Committed at **2026-08-04 12:40 UTC**, in THIS
repository's commit `73519b8f300c` — which you can open here:
[`73519b8f300c`](../../commit/73519b8f300c961d0f5c714942bb8ee3676d35e8). The forecast was committed **4.3 h before its target hour**.

**Bitcoin bound — check this without installing anything.** The mirror commit carrying this file, `73519b8f300c`, is timestamped into **Bitcoin block 961016**
(proof: [`proofs/mirror/73519b8f300c961d0f5c714942bb8ee3676d35e8.sha.ots`](proofs/mirror/73519b8f300c961d0f5c714942bb8ee3676d35e8.sha.ots)). Open that block on any explorer —
[mempool.space/block/961016](https://mempool.space/block/961016) or [blockstream.info/block-height/961016](https://blockstream.info/block-height/961016) —
and read its timestamp. No one, including us, can move a Bitcoin block's time. Git commit
times are self-settable; this is not.


## 2. The authority declaration (context, stated up front)

**NOTAM A3951/26** (EVRR, issued by EVRA),
in effect **since 2026-07-20 14:40 UTC**, radius 165 nm:

> PRECAUTION GNSS SIGNAL INTERFERENCE CAN BE EXPECTED AND MAY 
RESULT IN UNRELIABLE OR UNAVAILABLE GPS SIGNALS WITHIN RIGA FIR. 
CONVENTIONAL NAV AIDS AVAILABLE AND MAY BE USED AS RECOMMENDED IN 
EASA SIB 2022-02R3 

POSSI

This is a blanket area warning — 165 nautical miles, open-ended.
It cannot say which cells or which hour. **The model never reads NOTAMs**; they
are used only to grade it. The forecast above is the model's own call — specific
cells, a specific hour, committed before the window — inside an area the
authority had flagged.

Look it up yourself on any public NOTAM service. For European FIRs the
authoritative source is EUROCONTROL's European AIS Database (EAD) public
interface, or the issuing state's own AIS; the FAA's NOTAM Search
(notams.aim.faa.gov, free) also carries international NOTAMs and needs no
account. Search location EVRR, NOTAM A3951/26.

## 3. The overlap

All 19 cell(s) sit 96–114 nm from the NOTAM center — inside its
165 nm radius. Great-circle math; any calculator confirms it.

## What this example shows — and what it does not

- **Shows:** one high-confidence forecast was committed hours before its target window; at that window the same area was covered by an independent authority GPS-interference declaration.
- **Does not show:** prediction of the declaration itself (it was standing), or per-event skill.

> **Scope note:** the authority declaration was ALREADY ACTIVE at commit time (standing NOTAM) — stated up front, not discovered. It is a blanket area warning with no end date; it cannot say which cells or which hour. The model never reads NOTAMs (they are used only to grade it). This receipt shows the model's own call — specific cells, a specific hour, committed before the window — inside an area the authority had flagged. It does NOT claim the declaration was predicted.

Timing for rows dated before 2026-08-02 is anchored by the primary record
(daily HEAD stamps in [`proofs/primary/`](proofs/primary/) — see
[`VERIFY.md`](VERIFY.md)); from 2026-08-02 onward, this repository's own
commits are the anchored, commit-before-window record.

*Generated 2026-08-05 12:19 UTC from the
live receipt pipeline; a single example illustrates the mechanics — the
statistical evidence is the aggregate record.*
