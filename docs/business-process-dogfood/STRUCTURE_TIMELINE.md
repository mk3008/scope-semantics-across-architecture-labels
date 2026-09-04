# Structure timeline

## Stage 1 clean implementation snapshot — adopted

Snapshot: `work/business-process-dogfood/runs/stage1/implementation-rerun-2/`.

- Complete source tree: `src/app.js`.
- Relevant path: `src/app.js`.
- Current semantic owner: Sales Quotation creation and search, including Quotation Line persistence and expiry determination.
- Current consumers: the fixed application entry/cumulative Stage 1 acceptance test only.
- Apparent physical scope: feature-local / single-file; no folder structure is inferred as required at this state.
- Changed from baseline: the fixed entry now exposes the Stage 1 application behavior through raw PostgreSQL access.

## Stage 1 post-defect-resolution snapshot — adopted

Snapshot: `work/business-process-dogfood/runs/stage1/consistency-resolution/`.

- Complete source tree: `src/app.js`.
- Relevant path and semantic owner remain `src/app.js` / Sales Quotation creation and search.
- Current consumers remain the Stage 1 caller and test.
- Changed from clean implementation: statement-time expiry validation and numeric-NaN rejection; no physical move, promotion, or demotion.

## Stage 1 refactoring

Adopted snapshot: `work/business-process-dogfood/runs/stage1/refactoring-rerun-1/`.

- Complete source tree: `src/app.js`.
- Relevant physical path remains `src/app.js`; no directory was introduced.
- Current semantic owner and consumer set are unchanged: Sales Quotation creation/search and the fixed Stage 1 caller/test.
- Structural change: validation/read helpers are colocated in the `QuotationStore` boundary inside the existing file. No promotion/demotion or cross-scope sharing was introduced.
- Diff: `evidence/diffs/stage1-refactoring.diff`.
- Verification: PostgreSQL cumulative acceptance tests 2/2 pass.

Stage 1 status: **complete**.

## Stage 2 — complete

- Adopted post-resolution snapshot: `work/business-process-dogfood/runs/stage2/consistency-resolution/`.
- Adopted refactoring snapshot: `work/business-process-dogfood/runs/stage2/refactoring-rerun-1/`.
- Complete source tree remains `src/app.js`; current semantic owners are Quotation lifecycle and Order creation with their present consumers.
- Refactoring moved shared input validation to module functions and removed OrderStore dependence on QuotationStore internals. No file/directory move, promotion, or demotion occurred.
- Diff: `evidence/diffs/stage2-refactoring.diff`; behavior verification 1/1 pass.
