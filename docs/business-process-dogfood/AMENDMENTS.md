# Amendments

## 2026-09-05 — frozen acceptance-test path defect

Before worker dispatch, isolated run-copy inspection found that Stage 1–4 tests resolved `ddl.sql` one directory below repository root. Only the relative path changed from `../../../../docs/...` to `../../../../../docs/...`; business assertions, DDL, packets, and prompts are unchanged. The original freeze remains commit `1e67a6f853985ffe9e50d37fb8c9efd9efc79257`. No run had begun.

## 2026-09-05 — second path calculation correction

The first amendment used an incorrect ancestor count. The Stage 1 worker encountered `ENOENT` before application behavior ran; its source is not adopted. Mechanical `Resolve-Path` verification established six parent segments are required. Stage 1–4 tests change only the DDL path from five to six parent segments. A clean, fresh Stage 1 rerun is required.
