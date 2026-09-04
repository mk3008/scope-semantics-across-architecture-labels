# Blockers

## Stage 1 — resolved by HD-001 through HD-004

Fresh Sol review found expiry semantics, line cardinality, identifier/performer scope, and DDL association ambiguity. Human decisions are appended in `HUMAN_DECISIONS.md`; canonical association required `DDL_AMENDMENT_001.md`. Search and serialization details are now recorded as non-blocking implementation choices under the prospective blocker calibration.

## Stage 2 — HUMAN_BLOCKER

First observable stage: Stage 2 cross-activity consistency review. No Stage 2 refactoring or Stage 3 work is authorized.

1. **under-specification — Quotation to Order eligibility/lifecycle**: requirements do not say whether business-expired, persisted `expired`, or `ordered` Quotation may source an Order. A choice changes allowed state transitions.
2. **under-specification — post-conversion Quotation state**: requirements do not say whether successful conversion changes Quotation status to `ordered`, or what invariant relates status and canonical Order association.
3. **under-specification — Quotation revision policy**: editable fields and eligible Quotation states are undefined; this changes allowed transitions and expiry interpretation.
4. **under-specification — direct Order line cardinality**: zero Order Lines are DDL-permitted and implementation-permitted, but business cardinality is not defined.
5. **under-specification / conditional data-model insufficiency — copied header projection**: “then-current header” is undefined. If it includes expiry/status, the frozen Order schema lacks fields/meaning for that snapshot; no schema change is made pending decision.

Non-blocking implementation defect: Quotation header and lines are read in separate queries and can be non-snapshot-coherent during concurrent revision. This is fixable only after the blocker set is resolved and does not determine any policy.

## Stage 2 — resolved by HD-005 through HD-009

The blocked implementation remains historical, not adopted. No DDL amendment is authorized. A fresh resolution run must implement decisions and fix the non-policy coherent-snapshot defect before review.
