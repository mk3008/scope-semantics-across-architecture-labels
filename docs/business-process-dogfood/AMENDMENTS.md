# Amendments

## 2026-09-05 — frozen acceptance-test path defect

Before worker dispatch, isolated run-copy inspection found that Stage 1–4 tests resolved `ddl.sql` one directory below repository root. Only the relative path changed from `../../../../docs/...` to `../../../../../docs/...`; business assertions, DDL, packets, and prompts are unchanged. The original freeze remains commit `1e67a6f853985ffe9e50d37fb8c9efd9efc79257`. No run had begun.
