# PHANTOM — public forecast record (mirror)

Hourly GPS/GNSS-interference forecasts, committed BEFORE the window each
forecast predicts. One parquet per (observation hour, horizon):
`reports/forecast/<date>/<HH>_h<horizon>.parquet` with exactly six columns —
`h3_index, date, hour_observed, hour_target, horizon_h, probability`.

This repository mirrors the primary anchored record from 2026-08-01 onward and
carries its own independent verification history from its first commit.
The pre-2026-08-01 record (which this mirror does not contain) is maintained in
the primary record repository and is available for inspection during
evaluation. Gaps are real and never back-filled — a re-run would be
timestamped after the event, which would defeat the record's purpose.
