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
| Stage 2 implementation | Terra / medium | requested fresh | `87418fa` | Stage 2 filtered rules | behavior test pass 1/1; **not adopted pending blocker resolution** | actual model/session/timestamp unverified |
| Stage 2 consistency review | Sol / medium | requested fresh/read-only | `87418fa` | cumulative Stage 2 | **HUMAN_BLOCKER** — five under-specifications, conditional data-model insufficiency; one non-blocking implementation defect | actual model/session/timestamp unverified |
| Stage 2 resolution rerun 1 | Terra / medium | requested fresh | `6a6c66e` | HD-005..009 + current Stage 2 | **rejected** — worker edited frozen acceptance test; source output not adopted | actual model/session/timestamp unverified |
| Stage 2 resolution rerun 2 | Terra / medium | requested fresh | `a295f98` | HD-005..009 + old test | **rejected** — old acceptance test conflicts with HD-007; test defect amendment recorded | actual model/session/timestamp unverified |
| Stage 2 resolution rerun 3 | Terra / medium | requested fresh | `a295f98` | HD-005..009 + amended test | **adopted implementation** — PostgreSQL test 1/1 pass | actual model/session/timestamp unverified |
| Stage 2 post-decision review | Sol / medium | requested fresh/read-only | `a295f98` | cumulative Stage 2 | HUMAN_BLOCKER none; HD-007 implementation gap found | actual model/session/timestamp unverified |
| Stage 2 consistency resolution | Terra / medium | requested fresh | `a295f98` | HD-007 gap only | **adopted post-resolution snapshot** — PostgreSQL test 1/1 pass | actual model/session/timestamp unverified |
| Stage 2 refactoring rerun 1 | Terra / medium | requested fresh | `a295f98` | current Stage 2 filtered rules | **adopted** — PostgreSQL test 1/1 pass | actual model/session/timestamp unverified |
| Stage 3 implementation | Terra / medium | requested fresh | `448135a` | Stage 3 filtered rules | behavior test 1/1 pass; **not adopted pending blocker resolution** | actual model/session/timestamp unverified |
| Stage 3 consistency review | Sol / medium | requested fresh/read-only | `448135a` | cumulative Stage 3 | **HUMAN_BLOCKER** — performer authority/confirmation ownership; conditional actor-data insufficiency | actual model/session/timestamp unverified |
| Stage 1+2 post-review cumulative repair | operator verification | n/a | `a0cd6ca` adopted Stage 2 refactoring snapshot | `cumulative-stage2-repair.test.js` | **adopted evaluation-instrument repair** — PostgreSQL cumulative acceptance 2/2 pass | not original preregistered cumulative evidence; timestamp unverified |
| Stage 3 HD-010 resolution implementation | Terra / medium | requested fresh | `749f4b5` | amended DDL + self-contained rules v2 + cumulative Stage 3 | **unadopted pending review blockers** — PostgreSQL cumulative acceptance 2/2 pass; frozen test hash unchanged | actual model/session/timestamp unverified |
| Stage 3 HD-010 consistency review | Sol / medium | requested fresh/read-only | `749f4b5` | Stage 1–3 current state | **HUMAN_BLOCKER** — HB-S3-02 inconsistency and HB-S3-03 data-model insufficiency; three implementation/instrument defects | actual model/session/timestamp unverified; test not executed by read-only reviewer |
| Stage 3 HD-011/012 resolution rerun 2 | Terra / medium | requested fresh | `6ad7c9c` | amended DDL + cumulative v2 | **superseded by defect resolution** — cumulative PostgreSQL 3/3 pass | actual model/session/timestamp unverified |
| Stage 3 fresh Sol review / re-review | Sol / medium | requested fresh/read-only | `6ad7c9c` / `f18da4d` | current Stage 1–3 | HB-S3-02/03 resolved; no HUMAN_BLOCKER; implementation/instrument defects found and repaired | actual model/session/timestamp unverified |
| Stage 3 coherence resolution rerun 3 | Terra / medium | requested fresh | `02b64dd` | cumulative v4 | **adopted implementation candidate** — PostgreSQL cumulative 3/3 pass | actual model/session/timestamp unverified |
| Stage 3 final Sol review | Sol / medium | requested fresh/read-only | `02b64dd` | current Stage 1–3 | HUMAN_BLOCKER none; implementation defect none | actual model/session/timestamp unverified |
| Stage 3 refactoring rerun 1 | Terra / medium | requested fresh | `02b64dd` | cumulative v4 | **adopted** — PostgreSQL cumulative 3/3 pass | actual model/session/timestamp unverified |

## Protocol amendment 001

The original preregistration's frozen-cumulative-test claim was not realized for Stage 1/2, and Stage 5/6 placeholders are not executable acceptance tests. `PROTOCOL_AMENDMENT_001.md` records the correction, pre-release-only scope, and prospective cumulative rule. The Stage 1+2 repair is distinct retrospective evidence.

## Worker-rule filtering

The historical Business Rule timeline is not worker input. Before each Stage, Codex creates a `current accepted Business Rules` snapshot containing only rules active through that Stage. Stage 1 workers receive no Stage 2/3 pending rules; Stage 2 workers receive no Stage 3+ rules. Future packets, reviewer outputs from future state, and unrelated evidence are excluded.

From Stage 3 resolution forward, each worker input must reproduce the complete text of all active rules, rather than only rule IDs. It additionally contains exact current DDL, cumulative requirements, applicable decisions, current adopted source, current cumulative acceptance, current packet, and the fixed placement sentence. The initial DDL deliberately exposes future tables; that leakage is a validity limitation, not future-packet disclosure.
