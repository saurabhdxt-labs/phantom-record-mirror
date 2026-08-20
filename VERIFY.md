# Verify this record yourself

Nothing here asks for trust. Two independent checks, both runnable by anyone.

## 1. Timing — the Bitcoin bound

Every forecast file was committed BEFORE the window it predicts. Git commit
times alone are self-settable, so the binding bound is Bitcoin:

- `proofs/mirror/` — an OpenTimestamps stamp of each of this repository's own
  sync commits, made with the open-source `ots` client.

  **Two ways to check one. Start with (b) — it needs nothing installed.**

  **(a) Full verification, if you run a Bitcoin node:**
  `ots verify proofs/mirror/<commit>.sha.ots`
  Note this reads the block from a LOCAL Bitcoin node. Without one it reports
  `Could not connect to Bitcoin node` — that is the absence of a node on your
  machine, not a failure of the proof.

  **(b) Node-free, and sufficient for the timing claim:**
  `ots info proofs/mirror/<commit>.sha.ots`
  The output names a **Bitcoin block height**. Look that block up on any
  public explorer (blockstream.info, mempool.space, blockchain.com) and read
  its timestamp. That timestamp is a hard upper bound on when the commit —
  and every forecast file inside it — already existed. Nothing in this
  repository, and no action by us, can move a Bitcoin block's time.

  Worked example you can run today:
  `proofs/mirror/003aee6d9c56f5c58859e327fb93906448f98411.sha.ots` resolves to
  **Bitcoin block 961735**. That commit contains
  `reports/forecast/2026-08-09/12_h12.parquet` — a 12-hour-ahead forecast for
  the hour beginning 2026-08-10T00:00Z. Confirm the block predates the
  forecast hour, and the ordering is settled without trusting us.
- `proofs/primary/` — the daily HEAD stamps of the primary record repository
  (maintained since 2026-06; this mirror starts 2026-07-31). Each HEAD stamp
  anchors the primary record's entire commit ancestry via git's parent-hash
  chain. The primary repository is available for inspection during evaluation.
- Freshly created stamps are *pending* until Bitcoin aggregation completes
  (typically hours); `ots upgrade` completes them. Pending is a queue state,
  not a weaker claim — and it only ever affects the most recent stamps, so
  pick an older one if you want a confirmed proof immediately.

## 2. Outcomes — aviation-authority NOTAMs

Forecast rows with `probability >= 0.7` are the record's graded high-
confidence level. To check outcomes against an independent authority source:

1. Pick a date and area from `reports/forecast/`.
2. Pull that day's GPS-interference NOTAMs for the area from any public
   NOTAM service — EUROCONTROL EAD or the issuing state's AIS for European
   FIRs, the FAA's free NOTAM Search for a no-account option, or your own
   aviation-data provider.
3. Compare where the high-confidence rows fall against the areas the
   authorities declared. NOTAMs are declarations, not per-hour ground truth —
   the aggregate comparison methodology and its results are part of the
   evaluation materials.

## Honesty notes

- Gaps in the record are real and never back-filled: a re-run would be
  timestamped after the event, which would defeat the record's purpose.
- Files are first-write-final. Nothing in this repository is ever revised.
