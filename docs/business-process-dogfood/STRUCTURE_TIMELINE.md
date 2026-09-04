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

Not yet adopted. The earlier refactoring dispatch was immediately aborted because it targeted the resolution directory; no refactoring outcome is recorded here.
