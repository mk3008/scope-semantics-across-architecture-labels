# Run records

| run | requested model/effort | fresh | starting SHA | packet hash | result | metadata |
| --- | --- | --- | --- | --- | --- | --- |
| Stage 1 implementation | Terra / medium | requested fresh | `454d4d1` | original/amended test path before correction | **rejected** — frozen-test DDL path defect (`ENOENT`) before behavior test | actual model/session/timestamp unverified |
| Stage 1 clean rerun 1 | Terra / medium | requested fresh | `454d4d1` | first path amendment | **rejected** — same path defect remained; source not adopted | actual model/session/timestamp unverified |
| Stage 1 clean rerun 2 | Terra / medium | requested fresh | `c5d9d04` | amended DDL + Stage 1 packet | **adopted implementation snapshot** — PostgreSQL integration tests 2/2 pass | actual model/session/timestamp unverified |
| Stage 1 calibrated consistency review | Sol / medium | requested fresh/read-only | `c5d9d04` | cumulative Stage 1 | **adopted review** — HUMAN_BLOCKER none; found transaction-start expiry and numeric NaN implementation defects | actual model/session/timestamp unverified |
| Stage 1 transaction-start expiry fix | Terra / medium | requested fresh | `c5d9d04` | current Stage 1 | **adopted post-resolution snapshot** — changed comparison to statement-time; tests 2/2 pass | actual model/session/timestamp unverified |
| Stage 1 numeric NaN fix | Terra / medium | requested fresh | `c5d9d04` | current Stage 1 | **adopted post-resolution snapshot** — rejects NaN line values; tests 2/2 pass | actual model/session/timestamp unverified |
| Stage 1 refactoring mis-dispatch | Terra / medium | requested fresh | `c5d9d04` | current Stage 1 | **aborted** immediately: dispatched against resolution directory; outcome not adopted and directory not reused | actual model/session/timestamp unverified |
| Stage 1 refactoring rerun 1 | Terra / medium | requested fresh | `8459463` | current Stage 1 filtered rules | **adopted** — PostgreSQL integration/cumulative acceptance tests 2/2 pass | actual model/session/timestamp unverified |

## Worker-rule filtering

The historical Business Rule timeline is not worker input. Before each Stage, Codex creates a `current accepted Business Rules` snapshot containing only rules active through that Stage. Stage 1 workers receive no Stage 2/3 pending rules; Stage 2 workers receive no Stage 3+ rules. Future packets, reviewer outputs from future state, and unrelated evidence are excluded.
